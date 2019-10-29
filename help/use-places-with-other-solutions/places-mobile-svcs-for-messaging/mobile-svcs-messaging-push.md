---
title: Messagerie Push
seo-title: Messagerie Push
description: Cette section vous explique comment utiliser Places avec la messagerie push.
seo-description: Cette section vous explique comment utiliser Places avec la messagerie push.
translation-type: tm+mt
source-git-commit: accfa6ba009ad3419481d9bd3b498143228099fc

---


# Notifications Push (#places-push-message)

Notification Push : AMS vous permet d’envoyer des notifications Push aux segments Adobe Analytics. Le service d’emplacement vous permet de segmenter l’audience de votre message push en fonction de leurs interactions historiques avec vos points d’intérêt. Par exemple, vous pouvez envoyer un message aux utilisateurs qui se trouvent dans l’un de vos magasins au cours des 30 derniers jours.

Avant de commencer, vérifiez que vous avez effectué les tâches suivantes :

* Les données du service d’emplacement ont été traitées par Adobe Analytics.

   Cela signifie que votre application mobile a réussi à envoyer les données du service d’emplacement dans une suite de rapports et que les données sont disponibles pour la segmentation.

* Le canal de notification Push dans Mobile Services est configuré.

   Pour plus d’informations, voir [Création d’un message push](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Familiarisez-vous avec la manière d’envoyer une notification Push à un segment Analytics dans Mobile Services.

   * Pour plus d’informations, voir [Création d’un message push](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Envoi d’une notification

Dans l’ **[!UICONTROL Audience]** onglet du flux de travail *Créer une notification* Push, vous pouvez créer l’audience pour ce message de l’une des manières suivantes :

* Sélectionnez un segment Adobe Analytics créé précédemment.

* Créez une audience en utilisant les paramètres de segment personnalisé disponibles.

![configuration d’un message push](/help/assets/push-set-up.png)

