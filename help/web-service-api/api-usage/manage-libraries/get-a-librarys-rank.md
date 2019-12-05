---
title: Obtenir le rang d'une bibliothèque
description: Obtenez le classement d’une bibliothèque à l’aide de l’API REST Places.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Obtenir le rang d'une bibliothèque

Méthode GET qui vous permet de classer les bibliothèques.

## Requête

`GET https://api-places.adobe.io/places/placesapi/v1/libraries/rank`

## En-têtes

```
-H Content-Type: application/JSON  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Exemple de réponse

```
{"library_rank_order":["ea45781f-26af-44b1-b4f8-43baf5f0fe28","dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b"]}
```

## CURL, commande

```
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank ' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Remplacez des variables telles que `<API KEY>`, `<TOKEN>`et `<ORGID>` par des valeurs réelles.

