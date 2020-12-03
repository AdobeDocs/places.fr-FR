---
title: Rapport sur les données d’emplacement dans Analytics Workspace
description: Cette section fournit des informations sur la manière de créer des rapports sur les données d’emplacement dans Analytics Workspace.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 9%

---


# Rapport sur les données d’emplacement dans Analytics Workspace {#places-in-workspace}

Ce document présente un exemple de rapport sur les données de votre emplacement dans Analytics Workspace. Chaque étape contient un résumé de haut niveau, avec des détails fournis en référençant d&#39;autres pages de documentation.

## Conditions préalables 

Ce document suppose ce qui suit :

1. L&#39;extension Places est implémentée dans votre application.

   Pour plus d’informations sur l’implémentation de l’extension Places, voir [Extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md)Places.

1. L’utilisateur Adobe Analytics est un administrateur et a accès aux règles de traitement.

   Pour plus d’informations sur les règles de traitement, voir l’[Aperçu des règles de traitement](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

1. Dans la propriété Launch, des éléments de données ont été créés pour les variables du service Places que vous souhaitez.

   Pour plus d’informations sur les éléments de données dans Lancement, voir [Définition d’un élément](/help/use-places-launch-workflow/define-data-elements.md)de données.


## 1. Création d’une règle de lancement

Créez une règle qui fera en sorte que le SDK envoie des données à Analytics lorsque l’appareil entre dans un point d’intérêt. La création de ce type de règle est décrite sur la page [Envoyer les données d’entrée et de sortie du point d’accès à Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) .

Dans cet exemple, les valeurs suivantes sont définies pour l’action de la règle pour la demande Analytics :

* **[!UICONTROL Action]** est fourni avec la valeur de **[!UICONTROL Places Entry]**.

* La clé de données contextuelles **[!UICONTROL poi.name]** est définie sur la valeur de l’élément de données **[!UICONTROL {%%POI Name%%}]**.

![&quot;définir une action&quot;](/help/assets/pt-setAction.png)

## 2. Création de variables Analytics

Pour mapper les données contextuelles (envoyées à l’étape 1), les variables doivent d’abord être créées pour la suite de rapports Analytics. Pour plus d’informations sur la création de variables dans Analytics, voir Variables de [conversion (eVars)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html).

Dans cet exemple, une variable de conversion **[!UICONTROL Evar2]** a été créée et nommée **[!UICONTROL Places POI Name]**. D’autres variables devront être créées pour chaque variable d’emplacement à exposer dans le rapports.

![&quot;création d’une variable d’analyse&quot;](/help/assets/aa-evar.png)

## 3. Création de règles de traitement

Cette étape est nécessaire pour mapper les données contextuelles (étape 1) aux variables Analytics (étape 2). For more information on creating processing rules, see [Processing rules overview](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Dans cet exemple, une règle de traitement a été créée pour mapper la valeur des données contextuelles **[!UICONTROL poi.name]** à **[!UICONTROL Places POI Name (eVar2)]**. D’autres règles de traitement devront être créées pour chaque variable d’emplacement créée.

![&quot;créer une règle de traitement&quot;](/help/assets/aa-processing-rule.png)

## 4. Générez un rapport dans Workspace.

Cette étape présente un rapport de base dans Analytics Workspace pour vue des données collectées aux étapes 1 à 3. Pour plus d’informations sur l’utilisation d’Analytics Workspace, voir Présentation [d’](https://docs.adobe.com/content/help/fr-FR/analytics/analyze/analysis-workspace/home.html)Analytics Workspace.

Dans cet exemple, le rapport comporte les paramètres suivants :

* Mesure - **[!UICONTROL Occurrences]**

* Dimension - **[!UICONTROL Action Name]**

   * Répartition par Dimension - **[!UICONTROL Places POI Name]**

![&quot;créer un rapport dans l’espace de travail&quot;](/help/assets/aa-workspace.png)
