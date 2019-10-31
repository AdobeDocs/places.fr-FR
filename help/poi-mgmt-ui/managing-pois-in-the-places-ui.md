---
title: Gestion des points d’intérêt existants
seo-title: Gestion des points d’intérêt existants
description: Dans l’interface utilisateur du service d’emplacement, vous pouvez modifier, supprimer ou filtrer les points d’intérêt existants.
seo-description: Dans l’interface utilisateur du service d’emplacement, vous pouvez modifier, supprimer ou filtrer les points d’intérêt existants.
translation-type: tm+mt
source-git-commit: 32c670773421406591ba85a628760553ce6ad840

---


# Gestion des points d’intérêt existants

Les points d’accès et les bibliothèques sont créés et gérés dans la base de données Places à l’aide de l’interface utilisateur Places.

## Modification d’une API

1. Connectez-vous à Places à l’aide de votre Adobe ID.
1. Connectez-vous au service Places à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône qui ressemble à une liste à puces.
1. Localisez le point d’accès à modifier.
1. Cliquez sur **[!UICONTROL ...]** puis sélectionnez **[!UICONTROL View Details]**.
1. Mettez à jour les informations, puis cliquez sur **[!UICONTROL Save]**.

## Suppression d’un point d’intérêt

1. Connectez-vous à Places à l’aide de votre Adobe ID.
1. Connectez-vous au service Places à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône qui ressemble à une liste à puces.
1. Localisez le point d’accès à supprimer.
1. Cliquez sur **[!UICONTROL ...]** puis sélectionnez **[!UICONTROL Delete]**.

## Filtrage des points d’intérêt par ville, état, pays ou métadonnées

![filtrage d’une API](/help/assets/filter_poi.png)

1. Connectez-vous à l’interface utilisateur du service d’emplacement à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône de filtrage.
1. Vous pouvez filtrer les points d’intérêt de l’une des manières suivantes :

   * Par bibliothèque :

      a. Sélectionnez une bibliothèque.

   * Par propriété :

      a. Dans la liste déroulante Propriété, sélectionnez **[!UICONTROL Country]**, **[!UICONTROL State]** ou **[!UICONTROL City]**.

      b. Dans la ligne suivante, entrez une valeur.

      Par exemple, vous pouvez sélectionner **[!UICONTROL State]** et saisir **[!UICONTROL California]**.

   * Avec métadonnées :

      a. Entrez une clé et une valeur.

## Définition d’un POI de géofence

Les Geofences sont un type d’API et sont définies dans la base de données en fonction des clés suivantes :

| Clés | Description | Obligatoire? |
| :--- | :--- | :--- |
| ID | Identifiant unique attribué à chaque point d’intérêt | Oui |
| Nom | Nom convivial donné à la POI. | Oui |
| Bibliothèque | Chaque point d’intérêt doit se voir attribuer une bibliothèque pour l’organisation. | Oui |
| Icône | Aide à la visualisation des points d’intérêt. | Oui (valeur par défaut affectée) |
| Couleur | Aide à la visualisation des points d’intérêt. | Oui (valeur par défaut affectée) |
| Catégorie | Attribuez un cadre commun aux catégories communes à tous les points d’intérêt dans toutes les bibliothèques. | Non |
| Adresse | Adresse. | Non |
| Ville | Ville de la POI. | Non |
| État/Région | État ou région de l'IPE. | Non |
| Pays | Pays de la zone d'intérêt. | Non |
| Latitude | Coordonnée de la latitude pour le centre du point d’intérêt. | Oui |
| Longitude | Coordonnée de la longitude pour le centre du point d’intérêt. | Oui |
| Métadonnées | Des paires clé/valeur personnalisées qui peuvent être attribuées aux points d’intérêt. Ces métadonnées rationalisent les flux de travaux futurs en vous permettant de regrouper les points d’intérêt entre les bibliothèques pour que chacune d’elles utilise des règles et des filtres dans les flux de travaux en aval, tels que l’envoi d’une notification Push lorsqu’une personne entre dans un point d’intérêt avec le paramètre Type = Concurrent. | Non |
