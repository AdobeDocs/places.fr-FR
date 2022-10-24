---
title: Utilisation de Places Service avec Mobile Services pour la messagerie
description: Cette section vous explique comment utiliser Places Service avec Mobile Services pour la messagerie.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

Avant d’utiliser l’extension Mobile Services pour la messagerie, vérifiez les conditions préalables suivantes :

* Des points ciblés ont été créés dans Places Service. Pour plus d’informations, voir [Création d’un point ciblé](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Le service Places comprend une nouvelle base de données POI améliorée pour votre organisation, qui existe en dehors de l’ancienne interface utilisateur de Mobile Services. Points ciblés situés sur Mobile Service *Gérer les emplacements* La navigation dans les pages ne fonctionne que pour la version 4 du SDK.

* Voici la *Gestion des emplacements* Page de gestion des points ciblés dans l’ancienne interface utilisateur de Mobile Services pour les versions plus anciennes du SDK :

   ![Interface utilisateur héritée](/help/assets/legacy-location-v4-ui.png)

* Voici l’interface utilisateur du service Places :

   ![Interface utilisateur de gestion des points ciblés de Places Service](/help/assets/places-ui.png)

* Le SDK ACP est correctement configuré avec l’extension Places.

   Cela signifie que les données sont disponibles en tant qu’événements et/ou conditions dans le moteur de règles de l’Experience Platform Launch pour votre application mobile. Pour plus d’informations, voir [Extension Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Familiarisez-vous avec la création et la publication de règles Experience Platform Launch sur le SDK ACP dans votre application mobile.

   Pour plus d’informations, voir [Moteur de règles](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Les éléments de données Experience Platform Launch sont créés à partir des données de l’extension Places qui seront utilisées dans le moteur de règles.

   Pour plus d’informations, voir [Éléments de données](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Création de rapports

Pour pouvoir utiliser la création de rapports, remplissez les conditions préalables suivantes :

* Envoi réussi des données du service Places dans la suite de rapports Adobe Analytics.

   Pour plus d’informations, voir [Utilisation du service Places avec Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Familiarisez-vous avec les rapports Mobile Services.

   Pour plus d’informations, voir [Rapports](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Visualisation des rapports

Vous pouvez exécuter des rapports Mobile Service à l’aide des données de Places Service envoyées à Adobe Analytics. Dans l’exemple suivant, des événements sont envoyés lorsque les utilisateurs ont des entrées dans l’un des points ciblés. Dans ce rapport, un filtre de l’événement d’entrée de POI a été ajouté sur le rapport utilisateur d’usine :

![Visualisation des rapports](/help/assets/report-visualize.png)

Une flexibilité supplémentaire pour visualiser les données de Places Service est disponible dans les interfaces Adobe Analytics.
