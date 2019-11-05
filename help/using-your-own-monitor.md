---
title: Utilisation de votre propre moniteur
seo-title: Utilisation de votre propre moniteur
description: Vous pouvez également utiliser vos services de surveillance et vous intégrer à Places à l’aide des API d’extension Places.
seo-description: Vous pouvez également utiliser vos services de surveillance et vous intégrer à Places à l’aide des API d’extension Places.
translation-type: tm+mt
source-git-commit: 95dd010db8a860ebf489d04c7a70ec9cda8b3fb1

---


# Utilisation de votre propre moniteur {#using-your-monitor}

Vous pouvez également utiliser vos services de surveillance et vous intégrer à Places à l’aide des API d’extension Places.

## Enregistrement des références géographiques

Si vous décidez d’utiliser vos services de surveillance, enregistrez les caractéristiques géographiques des points d’intérêt autour de votre emplacement actuel en procédant comme suit :

### iOS

Sous iOS, procédez comme suit :

1. Transmettez les mises à jour d’emplacement obtenues des services d’emplacement principaux d’iOS à l’extension Places.

1. Utilisez l’API `getNearbyPointsOfInterest` d’extension Places pour obtenir le tableau des *n* `ACPPlacesPoi` objets autour de l’emplacement actuel.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Extrayez les informations des `ACPPlacesPOI` objets obtenus et commencez à surveiller ces points d’intérêt.

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center                                                                                                                              radius:currentRegion.radius                                                                                                                    identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
   
       }
   }
   ```

### Android

1. Transmettez les mises à jour d’emplacement obtenues des services Google Play ou Android aux services d’emplacement Places Extension.

1. Utilisez l’API `getNearbyPointsOfInterest` Places Extension pour obtenir la liste des n objets `PlacesPoi` autour de l’emplacement actuel.

   ```java
       LocationCallback callback = new LocationCallback() {
               @Override
               public void onLocationResult(LocationResult locationResult) {
                   super.onLocationResult(locationResult);
   
                   Places.getNearbyPointsOfInterest(currentLocation, 10, new            AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois)
                   starMonitoringGeofence(pois);
               }
           });
   
               }
           };
   ```

1. Extrayez les données des `PlacesPOI` objets obtenus et commencez à surveiller ces points d’intérêt.

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


L’appel de l’ `getNearbyPointsOfInterest` API génère un appel réseau qui obtient l’emplacement autour de l’emplacement actuel.

>[!IMPORTANT]
>
>Vous devez appeler l’API avec modération ou uniquement en cas de changement d’emplacement important de l’utilisateur.

## Publication des événements de géofence

### iOS

Sous iOS, appelez l’API `processGeofenceEvent` Places dans le `CLLocationManager` délégué. Cette API vous informe si l’utilisateur est entré dans une région spécifique ou s’il l’a quitté.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```
