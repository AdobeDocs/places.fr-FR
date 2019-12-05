---
title: Suppression d’une bibliothèque
description: Supprimez une bibliothèque à l’aide des API REST Places.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Suppression d’une bibliothèque

Méthode DELETE qui permet de supprimer une bibliothèque.

## Requête

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
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

Utilisez la commande CURL suivante pour tester cette API :

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Remplacez des variables telles que `<lIBRARYID>`, `<API KEY>`, `<TOKEN>`et `<ORGID>`par des valeurs réelles.

