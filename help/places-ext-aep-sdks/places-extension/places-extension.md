---
title: Extension Places
description: L’extension Places vous permet d’agir en fonction de l’emplacement de vos utilisateurs.
exl-id: 09c02753-09b3-4e07-82b2-b6c72c4e0e42
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 5%

---

# Extension Places {#places-extension}

L’extension Places vous permet d’agir en fonction de l’emplacement de vos utilisateurs. Cette extension est l’interface des API de Places Query Service. En écoutant les événements qui contiennent des coordonnées GPS et des événements de région de géobarrière, cette extension distribue les nouveaux événements qui sont traités par le moteur de règles. L’extension Places récupère et fournit également une liste du point ciblé le plus proche pour les données de l’application récupérées à partir des API. Les régions renvoyées par les API sont stockées dans le cache et la persistance, ce qui permet un traitement hors ligne limité.

## Installation de l’extension Places dans Adobe Experience Platform Launch

1. Dans Experience Platform Launch, cliquez sur le **[!UICONTROL Extensions]** .
1. Sur le **[!UICONTROL Catalogue]** , recherchez la variable **[!UICONTROL Places]** puis cliquez sur **[!UICONTROL Installer]**.
1. Sélectionnez les bibliothèques Places que vous souhaitez utiliser dans cette propriété. Il s’agit des bibliothèques qui seront accessibles dans votre application.
1. Cliquez sur **[!UICONTROL Enregistrer]**.

   Lorsque vous cliquez **[!UICONTROL Enregistrer]**, le SDK Experience Platform recherche les points ciblés dans les services Places dans les bibliothèques que vous avez sélectionnées. Les données du point ciblé ne sont pas incluses dans le téléchargement de la bibliothèque lorsque vous créez l’application, mais un sous-ensemble de points ciblés basé sur l’emplacement est téléchargé sur l’appareil de l’utilisateur final au moment de l’exécution et est basé sur les coordonnées GPS de l’utilisateur.

1. Suivez le processus de publication pour mettre à jour la configuration du SDK.

   Pour plus d’informations sur la publication dans Experience Platform Launch, voir [Publication](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html?lang=fr).

### Configuration de l’extension Places {#configure-places-extension}

![](/help/assets/places-extension.png)

## Ajout de l’extension Places à votre application {#add-places-to-app}

Vous pouvez ajouter l’extension Places à vos applications Android et iOS. Les étapes d’ajout de Places à votre application iOS ou Android sont présentées ci-dessous. Les extensions Places sont également disponibles pour les plateformes suivantes. Pour ajouter des Places à votre application lors du développement avec l’une de ces plateformes, consultez les liens suivants :

**[Plug-in Cordova Places](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[Module externe React Native Places](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Plug-in Fbattaces](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Module externe Xamarin Places](https://github.com/adobe/xamarin-acpcore)**


### Android

Pour ajouter l’extension Places à votre application à l’aide de Java :

1. Ajoutez l’extension Places à votre projet à l’aide du fichier gradle de votre application.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importez l&#39;extension Places dans l&#39;activité principale de votre application.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Pour ajouter l’extension Places à votre application à l’aide d’Objective-C ou de Swift :

1. Ajoutez les Places et [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) bibliothèques de votre projet. Vous devrez ajouter les capsules suivantes à votre `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Si vous n’utilisez pas Cocoapods, vous pouvez également inclure manuellement les bibliothèques Mobile Core et Places de notre [page des versions](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) sur Github.

1. Mettez à jour votre Cocoapods :

   ```objective-c
   pod update
   ```

1. Ouvrez Xcode, puis, dans votre classe AppDelegate, importez les en-têtes Core et Places :

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

Vous devez enregistrer l’extension Places avec Mobile Core dans Android et iOS.

#### Android

Dans votre application `OnCreate` enregistrer les extensions Places :

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

Dans votre application `application:didFinishLaunchingWithOptions:` , enregistrez l’extension Places avec vos autres appels d’enregistrement SDK :

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

### Modification de la durée de vie de l’appartenance à Places {#places-ttl}

Les données d’emplacement peuvent rapidement devenir obsolètes, en particulier si l’appareil ne reçoit pas de mises à jour d’emplacement en arrière-plan.

Contrôlez la durée de vie des données d’appartenance à Places sur l’appareil en définissant la variable `places.membershipttl` paramètre de configuration . La valeur transmise à représente le nombre de secondes pendant lesquelles l’état Places reste valide pour l’appareil.

#### Android

Dans le rappel de `MobileCore.start()` mettre à jour la configuration avec les modifications nécessaires avant d’appeler `lifecycleStart`:

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

Sur la première ligne du rappel de `ACPCore`&#39;s `start:` méthode, appel `updateConfiguration:`

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

Pour mettre à jour la configuration du SDK par programmation au moment de l’exécution, utilisez les informations suivantes pour modifier les valeurs de configuration de l’extension Places. Pour plus d’informations, voir [Référence de l’API de configuration](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| Clé | Obligatoire | Description |
| :--- | :--- | :--- |
| `places.libraries` | Oui | Les bibliothèques d’extension Places pour l’application mobile. Il spécifie l’ID de bibliothèque et le nom de la bibliothèque pris en charge par l’application mobile. |
| `places.endpoint` | Oui | Point d’entrée Places Query Service par défaut, utilisé pour obtenir des informations sur les bibliothèques et les points ciblés. |
| `places.membershipttl` | Non | Valeur par défaut de 3 600 (secondes dans une heure). Indique la durée de validité, en secondes, des informations d’appartenance à Places pour l’appareil. |
