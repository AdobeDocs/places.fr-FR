---
title: Adobe Target
description: Cette section fournit des informations sur l’utilisation du service Places avec Adobe Target.
translation-type: tm+mt
source-git-commit: d33e4e2d798c7048bdd275cdf6c0aabf3434f789
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 2%

---


# Utiliser le service Places avec Adobe Target {#places-target}

Ce document suppose que l&#39;extension Places est implémentée dans votre application. Si vous avez besoin d’aide pour implémenter l’extension Places, voir [Extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md)Places.

Une fois que l’extension Lieux est envoyée dans des événements pour les entrées et les sorties, vous pouvez utiliser Règles dans Lancement pour associer vos données du service Lieux à vos événements du SDK Adobe Target. Lorsque la propriété de votre choix est sélectionnée dans Lancer, vous pouvez créer ce type de règle en exécutant les tâches suivantes :

## 1. Création d’une règle

1. Dans l’ **[!UICONTROL Rules]** onglet, cliquez sur **[!UICONTROL Create New Rule]**.

   Gardez à l’esprit les informations suivantes :

   * Si vous ne disposez pas de règles existantes pour cette propriété, le bouton se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton se trouve en haut à droite de l’écran.

## 2. Sélectionnez un Événement

1. Attribuez un nom significatif à votre règle afin qu’elle soit facilement reconnaissable dans votre liste de règles.

   Dans cet exemple, la règle est nommée **[!UICONTROL Attach Places Service Data to Target Content Requested]**.

1. Sous la **[!UICONTROL Events]** section, cliquez sur **[!UICONTROL Add]**.
1. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Adobe Target]**.
1. Dans la liste **[!UICONTROL Event Type]** déroulante, sélectionnez **[!UICONTROL Content Requested]**.
1. Cliquez sur **[!UICONTROL Keep Changes]**.

![ajouter un événement](/help/assets/ad-setEvent_target.png)

## 3. Conditions d&#39;Ajoute

>[!IMPORTANT]
>
>Suivez cette étape si vous souhaitez ajouter des conditions à votre règle. Sinon, passez à la section *Définir l’action* ci-dessous.

Dans l’exemple suivant, une condition est créée qui provoque le déclenchement de la règle uniquement pour les utilisateurs qui ont lancé l’application cinq fois ou plus.

1. Sous la **[!UICONTROL Conditions]** section, cliquez sur **[!UICONTROL Add]**.
1. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Mobile Core]**.
1. Dans la liste **[!UICONTROL Condition Type]** déroulante, sélectionnez **[!UICONTROL Launches]**.
1. Dans le volet de droite, modifiez la liste déroulante et les contrôles de numéro afin que la condition soit lue **[!UICONTROL User has launched the app greater than or equal to 5 times]**.
1. Cliquez sur **[!UICONTROL Keep Changes]**.

![ajouter une condition](/help/assets/ad-setCondition_target.png)

## 4. Définir l&#39;action

1. Sous la **[!UICONTROL Actions]** section, cliquez sur **[!UICONTROL Add]**.
1. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Mobile Core]**.
1. Dans la liste **[!UICONTROL Action Type]** déroulante, sélectionnez **[!UICONTROL Attach Data]**.
1. Dans le volet de droite, dans le **[!UICONTROL JSON Payload]** champ, tapez les données qui seront ajoutées à ce Événement.
1. Cliquez sur **[!UICONTROL Keep Changes]**.

Dans le volet de droite, vous pouvez ajouter une charge JSON à structure libre qui ajoute des données à un événement SDK avant que les extensions qui écoutent ce événement ne l’entendent.

Dans l’exemple suivant, `poiCity` et `poiName` sont ajoutés au **[!UICONTROL mboxparameters]** pour chaque requête traitée dans le événement de Cible. Les valeurs des nouvelles clés sont déterminées dynamiquement par le SDK au moment du traitement de ce événement.

>[!TIP]
>
>Cette charge utile JSON utilise une notation spéciale pour l’ `request` objet. Dans le événement d’origine, `request` est un tableau d’objets anonymes. Lorsque vous associez des données à tous les objets d&#39;un tableau à l&#39;aide de l&#39;option Joindre les données, la `[*]` notation d&#39;une clé connue pour contenir un tableau entraîne l&#39;application de la charge utile à tous les objets de ce tableau.
>
>La notation de `request[*]` peut être lue à haute voix comme _pour chaque objet du tableau `request`_.

![définir l&#39;action](/help/assets/ad-setAction-target.png)

## 5. Enregistrez la règle et recréez votre propriété

Une fois la configuration terminée, vérifiez que votre règle ressemble à l’image suivante :

![règle terminée](/help/assets/ad-ruleComplete-target.png)

1. Cliquez sur **[!UICONTROL Save]**.
1. Régénérez votre propriété Launch et déployez-la sur l’Environnement approprié.
