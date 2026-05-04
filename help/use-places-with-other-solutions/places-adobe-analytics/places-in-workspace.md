---
title: Rapport sur les données de localisation dans Analytics Workspace
description: Cette section fournit des informations sur la création de rapports sur les données d’emplacement dans Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
TQID: https://experienceleague.adobe.com/Xym9Ko8czyd3wYWVo22sQoK6gk-VvftGVHfIDUys06E
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 483
ht-degree: 6%

---

# Rapport sur les données de localisation dans Analytics Workspace {#places-in-workspace}

Ce document présente un exemple de création de rapports sur vos données d’emplacement dans le Workspace Analytics. Chaque étape contient un résumé général, avec des détails fournis en référençant d’autres pages de documentation.

## Conditions préalables

Ce document suppose ce qui suit :

1. L’extension Places est implémentée dans votre application.

   Pour plus d’informations sur l’implémentation de l’extension Places, voir [Extensions Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. L’utilisateur Adobe Analytics est un administrateur et a accès aux règles de traitement.

   Pour plus d’informations sur les règles de traitement, voir l’[Aperçu des règles de traitement](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=fr).

1. Dans la propriété Launch, des éléments de données ont été créés pour les variables du service Places que vous souhaitez.

   Pour plus d’informations sur les éléments de données dans Launch, voir [Définition d’un élément de données](/help/use-places-launch-workflow/define-data-elements.md).


## &#x200B;1. Création d’une règle Launch

Créez une règle qui amènera le SDK à envoyer des données à Analytics lorsque l’appareil accède à un point d’intérêt. La création de ce type de règle est décrite à la page [Envoyer des données d’entrée et de sortie de point d’intérêt à Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

Dans cet exemple, les valeurs suivantes sont définies pour la requête Analytics de l’action de la règle :

* La valeur fournie pour **[!UICONTROL Action]** est **[!UICONTROL Entrée Places]**.

* La clé de données contextuelles **[!UICONTROL poi.name]** est définie sur la valeur de l’élément de données **[!UICONTROL {%%POI Name%}]**.

![« définir une action »](/help/assets/pt-setAction.png)

## &#x200B;2. Création de variables Analytics

Pour mapper les données contextuelles (envoyées à l’étape 1), les variables doivent d’abord être créées pour la suite de rapports Analytics. Pour plus d’informations sur la création de variables dans Analytics, voir [Variables de conversion (eVars)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=fr).

Dans cet exemple, une variable de conversion, **[!UICONTROL Evar2]**, a été créée et nommée **[!UICONTROL Places POI Name]**. Des variables supplémentaires doivent être créées pour chaque variable d’emplacement que vous souhaitez exposer dans les rapports.

![« créer une variable analytics »](/help/assets/aa-evar.png)

## &#x200B;3. Création de règles de traitement

Cette étape est nécessaire pour mapper les données contextuelles (étape 1) aux variables Analytics (étape 2). Pour plus d’informations sur la création de règles de traitement, voir [&#x200B; Présentation des règles de traitement &#x200B;](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=fr).

Dans cet exemple, une règle de traitement a été créée pour mapper la valeur des données contextuelles **[!UICONTROL poi.name]** dans **[!UICONTROL Nom du point de contact Places (eVar2)]**. Des règles de traitement supplémentaires devront être créées pour chaque variable d’emplacement créée.

![« créer une règle de traitement »](/help/assets/aa-processing-rule.png)

## &#x200B;4. Générer un rapport dans Workspace

Cette étape présente un rapport de base dans Analytics Workspace pour afficher les données collectées lors des étapes 1 à 3. Pour plus d’informations sur l’utilisation d’Analytics Workspace, consultez [Présentation d’Analytics Workspace](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=fr).

Dans cet exemple, le rapport présente les paramètres suivants :

* Mesure - **[!UICONTROL Occurrences]**

* Dimension - **[!UICONTROL Nom de l’action]**

   * Répartition par Dimension - **[!UICONTROL Nom du point d’intérêt Places]**

![« créer un rapport dans workspace »](/help/assets/aa-workspace.png)
