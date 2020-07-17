---
title: Extension Places
description: L'extension Places vous permet d'agir en fonction de l'emplacement de vos utilisateurs.
translation-type: tm+mt
source-git-commit: a7dddb78e1e00a0bde01ea668334932759a9dae8
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 5%

---


# Extension Places {#places-extension}

L&#39;extension Places vous permet d&#39;agir en fonction de l&#39;emplacement de vos utilisateurs. Cette extension est l&#39;interface des API du service de Requête des emplacements. En écoutant les événements qui contiennent des coordonnées GPS et des événements de région de géofence, cette extension envoie de nouveaux événements qui sont traités par le moteur de règles. L’extension Places récupère également et fournit une liste de l’API la plus proche pour les données de l’application qui sont récupérées à partir des API. Les régions renvoyées par les API sont stockées dans le cache et la persistance, ce qui permet un traitement hors ligne limité.

## Installer l&#39;extension Places dans le lancement d&#39;Adobe Experience Platform

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. Dans l’ **[!UICONTROL Catalog]** onglet, recherchez l’ **[!UICONTROL Places]** extension, puis cliquez sur **[!UICONTROL Install]**.
1. Sélectionnez les bibliothèques de lieux que vous souhaitez utiliser dans cette propriété. Il s’agit des bibliothèques qui seront accessibles dans votre application.
1. Cliquez sur **[!UICONTROL Save]**.

   Lorsque vous cliquez sur **[!UICONTROL Save]**, le SDK Experience Platform recherche les points d’accès dans les services de lieux dans les bibliothèques que vous avez sélectionnées. Les données d’API ne sont pas incluses dans le téléchargement de la bibliothèque lorsque vous créez l’application, mais un sous-ensemble d’API basé sur l’emplacement est téléchargé sur le périphérique de l’utilisateur final au moment de l’exécution et est basé sur les coordonnées GPS de l’utilisateur.

1. Terminez le processus de publication pour mettre à jour la configuration du SDK.

   Pour plus d’informations sur la publication dans l’Experience Platform Launch, voir [Publication](https://docs.adobe.com/content/help/fr-FR/launch/using/reference/publish/overview.html).

### Configure the Places extension {#configure-places-extension}

![](//help/assets/places-extension.png)

## Ajouter l’extension Places à votre application {#add-places-to-app}

Vous pouvez ajouter l’extension Places à vos applications Android et iOS. Vous trouverez ci-dessous la procédure à suivre pour ajouter des emplacements à votre application iOS ou Android. Les extensions Places sont également disponibles pour les plateformes suivantes. Pour ajouter des emplacements à votre application lors du développement avec l’une de ces plateformes, consultez les liens suivants :

**[Plug-in Cordova Places](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[Module externe Réagir aux emplacements natifs](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Plug-in Fbattement Places](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Module externe Places Xamarin](https://github.com/adobe/xamarin-acpcore)**


### Android

Pour ajouter l’extension Places à votre application à l’aide de Java :

1. Ajoutez l’extension Places sur votre projet à l’aide du fichier de nivellement de votre application.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importez l&#39;extension Places dans l&#39;activité principale de votre application.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Pour ajouter l&#39;extension Places à votre application à l&#39;aide de Objective-C ou Swift :

1. Ajoutez les bibliothèques Places et Core [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) Mobile à votre projet. Vous devez ajouter les modules suivants à votre `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Sinon, si vous n&#39;utilisez pas Cocoapods, vous pouvez inclure manuellement les bibliothèques Mobile Core et Places dans la page [](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) de publication de Github.

1. Mettez à jour vos Cocoapods :

   ```objective-c
   pod update
   ```

1. Ouvrez Xcode et dans la classe AppDelegate, importez les en-têtes Core et Places :

   **Objective-C**

   ```objective-c
   #import "ACPCore.h"
   #import "ACPPlaces.h"
   ```

   **Swift**

   ```swift
   import ACPCore
   import ACPPlaces
   ```

### Enregistrement de l’extension Places avec Mobile Core {#register-places-mobile-core}

Vous devez enregistrer l’extension Places avec Mobile Core sous Android et iOS.

#### Android

Dans la `OnCreate` méthode de votre application, enregistrez les extensions Places :

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(null);
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

Dans la `application:didFinishLaunchingWithOptions:` méthode de votre application, enregistrez l’extension Places avec vos autres appels d’enregistrement SDK :

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls
    [ACPPlaces registerExtension];    
    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls
    ACPPlaces.registerExtension();
    return true;
}
```

### Modification des lieux où la durée de vie de l’abonnement {#places-ttl}

Les données d’emplacement peuvent rapidement devenir obsolètes, en particulier si le périphérique ne reçoit pas de mises à jour d’emplacement en arrière-plan.

Contrôlez la durée de vie des données d’adhésion Places sur le périphérique en définissant le paramètre de `places.membershipttl` configuration. La valeur transmise représente le nombre de secondes pendant lesquelles l’état Lieux reste valide pour le périphérique.

#### Android

Dans le rappel de `MobileCore.start()` mise à jour de la configuration avec les modifications nécessaires avant d&#39;appeler `lifecycleStart`:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(new AdobeCallback() {
                @Override
                public void call(Object o) {
                    // switch to your App ID from Launch
                    MobileCore.configureWithAppID("my-app-id");

                    final Map<String, Object> config = new HashMap<>();
                    config.put("places.membershipttl", 30);
                    MobileCore.updateConfiguration(config);

                    MobileCore.lifecycleStart(null);
                }
            });
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

Sur la première ligne du rappel de la `ACPCore`méthode `start:` de, appelez `updateConfiguration:`

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls

    const UIApplicationState appState = application.applicationState;
    [ACPCore start:^{
        [ACPCore updateConfiguration:@{@"places.membershipttl":@(30)}];

        if (appState != UIApplicationStateBackground) {
            [ACPCore lifecycleStart:nil];            
        }
    }];

    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls

    let appState = application.applicationState;            
    ACPCore.start {
        ACPCore.updateConfiguration(["places.membershipttl" : 30])

        if appState != .background {
            ACPCore.lifecycleStart(nil)
        }    
    }

    return true;
}
```

## Clés de configuration

Pour mettre à jour la configuration du SDK par programmation au moment de l’exécution, utilisez les informations suivantes pour modifier les valeurs de configuration de l’extension Places. Pour plus d’informations, voir Référence [sur les API](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)de configuration.

| Clé | Obligatoire | Description |
| :--- | :--- | :--- |
| `places.libraries` | Oui | Bibliothèques d’extensions Places pour l’application mobile. Il spécifie l’ID de bibliothèque et le nom de la bibliothèque pris en charge par l’application mobile. |
| `places.endpoint` | Oui | Point de terminaison Service de Requête de lieux par défaut, qui est utilisé pour obtenir des informations sur les bibliothèques et les points d’intérêt. |
| `places.membershipttl` | Non | Valeur par défaut : 3 600 (secondes dans une heure). Indique la durée, en secondes, pendant laquelle les informations d&#39;adhésion de l&#39;appareil restent valides. |
