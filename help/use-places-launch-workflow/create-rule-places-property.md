---
title: Création d’une règle pour la propriété Places
seo-title: Création d’une règle pour la propriété Places
description: 'Le SDK Places surveille l’emplacement actuel, surveille les points d’intérêt configurés autour de l’emplacement actuel et suit les événements d’entrée et de sortie pour ces points d’intérêt. '
seo-description: 'Le SDK Places surveille l’emplacement actuel, surveille les points d’intérêt configurés autour de l’emplacement actuel et suit les événements d’entrée et de sortie pour ces points d’intérêt. '
translation-type: tm+mt
source-git-commit: 9feb88f1ccec83c96d08ac5bd48e43d7d9c247c8

---


# Création de règles d’entrée et de sortie {#create-entry-exit-rules}

Une fois les extensions Places et Places Monitor installées dans votre application mobile, vous pouvez créer dans Adobe Experience Platform Launch des règles qui sont des données d’emplacement déclenchées ou conditionnées, y compris les événements d’entrée et de sortie d’emplacement Places.

## Règles

Vous pouvez configurer une règle, composée d’un événement, d’une condition et d’une action. Chaque règle est composée des éléments suivants :

* Un ou plusieurs événements
* (Facultatif) conditions
* Une ou plusieurs actions

### Evénements de lieux

Places offre les événements suivants sur lesquels vous pouvez exécuter une règle :

* **Entrez l’API**, qui est déclenchée par le kit Places SDK lorsque votre client entre dans le PDV que vous avez configuré.
* **Quittez le point d’accès**, qui est déclenché par le SDK Places lorsque votre client quitte le point d’accès que vous avez configuré.

### Conditions de place

Les conditions définissent les critères que les données associées à l’événement, ou l’état partagé d’une extension à cette instance, doivent respecter pour que l’action soit entreprise. Par exemple, vous pouvez définir une condition pour déclencher une action sur l’entrée d’un café dans la ville de San Francisco uniquement.

Le SDK Places conserve les états suivants :

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

* **Evénement**: Place l’événement d’entrée.
* **Condition**: La ville de l'IPE **** actuelle est San Francisco
* **Action**: Envoyez un postback à Slack pour connaître le nom du café que votre client a entré.

### Condition requise

Avant de créer une règle, vous devez créer un élément de données dans Adobe Experience Platform Launch. Les éléments de données renseignent automatiquement les informations nécessaires sur votre point d’intérêt dans le message postback.

Pour créer un élément de données dans Experience Platform Launch :

1. Cliquez sur l’onglet Eléments **de** données.
2. Click **Add Data Element**.
3. Entrez un nom, par exemple, **Current coffee shop name**.
4. Dans la liste déroulante **Extension** , sélectionnez **Places - Bêta**.
5. Dans Elément **** de données, sélectionnez **Ville**.
6. Dans le volet de droite, sélectionnez **Actuel**.
7. Cliquez sur **Enregistrer**.

### Création d’une règle dans le lancement de la plateforme d’expérience pour les emplacements

![création d’une règle](/help/assets/placesrule.png)

1. Dans le lancement de la plateforme d’expérience, cliquez sur l’ **[!UICONTROL Rules]** onglet.
2. Cliquez sur **[!UICONTROL Add Rule]** (Nouvelle propriété).
3. Tapez le nom de la règle, par exemple **[!UICONTROL Track entry for coffee shop in SF]**.

### Créez un événement

1. Dans la section Evénements, cliquez sur **[!UICONTROL + Add]**. Les événements déterminent à quel moment la règle doit se déclencher.
2. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Places – Beta]**.
3. Dans la liste **[!UICONTROL Event Type]** déroulante, sélectionnez **[!UICONTROL Enter POI]**.
4. Dans **[!UICONTROL Name]**, saisissez un nom pour l’événement, par exemple **[!UICONTROL Entering a coffee shop]**.
5. Cliquez sur **[!UICONTROL Keep Changes]** (Conserver les modifications).

### Créer une condition

1. Dans la section Conditions, cliquez sur **[!UICONTROL +Add]**. Les conditions déterminent les critères à respecter pour que l'action soit entreprise.
2. Dans **[!UICONTROL Logic Type]**, sélectionnez Normal, ce qui permet aux actions de s’exécuter si la condition est remplie.
3. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Places – Beta]**.
4. Dans **[!UICONTROL Condition Type]**, sélectionnez **[!UICONTROL City]**.
5. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
6. Dans le volet de droite, cliquez sur **[!UICONTROL Current POI]**, puis dans la liste déroulante, sélectionnez **[!UICONTROL San Francisco]** comme l’une de vos villes.
7. Cliquez sur **[!UICONTROL Keep Changes]** (Conserver les modifications).

### Créer une action

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL + Add]**.
2. Dans la liste **[!UICONTROL Extension]** déroulante, laissez l’ **[!UICONTROL Mobile Core]** option par défaut sélectionnée.
3. Sélectionnez un type d’action, par exemple **[!UICONTROL Send Postback]**.

   a. Dans **[!UICONTROL URL]**, saisissez l’URL de postback pour Slack, par exemple `https://hooks.slack.com/services/`.

   b. Pour envoyer un corps de publication, activez la **[!UICONTROL Add Post Body]** case à cocher.

   c. Dans **[!UICONTROL Post Body]**, ajoutez le corps de la publication, par exemple : `{ "text": "A customer has entered" }`

   c. Entrez un type de contenu, par exemple **[!UICONTROL application/json]**.

   d. Sélectionnez une valeur de délai d’expiration, par exemple **[!UICONTROL 5]**.

4. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).

### Publication de la règle

1. Pour activer la règle, vous devez la publier. Pour plus d’informations sur la publication de votre règle dans le lancement de la plateforme d’expérience, voir [Publication](https://docs.adobelaunch.com/launch-reference/publishing).

### Penser au-delà des entrées et des sorties

L’utilisation des entrées et des sorties de géolocalisation Places pour déclencher des règles dans Lancement est extrêmement puissante, mais vous pouvez également utiliser les données d’emplacement comme condition de déclenchement d’autres événements. Par exemple, vous pouvez avoir un déclencheur d’événement d’action de suivi principal mobile prêt à se déclencher en fonction d’un événement d’appel trackAction particulier dans votre application. En fonction de cet événement, vous pouvez placer des conditions d’emplacement supplémentaires dans l’événement avant qu’une action ne soit exécutée. Par exemple, ouvrez une enquête intégrée lorsqu'un `trackAction` événement d'achat se produit, mais **uniquement** si l'emplacement actuel de l'utilisateur inclut des métadonnées spécifiques du service d'emplacement.

![créer une condition](/help/assets/places-condition.png)