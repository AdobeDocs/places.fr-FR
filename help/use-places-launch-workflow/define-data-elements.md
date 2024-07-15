---
title: Définition des éléments de données
description: Cette section fournit des informations sur la création, l’utilisation et la publication d’éléments de données dans Experience Platform Launch for Places.
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---

# Définition d’un élément de données {#define-data-elements}

Les informations suivantes vous aident à comprendre les éléments de données, ainsi que la manière de les créer et de les publier.

## À propos des éléments de données

Les éléments de données sont les blocs de création du dictionnaire de données de l’application. Ils sont utilisés pour collecter, organiser et diffuser des données dans les technologies marketing et publicitaire.

Un élément de données est une variable où la valeur peut être mappée à un identifiant visiteur, un nom d’opérateur, un identifiant Advertising, un identifiant push, etc. Dans Experience Platform Launch, vous pouvez référencer cette valeur par son nom de variable. Cette collection d’éléments de données devient le dictionnaire des données définies que vous pouvez utiliser pour créer vos règles (événements, conditions et actions). Ce dictionnaire est partagé sur l’ensemble de l’Experience Platform Launch où il peut être utilisé avec toute extension de votre propriété.

Avec l&#39;extension Places, vous pouvez référencer des valeurs à partir des cibles suivantes :

* Point ciblé actuel, qui fait référence au point ciblé où se trouve actuellement votre client.

  Si l’utilisateur se trouve dans plusieurs points ciblés, celui qui appartient à la bibliothèque dont le rang est le plus élevé est sélectionné. Si plusieurs points ciblés appartiennent à la bibliothèque dont le rang est le plus élevé, celui dont le rayon est le plus petit est sélectionné.
* Dernier point ciblé de sortie, qui fait référence au point ciblé le plus récent que l’utilisateur a quitté.
* Dernier point ciblé saisi, qui fait référence au dernier point ciblé saisi par l’utilisateur.

Chaque point ciblé contient les références de données suivantes :

* **[!UICONTROL Catégorie]** : catégorie du point ciblé
* **[!UICONTROL Ville]** : ville du point ciblé
* **[!UICONTROL Country]** : pays du POI
* **[!UICONTROL Latitude]** : latitude du point ciblé
* **[!UICONTROL Longitude]** : longitude du point ciblé
* **[!UICONTROL Métadonnées]** : métadonnées personnalisées du point ciblé
* **[!UICONTROL Nom]** : nom du point ciblé
* **[!UICONTROL Rayon]** : rayon du point ciblé
* **[!UICONTROL Identifiant de région]** : identifiant du point ciblé
* **[!UICONTROL Région/état]** : région, province ou état du POI

### Créer un élément de données

1. Sur la page Propriété de votre application, cliquez sur l’onglet **[!UICONTROL Data Elements]** .

1. Cliquez sur **[!UICONTROL Créer un élément de données]**.

1. Dans la liste des extensions installées, recherchez **[!UICONTROL Places]**.

1. Dans la liste déroulante **[!UICONTROL Type d’élément de données]**, sélectionnez une référence de données pour cet élément de données.

1. Sélectionnez une cible de point ciblé.

1. Si cet élément de données est une référence de métadonnées personnalisée, sélectionnez une clé de métadonnées.

1. Saisissez un nom pour l’élément de données et cliquez sur **[!UICONTROL Enregistrer]**.

   ![Créer un élément de données](/help/assets/create-de-7-v3.png)


## Utilisation d’un élément de données

Après la création d’un élément de données, si un sélecteur d’élément de données est présent, vous pouvez utiliser l’élément de données de n’importe quel composant de règle.

![Utiliser l’élément de données](/help/assets/use-de-v2.png)

Si un sélecteur d’élément de données n’est pas présent dans le composant de règle, vous pouvez utiliser l’élément de données en encapsulant le nom de l’élément de données avec les jetons **[!UICONTROL %]**.
Par exemple, si le nom de l’élément de données est **[!UICONTROL Last POI City]**, vous pouvez ajouter **[!UICONTROL LAST POI City]** à une entrée de texte.


## Éléments de données Publish

Si des éléments de données sont utilisés dans l’un des composants de règle, ces éléments de données doivent également être inclus dans la bibliothèque et publiés.
