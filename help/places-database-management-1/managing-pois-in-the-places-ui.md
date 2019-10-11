---
title: Gestion des points d’accès dans l’interface utilisateur Lieux
seo-title: Gestion des points d’accès dans l’interface utilisateur Lieux
description: Utilisez l’interface utilisateur Places pour gérer vos points d’intérêt.
seo-description: Utilisez l’interface utilisateur Places pour gérer vos points d’intérêt.
translation-type: tm+mt
source-git-commit: 01617e4e1658f92234803baf1e57282777d04b13

---


# Gestion des points d’accès dans l’interface utilisateur Lieux

Les points d’accès et les bibliothèques sont créés et gérés dans la base de données Places à l’aide de l’interface utilisateur Places.

## Définition d’un POI de géofence

Les Geofences sont un type d’API et sont définies dans la base de données en fonction des clés suivantes :

| Clés | Description | Obligatoire? |
| :--- | :--- | :--- |
| ID | Identifiant unique attribué à chaque point d’intérêt | Oui |
| Nom | Nom convivial attribué au point d’intérêt | Oui |
| Bibliothèque | Chaque point d’intérêt doit se voir attribuer une bibliothèque pour l’organisation. | Oui |
| Icône | Aide à la visualisation des points d’intérêt | Oui (valeur par défaut affectée) |
| Couleur | Aide à la visualisation des points d’intérêt | Oui (valeur par défaut affectée) |
| Catégorie | Attribuer un cadre commun de catégories communes à tous les points d’intérêt dans toutes les bibliothèques | Non |
| Adresse | Adresse de rue | Non |
| Ville | ville de POI | Non |
| État/Région | état ou région du POI | Non |
| Pays | pays d'origine | Non |
| Latitude | Coordonnée de la latitude pour le centre de la zone d'intérêt | Oui |
| Longitude | Coordonnée de la longitude pour le centre de la zone d’intérêt | Oui |
| Métadonnées | des paires clé + valeur personnalisées qui peuvent être attribuées aux points d’intérêt. Ces métadonnées rationalisent les flux de travaux futurs en vous permettant de regrouper les points d’intérêt entre les bibliothèques pour que chacune d’elles utilise des règles et des filtres dans les flux de travaux en aval, tels que l’envoi d’une notification Push chaque fois qu’une personne entre dans un point d’intérêt avec Type = Concurrent. | Non |

## Créer un POI {#create-a-poi}

Un point d'intérêt (POI) est un emplacement ou un point sur une carte qui vous intéresse. Il peut inclure des cafés, des restaurants, etc.

1. Connectez-vous à Adobe Places avec votre Adobe ID.
2. Dans le coin supérieur droit, cliquez sur l’icône qui ressemble à une liste à puces, puis cliquez sur **[!UICONTROL New]**.
3. Entrez le nom de votre point d’intérêt.
4. Sélectionnez ou ajoutez une bibliothèque.
5. Entrez ou sélectionnez un rayon.

   a. Sélectionnez une icône pour votre point d’accès.
b.b. Sélectionnez une couleur pour l’icône.

6. Expand the **[!UICONTROL Location]** section.

   a. Entrez une adresse.

   b. Tapez la ville.

   c. Tapez le nom de l'état.

   d. Entrez le nom du pays.

   e. Sélectionnez ou entrez une latitude ou une longitude.

   f. Cliquez sur **[!UICONTROL Drop Pin on Map]**.

7. Développez la **[!UICONTROL Metadata]** section et cliquez sur **[!UICONTROL Add Metadata]**.

   a. Tapez le nom de la clé.

   b. Tapez la valeur de clé.

8. Cliquez **[!UICONTROL Confirm]** puis **[!UICONTROL  Save]**.

## Modification d’une API

1. Connectez-vous à Places à l’aide de votre Adobe ID.
1. Connectez-vous au service Adobe Places à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône qui ressemble à une liste à puces.
1. Localisez le point d’accès à modifier.
1. Cliquez sur **[!UICONTROL ...]** puis sélectionnez **[!UICONTROL View Details]**.
1. Mettez à jour les informations, puis cliquez sur **[!UICONTROL Save]**.

## Suppression d’un point d’intérêt

1. Connectez-vous à Places à l’aide de votre Adobe ID.
1. Connectez-vous au service Adobe Places à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône qui ressemble à une liste à puces.
1. Localisez le point d’accès à supprimer.
1. Cliquez sur **[!UICONTROL ...]** puis sélectionnez **[!UICONTROL Delete]**.

## Filtrage des points d’intérêt par ville, état, pays ou métadonnées

1. Connectez-vous au service Adobe Places à l’aide de votre Adobe ID.
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

