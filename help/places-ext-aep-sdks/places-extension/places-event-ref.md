---
title: Référence d’événement Places
description: Liste des événements gérés par l’extension Places.
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 17%

---

# Référence d’événement Places {#places-event-reference}

Voici la liste des événements gérés par l&#39;extension Places.

## GetCurrentPointsOfInterest

**Détails de l’événement**

| Type | Source | Nom | Paire |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Description de l’événement**

Cet événement est une requête pour récupérer les points ciblés dans lesquels se trouve actuellement l’appareil.

**Définition de la charge utile de données**

S.O.

## GetNearbyPointsOfInterest

**Détails de l’événement**

| Type | Source | Nom | Paire |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Description de l’événement**

Cet événement est une requête pour obtenir les points ciblés à proximité en tenant compte de l’emplacement actuel de l’appareil et des bibliothèques Places configurées.

**Définition de la charge utile de données**

| Clé | Type de valeur | Obligatoire | Valeur par défaut | Description |
| :--- | :--- | :--- | :--- | :--- |
| latitude | double | vrai | S.O. | Contient la valeur de latitude pour le centre de la recherche des points ciblés voisins. |
| longitude | double | vrai | S.O. | Contient la valeur de longitude pour le centre de la recherche des points ciblés proches. |
| radius | Entier | false | S.O. | Rayon, en mètres, utilisé par la recherche des points ciblés à proximité. |
| count | Entier | false | 10 | Nombre maximal de points ciblés à renvoyer dans l’événement de réponse résultant. |

## ProcessRegionEvent

**Détails de l’événement**

| Type | Source | Nom | Paire |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Description de l’événement**

Cet événement provoque le traitement par l’extension Places d’un événement d’entrée ou de sortie de géo-barrière.

**Définition de la charge utile de données**

| Clé | Type de valeur | Obligatoire | Description |
| :--- | :--- | :--- | :--- |
| région | Chaîne | vrai | Identifiant de la région qui génère l’événement. |
| régiononeventtype | int | vrai | Type d’événement de région généré. 1 pour entrée et 2 pour sortie. |

## Événements distribués par l’extension Places

Ces informations sont actuellement en cours.
