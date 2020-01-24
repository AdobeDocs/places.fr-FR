---
title: Messages in-app avec le service Places
description: Cette section fournit des informations sur l’utilisation de la messagerie Push dans Campaign Standard avec des messages in-app dans Campaign Standard.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Messagerie in-app avec le service Places {#in-app-messages-loc-service}

Ces informations vous aident à comprendre comment utiliser les informations du service Places pour envoyer des messages in-app ou des notifications locales.

## Conditions préalables 

Avant de commencer, effectuez les tâches suivantes :

* Disposez d’une application mobile configurée avec le SDK mobile Adobe Experience Platform, y compris l’extension [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Intégrez le SDK [mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform à votre application.
* Ajoutez [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à la configuration de votre application mobile.

* [Créez un point d’accès](/help/poi-mgmt-ui/create-a-poi-ui.md) dans l’interface de gestion des points d’accès du service Places.

* Installez et configurez l’extension [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md) et les extensions [](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) Places Monitor dans votre application mobile.

## Envoi d’un message in-app basé sur une entrée ou une sortie de géolocalisation

1. Dans votre instance Adobe Campaign Standard, cliquez sur **[!UICONTROL Create In-App message]**.
1. Pour le type de message, sélectionnez **[!UICONTROL Target all users of a Mobile application]**.
1. Cliquez sur **[!UICONTROL Next]**et saisissez les détails généraux.
1. Dans le volet de gauche, vérifiez que vous pouvez utiliser divers déclencheurs liés aux services Places.

   * Vous pouvez choisir d’afficher le message in-app si l’utilisateur a saisi une clôture d’accès aux données d’identification géographique.
   * Vous pouvez également utiliser des métadonnées définies dans l’interface utilisateur des services Places pour filtrer l’audience.
   Dans l’exemple ci-dessous, vous pouvez déclencher un message in-app qui s’affiche uniquement pour les utilisateurs qui entrent dans l’un des centres de villégiature participant à un programme de boisson gratuite et vous souhaitez envoyer un bon à ces utilisateurs lorsqu’ils arrivent.

   ![&quot;Métadonnées de place des messages in-app&quot;](/help/assets/last-entered-vacation.png)

1. Click the **[!UICONTROL Next]**to finish creating the In-app message for delivery.

   ![&quot;créer un événement&quot;](/help/assets/prepare-ACS.png)

   Pour tester la remise des messages in-app, lancez l’application dans Xcode ou Android studio et utilisez le simulateur d’emplacement pour sélectionner un point d’accès correspondant aux critères de messagerie.

   ![&quot;coupon de boisson&quot;](/help/assets/drink-coupon-on-app.png)

L’utilisation de Places Services avec Adobe Campaign Standard vous offre un outil puissant pour segmenter et cibler vos messages sur les utilisateurs en fonction des entrées et des sorties de géolocalisation. Cette intégration vous permet de créer des cas d’utilisation plus personnalisés et contextuels.

>[!VIDEO](https://www.youtube.com/watch?v=ikiTTQw9c-o)