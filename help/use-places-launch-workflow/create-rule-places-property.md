---
title: Création d’une règle pour la propriété Places Service
description: Le SDK Places effectue le suivi de l’emplacement actuel, surveille les points ciblés configurés autour de l’emplacement actuel et suit les événements d’entrée et de sortie pour ces points ciblés.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 14%

---

# Création de règles d’entrée et de sortie {#create-entry-exit-rules}

Avec l’extension Places et une solution de surveillance de région installée dans votre application mobile, vous pouvez créer des règles dans Adobe Experience Platform Launch qui sont des données d’emplacement déclenchées ou conditionnées, y compris les événements d’entrée et de sortie d’emplacement.

## Règles

Vous pouvez configurer une règle composée d’un événement, d’une condition et d’une action. Chaque règle est composée des éléments suivants :

* Un ou plusieurs événements
* Conditions (facultatives)
* Une ou plusieurs actions

### Événements du service Places

Places Service propose les événements suivants sur lesquels vous pouvez exécuter une règle :

* **Entrez POI**, qui est déclenché par le SDK Places lorsque votre client entre dans le POI que vous avez configuré.
* **Quitter le POI**, qui est déclenché par le SDK Places lorsque votre client quitte le POI que vous avez configuré.

### Conditions du service Places

Les conditions définissent les critères que les données associées à l’événement, ou l’état partagé d’une extension sur cette instance, doivent satisfaire pour que l’action soit entreprise. Par exemple, vous pouvez définir une condition pour déclencher une action sur une entrée d’un café uniquement dans la ville de San Francisco.

Le SDK Places conserve les états suivants :

* Point ciblé actuel, qui fait référence au point ciblé où se trouve actuellement votre client.
* Dernier point ciblé de sortie, qui fait référence au point ciblé le plus récent auquel votre client a quitté le site.
* Dernier point ciblé saisi, qui fait référence au point ciblé le plus récent que votre client a saisi.

Chaque point ciblé contient les éléments de données suivants :

* Identifiant
* Nom
* Latitude/longitude
* Rayon
* Métadonnées telles que ville, pays, état, catégorie

### Actions

Les actions définissent ce que l’application fera en réponse à la condition que la règle soit remplie pour l’événement déclenché. Par exemple, lorsque votre client entre dans votre point ciblé, vous pouvez configurer un message de bienvenue à afficher sur son appareil mobile.

## Créer une règle : exemple

>[!CAUTION]
>
>Cet exemple implique que vous ayez créé une bibliothèque POI de tous les cafés aux États-Unis. Pour plus d’informations sur la création de POI et de bibliothèques, voir [Création d’un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) et *Création d’une bibliothèque* dans [Gestion de plusieurs bibliothèques](https://experienceleague.adobe.com/docs/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html?lang=fr).

La procédure suivante est un exemple de création d’une règle qui renvoie une publication au Slack lorsque vous entrez dans un café à San Francisco.

L’événement, la condition et l’action sont définis comme suit :

* **Event** : place l’événement d’entrée.
* **Condition** : la ville du **Point ciblé actuel** est San Francisco
* **Action** : envoyez un postback au Slack du nom du café que votre client a entré.

### Prérequis

Avant de créer une règle, vous devez créer un élément de données dans Adobe Experience Platform Launch. Les éléments de données renseignent automatiquement les informations nécessaires sur votre point ciblé dans le message postback.

Pour créer un élément de données dans Experience Platform Launch :

1. Cliquez sur l’onglet **Data Elements** (Éléments de données).
1. Cliquez sur **Ajouter un élément de données**.
1. Saisissez un nom, par exemple, **Nom actuel du café**.
1. Dans la liste déroulante **Extension**, sélectionnez **Places - Beta**.
1. Dans **Élément de données**, sélectionnez **Ville**.
1. Dans le volet de droite, sélectionnez **POI actuel**.
1. Cliquez sur **Enregistrer**.

### Création d’une règle dans Experience Platform Launch pour Places Service

![création d’une règle](/help/assets/placesrule.png)

1. Dans Experience Platform Launch, cliquez sur l’onglet **[!UICONTROL Règles]**.
1. Cliquez sur **[!UICONTROL Ajouter une règle]**.
1. Saisissez un nom pour la règle, par exemple **[!UICONTROL Suivi de l’entrée pour le café dans SF]**.

### Créer un événement

1. Dans la section Événements , cliquez sur **[!UICONTROL + Ajouter]**. Les événements déterminent à quel moment la règle doit se déclencher.
1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Places - Beta]**.
1. Dans la liste déroulante **[!UICONTROL Type d’événement]**, sélectionnez **[!UICONTROL Saisir POI]**.
1. Dans **[!UICONTROL Nom]**, saisissez un nom pour l’événement ; par exemple **[!UICONTROL Entrée dans un café]**.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

### Créer une condition

1. Dans la section Conditions, cliquez sur **[!UICONTROL +Ajouter]**. Les conditions déterminent quels critères doivent être remplis pour que l’action soit entreprise.
1. Dans **[!UICONTROL Type logique]**, sélectionnez Normal afin de permettre aux actions de s’exécuter si la condition est remplie.
1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Places - Beta]**.
1. Dans **[!UICONTROL Type de condition]**, sélectionnez **[!UICONTROL Ville]**.
1. Saisissez un nom de condition, par exemple **[!UICONTROL Café-shop en SF]**.
1. Dans le volet de droite, cliquez sur **[!UICONTROL Point ciblé actuel]**, puis, dans la liste déroulante, sélectionnez **[!UICONTROL San Francisco]** comme étant l’une de vos villes.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

### Créer une action

1. Dans la section **[!UICONTROL Actions]** , cliquez sur **[!UICONTROL + Ajouter]**.
1. Dans la liste déroulante **[!UICONTROL Extension]** , laissez l’option par défaut **[!UICONTROL Mobile Core]** sélectionnée.
1. Sélectionnez un type d’action, par exemple **[!UICONTROL Envoyer le postback]**.

   a. Dans **[!UICONTROL URL]**, saisissez l’URL de postback pour Slack, par exemple `https://hooks.slack.com/services/`.

   b. Pour envoyer un corps de publication, cochez la case **[!UICONTROL Ajouter un corps de Post]** .

   c. Dans **[!UICONTROL Post Body]**, ajoutez le corps de publication, par exemple : `{ "text": "A customer has entered" }`

   c. Saisissez un type de contenu par exemple **[!UICONTROL application/json]**.

   d. Sélectionnez une valeur de délai d’expiration, par exemple **[!UICONTROL 5]**.

1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

### Publish de la règle

1. Pour activer la règle, vous devez la publier. Pour plus d’informations sur la publication de votre règle dans Experience Platform Launch, voir [Publication](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html?lang=fr).

### Penser au-delà des entrées et des sorties

L’utilisation d’entrées et de sorties de géo-barrières du service Places pour déclencher des règles dans Experience Platform Launch est incroyablement puissante, mais vous pouvez également utiliser les données de localisation comme condition pour que d’autres événements se déclenchent. Par exemple, un déclencheur d’événement d’action de suivi principal Mobile peut être prêt à se déclencher en fonction d’un événement d’appel trackAction particulier dans votre application. En fonction de cet événement, vous pouvez placer des conditions d’emplacement supplémentaires dans l’événement avant qu’une action ne soit effectuée. Par exemple, ouvrez une enquête in-app lorsqu’un événement d’achat `trackAction` se produit, mais **uniquement** si l’emplacement actuel de l’utilisateur inclut des métadonnées de service Places spécifiques.

![créer une condition](/help/assets/places-condition.png)
