---
title: Adobe Target
seo-title: Adobe Target
description: Cette section fournit des informations sur l’utilisation du service d’emplacement avec Adobe Target.
seo-description: 'Cette section fournit des informations sur l’utilisation du service d’emplacement avec Adobe Target. '
translation-type: tm+mt
source-git-commit: ba918bfdb989ba4037409b17d799ef596064b676

---


# Adobe Target {#places-target}

Ce document suppose que l’extension Places est implémentée dans votre application. Si vous avez besoin d’aide pour implémenter l’extension Places, voir [Extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md)Lieux.

Une fois que l’extension Places envoie des événements pour les entrées et les sorties, vous pouvez utiliser les règles de lancement pour associer vos données Places à vos événements SDK Adobe Target. Lorsque la propriété de votre choix est sélectionnée dans Lancer, vous pouvez créer ce type de règle en procédant comme suit :

## 1. Création d’une règle

1. Sur l’ **[!UICONTROL Rules]** onglet, cliquez sur **[!UICONTROL Create New Rule]**.

   À noter :

   * Si vous ne disposez pas de règles existantes pour cette propriété, le bouton se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton se trouve en haut à droite de l’écran.

## 2. Sélectionner un événement

1. Attribuez un nom significatif à votre règle afin qu’elle soit facilement reconnaissable dans votre liste de règles.

   Dans cet exemple, la règle est nommée **[!UICONTROL Attach Places Data to Target Content Requested]**.

2. Sous la **[!UICONTROL Events]** section, cliquez sur **[!UICONTROL Add]**.

3. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Adobe Target]**.

4. Dans la liste **[!UICONTROL Event Type]** déroulante, sélectionnez **[!UICONTROL Content Requested]**.

5. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).

![ajouter un événement](/help/assets/ad-addEvent.png)

## 3. Ajouter des conditions

>[!IMPORTANT]
>
>Suivez cette étape si vous souhaitez ajouter des conditions à votre règle. Sinon, passez à la section *Définir l’action* ci-dessous.

Dans l’exemple suivant, une condition est créée, qui provoque le déclenchement de la règle uniquement pour les utilisateurs qui ont lancé l’application cinq fois ou plus.

1. Sous la **[!UICONTROL Conditions]** section, cliquez sur **[!UICONTROL Add]**.

2. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Mobile Core]**.

3. Dans la liste **[!UICONTROL Condition Type]** déroulante, sélectionnez **[!UICONTROL Launches]**.

4. Dans le volet de droite, modifiez la liste déroulante et les contrôles de nombre afin que la condition indique **[!UICONTROL User a lancé l’application plus de 5 fois** ou plus.

5. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).

![ajouter un événement](/help/assets/ad-setCondition.png)

## 4. Définir l'action

1. Sous la **[!UICONTROL Actions]** section, cliquez sur **[!UICONTROL Add]**.

2. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Mobile Core]**.

3. Dans la liste **[!UICONTROL Action Type]** déroulante, sélectionnez **[!UICONTROL Attach Data]**.

4. Dans le volet de droite, dans le **[!UICONTROL JSON Payload]** champ, saisissez les données qui seront ajoutées à cet événement.

5. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).

Dans le volet de droite, vous pouvez ajouter une charge JSON à structure libre qui ajoute des données à un événement SDK avant que les extensions qui écoutent cet événement ne l’entendent.

Dans l’exemple suivant, `poiCity` et `poiName` sont ajoutées à la **[!UICONTROL mboxparameters]** requête pour chaque requête traitée dans l’événement Target. Les valeurs des nouvelles clés sont déterminées dynamiquement par le SDK au moment du traitement de cet événement.

>[!TIP
>]
>Cette charge JSON utilise une notation spéciale pour l’ `request` objet. Dans l’événement d’origine, `request` est un tableau d’objets anonymes. Lorsque vous associez des données à tous les objets d’un tableau à l’aide de l’option Joindre les données, la `[*]` notation d’une clé connue pour contenir un tableau entraîne l’application de la charge utile à tous les objets de ce tableau.
>
>La notation de `request[*]` peut être lue à haute voix sous la forme _pour chaque objet du `request` tableau.

![ajouter un événement](/help/assets/ad-setAction.png)

## 5. Enregistrez la règle et recréez votre propriété

Une fois la configuration terminée, vérifiez que votre règle ressemble à l’image suivante :

![règle terminée](/help/assets/ad-ruleComplete.png)

1. Cliquez sur **[!UICONTROL Save]** (Conserver les modifications).

2. Reconstruisez votre propriété Launch et déployez-la dans l’environnement approprié.
