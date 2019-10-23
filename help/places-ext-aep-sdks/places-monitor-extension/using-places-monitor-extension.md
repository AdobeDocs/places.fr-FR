---
title: Utilisation de l’extension Places Monitor
seo-title: Utilisation de l’extension Places Monitor
description: Informations sur l’installation, la configuration et l’utilisation de l’extension Places Monitor.
seo-description: 'Informations sur l’installation, la configuration et l’utilisation de l’extension Places Monitor. '
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# Utilisation de l’extension Places Monitor {#using-places-monitor-extension}

Pour utiliser l’extension Places Monitor, procédez comme suit :

## Installation de l’extension Places Monitor dans Experience Platform Launch

1. Dans le lancement de la plateforme d’expérience, cliquez sur l’ **[!UICONTROL Extensions]** onglet.
2. Dans l’ **[!UICONTROL Catalog]** onglet, recherchez l’ **[!UICONTROL Places Monitor]** extension, puis cliquez sur **Installer**.
3. Cliquez sur **[!UICONTROL Save]** (Nouvelle propriété).
4. Suivez le processus de publication pour mettre à jour la configuration du SDK.

### Configuration de l’extension Places Monitor {#configure-places-monitor-extension}

Il n’existe aucune tâche de configuration pour l’extension Places Monitor.

![configuration du moniteur](/help/assets/configure_places_monitor.png)Places ‌

## Ajout de l’extension Places Monitor à votre application {#add-monitor-extension-to-app}

Vous devez ajouter l’extension Places Monitor à votre application Android ou iOS.

### Android

Dans Android, procédez comme suit :

#### Java

1. Ajoutez l’extension Places Monitor et l’extension Places à votre projet à l’aide du fichier de nivellement de votre application.

2. Incluez également les derniers services Google Location dans le fichier de classification.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

3. Importez l’extension Places Monitor dans l’activité principale de votre application.

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

Sous iOS, procédez comme suit :

1. Ajoutez la bibliothèque à votre projet via votre Cocoapods `Podfile` en ajoutant `pod 'ACPPlacesMonitor'`.
2. Importez les bibliothèques du moniteur Lieux et Lieux :

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


## Enregistrement et démarrage du moniteur de lieux {#register-start-places-monitor}

Vous devez vous enregistrer et démarrer Places Monitor sous Android ou iOS.

## Android

Dans Android, procédez comme suit :

### Java

Dans la `OnCreate` méthode de votre application, enregistrez les extensions du moniteur de lieux :

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
        } catch (Exception e) {
            //Log the exception
         }
    }
}
```

**** Important :La surveillance des lieux dépend de l’extension Places. Lorsque vous installez manuellement l’extension Places Monitor, veillez à ajouter également la `places.aar` bibliothèque à votre projet.

## iOS

Dans les`application:didFinishLaunchingWithOptions`applications iOS, inscrivez-vous `PlacesMonitor` et emplacements avec Mobile Core :

### Objective-C

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
>La surveillance des lieux dépend de l’extension Places. Lors de l’installation manuelle de l’extension Places Monitor, veillez à ajouter également la `libACPPlaces_iOS.a` bibliothèque à votre projet.


## Ajouter des autorisations au manifeste

### Android

**Java**

Pour toutes les versions d’Android, pour déclarer que votre application a besoin d’une autorisation d’emplacement, ajoutez un `<uses-permission>` élément dans le manifeste de votre application, en tant qu’enfant de l’ `<manifest>` élément de niveau supérieur. Pour les applications Android qui ciblent les API Niveau 29 et supérieur, pour permettre à l'application d'accéder à l'emplacement en arrière-plan, incluez l'autorisation ACCESS_BACKGROUND_LOCATION.

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


## Activation des mises à jour d’emplacement en arrière-plan {#enable-location-updates-background}

iOS prend en charge la diffusion d’événements d’emplacement dans les applications qui sont suspendues ou qui ne sont plus en cours d’exécution. Pour recevoir les mises à jour de l’emplacement en arrière-plan pour l’extension du moniteur de lieux, configurez la fonctionnalité des mises à jour de l’emplacement pour votre application dans `Xcode.background-location-updates`.

![utilisation du moniteur des lieux](/help/assets/using-the-places-monitor_1.png)

## Configuration des clés de liste

Les clés suivantes doivent être incluses dans le `Info.plist` fichier de votre application :

* `NSLocationWhenInUseUsageDescription` - le texte doit expliquer pourquoi l’application demande l’accès aux informations d’emplacement de l’utilisateur lors de son exécution au premier plan.
* `NSLocationAlwaysAndWhenInUseUsageDescription` - le texte doit décrire pourquoi l’application demande en permanence l’accès aux informations d’emplacement de l’utilisateur.

>[!TIP]
>
>Si votre application prend en charge iOS 10 et les versions antérieures, la `NSLocationAlwaysUsageDescription` clé est également requise.

![](/help/assets/using-the-places-monitor_2.png)

