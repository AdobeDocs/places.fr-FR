---
title: Définition des éléments de données
description: Cette section fournit des informations sur la création, l’utilisation et la publication d’éléments de données dans Experience Platform Launch pour Places.
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
TQID: https://experienceleague.adobe.com/NQ83uUZJtNglAcxD6HNl4Gw1Y8-0-uqfu-hH8H0EITg
product_v2:
  - id: a829a185-511f-4bf8-8dcf-9e684f8011cf
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
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
source-wordcount: 486
ht-degree: 1%

---

# Définition d’un élément de données {#define-data-elements}

Les informations suivantes vous aident à comprendre les éléments de données et comment les créer et les publier.

## À propos des éléments de données

Les éléments de données sont les blocs de création du dictionnaire de données de l’application et sont utilisés pour collecter, organiser et diffuser des données dans les technologies marketing et publicitaires.

Un élément de données est une variable où la valeur peut être mappée à un identifiant visiteur, un nom d’opérateur, un Advertising ID, un Push ID, etc. Dans Experience Platform Launch, vous pouvez référencer cette valeur par son nom de variable. Cette collection d’éléments de données devient le dictionnaire des données définies que vous pouvez utiliser pour créer vos règles (événements, conditions et actions). Ce dictionnaire est partagé dans Experience Platform Launch, où il peut être utilisé avec n’importe quelle extension de votre propriété.

Avec l’extension Places , vous pouvez référencer des valeurs à partir des cibles suivantes :

* Point d’intérêt actuel, qui fait référence au point d’intérêt dans lequel votre client se trouve actuellement.

  Si l’utilisateur se trouve dans plusieurs points d’intérêt, celui qui appartient à la bibliothèque de rang supérieur est sélectionné. Si plusieurs points d’intérêt appartiennent à la bibliothèque de rang le plus élevé, celui dont le rayon est le plus petit est sélectionné.
* Dernier point ciblé quitté, qui fait référence au dernier point ciblé quitté par l’utilisateur.
* Dernier POI saisi, qui fait référence au dernier POI saisi par l’utilisateur.

Chaque point d’intérêt contient les références de données suivantes :

* **[!UICONTROL Catégorie]** : catégorie du point d’intérêt
* **[!UICONTROL Ville]** : ville du point d’intérêt
* **[!UICONTROL Pays]** : pays de l’IPE
* **[!UICONTROL Latitude]** : latitude du point d’intérêt
* **[!UICONTROL Longitude]** : longitude du point d’intérêt
* **[!UICONTROL Métadonnées]** : métadonnées personnalisées du point d’intérêt
* **[!UICONTROL Nom]** : nom du point d’intérêt
* **[!UICONTROL Rayon]** : rayon du point d’intérêt
* **[!UICONTROL ID de région]** : ID du point d’intérêt
* **[!UICONTROL Région/État]** : région, province ou État de la PI

### Créer un élément de données

1. Dans la page de propriétés de votre application, cliquez sur l’onglet **[!UICONTROL Éléments de données]**.

1. Cliquez sur **[!UICONTROL Créer un élément de données]**.

1. Dans la liste des extensions installées, trouvez **[!UICONTROL Places]**.

1. Dans la liste déroulante **[!UICONTROL Type d’élément de données]**, sélectionnez une référence de données pour cet élément de données.

1. Sélectionnez une cible de point d’intérêt.

1. Si cet élément de données est une référence de métadonnées personnalisée, sélectionnez une clé de métadonnées.

1. Saisissez le nom de l’élément de données, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![Créer un élément de données](/help/assets/create-de-7-v3.png)


## Utiliser un élément de données

Après la création d’un élément de données, si un sélecteur d’éléments de données est présent, vous pouvez utiliser l’élément de données de n’importe quel composant de règle.

![Utiliser l’élément de données](/help/assets/use-de-v2.png)

Si un sélecteur d’éléments de données n’est pas présent dans le composant de règle, vous pouvez utiliser l’élément de données en encapsulant le nom de l’élément de données avec les jetons **[!UICONTROL %%]**.
Par exemple, si le nom de l’élément de données est **[!UICONTROL Ville du dernier point d’intérêt]**, vous pouvez ajouter **[!UICONTROL Ville du dernier point d’intérêt]** à une entrée de texte.


## Publication des éléments de données

Si des éléments de données sont utilisés dans l’un des composants de règle, ces éléments de données doivent également être inclus dans la bibliothèque et publiés.
