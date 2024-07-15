---
title: Notifications In-App
description: Cette section vous explique comment utiliser le service Places avec la messagerie In-App.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# Notifications In-App {#places-push-messaging}

Les informations suivantes vous montrent comment configurer les messages In-App à déclencher à partir des événements Places Service.

>[!IMPORTANT]
>
>Les messages doivent se trouver sur un accès Analytics.

## Message in-app

Mobile Services vous permet d’utiliser les données d’emplacement envoyées à Analytics comme événement(s) de déclenchement et/ou condition d’un message in-app. Si les messages In-App sont déclenchés à partir du SDK et n’ont pas besoin d’attendre que les données soient traitées par Analytics, ils peuvent s’afficher en temps réel dès que le déclencheur se produit.

### Notifications locales

Voici une liste des types de messagerie in-app disponibles :

* Plein écran
* Alerte
* Notifications locales

Ces types sont des messages in-app, car ils sont déclenchés par le SDK. Les notifications locales ressemblent aux notifications push, car elles apparaissent lorsque l’application est en arrière-plan. Ces notifications diffusent également des notifications en temps réel lorsque les utilisateurs entrent ou sortent de vos points ciblés lorsque l’application est en arrière-plan.

### Conditions préalables

Avant de commencer, vous devez comprendre comment envoyer et créer un message in-app dans Mobile Services, ainsi que le fonctionnement des déclencheurs. Pour plus d’informations, voir [Création d’un message in-app.](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=fr)

## Règles dans Experience Platform Launch

Vous pouvez créer des règles Experience Platform Launch qui envoient les données que vous souhaitez pouvoir utiliser dans le cadre de vos règles de déclenchement de messages in-app à Analytics. Vous pouvez utiliser les données des extensions Places dans vos règles Experience Platform Launch sous la forme d’événements et/ou de conditions selon votre cas d’utilisation.

* Utilisation des données d’emplacement comme événement de déclenchement.

  Par exemple, vous pouvez envoyer des données à Analytics lorsqu’un utilisateur entre dans un point ciblé.

* Utilisation des données d’emplacement comme condition à un événement de déclenchement.

  Par exemple, si vous avez créé une balise de métadonnées personnalisée dans le service Places pour la météo à différents points ciblés, vous pouvez utiliser ces métadonnées comme paramètre pour votre condition de règle. Bien que vous puissiez utiliser cette condition avec un événement d’entrée de point ciblé décrit précédemment, vous pouvez également utiliser la condition comme contexte pour tout événement.

Une fois la règle configurée avec les paramètres d’événement et de condition appropriés, effectuez la configuration de la règle en configurant l’action pour envoyer des données à Analytics.

## Créer une action

Pour créer une action :

1. Sélectionnez l’extension **[!UICONTROL Adobe Analytics]**.
1. Dans la liste déroulante **[!UICONTROL Action type]**, sélectionnez **[!UICONTROL Track.]**
1. Saisissez le nom de votre action.
1. Dans le volet de droite, dans **[!UICONTROL Données contextuelles]**, sélectionnez la paire clé-valeur pour définir les données contextuelles qui seront envoyées à Analytics.

Par exemple, vous pouvez sélectionner `poiname` comme clé et `{%%Last Entered POI Name}` comme valeur.

>[!TIP]
>
>Les règles de traitement Analytics peuvent être définies pour récupérer ces données contextuelles. Pour plus d’informations, voir [Règles de traitement](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html). Dans l’exemple de *Créer une action*, l’action envoie `poiname` comme contexte pour décrire l’événement d’entrée de point ciblé envoyé à Analytics.

![création d’une action](/help/assets/configure-action.png)

Voici un exemple de règle complète :

![règle terminée](/help/assets/create-a-rule.png)

## Création d’un message in-app dans Mobile Services

Dans le cadre de vos paramètres Déclencheur, vous pouvez créer l&#39;audience du message avec les données du service Places de l&#39;une des manières suivantes :

* Utilisation d’actions spécifiques à un emplacement, telles qu’une entrée ou une sortie.
* Utilisation de métadonnées de point ciblé envoyées en tant que données contextuelles pour réduire la cible de votre audience.

  Cette option peut être utilisée avec une action spécifique à un emplacement, telle qu’une entrée, ou elle peut être utilisée comme contexte à un autre événement, tel qu’un lancement ou un clic sur un bouton.

  Voici un exemple de configuration d’un message in-app pour accueillir les utilisateurs qui entrent dans un point ciblé dont le nom contient **[!UICONTROL Adobe]** :

  ![paramètres de déclenchement](/help/assets/trigger-parameters.png)

* Les paramètres des en-têtes du service Places de la page *Triggers and Traits* de Mobile Services ne fonctionnent pas avec les données du service Places.

  Ces paramètres concernent uniquement la base de données Places Service héritée qui a été créée dans Mobile Services.
