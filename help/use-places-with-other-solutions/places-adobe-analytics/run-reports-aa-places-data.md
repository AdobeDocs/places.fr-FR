---
title: Ajouter le contexte d’emplacement aux demandes Analytics
description: Cette section fournit des informations sur la manière d’ajouter un contexte d’emplacement aux requêtes Analytics.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 2%

---


# Ajouter le contexte d’emplacement aux demandes Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Ce document suppose que le service Places est mis en oeuvre dans votre application. Pour plus d’informations sur l’implémentation du service Places, voir [Installations d’extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Après l’envoi des événements d’entrée et de sortie par le service Places, vous pouvez créer des règles dans l’Experience Platform Launch et joindre vos données du service Places à tous les événements Adobe Analytics. Pour créer ce type de règle, sélectionnez votre propriété dans Lancer et procédez comme suit :

## 1. Créez une règle.

1. Dans l&#39;onglet **[!UICONTROL Règles]**, cliquez sur **[!UICONTROL Créer une règle]**.

   Gardez à l’esprit les informations suivantes :
   * Si vous ne disposez pas de règles existantes pour cette propriété, le bouton **[!UICONTROL Créer une règle]** se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton **[!UICONTROL Créer une règle]** se trouve en haut à droite de l’écran.

## 2.Sélectionner un événement

1. Attribuez un nom significatif à votre règle afin qu’elle soit facilement reconnaissable dans votre liste de règles.

   Dans cet exemple, la règle est nommée **[!UICONTROL Joindre les données du service Lieux aux Événements d’action de suivi Analytics]**.

1. Sous la section **[!UICONTROL Événements]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]**.

1. Dans la liste déroulante **[!UICONTROL Type d&#39;événement]**, sélectionnez **[!UICONTROL Suivi de l&#39;action]**.

Vous pouvez maintenant déterminer les déclencheurs à inclure pour cette règle. Dans cet exemple, le déclencheur est basé sur tous les appels `TrackAction`. Après avoir configuré le Événement, cliquez sur **[!UICONTROL Conserver les modifications]**.

![&quot;créer un événement&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Conditions d&#39;Ajoute

>[!IMPORTANT]
>
>Suivez cette procédure pour ajouter des conditions à votre règle. Sinon, passez à la section *Définir l&#39;action* ci-dessous.

Dans cet exemple, une condition est créée qui provoque le déclenchement de la règle uniquement pour les clients AT&amp;T.

1. Sous la section **[!UICONTROL Conditions]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]**.

1. Dans la liste déroulante **[!UICONTROL Type de condition]**, sélectionnez **[!UICONTROL Nom de l’opérateur]**.

1. Dans la fenêtre de droite, cochez la case **[!UICONTROL AT&amp;T]**.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

![&quot;créer une condition&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Définir l&#39;action

1. Sous la section **[!UICONTROL Actions]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]**.

1. Dans la liste déroulante **[!UICONTROL Type d’action]**, sélectionnez **[!UICONTROL Joindre les données]**.

1. Dans le volet de droite, dans le champ **[!UICONTROL JSON Payload]**, saisissez les données qui seront ajoutées à ce Événement.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

Dans le volet de droite, vous pouvez ajouter une charge JSON à structure libre qui ajoute des données à un événement SDK avant qu’une extension qui écoute ce événement n’entende le événement. Dans cet exemple, certaines données contextuelles sont ajoutées à ce événement avant que l’extension Analytics ne les traite. Les données contextuelles ajoutées seront désormais présentes dans l’accès Analytics sortant.

Dans l’exemple suivant, les valeurs `poi.city` et `poi.name` sont ajoutées aux données contextuelles du événement Analytics. Les valeurs des nouvelles clés sont déterminées dynamiquement par le SDK lorsque ce événement est traité.

![&quot;créer une action&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Enregistrez la règle et recréez votre propriété.

Une fois la configuration terminée, vérifiez que votre règle ressemble à l’image suivante :

![&quot;la règle est terminée.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Régénérez votre propriété Launch et déployez-la sur l’Environnement approprié.
