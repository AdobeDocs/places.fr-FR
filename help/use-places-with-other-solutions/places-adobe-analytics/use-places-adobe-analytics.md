---
title: Envoyer les données d’entrée et de sortie de point d’intérêt à Analytics
description: Cette section fournit des informations sur la manière d’envoyer des données d’entrée et de sortie de point ciblé à Analytics.
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
TQID: https://experienceleague.adobe.com/H-NkwK7KNSGPjEKYuWNc8F0f3MIu3wBr5FGjypxnqng
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: b069d60e-95f3-44d6-95a8-ddc862a4bc38id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 443
ht-degree: 6%

---

# Envoyer les données d’entrée et de sortie de point d’intérêt à Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>Cette section suppose que le service Places est implémenté dans votre application. Pour plus d’informations sur l’implémentation de Places Service, voir [Extensions Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Une fois que Places Service a envoyé les événements d’entrée et de sortie, vous pouvez créer des règles dans Experience Platform Launch pour envoyer les données Places Service à Adobe Analytics. Pour créer ce type de règle, sélectionnez votre propriété dans Launch et effectuez les étapes suivantes :

## &#x200B;1. Création d’une règle

1. Dans l’onglet **[!UICONTROL Règles]**, cliquez sur **[!UICONTROL Créer une règle]**.

   Gardez à l’esprit les informations suivantes :

   * Si vous ne disposez pas de règles existantes pour cette propriété, le bouton **[!UICONTROL Créer une règle]** se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton **[!UICONTROL Créer une règle]** s’affiche en haut à droite de l’écran.

## &#x200B;2. Sélectionner un événement

1. Saisissez un nom significatif pour votre règle.

   De cette manière, la règle sera facilement reconnaissable dans votre liste de règles. Dans cet exemple, la règle est nommée **[!UICONTROL Envoyer des données à Analytics]**.

1. Dans la section **[!UICONTROL Events]**, cliquez sur **[!UICONTROL Add]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Places Service]**.

1. Dans la liste déroulante **[!UICONTROL Type d’événement]**, sélectionnez **[!UICONTROL Saisir un point ciblé]**.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

   ![« sélectionner un événement »](/help/assets/pt-selectEvent.png)


## &#x200B;3. Ajouter des conditions

>[!IMPORTANT]
>
>Effectuez cette étape pour ajouter des conditions à votre règle. Sinon, passez à *Définir l’action* ci-dessous.

Dans cet exemple, une condition est créée pour que la règle se déclenche uniquement lorsque le nom du point d’intérêt actuel est égal à **[!UICONTROL Mon point d’intérêt]**.

1. Dans la section **[!UICONTROL Conditions]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Places Service]**.

1. Dans la liste déroulante **[!UICONTROL Type de condition]**, sélectionnez **[!UICONTROL Nom]**.

1. Dans le volet de droite, dans le champ de texte, saisissez **[!UICONTROL Mon point d’intérêt]**.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

   ![« définir une condition »](/help/assets/pt-setCondition.png)


## &#x200B;4. Définition de l’action

1. Sous la section **[!UICONTROL Actions]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Adobe Analytics]**.

1. Dans la liste déroulante **[!UICONTROL Type d’action]**, sélectionnez **[!UICONTROL Suivi]**.

1. Dans le volet de droite, ajoutez l’action ou l’état à envoyer à Analytics.

   Vous pouvez également choisir d’ajouter des données contextuelles supplémentaires à cette requête. N’oubliez pas que vous pouvez utiliser des éléments de données pour obtenir ces données de manière dynamique à partir du SDK.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

   Dans l’exemple suivant, un appel `TrackAction` est envoyé à Analytics avec des données contextuelles supplémentaires de `poi.name` égale au nom du point d’intérêt qui a déclenché cet événement d’entrée :

   ![« définir une action »](/help/assets/pt-setAction.png)

## &#x200B;5. Enregistrez la règle et recréez votre propriété

Une fois la configuration terminée, vérifiez que votre règle ressemble à l’image suivante :

![« règle créée »](/help/assets/pt-ruleComplete.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Recréez la propriété Launch et déployez-la dans l’environnement approprié.
