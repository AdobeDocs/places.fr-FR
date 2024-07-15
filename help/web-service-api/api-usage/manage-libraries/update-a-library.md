---
title: Mise à jour d’une bibliothèque
description: Mettez à jour une bibliothèque à l’aide de l’API REST Places.
exl-id: 37ca2be2-39e1-4f8e-87c2-ef4cb366db0d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 6%

---

# Mise à jour d’une bibliothèque {#update-a-library}

Méthode de PUT qui vous permet de mettre à jour une bibliothèque.

## Requête

```text
PUT https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
```

## En-têtes

```text
-H' Content-Type: application/json'  -H 'Authorization: bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Corps

```text
{"name": "<NEW_LIBRARY_NAME>"}
```

## Exemple de réponse

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Really facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL, commande

Utilisez la commande CURL suivante pour tester cette API :

```text
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"Updated Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Remplacez des variables telles que `<lIBRARYID>`, `<API KEY>`, `<TOKEN>` et `<ORGID>` par des valeurs réelles.
