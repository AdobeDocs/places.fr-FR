---
title: Utilisation du service Places avec Mobile Services pour la messagerie
description: Cette section vous explique comment utiliser Places Service avec Mobile Services pour la messagerie.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
TQID: https://experienceleague.adobe.com/-axuli6p-QHthMkucGLCcgyHCqrwudXmif-dZwpGli4
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: b069d60e-95f3-44d6-95a8-ddc862a4bc38id: c20d46e7-1c7d-476c-a50e-3961d4dce35fid: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 359
ht-degree: 3%

---

# Adobe Mobile Services {#places-mobile-services}

Avant de pouvoir utiliser l’extension Mobile Services pour la messagerie, passez en revue les conditions préalables suivantes :

* Des points d’intérêt ont été créés dans Places Service. Pour plus d’informations, voir [Créer un point d’intérêt](/help/poi-mgmt-ui/create-a-poi-ui.md).

  >[!IMPORTANT]
  >
  >Le service Places comprend une nouvelle base de données de points d’intérêt améliorée pour votre organisation qui existe en dehors de l’ancienne interface utilisateur de Mobile Services. Les points d’intérêt situés sur la navigation de page Mobile Service *Gérer les emplacements* ne fonctionnent que pour la version 4 de SDK.

* Voici la page de gestion des points d’intérêt *Gérer les emplacements* dans l’ancienne interface utilisateur de Mobile Services pour les versions plus anciennes de SDK :

  ![IU héritée](/help/assets/legacy-location-v4-ui.png)

* Voici l’interface utilisateur du service Places :

  ![Interface utilisateur de gestion des points d’intérêt du service Places](/help/assets/places-ui.png)

* Le SDK ACP est correctement configuré avec l’extension Places .

  Cela signifie que les données sont disponibles sous la forme d’événements et/ou de conditions dans le moteur de règles Experience Platform Launch pour votre application mobile. Pour plus d’informations, voir [Extension Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Familiarisez-vous avec la création et la publication de règles Experience Platform Launch dans le SDK ACP dans votre application mobile.

  Pour plus d’informations, voir [Moteur de règles](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Les éléments de données Experience Platform Launch sont créés à partir des données d’extension Places qui seront utilisées dans le moteur de règles.

  Pour plus d’informations, voir [Éléments de données](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Création de rapports

Avant de pouvoir utiliser la création de rapports, remplissez les conditions préalables suivantes :

* Les données du service Places ont été envoyées dans la suite de rapports Adobe Analytics.

  Pour plus d’informations, voir [Utilisation du service Places avec Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Familiarisez-vous avec la création de rapports Mobile Services.

  Pour plus d’informations, voir [Rapports](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=fr).

## Visualisation des rapports

Vous pouvez exécuter des rapports Mobile Service à l’aide des données Places Service envoyées à Adobe Analytics. Dans l’exemple suivant, des événements sont envoyés lorsque des utilisateurs disposent d’entrées dans l’un des POI. Dans ce rapport, un filtre de l’événement d’entrée de point d’intérêt a été ajouté au rapport d’utilisateur prêt à l’emploi :

![Visualisation des rapports](/help/assets/report-visualize.png)

Une flexibilité supplémentaire dans la visualisation des données du service Places est disponible dans les interfaces Adobe Analytics.
