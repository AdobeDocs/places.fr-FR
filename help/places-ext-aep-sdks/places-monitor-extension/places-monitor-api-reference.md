---
title: Référence à l'API d'analyse des lieux
description: Liste des API pour le moniteur de lieux.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 2%

---


# Place la référence de l&#39;API Monitor {#places-api-reference}

## Enregistrer l&#39;extension du moniteur de lieux

Enregistre l&#39;extension Places Monitor dans le Core Événement Hub.

### RegisterExtension (Android)

Voici la syntaxe et l’exemple de code de cette API :

#### Syntaxe

Voici la syntaxe de Java :

```java
public static void registerExtension();
```

#### Exemple

Appelez cette méthode dans la méthode `onCreate` où vous initialisez le reste du SDK Experience Platform.

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

Voici la syntaxe et l’exemple de code de cette API :

#### Syntaxe

Voici la syntaxe de Objective-C :

```objective-c
+ (void) registerExtension;
```

#### Exemple

Cette méthode doit être appelée dans la méthode déléguée `didFinishLaunchingWithOptions` de `AppDelegate`.

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

## Version de l’extension

Renvoie la version actuelle de l’extension Places Monitor

### ExtensionVersion (Android)

Voici la syntaxe et l’exemple de code de cette API :

#### Syntaxe

```java
public static String extensionVersion();
```

#### Exemple

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion (iOS)

Voici la syntaxe et l’exemple de code de cette API :

#### Syntaxe

```objective-c
+ (nonnull NSString*) extensionVersion;
```

#### Exemple

```objective-c
NSString *placesMonitorVersion = [ACPPlacesMonitor extensionVersion];
```

## Surveillance des dispositifs de début

Commencez à suivre l&#39;emplacement du périphérique et à surveiller les emplacements voisins.

### Début (Android)

Si l&#39;utilisateur n&#39;a pas accordé l&#39;autorisation d&#39;utiliser l&#39;emplacement du périphérique, le premier appel à l&#39;API `start` invite l&#39;utilisateur à l&#39;autoriser.

Voici la syntaxe et l’exemple de code de cette API :

#### Syntaxe

```java
public static void start();
```

#### Exemple

```java
PlacesMonitor.start();
```

### Début (iOS)

>[!IMPORTANT]
>
>Pour commencer la surveillance, le service de localisation doit avoir l’autorisation nécessaire :
>
>* Si l&#39;autorisation du service Places n&#39;a pas été fournie à l&#39;application, le premier appel à l&#39;API `start` demande l&#39;autorisation d&#39;utiliser le service Places tel que configuré pour l&#39;application.
>* Selon les capacités de votre périphérique, si l&#39;autorisation a été fournie, le moniteur des lieux effectue le suivi de l&#39;emplacement de l&#39;utilisateur en fonction de l&#39;emplacement actuellement défini `ACPPlacesMonitorMode`. Par défaut, le moniteur utilise `ACPPlacesMonitorModeSignificantChanges`.


>[!CAUTION]
>
>Si votre appel à la surveillance des débuts est effectué avant l’initialisation du SDK, il est possible qu’il soit ignoré.

Vous pouvez vous assurer que l’initialisation du SDK est terminée en appelant `start` à partir du rappel fourni à `ACPCore::start:`.

Voici la syntaxe et l’exemple de code de cette API :

#### Syntaxe

```objectivec
+ (void) start;
```

#### Exemple

Démarrage du moniteur des emplacements lors de l’initialisation du SDK :

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

Démarrage de Places Monitor ultérieurement lors de l’exécution de l’application :

```objective-c
[ACPPlacesMonitor start];
```

## Arrêt de la surveillance du périphérique

Arrête le suivi de l&#39;emplacement du périphérique.

### Arrêt (Android)

Voici la syntaxe et l’exemple de code de cette API :

#### Syntaxe

```java
public static void stop();
```

#### Exemple

```java
PlacesMonitor.stop();
```

### Arrêt (iOS)

Voici la syntaxe et l’exemple de code de cette API :

#### Syntaxe

```objectivec
+ (void) stop;
```

#### Exemple

```objective-c
[ACPPlacesMonitor stop];
```

## Emplacement de mise à jour

Utilisez cette API pour effectuer une mise à jour immédiate de l’emplacement du périphérique. Lorsque vous appelez cette API, le périphérique tente de déterminer l’emplacement avec le niveau de précision que vous avez spécifié. Ce processus actualise également les points d’intérêt voisins qui sont surveillés par l’extension.

### UpdateLocation (Android)

Voici la syntaxe et l’exemple de code de cette API :

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

Vous pouvez utiliser cette API pour définir le type d’autorisation d’emplacement que l’utilisateur est invité à utiliser et autorisé à utiliser pour le service Places.

### SetLocationPermission (Android)

Cette API définit le type de demande d&#39;autorisation d&#39;emplacement pour laquelle l&#39;utilisateur est invité à sélectionner.

>[!TIP]
>
>Cette API n’est efficace que pour les périphériques fonctionnant sous Android 10 et versions ultérieures.
>
>Pour définir l&#39;invite d&#39;autorisation appropriée à afficher à l&#39;utilisateur, appelez cette API avant le `PlacesMonitor.start()`. L’appel de cette méthode, tout en surveillant activement, met à niveau le niveau d’autorisation d’emplacement vers la valeur d’autorisation demandée. Si le niveau d&#39;autorisation demandé est déjà fourni ou refusé par l&#39;utilisateur de l&#39;application, ou si vous tentez de réduire l&#39;autorisation de `ALWAYS_ALLOW` à `WHILE_USING_APP`, cette méthode n&#39;a aucun effet.

