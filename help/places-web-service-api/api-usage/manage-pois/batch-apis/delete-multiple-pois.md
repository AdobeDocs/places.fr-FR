---
title: Suppression de plusieurs points d’intérêt
seo-title: Suppression de plusieurs points d’intérêt
description: Utilisez les API par lot pour supprimer plusieurs points d’intérêt.
seo-description: Utilisez les API par lot pour supprimer plusieurs points d’intérêt.
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---



# Suppression de plusieurs points d’intérêt {#delete-multiple-pois}

Méthode POST qui permet de supprimer plusieurs points d’intérêt.

## Demande

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
>Remplacez `<API KEY>`, `<TOKEN>`, `<ORGID>`et `<PATHTOBATCHDELETEJSONFILE>` par des valeurs réelles.

## Exemple de fichier JSON

Voici l’exemple de fichier JSON pour l’ `batchDelete` API :

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
