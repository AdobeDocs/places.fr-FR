---
title: Notes de mise à jour des emplacements d’Adobe Experience Platform
seo-title: Notes de mise à jour des emplacements de plateformes Adobe Experience Platform.
description: Notes de mise à jour des emplacements de plateformes Adobe Experience Platform.
seo-description: Notes de mise à jour des emplacements de plateformes Adobe Experience Platform.
translation-type: tm+mt
source-git-commit: 9fc484fd44c74ad77255668e4fbd7bc1642932e2

---


# Notes de mise à jour {#release-notes}

Voici les notes de mise à jour pour les emplacements (emplacements) d’Adobe Experience Platform :

## 9 octobre 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Ajout d’une nouvelle API `setRequestAuthorizationLevel`, afin de définir le type de demande d’autorisation d’emplacement pour laquelle l’utilisateur sera invité.
   * **Android**

      * Ajout d’une nouvelle API `setLocationPermission`, afin de définir le type de demande d’autorisation d’emplacement pour laquelle l’utilisateur sera invité.
      * Le moniteur de lieux prend désormais en charge Android 10.



## 8 août 2019

Les mises à jour suivantes ont été effectuées dans cette version :

### Mises à jour de l’interface utilisateur Places

Voici la liste des mises à jour apportées à l’interface utilisateur Places :

#### Nouvelles fonctionnalités

* Ajout d’un nouvel affichage de liste qui affiche les points d’intérêt sans mappage.
* Ajout d’options de filtrage POI pour la ville, l’état, le pays et les métadonnées.
* La première bibliothèque d’une organisation est automatiquement créée.
* Ajout d’un tri POI en mode Liste.

#### Mises à jour de l’interface utilisateur

* Déplacement du panneau de liste et de détails sur le côté droit de l’interface utilisateur.
* Ajout d’un nouveau panneau de recherche en haut de l’interface utilisateur.
* Si une seule bibliothèque est présente, cette bibliothèque est automatiquement sélectionnée lors de la création d’une API.
* Déplacement de la gestion des bibliothèques dans une fenêtre contextuelle.
* Ajout d’un nombre de points d’intérêt en regard des filtres.

## 6 août 2019

Les mises à jour suivantes ont été effectuées dans cette version :

### Places Monitor Launch Extension 2.0.0

* Mise à jour des instructions d’installation d’Android et d’iOS pour Places Monitor 2.0.

## 31 juillet 2019

Les mises à jour suivantes ont été effectuées dans cette version :

### Places Monitor 2.0.0

* L’état de surveillance est maintenant conservé entre les lancements.
* La gestion du rappel, qui résulte d’une demande d’autorisation d’emplacement, n’exige plus que vous étendiez PlacesActivity.
* Modification d’une API existante, permettant aux développeurs d’effacer toutes les données Places du périphérique :

   Ancienne API : `public static void stop();`

   Nouvelle API : `public static void stop (final boolean clearData);`

* Mise à jour de l’utilisation de l’ `getNearbyPointsOfInterest` API Lieux pour gérer les scénarios d’erreur de manière plus efficace.

## 25 juillet 2019

Les mises à jour suivantes ont été effectuées dans cette version :

### ACPPlacesMonitor 2.0.0

* Pour effacer toutes les données Places du périphérique,

   dans ACPPlacesMonitor, remplacez une API existante `+ (void) stop;` par`+ (void) stop: (BOOL) clearData;`.

* Mise à jour de l’utilisation de l’ `getNearbyPointsOfInterest` API ACPPlaces pour gérer les scénarios d’erreur de manière plus efficace.

## 22 juillet 2019

Les mises à jour suivantes ont été effectuées dans cette version :

### Android Places 1.3.0

* Ajout d’une nouvelle API qui efface toutes les données liées aux emplacements de l’état partagé, de la mémoire in-app et de la préférence partagée.
* Correction d’un problème en raison duquel l’état partagé n’était pas mis à jour au démarrage de l’application.
* Correction d’un bogue en raison duquel le `getNearbyPointsOfInterest` rappel renvoyait du code d’erreur `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` sur Internet.
* `getNearbyPointsOfInterest` L’API (sans errorCallback) aura l’ `successCallback` appel avec une liste de points d’intérêt vide, en cas d’erreur lors de la récupération des points d’intérêt voisins.

## 19 juillet 2019

Les mises à jour suivantes ont été effectuées dans cette version :

**iOS Places 1.2.0**

Ajout d’une nouvelle API qui efface toutes les données liées aux emplacements de l’état partagé, de la mémoire in-app et `NSUserDefaults`.

## 25 juin 2019

Les mises à jour suivantes ont été effectuées dans cette version :

**iOS Places Monitor 1.0.2**

* Améliorations de la qualité de vie, notamment une meilleure documentation et une meilleure journalisation en code.

## 17 juin 2019

Les mises à jour suivantes ont été effectuées dans cette version :

**iOS Places 1.1.0**

* Ajout d’une nouvelle API pour renvoyer un code d’erreur en cas d’échec de récupération des emplacements voisins.
* Lorsque l’état de confidentialité est défini sur l’exclusion, toutes les données relatives aux emplacements sont désormais effacées du périphérique.
* Correction d’un problème en raison duquel, après un premier lancement, les événements Places étaient parfois perdus en raison de mauvaises conditions réseau.
* Correction d’un problème en raison duquel, lors du traitement des événements d’entrée d’un point d’entrée, le remplacement de jeton par le biais du moteur de règles faisait parfois référence à un point d’entrée incorrect.

## 30 mai 2019 (Lieux)

