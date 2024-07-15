---
title: Vue d’ensemble
description: Comprendre et utiliser les API de requête.
exl-id: cc61a49c-1cf2-407f-b81a-3d38fcb622cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 3%

---

# API de requête

Méthode de GET qui vous permet d’interroger les points ciblés les plus proches de l’appelant.

## Requête

```text
GET https://query.places.adobe.com/placesedgequery
```

Avec l’entrée suivante, le service renvoie une liste des points ciblés les plus proches de l’appelant :

* Position de l’appelant (latitude, longitude).
* ID des bibliothèques POI à inclure dans la recherche.
* Nombre maximal de points ciblés à renvoyer.  La valeur par défaut est 100.

  La distance entre l’appelant et le point ciblé est définie comme la distance entre l’appelant et le bord de la clôture virtuelle du point ciblé. Dans la réponse, les points ciblés contenant l’appelant sont marqués comme ayant l’appelant.

Les arguments sont fournis en tant que paramètres de requête suivants :

* (**Obligatoire**) `latitude`

  La latitude de l’appelant, qui doit être comprise entre -85 et 85.
* (**Obligatoire**) `longitude`

  Longitude de l’appelant, qui doit être comprise entre -180 et 180.

* (**Facultatif**) `limit`

  Nombre maximal de points ciblés à renvoyer.

* (**Obligatoire**) `library`

  L’identifiant de la bibliothèque à interroger. Pour interroger plusieurs bibliothèques, veillez à inclure plusieurs copies du paramètre de bibliothèque dans la requête.

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

Les points ciblés sous `places.pois` sont triés par distance entre l’appelant et le bord des points ciblés. Les points ciblés sous `places.userWithin` contiennent l’appelant et ces points ciblés sont triés par rang, puis par rayon croissant.

## Exemple d’appel

Voici un exemple d’appel :

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
