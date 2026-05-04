---
title: Ajout du contexte d’emplacement aux requêtes Analytics
description: Cette section fournit des informations sur la manière d’ajouter un contexte d’emplacement aux requêtes Analytics.
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
TQID: https://experienceleague.adobe.com/NR-CowJgzUBMVWcbV-EvdyBDsiwLi72yxM-Vjx5oNwk
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: b069d60e-95f3-44d6-95a8-ddc862a4bc38id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 512
ht-degree: 3%

---

# Ajout du contexte d’emplacement aux requêtes Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Ce document suppose que le service Places est implémenté dans votre application. Pour plus d’informations sur l’implémentation de Places Service, voir [Extensions Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Une fois que Places Service a envoyé les événements d’entrée et de sortie, vous pouvez créer des règles dans Experience Platform Launch et joindre vos données Places Service à tous les événements Adobe Analytics. Pour créer ce type de règle, sélectionnez votre propriété dans Launch et effectuez les étapes suivantes :

## &#x200B;1. Création d’une règle

1. Dans l’onglet **[!UICONTROL Règles]**, cliquez sur **[!UICONTROL Créer une règle]**.

   Gardez à l’esprit les informations suivantes :
   * Si vous ne disposez pas de règles existantes pour cette propriété, le bouton **[!UICONTROL Créer une règle]** se trouve au milieu de l’écran.
   * Si votre propriété comporte des règles, le bouton **[!UICONTROL Créer une règle]** s’affiche en haut à droite de l’écran.

## 2.Sélectionner un événement

1. Donnez à votre règle un nom significatif afin qu’elle soit facilement reconnaissable dans votre liste de règles.

   Dans cet exemple, la règle est nommée **[!UICONTROL Joindre des données du service Places aux événements d’action de suivi Analytics]**.

1. Sous la section **[!UICONTROL Événements]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]**.

1. Dans la liste déroulante **[!UICONTROL Type d’événement]**, sélectionnez **[!UICONTROL Suivre l’action]**.

Vous pouvez maintenant déterminer les déclencheurs que vous souhaitez inclure pour cette règle. Dans cet exemple, le déclencheur est basé sur tous les appels `TrackAction`. Après avoir configuré l’événement, cliquez sur **[!UICONTROL Conserver les modifications]**.

![« créer un événement »](/help/assets/ad-setEvent_use-analytics-data.png)


## &#x200B;3. Ajouter des conditions

>[!IMPORTANT]
>
>Suivez cette procédure pour ajouter des conditions à votre règle. Sinon, passez à la section *Définir l’action* ci-dessous.

Dans cet exemple, une condition est créée qui entraîne le déclenchement de la règle uniquement pour les clients AT&amp;T.

1. Dans la section **[!UICONTROL Conditions]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]**.

1. Dans la liste déroulante **[!UICONTROL Type de condition]**, sélectionnez **[!UICONTROL Nom de l’opérateur]**.

1. Dans la fenêtre de droite, cochez la case **[!UICONTROL AT&amp;T]**.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

![« créer une condition »](/help/assets/ad-setCondition_use-analytics-data.png)

## &#x200B;4. Définition de l’action

1. Sous la section **[!UICONTROL Actions]**, cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]**.

1. Dans la liste déroulante **[!UICONTROL Type d’action]**, sélectionnez **[!UICONTROL Joindre des données]**.

1. Dans le volet de droite, dans le champ **[!UICONTROL Payload JSON]**, saisissez les données qui seront ajoutées à cet événement.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

Dans le volet de droite, vous pouvez ajouter une payload JSON à structure libre qui ajoute des données à un événement SDK avant qu’une extension qui écoute cet événement puisse entendre l’événement. Dans cet exemple, certaines données contextuelles sont ajoutées à cet événement avant que l’extension Analytics ne le traite. Les données contextuelles ajoutées se trouvent désormais sur l’accès Analytics sortant.

Dans l’exemple suivant, les valeurs `poi.city` et `poi.name` sont ajoutées aux données contextuelles de l’événement Analytics. Les valeurs des nouvelles clés sont déterminées dynamiquement par le SDK lors du traitement de cet événement.

![« créer une action »](/help/assets/ad-setAction_use-analytics-data.png)

## &#x200B;5. Enregistrez la règle et recréez votre propriété

Une fois la configuration terminée, vérifiez que votre règle ressemble à l’image suivante :

![« la règle est terminée.« ](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Recréez la propriété Launch et déployez-la dans l’environnement approprié.
