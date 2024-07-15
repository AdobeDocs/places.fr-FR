---
title: Gestion des points ciblés existants
description: Dans l’interface utilisateur du service Places, vous pouvez modifier, supprimer ou filtrer les points ciblés existants.
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 6%

---

# Gestion des points ciblés existants {#managing-existing-pois}

Les points ciblés et les bibliothèques sont créés et gérés dans la base de données Places à l’aide de l’interface utilisateur de Places.

## Modification d’un point ciblé

1. Connectez-vous à Places à l’aide de votre Adobe ID.
1. Connectez-vous au service Places à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône qui ressemble à une liste à puces.
1. Recherchez le point ciblé que vous souhaitez modifier.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Afficher les détails]**.
1. Mettez à jour les informations et cliquez sur **[!UICONTROL Enregistrer]**.

## Suppression d’un point ciblé

1. Connectez-vous à Places à l’aide de votre Adobe ID.
1. Connectez-vous au service Places à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône qui ressemble à une liste à puces.
1. Recherchez le point ciblé que vous souhaitez supprimer.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Supprimer]**.

## Filtrage des points ciblés par ville, état, pays ou métadonnées

![filtrer un point ciblé](/help/assets/filter_poi.png)

1. Connectez-vous à l’interface utilisateur du service Places à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône de filtrage.
1. Vous pouvez filtrer les points ciblés de l’une des façons suivantes :

   * Par bibliothèque :

     a. Sélectionnez une bibliothèque.

   * Par propriété :

     a. Dans la liste déroulante Propriété, sélectionnez **[!UICONTROL Country]**, **[!UICONTROL State]** ou **[!UICONTROL City]**.

     b. Dans la ligne suivante, saisissez une valeur.

     Par exemple, vous pouvez sélectionner **[!UICONTROL State]** et saisir **[!UICONTROL California]**.

   * Avec les métadonnées :

     a. Saisissez une clé et une valeur.

## Définition d’un point ciblé de géo-barrière

Les clôtures virtuelles sont un type de point ciblé et sont définies dans la base de données à l’aide des clés suivantes :

| Clés | Description | Obligatoire ? |
| :--- | :--- | :--- |
| Identifiant | Identifiant unique attribué à chaque point ciblé | Oui |
| Nom | Nom convivial donné au point ciblé. | Oui |
| Bibliothèque | Chaque point ciblé doit se voir attribuer une bibliothèque pour l’organisation. | Oui |
| Rayon | Rayon de votre point ciblé en mètres. | Oui |
| Icône | Aide à la visualisation des points ciblés. | Oui (valeur par défaut affectée) |
| Couleur | Aide à la visualisation des points ciblés. | Oui (valeur par défaut affectée) |
| Catégorie | Attribuez une structure commune de catégories communes à tous les points ciblés dans toutes les bibliothèques. | Non |
| Adresse | Adresse postale. | Non |
| Ville | Ville du point ciblé. | Non |
| État/région | État ou région du point ciblé. | Non |
| Pays | Pays du point ciblé. | Non |
| Latitude | Coordonnée de la latitude pour le centre du point ciblé. | Oui |
| Longitude | Coordonnée de longitude pour le centre du point ciblé. | Oui |
| Métadonnées | Paires clé et valeur personnalisées qui peuvent être affectées aux points ciblés. Ces métadonnées simplifient les workflows futurs en vous permettant de regrouper les points ciblés entre les bibliothèques pour que chacun utilise des règles et des filtres dans les workflows en aval, comme envoyer une notification push lorsqu’une personne entre dans un point ciblé avec le type = concurrent. | Non |
