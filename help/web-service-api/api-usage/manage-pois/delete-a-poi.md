---
title: Suppression d’un point d’intérêt
seo-title: Suppression d’un point d’intérêt
description: Supprimez un point d’intérêt en utilisant les API REST de lieux.
seo-description: Supprimez un point d’intérêt en utilisant les API REST de lieux.
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---


# Suppression d’un point d’intérêt

Méthode DELETE qui vous permet de supprimer un point d’intérêt.

## Demande

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
>Remplacez `<POIID>`, `<API KEY>`, `<TOKEN>`et `<ORGID>` par des valeurs réelles.

