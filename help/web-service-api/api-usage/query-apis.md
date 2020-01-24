---
title: Aperçu
description: Compréhension et utilisation des API de requête.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---



# API de requête

Méthode GET qui vous permet d’interroger les points d’intérêt les plus proches de l’appelant.

## Requête

```text
GET https://query.places.adobe.com/placesedgequery
```

Avec l’entrée suivante, le service renvoie une liste des points d’intérêt les plus proches de l’appelant :

* Position de l’appelant (latitude, longitude).
* ID des bibliothèques d’API à inclure dans la recherche.
* Nombre maximal de points d’intérêt à renvoyer.  La valeur par défaut est 100.

   La distance entre l’appelant et le point d’accès est définie comme la distance entre l’appelant et le bord de la géofence du point d’accès. Dans la réponse, les points d’intérêt qui contiennent l’appelant sont marqués comme ayant l’appelant.

Les arguments sont fournis comme paramètres de requête suivants :

* (**Required**) `latitude`

   La latitude de l’appelant, qui doit être comprise entre -85 et 85.
* (**Required**) `longitude`

   Longitude de l’appelant, qui doit être comprise entre -180 et 180.

* (**Facultatif**) `limit`

   Nombre maximal de points d’intérêt à renvoyer.

* (**Required**) `library`

   ID de la bibliothèque à interroger. Pour interroger plusieurs bibliothèques, veillez à inclure plusieurs copies du paramètre de bibliothèque dans la requête.

Voici un exemple du format JSON renvoyé avec succès :

```markup
{
    "places": {
        "userWithin": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": "Vineyard Heights",
                    "Color": "Blue",
                    "state": "CA",
                    <other POI metadata>
                }
            }
        ],
        "pois": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Milpitas",
                    "street": null,
                    "state": "CA"
                }
            },
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": null,
                    "state": "CA"
                }
            }
        ]
    }
}
```

Les points d’intérêt sous `places.pois` sont triés par distance entre l’appelant et le bord des points d’intérêt. Les points d’intérêt sous `places.userWithin` contiennent l’appelant, et ces points d’intérêt sont classés par rang puis par augmentation du rayon.

## Exemple d’appel

Voici un exemple de cet appel :

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
