---
title: Gérer les points d’intérêt existants
description: Dans l’interface utilisateur de Places Service, vous pouvez modifier, supprimer ou filtrer des points d’intérêt existants.
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
TQID: https://experienceleague.adobe.com/2VnBQ5-flpx5cyeK3n5b3AOKqnt7RVkdqFBXYa9O5Ys
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 408
ht-degree: 6%

---

# Gérer les points d’intérêt existants {#managing-existing-pois}

Les POI et les bibliothèques sont créés et gérés dans la base de données Places à l&#39;aide de l&#39;interface utilisateur de Places.

## Modifier un point d’intérêt

1. Connexion à Places à l’aide de votre Adobe ID.
1. Connectez-vous au service Places à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône qui ressemble à une liste à puces.
1. Recherchez le point d’intérêt à modifier.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Afficher les détails]**.
1. Mettez à jour les informations et cliquez sur **[!UICONTROL Enregistrer]**.

## Supprimer un point d’intérêt

1. Connexion à Places à l’aide de votre Adobe ID.
1. Connectez-vous au service Places à l’aide de votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur l’icône qui ressemble à une liste à puces.
1. Recherchez le point d’intérêt à supprimer.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Supprimer]**.

## Filtrer les points d’intérêt par ville, état, pays ou métadonnées

![filtrer un point d’intérêt](/help/assets/filter_poi.png)

1. Connectez-vous à l’interface utilisateur du service Places à l’aide de votre Adobe ID.
1. En haut à droite, cliquez sur l&#39;icône de filtrage.
1. Vous pouvez filtrer les points d’intérêt de l’une des manières suivantes :

   * Par bibliothèque :

     a. Sélectionnez une bibliothèque.

   * Par propriété :

     a. Dans la liste déroulante Propriété, sélectionnez **[!UICONTROL Pays]**, **[!UICONTROL État]** ou **[!UICONTROL Ville]**.

     b. Sur la ligne suivante, saisissez une valeur.

     Par exemple, vous pouvez sélectionner **[!UICONTROL État]** et saisir **[!UICONTROL Californie]**.

   * Avec des métadonnées :

     a. Saisissez une clé et une valeur.

## Définition d’un point d’intérêt de limite géographique

Les limites géographiques sont un type de point d’intérêt et sont définies dans la base de données par les clés suivantes :

| Clés | Description | Obligatoire ? |
| :--- | :--- | :--- |
| Identifiant | Identifiant unique attribué à chaque point d’intérêt | Oui |
| Nom | Nom convivial donné au point d’intérêt. | Oui |
| Bibliothèque | Une bibliothèque doit être affectée à chaque point d’intérêt pour l’organisation. | Oui |
| Rayon | Rayon de votre point d’intérêt en mètres. | Oui |
| Icône | Aidez à visualiser les points d’intérêt. | Oui (affecté par défaut) |
| Couleur | Aidez à visualiser les points d’intérêt. | Oui (affecté par défaut) |
| Catégorie | Attribuez un framework commun de catégories communes à tous les POI dans toutes les bibliothèques. | Non |
| Adresse | Rue. | Non |
| Ville | Ville du point d’intérêt. | Non |
| État/Région | État ou région du point d’intérêt. | Non |
| Pays | Pays du point d’intérêt. | Non |
| Latitude | Coordonnée de latitude pour le centre du point d’intérêt. | Oui |
| Longitude | Coordonnée de longitude pour le centre du point d’intérêt. | Oui |
| Métadonnées | Paires clé-valeur personnalisées pouvant être affectées aux POI. Ces métadonnées rationalisent les futurs workflows en vous permettant de regrouper les points d’intérêt entre les bibliothèques pour que chacune d’elles utilise des règles et des filtres dans les workflows en aval, tels que l’envoi d’une notification push lorsqu’un utilisateur accède à un point d’intérêt avec le type = concurrent. | Non |
