---
title: En-têtes et paramètres
description: En-têtes et paramètres disponibles dans les API REST Places.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# En-têtes et paramètres {#headers-and-parameters}

Voici les détails relatifs aux en-têtes et aux paramètres disponibles dans l’API REST Places :

## En-têtes pris en charge

| En-tête | Description | Méthode | Exemple |
| :--- | :--- | :--- | :--- |
| `Authorization` | Votre jeton porteur | Toutes |  |
| `x-api-key` | Votre clé API | Toutes | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Votre ID d’organisation | Toutes | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Format du contenu envoyé ou reçu | PUT, POST | `application/json` |
| `Accept-Language` | Langue utilisée pour les messages d’erreur | Facultatif | `en-US` |

## Paramètres de bibliothèque

| Paramètre | Description | Type | Limite | Demande ou réponse | Exemple |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID de bibliothèque | affecté | n/d | Réponse | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Nom de la bibliothèque | string | 256 caractères | les deux, requis dans la demande | `"name": "Amazing Places"` |
| `orgID` | ID d’organisation Experience Cloud de l’entreprise | affecté | n/d | Réponse | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Nombre de points d’intérêt dans la bibliothèque | integer | 150 000 max | Réponse | `"poiCount": 25149` |
| `metadataDescriptors` | Compter pour chaque paire de valeurs de clé de métadonnées de point d’intérêt unique | mixte | n/d | Réponse |  |
| `poiCountInCities` | Compter pour chaque valeur de ville de point d’intérêt unique | mixte | n/d | Réponse |  |

## Paramètres POI

| Paramètre | Description | Type | Limite | Demande ou réponse | Exemple |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Données du Poi | Tableau des détails des points d’intérêt | n/d | both |  |
| `id` | ID du point d’accès | affecté | n/d | réponse | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Nom du point d’intérêt | string | 512 caractères | les deux, facultatif\* | `"name": "My Favorite Place"` |
| `description` | Description de l’API | string | 512 caractères | les deux, facultatif\* | `"description": "This is a very good place."` |
| `location` | Tableau du type et des coordonnées de l'IPE | tableau (mixte) | n/d | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Type d’IPE | string | seul "Point" actuellement pris en charge | les deux, requis dans la demande | `"type": "Point"` |
| `coordinates` | Tableau de longitude et de latitude de la POI | tableau (float) | longitude : -180 à 180, latitude -85 à 85 | les deux, requis dans la demande | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Taille de la géofence circulaire autour de l'IPE | flotter | 10 à 2 000 mètres | les deux, requis dans la demande | `"radius": 100` |
| `country` | Pays pour la période d'enquête | string | 32 caractères | les deux, facultatif* | `"country": "United States"` |
| `state` | État de l'IPE | string | 32 caractères | les deux, facultatif* | `"state": "California"` |
| `city` | Ville de l’API | string | 32 caractères | les deux, facultatif* | `"city": "San Jose"` |
| `street` | Adresse de rue du point d'entrée | string | 256 caractères | les deux, facultatif* | `"street": "122 Woz Way"` |
| `category` | Catégorie de l’API | string | 100 caractères | les deux, facultatif* | `"category": "cafe"` |
| `icon` | Icône de l’API | string | 50 caractères | les deux, facultatif* | `"icon": "star"` |
| `color` | Couleur de la zone cliquable | string | 8 caractères | les deux, facultatif* | `"color": "blue"` |
| `metadata` | Tableau de paires clé/valeur pour l’API | array(string) | key : 256 caractères, valeur : 256 caractères, maximum 10 paires | les deux, facultatif* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID de la bibliothèque dans laquelle se trouve le point d’accès | n/d | n/d | les deux, obligatoires | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Si la valeur du paramètre n’est pas incluse, elle est définie sur `empty` dans la base de données. Si la paire clé/valeur existante n’est pas incluse, la paire clé/valeur est supprimée pour cette API dans la base de données.

