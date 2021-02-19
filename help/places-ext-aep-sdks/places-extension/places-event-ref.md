---
title: Place la référence de événement
description: 'Liste des événements gérés par l''extension Places. '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 25%

---


# Place la référence de événement {#places-event-reference}

Voici une liste des événements qui sont gérés par l&#39;extension Places.

## GetCurrentPointsOfInterest

**Event Details (Détails de l’événement)**

| Type | Source | Nom | Paired (Couplé) |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Event Description (Description de l’événement)**

Ce événement est une demande de récupération des points d’accès sur lesquels se trouve actuellement le périphérique.

**Définition de la charge utile des données**

n/a

## GetNearbyPointsOfInterest

**Event Details (Détails de l’événement)**

| Type | Source | Nom | Paired (Couplé) |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Event Description (Description de l’événement)**

Ce événement est une demande pour obtenir les points d’intérêt proches en tenant compte de l’emplacement actuel du périphérique et des bibliothèques Places configurées.

**Définition de la charge utile des données**

| Clé | Type de valeur | Obligatoire | Valeur par défaut | Description |
| :--- | :--- | :--- | :--- | :--- |
| latitude | double | true | n/a | Contient la valeur de latitude pour le centre de la recherche des points d’intérêt voisins. |
| longitude | doublon | true | n/a | Contient la valeur de longitude du centre de la recherche des points d’intérêt voisins. |
| radius | entier | false | n/a | Rayon, en mètres, utilisé par la recherche des points d’intérêt proches. |
| count | entier | false | 10 | Nombre maximal de points d’intérêt à renvoyer dans le événement de réponse résultant. |

## ProcessRegionEvent

**Event Details (Détails de l’événement)**

| Type | Source | Nom | Paired (Couplé) |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Event Description (Description de l’événement)**

Ce événement entraîne le traitement par l&#39;extension Places d&#39;un événement d&#39;entrée ou de sortie de géoofence.

**Définition de la charge utile des données**

| Clé | Type de valeur | Obligatoire | Description |
| :--- | :--- | :--- | :--- |
| régionid | chaîne | vrai | ID de la région qui génère le événement. |
| regioneventtype | int | vrai | Type de événement de région généré. 1 pour l&#39;entrée et 2 pour la sortie. |

## Événements expédiés par l&#39;extension Places

Ces informations sont actuellement en cours.

