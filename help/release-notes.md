---
title: Notes de mise à jour
description: Notes de mise à jour du service Places.
translation-type: tm+mt
source-git-commit: 3f986697179eb9c0af1d9b54daf67793a99b8491
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 3%

---


# Notes de mise à jour {#release-notes}

## 8 juillet 2020

* **Lieux et emplacements des extensions Moniteur**

   * Des emplacements et des emplacements ont été ajoutés pour [Réagir aux applications natives](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Des emplacements et des emplacements ont été ajoutés pour les [applications Cordova](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Pour plus d&#39;informations, voir : [Utilisation de l&#39;extension Places](https://docs.adobe.com/content/help/fr-FR/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 12 mai 2020

* **Places Service**

   * Importer en bloc les points d’intérêt d’un fichier CSV à l’aide du bouton &quot;Importer les points d’intérêt&quot;
   * Sélection de plusieurs points d’intérêt et modification en masse ou ajout de valeurs de métadonnées

## 6 mai 2020

* **PlacesMonitor 2.1.1**

   * **Android**

      * Journalisation améliorée

## 5 mai 2020


* **PlacesMonitor 2.1.3**

   * **iOS**

      * Journalisation améliorée

## 20 février 2020

* **ACPPlaces 1.3.1 (iOS)**

   * L’extension Places signale désormais les informations de version au concentrateur de événements dans le SDK principal.
   * Les informations d’adhésion à l’API du périphérique comportent désormais une durée de vie par défaut d’une heure à partir du moment où elles sont collectées. Pour plus d’informations, voir [Modification des lieux où la durée de vie de l’abonnement](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl).


* **Lieux 1.4.1 (Android)**

   * L’extension Places signale désormais les informations de version au concentrateur de événements dans le SDK principal.
   * Les informations d’adhésion à l’API du périphérique comportent désormais une durée de vie par défaut d’une heure à partir du moment où elles sont collectées. Pour plus d’informations, voir [Modification des lieux où la durée de vie de l’abonnement](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl).

## 27 janvier 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Appelez la nouvelle API Places pour collecter l’état d’autorisation de l’emplacement au lancement de l’application et lorsque l’autorisation est modifiée pendant l’exécution de l’application.
      * API setRequestLocationPermission Ajoutée et API setLocationPermission obsolète.

## 9 janvier 2020

* **Lieux 1.4.0**

   * **Android**

      * Ajouté une nouvelle API, `setAuthorizationStatus`, pour définir l&#39;état d&#39;autorisation du périphérique pour Places Services. La valeur est stockée et utilisée dans l’état Lieux partagés.

## 4 décembre 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Appelez l&#39;API Places pour collecter CLAuthorizationStatus depuis le périphérique lorsqu&#39;il change.

## 3 décembre 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * Ajouté une nouvelle API, `setAuthorizationStatus`, pour définir l&#39;état d&#39;autorisation du périphérique pour Places Services. La valeur est stockée et utilisée dans l’état Lieux partagés.

## 25 novembre 2019

* **PlacesMonitor 2.2.1**

   * **iOS**

      * Correction des instructions d&#39;importation pour les projets Cocoapods à l&#39;aide de l&#39;option de plusieurs projets de capsules.

## 22 novembre 2019

* **PlacesMonitor 2.2.1**

   * **Android**

      * Le Moniteur reconnaît désormais le démarrage d’un périphérique Android et, si nécessaire, enregistre à nouveau les géoofences avec le système d’exploitation en fonction de l’emplacement actuel du périphérique.
      * Correction d’une condition de concurrence en raison de laquelle les événements d’entrée/sortie étaient parfois ignorés.

## 9 octobre 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Ajouté une nouvelle API, `setRequestAuthorizationLevel`, pour définir le type de demande d&#39;autorisation d&#39;emplacement pour laquelle l&#39;utilisateur sera invité à répondre.
   * **Android**

      * Ajouté une nouvelle API, `setLocationPermission`, afin de définir le type de demande d&#39;autorisation d&#39;emplacement pour laquelle l&#39;utilisateur sera invité.
      * Le moniteur de lieux prend désormais en charge Android 10.



## 8 août 2019

Les mises à jour suivantes ont été apportées à cette version :

### Mises à jour de l’interface utilisateur

Voici une liste des mises à jour apportées à l’interface utilisateur Lieux :

#### Nouvelles fonctionnalités

* Ajouté une nouvelle vue de liste qui montre les points d’intérêt sans la carte.
* Options de filtrage POI Ajoutées pour la ville, l’état, le pays et les métadonnées.
* La première bibliothèque d’une organisation est automatiquement créée.
* Tri POI Ajouté vers la Vue de Liste.

#### Mises à jour de l’interface utilisateur

* Déplacement du panneau liste et détails sur le côté droit de l’interface utilisateur.
* Ajouté un nouveau panneau de recherche en haut de l’interface utilisateur.
* Si une seule bibliothèque est présente, cette bibliothèque est automatiquement sélectionnée lors de la création d’une API.
* Déplacement de la gestion des bibliothèques dans une fenêtre contextuelle.
* Ajouté un nombre de points d’intérêt à côté des filtres.

## 6 août 2019

Les mises à jour suivantes ont été apportées à cette version :

### Monitor Launch Extension 2.0.0

* Mise à jour des instructions d’installation Android et iOS pour le moniteur de lieux 2.0.

## 31 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

### Places Monitor 2.0.0

* L’état de surveillance est maintenant conservé entre les lancements.
* Le traitement du rappel, qui résultait d&#39;une demande d&#39;autorisation d&#39;emplacement n&#39;exige plus que vous étendiez PlacesActivity.
* Modification d’une API existante, permettant aux développeurs d’effacer toutes les données Places du périphérique :

   Ancienne API : `public static void stop();`

   Nouvelle API : `public static void stop (final boolean clearData);`

* Mise à jour de l&#39;utilisation de l&#39;API `getNearbyPointsOfInterest` pour gérer plus efficacement les scénarios d&#39;erreur.

## 25 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

### ACPPlacesMonitor 2.0.0

* Pour effacer toutes les données Places du périphérique,

   dans ACPPlacesMonitor, remplacez une API existante `+ (void) stop;` par `+ (void) stop: (BOOL) clearData;`.

* Mise à jour de l’utilisation de l’API ACPPlaces `getNearbyPointsOfInterest` pour gérer les scénarios d’erreur de manière plus efficace.

## 22 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

### Android Places 1.3.0

* Ajouté une nouvelle API qui efface toutes les données relatives aux emplacements de l’état partagé, de la mémoire in-app et de la préférence partagée.
* Correction d’un problème en raison duquel l’état partagé n’était pas mis à jour pendant le début de l’application.
* Correction d’un bogue en raison duquel le rappel `getNearbyPointsOfInterest` renvoyait le code d’erreur `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` sur Internet.
* `getNearbyPointsOfInterest` L&#39;API (sans errorCallback) sera  `successCallback` appelée avec une liste de point vide, en cas d&#39;erreur lors de la récupération des points d&#39;intérêt voisins.

## 19 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places 1.2.0**

Ajouté une nouvelle API qui efface toutes les données relatives aux emplacements de l’état partagé, de la mémoire in-app et `NSUserDefaults`.

## 25 juin 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places Monitor 1.0.2**

* Améliorations de la qualité de vie, notamment une meilleure documentation et une meilleure consignation en code.

## 17 juin 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places 1.1.0**

* Ajouté une nouvelle API pour renvoyer un code d&#39;erreur en cas d&#39;échec de récupération des emplacements voisins.
* Lorsque l’état de confidentialité est défini sur l’exclusion, toutes les données relatives aux emplacements sont désormais effacées du périphérique.
* Correction d’un problème en raison duquel, après un premier lancement, les événements Places étaient parfois perdus en raison de mauvaises conditions réseau.
* Correction d’un problème en raison duquel, lors du traitement des événements d’entrée POI en succession rapide, le remplacement de jetons via le moteur de règles référençait parfois un point d’entrée incorrect.

## 30 mai 2019

**Android Places Monitor 1.0.1**

* Correction d’un problème qui empêchait un événement d’entrée pour les points d’intérêt lorsque la surveillance Places était lancée.

## 28 mai 2019

Correction des problèmes suivants dans l’interface utilisateur Lieux :

* Mise à jour du commutateur de solutions en emplacements afin de l’aligner sur le reste de l’Experience Cloud.
* Correction d’un problème en raison duquel le classement était enregistré dans les cas où aucun changement de classement n’était effectué.
* Augmentation à 10 mètres du rayon minimum autorisé dans l’interface utilisateur.
* Correction d’un problème en raison duquel, si vous supprimez tous les nombres du champ, le champ de rayon était rétabli à 20 mètres.

## 17 mai 2019

Les mises à jour suivantes ont été apportées à cette version :

**Android Places 1.2.0**

* Ajouté une nouvelle API pour traiter une Geofence individuelle.
* Correction de bogues pour empêcher plusieurs événements d’entrée consécutifs.

**Android Places Monitor 1.0.0**

Version initiale du moniteur de lieux pour Android.

Le moniteur de lieux gère les API d&#39;emplacement au niveau du système d&#39;exploitation et communique directement avec l&#39;extension Places. Avec les deux extensions installées, les clients peuvent avoir une surveillance régionale prête à l&#39;emploi dans leur application.
Pour plus d&#39;informations sur le Moniteur des lieux, cliquez ici.


## 2 mai 2019

**Android Places 1.1.0**

* Introduction d&#39;une nouvelle API pour getNearByPlaces, qui comporte un errorCallback et est appelée avec un errorCode qui indique la raison de l&#39;erreur.
* L&#39;extension Places met maintenant les événements en file d&#39;attente jusqu&#39;à ce qu&#39;une configuration soit obtenue.
* Prise en charge Ajoutée des configurations prenant en charge les environnements.
* Correctif : correction des clés des événements d&#39;entrée/sortie de la région
* L’Enregistrement du dernier emplacement connu respecte désormais correctement l’état de confidentialité de l’utilisateur.


## 9 avril 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places Monitor 1.0.1**

* Couverture d&#39;essai de l&#39;unité complète Ajoutée.
* Intégration CI (CircleCI)
* Intégration de la couverture du code (codecov)

## 25 mars 2019

iOS Places Monitor 1.0.0

Version initiale du moniteur de lieux pour iOS.

Le moniteur de lieux gère les API d&#39;emplacement au niveau du système d&#39;exploitation et communique directement avec l&#39;extension Places. Avec les deux extensions installées, les clients peuvent avoir une surveillance régionale prête à l&#39;emploi dans leur application. Pour plus d&#39;informations sur le moniteur de lieux, voir [Extension du moniteur de lieux](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

## 28 février 2019

### Version bêta

Il s&#39;agit de la première version du service Places, un ensemble d&#39;outils qui permet aux clients d&#39;enrichir l&#39;expérience de leurs utilisateurs avec des données de localisation dans le monde réel. Pour la première version, notre Principale utilisation consiste à permettre aux applications mobiles de récupérer des données d’emplacement personnalisées et d’agir sur ces données via Adobe Experience Platform Launch.

### Principales fonctionnalités

Voici les principales fonctionnalités de cette version :

#### Interface utilisateur du service Places

Nous avons publié une interface utilisateur de gestion dans laquelle vous pouvez vue et gérer vos points d’intérêt (POI). Vous pouvez également organiser vos points d’intérêt en bibliothèques. Outre les métadonnées standard telles que la ville, l’état et la catégorie, nous prenons également en charge la possibilité d’ajouter des métadonnées personnalisées à vos points d’intérêt.

* Pour afficher l’interface utilisateur, accédez à [https://places.adobe.com](https://places.adobe.com).
* Pour commencer à utiliser l’interface utilisateur, voir [Prise en main](/help/getting-started.md).

#### Place l&#39;extension

A l’aide de l’extension Places, vous pouvez ajouter vos bibliothèques du service Places à votre application mobile et agir sur leurs points d’accès. En utilisant le créateur de règles dans l’Experience Platform Launch, vous pouvez déclencher des actions lorsque les utilisateurs entrent et sortent des points d’intérêt.

Dans l&#39;extension Places :

* Vous pouvez choisir les bibliothèques POI à inclure dans votre application.
* Événements de règle qui se déclenchent lors de l’entrée ou de la sortie d’un point d’accès.
* Créez des éléments de données qui pointent vers le point d’intérêt actuel de l’utilisateur.

Pour plus d’informations sur l’extension Places, voir [Extension Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Place les API

Vous pouvez utiliser les API Lieux pour effectuer les opérations suivantes :

* Permettre aux développeurs de renseigner et de mettre à jour leur liste de points d’intérêt.
* Créez votre propre interface utilisateur ou intégrez-la à une base de données de point d’accès existante.
* Utilisez les points de fin de lot de l’API Places pour effectuer une importation en masse des points d’intérêt.

   Vous pouvez utiliser l&#39;utilitaire Python fourni pour terminer l&#39;importation en masse.

Pour plus d&#39;informations sur les API Places, voir [API de service Web](/help/web-service-api/places-web-services.md).

### Bientôt disponible

#### Intégration    Analytics

L’extension Analytics est en cours de mise à jour afin d’ajouter automatiquement des données contextuelles d’emplacement de votre base de données du service Places à tous les appels Analytics sortants lorsqu’un utilisateur est dans un point d’accès (appels passifs). Cette mise à jour permet également à la création de règles de déclencher les appels de suivi Analytics directement à l’entrée ou à la sortie de l’API (appels Principaux).
