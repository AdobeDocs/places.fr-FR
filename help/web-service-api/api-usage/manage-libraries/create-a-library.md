---
title: Créer une bibliothèque
description: Créez une bibliothèque à l’aide de l’API REST Places.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e

---


# Création d’une bibliothèque {#create-a-library}

Méthode POST qui vous permet de créer une bibliothèque.

## Requête

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## En-têtes

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Corps

```text
{"name": "<LIBRARY_NAME>"}
```

## Exemple de réponse

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL, commande

Utilisez la commande CURL suivante pour tester cette API :

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Remplacez des variables telles que `<API KEY>`, `<TOKEN>`et `<ORGID>` par des valeurs réelles.

