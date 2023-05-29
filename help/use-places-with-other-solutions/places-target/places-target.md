---
title: Adobe Target
description: Cette section fournit des informations sur l’utilisation du service Places avec Adobe Target.
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 3%

---

# Utilisation du service Places avec Adobe Target {#places-target}

Ce document suppose que l’extension Places est implémentée dans votre application. Si vous avez besoin d’aide pour implémenter l’extension Places, reportez-vous à la section [Extensions Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Une fois que l’extension Places envoie des événements pour les entrées et les sorties, vous pouvez utiliser des règles dans Launch pour joindre vos données de service Places à vos événements SDK Adobe Target. Lorsque la propriété de votre choix est sélectionnée dans Launch, vous pouvez créer ce type de règle en procédant comme suit :

## 1. Création d’une règle

1. Sur le **[!UICONTROL Règles]** , cliquez sur **[!UICONTROL Créer une règle]**.

   Gardez à l’esprit les informations suivantes :

   * Si vous ne disposez pas de règles existantes pour cette propriété, le bouton se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton se trouve en haut à droite de l’écran.

## 2. Sélection d’un événement

1. Donnez un nom significatif à votre règle afin qu’elle soit facilement reconnaissable dans votre liste de règles.

   Dans cet exemple, la règle est nommée **[!UICONTROL Joindre les données du service Places au contenu Target demandé]**.

1. Sous , **[!UICONTROL Événements]** , cliquez sur **[!UICONTROL Ajouter]**.
1. Dans la **[!UICONTROL Extension]** liste déroulante, sélectionnez **[!UICONTROL Adobe Target]**.
1. Dans la **[!UICONTROL Type d’événement]** liste déroulante, sélectionnez **[!UICONTROL Contenu demandé]**.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

![ajouter un événement](/help/assets/ad-setEvent_target.png)

## 3. Ajout de conditions

>[!IMPORTANT]
>
>Suivez cette étape si vous souhaitez ajouter des conditions à votre règle. Sinon, passez à la *Définition de l’action* ci-dessous.

Dans l’exemple suivant, une condition est créée, qui entraîne le déclenchement de la règle uniquement pour les utilisateurs qui ont lancé l’application cinq fois ou plus.

1. Sous , **[!UICONTROL Conditions]** , cliquez sur **[!UICONTROL Ajouter]**.
1. Dans la **[!UICONTROL Extension]** liste déroulante, sélectionnez **[!UICONTROL Mobile Core]**.
1. Dans la **[!UICONTROL Type de condition]** liste déroulante, sélectionnez **[!UICONTROL Lancements]**.
1. Dans le volet de droite, modifiez la liste déroulante et les contrôles numériques afin que la condition soit lue. **[!UICONTROL L’utilisateur a lancé l’application plus ou moins 5 fois]**.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

![ajouter une condition](/help/assets/ad-setCondition_target.png)

## 4. Définition de l’action

1. Sous , **[!UICONTROL Actions]** , cliquez sur **[!UICONTROL Ajouter]**.
1. Dans la **[!UICONTROL Extension]** liste déroulante, sélectionnez **[!UICONTROL Mobile Core]**.
1. Dans la **[!UICONTROL Type d’action]** liste déroulante, sélectionnez **[!UICONTROL Joindre des données]**.
1. Dans le volet de droite, dans **[!UICONTROL Charge utile JSON]** , saisissez les données qui seront ajoutées à cet événement.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

Dans le volet de droite, vous pouvez ajouter une payload JSON à structure libre qui ajoute des données à un événement SDK avant que les extensions qui écoutent cet événement ne l’entendent.

Dans l’exemple suivant, `poiCity` et `poiName` sont ajoutées à la variable **[!UICONTROL mboxparameters]** pour chaque requête traitée dans l’événement Target. Les valeurs des nouvelles clés sont déterminées dynamiquement par le SDK au moment du traitement de cet événement.

>[!TIP]
>
>Ce payload JSON utilise une notation spéciale pour la variable `request` . Dans l’événement d’origine, `request` est un tableau d’objets anonymes. Lors de l’association de données à tous les objets d’un tableau à l’aide de l’option Joindre des données, la variable `[*]` sur une clé connue pour contenir un tableau , la charge utile est appliquée à tous les objets de ce tableau.
>
>La notation de `request[*]` peut être lu à haute voix comme _pour chaque objet de la fonction `request` tableau_.

![définir l’action ;](/help/assets/ad-setAction-target.png)

## 5. Enregistrez la règle et recréez votre propriété.

Une fois la configuration terminée, vérifiez que la règle ressemble à l’image suivante :

![règle terminée](/help/assets/ad-ruleComplete-target.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Recréez votre propriété Launch et déployez-la dans l’environnement approprié.
