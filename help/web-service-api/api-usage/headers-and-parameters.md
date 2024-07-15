---
title: En-têtes et paramètres
description: En-têtes et paramètres disponibles dans les API REST de Places Service.
exl-id: 3c7e76de-f0ff-4966-a3ec-7f64d819c140
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 19%

---

# En-têtes et paramètres {#headers-and-parameters}

Voici les détails sur les en-têtes et les paramètres disponibles dans l’API REST Places Service :

## En-têtes pris en charge

| Header | Description | Méthode | Exemple |
| :--- | :--- | :--- | :--- |
| `Authorization` | Votre jeton porteur | Toutes |  |
| `x-api-key` | Votre clé API | Toutes | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Votre ID d’organisation | Toutes | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Format du contenu envoyé ou reçu | PUT, POST | `application/json` |
| `Accept-Language` | Langue utilisée pour les messages d’erreur | Facultatif | `en-US` |

## Paramètres de bibliothèque

| Paramètre | Description | Type | Limite | Requête ou réponse | Exemple |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID de bibliothèque | affecté | S.O. | Réponse | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Nom de la bibliothèque | Chaîne | 256 caractères | les deux, requis dans la requête | `"name": "Amazing Places"` |
| `orgID` | ID d’organisation Experience Cloud de l’organisation | affecté | S.O. | Réponse | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Nombre de points ciblés dans la bibliothèque | Entier | 150 000 max | Réponse | `"poiCount": 25149` |
| `metadataDescriptors` | Comptage de chaque paire de valeurs de clés de métadonnées de point ciblé unique | mixte | S.O. | Réponse |  |
| `poiCountInCities` | Comptage pour chaque valeur de ville de point ciblé unique | mixte | S.O. | Réponse |  |

## Paramètres des points ciblés

| Paramètre | Description | Type | Limite | Requête ou réponse | Exemple |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Données du point d’interrogation | Tableau des détails des points ciblés | S.O. | both |  |
| `id` | ID du point ciblé | affecté | S.O. | response | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Nom du point ciblé | Chaîne | 512 caractères | les deux, facultatif\* | `"name": "My Favorite Place"` |
| `description` | Description du point ciblé | Chaîne | 512 caractères | les deux, facultatif\* | `"description": "This is a very good place."` |
| `location` | Tableau de type et coordonnées du point ciblé | tableau (mixte) | S.O. | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Type de point ciblé | Chaîne | actuellement uniquement &quot;Point&quot; pris en charge | les deux, requis dans la requête | `"type": "Point"` |
| `coordinates` | Tableau de longitude et de latitude des points ciblés | tableau (float) | longitude : -180 à 180, latitude -85 à 85 | les deux, requis dans la requête | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Taille de la géobarrière circulaire autour du point ciblé | float | 10 à 2 000 mètres | les deux, requis dans la requête | `"radius": 100` |
| `country` | Pays du point ciblé | Chaîne | 32 caractères | les deux, facultatif* | `"country": "United States"` |
| `state` | État du point ciblé | Chaîne | 32 caractères | les deux, facultatif* | `"state": "California"` |
| `city` | Ville du point ciblé | Chaîne | 32 caractères | les deux, facultatif* | `"city": "San Jose"` |
| `street` | Adresse postale du point ciblé | Chaîne | 256 caractères | les deux, facultatif* | `"street": "122 Woz Way"` |
| `category` | Catégorie du point ciblé | Chaîne | 100 caractères | les deux, facultatif* | `"category": "cafe"` |
| `icon` | Icône du point ciblé | Chaîne | 50 caractères | les deux, facultatif* | `"icon": "star"` |
| `color` | Couleur du point ciblé | Chaîne | 8 caractères | les deux, facultatif* | `"color": "blue"` |
| `metadata` | Tableau de paires clé/valeur pour le point ciblé | array(string) | clé : 256 caractères, valeur : 256 caractères, maximum 10 paires | les deux, facultatif* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID de la bibliothèque dans laquelle se trouve le point ciblé | S.O. | S.O. | les deux, obligatoire | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Si la valeur du paramètre n’est pas incluse, la valeur est définie sur `empty` dans la base de données. Si la paire clé/valeur existante n’est pas incluse, la paire clé/valeur est supprimée pour ce point ciblé dans la base de données.
