---
title: Rapport sur les données d’emplacement dans Analytics Workspace
description: Cette section fournit des informations sur la manière de créer des rapports sur les données d’emplacement dans Analytics Workspace.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Rapport sur les données d’emplacement dans Analytics Workspace {#places-in-workspace}

Ce document présente un exemple de rapport sur les données de votre emplacement dans Analytics Workspace. Chaque étape contiendra un résumé de haut niveau, avec les détails fournis en référençant d&#39;autres pages de documentation.

## Conditions préalables 

Ce document suppose ce qui suit :

1. L’extension Adobe Places est implémentée dans votre application. Pour plus d’informations sur l’implémentation d’Adobe Places, voir [Places extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. L’utilisateur d’Adobe Analytics est un administrateur et a accès aux règles de traitement. Pour plus d’informations sur les règles de traitement, voir l’[Aperçu des règles de traitement](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

1. Dans la propriété Launch, des éléments de données ont été créés pour les variables de service d’emplacement souhaitées. Pour plus d’informations sur les éléments de données dans Lancement, voir [Définition d’un élément](/help/use-places-launch-workflow/define-data-elements.md)de données.


## 1. Création d’une règle de lancement

Créez une règle qui fera en sorte que le SDK envoie des données à Analytics lorsque le périphérique entre dans un point d’accès. La création de ce type de règle est décrite dans la page [Envoyer les données d’entrée et de sortie du point d’accès vers Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) .

Dans cet exemple, les valeurs suivantes sont définies pour la requête Analytics pour l’action de la règle :

* **[!UICONTROL Action]**est fournie avec la valeur de**[!UICONTROL Places Entry]**.

* La clé de données contextuelles **[!UICONTROL poi.name]**est définie sur la valeur de l’élément de données**[!UICONTROL {%%POI Name%%}]**.

![&quot;définir une action&quot;](/help/assets/pt-setAction.png)

## 2. Création de variables Analytics

Pour mapper les données contextuelles (envoyées à l’étape 1), les variables doivent d’abord être créées pour la suite de rapports Analytics. Pour plus d’informations sur la création de variables dans Analytics, voir Variables de [conversion \(eVars\)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html).

Dans cet exemple, une variable de conversion **[!UICONTROL Evar2]**a été créée et nommée**[!UICONTROL Places POI Name]**. D’autres variables devront être créées pour chaque variable d’emplacement à exposer dans les rapports.

![&quot;création d’une variable d’analyse&quot;](/help/assets/aa-evar.png)

## 3. Création de règles de traitement

Cette étape est nécessaire pour mapper les données contextuelles (étape 1) aux variables Analytics (étape 2). For more information on creating processing rules, see [Processing rules overview](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Dans cet exemple, une règle de traitement a été créée pour mapper la valeur des données contextuelles **[!UICONTROL poi.name]**dans**[!UICONTROL Places POI Name \(eVar2\)]**. Des règles de traitement supplémentaires devront être créées pour chaque variable d’emplacement créée.

![&quot;créer une règle de traitement&quot;](/help/assets/aa-processing-rule.png)

## 4. Générer un rapport dans Workspace

Cette étape présente un rapport de base dans Analytics Workspace pour afficher les données collectées aux étapes 1 à 3. Pour plus d’informations sur l’utilisation d’Analytics Workspace, voir Présentation [d’](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/analysis-workspace-features.html)Analytics Workspace.

Dans cet exemple, le rapport comporte les paramètres suivants :

* Mesure - **[!UICONTROL Occurrences]**

* Dimension - **[!UICONTROL Action Name]**

   * Répartition par dimension - **[!UICONTROL Places POI Name]**

![&quot;créer un rapport dans l’espace de travail&quot;](/help/assets/aa-workspace.png)
