---
title: Adobe Target
description: Cette section fournit des informations sur l’utilisation du service Places avec les  Adobe.
translation-type: tm+mt
source-git-commit: d33e4e2d798c7048bdd275cdf6c0aabf3434f789

---


# Utiliser le service Places avec le Adobe {#places-target}

Ce suppose que l’extension Places est implémentée dans votre application. Si vous avez besoin d’aide pour implémenter l’extension Places, voir [Extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md)Lieux.

Une fois que l’extension Places envoie des  d’entrée et de sortie dans le, vous pouvez utiliser les règles de lancement pour associer vos données du service Places à votre  SDK Adobe. Lorsque la propriété de votre choix est sélectionnée dans Lancer, vous pouvez créer ce type de règle en remplissant le  de suivant :

## 1. Création d’une règle

1. Sur l’ **[!UICONTROL Rules]** onglet, cliquez sur **[!UICONTROL Create New Rule]**.

   À noter :

   * Si vous n’avez pas de règles existantes pour cette propriété, le bouton se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton se trouve dans le coin supérieur droit de l’écran.

## 2. Sélectionner un 

1. Attribuez un nom significatif à votre règle afin qu’elle soit facilement reconnaissable dans votre  de règles.

   Dans cet exemple, la règle est nommée **[!UICONTROL Attach Places Service Data to Target Content Requested]**.

1. Sous la **[!UICONTROL Events]** section, cliquez sur **[!UICONTROL Add]**.
1. Dans le  **[!UICONTROL Extension]** déroulant, sélectionnez **[!UICONTROL Adobe Target]**.
1. Dans le  **[!UICONTROL Event Type]** déroulant, sélectionnez **[!UICONTROL Content Requested]**.
1. Cliquez sur **[!UICONTROL Keep Changes]**.

![ajouter un](/help/assets/ad-setEvent_target.png)

## 3. Conditions Ajouter

>[!IMPORTANT]
>
>Suivez cette étape si vous souhaitez ajouter des conditions à votre règle. Sinon, passez à la section *Définir l’action* ci-dessous.

Dans l’exemple suivant, une condition est créée, qui provoque le déclenchement de la règle uniquement pour les utilisateurs qui ont lancé l’application cinq fois ou plus.

1. Sous la **[!UICONTROL Conditions]** section, cliquez sur **[!UICONTROL Add]**.
1. Dans le  **[!UICONTROL Extension]** déroulant, sélectionnez **[!UICONTROL Mobile Core]**.
1. Dans le  **[!UICONTROL Condition Type]** déroulant, sélectionnez **[!UICONTROL Launches]**.
1. Dans le volet de droite, modifiez le  déroulant et les contrôles de numéro afin que la condition soit lue **[!UICONTROL User has launched the app greater than or equal to 5 times]**.
1. Cliquez sur **[!UICONTROL Keep Changes]**.

![ajouter une condition](/help/assets/ad-setCondition_target.png)

## 4. Définir l&#39;action

1. Sous la **[!UICONTROL Actions]** section, cliquez sur **[!UICONTROL Add]**.
1. Dans le  **[!UICONTROL Extension]** déroulant, sélectionnez **[!UICONTROL Mobile Core]**.
1. Dans le  **[!UICONTROL Action Type]** déroulant, sélectionnez **[!UICONTROL Attach Data]**.
1. Dans le volet de droite, dans le **[!UICONTROL JSON Payload]** champ, saisissez les données qui seront ajoutées à ce  de.
1. Cliquez sur **[!UICONTROL Keep Changes]**.

Dans le volet de droite, vous pouvez ajouter une charge JSON à structure libre qui ajoute des données à un SDK avant que les extensions qui écoutent ce ne l’entendent .

Dans l’exemple suivant, `poiCity` des valeurs et `poiName` sont ajoutées à la **[!UICONTROL mboxparameters]** pour chaque requête traitée dans le  de  du. Les valeurs des nouvelles clés sont déterminées dynamiquement par le kit SDK au moment où ce est .

>[!TIP]
>
>Cette charge JSON utilise une notation spéciale pour l’ `request` objet. Dans le  d’origine, `request` est un tableau d’objets anonymes. Lorsque vous associez des données à tous les objets d’un tableau à l’aide de l’option Joindre les données, la `[*]` notation d’une clé connue pour contenir un tableau entraîne l’application de la charge utile à tous les objets de ce tableau.
>
>La notation de `request[*]` peut être lue à haute voix comme _pour chaque objet du`request`tableau_.

![définir l&#39;action](/help/assets/ad-setAction-target.png)

## 5. Enregistrez la règle et recréez votre propriété

Une fois la configuration terminée, vérifiez que votre règle ressemble à l’image suivante :

![règle terminée](/help/assets/ad-ruleComplete-target.png)

1. Cliquez sur **[!UICONTROL Save]**.
1. Reconstruisez votre propriété Launch et déployez-la vers le   approprié.
