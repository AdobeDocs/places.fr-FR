---
title: Notifications Push
seo-title: Notifications Push
description: Cette section explique comment utiliser Places avec des notifications Push.
seo-description: Cette section explique comment utiliser Places avec des notifications Push.
translation-type: tm+mt
source-git-commit: 60c274c309a2c86b67d6c19ea28ae300a37d723a

---


# Notifications Push

Mobile Services vous permet d’envoyer des notifications Push aux segments Adobe Analytics. Dans le service d’emplacement, vous pouvez segmenter l’audience de votre message push en utilisant leurs interactions historiques avec vos points d’intérêt. Par exemple, vous pouvez envoyer un message aux utilisateurs qui se trouvent dans l’une de vos boutiques au cours des 30 derniers jours.

Avant de commencer, vérifiez que vous avez effectué les tâches suivantes :

* Les données du service d’emplacement ont été traitées par Adobe Analytics.

   Cela signifie que votre application mobile a réussi à envoyer les données du service d’emplacement dans une suite de rapports et que les données sont disponibles pour la segmentation.

* Le canal de notification Push dans Mobile Services est configuré.

   Pour plus d’informations, voir [Création d’un message push](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Découvrez comment envoyer une notification Push à un segment Analytics dans Mobile Services.

   Pour plus d’informations, voir [Création d’un message push](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Envoyer une notification

Dans l’ **[!UICONTROL Audience]** onglet du flux de travail *Créer une notification* Push, vous pouvez créer l’audience pour ce message de l’une des manières suivantes :

* Dans la liste **[!UICONTROL Analytics Segments]** déroulante, sélectionnez un segment Adobe Analytics créé précédemment.

* Dans la **[!UICONTROL Custom Segment]** section, créez une audience à l’aide des paramètres de segment personnalisé disponibles.

![configuration d’un message push](/help/assets/push-set-up.png)
