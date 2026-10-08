---
title: Vue d’ensemble
description: Comprendre et utiliser les API Query.
exl-id: cc61a49c-1cf2-407f-b81a-3d38fcb622cc
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 3%
---
# API de requête

Méthode GET qui permet d’interroger les points d’intérêt les plus proches de l’appelant.

## Requête

```text
GET https://query.places.adobe.com/placesedgequery
```

Avec l’entrée suivante, le service renvoie une liste des points d’intérêt les plus proches de l’appelant :

* Position de l’appelant (latitude, longitude).
* Identifiants des bibliothèques de points d’intérêt à inclure dans la recherche.
* Nombre maximal de POI à renvoyer.  La valeur par défaut est 100.

  La distance entre l&#39;appelant et le point d&#39;intérêt est définie comme la distance entre l&#39;appelant et le bord de la limite géographique du point d&#39;intérêt. Dans la réponse, les points d’intérêt qui contiennent l’appelant sont marqués comme ayant l’appelant.

Les arguments sont fournis sous la forme des paramètres de requête suivants :

* (**Obligatoire**) `latitude`

  La latitude de l&#39;appelant, qui doit être comprise entre -85 et 85.
* (**Obligatoire**) `longitude`

  Longitude de l&#39;appelant, qui doit être comprise entre -180 et 180.

* (**Facultatif**) `limit`

  Nombre maximal de POI à renvoyer.

* (**Obligatoire**) `library`

  Identifiant de la bibliothèque à interroger. Pour interroger plusieurs bibliothèques, veillez à inclure plusieurs copies du paramètre de bibliothèque dans la requête.

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

Les points d’intérêt sous `places.pois` sont triés par distance entre l’appelant et le bord des points d’intérêt. Les points d’intérêt sous `places.userWithin` contiennent l’appelant et ces points d’intérêt sont classés par rang, puis par rayon croissant.

## Exemple d’appel

Voici un exemple de l’appel :

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