**Android Places Monitor 1.0.1**

* Correction d’un problème qui empêchait un événement d’entrée pour les points d’intérêt lors du démarrage de la surveillance Places.

## 28 mai 2019

Correction des problèmes suivants dans l’interface utilisateur Lieux :

* Mise à jour du sélecteur de solutions dans les emplacements afin de l’aligner sur le reste d’Experience Cloud.
* Correction d’un problème en raison duquel le classement était enregistré dans les cas où aucun changement de classement n’était effectué.
* Augmentation à 10 mètres du rayon minimal autorisé dans l’interface utilisateur.
* Correction d’un problème en raison duquel, si vous supprimez tous les nombres du champ, le champ de rayon était rétabli à 20 mètres.

## 17 mai 2019 (Lieux)

Les mises à jour suivantes ont été effectuées dans cette version :

**Android Places 1.1.0**

* Ajout d’une nouvelle API pour traiter une Geofence individuelle.
* Correction de bogues pour empêcher plusieurs événements d’entrée consécutifs.

**Android Places Monitor 1.0.0**

Version initiale de Places Monitor pour Android.

Le moniteur de lieux gère les API d’emplacement au niveau du système d’exploitation et communique directement avec l’extension Places. Avec les deux extensions installées, les clients peuvent avoir une surveillance de région prête à l’emploi dans leur application.
Pour plus d'informations sur le moniteur des lieux, cliquez ici.


## 2 mai 2019

**Android Places 1.1.0**

* Introduction d’une nouvelle API pour getNearByPlaces, qui comporte un errorCallback et est appelée avec un errorCode qui indique la raison de l’erreur.
* L’extension Places met maintenant les événements en file d’attente jusqu’à ce qu’une configuration soit obtenue.
* Ajout de la prise en charge des configurations respectueuses de l’environnement.
* Correctif : correction des clés pour les événements d’entrée/sortie de région
* Le stockage du dernier emplacement connu respecte désormais correctement l’état de confidentialité de l’utilisateur.


## 9 avril 2019

Les mises à jour suivantes ont été effectuées dans cette version :

**iOS Places Monitor 1.0.1**

* Ajout de la couverture complète des tests unitaires.
* Intégration CI (CircleCI)
* Intégration de la couverture du code (codecov)

## 25 mars 2019

iOS Places Monitor 1.0.0

Version initiale de Places Monitor pour iOS.

Le moniteur de lieux gère les API d’emplacement au niveau du système d’exploitation et communique directement avec l’extension Places. Avec les deux extensions installées, les clients peuvent avoir une surveillance de région prête à l’emploi dans leur application. Pour plus d’informations sur le moniteur de lieux, voir [Extension](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)du moniteur de lieux.

## 28 février 2019

### Version bêta

Il s’agit de la première version de Places, un ensemble d’outils qui permet aux clients d’enrichir l’expérience de leurs utilisateurs avec des données d’emplacement réelles. Pour la première version, notre principal cas d’utilisation consiste à permettre aux applications mobiles de récupérer des données d’emplacement personnalisées et d’agir sur ces données par le biais d’Adobe Experience Platform Launch.

### Fonctionnalités clés

Voici les principales fonctionnalités de cette version :

#### Interface utilisateur Places

Nous avons publié une interface utilisateur de gestion dans laquelle vous pouvez afficher et gérer vos points d’intérêt (POI). Vous pouvez également organiser vos points d’intérêt en bibliothèques. Outre les métadonnées standard telles que la ville, l’état et la catégorie, nous prenons également en charge la possibilité d’ajouter des métadonnées personnalisées à vos points d’intérêt.

* Pour afficher l’interface utilisateur Places, accédez à [https://places.adobe.com](https://places.adobe.com).
* Pour commencer avec l’interface utilisateur Places, voir [Prise en main](/help/getting-started.md).

#### Extension Places

A l’aide de l’extension Places, vous pouvez ajouter vos bibliothèques Places à votre application mobile et agir sur leurs points d’intérêt. A l’aide du créateur de règles dans le lancement de la plateforme d’expérience, vous pouvez déclencher des actions pour déclencher le déclenchement lorsque les utilisateurs entrent et sortent des points d’accès.

Dans l’extension Places :

* Vous pouvez choisir les bibliothèques POI à inclure dans votre application.
* Evénements de règle qui se déclenchent lors de l’entrée ou de la sortie d’un point d’accès.
* Créez des éléments de données qui pointent vers le point d’intérêt actuel de l’utilisateur.

Pour plus d’informations sur l’extension Places, voir [Extension](/help/places-ext-aep-sdks/places-extension/places-extension.md)Places.

#### Utilise des API

Vous pouvez utiliser les API Places pour effectuer les opérations suivantes :

* Permet aux développeurs de renseigner et de mettre à jour leur liste d’API.
* Créez votre propre interface utilisateur ou intégrez-la à une base de données d’API existante.
* Utilisez les points de fin de lot de l’API Places pour effectuer une importation en masse des points d’intérêt.

   Un utilitaire python est fourni avec les API.

Pour plus d’informations sur les API Places, voir Services [Web](/help/places-web-service-api/places-web-services.md)Places.

### Bientôt disponible

#### Intégration    Analytics

L’extension Analytics est en cours de mise à jour afin d’ajouter automatiquement des données contextuelles d’emplacement de votre base de données Places à tous les appels Analytics sortants lorsqu’un utilisateur se trouve dans une API (appels passifs). Cette mise à jour permet également à la création de règles de déclencher les appels de suivi Analytics directement à l’entrée ou à la sortie de l’API (appels actifs).

