---
title: Référence à l’API du moniteur de lieux
description: Liste des API du moniteur des lieux.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Référence à l’API du moniteur de lieux {#places-api-reference}

## Enregistrer l&#39;extension d&#39;écran Places

Enregistre l’extension Places Monitor dans le concentrateur d’événements principaux.

### RegisterExtension (Android)

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

Voici la syntaxe en Java :

```java
public static void registerExtension();
```

#### Exemple

Appelez cette méthode dans la `onCreate` méthode où vous initialisez le reste du SDK de la plateforme d’expérience.

```java
public class MobileApp extends Application {
  @Override
  public void onCreate(){
     super.onCreate();
     MobileCore.setApplication(this);
     try {
        PlacesMonitor.registerExtension();
     } catch (Exception e) {
       //Log the exception
       }
    }
 }
```

### RegisterExtension (iOS)

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

Voici la syntaxe de Objective-C :

```objective-c
+ (void) registerExtension;
```

#### Exemple

This method should be called in the `didFinishLaunchingWithOptions` delegate method of the `AppDelegate`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [ACPCore configureWithAppId:@"launch-appID"];    
    [ACPPlaces registerExtension];    
    [ACPPlacesMonitor registerExtension];

    [ACPCore start:^{
        // do other initialization of the SDK
    }];

    return YES;
}
```

## Version d’extension

Renvoie la version actuelle de l’extension Places Monitor

### ExtensionVersion (Android)

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

```java
public static String extensionVersion();
```

#### Exemple

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion (iOS)

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

```objective-c
+ (nonnull NSString*) extensionVersion;
```

#### Exemple

```objective-c
NSString *placesMonitorVersion = [ACPPlacesMonitor extensionVersion];
```

## Démarrer la surveillance du périphérique

Commencez à suivre l’emplacement du périphérique et à surveiller les emplacements voisins.

### Démarrer (Android)

Si l’autorisation d’utiliser l’emplacement du périphérique n’a pas été accordée par l’utilisateur, le premier appel à l’ `start` API l’invite à l’autoriser.

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

```java
public static void start();
```

#### Exemple

```java
PlacesMonitor.start();
```

### Démarrer (iOS)

>[!IMPORTANT]
>
>Pour commencer la surveillance, le service de localisation doit avoir l’autorisation nécessaire :
>
>* Si l’autorisation du service Places n’a pas été fournie à l’application, le premier appel à l’ `start` API demande l’autorisation d’utiliser le service Places tel que configuré pour l’application.
>* Selon les capacités de votre périphérique, si l’autorisation a été fournie, le moniteur des lieux effectue le suivi de l’emplacement de l’utilisateur en fonction de l’emplacement actuellement défini `ACPPlacesMonitorMode`. Par défaut, le moniteur utilise `ACPPlacesMonitorModeSignificantChanges`.


>[!CAUTION]
>
>Si votre appel à démarrer la surveillance est effectué avant l’initialisation du SDK, il se peut qu’il soit ignoré.

Vous pouvez vous assurer que le SDK a terminé l’initialisation en appelant `start` à partir du rappel fourni à `ACPCore::start:`.

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

```objectivec
+ (void) start;
```

#### Exemple

Démarrage du moniteur des emplacements lorsque le SDK est en cours d’initialisation :

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

Démarrage du moniteur de lieux plus tard dans l’exécution de l’application :

```objective-c
[ACPPlacesMonitor start];
```

## Arrêter la surveillance du périphérique

Arrête le suivi de l’emplacement du périphérique.

### Arrêt (Android)

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

```java
public static void stop();
```

#### Exemple

```java
PlacesMonitor.stop();
```

### Arrêt (iOS)

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

```objectivec
+ (void) stop;
```

#### Exemple

```objective-c
[ACPPlacesMonitor stop];
```

## Emplacement de mise à jour

Utilisez cette API pour une mise à jour immédiate de l’emplacement du périphérique. Lorsque vous appelez cette API, le périphérique tente de déterminer l’emplacement avec le niveau de précision que vous avez spécifié. Ce processus actualise également les points d’intérêt voisins qui sont surveillés par l’extension.

### UpdateLocation (Android)

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

```java
public static void updateLocation();
```

#### Exemple

```java
PlacesMonitor.updateLocation();
```

### UpdateLocationNow (iOS)

#### Syntaxe

```objective-c
+ (void) updateLocationNow;
```

#### Exemple

```objective-c
[ACPPlacesMonitor updateLocationNow];
```

## Autorisation d’emplacement de l’application

Vous pouvez utiliser cette API pour définir le type d’autorisation d’emplacement que l’utilisateur est invité à utiliser pour le service Places.

### SetLocationPermission (Android)

Cette API définit le type de demande d’autorisation d’emplacement pour laquelle l’utilisateur est invité à sélectionner.

>[!TIP]
>
>Cette API n’est efficace que pour les périphériques utilisant Android 10 et versions ultérieures.
>
>Pour définir l’invite d’autorisation appropriée à afficher pour l’utilisateur, appelez cette API avant le `PlacesMonitor.start()`. L’appel de cette méthode, tout en effectuant une surveillance active, met à niveau le niveau d’autorisation d’emplacement vers la valeur d’autorisation demandée. Si le niveau d’autorisation demandé est déjà fourni ou refusé par l’utilisateur de l’application, ou si vous tentez de rétrograder l’autorisation `ALWAYS_ALLOW` vers `WHILE_USING_APP`, cette méthode n’a aucun effet.

L’autorisation d’emplacement peut être définie sur l’une des valeurs suivantes :

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   Cette valeur invite l’utilisateur à accéder à l’emplacement du périphérique uniquement lors de l’utilisation de l’application. Une application est considérée comme étant en cours d’utilisation lorsque l’utilisateur consulte l’application sur son écran de périphérique, par exemple lorsqu’une activité est en cours d’exécution au premier plan.

   >[!TIP]
   >
   >Assurez-vous que l’autorisation utilisateur ACCESS_FINE_LOCATION est définie dans le fichier manifeste de l’application.

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   Cette valeur invite l’utilisateur à accéder à l’emplacement du périphérique, même lorsque l’application est en arrière-plan.

   >[!TIP]
   >
   >Assurez-vous que les autorisations utilisateur ACCESS_BACKGROUND_LOCATION et ACCESS_FINE_LOCATION sont définies dans le fichier manifeste de l’application.

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` est la valeur d’autorisation d’emplacement par défaut.

