---
title: Référence de l’API Places
description: Informations sur les références d’API dans Places.
exl-id: ce1a113c-dee0-49df-8d2f-789ccc1c8322
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 32%

---

# Référence de l’API Places {#places-api-reference}

Voici des informations sur les références d’API dans l’extension Places :

## Traitement d’un événement de région

Lorsqu’un appareil dépasse l’une des limites de région du service Places prédéfinies de votre application, la région et le type d’événement sont transmis au SDK pour traitement.

### ProcessGeofence (Android)

Traitement d’une `Geofence` événement de région pour le fourni `transitionType`.

Transmettez la variable `transitionType` de `GeofencingEvent.getGeofenceTransition()`. Actuellement `Geofence.GEOFENCE_TRANSITION_ENTER` et `Geofence.GEOFENCE_TRANSITION_EXIT` sont prises en charge.

**Syntaxe**

Voici la syntaxe de cette méthode :

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Exemple**

Appelez cette méthode dans votre `IntentService` qui est enregistré pour recevoir les événements de géo-barrière Android.

Voici un exemple de code pour cette méthode :

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);

        List<Geofence> geofences = geofencingEvent.getTriggeringGeofences();

        if (geofences.size() > 0) {
          // Call the Places API to process information
          Places.processGeofence(geofences.get(0), geofencingEvent.getGeofenceTransition());
        }
    }
}
```

### ProcessRegionEvent (iOS)

Cette méthode doit être appelée dans la variable `CLLocationManager` délégué, qui indique si l’utilisateur est entré dans une région spécifique ou s’il l’a quitté.

**Syntaxe**

Voici la syntaxe de cette méthode :

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**Exemple**

Voici l’exemple de code pour cette méthode :


```objectivec
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### ProcessGeofizingEvent (Android)

Traiter tout `Geofences` dans le `GeofencingEvent` en même temps.

**Syntaxe**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Exemple**

Appelez cette méthode dans votre `IntentService` qui est enregistré pour la réception d’événements de géolocalisation Android

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);
        // Call the Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## Récupération des points ciblés proches

Renvoie une liste classée des points ciblés proches dans un rappel. Une version surchargée de cette méthode renvoie un code d’erreur si un problème s’est produit avec l’appel réseau obtenu.

### GetNearbyPointsOfInterest (Android)

Voici la syntaxe de cette méthode :

**Syntaxe**

```java
public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback);

public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback,
                                             final AdobeCallback<PlacesRequestError> errorCallback);
```

**Exemple**

Voici l’exemple de code pour cette méthode :

```java
// getNearbyPointsOfInterest without an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});

// getNearbyPointsOfInterest with an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10,
    new AdobeCallback<List<PlacesPOI>>() {
        @Override
        public void call(List<PlacesPOI> pois) {
            // do required processing with the returned nearbyPoi array
            startMonitoringPois(pois);
        }
    }, new AdobeCallback<PlacesRequestError>() {
        @Override
        public void call(PlacesRequestError placesRequestError) {
            // look for the placesRequestError and handle the error accordingly
            handleError(placesRequestError);
        }
    }
);
```

### GetNearbyPointsOfInterest (iOS)

**Syntaxe**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;

+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback
                     errorCallback: (nullable void (^) (ACPPlacesRequestError result)) errorCallback;
```

**Exemple**

```objectivec
// getNearbyPointsOfInterest without an error callback
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];

