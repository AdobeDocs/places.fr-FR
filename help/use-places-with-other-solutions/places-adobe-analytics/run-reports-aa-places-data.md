---
title: Exécution de rapports dans Adobe Analytics qui incluent des données Places
seo-title: Exécution de rapports dans Adobe Analytics qui incluent des données Places
description: Cette section fournit des informations sur la manière d’exécuter des rapports dans Analytics qui incluent des données Places.
seo-description: Cette section fournit des informations sur la manière d’exécuter des rapports dans Analytics qui incluent des données Places.
translation-type: tm+mt
source-git-commit: 0612e2fb06e45ff25ad580e3336be3eb48bb39b9

---


# Exécution de rapports dans Adobe Analytics qui incluent des données Places {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Ce document suppose que votre application met en oeuvre Adobe Places. Pour plus d’informations sur l’implémentation d’Adobe Places, voir [Places extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Une fois les événements d’entrée et de sortie envoyés, vous pouvez créer des règles dans le lancement de la plateforme d’expérience et joindre vos données Places à tous les événements Adobe Analytics. Pour créer ce type de règle, sélectionnez votre propriété dans Lancer et procédez comme suit :

## 1. Création d’une règle

1. Sur l’ **[!UICONTROL Rules]** onglet, cliquez sur **[!UICONTROL Create New Rule]**.

   À noter :
   * Si vous ne disposez pas de règles existantes pour cette propriété, le bouton se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton se trouve en haut à droite de l’écran.

## 1.Sélectionner un événement

1. Attribuez un nom significatif à votre règle afin qu’elle soit facilement reconnaissable dans votre liste de règles.

   Dans cet exemple, la règle est nommée **Joindre des données aux événements** d’action de suivi Analytics.

2. Sous la **[!UICONTROL Events]** section, cliquez sur **[!UICONTROL Add]**.

3. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Mobile Core]**.

4. Dans la liste **[!UICONTROL Event Type]** déroulante, sélectionnez **[!UICONTROL Track Action]**.

Vous pouvez maintenant déterminer les déclencheurs à inclure pour cette règle. Dans cet exemple, le déclencheur est basé sur tous les `TrackAction` appels. Après avoir configuré l’événement, cliquez sur **[!UICONTROL Keep Changes]**.

!["créer un événement"](/help/assets/ad-setEvent.png)


## 2. Ajouter des conditions

>[!IMPORTANT]
>
>Suivez cette étape si vous souhaitez ajouter des conditions à votre règle. Sinon, passez à la section *Définir l’action* ci-dessous.

Dans cet exemple, une condition est créée, qui entraîne le déclenchement de la règle uniquement pour les clients AT&amp;T.

1. Sous la **[!UICONTROL Conditions]** section, cliquez sur **[!UICONTROL Add]**.

2. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTORL Mobile Core]**.

3. Dans la liste **[!UICONTROL Condition Type]** déroulante, sélectionnez **[!UICONTROL Carrier Name]**.

4. Dans la fenêtre de droite, cochez la **[!UICONTROL AT&T]** case.

5. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).

!["create a condition"](/help/assets/ad-setCondition.png)

## 3. Définir l'action

1. Sous la **[!UICONTROL Actions]** section, cliquez sur **[!UICONTROL Add]**.

2. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Mobile Core]**.

3. Dans la liste **[!UICONTROL Action Type]** déroulante, sélectionnez **[!UICONTROL Attach Data]**.

4. Dans le volet de droite, dans le **[!UICONTROL JSON Payload]** champ, saisissez les données qui seront ajoutées à cet événement.

5. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).

Dans le volet de droite, vous pouvez ajouter une charge JSON à structure libre qui ajoute des données à un événement SDK avant qu’une extension qui écoute cet événement n’entende l’événement. Dans cet exemple, certaines données contextuelles sont ajoutées à cet événement avant que l’extension Analytics ne les traite. Les données contextuelles ajoutées se trouvent désormais dans l’accès Analytics sortant.

Dans l’exemple suivant, `poi.city` des valeurs et `poi.name` des valeurs sont ajoutées aux données contextuelles de l’événement Analytics. Les valeurs des nouvelles clés sont déterminées dynamiquement par le SDK lorsque cet événement se produit.

!["créer une action"](/help/assets/pt-setAction.png)

## 4. Enregistrez la règle et recréez votre propriété.

Une fois la configuration terminée, vérifiez que votre règle ressemble à l’image suivante :

!["la règle est terminée."](/help/assets/pt-ruleComplete.png)

1. Cliquez sur **[!UICONTROL Save]** (Conserver les modifications).

2. Reconstruisez votre propriété Launch et déployez-la dans l’environnement approprié.