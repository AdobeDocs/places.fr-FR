---
title: Lecture d’une bibliothèque
seo-title: Lecture d’une bibliothèque
description: Lisez une bibliothèque à l’aide de l’API REST Places.
seo-description: Lisez une bibliothèque à l’aide de l’API REST Places.
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---



# Lecture d’une bibliothèque

Méthode GET qui renvoie les détails d’une bibliothèque.

## Demande

```text
GET https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>
```

## En-têtes

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Exemple de réponse

```text
{
    "id": "9aa7f663-35cc-4de6-8643-ae7779f3bb87",
    "name": "Facinating places",
    "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",
    "poiCount": 30,
    "metadataDescriptors": [
        {
            "key": "region",
            "type": "string",
            "value": "Equator",
            "count": 29
        },
        {
            "key": "ownership",
            "type": "string",
            "value": "LS",
            "count": 1
        },
        {
            "key": "brand",
            "type": "string",
            "value": "Coffee Cafe",
            "count": 1
        },
        {
            "key": "Color",
            "type": "string",
            "value": "Blue",
            "count": 1
        }
    ],
    "poiCountInCities": [
        {
            "country": "Ghana",
            "state": "Ghana",
            "city": "Accra",
            "count": 29
        },
        {
            "country": "CN",
            "state": "91",
            "city": "Hong Kong",
            "count": 1
        }
    ]
}
```

## CURL, commande

Utilisez la commande CURL suivante pour tester l’API :

```text
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Remplacez `<LIBRARYID>`, `<API KEY>`, `<TOKEN>`et `<ORGID>` par des valeurs réelles.

