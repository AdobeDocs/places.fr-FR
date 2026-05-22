---
title: Création d’une règle pour votre propriété Places Service
description: Places SDK effectue le suivi de l’emplacement actuel, surveille les points d’intérêt configurés autour de l’emplacement actuel et suit les événements d’entrée et de sortie pour ces points d’intérêt.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
TQID: https://experienceleague.adobe.com/jyGVmk-oKX6-5vxZBx6Mz-QF8SBYxAWssvAxJ0QLYWQ
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
  - id: f9a2105e-7a47-4e85-9193-31a519a2cb83
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 939
ht-degree: 13%

---

# Créer des règles d’entrée et de sortie {#create-entry-exit-rules}

Avec l&#39;extension Places et une solution de surveillance des régions installées dans votre application mobile, vous pouvez créer des règles dans Adobe Experience Platform Launch qui sont déclenchées ou conditionnées par les données de localisation, y compris les événements d&#39;entrée et de sortie de localisation.

## Règles

Vous pouvez configurer une règle composée d’un événement, d’une condition et d’une action. Chaque règle se compose des éléments suivants :

* Un ou plusieurs événements
* Conditions (facultatives)
* Une ou plusieurs actions

### Événements Places Service

Places Service propose les événements suivants sur lesquels vous pouvez exécuter une règle :

* **Saisie du point d’intérêt**, qui est déclenché par Places SDK lorsque votre client saisit le point d’intérêt que vous avez configuré.
* **Quitter le point d’intérêt**, qui est déclenché par Places SDK lorsque votre client quitte le point d’intérêt que vous avez configuré.

### Conditions de Places Service

Les conditions définissent les critères que les données associées à l’événement, ou l’état partagé d’une extension dans cette instance, doivent respecter pour que l’action soit effectuée. Par exemple, vous pouvez définir une condition pour déclencher une action sur une entrée dans un café uniquement dans la ville de San Francisco.

Le SDK Places conserve les statuts suivants :

* Point d’intérêt actuel, qui fait référence au point d’intérêt dans lequel votre client se trouve actuellement.
* Dernier point ciblé quitté, qui fait référence au dernier point ciblé quitté par votre client.
* Dernier POI saisi, qui fait référence au dernier POI saisi par votre client.

Chaque point d’intérêt contient les éléments de données suivants :

* Identifiant
* Nom
* Latitude/longitude
* Rayon
* Métadonnées telles que la ville, le pays, l’État ou la catégorie

### Actions

Les actions définissent ce que l’application fera en réponse à la condition pour que la règle soit remplie pour l’événement déclenché. Par exemple, lorsque votre client accède à votre point d’intérêt, vous pouvez configurer un message de bienvenue à afficher sur son appareil mobile.

## Créer une règle : un exemple

>[!CAUTION]
>
>Cet exemple implique que vous ayez créé une bibliothèque POI de tous les cafés aux États-Unis. Pour plus d’informations sur la création de POI et de bibliothèques, consultez [Création d’un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) et *Création d’une bibliothèque* dans [Gestion de plusieurs bibliothèques](https://experienceleague.adobe.com/docs/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

La procédure ci-dessous est un exemple de création d’une règle qui renvoie une publication à Slack lorsque vous entrez dans un café à San Francisco.

L’événement, la condition et l’action sont définis comme suit :

* **Événement** : événement d’entrée de Places.
* **Condition** : la ville du **Point ciblé actuel** est San Francisco
* **Action** : envoyez une publication à Slack avec le nom du café saisi par votre client.

### Prérequis

Avant de créer une règle, vous devez créer un élément de données dans Adobe Experience Platform Launch. Les éléments de données renseignent automatiquement les informations nécessaires sur votre point d’intérêt dans le message de publication.

Pour créer un élément de données dans Experience Platform Launch :

1. Cliquez sur l’onglet **Data Elements**.
1. Cliquez sur **Ajouter un élément de données**.
1. Saisissez un nom, par exemple, **nom actuel du café**.
1. Dans la liste déroulante **Extension**, sélectionnez **Places - Beta**.
1. Dans **Élément de données**, sélectionnez **Ville**.
1. Dans le volet de droite, sélectionnez **POI actuel**.
1. Cliquez sur **Enregistrer**.

### Création d’une règle dans Experience Platform Launch pour Places Service

![création d’une règle](/help/assets/placesrule.png)

1. Dans Experience Platform Launch, cliquez sur l’onglet **[!UICONTROL Règles]**.
1. Cliquez sur **[!UICONTROL Ajouter une règle]**.
1. Saisissez le nom de la règle, par exemple **[!UICONTROL Suivre l’entrée pour le café dans SF]**.

### Créer un événement

1. Dans la section Événements , cliquez sur **[!UICONTROL + Ajouter]**. Les événements déterminent à quel moment vous souhaitez déclencher la règle.
1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Places - Beta]**.
1. Dans la liste déroulante **[!UICONTROL Type d’événement]**, sélectionnez **[!UICONTROL Saisir POI]**.
1. Dans **[!UICONTROL Nom]**, saisissez un nom pour l’événement ; par exemple **[!UICONTROL Entrée dans un café]**.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

