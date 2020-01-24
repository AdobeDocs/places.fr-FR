---
title: Extension Places
description: L’extension Places vous permet d’agir en fonction de l’emplacement de vos utilisateurs.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Extension Places {#places-extension}

L’extension Places vous permet d’agir en fonction de l’emplacement de vos utilisateurs. Cette extension est l&#39;interface des API du service de requête Places. En écoutant les événements qui contiennent des coordonnées GPS et des événements de région de géofence, cette extension distribue les nouveaux événements qui sont traités par le moteur de règles. L’extension Places récupère et fournit également une liste des points d’intérêt les plus proches pour les données de l’application récupérées à partir des API. Les régions renvoyées par les API sont stockées dans le cache et la persistance, ce qui permet un traitement hors ligne limité.

## Installation de l’extension Places dans Adobe Experience Platform Launch

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]**tab.
1. Dans l’ **[!UICONTROL Catalog]**onglet, recherchez l’**[!UICONTROL Places]** extension, puis cliquez sur **[!UICONTROL Install]**.
1. Sélectionnez les bibliothèques Places que vous souhaitez utiliser dans cette propriété. Ce sont les bibliothèques qui seront accessibles dans votre application.
1. Cliquez sur **[!UICONTROL Save]**(Exécuter des tests d’Auditor).

   Lorsque vous cliquez sur **[!UICONTROL Save]**, le SDK de la plate-forme d’expérience recherche des points d’accès dans les services Places dans les bibliothèques que vous avez sélectionnées. Les données d’API ne sont pas incluses dans le téléchargement de la bibliothèque lorsque vous créez l’application, mais un sous-ensemble d’API basé sur l’emplacement est téléchargé sur le périphérique de l’utilisateur final au moment de l’exécution et est basé sur les coordonnées GPS de l’utilisateur.

1. Terminez le processus de publication pour mettre à jour la configuration du SDK.

   Pour plus d’informations sur la publication dans Experience Platform Launch, voir [Publication](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html).

### Configure the Places extension {#configure-places-extension}

![](//help/assets/places-extension.png)

## Ajout de l’extension Places à votre application {#add-places-to-app}

Vous pouvez ajouter l’extension Places à vos applications Android et iOS.

### Android

Pour ajouter l’extension Places à votre application à l’aide de Java :

1. Ajoutez l’extension Places à votre projet à l’aide du fichier de nivellement de votre application.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importez l’extension Places dans l’activité principale de votre application.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Pour ajouter l&#39;extension Places à votre application à l&#39;aide de Objective-C ou Swift :

1. Ajoutez les bibliothèques Places et [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) à votre projet. Vous devez ajouter les conteneurs suivants à votre `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Sinon, si vous n&#39;utilisez pas Cocoapods, vous pouvez inclure manuellement les bibliothèques Mobile Core et Places de notre page [](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) de publication sur Github.

1. Mettez à jour vos Cocoapods :

   ```objective-c
   pod update
   ```

1. Ouvrez Xcode et, dans la classe AppDelegate, importez les en-têtes Core et Places :

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

## Clés de configuration

Pour mettre à jour la configuration du SDK par programmation au moment de l’exécution, utilisez les informations suivantes pour modifier les valeurs de configuration de l’extension Places. Pour plus d’informations, voir Référence [sur les API](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)de configuration.

| Clé | Obligatoire | Description |
| :--- | :--- | :--- |
| `places.libraries` | Oui | Bibliothèques d’extensions Places pour l’application mobile. Il spécifie l’ID de bibliothèque et le nom de la bibliothèque que l’application mobile prend en charge. |
| `places.endpoint` | Oui | Point de fin Places Query Service par défaut, utilisé pour obtenir des informations sur les bibliothèques et les points d’accès (POI). |