>[!IMPORTANT]
>
>Si l’utilisateur de l’application se voit accorder l’ `WHILE_USING_APP` autorisation, les expressions Geofence ne seront pas enregistrées auprès du système d’exploitation. Par conséquent, l’extension du moniteur des lieux ne déclenchera pas d’événements d’entrée/sortie dans les régions qui se produisent en arrière-plan.

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### Exemple

Pour demander l&#39; `WHILE_USING_APP` autorisation :

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

Pour mettre à niveau vers `ALWAYS_ALLOW` l’autorisation :

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel (iOS)

Cette API définit le type de demande d’autorisation d’emplacement pour laquelle l’utilisateur sera invité à répondre.

Pour définir l’invite d’autorisation appropriée à afficher pour l’utilisateur, appelez `SetRequestAuthorizationLevel` avant d’appeler `[ACPPlacesMonitor start]`. Pour définir l’invite d’autorisation appropriée à afficher à l’utilisateur, appelez cette API avant le `[ACPPlacesMonitor start]`. L’appel de cette méthode lors de la surveillance active met à niveau le niveau d’autorisation de l’emplacement vers la valeur d’autorisation demandée. Si le niveau d’autorisation demandé est déjà fourni ou refusé par l’utilisateur de l’application ou en cas de rétrogradation de l’autorisation `ACPPlacesRequestAuthorizationLevelAlways` vers `ACPPlacesRequestAuthorizationLevelWhenInUse` l’autorisation, cette méthode n’a aucun effet.

Le niveau d’autorisation peut être défini sur l’une des valeurs suivantes :

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   Demande à l’utilisateur l’autorisation d’utiliser le service Places pendant que l’application est en cours d’utilisation. L’invite de l’utilisateur contient le texte de la `NSLocationWhenInUseUsageDescription` clé dans le fichier Info.plist de votre application, et la présence de cette clé est requise lors de l’appel de cette méthode. Pour plus d’informations, consultez la documentation [Apple sur requestWhenInUseAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization).

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   Utilisez cet énumérateur pour demander Places Service même lorsque l’application est en arrière-plan. Vous devez avoir les clés `NSLocationAlwaysUsageDescription` et `NSLocationWhenInUseUsageDescription` les clés dans Info.plist de votre application. Ces touches définissent le texte qui apparaîtra à l’invite de l’utilisateur. Pour plus d’informations, consultez la documentation [Apple sur requestAlwaysAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization).

`ACPPlacesRequestAuthorizationLevelAlways` est la valeur d’autorisation de requête par défaut.

>[!IMPORTANT]
>
>L’application qui a autorisé l’utilisation de l’ `ACPPlacesRequestAuthorizationLevelWhenInUse` autorisation ne déclenchera pas d’événements d’entrée/sortie dans les régions qui se produisent en arrière-plan.

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel;
```

#### Exemple

Pour demander l&#39; `ACPPlacesRequestAuthorizationLevelWhenInUse` autorisation :

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

Pour mettre à niveau vers `ACPPlacesRequestAuthorizationLevelAlways` l’autorisation :

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways];
```

## Mode de surveillance (iOS uniquement)

La surveillance peut être définie sur l’une des valeurs suivantes :

* `ACPPlacesMonitorModeContinuous`

   L’extension de surveillance reçoit et traite les emplacements plus fréquemment. Cette stratégie de surveillance consomme beaucoup de puissance, mais offre une précision accrue. Pour plus d’informations, voir la documentation [Apple sur la surveillance](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation)continue.

* `ACPPlacesMonitorModeSignificantChanges`

   L’extension de surveillance ne reçoit et traite les mises à jour de l’emplacement qu’une fois que le périphérique a déplacé une distance importante de l’emplacement précédemment traité. Cette stratégie de surveillance consomme moins de puissance que la stratégie de surveillance continue. Pour plus d’informations, reportez-vous à la documentation [Apple sur la surveillance importante](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode (iOS)

Voici la syntaxe et l’exemple de code pour cette API :

#### Syntaxe

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### Exemple

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
