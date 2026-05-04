---
title: Notifications In-App
description: Cette section vous explique comment utiliser le service Places avec la messagerie In-App.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
TQID: https://experienceleague.adobe.com/Z39ybIytDRlCbkMthWjvk5F-oexy0C9gtqgK1mmyMxM
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 689
ht-degree: 2%

---

# Notifications In-App {#places-push-messaging}

Les informations suivantes vous montrent comment configurer des messages In-App à déclencher à partir d’événements du service Places.

>[!IMPORTANT]
>
>Les messages doivent se trouver sur un accès Analytics.

## Message in-app

Mobile Services vous permet d’utiliser les données de localisation envoyées à Analytics comme événement(s) et/ou condition de déclenchement d’un message in-app. Si des messages In-App sont déclenchés à partir du SDK et qu’il n’est pas nécessaire d’attendre que les données soient traitées par Analytics, les messages peuvent apparaître en temps réel dès que le déclencheur se produit.

### Notifications locales

Voici une liste des types de messagerie in-app disponibles :

* Plein écran
* Alerte
* Notifications locales

Ces types sont des messages in-app car ils sont déclenchés par le SDK. Les notifications locales ressemblent aux notifications push, car elles s’affichent lorsque l’application est en arrière-plan. Ces notifications diffusent également des notifications en temps réel lorsque les utilisateurs accèdent à vos points d’intérêt ou en sortent pendant que l’application est en arrière-plan.

### Conditions préalables

Avant de commencer, vous comprenez comment envoyer et créer un message in-app dans Mobile Services et comment fonctionnent les déclencheurs. Pour plus d’informations, voir [Créer un message in-app.](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=fr)

## Règles dans Experience Platform Launch

Vous pouvez créer des règles Experience Platform Launch qui envoient à Analytics les données que vous souhaitez pouvoir utiliser dans le cadre de vos règles de déclenchement de messages in-app. Vous pouvez utiliser les données des extensions Places dans vos règles Experience Platform Launch sous la forme d’événements et/ou de conditions en fonction de votre cas d’utilisation.

* Utilisation des données d’emplacement comme événement déclencheur.

  Par exemple, vous pouvez envoyer des données à Analytics lorsqu’un utilisateur saisit un point d’intérêt.

* Utilisation des données d’emplacement en tant que condition pour un événement déclencheur.

  Par exemple, si vous avez créé une balise de métadonnées personnalisée dans le service Places pour la météo à différents points d’intérêt, vous pouvez utiliser ces métadonnées comme paramètre de votre condition de règle. Bien que vous puissiez utiliser cette condition avec un événement d’entrée de point d’intérêt décrit précédemment, vous pouvez également utiliser la condition comme contexte pour n’importe quel événement.

Une fois la règle configurée avec les paramètres d’événement et de condition appropriés, terminez la configuration de la règle en configurant l’action pour envoyer des données à Analytics.

## Créer une action

Pour créer une action :

1. Sélectionnez l’extension **&#x200B;**.
1. Dans la liste déroulante **[!UICONTROL Type d’action]**, sélectionnez **[!UICONTROL Suivi.]**
1. Saisissez le nom de l’action.
1. Dans le volet de droite, dans **[!UICONTROL Données contextuelles]**, sélectionnez la paire clé-valeur pour définir les données contextuelles qui seront envoyées à Analytics.

Par exemple, vous pouvez sélectionner `poiname` comme clé et `{%%Last Entered POI Name}` comme valeur.

>[!TIP]
>
>Les règles de traitement Analytics peuvent être définies pour récupérer ces données contextuelles. Pour plus d’informations, voir [&#x200B; Règles de traitement &#x200B;](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=fr). Dans l’exemple de *Créer une action*, l’action envoie l’`poiname` comme contexte pour décrire l’événement d’entrée de point d’intérêt envoyé à Analytics.

![création d’une action](/help/assets/configure-action.png)

Voici un exemple de règle complète :

![règle terminée](/help/assets/create-a-rule.png)

## Création d’un message in-app dans Mobile Services

Dans le cadre de vos paramètres de déclencheur, vous pouvez créer l’audience du message avec des données du service Places de l’une des façons suivantes :

* Utilisation d’actions spécifiques à un emplacement, telles qu’une entrée ou une sortie.
* Utilisation des métadonnées de point d’intérêt envoyées en tant que données contextuelles pour cibler précisément l’audience.

  Cette option peut être utilisée avec une action spécifique à l’emplacement, telle qu’une entrée, ou elle peut être utilisée comme contexte pour un autre événement, tel qu’un lancement ou un clic sur un bouton.

  Voici un exemple de configuration d’un message in-app pour accueillir les utilisateurs qui entrent dans un point d’intérêt dont le nom contient **&#x200B;**&#x200B;:

  ![paramètres de déclenchement](/help/assets/trigger-parameters.png)

* Les paramètres des en-têtes Places Service de la page *Triggers et caractéristiques* de Mobile Services ne fonctionnent pas avec les données Places Service.

  Ces paramètres concernent uniquement la base de données Places Service héritée qui a été créée dans Mobile Services.
