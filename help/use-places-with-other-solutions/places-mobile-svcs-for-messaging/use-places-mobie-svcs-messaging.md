---
title: Utilisation du service Places avec Mobile Services pour la messagerie
description: Cette section vous explique comment utiliser Places Service avec Mobile Services pour la messagerie.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 1%

---


# Adobe Mobile Services {#places-mobile-services}

Avant de pouvoir utiliser l’extension Mobile Services pour la messagerie, vérifiez les conditions préalables suivantes :

* Des points d&#39;intérêt ont été créés dans le service Places. Pour plus d’informations, voir [Création d’un POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Le service Places comprend une nouvelle base de données d’API améliorée pour votre entreprise qui existe en dehors de l’interface utilisateur héritée de Mobile Services. Les points d’accès situés sur la page Service mobile *Gérer les emplacements* ne fonctionnent que pour la version 4 du SDK.

* Voici la *page de gestion des emplacements* POI dans l’interface utilisateur héritée de Mobile Services pour les anciennes versions du SDK :

   ![Interface utilisateur héritée](/help/assets/legacy-location-v4-ui.png)

* Voici l’interface utilisateur du service Places :

   ![Interface utilisateur de gestion des points d’accès du service Places](/help/assets/places-ui.png)

* Le SDK ACP est correctement configuré avec les extensions du service Places et/ou du moniteur Places.

   Cela signifie que les données sont disponibles en tant que événements et/ou conditions dans le moteur de règles Experience Platform Launch pour votre application mobile. Pour plus d’informations, voir [Place extension](/help/places-ext-aep-sdks/places-extension/places-extension.md) ou [Place Monitor extension](/help/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md).

* Familiarisez-vous avec la création et la publication de règles Experience Platform Launch au SDK ACP dans votre application mobile.

   Pour plus d’informations, voir [Moteur de règles](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Les éléments de données Experience Platform Launch sont créés à partir des données de l&#39;extension Places qui seront utilisées dans le moteur de règles.

   Pour plus d’informations, voir [Éléments de données](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Création de rapports

Avant d’utiliser le rapports, remplissez les conditions préalables suivantes :

* Envoi réussi des données du service Lieux vers la suite de rapports Adobe Analytics.

   Pour plus d’informations, voir [Utiliser le service Lieux avec Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Familiarisez-vous avec Mobile Services rapports.

   Pour plus d&#39;informations, voir [Rapports](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Visualisation des rapports

Vous pouvez exécuter des rapports Mobile Service à l’aide de données du service Places qui sont envoyées à Adobe Analytics. Dans l’exemple suivant, des événements sont envoyés lorsque des utilisateurs ont des entrées dans l’une des API. Dans ce rapport, un filtre du événement d’entrée de la page d’accueil a été ajouté sur le rapport utilisateur prêt à l’emploi :

![Visualisation des rapports](/help/assets/report-visualize.png)

Les interfaces Adobe Analytics offrent une plus grande souplesse dans la visualisation des données du service Places.

