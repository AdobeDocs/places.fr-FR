---
title: Utilisation de l’extension Places Monitor
description: Informations sur l’installation, la configuration et l’utilisation de l’extension Places Monitor.
translation-type: tm+mt
source-git-commit: 7fdaace59886225b7fd9b0eba8cc6c2a139fa2d7
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 10%

---


# Utilisation de l&#39;extension Places Monitor {#using-places-monitor-extension}

Pour utiliser l&#39;extension Places Monitor, effectuez les tâches suivantes :

## Installez l’extension Places Monitor dans Experience Platform Launch

1. Dans l’Experience Platform Launch, cliquez sur l’onglet **[!UICONTROL Extensions]**.
1. Dans l&#39;onglet **[!UICONTROL Catalogue]**, recherchez l&#39;extension **[!UICONTROL Moniteur des emplacements]**, puis cliquez sur **Installer**.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Suivez le processus de publication pour mettre à jour la configuration du SDK.

### Configuration de l&#39;extension Places Monitor {#configure-places-monitor-extension}

Il n&#39;existe aucune tâche de configuration pour l&#39;extension du moniteur de lieux.

![configuration du moniteur](/help/assets/configure_places_monitor.png) de lieux ‌

## Ajouter l&#39;extension Places Monitor à votre application {#add-monitor-extension-to-app}

Vous trouverez ci-dessous les instructions concernant l’ajout de l’extension Places Monitor à votre application Android ou iOS.

La prise en charge des plates-formes supplémentaires pour l&#39;extension Places Monitor inclut :
**[Cordova Places Monitor](https://github.com/adobe/cordova-acpplaces-monitor/blob/master/README.md)**

**[Réagir à l&#39;écran des emplacements natifs](https://github.com/adobe/react-native-acpplaces-monitor/blob/master/README.md)**

**[Écran de battage](https://github.com/adobe/flutter_acpplaces_monitor/blob/master/README.md)**


### Android

Sous Android, procédez comme suit :

#### Java

1. Ajoutez l’extension Places Monitor et l’extension Places à votre projet à l’aide du fichier de nivellement de votre application.

1. Incluez également les derniers services Google Location dans le fichier de classement.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

1. Importez l’extension Places Monitor dans l’activité principale de votre application.

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

Sous iOS, procédez comme suit :

1. Ajoutez la bibliothèque à votre projet via votre `Podfile` Cocoapods en ajoutant le `pod 'ACPPlacesMonitor'`.
1. Importez les bibliothèques d’écran Lieux et Lieux :

#### Objective-C

```objectivec
#import "ACPCore.h"
#import "ACPPlaces.h"
#import "ACPPlacesMonitor.h"
```

#### Swift

```swift
import ACPCore
import ACPPlaces
import ACPPlacesMonitor
```


## Enregistrer et début le moniteur des lieux {#register-start-places-monitor}

Vous devez enregistrer et début le moniteur de lieux sur Android ou iOS.

## Android

Sous Android, procédez comme suit :

### Java

Dans la méthode `OnCreate` de votre application, enregistrez les extensions du moniteur de lieux :

```java
public class MobileApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.ConfigureWithAppId("yourAppId");
        try {
            PlacesMonitor.registerExtension(); //Register PlacesMonitor with Mobile Core
            Places.registerExtension(); //Register Places with Mobile Core
            MobileCore.start(null);
            PlacesMonitor.start();//Start monitoring the geo-fences
        } catch (Exception e) {
            //Log the exception
        }
    }
}
```

>[!IMPORTANT]
>
>La surveillance des lieux dépend de l&#39;extension Places. Lorsque vous installez manuellement l’extension Surveiller les Places, veillez à ajouter également la bibliothèque `places.aar` à votre projet.

## iOS

Dans l’application iOS `application:didFinishLaunchingWithOptions`, inscrivez `PlacesMonitor` et les emplacements avec Mobile Core :

### Objectif C

```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions {
    [ACPCore configureWithAppId:@"yourAppId"];
    [ACPPlaces registerExtension];
    [ACPPlacesMonitor registerExtension];
    [ACPCore start:^{            
        // do other initialization required for the SDK
        [ACPPlacesMonitor start];
    }];

    return YES;
}
```

#### Swift

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    ACPCore.configure(withAppId: "yourAppId")
    ACPPlaces.registerExtension()       
    ACPPlacesMonitor.registerExtension()
    ACPCore.start({
        // do other initialization required for the SDK
        ACPPlacesMonitor.start()
    })

    // Override point for customization after application launch.        
    return true
}
```

>[!IMPORTANT]
>
>La surveillance des lieux dépend de l&#39;extension Places. Lors de l&#39;installation manuelle de l&#39;extension Places Monitor, veillez à ajouter également la bibliothèque `libACPPlaces_iOS.a` à votre projet.


## Ajouter des autorisations pour le manifeste

### Android

**Java**

Pour toutes les versions d&#39;Android, pour déclarer que votre application a besoin d&#39;une autorisation d&#39;emplacement, ajoutez un élément `<uses-permission>` dans votre manifeste d&#39;application, en tant qu&#39;enfant de l&#39;élément de niveau supérieur `<manifest>`. Pour les applications Android qui utilisent l&#39;API de cible Niveau 29 et plus, pour permettre à l&#39;application d&#39;accéder à un emplacement en arrière-plan, incluez l&#39;autorisation ACCESS_BACKGROUND_LOCATION.

```java
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.adobe.placesapp">
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    // Only for Android apps targeting API level 29 and above
  <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
  <application>        
    ...    
  </application>
</manifest>
```


## Activer les mises à jour d&#39;emplacement en arrière-plan {#enable-location-updates-background}

iOS prend en charge la diffusion de événements d’emplacement pour les applications suspendues ou qui ne sont plus en cours d’exécution. Pour recevoir les mises à jour d&#39;emplacement en arrière-plan pour l&#39;extension Places Monitor, configurez la fonctionnalité de mises à jour d&#39;emplacement pour votre application dans `Xcode.background-location-updates`.

![utilisation du moniteur de lieux](/help/assets/using-the-places-monitor_1.png)

## Configuration des clés de liste

Les clés suivantes doivent être incluses dans le fichier `Info.plist` de votre application :

* `NSLocationWhenInUseUsageDescription` - le texte doit décrire pourquoi l’application demande l’accès aux informations d’emplacement de l’utilisateur lors de son exécution au premier plan.
* `NSLocationAlwaysAndWhenInUseUsageDescription` - le texte doit décrire pourquoi l’application demande l’accès aux informations d’emplacement de l’utilisateur en tout temps.

>[!TIP]
>
>Si votre application prend en charge iOS 10 et les versions antérieures, la clé `NSLocationAlwaysUsageDescription` est également requise.

![](/help/assets/using-the-places-monitor_2.png)
