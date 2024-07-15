---
title: Utilisation de votre propre moniteur
description: Vous pouvez également utiliser vos services de surveillance et intégrer avec Places Service en utilisant les API d'extension de Places Service.
exl-id: 8ca4d19b-0f23-4291-b335-af47f03179fa
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---

# Utilisation de votre propre moniteur {#using-your-monitor}

Vous pouvez également utiliser vos services de surveillance et intégrer avec Places Service en utilisant les API de l&#39;extension Places.

## Enregistrement de clôtures géographiques

Si vous décidez d’utiliser vos services de surveillance, enregistrez les clôtures virtuelles des points ciblés autour de votre emplacement actuel en procédant comme suit :

### iOS

Dans iOS, procédez comme suit :

1. Transmettez les mises à jour d’emplacement obtenues à partir des services de l’emplacement principal d’iOS à l’extension Places.

1. Utilisez l’API d’extension `getNearbyPointsOfInterest` Places pour obtenir le tableau d’objets `ACPPlacesPoi` autour de l’emplacement actuel.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Extrayez les informations des objets `ACPPlacesPOI` obtenus et commencez à surveiller ces points ciblés.

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center
                                                                                 radius:currentRegion.radius
                                                                             identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
       }
   }
   ```

### Android

1. Transmettez les mises à jour d’emplacement obtenues à partir des services Google Play ou des services d’emplacement Android à l’extension Places.

1. Utilisez l’API d’extension `getNearbyPointsOfInterest` Places pour obtenir la liste des objets `PlacesPoi` autour de l’emplacement actuel.

   ```java
   LocationCallback callback = new LocationCallback() {
       @Override
       public void onLocationResult(LocationResult locationResult) {
           super.onLocationResult(locationResult);
   
           Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois) {
                   starMonitoringGeofence(pois);
               }
           });
       }
   };
   ```

1. Extrayez les données des objets `PlacesPOI` obtenus et commencez à surveiller ces points ciblés.

   ```java
   private void startMonitoringFences(final List<PlacesPOI> nearByPOIs) {
       // check for location permission
       for (PlacesPOI poi : nearByPOIs) {
           final Geofence fence = new Geofence.Builder()
               .setRequestId(poi.getIdentifier())
               .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
               .setExpirationDuration(Geofence.NEVER_EXPIRE)
               .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER |
                                   Geofence.GEOFENCE_TRANSITION_EXIT)
               .build();
           geofences.add(fence);
       }
   
       GeofencingRequest.Builder builder = new GeofencingRequest.Builder();
       builder.setInitialTrigger(GeofencingRequest.INITIAL_TRIGGER_ENTER);
       builder.addGeofences(geofences);
       builder.build();
       geofencingClient.addGeofences(builder.build(), geoFencePendingIntent)
   }
   ```


L’appel de l’API `getNearbyPointsOfInterest` entraîne un appel réseau qui obtient l’emplacement autour de l’emplacement actuel.

>[!IMPORTANT]
>
>Vous devez appeler l’API avec parcimonie ou uniquement en cas de modification significative de l’emplacement de l’utilisateur.

## Publication d’événements de géolocalisation

### iOS

Dans iOS, appelez l’API Places `processGeofenceEvent` dans le délégué `CLLocationManager`. Cette API vous indique si l’utilisateur est entré dans une région spécifique ou s’il l’a quitté.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

Dans Android, appelez la méthode `processGeofence` avec l’événement de transition approprié dans votre récepteur de diffusion Geofence. Vous pouvez organiser la liste des clôtures virtuelles reçues pour éviter les entrées/sorties en double.

```java
void onGeofenceReceived(final Intent intent) {
    // do appropriate validation steps for the intent
    ...

    // get GeofencingEvent from intent
    GeofencingEvent geoEvent = GeofencingEvent.fromIntent(intent);

    // get the transition type (entry or exit)
    int transitionType = geoEvent.getGeofenceTransition();

    // validate your geoEvent and get the necessary Geofences from the list
    List<Geofence> myGeofences = geoEvent.getTriggeringGeofences();

    // process region events for your geofences
    for (Geofence geofence : myGeofences) {
        Places.processGeofence(geofence, transitionType);
    }
}
```
