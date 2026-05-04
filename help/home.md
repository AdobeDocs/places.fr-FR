---
title: Places Service
description: Places Service est un contexte important pour comprendre l'engagement des utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et plus attrayante.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
TQID: https://experienceleague.adobe.com/4kI1AuV2l-qfC3mOrcsoG9NDRcOPJBdkWPmKkQuDIJk
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 684
ht-degree: 9%

---

# Places Service {#home}

L’emplacement est un contexte important pour comprendre et interagir avec les utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et plus attrayante.

Places Service, précédemment connu sous le nom de Adobe Experience Platform Location Service, est un service de géolocalisation qui permet aux applications mobiles reconnaissant l’emplacement de l’utilisateur de comprendre le contexte de l’emplacement grâce à l’utilisation d’interfaces SDK enrichies et faciles à utiliser, accompagnées d’une base de données flexible de points ciblés (POI).

Places Service vous permet d’atteindre les objectifs suivants :

* Créez et gérez une base de données de points d’intérêt pouvant être utilisés avec d’autres solutions Adobe Experience Cloud.
* Joignez des métadonnées personnalisées aux points d’intérêt pour les enrichir et les rendre plus significatifs en spécifiant des attributs supplémentaires.
* Visualisez les points d’intérêt sur une carte pour comprendre facilement le contexte spatial et ajouter/modifier des attributs de métadonnées.
* Configurez le SDK dans Adobe Experience Platform Launch pour définir vos règles déclenchées par l’emplacement et vos conditions basées sur les métadonnées.
* Réduisez le code que vous devez écrire pour surveiller l’emplacement d’un appareil et utilisez l’extension Places pour déclencher automatiquement les règles spécifiques à l’emplacement.

Cela vous permettra de prendre des mesures à partir des signaux de localisation en temps réel, quand et où cela importe. Le bon contexte offre une expérience d’engagement mobile plus enrichissante.

Voici quelques-unes des façons d&#39;utiliser Places :

* Envoyer une notification en temps réel quand quelqu&#39;un entre dans un point d&#39;intérêt, *« Hé.. bienvenue au stade.«*
* Analysez le trafic piétonnier de vos propres magasins par rapport à celui de vos concurrents.
* Segmentez une audience en fonction du comportement hors ligne à l’aide de profils d’audience avec un contexte d’emplacement.
* Ciblez un utilisateur disposant d’une expérience en magasin, le cas échéant.

## Composants du service Places

Le service Places comprend les éléments suivants :

* **Service Web**

  Vous pouvez créer et gérer des points d’intérêt à l’aide des API REST Places. Pour plus d’informations sur les API REST, voir [Gestion des bibliothèques](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) et [Gestion des POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interface de gestion des points d’intérêt**

  Visualisez les points d’intérêt sur une carte pour comprendre le contexte spatial et ajouter/modifier des points d’intérêt et leurs métadonnées personnalisées.

* **Extension Places**

  Interface d’API mobile multi-plateforme permettant d’intégrer le contexte de l’emplacement dans vos applications mobiles. Pour plus d’informations sur les SDK, voir [Extension Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Règles de Launch**

  Les règles de lancement géo-intelligentes qui vous permettent de déclencher des actions avec des événements d’entrée et de sortie. Les règles vous permettent également d’utiliser des attributs géographiques dans des conditions pour personnaliser l’expérience.

## Terminologie

Voici quelques termes courants utilisés dans cette documentation :

* Un **point d’intérêt)** est un emplacement géographique qui présente un intérêt pour votre organisation.

  Vous pouvez définir des POI avec des attributs tels qu’un nom, un rayon, une adresse, une catégorie et des balises de métadonnées.

* Une **limite géographique** est un type de point d’intérêt.

  Ce type de point d’intérêt est une limite géographique virtuelle définie par les coordonnées de latitude et de longitude.

* Une **balise** est un type de point d’intérêt.

  Ce type de point d&#39;intérêt est un appareil physique qui représente un emplacement en émettant un signal Bluetooth de faible puissance. La prise en charge des balises sera assurée dans une version ultérieure.

* Une **bibliothèque** est une collection de POI permettant l’association plus simple de règles à un ensemble de POI plutôt qu’à un POI unique.

* Une **extension** est l’extension d’Experience Platform Launch requise pour intégrer Places SDK dans vos applications mobiles.

  L’extension utilisée avec les autres SDK mobiles pour ajouter du contexte d’emplacement à vos expériences.

* Une **organisation** est l’entité Adobe qui identifie votre société dans Adobe Experience Cloud.

  En règle générale, une organisation correspond au nom de votre société. Cependant, une entreprise peut avoir plusieurs organisations. L’administrateur de l’organisation peut configurer des groupes et des utilisateurs, ainsi que la fonctionnalité d’authentification unique.

* L’**orgID** est l’identifiant représentant votre organisation dans Adobe Experience Platform.

  Pour plus d’informations, voir [Recherche de l’ID d’organisation](https://forums.adobe.com/thread/2339895).

* Le service **Experience Cloud ID** fournit un identifiant universel et persistant qui identifie vos visiteurs dans toutes les solutions d’Experience Cloud.

  Pour plus d’informations, voir [Aperçu](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=fr).

