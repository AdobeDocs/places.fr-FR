---
title: créer une bibliothèque ;
description: Créez une bibliothèque à l’aide de l’API REST Places.
exl-id: 155cc6e6-9254-4389-bb02-e526d15908f4
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 22%

---

# créer une bibliothèque ; {#create-a-library}

Méthode de POST qui vous permet de créer une bibliothèque.

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
>Remplacer des variables telles que `<API KEY>`, `<TOKEN>`, et `<ORGID>` avec des valeurs réelles.
