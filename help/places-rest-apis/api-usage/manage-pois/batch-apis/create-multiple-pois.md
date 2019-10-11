---
title: Création de plusieurs points d’intérêt
seo-title: Création de plusieurs points d’intérêt
description: Utilisez les API par lot pour créer plusieurs points d’intérêt.
seo-description: Utilisez les API par lot pour créer plusieurs points d’intérêt.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Création de plusieurs points d’intérêt {#create-multiple-pois}

Méthode POST qui permet de créer plusieurs points d’intérêt.

## Demande

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchCreate
```

## En-têtes

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Corps

```text
{    "createPOIRequests": [        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        .        .        .        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        }    ]}
```

## Exemple de réponse

```text
{    "ids": [        "558360b5-5b4b-4c8a-777f-5e3f4b60e4cb",        "ac01c21c-6274-4922-86d5-7777b59dc9b0",        .        .        .        "acf0fde0-22ee-470a-bfa9-b760777cefdc",        "d3cf8338-520f-49a5-8ee7-3777df69be91"    ],    "_links": {        "pois": {            "href": "https://api-places-dev.adobe.io/places/placesapi/v1/pois/{poi_id}",            "templated": true        }    }}
```

## CURL, commande

Utilisez la commande CURL suivante pour tester cette API :

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchCreate' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHCREATEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Remplacez `<API KEY>`, `<TOKEN>`, `<ORGID>`et `<PATHTOBATCHCREATEJSONFILE>` par des valeurs réelles.

## Exemple de fichier JSON

Voici l’exemple de fichier JSON pour l’ `batchCreate` API :

```text
{    "createPOIRequests": [{            "name": "Sample POI 1",            "description": "1",            "location": {                "type": "Point",                "coordinates": [0.0, 0.0]            },            "radius": 25,            "country": "Ghana",            "state": "Ghana",            "city": "Accra",            "street": "",            "category": "cafe",            "icon": "nice",            "color": "red",            "metadata": {                "region": "Equator"            },            "lib_id" : "42b4d03c-672c-4deb-83e0-134ef070c2af"        },        {            "name": "Sample POI 2",            "description": "2",            "location": {                "type": "Point",                "coordinates": [0.025, 0.025]            },            "radius": 50,            "country": "Ghana",            "state": "Ghana",            "city": "Accra",            "street": "",            "category": "cafe",            "icon": "nice",            "color": "blue",            "metadata": {                "region": "Equator"            },            "lib_id" : "42b4d03c-672c-4deb-83e0-134ef070c2af"        },        {            "name": "Sample POI 3",            "description": "3",            "location": {                "type": "Point",                "coordinates": [0.05, 0.05]            },            "radius": 100,            "country": "Ghana",            "state": "Ghana",            "city": "Accra",            "street": "",            "category": "cafe",            "icon": "nice",            "color": "green",            "metadata": {                "region": "Equator"            },            "lib_id" : "42b4d03c-672c-4deb-83e0-134ef070c2af"        }    ]}
```
