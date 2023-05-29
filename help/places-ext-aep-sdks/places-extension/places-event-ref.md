---
title: Référence d’événement Places
description: Liste des événements gérés par l’extension Places.
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 29%

---

# Référence d’événement Places {#places-event-reference}

Voici la liste des événements gérés par l&#39;extension Places.

## GetCurrentPointsOfInterest

**Event Details (Détails de l’événement)**

| Type | Source | Nom | Paired (Couplé) |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Event Description (Description de l’événement)**

Cet événement est une requête pour récupérer les points ciblés dans lesquels se trouve actuellement l’appareil.

**Définition de la charge utile des données**

n/a

## GetNearbyPointsOfInterest

**Event Details (Détails de l’événement)**

| Type | Source | Nom | Paired (Couplé) |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Event Description (Description de l’événement)**

Cet événement est une requête pour obtenir les points ciblés à proximité en tenant compte de l’emplacement actuel de l’appareil et des bibliothèques Places configurées.

**Définition de la charge utile des données**

| Clé | Type de valeur | Obligatoire | Valeur par défaut | Description |
| :--- | :--- | :--- | :--- | :--- |
| latitude | double | vrai | n/a | Contient la valeur de latitude pour le centre de la recherche des points ciblés voisins. |
| longitude | double | vrai | n/a | Contient la valeur de longitude pour le centre de la recherche des points ciblés proches. |
| radius | nombre entier | false | n/a | Rayon, en mètres, utilisé par la recherche des points ciblés à proximité. |
| count | nombre entier | false | 10 | Nombre maximal de points ciblés à renvoyer dans l’événement de réponse résultant. |

## ProcessRegionEvent

**Event Details (Détails de l’événement)**

| Type | Source | Nom | Paired (Couplé) |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Event Description (Description de l’événement)**

Cet événement provoque le traitement par l’extension Places d’un événement d’entrée ou de sortie de géo-barrière.

**Définition de la charge utile des données**

| Clé | Type de valeur | Obligatoire | Description |
| :--- | :--- | :--- | :--- |
| région | chaîne | vrai | Identifiant de la région qui génère l’événement. |
| régiononeventtype | int | vrai | Type d’événement de région généré. 1 pour l’entrée et 2 pour la sortie. |

## Événements distribués par l’extension Places

Ces informations sont actuellement en cours.
