---
title: Adobe Target
description: Cette section fournit des informations sur l’utilisation du service Places avec Adobe Target.
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
TQID: https://experienceleague.adobe.com/WsfkEJD0mN5aYKETjcnqiC13dVe5NPYeKfOCTOK82uE
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 549
ht-degree: 4%

---

# Utilisation du service Places avec Adobe Target {#places-target}

Ce document suppose que l’extension Places est implémentée dans votre application. Si vous avez besoin d’aide pour implémenter l’extension Places, voir [Extensions Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Une fois que l’extension Places a envoyé des événements pour les entrées et les sorties, vous pouvez utiliser des règles dans Launch pour joindre vos données Places Service à vos événements Adobe Target SDK. Une fois la propriété souhaitée sélectionnée dans Launch, vous pouvez créer ce type de règle en effectuant les tâches suivantes :

## &#x200B;1. Création d’une règle

1. Dans l’onglet **[!UICONTROL Règles]**, cliquez sur **[!UICONTROL Créer une règle]**.

   Gardez à l’esprit les informations suivantes :

   * Si vous n’avez pas de règles existantes pour cette propriété, le bouton se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton se trouve en haut à droite de l’écran.

## &#x200B;2. Sélectionner un événement

1. Donnez à votre règle un nom significatif afin qu’elle soit facilement reconnaissable dans votre liste de règles.

   Dans cet exemple, la règle est nommée **[!UICONTROL Joindre des données du service Places au contenu cible demandé]**.

1. Sous la section **[!UICONTROL Événements]**, cliquez sur **[!UICONTROL Ajouter]**.
1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Adobe Target]**.
1. Dans la liste déroulante **[!UICONTROL Type d’événement]**, sélectionnez **[!UICONTROL Contenu demandé]**.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

![ajouter un événement](/help/assets/ad-setEvent_target.png)

## &#x200B;3. Ajouter des conditions

>[!IMPORTANT]
>
>Effectuez cette étape si vous souhaitez ajouter des conditions à votre règle. Sinon, passez à l’étape *Définir l’action* ci-dessous.

Dans l’exemple suivant, une condition est créée qui entraîne le déclenchement de la règle uniquement pour les utilisateurs qui ont lancé l’application cinq fois ou plus.

1. Dans la section **[!UICONTROL Conditions]**, cliquez sur **[!UICONTROL Ajouter]**.
1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]**.
1. Dans la liste déroulante **[!UICONTROL Type de condition]**, sélectionnez **[!UICONTROL Lancements]**.
1. Dans le volet de droite, modifiez les commandes de liste déroulante et de nombre afin que la condition indique **[!UICONTROL L’utilisateur a lancé l’application à plus de 5 reprises]**.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

![ajouter une condition](/help/assets/ad-setCondition_target.png)

## &#x200B;4. Définition de l’action

1. Sous la section **[!UICONTROL Actions]**, cliquez sur **[!UICONTROL Ajouter]**.
1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]**.
1. Dans la liste déroulante **[!UICONTROL Type d’action]**, sélectionnez **[!UICONTROL Joindre des données]**.
1. Dans le volet de droite, dans le champ **[!UICONTROL Payload JSON]**, saisissez les données qui seront ajoutées à cet événement.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

Dans le volet de droite, vous pouvez ajouter une payload JSON à structure libre qui ajoute des données à un événement SDK avant que les extensions qui écoutent cet événement ne l’entendent.

Dans l’exemple suivant, les valeurs `poiCity` et `poiName` sont ajoutées aux **[!UICONTROL mboxparameters]** pour chaque requête traitée dans l’événement Target. Les valeurs des nouvelles clés sont déterminées dynamiquement par le SDK au moment du traitement de cet événement.

>[!TIP]
>
>Cette payload JSON utilise une notation spéciale pour l’objet `request`. Dans l’événement d’origine, `request` est un tableau d’objets anonymes. Lorsque vous joignez des données à tous les objets d’un tableau à l’aide de l’option Joindre des données, la notation `[*]` sur une clé qui est connue pour contenir un tableau entraîne l’application de la payload à tous les objets de ce tableau.
>
>La notation de `request[*]` peut être lue à haute voix sous la forme _pour chaque objet dans le tableau de `request`_.

![définissez l’action](/help/assets/ad-setAction-target.png)

## &#x200B;5. Enregistrer la règle et recréer votre propriété

Une fois la configuration terminée, vérifiez que votre règle ressemble à l’image suivante :

![règle terminée](/help/assets/ad-ruleComplete-target.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Recréez la propriété Launch et déployez-la dans l’environnement approprié.
