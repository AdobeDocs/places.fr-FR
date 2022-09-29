---
title: Places Service
description: Places Service est un contexte important pour comprendre l’engagement des utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et attrayante.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: c13da9ea3dc0cd574f2f9a496405867f7d36eae0
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 10%

---

# Places Service {#home}

La localisation est un contexte important pour comprendre et interagir avec les utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et attrayante.

Places Service, anciennement appelé Adobe Experience Platform Location Service, est un service de géolocalisation qui permet aux applications mobiles reconnaissant l’emplacement de l’utilisateur de comprendre le contexte de l’emplacement à l’aide d’interfaces SDK enrichies et faciles à utiliser, accompagnées d’une base de données flexible de points ciblés (POI).

Places Service vous permet d’effectuer les opérations suivantes :

* Créez et gérez une base de données de POI pouvant être utilisée avec d’autres solutions Adobe Experience Cloud.
* Associez des métadonnées personnalisées aux points ciblés pour les rendre plus riches et plus significatifs en spécifiant des attributs supplémentaires.
* Visualisez les points ciblés sur une carte pour comprendre facilement le contexte spatial et ajouter/modifier des attributs de métadonnées.
* Configurez le SDK dans Adobe Experience Platform Launch pour définir les règles déclenchées par l’emplacement et les conditions basées sur les métadonnées.
* Réduisez le code que vous devez écrire pour surveiller l’emplacement d’un appareil et utilisez l’extension Places pour déclencher automatiquement les règles spécifiques à l’emplacement.

Cela vous permet d’agir à partir des signaux de localisation en temps réel, quand et où c’est important. Le contexte approprié fournit une expérience d’engagement mobile plus enrichissante.

Voici quelques-unes des façons d&#39;utiliser Places :

* envoyer une notification en temps réel lorsqu’une personne entre dans un point ciblé ; *&quot;Hé...bienvenue au stade.&quot;*
* Comparez le trafic de pied de vos propres magasins à celui de vos concurrents.
* Segmenter une audience en fonction du comportement hors ligne à l’aide de profils d’audience avec un contexte d’emplacement.
* Ciblez un utilisateur avec une expérience en magasin, le cas échéant.

## Composants du service Places

Places Service comprend les composants suivants :

* **Service Web**

   Vous pouvez créer et gérer des points ciblés à l’aide des API REST Places. Pour plus d’informations sur les API REST, voir [Gestion des bibliothèques](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) et [Gestion des points ciblés](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interface de gestion des points ciblés**

   Visualisez les points ciblés sur une carte pour comprendre le contexte spatial et ajouter/modifier les points ciblés et leurs métadonnées personnalisées.

* **Extension Places**

   L’interface d’API mobile multiplateforme pour intégrer le contexte d’emplacement dans vos applications mobiles. Pour plus d’informations sur les SDK, voir [Extension Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Règles de lancement**

   Les règles Launch géointelligentes vous permettent de déclencher des actions avec des événements d’entrée et de sortie. Les règles vous permettent également d’utiliser des attributs géographiques dans des conditions pour personnaliser l’expérience.

* **Extension Places Monitor**

   Le SDK mobile multiplateforme qui peut être incorporé dans votre application mobile pour surveiller automatiquement les modifications d’emplacement de votre utilisateur et déclencher des règles Places. Pour plus d’informations, voir [Extension Places Monitor](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

## Terminologie

Voici quelques termes courants utilisés dans cette documentation :

* A **Point ciblé** est un emplacement géographique qui intéresse votre entreprise.

   Vous pouvez définir des points ciblés avec des attributs tels que le nom, le rayon, l’adresse, la catégorie et les balises de métadonnées.

* A **geofence** est un type de point ciblé.

   Ce type de point ciblé est une limite géographique virtuelle définie par les coordonnées de latitude et de longitude.

* A **beacon** est un type de point ciblé.

   Ce type de point ciblé est un appareil physique qui représente un emplacement en émettant un signal Bluetooth à faible puissance. La prise en charge des balises sera disponible dans une version ultérieure.

* Une **bibliothèque** est une collection de POI permettant l’association plus simple de règles à un ensemble de POI plutôt qu’à un POI unique.

* Un **extension** est l’extension Experience Platform Launch requise pour intégrer le SDK Places dans vos applications mobiles.

   Extension utilisée avec les autres SDK mobiles pour ajouter un contexte d’emplacement à vos expériences.

* Une **organisation** est l’entité Adobe qui identifie votre société dans Adobe Experience Cloud.

   En règle générale, une organisation correspond au nom de votre société. Cependant, une société peut avoir plusieurs organisations. L’administrateur de l’organisation peut configurer des groupes et des utilisateurs et configurer la fonctionnalité d’authentification unique.

* L’**orgID** est l’identifiant représentant votre organisation dans Adobe Experience Platform.

   Pour plus d’informations, voir [Recherche de votre orgID](https://forums.adobe.com/thread/2339895).

* Le **ID Experience Cloud** Le service fournit un identifiant universel et permanent qui identifie vos visiteurs à l’échelle de toutes les solutions de l’Experience Cloud.

   Pour plus d’informations, voir [Aperçu](https://docs.adobe.com/content/help/fr-FR/id-service/using/intro/overview.html).