### Créer une condition

1. Dans la section Conditions , cliquez sur **[!UICONTROL +Ajouter]**. Les conditions déterminent quels critères doivent être remplis pour que les mesures soient prises.
1. Dans **[!UICONTROL Type logique]**, sélectionnez Normal afin de permettre aux actions de s’exécuter si la condition est remplie.
1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Places - Beta]**.
1. Dans **[!UICONTROL Type de condition]**, sélectionnez **[!UICONTROL Ville]**.
1. Saisissez le nom d’une condition, par exemple, **[!UICONTROL Coffee shop in SF]**.
1. Dans le volet de droite, cliquez sur **[!UICONTROL Point ciblé actuel]**, puis, dans la liste déroulante, sélectionnez **[!UICONTROL San Francisco]** comme étant l’une de vos villes.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

### Créer une action

1. Dans la section **[!UICONTROL Actions]**, cliquez sur **[!UICONTROL + Ajouter]**.
1. Dans la liste déroulante **[!UICONTROL Extension]**, laissez l’option par défaut **[!UICONTROL Mobile Core]** sélectionnée.
1. Sélectionnez un type d’action, par exemple **[!UICONTROL Envoyer le postback]**.

   a. Dans **[!UICONTROL URL]**, saisissez l’URL de publication pour Slack, par exemple `https://hooks.slack.com/services/`.

   b. Pour envoyer un corps de publication, cochez la case **[!UICONTROL Ajouter un corps de publication]**.

   c. Dans **[!UICONTROL Corps de publication]**, ajoutez le corps de publication, par exemple : `{ "text": "A customer has entered" }`

   c. Saisissez un type de contenu, par exemple **[!UICONTROL application/json]**.

   d. Sélectionnez une valeur de délai d’expiration, par exemple **[!UICONTROL 5]**.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

### Publier la règle

1. Pour activer la règle, vous devez la publier. Pour plus d’informations sur la publication de votre règle dans Experience Platform Launch, voir [&#x200B; Publication &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html).

### Voir au-delà des entrées et des sorties

L’utilisation des entrées et des sorties du service Places pour déclencher des règles dans Experience Platform Launch est incroyablement puissante, mais vous pouvez également utiliser les données de localisation comme condition pour que d’autres événements se déclenchent. Par exemple, vous pouvez avoir un déclencheur d’événement Mobile Core Track Action prêt à se déclencher en fonction d’un événement d’appel trackAction particulier dans votre application. En fonction de cet événement, vous pouvez placer des conditions d’emplacement supplémentaires dans l’événement avant d’effectuer une action. Par exemple, ouvrez une enquête in-app lorsqu’un événement de `trackAction` d’achat se produit, mais **uniquement** si l’emplacement actuel de l’utilisateur ou de l’utilisatrice inclut des métadonnées Places Service spécifiques.

![créer une condition](/help/assets/places-condition.png)
