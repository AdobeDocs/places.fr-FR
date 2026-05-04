---
title: Utilisation du service Places sans surveillance active des régions
description: Cette section fournit des informations sur l’utilisation du service Places sans surveillance active des régions.
exl-id: 0ba7949a-447e-4754-9b45-945e58e29541
TQID: https://experienceleague.adobe.com/xUmdMOa5CvDZSxKFeyse-3vHsUwvm2s04-sIG0FnnCs
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: bef6f891-2e8a-425e-8f99-7ddf22070daa
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
  - id: d833d0ef-8ed5-4cff-a5e7-9f12abd02a31
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2:
  - id: b572b7ff-a413-4173-b2b4-d7d3874f1b9b
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
  - id: ee602049-8a18-43df-9299-a689a025a371
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 786
ht-degree: 0%

---

# Utilisation du service Places sans surveillance active des régions {#use-places-without-active-monitoring}

Les cas d’utilisation de votre application peuvent ne pas nécessiter une surveillance active de la région. Places Service peut toujours être utilisé pour intégrer les données de localisation de vos utilisateurs à d’autres produits Experience Platform.

## Prérequis

Le développeur va collecter l&#39;emplacement de l&#39;appareil en utilisant les API fournies par le système d&#39;exploitation de la plateforme cible.

>[!TIP]
>
>Si les cas d’utilisation de votre application nécessitent une surveillance active de la région, consultez [Utilisation du service Places avec votre propre solution de surveillance](/help/using-your-own-monitor.md).

Pour utiliser Places Service sans surveillance active des régions :

## &#x200B;1. Collecter l’emplacement de l’utilisateur

Le développeur ou la développeuse d’applications doit collecter l’emplacement actuel de l’appareil à l’aide de l’`CoreLocation.framework` (iOS) ou des API `Location` fournies par les services Google Play (Android).

Pour plus d’informations, consultez la documentation suivante :

