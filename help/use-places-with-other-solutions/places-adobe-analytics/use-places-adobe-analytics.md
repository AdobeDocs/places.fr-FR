---
title: Envoi de données d’entrée et de sortie de point ciblé à Analytics
description: Cette section fournit des informations sur la manière d’envoyer des données d’entrée et de sortie de point ciblé à Analytics.
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 4%

---

# Envoi de données d’entrée et de sortie de point ciblé à Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>Cette section suppose que le service Places est implémenté dans votre application. Pour plus d’informations sur l’implémentation de Places Service, voir [Extensions Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Une fois que le service Places a envoyé les événements d’entrée et de sortie, vous pouvez créer des règles dans Experience Platform Launch pour envoyer les données du service Places à Adobe Analytics. Pour créer ce type de règle, sélectionnez votre propriété dans Launch et procédez comme suit :

## 1. Création d’une règle

1. Sur le **[!UICONTROL Règles]** , cliquez sur **[!UICONTROL Créer une règle]**.

   Gardez à l’esprit les informations suivantes :

   * Si vous ne disposez pas de règles existantes pour cette propriété, la variable **[!UICONTROL Créer une règle]** se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, la variable **[!UICONTROL Créer une règle]** se trouve en haut à droite de l’écran.

## 2. Sélection d’un événement

1. Saisissez un nom significatif pour votre règle.

   Ainsi, la règle sera facilement reconnaissable dans votre liste de règles. Dans cet exemple, la règle est nommée **[!UICONTROL Envoi de données à Analytics]**.

1. Dans la section **[!UICONTROL Events]**, cliquez sur **[!UICONTROL Add]**.

1. Dans la **[!UICONTROL Extension]** liste déroulante, sélectionnez **[!UICONTROL Places Service]**.

1. Dans la **[!UICONTROL Type d’événement]** liste déroulante, sélectionnez **[!UICONTROL Entrée dans le point ciblé]**.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

   ![&quot;sélectionner un événement&quot;](/help/assets/pt-selectEvent.png)


## 3. Ajouter des conditions

>[!IMPORTANT]
>
>Suivez cette étape pour ajouter des conditions à votre règle. Sinon, passez à *Définition de l’action* ci-dessous.

Dans cet exemple, une condition est créée, qui entraîne le déclenchement de la règle uniquement lorsque le nom du point ciblé actuel est égal à **[!UICONTROL Mon point ciblé]**.

1. Sous , **[!UICONTROL Conditions]** , cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la **[!UICONTROL Extension]** liste déroulante, sélectionnez **[!UICONTROL Places Service]**.

1. Dans la **[!UICONTROL Type de condition]** liste déroulante, sélectionnez **[!UICONTROL Nom]**.

1. Dans le volet de droite, dans le champ de texte, saisissez **[!UICONTROL Mon point ciblé]**.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

   ![&quot;définir une condition&quot;](/help/assets/pt-setCondition.png)


## 4. Définissez l’action.

1. Sous , **[!UICONTROL Actions]** , cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la **[!UICONTROL Extension]** liste déroulante, sélectionnez **[!UICONTROL Adobe Analytics]**.

1. Dans la **[!UICONTROL Type d’action]** liste déroulante, sélectionnez **[!UICONTROL Suivi]**.

1. Dans le volet de droite, ajoutez l’action ou l’état que vous souhaitez envoyer à Analytics.

   Vous pouvez également choisir d’ajouter des données contextuelles supplémentaires à cette requête. N’oubliez pas que vous pouvez utiliser des éléments de données pour obtenir ces données dynamiquement à partir du SDK.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

   Dans l’exemple suivant, une `TrackAction` est envoyé à Analytics avec des données contextuelles supplémentaires de `poi.name` égal au nom du point ciblé qui a déclenché cet événement d’entrée :

   ![&quot;définir une action&quot;](/help/assets/pt-setAction.png)

## 5. Enregistrez la règle et recréez votre propriété.

Une fois la configuration terminée, vérifiez que la règle ressemble à l’image suivante :

![&quot;règle créée&quot;](/help/assets/pt-ruleComplete.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Recréez votre propriété Launch et déployez-la dans l’environnement approprié.
