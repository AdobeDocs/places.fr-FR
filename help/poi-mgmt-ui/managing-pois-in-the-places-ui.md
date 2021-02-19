---
title: Gérer les points d’intérêt existants
description: Dans l’interface utilisateur du service Lieux, vous pouvez modifier, supprimer ou filtrer les points d’accès existants.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 7%

---


# Gérer les points d’intérêt existants {#managing-existing-pois}

Les points d’accès et les bibliothèques sont créés et gérés dans la base de données Places à l’aide de l’interface utilisateur Places.

## Modification d’un point d’intérêt

1. Connectez-vous à Places à l’aide de votre Adobe ID.
1. Connectez-vous au service Places à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône qui ressemble à une liste à puces.
1. Localisez le point d’accès à Internet que vous souhaitez modifier.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Détails de la Vue]**.
1. Mettez à jour les informations et cliquez sur **[!UICONTROL Enregistrer]**.

## Suppression d’un point d’intérêt

1. Connectez-vous à Places à l’aide de votre Adobe ID.
1. Connectez-vous au service Places à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône qui ressemble à une liste à puces.
1. Localisez le point d’accès à Internet que vous souhaitez supprimer.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Supprimer]**.

## Filtrage des points d’intérêt par ville, état, pays ou métadonnées

![filtrage d’un point d’accès](/help/assets/filter_poi.png)

1. Connectez-vous à l’interface utilisateur du service Lieux à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône de filtrage.
1. Vous pouvez filtrer les points d’intérêt de l’une des manières suivantes :

   * Par bibliothèque :

      a. Sélectionnez une bibliothèque.

   * Par propriété :

      a. Dans la liste déroulante Propriété, sélectionnez **[!UICONTROL Pays]**, **[!UICONTROL Etat]** ou **[!UICONTROL Ville]**.

      b. Dans la ligne suivante, entrez une valeur.

      Par exemple, vous pouvez sélectionner **[!UICONTROL Etat]** et taper **[!UICONTROL Californie]**.

   * Avec métadonnées :

      a. Saisissez une clé et une valeur.

## Définition d’une POI de géofence

Les Geofences sont un type d’IPE et sont définies dans la base de données en fonction des clés suivantes :

| Keys | Description | Obligatoire? |
| :--- | :--- | :--- |
| Identifiant | Identificateur unique attribué à chaque point d’intérêt | Oui |
| Nom | Nom convivial attribué à l’objet de l’enquête. | Oui |
| Bibliothèque | Chaque point d’accès doit se voir attribuer une bibliothèque pour l’organisation. | Oui |
| Rayon | Rayon de votre point d’intérêt en mètres. | Oui |
| Icône | Aide à la visualisation des points d’intérêt. | Oui (valeur par défaut affectée) |
| Couleur | Aide à la visualisation des points d’intérêt. | Oui (valeur par défaut affectée) |
| Catégorie | Attribuez un cadre commun de catégories communes à tous les points d’intérêt dans toutes les bibliothèques. | Non |
| Adresse | Adresse postale. | Non |
| Ville | Ville de l&#39;IPE. | Non |
| Etat/région | État ou région de l’IPE. | Non |
| Pays | Pays de la période d’enquête. | Non |
| Latitude | Coordonnée de la latitude pour le centre de l&#39;interface utilisateur. | Oui |
| Longitude | Coordonnée de la longitude pour le centre de l’objet ciblé. | Oui |
| Métadonnées | Des paires clé/valeur personnalisées qui peuvent être attribuées aux points d’intérêt. Ces métadonnées simplifient les futurs workflows en vous permettant de regrouper les points d’intérêt entre les bibliothèques pour que chacune d’elles utilise des règles et des filtres dans les workflows en aval, tels que l’envoi d’une notification Push lorsqu’une personne entre dans un point d’intérêt avec le Concurrent Type =. | Non |
