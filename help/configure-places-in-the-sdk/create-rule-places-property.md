---
title: Création d’une règle pour la propriété Places
seo-title: Création d’une règle pour la propriété Places
description: 'Le SDK Places surveille l’emplacement actuel, surveille les points d’intérêt configurés autour de l’emplacement actuel et suit les événements d’entrée et de sortie pour ces points d’intérêt. '
seo-description: 'Le SDK Places surveille l’emplacement actuel, surveille les points d’intérêt configurés autour de l’emplacement actuel et suit les événements d’entrée et de sortie pour ces points d’intérêt. '
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Création d’une règle pour la propriété Places {#creating-rule-places-property}

Le SDK du service d’emplacement effectue le suivi de l’emplacement actuel, surveille les points d’intérêt configurés autour de l’emplacement actuel et suit les événements d’entrée et de sortie pour ces points d’intérêt.

## Règles

Vous pouvez configurer une règle, composée d’un événement, d’une condition et d’une action. Chaque règle est composée des éléments suivants :

* Un ou plusieurs événements
* (Facultatif) conditions
* Une ou plusieurs actions

### Events (Événements)

Places offre les événements suivants sur lesquels vous pouvez exécuter une règle :

* **[!UICONTROL Enter POI]**, qui est déclenché par le SDK Places lorsque votre client entre dans le point d’accès que vous avez configuré.
* **[!UICONTROL Exit POI]**, qui est déclenché par le SDK Places lorsque votre client quitte le point d’accès que vous avez configuré.

### Conditions

Les conditions définissent les critères que les données associées à l’événement, ou l’état partagé d’une extension à cette instance, doivent respecter pour que l’action soit entreprise. Par exemple, vous pouvez définir une condition pour déclencher une action sur l’entrée d’un café dans la ville de San Francisco uniquement.

Le SDK du service d’emplacement conserve les états suivants :

* Le point d’accès actuel, qui fait référence au point d’accès dans lequel se trouve actuellement votre client.
* Dernier point d’intérêt de sortie, qui fait référence au point d’intérêt le plus récent que votre client a quitté.
* Dernier point d’intérêt saisi, qui fait référence au point d’intérêt le plus récent saisi par votre client.

Chaque API contient les éléments de données suivants :

* ID
* Nom:
* Latitude/longitude
* Rayon
* Métadonnées telles que ville, pays, état, catégorie

### Actions

Les actions définissent ce que l’application fera en réponse à la condition que la règle soit satisfaite pour l’événement déclenché. Par exemple, lorsque votre client entre dans votre point d’accès, vous pouvez configurer un message de bienvenue pour qu’il s’affiche sur son périphérique mobile.

## Créez une règle : un exemple

>[!CAUTION]
>
>Cet exemple suppose que vous avez créé une bibliothèque d’API de tous les cafés des États-Unis. Pour plus d’informations sur la création de points d’intérêt et de bibliothèques, voir [Création d’un point d’intérêt](https://placesdocs.com/places-services-by-adobe-documentation/places-database-management-1/managing-pois-in-the-places-ui#create-a-poi) et [Création d’une bibliothèque](https://placesdocs.com/places-services-by-adobe-documentation/places-database-management-1/manage-libraries#create-a-library).

La procédure suivante est un exemple de création d’une règle qui renvoie une publication à Slack lorsque vous entrez dans un café à San Francisco.

L’événement, la condition et l’action sont définis comme suit :

* **Evénement**: Événement d’entrée du service d’emplacement.
* **Condition**: La ville de l'IPE **** actuelle est San Francisco
* **Action**: Envoyez un postback à Slack pour connaître le nom du café que votre client a entré.

### Condition requise

Avant de créer une règle, vous devez créer un élément de données dans le lancement de la plateforme d’expérience. Les éléments de données renseignent automatiquement les informations nécessaires sur votre point d’intérêt dans le message postback.

Pour créer un élément de données dans Experience Platform Launch :

1. Click the **[!UICONTROL Data Elements]** tab.
2. Cliquez sur **[!UICONTROL Add Data Element]** (Nouvelle propriété).
3. Type a name, for example, **[!UICONTROL Current coffee shop name]**.
4. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Places – Beta]**.
5. Dans **[!UICONTROL Data Element]**, sélectionnez **[!UICONTROL City]**.
6. Dans le volet de droite, sélectionnez **Actuel**.
7. Cliquez sur **[!UICONTROL Save]** (Nouvelle propriété).

### Création d’une règle dans Experience Platform Launch pour le service d’emplacement

![](//help/assets/create-a-rule.png)

1. Dans le lancement de la plateforme d’expérience, cliquez sur l’ **[!UICONTROL Rules]** onglet.
2. Cliquez sur **Ajouter une règle**.
3. Entrez le nom de la règle, par exemple, **Suivi de l'entrée pour le café en SF**.

### Créez un événement

1. Dans la section Evénements, cliquez sur **[!UICONTROL + Add]**. Les événements déterminent à quel moment la règle doit se déclencher.
2. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Places – Beta]**.
3. Dans la liste **[!UICONTROL Event Type]** déroulante, sélectionnez **[!UICONTROL Enter POI]**.
4. Dans **[!UICONTROL Name]**, saisissez un nom pour l’événement, par exemple **[!UICONTROL Entering a coffee shop]**.
5. Cliquez sur **[!UICONTROL Keep Changes]** (Conserver les modifications).

### Créer une condition

1. Dans la section Conditions, cliquez sur **[!UICONTROL +Add]**. Les conditions déterminent les critères à respecter pour que l'action soit entreprise.
2. Dans **[!UICONTROL Logic Type]**, sélectionnez Normal, ce qui permet aux actions de s’exécuter si la condition est remplie.
3. Dans la liste déroulante **Extension** , sélectionnez **[!UICONTROL Places – Beta]**.
4. Dans **[!UICONTROL Condition Type]**, sélectionnez **[!UICONTROL City]**.
5. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
6. Dans le volet de droite, cliquez sur **[!UICONTROL Current POI]**, puis dans la liste déroulante, sélectionnez **[!UICONTROL San Francisco]** comme l’une de vos villes.
7. Cliquez sur **[!UICONTROL Keep Changes]** (Conserver les modifications).

### Créer une action

1. Dans la **[!UICONTROL Actions]** section, cliquez sur **[!UICONTRO+ Ajouter]**.
2. Dans la liste déroulante **[!UICONTRO Extension]** , laissez l’option par défaut **[!UICONTRO Mobile Core]** sélectionnée.
3. Sélectionnez un type d’action, par exemple **[!UICONTRO Envoyer un postback]**.

   a. Dans **[!UICONTROL URL]**, saisissez l’URL de postback pour Slack, par exemple `https://hooks.slack.com/services/`.

   b. Pour envoyer un corps de publication, cochez la case **[!UICONTRO Ajouter un corps]** de publication.

   c. Dans Corps **[!UICONTRO de la]** publication, ajoutez le corps de la publication, par exemple : `{ "text": "A customer has entered" }`

   c. Entrez un type de contenu par exemple **[!UICONTRO application/json]**.

   d. Sélectionnez une valeur de délai d’expiration, par exemple **5**.

4. Click **[!UICONTRO Keep Changes]**.

### Publication de la règle

1. Pour activer la règle, vous devez la publier. Pour plus d’informations sur la publication de votre règle dans le lancement de la plateforme d’expérience, voir [Publication](https://docs.adobelaunch.com/launch-reference/publishing).