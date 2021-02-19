---
title: Notifications push
description: Cette section vous explique comment utiliser le service Places avec des notifications Push.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 8%

---


# Notifications push

Mobile Services vous permet d’envoyer des notifications Push aux segments Adobe Analytics. Dans le service Places, vous pouvez segmenter l’audience de votre message push en utilisant leurs interactions historiques avec vos points d’intérêt. Par exemple, vous pouvez envoyer un message aux utilisateurs qui se trouvent dans l’une de vos boutiques au cours des 30 derniers jours.

Avant de commencer, vérifiez que vous avez effectué les tâches suivantes :

* Les données du service Places ont été traitées par Adobe Analytics.

   Cela signifie que votre application mobile a envoyé avec succès des données du service Lieux dans une suite de rapports et que les données sont disponibles pour la segmentation.

* Le canal de notification Push dans Mobile Services est configuré.

   Pour plus d’informations, voir [Création d’un message push](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Découvrez comment envoyer une notification Push à un segment Analytics dans Mobile Services.

   Pour plus d’informations, voir [Création d’un message push](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Envoyer une notification

Dans l&#39;onglet **[!UICONTROL Audience]** du flux de travaux *Créer une notification Push*, vous pouvez créer l&#39;audience de ce message de l&#39;une des manières suivantes :

* Dans la liste déroulante **[!UICONTROL Segments Analytics]**, sélectionnez un segment Adobe Analytics créé précédemment.

* Dans la section **[!UICONTROL Segment personnalisé]**, créez une audience en utilisant les paramètres de segment personnalisé disponibles.

![configuration d’un message push](/help/assets/push-set-up.png)
