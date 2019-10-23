---
title: Référence de l’API Places
seo-title: Référence de l’API Places
description: Informations sur les références API dans Places.
seo-description: Informations sur les références API dans Places.
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# Référence de l’API Places {#places-api-reference}

Voici des informations sur les références API dans Places :

## Traitement d’un événement de région

Lorsqu’un périphérique franchit l’une des limites de région Places prédéfinies de votre application, la région et le type d’événement sont transmis au SDK en vue de leur traitement.

### ProcessGeofence (Android)

Traitez un événement de `Geofence` région pour le paramètre fourni `transitionType`.

Passez le `transitionType` de `GeofencingEvent.getGeofenceTransition()`. Actuellement `Geofence.GEOFENCE_TRANSITION_ENTER` et `Geofence.GEOFENCE_TRANSITION_EXIT` sont pris en charge.

**Syntaxe**

Voici la syntaxe de cette méthode :

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Exemple**

Appelez cette méthode dans votre `IntentService` qui est enregistrée pour recevoir des événements de géofence Android.

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
          // Call Adobe Places API to process information
          Places.processGeofence(geofences.get(0), geofencingEvent.getGeofenceTransition());
        }
    }
}
```

### ProcessRegionEvent (iOS)

Cette méthode doit être appelée dans le `CLLocationManager` délégué, ce qui indique si l’utilisateur est entré ou a quitté une région spécifique.

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

### ProcessGeofenceEvent (Android)

Traitez tout `Geofences` en même temps `GeofencingEvent` .

**Syntaxe**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Exemple**

Appelez cette méthode dans votre `IntentService` qui est enregistré pour recevoir des événements de géofence Android.

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);
        // Call Adobe Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## Récupérez les points d'intérêt voisins

Renvoie une liste ordonnée des points d’intérêt voisins dans un rappel.

### GetNearbyPointsOfInterest (Android)

Voici la syntaxe de cette méthode :

**Syntaxe**

```java
public static void getNearbyPointsOfInterest(final Location location,
    final int limit, final AdobeCallback<List<PlacesPOI>> callback);
```

**Exemple**

Voici l’exemple de code pour cette méthode :

```java
Places.getNearbyPlaces(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});
```

### GetNearbyPointsOfInterest (iOS)

**Syntaxe**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;
```

**Exemple**

```objectivec
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];
```

## Récupérer les points ciblés actuels du périphérique

Demande une liste des points d’intérêt dans lesquels le périphérique est actuellement connu et les renvoie dans un rappel.

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


## Obtention de l’emplacement du périphérique

Demande l’emplacement du périphérique, tel que précédemment connu, par l’extension Places.

>[!TIP]
>
>L’extension Places ne connaît que les emplacements qui lui ont été fournis par le biais d’appels à `GetNearbyPointsOfInterest`.


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


### Clear (Android)

Efface les données côté client pour les emplacements dans l’état partagé, le stockage local et en mémoire.

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

Efface les données côté client pour les emplacements dans l’état partagé, le stockage local et en mémoire.

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
