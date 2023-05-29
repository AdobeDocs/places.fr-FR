---
title: Suppression d’un point ciblé
description: Supprimez un point ciblé à l’aide des API REST de Places.
exl-id: 0325eb3b-f9b2-4b21-bed8-e318e8072a69
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 9%

---

# Suppression d’un point ciblé {#delete-a-poi}

Méthode de DELETE qui vous permet de supprimer un point ciblé.

## Requête

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
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
If successful a Status of "204 No Content" is returned.
```

## CURL, commande

Utilisez la commande CURL suivante pour tester l’API :

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Remplacer `<POIID>`, `<API KEY>`, `<TOKEN>`, et `<ORGID>` avec des valeurs réelles.
