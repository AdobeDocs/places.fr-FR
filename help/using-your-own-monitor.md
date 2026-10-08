---
title: Utilisation de votre propre moniteur
description: Vous pouvez également utiliser vos services de surveillance et intégrer Places Service à l’aide des API d’extension de Places Service.
exl-id: 8ca4d19b-0f23-4291-b335-af47f03179fa
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%
---
# Utilisation de votre propre moniteur {#using-your-monitor}

Vous pouvez également utiliser vos services de surveillance et intégrer Places Service à l’aide des API de l’extension Places.

## Enregistrement de géorepères

Si vous décidez d&#39;utiliser vos services de surveillance, enregistrez les clôtures géographiques des points d&#39;intérêt à proximité de votre emplacement actuel en procédant comme suit :

### iOS

Dans iOS, procédez comme suit :

1. Transmettez les mises à jour de localisation obtenues à partir des services de localisation principaux d’iOS à l’extension Places.

1. Utilisez l’API d’extension `getNearbyPointsOfInterest` Places pour obtenir le tableau d’objets `ACPPlacesPoi` autour de l’emplacement actuel.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Extrayez les informations des objets `ACPPlacesPOI` obtenus et commencez à surveiller ces points d’intérêt.

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

1. Utilisez l’API de l’extension `getNearbyPointsOfInterest` Places pour obtenir la liste des objets `PlacesPoi` autour de l’emplacement actuel.

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

1. Extrayez les données des objets `PlacesPOI` obtenus et commencez à surveiller ces points d’intérêt.

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


L’appel à l’API `getNearbyPointsOfInterest` génère un appel réseau qui récupère l’emplacement autour de l’emplacement actuel.

>[!IMPORTANT]
>
>Vous devez appeler l’API avec parcimonie ou uniquement en cas de changement d’emplacement significatif de l’utilisateur.

## Publication des événements de limite géographique

### iOS

Dans iOS, appelez l’API `processGeofenceEvent` Places dans le délégué `CLLocationManager`. Cette API vous informe si l’utilisateur est entré ou sorti d’une zone géographique spécifique.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

Dans Android, appelez la méthode `processGeofence` avec l’événement de transition approprié dans votre récepteur de diffusion Geofence. Vous pouvez traiter la liste des limites géographiques reçues pour empêcher les entrées/sorties en double.

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
