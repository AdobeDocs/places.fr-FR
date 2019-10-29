---
title: Messagerie in-app
seo-title: Messagerie in-app
description: Cette section explique comment utiliser Places avec la messagerie in-app.
seo-description: Cette section explique comment utiliser Places avec la messagerie in-app.
translation-type: tm+mt
source-git-commit: 7985943cef606525401983c4c80862c277f41bf0

---


# Notifications in-app (#places-push-message)

Configuration des messages in-app à déclencher à partir des événements Places ; les messages doivent figurer sur un accès Analytics.

## Message in-app

AMS vous permet d’utiliser les données d’emplacement envoyées à Analytics comme événement(s) de déclenchement et/ou condition pour un message in-app. Les messages in-app peuvent s’afficher en temps réel à l’utilisateur dès que le déclencheur est déclenché à partir du SDK et il n’est pas nécessaire d’attendre que les données soient traitées par Analytics.

Notifications locales : La messagerie in-app comporte trois types différents :

* Plein écran
* Alerte
* Notifications locales.

Ces types sont considérés comme des messages in-app car ils sont déclenchés par le SDK, mais il est important de noter que les notifications locales ressemblent aux notifications Push lorsqu’elles apparaissent alors que l’application n’est pas au premier plan. Les notifications locales constituent une excellente option pour envoyer des notifications en temps réel aux utilisateurs lorsqu’ils entrent ou sortent de vos points d’intérêt pendant que l’application est en arrière-plan. Consultez la documentation de l’extension Places Monitor pour comprendre la surveillance de l’emplacement (https://placesdocs.com/places-services-by-adobe-documentation/configure-places-in-the-sdk/places-monitor-extension).

### Conditions préalables

* Découvrez comment envoyer et créer un message in-app dans AMS et comment fonctionnent les déclencheurs.

   Pour plus d’informations, voir [Création d’un message in-app](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html).


## Création d’une règle dans Experience Platform Launch

Créez des règles de lancement qui envoient les données correctes à Analytics que vous souhaitez utiliser dans le cadre de vos règles Déclencheur de message in-app. Vous pouvez utiliser les données des extensions Lieux dans vos règles de lancement comme des événements et/ou des conditions selon votre cas d’utilisation.

* Utilisation des données d’emplacement comme événement de déclenchement. Par exemple, si vous souhaitez envoyer des données à Analytics lorsqu’un utilisateur entre dans un point d’accès.

* Utilisation des données d’emplacement comme condition à un événement de déclenchement. Par exemple, si vous avez créé une balise de métadonnées personnalisée dans le service d’emplacement pour la météo dans différents points d’intérêt, vous pouvez utiliser ces métadonnées comme paramètre pour votre condition de règle, comme illustré ci-dessous. Bien que vous puissiez utiliser cette condition avec l’événement d’entrée POI décrit précédemment, vous pouvez également l’utiliser comme contexte pour tout événement.

Une fois la règle configurée avec les paramètres d’événement et de condition appropriés, terminez votre configuration de règle en configurant l’action pour envoyer des données à Analytics. Pour ce faire :

* Sélectionner Adobe Analytics comme extension
* Choisissez "Suivi" comme type d’action.
* Détermination du nom de votre action
* Définissez les données contextuelles à envoyer avec l’événement. Utilisez l’interface Données contextuelles pour mapper les éléments de données de lancement aux noms de clés que vous souhaitez envoyer à Analytics.

Notez que les règles de traitement Analytics peuvent être définies pour sélectionner ces données contextuelles. Voir les règles de traitement Analytics si nécessaire (https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html) Par exemple, cette action envoie le nom pointé en tant que contexte pour décrire l’événement POIentry envoyé à Analytics.

![création d’une action](/help/assets/configure-action.png)

Voici un exemple de ce à quoi la règle finie pourrait ressembler.

![règle terminée](/help/assets/create-a-rule.png)

## Création d’un message in-app dans AMS :

Vous allez créer l’audience du message avec les données du service d’emplacement dans le cadre de vos paramètres de déclenchement.

* Utilisation d’actions spécifiques à l’emplacement, telles que l’entrée ou la sortie
* Utilisation de métadonnées de point d’accès envoyées sous forme de données contextuelles pour restreindre la cible de votre audience. Il peut être utilisé avec une action spécifique à un emplacement, telle qu’une entrée, ou comme contexte à un autre événement, tel qu’un lancement ou un clic sur un bouton.

   Voici un exemple de configuration d’un message in-app pour accueillir les utilisateurs qui entrent dans un point d’intérêt dont le nom contient "Adobe" :

   ![paramètres de déclenchement](/help/assets/trigger-parameters.png)

* Les paramètres trouvés dans les en-têtes "Lieux" dans les Triggers et Caractéristiques AMS ne fonctionnent pas avec les données du service de localisation. Ces paramètres concernent la base de données Places héritée créée dans AMS.