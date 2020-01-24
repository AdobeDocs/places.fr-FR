---
title: Ajout d’un contexte d’emplacement aux requêtes Analytics
description: Cette section fournit des informations sur la manière d’ajouter un contexte d’emplacement aux requêtes Analytics.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Ajout d’un contexte d’emplacement aux requêtes Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Ce document suppose que le service Places est mis en oeuvre dans votre application. Pour plus d’informations sur l’implémentation du service Places, voir [Places extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Une fois les événements d’entrée et de sortie envoyés par le service Places, vous pouvez créer des règles dans le lancement de la plateforme d’expérience et joindre vos données du service Places à tous les événements Adobe Analytics. Pour créer ce type de règle, sélectionnez votre propriété dans Lancer et procédez comme suit :

## 1. Création d’une règle

1. Sur l’ **[!UICONTROL Rules]**onglet, cliquez sur**[!UICONTROL Create New Rule]**.

   À noter :
   * Si vous n’avez pas de règles existantes pour cette propriété, le **[!UICONTROL Create New Rule]**bouton se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le **[!UICONTROL Create New Rule]**bouton se trouve en haut à droite de l’écran.

## 2.Sélectionner un événement

1. Attribuez un nom significatif à votre règle afin qu’elle soit facilement reconnaissable dans votre liste de règles.

   Dans cet exemple, la règle est nommée **[!UICONTROL Attach Places Service Data to Analytics Track Action Events]**.

1. Sous la **[!UICONTROL Events]**section, cliquez sur**[!UICONTROL Add]**.

1. Dans la liste **[!UICONTROL Extension]**déroulante, sélectionnez**[!UICONTROL Mobile Core]**.

1. Dans la liste **[!UICONTROL Event Type]**déroulante, sélectionnez**[!UICONTROL Track Action]**.

Vous pouvez maintenant déterminer les déclencheurs à inclure pour cette règle. Dans cet exemple, le déclencheur est basé sur tous les `TrackAction` appels. Après avoir configuré l’événement, cliquez sur **[!UICONTROL Keep Changes]**.

![&quot;créer un événement&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Ajouter des conditions

>[!IMPORTANT]
>
>Suivez cette procédure pour ajouter des conditions à votre règle. Sinon, passez à la section *Définir l’action* ci-dessous.

Dans cet exemple, une condition est créée, qui entraîne le déclenchement de la règle uniquement pour les clients AT&amp;T.

1. Sous la **[!UICONTROL Conditions]**section, cliquez sur**[!UICONTROL Add]**.

1. Dans la liste **[!UICONTROL Extension]**déroulante, sélectionnez**[!UICONTROL Mobile Core]**.

1. Dans la liste **[!UICONTROL Condition Type]**déroulante, sélectionnez**[!UICONTROL Carrier Name]**.

1. Dans la fenêtre de droite, cochez la **[!UICONTROL AT&T]**case.

1. Cliquez sur **[!UICONTROL Keep Changes]**(Exécuter des tests d’Auditor).

![&quot;create a condition&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Définir l&#39;action

1. Sous la **[!UICONTROL Actions]**section, cliquez sur**[!UICONTROL Add]**.

1. Dans la liste **[!UICONTROL Extension]**déroulante, sélectionnez**[!UICONTROL Mobile Core]**.

1. Dans la liste **[!UICONTROL Action Type]**déroulante, sélectionnez**[!UICONTROL Attach Data]**.

1. Dans le volet de droite, dans le **[!UICONTROL JSON Payload]**champ, saisissez les données qui seront ajoutées à cet événement.

1. Cliquez sur **[!UICONTROL Keep Changes]**(Exécuter des tests d’Auditor).

Dans le volet de droite, vous pouvez ajouter une charge JSON à structure libre qui ajoute des données à un événement SDK avant qu’une extension qui écoute cet événement n’entende l’événement. Dans cet exemple, certaines données contextuelles sont ajoutées à cet événement avant que l’extension Analytics ne les traite. Les données contextuelles ajoutées se trouvent désormais dans l’accès Analytics sortant.

Dans l’exemple suivant, `poi.city` des valeurs et `poi.name` des valeurs sont ajoutées aux données contextuelles de l’événement Analytics. Les valeurs des nouvelles clés sont déterminées dynamiquement par le SDK lorsque cet événement se produit.

![&quot;créer une action&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Enregistrez la règle et recréez votre propriété.

Une fois la configuration terminée, vérifiez que votre règle ressemble à l’image suivante :

![&quot;la règle est terminée.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Cliquez sur **[!UICONTROL Save]**

1. Reconstruisez votre propriété Launch et déployez-la dans l’environnement approprié.
