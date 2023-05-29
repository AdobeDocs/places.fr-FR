---
title: Obtention du rang d’une bibliothèque
description: Obtenez le classement d’une bibliothèque à l’aide de l’API REST Places.
exl-id: c0abedd0-5ff4-4a01-9f8d-e3d17ea53a97
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '41'
ht-degree: 9%

---

# Obtention du rang d’une bibliothèque {#get-library-rank}

Méthode de GET qui vous permet de classer les bibliothèques.

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
>Remplacer des variables telles que `<API KEY>`, `<TOKEN>`, et `<ORGID>` avec des valeurs réelles.
