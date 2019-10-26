---
title: Envoyer des données de lieux à Adobe Analytics
seo-title: Envoyer des données de lieux à Adobe Analytics
description: Cette section fournit des informations sur la manière d’envoyer des données Places à Analytics.
seo-description: 'Cette section fournit des informations sur la manière d’envoyer des données Places à Analytics. '
translation-type: tm+mt
source-git-commit: 0612e2fb06e45ff25ad580e3336be3eb48bb39b9

---


# Envoyer des données de lieux à Adobe Analytics {#places-data-analytics}


(Espace réservé pour la vidéo de Steve.)

>[!IMPORTANT]
>
>Ce document part du principe que des emplacements sont implémentés dans votre application. Pour plus d’informations sur l’implémentation de lieux, voir [Lieux Extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Une fois que Places a envoyé les événements d’entrée et de sortie, vous pouvez créer des règles dans le lancement de la plate-forme d’expérience pour envoyer les données Places à Adobe Analytics. Pour créer ce type de règle, sélectionnez votre propriété dans Lancer et procédez comme suit :

## 1. Création d’une règle

1. Sur l’ **[!UICONTROL Rules]** onglet, cliquez sur **[!UICONTROL Create New Rule]**.

   À noter :

   * Si vous ne disposez pas de règles existantes pour cette propriété, le bouton se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton se trouve en haut à droite de l’écran.

## 2. Sélectionner un événement

1. Attribuez un nom significatif à votre règle afin qu’elle soit facilement reconnaissable dans votre liste de règles. Dans cet exemple, la règle est nommée **Envoyer des données à Analytics**.

2. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

3. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Places]**.

4. Dans la liste **[!UICONTROL Event Type]** déroulante, sélectionnez **[!UICONTROL Enter POI]**.

5. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).

   !["sélectionner un événement"](/help/assets/pt-selectEvent.png)


## 3. Ajouter des conditions

>[!IMPORTANT]
>
>Suivez cette étape si vous souhaitez ajouter des conditions à votre règle. Sinon, ignorez pour *définir l’action* ci-dessous.


Dans cet exemple, une condition est créée, qui provoque le déclenchement de la règle uniquement lorsque le nom de l’objet d’intérêt actif est égal à **[!UICONTROL My POI]**.

1. Sous la **[!UICONTROL Conditions]** section, cliquez sur **[!UICONTROL Add]**.

2. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Places]**.

3. Dans la liste **[!UICONTROL Condition Type]** déroulante, sélectionnez **[!UICONTROL Name]**.

4. Dans la fenêtre de droite, dans le champ de texte, saisissez **[!UICONTROL My POI]**.

5. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).

   !["set a condition"](/help/assets/ad-setCondition.png)


## 4. Définir l'action

1. Sous la **[!UICONTROL Actions]** section, cliquez sur **[!UICONTROL Add]**.

2. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Adobe Analytics]**.

3. Dans la liste **[!UICONTROL Action Type]** déroulante, sélectionnez **[!UICONTROL Track]**.

4. Dans le volet de droite, ajoutez l’action ou l’état que vous souhaitez envoyer à Analytics. Vous pouvez également choisir d’ajouter des données contextuelles supplémentaires à cette requête. N’oubliez pas que vous pouvez utiliser des éléments de données pour obtenir dynamiquement ces données à partir du SDK.

5. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).

Dans l’exemple suivant, un `TrackAction` appel est envoyé à Analytics avec des données contextuelles supplémentaires de **poi.name** égales au nom de l’API qui a déclenché cet événement d’entrée :

!["définir une action"](/help/assets/pt-setAction.png)

## 5. Enregistrer la règle et recréer votre propriété

Une fois la configuration terminée, vérifiez que votre règle ressemble à l’image suivante :

!["règle créée"](/help/assets/pt-ruleComplete.png)


1. Cliquez sur **[!UICONTROL Save]** (Conserver les modifications).

2. Reconstruisez votre propriété Launch et déployez-la dans l’environnement approprié.

