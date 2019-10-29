---
title: Notifications in-app
seo-title: Notifications in-app
description: Cette section explique comment utiliser Places avec la messagerie in-app.
seo-description: Cette section explique comment utiliser Places avec la messagerie in-app.
translation-type: tm+mt
source-git-commit: 95c29df19f61e7854e39b47e39471f7f1e94b736

---


# Notifications in-app (#places-push-message)

Les informations suivantes montrent comment configurer les messages in-app pour qu’ils se déclenchent à partir d’événements Places.

>[!IMPORTANT]
>
>Les messages doivent figurer sur un accès Analytics.

## Message in-app

Mobile Services vous permet d’utiliser les données d’emplacement envoyées à Analytics comme événement(s) de déclenchement et/ou condition pour un message in-app. Si des messages in-app sont déclenchés à partir du SDK et qu’il n’est pas nécessaire d’attendre le traitement des données par Analytics, les messages peuvent s’afficher en temps réel dès que le déclencheur se produit.

### Notifications locales

Voici la liste des types de messagerie in-app disponibles :

* Plein écran
* Alerte
* Notifications locales

Ces types sont des messages in-app, car ils sont déclenchés par le SDK. Les notifications locales ressemblent aux notifications Push, car elles apparaissent lorsque l’application est en arrière-plan. Ces notifications fournissent également des notifications en temps réel lorsque les utilisateurs entrent dans vos points d’intérêt ou en sortent lorsque l’application est en arrière-plan. Pour plus d’informations, voir [Extension du moniteur de lieux.](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)

### Conditions préalables

Avant de commencer, vous devez comprendre comment envoyer et créer un message in-app dans Mobile Services et comment fonctionnent les déclencheurs. Pour plus d’informations, voir [Création d’un message in-app.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Règles dans Experience Platform Launch

Vous pouvez créer des règles de lancement qui envoient les données que vous souhaitez utiliser dans le cadre de votre message intégré Déclencheur de règles vers Analytics. Vous pouvez utiliser les données des extensions Lieux dans vos règles de lancement comme des événements et/ou des conditions selon votre cas d’utilisation.

* Utilisation des données d’emplacement comme événement de déclenchement.

   Par exemple, vous pouvez envoyer des données à Analytics lorsqu’un utilisateur entre dans un point d’accès.

* Utilisation des données d’emplacement comme condition à un événement de déclenchement.

   Par exemple, si vous avez créé une balise de métadonnées personnalisée dans le service d’emplacement pour la météo dans différents points d’intérêt, vous pouvez utiliser ces métadonnées comme paramètre pour votre condition de règle. Bien que vous puissiez utiliser cette condition avec un événement d’entrée d’API décrit précédemment, vous pouvez également utiliser la condition comme contexte pour tout événement.

Une fois la règle configurée avec les paramètres d’événement et de condition appropriés, terminez la configuration de la règle en configurant l’action pour envoyer des données à Analytics.

## Créer une action

Pour ce faire :

1. Sélectionnez l’extension **.[!UICONTROL Adobe Analytics]**
1. Dans la liste **[!UICONTROL Action type]** déroulante, sélectionnez **[!UICONTROL Track.]**
1. Entrez le nom de votre action.
1. Dans le volet de droite, dans **[!UICONTROL Context Data]**, sélectionnez la paire clé/valeur pour définir les données contextuelles qui seront envoyées à Analytics.

Par exemple, vous pouvez sélectionner **[!UICONTROL poiname]** comme clé et **[!UICONTROL `{%%Last Entered POI Name}`.]

>[!TIP]
>
>Les règles de traitement Analytics peuvent être définies pour sélectionner ces données contextuelles. For more information, see [Processing Rules](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). Dans l’exemple de *Création d’une action*, l’action envoie le `poiname` sous forme de contexte pour décrire l’événement POIentry envoyé à Analytics.

![création d’une action](/help/assets/configure-action.png)

Voici un exemple de règle complète :

![règle terminée](/help/assets/create-a-rule.png)

## Création d’un message in-app dans AMS

Dans le cadre des paramètres de déclenchement, vous pouvez créer l’audience du message avec les données du service d’emplacement de l’une des manières suivantes :

* Utilisation d’actions spécifiques à un emplacement, telles qu’une entrée ou une sortie.
* Utilisation de métadonnées de point d’accès envoyées en tant que données contextuelles pour restreindre la cible de votre audience.

   Cette option peut être utilisée avec une action spécifique à un emplacement, telle qu’une entrée, ou peut être utilisée comme contexte à un autre événement, tel qu’un lancement ou un clic sur un bouton.

   Voici un exemple de configuration d’un message in-app afin d’accueillir les utilisateurs qui entrent dans un point d’accès qui porte **[!UICONTROL Adobe]** le nom :

   ![paramètres de déclenchement](/help/assets/trigger-parameters.png)

* Les paramètres des en-têtes Places de la page *Déclencheurs et caractéristiques* de Mobile Services ne fonctionnent pas avec les données du service d’emplacement. Ces paramètres concernent uniquement la base de données Places héritée créée dans Mobile Services.