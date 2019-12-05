---
title: Définition des éléments de données
description: Cette section fournit des informations sur la création, l’utilisation et la publication d’éléments de données dans le lancement de la plateforme d’expérience pour les emplacements.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Define a data element {#define-data-elements}

Les informations suivantes vous aident à comprendre les éléments de données et comment les créer et les publier.

## A propos des éléments de données

Les éléments de données constituent les blocs de création du dictionnaire de données de l’application et sont utilisés pour collecter, organiser et diffuser des données sur le marketing et la technologie publicitaire.

Un élément de données est une variable dans laquelle la valeur peut être mappée à un identifiant visiteur, un nom d’opérateur, un identifiant de publicité, un identifiant Push, etc. Dans le lancement de la plateforme d’expérience, vous pouvez référencer cette valeur par son nom de variable. Cette collection d’éléments de données devient le dictionnaire des données définies que vous pouvez utiliser pour créer vos règles (événements, conditions et actions). Ce dictionnaire est partagé dans le lancement de la plateforme d’expérience, où il peut être utilisé avec toute extension de votre propriété.

Avec l’extension Places, vous pouvez référencer des valeurs à partir des cibles suivantes :

* Le point d’accès actuel, qui fait référence au point d’accès dans lequel se trouve actuellement votre client.

   Si l’utilisateur est situé dans plusieurs points d’intérêt, celui qui appartient à la bibliothèque avec un rang supérieur est sélectionné. Si plusieurs points d’intérêt appartiennent à la bibliothèque de classement supérieur, celui qui a le plus petit rayon est sélectionné.
* Dernier point d’intérêt de sortie, qui fait référence au point d’intérêt le plus récent que l’utilisateur a quitté.
* Dernier point d’accès saisi, qui fait référence au point d’accès le plus récent saisi par l’utilisateur.

Chaque API contient les références de données suivantes :

* **[!UICONTROL Category]**: catégorie de l'IPE
* **[!UICONTROL City]**: ville de la POI
* **[!UICONTROL Country]**: pays de la période d'enquête
* **[!UICONTROL Latitude]**: latitude du POI
* **[!UICONTROL Longitude]**: longitude de de l'IPE
* **[!UICONTROL Metadata]**: métadonnées personnalisées de l’API
* **[!UICONTROL Name]**: région du POI
* **[!UICONTROL Radius]**: rayon de l’objet ciblé
* **[!UICONTROL Region ID]**: ID du point d’accès
* **[!UICONTROL Region/State]**: région, province ou état de la période d'enquête

### Créer un élément de données

1. Dans la page Propriétés de votre application, cliquez sur l’ **[!UICONTROL Data Elements]** onglet.

1. Cliquez sur **[!UICONTROL Create New Data Element]** (Nouvelle propriété).

1. Dans la liste des extensions installées, recherchez **[!UICONTROL Places]**.

1. Dans la liste **[!UICONTROL Data Element Type]** déroulante, sélectionnez une référence de données pour cet élément de données.

1. Sélectionnez une cible d’API.

1. Si cet élément de données est une référence de métadonnées personnalisée, sélectionnez une clé de métadonnées.

1. Saisissez le nom de l’élément de données, puis cliquez sur **[!UICONTROL Save]**.

   ![Créer un élément de données](/help/assets/create-de-7-v3.png)


## utiliser un élément de données.

Après la création d’un élément de données, si un sélecteur d’élément de données est présent, vous pouvez utiliser l’élément de données de n’importe quel composant de règle.

![Utilisation de l’élément de données](/help/assets/use-de-v2.png)

Si un sélecteur d’éléments de données n’est pas présent dans le composant de règle, vous pouvez utiliser l’élément de données en enveloppant le nom de l’élément de données avec les **[!UICONTROL %%]** jetons.
Par exemple, si le nom de l’élément de données est **[!UICONTROL Last POI City]**, vous pouvez ajouter **[!UICONTROL LAST POI City]** à une entrée de texte.


## Publication des éléments de données

Si des éléments de données sont utilisés dans l’un des composants de règle, ces éléments de données doivent également être inclus dans la bibliothèque et publiés.