- [CoreLocation](https://developer.apple.com/documentation/corelocation) (Apple)
- [API d’emplacement dans les services Google Play](https://developer.android.com/training/location) (Google)

## &#x200B;2. Récupérer les points d’intérêt à proximité à partir du SDK

Une fois que vous avez obtenu l’emplacement de l’utilisateur, vous pouvez le transmettre au SDK pour récupérer une liste des points d’intérêt à proximité.

### Android

Voici un exemple d’implémentation dans Android qui utilise un [`BroadcastReceiver`](https://codelabs.developers.google.com/codelabs/background-location-updates-android-o/index.html?index=..%2F..index#5) :

```java
public class LocationBroadcastReceiver extends BroadcastReceiver {
    static final String ACTION_LOCATION_UPDATE = "locationUpdate";
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent == null || context == null) {
            return;
        }

        final String action = intent.getAction();
        if (!ACTION_LOCATION_UPDATE.equals(action)) {
            return;
        }

        LocationResult result = LocationResult.extractResult(intent);
        if (result == null) {
            return;
        }

        Location currentLocation = result.getLastLocation();
        if (currentLocation == null) {
            return;
        }

        // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
        Places.getNearbyPointsOfInterest(currentLocation, 10,
            new AdobeCallback<List<PlacesPOI>>() {
                @Override
                public void call(List<PlacesPOI> pois) {
                    // pois is the 10 nearest POIs based on the location
                }
            }, new AdobeCallback<PlacesRequestError>() {
                @Override
                public void call(PlacesRequestError placesRequestError) {
                    // Look for the placesRequestError and handle the error accordingly
                }
            }
        );
    }
}
```

### Objectif-C

Voici un exemple d’implémentation pour iOS. Le code affiche l’implémentation de la méthode [`locationManager:didUpdateLocations:`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager?language=objc) dans le [`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager?language=objc) :

```objectivec
- (void) locationManager:(CLLocationManager*)manager didUpdateLocations:(NSArray<CLLocation*>*)locations {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    [ACPPlaces getNearbyPointsOfInterest:[locations lastObject] limit:10 callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // nearbyPoi is the 10 nearest POIs based on the location
    } errorCallback:^(ACPPlacesRequestError result) {
        // log the error if we got one
        NSLog(@"error: %lu", (unsigned long)result);
    }];
}
```

### Swift

Voici un exemple d’implémentation pour iOS. Le code affiche l’implémentation de la méthode [`locationManager(_:didUpdateLocations:)`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager) dans le [`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager) :

```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    ACPPlaces.getNearbyPoints(ofInterest: locations.last!, limit: 10, callback: { (nearbyPoi) in
        // nearbyPoi is the 10 nearest POIs based on the location
    }) { (error) in
        // log the error if we have one
        print("error: \(error)")
    }
}
```

## &#x200B;3. Joindre les données Places à vos requêtes Analytics

En appelant l’API `getNearbyPointsOfInterest`, Places SDK rend toutes les données de point d’intérêt pertinentes pour l’appareil disponibles via les éléments de données dans Launch. En utilisant une règle [Joindre les données](https://aep-sdks.gitbook.io/docs/resources/user-guides/attach-data), les données Places peuvent être automatiquement ajoutées aux futures requêtes envoyées à Analytics. Cela élimine la nécessité d’un appel unique à Analytics au moment de la collecte de l’emplacement de l’appareil.

Voir [Ajouter du contexte d’emplacement aux requêtes Analytics](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md) pour en savoir plus sur cette rubrique.

## Facultatif - Déclenchez des événements d’entrée lorsque l’utilisateur se trouve dans un point d’intérêt

>[!TIP]
>
>La méthode recommandée pour capturer les données Places consiste à [Joindre les données Places à vos requêtes Analytics](#attach-places-data-to-your-analytics-requests).
>
>Si le cas d’utilisation nécessite le déclenchement d’un événement d’entrée [région](https://developer.adobe.com/client-sdks/documentation/places/api-reference/#processregionevent) par le SDK, il doit être effectué manuellement comme indiqué ci-dessous.

La liste renvoyée par l’API `getNearbyPointsOfInterest` contient des [objets personnalisés](https://developer.adobe.com/client-sdks/documentation/places/api-reference/#additional-classes-and-enums) qui indiquent si l’utilisateur se trouve actuellement dans un point d’intérêt. Si l’utilisateur se trouve dans un point d’intérêt, le SDK peut déclencher un événement d’entrée pour cette région.

>[!IMPORTANT]
>
>Pour éviter que votre application ne déclenche plusieurs événements d’entrée au cours d’une seule visite, conservez la liste des régions dans lesquelles vous savez que l’utilisateur a saisi des données. Lors du traitement de la réponse des points d’intérêt à proximité à partir du SDK, déclenchez un événement d’entrée uniquement lorsque la région ne figure pas dans votre liste.
>
>Dans l’exemple de code suivant, `NSUserDefaults` (iOS) et `SharedPreferences` (Android) sont utilisés pour gérer la liste des régions :

### Android

L’exemple de code suivant montre la gestion du résultat fourni dans le rappel d’un `List<PlacesPOI>` `getNearbyPointsOfInterest` :

```java
void handleUpdatedPOIs(final List<PlacesPOI> nearbyPois) {
    // get the list of regions we know the user is already within from SharedPreferences
    SharedPreferences preferences = getApplicationContext().getSharedPreferences("places", 0);
    Set<String> regionsUserIsAlreadyIn = preferences.getStringSet("regionsUserIsAlreadyIn", new HashSet<String>());

    // loop through new placesPOIS and post entry events for pois that aren't already in our list
    // also create the new list of regions that the user is in
    Set<String> updatedRegionsUserIsIn = new HashSet<String>();
    for (PlacesPOI poi : nearbyPois) {
        // check if the user is in this poi
        if (poi.containsUser()) {
            // the user is in the poi, now we need to make sure we haven't already recorded this entry event
            if (!regionsUserIsAlreadyIn.contains(poi.getIdentifier())) {
                Geofence poiGeofence = new Geofence.Builder()
                    .setRequestId(poi.getIdentifier())
                    .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER)
                    .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
                    .setExpirationDuration(Geofence.NEVER_EXPIRE)
                    .build();
                Places.processGeofence(poiGeofence, Geofence.GEOFENCE_TRANSITION_ENTER);
            }

            // add the region to our new list of regions
            updatedRegionsUserIsIn.add(poi.getIdentifier());
        }
    }

    // update SharedPreferences with our new list of regions
    SharedPreferences.Editor editor = getApplicationContext().getSharedPreferences("places", 0).edit();
    editor.putStringSet("regionsUserIsAlreadyIn", updatedRegionsUserIsIn).apply();
}
```

### Objectif-C

L’exemple de code suivant montre la gestion du résultat fourni dans le rappel d’un `NSArray<ACPPlacesPoi *> *` `getNearbyPointsOfInterest:limit:callback:errorCallback:` :

```objectivec
- (void) handleUpdatedPOIs:(NSArray<ACPPlacesPoi *> *)nearbyPois {
   // get the list of regions we know the user is already within from user defaults
   NSArray *regionsUserIsCurrentlyWithin = [[NSUserDefaults standardUserDefaults]
                                            arrayForKey:@"regionsUserIsAlreadyIn"];

   // loop through new nearbyPoi and post entry events for pois that aren't already in our list
   // also creating the new list of known regions that the user is in
   NSMutableArray *updatedRegionsUserIsCurrentlyWithin = [@[] mutableCopy];
   for (ACPPlacesPoi *poi in nearbyPois) {
       // check if the user is in this poi
       if (poi.userIsWithin) {
           // the user is in the poi, now we need to make sure we haven't already recorded the entry event
           if (![regionsUserIsCurrentlyWithin containsObject:poi.identifier]) {
               CLCircularRegion *region = [[CLCircularRegion alloc] initWithCenter:CLLocationCoordinate2DMake(poi.latitude, poi.longitude)
                                                                            radius:poi.radius
                                                                        identifier:poi.identifier];
               [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
           }

           // add the region to our updated list
           [updatedRegionsUserIsCurrentlyWithin addObject:poi.identifier];
       }
   }

   // update user defaults with the new list
   [[NSUserDefaults standardUserDefaults] setObject:updatedRegionsUserIsCurrentlyWithin forKey:@"regionsUserIsAlreadyIn"];
}
```

### Swift

L’exemple de code suivant montre la gestion du résultat fourni dans le rappel d’un `[ACPPlacesPoi]` `getNearbyPoints(_ ofInterest: CLLocation, limit: UInt, callback: (([ACPPlacesPoi]?) -> Void)?, errorCallback: ((ACPPlacesRequestError) -> Void)?)` :

```swift
func handleUpdatedPOIs(_ nearbyPois:[ACPPlacesPoi]) {
    // get the list of regions we know the user is already within from user defaults
    let regionsUserIsCurrentlyWithin : [String] = UserDefaults.standard.array(forKey: "regionsUserIsAlreadyIn") as! [String]

    // loop through new nearbyPoi and post entry events for pois that aren't already in our list
    // also creating the new list of known regions that the user is in
    var updatedRegionsUserIsCurrentlyWithin: [String] = []
    for poi in nearbyPois {
        // check if the user is in this poi
        if poi.userIsWithin {
            // the user is in the poi, now we need to make sure we haven't already recorded the entry event
            if !regionsUserIsCurrentlyWithin.contains(poi.identifier!) {
                let region = CLCircularRegion.init(center: CLLocationCoordinate2D.init(latitude: poi.latitude, longitude: poi.longitude), radius: CLLocationDistance(poi.radius), identifier: poi.identifier!)
                ACPPlaces.processRegionEvent(region, for: .entry)
            }

            // add the region to our updated list
            updatedRegionsUserIsCurrentlyWithin.append(poi.identifier!)
        }
    }

    // update user defaults with the new list
    UserDefaults.standard.set(updatedRegionsUserIsCurrentlyWithin, forKey: "regionsUserIsAlreadyIn")
}
```

## Exemple complet d’implémentation

Les exemples de code ci-dessous vous montrent comment récupérer l’emplacement actuel de l’appareil, déclencher les événements d’entrée nécessaires et vous assurer que vous n’obtenez pas plusieurs entrées pour le même emplacement lors d’une seule visite.

Cet exemple de code comprend l’étape facultative [déclencher des événements d’entrée lorsque l’utilisateur se trouve dans un point d’intérêt](#trigger-entry-events-when-the-user-is-in-a-poi).

>[!IMPORTANT]
>
>Ces fragments de code ne sont que **exemples** L’équipe de développement doit déterminer comment elle souhaite implémenter la fonctionnalité. Dans sa décision, elle doit tenir compte des bonnes pratiques recommandées par le système d’exploitation cible.

### Android

```java
public class LocationBroadcastReceiver extends BroadcastReceiver {
    static final String ACTION_LOCATION_UPDATE = "locationUpdate";
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent == null || context == null) {
            return;
        }

        final String action = intent.getAction();
        if (!ACTION_LOCATION_UPDATE.equals(action)) {
            return;
        }

        LocationResult result = LocationResult.extractResult(intent);
        if (result == null) {
            return;
        }

        Location currentLocation = result.getLastLocation();
        if (currentLocation == null) {
            return;
        }

        // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
        Places.getNearbyPointsOfInterest(currentLocation, 10,
            new AdobeCallback<List<PlacesPOI>>() {
                @Override
                public void call(List<PlacesPOI> pois) {
                    // pois is the 10 nearest POIs based on the location
                    handleUpdatedPOIs(pois);
                }
            }, new AdobeCallback<PlacesRequestError>() {
                @Override
                public void call(PlacesRequestError placesRequestError) {
                    // Look for the placesRequestError and handle the error accordingly
                }
            }
        );
    }

    void handleUpdatedPOIs(final List<PlacesPOI> nearbyPois) {
        // get the list of regions we know the user is already within from SharedPreferences
        SharedPreferences preferences = getApplicationContext().getSharedPreferences("places", 0);
        Set<String> regionsUserIsAlreadyIn = preferences.getStringSet("regionsUserIsAlreadyIn", new HashSet<String>());

        // loop through new placesPOIS and post entry events for pois that aren't already in our list
        // also create the new list of regions that the user is in
        Set<String> updatedRegionsUserIsIn = new HashSet<String>();
        for (PlacesPOI poi : nearbyPois) {
            // check if the user is in this poi
            if (poi.containsUser()) {
                // the user is in the poi, now we need to make sure we haven't already recorded this entry event
                if (!regionsUserIsAlreadyIn.contains(poi.getIdentifier())) {
                    Geofence poiGeofence = new Geofence.Builder()
                        .setRequestId(poi.getIdentifier())
                        .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER)
                        .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
                        .setExpirationDuration(Geofence.NEVER_EXPIRE)
                        .build();
                    Places.processGeofence(poiGeofence, Geofence.GEOFENCE_TRANSITION_ENTER);
                }

                // add the region to our new list of regions
                updatedRegionsUserIsIn.add(poi.getIdentifier());
            }
        }

        // update SharedPreferences with our new list of regions
        SharedPreferences.Editor editor = getApplicationContext().getSharedPreferences("places", 0).edit();
        editor.putStringSet("regionsUserIsAlreadyIn", updatedRegionsUserIsIn).apply();
    }
}
```


### Objectif-C

```objectivec
- (void) locationManager:(CLLocationManager*)manager didUpdateLocations:(NSArray<CLLocation*>*)locations {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    [ACPPlaces getNearbyPointsOfInterest:[locations lastObject] limit:10 callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // nearbyPoi is the 10 nearest POIs based on the location
        [self handleUpdatedPOIs:nearbyPoi];
    } errorCallback:^(ACPPlacesRequestError result) {
        // log the error if we got one
        NSLog(@"error: %lu", (unsigned long)result);
    }];
}

- (void) handleUpdatedPOIs:(NSArray<ACPPlacesPoi *> *)nearbyPois {
   // get the list of regions we know the user is already within from user defaults
   NSArray *regionsUserIsCurrentlyWithin = [[NSUserDefaults standardUserDefaults]
                                            arrayForKey:@"regionsUserIsAlreadyIn"];

   // loop through new nearbyPoi and post entry events for pois that aren't already in our list
   // also creating the new list of known regions that the user is in
   NSMutableArray *updatedRegionsUserIsCurrentlyWithin = [@[] mutableCopy];
   for (ACPPlacesPoi *poi in nearbyPois) {
       // check if the user is in this poi
       if (poi.userIsWithin) {
           // the user is in the poi, now we need to make sure we haven't already recorded the entry event
           if (![regionsUserIsCurrentlyWithin containsObject:poi.identifier]) {
               CLCircularRegion *region = [[CLCircularRegion alloc] initWithCenter:CLLocationCoordinate2DMake(poi.latitude, poi.longitude)
                                                                            radius:poi.radius
                                                                        identifier:poi.identifier];
               [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
           }

           // add the region to our updated list
           [updatedRegionsUserIsCurrentlyWithin addObject:poi.identifier];
       }
   }

   // update user defaults with the new list
   [[NSUserDefaults standardUserDefaults] setObject:updatedRegionsUserIsCurrentlyWithin forKey:@"regionsUserIsAlreadyIn"];
}
```

### Swift

```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    ACPPlaces.getNearbyPoints(ofInterest: locations.last!, limit: 10, callback: { (nearbyPoi) in
        // nearbyPoi is the 10 nearest POIs based on the location
        self.handleUpdatedPOIs(nearbyPoi!)
    }) { (error) in
        // log the error if we have one
        print("error: \(error)")
    }
}

func handleUpdatedPOIs(_ nearbyPois:[ACPPlacesPoi]) {
    // get the list of regions we know the user is already within from user defaults
    let regionsUserIsCurrentlyWithin : [String] = UserDefaults.standard.array(forKey: "regionsUserIsAlreadyIn") as! [String]

    // loop through new nearbyPoi and post entry events for pois that aren't already in our list
    // also creating the new list of known regions that the user is in
    var updatedRegionsUserIsCurrentlyWithin: [String] = []
    for poi in nearbyPois {
        // check if the user is in this poi
        if poi.userIsWithin {
            // the user is in the poi, now we need to make sure we haven't already recorded the entry event
            if !regionsUserIsCurrentlyWithin.contains(poi.identifier!) {
                let region = CLCircularRegion.init(center: CLLocationCoordinate2D.init(latitude: poi.latitude, longitude: poi.longitude), radius: CLLocationDistance(poi.radius), identifier: poi.identifier!)
                ACPPlaces.processRegionEvent(region, for: .entry)
            }

            // add the region to our updated list
            updatedRegionsUserIsCurrentlyWithin.append(poi.identifier!)
        }
    }

    // update user defaults with the new list
    UserDefaults.standard.set(updatedRegionsUserIsCurrentlyWithin, forKey: "regionsUserIsAlreadyIn")
}
```

Outre le déclenchement des événements d’entrée du service Places dans le SDK, en raison des événements d’entrée de déclenchement, toutes les données qui définissent vos points d’intérêt peuvent être utilisées par le reste du SDK via `data elements` dans Experience Platform Launch. Avec Experience Platform Launch `rules`, vous pouvez joindre dynamiquement les données du service Places aux événements entrants qui sont traités par le SDK. Par exemple, vous pouvez joindre les métadonnées d’un point d’intérêt dans lequel se trouve l’utilisateur et envoyer les données à Analytics en tant que données contextuelles.

Pour plus d’informations, voir [Utilisation du service Places avec d’autres solutions Adobe](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md).
