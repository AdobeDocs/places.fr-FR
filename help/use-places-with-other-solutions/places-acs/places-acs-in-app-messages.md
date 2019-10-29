---
title: Messages in-app avec le service d’emplacement
seo-title: Messages in-app avec le service d’emplacement
description: Cette section fournit des informations sur l’utilisation de la messagerie Push dans Campaign Standard avec des messages in-app dans Campaign Standard.
seo-description: 'Cette section fournit des informations sur la manière d’utiliser "Messagerie Push dans Campaign Standard" avec les messages in-app dans Campaign Standard. '
translation-type: tm+mt
source-git-commit: 95c29df19f61e7854e39b47e39471f7f1e94b736

---


# Messagerie in-app avec le service de localisation {#in-app-messages-loc-service}

Ces informations vous aident à comprendre comment utiliser les informations du service d’emplacement de la plate-forme Adobe Experience Platform pour envoyer des messages in-app ou des notifications locales.

>[!IMPORTANT]
>
>Avant de commencer, effectuez les tâches suivantes :
>
>* Configurez une application mobile avec le SDK mobile Adobe Experience Platform, y compris l’extension [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.
   >
   >
* Intégrez le SDK [mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform à votre application.
>* Ajoutez [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à la configuration de votre application mobile.
   >
   >
* [Créez un point d’accès](/help/poi-mgmt-ui/create-a-poi-ui.md) dans l’interface de gestion des points d’accès.
   >
   >
* Installez et configurez l’extension [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md) et les extensions [](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) Places Monitor dans votre application mobile.


## Envoi d’un message in-app basé sur une entrée ou une sortie de géolocalisation

1. Dans votre instance Adobe Campaign Standard, cliquez sur **[!UICONTROL Create In-App message]**.
2. Pour le type de message, sélectionnez **[!UICONTROL Target all users of a Mobile application]**.
3. Cliquez sur **[!UICONTROL Next]** et saisissez les détails généraux.
4. Dans le volet de gauche, vérifiez que vous pouvez désormais utiliser divers déclencheurs liés aux services de localisation.

   * Vous pouvez choisir d’afficher le message in-app si l’utilisateur a saisi une clôture d’accès aux données d’identification géographique.
   * Vous pouvez également utiliser des métadonnées définies dans l’interface utilisateur des services d’emplacement pour filtrer l’audience.
   Dans l’exemple illustré ci-dessous, vous pouvez déclencher un message in-app qui s’affiche uniquement pour les utilisateurs qui sont entrés dans l’un des centres de vacances participant à un programme de boisson gratuite. Vous souhaitez envoyer un bon à vos utilisateurs lorsqu’ils arrivent.

   !["Métadonnées de place des messages in-app"](/help/assets/last-entered-vacation.png)

5. Cliquez sur **[!UICONTROL Next]** pour terminer la création du message in-app en vue de sa diffusion.

   !["créer un événement"](/help/assets/prepare-ACS.png)

   Pour tester la remise des messages in-app, lancez l’application dans Xcode ou Android studio et utilisez le simulateur d’emplacement pour sélectionner un point d’accès correspondant aux critères de messagerie.

   !["coupon de boisson"](/help/assets/drink-coupon-on-app.png)


L’utilisation des services de localisation avec Adobe Campaign Standard vous offre un outil puissant pour segmenter et cibler vos messages sur les utilisateurs en fonction des entrées et des sorties de géolocalisation. Cette simple intégration ouvre la porte à la création de cas d'utilisation plus personnalisés et contextuels.

>[!VIDEO](https://www.youtube.com/watch?v=ikiTTQw9c-o)