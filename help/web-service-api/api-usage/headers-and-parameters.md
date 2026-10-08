---
title: En-têtes et paramètres
description: En-têtes et paramètres disponibles dans les API REST Places Service.
exl-id: 3c7e76de-f0ff-4966-a3ec-7f64d819c140
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 19%
---
# En-têtes et paramètres {#headers-and-parameters}

Voici les détails sur les en-têtes et paramètres disponibles dans l’API REST Places Service :

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
| `id` | Identifiant de la bibliothèque | affecté | S.O. | Réponse | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Nom de la bibliothèque | chaîne | 256 caractères | les deux, requis dans la requête | `"name": "Amazing Places"` |
| `orgID` | OrgID Experience Cloud de l’organisation | affecté | S.O. | Réponse | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Nombre de POI dans la bibliothèque | entier | 150 000 max | Réponse | `"poiCount": 25149` |
| `metadataDescriptors` | Compter pour chaque paire unique de valeurs de clé de métadonnées de point d’intérêt | mixte | S.O. | Réponse |  |
| `poiCountInCities` | Compter pour chaque valeur de ville de point d’intérêt unique | mixte | S.O. | Réponse |  |

## Paramètres du point d’intérêt

| Paramètre | Description | Type | Limite | Requête ou réponse | Exemple |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Données de point d’intérêt | Tableau des détails du point d’intérêt | S.O. | les deux |  |
| `id` | ID du point d’intérêt | affecté | S.O. | réponse | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Nom du point d’intérêt | chaîne | 512 caractères | les deux, facultatif\* | `"name": "My Favorite Place"` |
| `description` | Description du point d’intérêt | chaîne | 512 caractères | les deux, facultatif\* | `"description": "This is a very good place."` |
| `location` | Tableau du type et des coordonnées du point d’intérêt | tableau (mixte) | S.O. | les deux | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Type de point d’intérêt | chaîne | seul « Point » est actuellement pris en charge | les deux, requis dans la requête | `"type": "Point"` |
| `coordinates` | Tableau de longitude et de latitude du point d’intérêt | tableau (flottant) | longitude : -180 à 180, latitude -85 à 85 | les deux, requis dans la requête | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Taille de la barrière géographique circulaire autour du point d’intérêt | float | 10 - 2000 mètres | les deux, requis dans la requête | `"radius": 100` |
| `country` | Pays du point d’intérêt | chaîne | 32 caractères | les deux, facultatif* | `"country": "United States"` |
| `state` | État du point d’intérêt | chaîne | 32 caractères | les deux, facultatif* | `"state": "California"` |
| `city` | Ville du point d’intérêt | chaîne | 32 caractères | les deux, facultatif* | `"city": "San Jose"` |
| `street` | Adresse postale du point d’intérêt | chaîne | 256 caractères | les deux, facultatif* | `"street": "122 Woz Way"` |
| `category` | Catégorie pour le point d’intérêt | chaîne | 100 caractères | les deux, facultatif* | `"category": "cafe"` |
| `icon` | Icône du point d’intérêt | chaîne | 50 caractères | les deux, facultatif* | `"icon": "star"` |
| `color` | Couleur du point d’intérêt | chaîne | 8 caractères | les deux, facultatif* | `"color": "blue"` |
| `metadata` | Tableau de paires clé/valeur pour le point d’intérêt | array(string) | clé : 256 caractères, valeur : 256 caractères, 10 paires au maximum | les deux, facultatif* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID de la bibliothèque dans laquelle se trouve le point d’intérêt | S.O. | S.O. | les deux, obligatoire | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Si la valeur du paramètre n’est pas incluse, elle est définie sur `empty` dans la base de données. Si la paire clé/valeur existante n’est pas incluse, elle est supprimée de la base de données pour ce point d’intérêt.
