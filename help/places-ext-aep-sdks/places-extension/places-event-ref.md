---
title: Référence d’événement Places
description: Une liste des événements gérés par l'extension Places.
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a8a79b8d-fdca-499c-a5ef-f88a099d8eb9
    internal-label: Mobile SDK
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 17%
---
# Référence d’événement Places {#places-event-reference}

Voici une liste des événements gérés par l&#39;extension Places.

## GetCurrentPointsOfInterest

**Détails de l’événement**

| Type | Source | Nom | Apparié |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Description de l’événement**

Cet événement est une demande de récupération des points d’intérêt dans lesquels se trouve actuellement l’appareil.

**Définition de la payload des données**

S.O.

## GetNearbyPointsOfInterest

**Détails de l’événement**

| Type | Source | Nom | Apparié |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Description de l’événement**

Cet événement est une demande d&#39;obtention des points d&#39;intérêt à proximité en prenant en compte l&#39;emplacement actuel de l&#39;appareil et les bibliothèques Places configurées.

**Définition de la payload des données**

| Clé | Type de valeur | Obligatoire | Valeur par défaut | Description |
| :--- | :--- | :--- | :--- | :--- |
| latitude | double | vrai | S.O. | Contient la valeur de latitude pour le centre de la recherche des points d’intérêt à proximité. |
| longitude | double | vrai | S.O. | Contient la valeur de longitude du centre de la recherche des points d’intérêt à proximité. |
| rayon | entier | False | S.O. | Rayon, en mètres, utilisé par la recherche des POI à proximité. |
| count | entier | False | 10 | Nombre maximal de POI à renvoyer dans l’événement de réponse obtenu. |

## ProcessRegionEvent

**Détails de l’événement**

| Type | Source | Nom | Apparié |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Description de l’événement**

Cet événement entraîne le traitement par l’extension Places d’un événement d’entrée ou de sortie de limite géographique.

**Définition de la payload des données**

| Clé | Type de valeur | Obligatoire | Description |
| :--- | :--- | :--- | :--- |
| regionid | chaîne | vrai | Identifiant de la région qui génère l’événement. |
| regioneventtype | int | vrai | Type d’événement de région en cours de génération. 1 pour l&#39;entrée et 2 pour la sortie. |

## Événements envoyés par l’extension Places

Cette information est en cours.
