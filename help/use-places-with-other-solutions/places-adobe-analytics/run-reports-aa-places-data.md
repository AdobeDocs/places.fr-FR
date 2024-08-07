---
title: Ajout d’un contexte d’emplacement aux requêtes Analytics
description: Cette section fournit des informations sur la manière d’ajouter un contexte d’emplacement aux requêtes Analytics.
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 2%

---

# Ajout d’un contexte d’emplacement aux requêtes Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Ce document suppose que le service Places est implémenté dans votre application. Pour plus d’informations sur l’implémentation de Places Service, voir [Extensions Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Une fois que le service Places a envoyé les événements d’entrée et de sortie, vous pouvez créer des règles dans Experience Platform Launch et joindre vos données du service Places à tous les événements Adobe Analytics. Pour créer ce type de règle, sélectionnez votre propriété dans Launch et procédez comme suit :

## 1. Créer une règle

1. Sur l’onglet **[!UICONTROL Rules]**, cliquez sur **[!UICONTROL Create New Rule]**.

   Gardez à l’esprit les informations suivantes :
   * Si vous ne disposez pas de règles existantes pour cette propriété, le bouton **[!UICONTROL Créer une règle]** se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton **[!UICONTROL Créer une règle]** se trouve en haut à droite de l’écran.

## 2. Sélectionner un événement

1. Donnez un nom significatif à votre règle afin qu’elle soit facilement reconnaissable dans votre liste de règles.

   Dans cet exemple, la règle est nommée **[!UICONTROL Attach Places Service Data to Analytics Track Action Events]**.

1. Dans la section **[!UICONTROL Events]**, cliquez sur **[!UICONTROL Add]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]**.

1. Dans la liste déroulante **[!UICONTROL Event Type]**, sélectionnez **[!UICONTROL Track Action]**.

Vous pouvez désormais déterminer les déclencheurs que vous souhaitez inclure pour cette règle. Dans cet exemple, le déclencheur est basé sur tous les appels `TrackAction`. Après avoir configuré l’événement, cliquez sur **[!UICONTROL Conserver les modifications]**.

![&quot;create an event&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Ajouter des conditions

>[!IMPORTANT]
>
>Suivez cette procédure pour ajouter des conditions à votre règle. Sinon, passez à la section *Définir l&#39;action* ci-dessous.

Dans cet exemple, une condition est créée, qui entraîne le déclenchement de la règle uniquement pour les clients AT&amp;T.

1. Dans la section **[!UICONTROL Conditions]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]**.

1. Dans la liste déroulante **[!UICONTROL Type de condition]**, sélectionnez **[!UICONTROL Nom de l’opérateur]**.

1. Dans la fenêtre de droite, cochez la case **[!UICONTROL AT&amp;T]** .

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

![&quot;create a condition&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Définir l’action

1. Sous la section **[!UICONTROL Actions]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]**.

1. Dans la liste déroulante **[!UICONTROL Type d’action]**, sélectionnez **[!UICONTROL Joindre les données]**.

1. Dans le volet de droite, dans le champ **[!UICONTROL JSON Payload]**, saisissez les données qui seront ajoutées à cet événement.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

Dans le volet de droite, vous pouvez ajouter une payload JSON à structure libre qui ajoute des données à un événement SDK avant qu’une extension qui écoute cet événement puisse entendre l’événement. Dans cet exemple, certaines données contextuelles sont ajoutées à cet événement avant que l’extension Analytics ne le traite. Les données contextuelles ajoutées se trouvent désormais dans l’accès Analytics sortant.

Dans l’exemple suivant, les valeurs `poi.city` et `poi.name` sont ajoutées aux données contextuelles de l’événement Analytics. Les valeurs des nouvelles clés sont déterminées dynamiquement par le SDK lors du traitement de cet événement.

![&quot;créer une action&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Enregistrez la règle et recréez votre propriété.

Une fois la configuration terminée, vérifiez que la règle ressemble à l’image suivante :

![&quot;la règle est terminée.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Recréez votre propriété Launch et déployez-la dans l’environnement approprié.
