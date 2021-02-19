---
title: En-têtes et paramètres
description: En-têtes et paramètres disponibles dans les API REST du service Places.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 12%

---


# En-têtes et paramètres {#headers-and-parameters}

Voici les détails concernant les en-têtes et les paramètres disponibles dans l’API REST du service Places :

## En-têtes pris en charge

| Header | Description | Méthode | Exemple |
| :--- | :--- | :--- | :--- |
| `Authorization` | Jeton au porteur | Toutes |  |
| `x-api-key` | Votre clé d’API | Toutes | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Votre ID d’organisation | Toutes | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Format du contenu envoyé ou reçu | PUT, POST | `application/json` |
| `Accept-Language` | Langue utilisée pour les messages d’erreur | Facultative | `en-US` |

## Paramètres de la bibliothèque

| Paramètre | Description | Type | Limite | Demande ou réponse | Exemple |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID de la bibliothèque | affecté | n/a | Réponse | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Nom de la bibliothèque | chaîne | 256 caractères | les deux, requis dans la demande | `"name": "Amazing Places"` |
| `orgID` | ID d’organisation Experience Cloud de l’organisation | affecté | n/a | Réponse | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Nombre de points d’intérêt dans la bibliothèque | entier | 150 000 max | Réponse | `"poiCount": 25149` |
| `metadataDescriptors` | Compter pour chaque paire de valeurs de clé de métadonnées de point d’intérêt unique | mixte | n/a | Réponse |  |
| `poiCountInCities` | Compter pour chaque valeur de ville POI unique | mixte | n/a | Réponse |  |

## Paramètres POI

| Paramètre | Description | Type | Limite | Demande ou réponse | Exemple |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Données du pétrole | Tableau des détails des points d’intérêt | n/a | both |  |
| `id` | ID de l’API | affecté | n/a | réponse | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Nom de l’API | chaîne | 512 caractères | les deux, facultatif\* | `"name": "My Favorite Place"` |
| `description` | Description du POI | chaîne | 512 caractères | les deux, facultatif\* | `"description": "This is a very good place."` |
| `location` | Tableau du type et des coordonnées de l&#39;IPE | tableau (mixte) | n/a | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Type de point d’intérêt | chaîne | seul &quot;point&quot; actuellement pris en charge | les deux, requis dans la demande | `"type": "Point"` |
| `coordinates` | Tableau de longitude et de latitude de l&#39;IPE | tableau (flottant) | longitude : -180 à 180, latitude -85 à 85 | les deux, requis dans la demande | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Taille de la géofence circulaire autour de l’IPE | float | 10 à 2 000 mètres | les deux, requis dans la demande | `"radius": 100` |
| `country` | Pays pour la période d’enquête | chaîne | 32 caractères | les deux, facultatif* | `"country": "United States"` |
| `state` | État de la période d’enquête | chaîne | 32 caractères | les deux, facultatif* | `"state": "California"` |
| `city` | Ville de l’API | chaîne | 32 caractères | les deux, facultatif* | `"city": "San Jose"` |
| `street` | Adresse de la rue du POI | chaîne | 256 caractères | les deux, facultatif* | `"street": "122 Woz Way"` |
| `category` | Catégorie pour le POI | chaîne | 100 caractères | les deux, facultatif* | `"category": "cafe"` |
| `icon` | Icône de l’API | chaîne | 50 caractères | les deux, facultatif* | `"icon": "star"` |
| `color` | Couleur de l’objet ciblé | chaîne | 8 caractères | les deux, facultatif* | `"color": "blue"` |
| `metadata` | Tableau de paires clé/valeur pour l’API | array(string) | key: 256 caractères, valeur : 256 caractères, maximum de 10 paires | les deux, facultatif* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID de la bibliothèque dans laquelle se trouve le point d’accès | n/a | n/a | les deux, obligatoires | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Si la valeur du paramètre n&#39;est pas incluse, elle est définie sur `empty` dans la base de données. Si la paire clé/valeur existante n’est pas incluse, la paire clé/valeur est supprimée pour cette API dans la base de données.

