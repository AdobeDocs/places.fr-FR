---
title: Place event reference
seo-title: Place event reference
description: 'Liste des événements gérés par l’extension Places. '
seo-description: 'Liste des événements gérés par l’extension Places.  '
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# Place event reference {#places-event-reference}

Voici la liste des événements gérés par l’extension Places.

## GetCurrentPointsOfInterest

**Event Details (Détails de l’événement)**

| Type | Source | Nom | Paired (Couplé) |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Event Description (Description de l’événement)**

Cet événement est une demande de récupération des points d’intérêt sur lesquels se trouve actuellement le périphérique.

**Définition de la charge utile des données**

n/d

## GetNearbyPointsOfInterest

**Event Details (Détails de l’événement)**

| Type | Source | Nom | Paired (Couplé) |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Event Description (Description de l’événement)**

Cet événement est une requête pour obtenir les points d’intérêt proches en prenant en compte l’emplacement actuel du périphérique et les bibliothèques Places configurées.

**Définition de la charge utile des données**

| Clé | Type de valeur | Obligatoire | Valeur par défaut | Description |
| :--- | :--- | :--- | :--- | :--- |
| latitude | double | true | n/d | Contient la valeur de latitude pour le centre de la recherche des points d’intérêt proches. |
| longitude | double | true | n/d | Contient la valeur de longitude pour le centre de la recherche des points d’intérêt proches. |
| radius | integer | false | n/d | Rayon, en mètres, utilisé par la recherche des points d'intérêt proches. |
| count | integer | false | 10 | Nombre maximal de points d’intérêt à renvoyer dans l’événement de réponse résultant. |

## ProcessRegionEvent

**Event Details (Détails de l’événement)**

| Type | Source | Nom | Paired (Couplé) |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Event Description (Description de l’événement)**

L’extension Places traite alors un événement d’entrée ou de sortie de géofence.

**Définition de la charge utile des données**

| Clé | Type de valeur | Obligatoire | Description |
| :--- | :--- | :--- | :--- |
| régionid | string | true | ID de la région qui génère l’événement. |
| regioneventtype | int | true | Type d’événement de région généré. 1 pour l'entrée et 2 pour la sortie. |

## Evénements distribués par l’extension Places

Ces informations sont actuellement en cours.

