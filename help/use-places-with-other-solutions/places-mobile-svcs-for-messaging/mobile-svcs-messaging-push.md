---
title: Notifications push
description: Cette section vous explique comment utiliser le service Places avec les notifications push.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 8%

---

# Notifications push

Mobile Services vous permet d’envoyer des notifications push aux segments Adobe Analytics. Dans Places Service, vous pouvez segmenter l’audience de votre message push à l’aide de leurs interactions historiques avec vos points ciblés. Par exemple, vous pouvez envoyer un message aux utilisateurs qui se trouvent dans l’un de vos magasins au cours des 30 derniers jours.

Avant de commencer, assurez-vous d’avoir effectué les tâches suivantes :

* Les données du service Places ont été traitées par Adobe Analytics.

   Cela signifie que votre application mobile a bien envoyé les données du service Places dans une suite de rapports et que les données sont disponibles pour la segmentation.

* Le canal des notifications push dans Mobile Services est configuré.

   Pour plus d’informations, voir [Création d’un message push](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Découvrez comment envoyer une notification push à un segment Analytics dans Mobile Services.

   Pour plus d’informations, voir [Création d’un message push](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Envoyer une notification

Sur le **[!UICONTROL Audience]** de l’onglet *Créer une notification push* vous pouvez créer l&#39;audience de ce message de l&#39;une des manières suivantes :

* Dans le **[!UICONTROL Segments Analytics]** , sélectionnez un segment Adobe Analytics créé précédemment.

* Dans le **[!UICONTROL Segment personnalisé]** , créez une audience à l’aide des paramètres de segment personnalisés disponibles.

![configuration d’un message push](/help/assets/push-set-up.png)