// getNearbyPointsOfInterest with an error callback
[ACPPlaces getNearbyPointsOfInterest:location limit:10
    callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // do required processing with the returned nearbyPoi array
        [self startMonitoringPois:nearbyPOI];
    } errorCallback:^(ACPPlacesRequestError result) {
        // look for the error and handle accordingly
        [self handleError:result];
    }
];
```

## Récupération des points ciblés actuels de l’appareil

Demande une liste des points ciblés dans lesquels l’appareil est actuellement connu et les renvoie dans un rappel.

### GetCurrentPointsOfInterest (Android)

Voici la syntaxe de cette méthode :

**Syntaxe**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**Exemple**

Voici l’exemple de code pour cette méthode :

```java
Places.getCurrentPointsOfInterest(new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // use the obtained POIs that the device is within
        processUserWithinPois(pois);        
    }
});
```

### GetCurrentPointsOfInterest (iOS)

**Syntaxe**

Voici la syntaxe de cette méthode :

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**Exemple**

Voici l’exemple de code pour cette méthode :

```objectivec
[ACPPlaces getCurrentPointsOfInterest:^(NSArray<ACPPlacesPoi*>* userWithinPoi) {
    // do required processing with the returned userWithinPoi array
    [self processUserWithinPois:userWithinPoi];
}];
```


## Obtention de l’emplacement de l’appareil

Demande l’emplacement de l’appareil, comme précédemment connu, par l’extension Places.

>[!TIP]
>
>L’extension Places ne connaît que les emplacements qui lui ont été fournis via des appels vers `GetNearbyPointsOfInterest`.


### GetLastKnownLocation (Android)

**Syntaxe**

Voici la syntaxe de cette méthode :

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**Exemple**

Voici l’exemple de code pour cette méthode :

```java
Places.getLastKnownLocation(new AdobeCallback<Location>() {
    @Override
    public void call(Location lastLocation) {
        // do something with the last known location
        processLastKnownLocation(lastLocation);        
    }
});
```

### GetLastKnownLocation (iOS)

**Syntaxe**

Voici la syntaxe de cette méthode :

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**Exemple**

Voici l’exemple de code pour cette méthode :

```objectivec
[ACPPlaces getLastKnownLocation:^(CLLocation* lastLocation) {
    // do something with the last known location
    [self processLastKnownLocation:lastLocation];
}];
```

## Effacement des données côté client


### Effacer (Android)

Efface les données côté client de l’extension Places dans l’état partagé, le stockage local et en mémoire.

**Syntaxe**

Voici la syntaxe de cette méthode :

```java
public static void clear();
```

**Exemple**

Voici l’exemple de code pour cette méthode :

```java
Places.clear();
```

### clear (iOS)

Efface les données côté client de l’extension Places dans l’état partagé, le stockage local et en mémoire.

**Syntaxe**

Voici la syntaxe de cette méthode :

```objectivec
+ (void) clear;
```

**Exemple**

Voici l’exemple de code pour cette méthode :

```objectivec
[ACPPlaces clear];
```

## Définition de l’état d’autorisation de l’emplacement

### setAuthorizationStatus (Android)

*Disponible à partir de Places v1.4.0*

Définit l’état d’autorisation dans l’extension Places.

L’état fourni est stocké à l’état Partages Places et est à titre de référence uniquement.
L’appel de cette méthode n’a aucune incidence sur l’état d’autorisation de l’emplacement réel de cet appareil.

**Syntaxe**

Voici la syntaxe de cette méthode :

```java
public static void setAuthorizationStatus(final PlacesAuthorizationStatus status);
```

**Exemple**

Voici l’exemple de code pour cette méthode :

```java
Places.setAuthorizationStatus(PlacesAuthorizationStatus.ALWAYS);
```

### setAuthorizationStatus (iOS)

*Disponible à partir de ACPPlaces v1.3.0*

Définit l’état d’autorisation dans l’extension Places.

L’état fourni est stocké à l’état Partages Places et est à titre de référence uniquement.
L’appel de cette méthode n’a aucune incidence sur l’état d’autorisation de l’emplacement réel de cet appareil.

Lorsque l’état d’autorisation du périphérique change, la variable `locationManager:didChangeAuthorizationStatus:` de votre `CLLocationManagerDelegate` est appelée. À partir de cette méthode, vous devez transmettre la nouvelle variable `CLAuthorizationStatus` à ACPPlaces `setAuthorizationStatus:` API.

**Syntaxe**

Voici la syntaxe de cette méthode :

```objectivec
+ (void) setAuthorizationStatus: (CLAuthorizationStatus) status;
```

**Exemple**

Voici l’exemple de code pour cette méthode :

```objectivec
- (void) locationManager: (CLLocationManager*) manager didChangeAuthorizationStatus: (CLAuthorizationStatus) status {    
    [ACPPlaces setAuthorizationStatus:status];
}
```
