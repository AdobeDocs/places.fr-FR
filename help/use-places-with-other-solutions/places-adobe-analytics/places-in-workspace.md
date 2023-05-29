---
title: Rapport sur les données de localisation dans Analytics Workspace
description: Cette section fournit des informations sur la manière de créer des rapports sur les données de localisation dans Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 8%

---

# Rapport sur les données d’emplacement dans Analytics Workspace {#places-in-workspace}

Ce document présente un exemple de rapport sur vos données d’emplacement dans Analytics Workspace. Chaque étape contient un résumé de haut niveau, avec les détails fournis en référençant d’autres pages de documentation.

## Conditions préalables

Ce document suppose les éléments suivants :

1. L’extension Places est implémentée dans votre application.

   Pour plus d’informations sur l’implémentation de l’extension Places, voir [Extensions Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. L’utilisateur Adobe Analytics est administrateur et a accès aux règles de traitement.

   Pour plus d’informations sur les règles de traitement, voir l’[Aperçu des règles de traitement](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

1. Dans la propriété Launch, des éléments de données ont été créés pour les variables du service Places que vous souhaitez.

   Pour plus d’informations sur les éléments de données dans Launch, voir [Définition d’un élément de données](/help/use-places-launch-workflow/define-data-elements.md).


## 1. Création d’une règle Launch

Créez une règle qui fera en sorte que le SDK envoie des données à Analytics lorsque l’appareil entre dans un point ciblé. La création de ce type de règle est décrite dans la section [Envoi de données d’entrée et de sortie de point ciblé à Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) page.

Dans cet exemple, l’action de la règle a les valeurs suivantes définies pour la requête Analytics :

* **[!UICONTROL Action]** reçoit une valeur de **[!UICONTROL Entrée Places]**.

* Clé de données contextuelles **[!UICONTROL poi.name]** est défini sur la valeur de l’élément de données **[!UICONTROL {%%Nom du point ciblé%}]**.

![&quot;définir une action&quot;](/help/assets/pt-setAction.png)

## 2. Création de variables Analytics

Pour mapper les données contextuelles (envoyées à l’étape 1), les variables doivent d’abord être créées pour la suite de rapports Analytics. Pour plus d’informations sur la création de variables dans Analytics, voir [Variables de conversion (eVars)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html).

Dans cet exemple, une variable de conversion, **[!UICONTROL Evar2]**, a été créé et nommé **[!UICONTROL Nom du point ciblé Places]**. Des variables supplémentaires doivent être créées pour chaque variable d’emplacement que vous souhaitez afficher dans les rapports.

![&quot;création d’une variable Analytics&quot;](/help/assets/aa-evar.png)

## 3. Création de règles de traitement

Cette étape est nécessaire pour mapper les données contextuelles (étape 1) aux variables Analytics (étape 2). Pour plus d’informations sur la création de règles de traitement, voir [Règles de traitement - Aperçu](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Dans cet exemple, une règle de traitement a été créée pour mapper la valeur de données contextuelles. **[!UICONTROL poi.name]** into **[!UICONTROL Nom du point ciblé Places (eVar2)]**. Des règles de traitement supplémentaires doivent être créées pour chaque variable d’emplacement créée.

![&quot;créer une règle de traitement&quot;](/help/assets/aa-processing-rule.png)

## 4. Générer un rapport dans Workspace

Cette étape affiche un rapport de base dans Analytics Workspace pour afficher les données collectées aux étapes 1 à 3. Pour plus d’informations sur l’utilisation d’Analytics Workspace, voir [Présentation d’Analytics Workspace](https://docs.adobe.com/content/help/fr-FR/analytics/analyze/analysis-workspace/home.html).

Dans cet exemple, les paramètres du rapport sont les suivants :

* Mesure - **[!UICONTROL Occurrences]**

* Dimension - **[!UICONTROL Nom de l’action]**

   * Répartition par Dimension - **[!UICONTROL Nom du point ciblé Places]**

![&quot;créer un rapport dans l’espace de travail&quot;](/help/assets/aa-workspace.png)
