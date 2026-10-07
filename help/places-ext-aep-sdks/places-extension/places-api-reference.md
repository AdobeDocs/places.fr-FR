---
title: Référence de l’API Places
description: Informations sur les références d’API dans Places.
feature: Mobile SDK
exl-id: ce1a113c-dee0-49df-8d2f-789ccc1c8322
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a8a79b8d-fdca-499c-a5ef-f88a099d8eb9
    internal-label: Mobile SDK
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 32%
---
# Référence de l’API Places {#places-api-reference}

Voici des informations sur les références d’API dans l’extension Places :

## Traitement d’un événement de région

Lorsqu’un appareil dépasse l’une des limites de zone géographique prédéfinies du service Places de votre application, la zone géographique et le type d’événement sont transmis au SDK pour traitement.

### ProcessGeofence (Android)

Traitez un événement de région `Geofence` pour le `transitionType` fourni.

Transmettez le `transitionType` à partir de `GeofencingEvent.getGeofenceTransition()`. Actuellement, `Geofence.GEOFENCE_TRANSITION_ENTER` et `Geofence.GEOFENCE_TRANSITION_EXIT` sont pris en charge.

**Syntaxe**

Voici la syntaxe de cette méthode :

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Exemple**

Appelez cette méthode dans votre `IntentService` enregistré pour la réception d’événements de limite géographique Android.

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

Cette méthode doit être appelée dans le délégué `CLLocationManager`, qui indique si l’utilisateur est entré ou sorti d’une région spécifique.

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

### ProcessGeofencingEvent (Android)

Traitez tous les `Geofences` du `GeofencingEvent` en même temps.

**Syntaxe**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Exemple**

Appelez cette méthode dans votre `IntentService` enregistré pour la réception d’événements de limite géographique Android

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

## Récupérer les points d’intérêt à proximité

Renvoie une liste ordonnée de points d’intérêt à proximité dans un rappel. Une version surchargée de cette méthode renvoie un code d’erreur si un problème est survenu avec l’appel réseau résultant.

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

## Récupérer les points ciblés actuels de l’appareil

Demande une liste des points d’intérêt dans lesquels l’appareil se trouve actuellement et les renvoie dans un rappel.

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


## Obtenir l’emplacement de l’appareil

Demande l&#39;emplacement de l&#39;appareil, comme connu précédemment, par l&#39;extension Places.

>[!TIP]
>
>L’extension Places ne connaît que les emplacements qui lui ont été fournis via des appels à `GetNearbyPointsOfInterest`.


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

## Effacer les données côté client


### Effacer (Android)

Efface les données côté client pour l’extension Places à l’état partagé, au stockage local et en mémoire.

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

### effacer (iOS)

Efface les données côté client pour l’extension Places en statut partagé, en stockage local et en mémoire.

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

## Définir le statut d’autorisation de l’emplacement

### setAuthorizationStatus (Android)

*Disponible à partir de Places v1.4.0*

Définit le statut d’autorisation dans l’extension Places.

Le statut fourni est stocké dans l&#39;état Places partagées et est fourni à titre de référence uniquement.
L’appel de cette méthode n’a aucune incidence sur le statut d’autorisation d’emplacement réel de cet appareil.

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

Définit le statut d’autorisation dans l’extension Places.

Le statut fourni est stocké dans l&#39;état Places partagées et est fourni à titre de référence uniquement.
L’appel de cette méthode n’a aucune incidence sur le statut d’autorisation d’emplacement réel de cet appareil.

Lorsque le statut d’autorisation de l’appareil change, la méthode `locationManager:didChangeAuthorizationStatus:` de votre `CLLocationManagerDelegate` est appelée. À partir de cette méthode, vous devez transmettre la nouvelle valeur `CLAuthorizationStatus` à l’API ACPPlaces `setAuthorizationStatus:`.

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
