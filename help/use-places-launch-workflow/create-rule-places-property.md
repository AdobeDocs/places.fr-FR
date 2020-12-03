---
title: Création d’une règle pour la propriété Service des emplacements
description: 'Le SDK Places surveille l’emplacement actuel, surveille les points d’intérêt configurés autour de l’emplacement actuel et suit les événements d’entrée et de sortie pour ces points d’intérêt. '
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 7%

---


# Création de règles d’entrée et de sortie {#create-entry-exit-rules}

Avec l&#39;extension Places et les extensions Places Monitor installées dans votre application mobile, vous pouvez créer des règles en Adobe Experience Platform Launch qui sont des données d&#39;emplacement déclenchées ou conditionnées, y compris les événements d&#39;entrée et de sortie d&#39;emplacement.

## Règles

Vous pouvez configurer une règle composée d’un événement, d’une condition et d’une action. Chaque règle est composée des éléments suivants :

* Un ou plusieurs événements
* (Facultatif) conditions
* Une ou plusieurs actions

### Événements du service Places

Place les offres de service sur lesquelles vous pouvez exécuter une règle les événements suivants :

* **Saisissez l’API**, qui est déclenchée par le SDK Places lorsque votre client entre dans l’API que vous avez configuré.
* **Quittez l’API**, qui est déclenché par le SDK Places lorsque votre client quitte l’API que vous avez configuré.

### Conditions du service Places

Les conditions définissent les critères que les données associées au événement, ou l’état partagé d’une extension à cette instance, doivent respecter pour que l’action soit entreprise. Par exemple, vous pouvez définir une condition pour déclencher une action sur une entrée dans un café uniquement dans la ville de San Francisco.

Le SDK Places conserve les états suivants :

* IPE actuelle, qui fait référence à l’IPE dans laquelle se trouve actuellement votre client.
* Dernier point d’intérêt de sortie, qui fait référence au point d’intérêt le plus récent que votre client a quitté.
* Dernier POI saisi, qui fait référence au dernier POI saisi par votre client.

Chaque POI contient les éléments de données suivants :

* Identifiant
* Nom
* Latitude/longitude
* Rayon
* Métadonnées telles que ville, pays, état, catégorie

### Actions

Les actions définissent ce que l’application fera en réponse à la condition que la règle soit satisfaite pour le événement déclenché. Par exemple, lorsque votre client entre dans votre point d’accès, vous pouvez configurer un message de bienvenue pour qu’il s’affiche sur son périphérique mobile.

## Créez une règle : un exemple

>[!CAUTION]
>
>Cet exemple implique que vous ayez créé une bibliothèque POI de tous les cafés aux États-Unis. For more information about creating POIs and libraries, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md) and *Create a Library* in [Manage multiple libraries](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

La procédure suivante est un exemple de création d’une règle qui renvoie une publication au Slack lorsque vous entrez dans un café de San Francisco.

Le événement, la condition et l’action sont définis comme suit :

* **Événement**: Place le événement d&#39;entrée.
* **Condition** : la ville du **Point ciblé actuel** est San Francisco
* **Action**: Envoyez un postback au Slack le nom du café que votre client a entré.

### Condition requise

Avant de créer une règle, vous devez créer un élément de données dans Adobe Experience Platform Launch. Les éléments de données renseignent automatiquement les informations nécessaires sur votre point d’intérêt dans le message postback.

Pour créer un élément de données dans l’Experience Platform Launch :

1. Cliquez sur l’onglet Eléments **de** données.
1. Click **Add Data Element**.
1. Entrez un nom, par exemple, **Current coffee shop name**.
1. In the **Extension** drop-down list, select **Places – Beta**.
1. Dans **Élément de données**, sélectionnez **Ville**.
1. Dans le volet de droite, sélectionnez **Actuelle API**.
1. Cliquez sur **Enregistrer**.

### Création d’une règle dans l’Experience Platform Launch pour le service Lieux

![création d’une règle](/help/assets/placesrule.png)

1. In Experience Platform Launch, click the **[!UICONTROL Rules]** tab.
1. Cliquez sur **[!UICONTROL Add Rule]**.
1. Tapez le nom de la règle, par exemple **[!UICONTROL Track entry for coffee shop in SF]**.

### Créez un événement

1. In the Events section, click **[!UICONTROL + Add]**. Les événements déterminent à quel moment la règle doit se déclencher.
1. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Places – Beta]**.
1. Dans la liste **[!UICONTROL Event Type]** déroulante, sélectionnez **[!UICONTROL Enter POI]**.
1. Dans **[!UICONTROL Name]**, saisissez un nom pour le événement, par exemple **[!UICONTROL Entering a coffee shop]**.
1. Cliquez sur **[!UICONTROL Keep Changes]**.

### Créer une condition

1. Dans la section Conditions, cliquez sur **[!UICONTROL +Add]**. Les conditions déterminent quels critères doivent être respectés pour que l&#39;action soit entreprise.
1. In **[!UICONTROL Logic Type]**, select Regular, which allows actions to execute if the condition is met.
1. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Places – Beta]**.
1. In **[!UICONTROL Condition Type]**, select **[!UICONTROL City]**.
1. Entrez un nom de condition, par exemple **[!UICONTROL Coffee shop in SF]**.
1. In the right pane, click **[!UICONTROL Current POI]**, and in the drop-down list, select **[!UICONTROL San Francisco]** as one of your cities.
1. Cliquez sur **[!UICONTROL Keep Changes]**.

### Créer une action

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL + Add]**.
1. Dans la liste **[!UICONTROL Extension]** déroulante, laissez l’ **[!UICONTROL Mobile Core]** option par défaut sélectionnée.
1. Sélectionnez un type d’action, par exemple **[!UICONTROL Send Postback]**.

   a. Dans **[!UICONTROL URL]**, saisissez l’URL de postback pour le Slack, par exemple `https://hooks.slack.com/services/`.

   b. Pour envoyer un corps de publication, cochez la **[!UICONTROL Add Post Body]** case.

   c. Dans **[!UICONTROL Post Body]** la section, ajoutez le corps de la poste, par exemple : `{ "text": "A customer has entered" }`

   c. Entrez un type de contenu, par exemple **[!UICONTROL application/json]**.

   d. Sélectionnez une valeur de délai d’expiration, par exemple **[!UICONTROL 5]**.

1. Cliquez sur **[!UICONTROL Keep Changes]**.

### Publier la règle

1. Pour activer la règle, vous devez la publier. Pour plus d’informations sur la publication de votre règle dans l’Experience Platform Launch, voir [Publication](https://docs.adobe.com/content/help/fr-FR/launch/using/reference/publish/overview.html).

### Penser au-delà des entrées et des sorties

L&#39;utilisation d&#39;entrées et de sorties de géolocalisation du service Places pour déclencher des règles dans l&#39;Experience Platform Launch est incroyablement puissante, mais vous pouvez également utiliser les données d&#39;emplacement comme condition pour que d&#39;autres événements puissent se déclencher. Par exemple, vous pouvez avoir un déclencheur Mobile Core Track Action événement prêt à se déclencher en fonction d’un événement d’appel trackAction particulier dans votre application. En fonction de ce événement, vous pouvez placer des conditions d’emplacement supplémentaires dans le événement avant qu’une action ne soit exécutée. Par exemple, ouvrez un questionnaire intégré à l’application lorsqu’un `trackAction` événement d’achat se produit, mais **** uniquement si l’emplacement actuel de l’utilisateur inclut des métadonnées spécifiques du service Lieux.

![créer une condition](/help/assets/places-condition.png)