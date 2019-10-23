---
title: Définir un rang sur vos bibliothèques
seo-title: Définir un rang sur vos bibliothèques
description: Définissez un classement sur vos bibliothèques à l’aide de l’API REST Places.
seo-description: Définissez un classement sur vos bibliothèques à l’aide de l’API REST Places.
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---


# Définir un rang sur vos bibliothèques

Méthode PUT qui vous permet de définir un ordre de classement pour toutes vos bibliothèques.

## Demande

`PUT https://api-places-dev.adobe.io/places/placesapi/v1/libraries/rank`

## En-têtes

```-H Content-Type: application/json'
-H 'Authorization: Bearer <TOKEN>`  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Données PUT

```
"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]  
}
```

## Exemple de réponse

```
{"library_rank_order" ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}
```

## CURL, commande

```
curl -X PUT `'https://api-places.adobe.io/places/placesapi/v1/libraries/rank'` -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Remplacez des variables telles que `<API KEY>`, `<TOKEN>`et `<ORGID>` par des valeurs réelles.

