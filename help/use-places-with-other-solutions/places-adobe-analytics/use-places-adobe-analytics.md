---
title: Envoyer les données d’entrée et de sortie du point d’accès à Analytics
description: Cette section fournit des informations sur la manière d’envoyer les données d’entrée et de sortie d’un point d’accès à Analytics.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 4%

---


# Envoyer les données d’entrée et de sortie du point d’accès à Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>Cette section suppose que le service Places est mis en oeuvre dans votre application. Pour plus d’informations sur l’implémentation du service Places, voir [Installations d’extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Une fois que le service Places envoie les événements d’entrée et de sortie, vous pouvez créer des règles dans l’Experience Platform Launch pour envoyer les données du service Places à Adobe Analytics. Pour créer ce type de règle, sélectionnez votre propriété dans Lancer et procédez comme suit :

## 1. Créez une règle.

1. Dans l&#39;onglet **[!UICONTROL Règles]**, cliquez sur **[!UICONTROL Créer une règle]**.

   Gardez à l’esprit les informations suivantes :

   * Si vous ne disposez pas de règles existantes pour cette propriété, le bouton **[!UICONTROL Créer une règle]** se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton **[!UICONTROL Créer une règle]** se trouve en haut à droite de l’écran.

## 2. Sélectionnez un événement

1. Entrez un nom significatif pour votre règle.

   Ainsi, la règle sera facilement reconnaissable dans votre liste de règles. Dans cet exemple, la règle est nommée **[!UICONTROL Envoyer des données à Analytics]**.

1. Dans la section **[!UICONTROL Events]**, cliquez sur **[!UICONTROL Add]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Service Lieux]**.

1. Dans la liste déroulante **[!UICONTROL Type d&#39;événement]**, sélectionnez **[!UICONTROL Entrer l&#39;IPE]**.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

   ![&quot;sélectionner un événement&quot;](/help/assets/pt-selectEvent.png)


## 3. Conditions d&#39;Ajoute

>[!IMPORTANT]
>
>Suivez cette étape pour ajouter des conditions à votre règle. Sinon, passez à *Définir l&#39;action* ci-dessous.

Dans cet exemple, une condition est créée, qui provoque le déclenchement de la règle uniquement lorsque le nom de l’API active est égal à **[!UICONTROL Mon POI]**.

1. Sous la section **[!UICONTROL Conditions]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Service Lieux]**.

1. Dans la liste déroulante **[!UICONTROL Type de condition]**, sélectionnez **[!UICONTROL Nom]**.

1. Dans le volet de droite, dans le champ de texte, saisissez **[!UICONTROL Mon POI]**.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

   ![&quot;set a condition&quot;](/help/assets/pt-setCondition.png)


## 4. Définir l&#39;action

1. Sous la section **[!UICONTROL Actions]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Adobe Analytics]**.

1. Dans la liste déroulante **[!UICONTROL Type d&#39;action]**, sélectionnez **[!UICONTROL Suivi]**.

1. Dans le volet de droite, ajoutez l’action ou l’état que vous souhaitez envoyer à Analytics.

   Vous pouvez également choisir d’ajouter d’autres données contextuelles à cette requête. N’oubliez pas que vous pouvez utiliser des éléments de données pour obtenir dynamiquement ces données à partir du SDK.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

   Dans l’exemple suivant, un appel `TrackAction` est envoyé à Analytics avec des données contextuelles supplémentaires de `poi.name` égales au nom de l’API qui a déclenché ce événement d’entrée :

   ![&quot;définir une action&quot;](/help/assets/pt-setAction.png)

## 5. Enregistrez la règle et recréez votre propriété.

Une fois la configuration terminée, vérifiez que votre règle ressemble à l’image suivante :

![&quot;règle créée&quot;](/help/assets/pt-ruleComplete.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Régénérez votre propriété Launch et déployez-la sur l’environnement approprié.
