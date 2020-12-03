---
title: Place la référence à l'API
description: Informations sur les références à l'API dans Lieux.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 32%

---


# Place la référence à l&#39;API {#places-api-reference}

Voici des informations sur les références d&#39;API dans l&#39;extension Places :

## Traitement d’un événement de région

Lorsqu’un appareil dépasse l’une des limites de la région du service Places prédéfinies de votre application, la région et le type d&#39;événement sont transmis au SDK pour traitement.

### ProcessGeofence (Android)

Traitez un événement de `Geofence` région pour le `transitionType`produit fourni.

Passe le `transitionType` de `GeofencingEvent.getGeofenceTransition()`. Actuellement `Geofence.GEOFENCE_TRANSITION_ENTER` et `Geofence.GEOFENCE_TRANSITION_EXIT` sont pris en charge.

**Syntaxe**

Voici la syntaxe de cette méthode :

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Exemple**

Appelez cette méthode dans votre `IntentService` application qui est enregistrée pour la réception de événements de géofence Android.

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

Cette méthode doit être appelée dans le `CLLocationManager` délégué, ce qui indique si l&#39;utilisateur est entré ou a quitté une région spécifique.

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

Traitez tout `Geofences` en `GeofencingEvent` même temps.

**Syntaxe**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Exemple**

Appelez cette méthode dans votre `IntentService` application qui est enregistrée pour la réception de événements de géofence Android.

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

## Récupérer les points d&#39;intérêt voisins

Renvoie une liste ordonnée des points d’intérêt voisins dans un rappel. Une version surchargée de cette méthode renvoie un code d&#39;erreur si un problème s&#39;est produit avec l&#39;appel réseau résultant.

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

## Récupérer les points ciblés actuels du périphérique

Demande une liste de points d’intérêt dans lesquels le périphérique est actuellement connu et les renvoie dans un rappel.

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


## Obtenir l&#39;emplacement du périphérique

Demande l’emplacement du périphérique, comme on l’a déjà appelé, par l’extension Places.

>[!TIP]
>
>L&#39;extension Places ne connaît que les emplacements qui lui ont été fournis par le biais d&#39;appels à `GetNearbyPointsOfInterest`.


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


### Clear (Android)

Efface les données côté client pour l&#39;extension Places dans l&#39;état partagé, l&#39;enregistrement local et en mémoire.

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

Efface les données côté client pour l&#39;extension Places dans l&#39;état partagé, l&#39;enregistrement local et en mémoire.

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

## Définir l&#39;état d&#39;autorisation de l&#39;emplacement

### setAuthorizationStatus (Android)

*Disponible à partir de Places v1.4.0*

Définit l’état d’autorisation dans l’extension Places.

L’état fourni est stocké dans l’état partagé Places et n’est utilisé que pour référence.
L&#39;appel de cette méthode n&#39;a aucune incidence sur l&#39;état réel d&#39;autorisation d&#39;emplacement pour ce périphérique.

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

L’état fourni est stocké dans l’état partagé Places et n’est utilisé que pour référence.
L&#39;appel de cette méthode n&#39;a aucune incidence sur l&#39;état réel d&#39;autorisation d&#39;emplacement pour ce périphérique.

Lorsque l&#39;état d&#39;autorisation du périphérique change, la `locationManager:didChangeAuthorizationStatus:` méthode de votre `CLLocationManagerDelegate` périphérique est appelée. Dans cette méthode, vous devez transmettre la nouvelle `CLAuthorizationStatus` valeur à l’ `setAuthorizationStatus:` API ACPPlaces.

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
