---
title: Notifications in-app
description: Cette section vous explique comment utiliser le service Places avec la messagerie in-app.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 4%

---


# Notifications in-app {#places-push-messaging}

Les informations suivantes montrent comment configurer les messages in-app pour qu’ils se déclenchent à partir des événements du service Places.

>[!IMPORTANT]
>
>Les messages doivent figurer sur un accès Analytics.

## Message in-app

Mobile Services vous permet d’utiliser les données d’emplacement envoyées à Analytics en tant que événement de déclenchement et/ou condition pour un message in-app. Si des messages in-app sont déclenchés à partir du SDK et qu’il n’est pas nécessaire d’attendre que les données soient traitées par Analytics, les messages peuvent s’afficher en temps réel dès que le déclencheur se produit.

### Notifications locales

Voici une liste des types de messagerie in-app disponibles :

* Plein écran
* Alerte
* Notifications locales

Ces types sont des messages in-app car ils sont déclenchés par le SDK. Les notifications locales ressemblent aux notifications Push car elles s’affichent lorsque l’application est en arrière-plan. Ces notifications délivrent également des notifications en temps réel lorsque les utilisateurs entrent ou sortent de vos points d’intérêt pendant que l’application est en arrière-plan. Pour plus d&#39;informations, voir [Place Monitor extension](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

### Conditions préalables

Avant de commencer, vous devez comprendre comment envoyer et créer un message in-app dans Mobile Services et comment fonctionnent les déclencheurs. Pour plus d’informations, voir [Créer un message in-app.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Règles dans Experience Platform Launch

Vous pouvez créer des règles d’Experience Platform Launch qui envoient les données que vous souhaitez utiliser dans le cadre de votre message intégré Déclencheur de règles à Analytics. Vous pouvez utiliser les données des extensions Lieux dans vos règles d’Experience Platform Launch sous la forme de événements et/ou de conditions, selon votre cas d’utilisation.

* Utilisation des données d’emplacement comme événement de déclenchement.

   Par exemple, vous pouvez envoyer des données à Analytics lorsqu’un utilisateur entre dans un point d’intérêt.

* Utilisation des données d’emplacement comme condition à un événement de déclenchement.

   Par exemple, si vous avez créé une balise de métadonnées personnalisée dans le service des emplacements pour la météo à différents points d’intérêt, vous pouvez utiliser ces métadonnées comme paramètre pour votre condition de règle. Bien que vous puissiez utiliser cette condition avec un événement d’entrée POI décrit plus haut, vous pouvez également utiliser la condition comme contexte pour n’importe quel événement.

Une fois la règle configurée avec les paramètres de événement et de condition appropriés, terminez la configuration de la règle en configurant l’action pour envoyer des données à Analytics.

## Créer une action

Pour créer une action :

1. Sélectionnez l&#39;extension **[!UICONTROL Adobe Analytics]**.
1. Dans la liste déroulante **[!UICONTROL Type d&#39;action]**, sélectionnez **[!UICONTROL Suivi.]**
1. Tapez le nom de votre action.
1. Dans le volet de droite, dans **[!UICONTROL Données contextuelles]**, sélectionnez la paire clé-valeur pour définir les données contextuelles qui seront envoyées à Analytics.

Par exemple, vous pouvez sélectionner `poiname` comme clé et `{%%Last Entered POI Name}` comme valeur.

>[!TIP]
>
>Les règles de traitement d’Analytics peuvent être définies pour récupérer ces données contextuelles. Pour plus d’informations, reportez-vous à la section [Règles de traitement](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). Dans l’exemple de *Création d’une action*, l’action envoie `poiname` comme contexte pour décrire le événement d’entrée POI envoyé à Analytics.

![création d’une action](/help/assets/configure-action.png)

Voici un exemple de règle complète :

![règle terminée](/help/assets/create-a-rule.png)

## Création d’un message in-app dans Mobile Services

Dans le cadre des paramètres Déclencheur, vous pouvez créer l’audience du message avec les données du service Lieux de l’une des manières suivantes :

* Utilisation d’actions spécifiques à un emplacement, telles qu’une entrée ou une sortie.
* Utilisation de métadonnées de point d’accès qui sont envoyées en tant que données contextuelles pour limiter la cible de votre audience.

   Cette option peut être utilisée avec une action spécifique à un emplacement, telle qu’une entrée, ou peut être utilisée comme contexte à un autre événement, tel qu’un lancement ou un clic de bouton.

   Voici un exemple de configuration d’un message in-app afin d’accueillir les utilisateurs qui entrent dans un point d’accès qui comporte **[!UICONTROL Adobe]** dans le nom :

   ![paramètres de déclenchement](/help/assets/trigger-parameters.png)

* Les paramètres des en-têtes du service Emplacements de la page *Déclencheurs et traits* de Mobile Services ne fonctionnent pas avec les données du service Emplacements.

   Ces paramètres concernent uniquement la base de données Places Service héritée qui a été créée dans Mobile Services.