---
title: Suppression de plusieurs points ciblés
description: Utilisez les API par lot pour supprimer plusieurs points ciblés.
exl-id: f170b722-e6f4-42a2-b3a6-1bf56965eb17
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 14%

---

# Suppression de plusieurs points ciblés {#delete-multiple-pois}

Méthode de POST qui vous permet de supprimer plusieurs points ciblés.

## Requête

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete
```

## En-têtes

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Corps

```text
{  "ids": [    "<POIID>",    "<POIID>",    .    .    .    "<POIID>",    "<POIID>"  ]}
```

## Exemple de réponse

```text
If successful a Status of "204 No Content" is returned.
```

## CURL, commande

Utilisez la commande CURL suivante pour tester cette API :

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Remplacer `<API KEY>`, `<TOKEN>`, `<ORGID>`, et `<PATHTOBATCHDELETEJSONFILE>` avec des valeurs réelles.

## Exemple de fichier JSON

Voici l’exemple de fichier JSON pour la variable `batchDelete` API :

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