L’autorisation d’emplacement peut être définie sur l’une des valeurs suivantes :

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   Cette valeur invite l’utilisateur à accéder à l’emplacement du périphérique uniquement lors de l’utilisation de l’application. Une application est considérée comme étant en cours d’utilisation lorsque l’utilisateur consulte l’application sur l’écran de son appareil, par exemple lorsqu’une activité s’exécute au premier plan.

   >[!TIP]
   >
   >Assurez-vous que l&#39;autorisation d&#39;utilisateur ACCESS_FINE_LOCATION est définie dans le fichier manifeste de l&#39;application.

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   Cette valeur invite l’utilisateur à accéder à l’emplacement du périphérique, même lorsque l’application est en arrière-plan.

   >[!TIP]
   >
   >Assurez-vous que les autorisations d’utilisateur ACCESS_BACKGROUND_LOCATION et ACCESS_FINE_LOCATION sont définies dans le fichier de manifeste de l’application.

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` est la valeur d’autorisation d’emplacement par défaut.

>[!IMPORTANT]
>
>Si l’utilisateur de l’application se voit accorder l’autorisation `WHILE_USING_APP`, les géoinfractions ne seront pas enregistrées auprès du système d’exploitation. Par conséquent, l&#39;extension Surveillance des lieux ne déclenchera pas de événements d&#39;entrée/sortie sur les régions qui se trouvent en arrière-plan.

Voici la syntaxe et l’exemple de code de cette API :

#### Syntaxe

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### Exemple

Pour demander l&#39;autorisation `WHILE_USING_APP` :

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

Pour mettre à niveau vers l&#39;autorisation `ALWAYS_ALLOW` :

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel (iOS)

Cette API définit le type de demande d&#39;autorisation d&#39;emplacement pour laquelle l&#39;utilisateur sera invité à répondre.

Pour définir l&#39;invite d&#39;autorisation appropriée à afficher à l&#39;utilisateur, appelez `SetRequestAuthorizationLevel` avant d&#39;appeler `[ACPPlacesMonitor start]`. Pour définir l&#39;invite d&#39;autorisation appropriée à afficher à l&#39;utilisateur, appelez cette API avant le `[ACPPlacesMonitor start]`. L&#39;appel de cette méthode pendant la surveillance active mettra à niveau le niveau d&#39;autorisation de l&#39;emplacement vers la valeur d&#39;autorisation demandée. Si le niveau d&#39;autorisation demandé est déjà fourni ou refusé par l&#39;utilisateur de l&#39;application ou s&#39;il existe une dégradation de l&#39;autorisation de `ACPPlacesRequestAuthorizationLevelAlways` à `ACPPlacesRequestAuthorizationLevelWhenInUse`, cette méthode n&#39;a aucun effet.

Le niveau d’autorisation peut être défini sur l’une des valeurs suivantes :

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   Demande à l’utilisateur l’autorisation d’utiliser le service Places pendant que l’application est en cours d’utilisation. L’invite utilisateur contient le texte de la clé `NSLocationWhenInUseUsageDescription` dans votre fichier Info.plist d’application et la présence de cette clé est requise lors de l’appel de cette méthode. Pour plus d&#39;informations, consultez la [documentation Apple sur requestWhenInUseAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization).

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   Utilisez cet énumération pour demander Places Service même si l’application est en arrière-plan. Vous devez disposer des clés `NSLocationAlwaysUsageDescription` et `NSLocationWhenInUseUsageDescription` dans la liste Info.plist de votre application. Ces clés définissent le texte qui apparaîtra à l’invite de l’utilisateur. Pour plus d’informations, consultez la [documentation Apple sur requestAlwaysAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization).

`ACPPlacesRequestAuthorizationLevelAlways` est la valeur d’autorisation de requête par défaut.

>[!IMPORTANT]
>
>L&#39;application qui a autorisé l&#39;utilisation de l&#39;autorisation `ACPPlacesRequestAuthorizationLevelWhenInUse` ne déclenchera pas de événements d&#39;entrée/sortie dans les régions qui se trouvent en arrière-plan.

Voici la syntaxe et l’exemple de code de cette API :

#### Syntaxe

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel;
```

#### Exemple

Pour demander l&#39;autorisation `ACPPlacesRequestAuthorizationLevelWhenInUse` :

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

Pour mettre à niveau l&#39;autorisation `ACPPlacesRequestAuthorizationLevelAlways` :

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways];
```

## Mode de surveillance (iOS uniquement)

La surveillance peut être définie sur l’une des valeurs suivantes :

* `ACPPlacesMonitorModeContinuous`

   L&#39;extension de surveillance reçoit et traite les emplacements plus fréquemment. Cette stratégie de surveillance consomme beaucoup de puissance mais offre une précision accrue. Pour plus d’informations, voir la [documentation Apple sur la surveillance continue](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation).

* `ACPPlacesMonitorModeSignificantChanges`

   L&#39;extension de surveillance ne reçoit et traite les mises à jour de l&#39;emplacement qu&#39;une fois que le périphérique a déplacé une distance importante de l&#39;emplacement précédemment traité. Cette stratégie de surveillance consomme moins de puissance que la stratégie de surveillance continue. Pour plus d’informations, voir la [documentation Apple sur la surveillance importante](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode (iOS)

Voici la syntaxe et l’exemple de code de cette API :

#### Syntaxe

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### Exemple

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
