---
title: Définition des éléments de données
description: Cette section fournit des informations sur la création, l’utilisation et la publication d’éléments de données dans Experience Platform Launch for Places.
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---


# Définir un élément de données {#define-data-elements}

Les informations suivantes vous aident à comprendre les éléments de données et comment les créer et les publier.

## A propos des éléments de données

Les éléments de données constituent les blocs de construction du dictionnaire de données de l’application et sont utilisés pour collecter, organiser et diffuser des données sur le marketing et la technologie publicitaire.

Un élément de données est une variable dans laquelle la valeur peut être mappée à un ID de Visiteur, un nom d’opérateur, un identifiant de publicité, un identifiant Push, etc. Dans l’Experience Platform Launch, vous pouvez référencer cette valeur par son nom de variable. Cette collection d’éléments de données devient le dictionnaire de données définies que vous pouvez utiliser pour créer vos règles (événements, conditions et actions), et ce dictionnaire est partagé entre les Experience Platform Launch où il peut être utilisé avec toute extension de votre propriété.

L’extension Places vous permet de référencer des valeurs à partir des cibles suivantes :

* IPE actuelle, qui fait référence à l’IPE dans laquelle se trouve actuellement votre client.

   Si l’utilisateur se trouve dans plusieurs points d’intérêt, celui qui appartient à la bibliothèque dont le classement est le plus élevé est sélectionné. Si plusieurs points d’intérêt appartiennent à la bibliothèque de classement supérieur, celui qui présente le plus petit rayon est sélectionné.
* Dernier point d’intérêt de sortie, qui fait référence au point d’intérêt le plus récent que l’utilisateur a quitté.
* Dernier point d’intérêt saisi, qui fait référence au point d’intérêt le plus récent saisi par l’utilisateur.

Chaque point d’intérêt contient les références de données suivantes :

* **[!UICONTROL Catégorie]** : catégorie du POI
* **[!UICONTROL Ville]** : ville du POI
* **[!UICONTROL Pays]** : pays de la période d&#39;enquête
* **[!UICONTROL Latitude]** : latitude du POI
* **[!UICONTROL Longitude]** : longitude de l’IPE
* **[!UICONTROL Métadonnées]** : métadonnées personnalisées de l’API
* **[!UICONTROL Nom]** : nom de l’API
* **[!UICONTROL Rayon]** : rayon du POI
* **[!UICONTROL ID]** de région : ID de l’API
* **[!UICONTROL Région/État]** : région, province ou état de l&#39;IPE

### Créer un élément de données

1. Dans la page Propriété de votre application, cliquez sur l’onglet **[!UICONTROL Éléments de données]**.

1. Cliquez sur **[!UICONTROL Créer un élément de données]**.

1. Dans la liste des extensions installées, recherchez **[!UICONTROL Places]**.

1. Dans la liste déroulante **[!UICONTROL Type d’élément de données]**, sélectionnez une référence de données pour cet élément de données.

1. Sélectionnez une cible d’API.

1. Si cet élément de données est une référence de métadonnées personnalisée, sélectionnez une clé de métadonnées.

1. Saisissez le nom de l’élément de données, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![Créer un élément de données](/help/assets/create-de-7-v3.png)


## Utilisation d’un élément de données

Après la création d’un élément de données, si un sélecteur d’élément de données est présent, vous pouvez utiliser l’élément de données à partir de n’importe quel composant de règle.

![Utilisation de l’élément de données](/help/assets/use-de-v2.png)

Si un sélecteur d’éléments de données n’est pas présent dans le composant de règle, vous pouvez utiliser l’élément de données en enveloppant le nom de l’élément de données avec les jetons **[!UICONTROL %]**.
Par exemple, si le nom de l’élément de données est **[!UICONTROL Dernière ville d’intérêt public]**, vous pouvez ajouter **[!UICONTROL DERNIÈRE ville d’intérêt public]** à une entrée de texte.


## Publication des éléments de données

Si des éléments de données sont utilisés dans l’un des composants de règle, ces éléments de données doivent également être inclus dans la bibliothèque et publiés.
