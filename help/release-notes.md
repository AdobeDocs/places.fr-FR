---
title: Notes de mise à jour
description: Notes de mise à jour de Places Service.
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 3%

---

# Notes de mise à jour {#release-notes}

## 8 juillet 2020

* **Extensions de surveillance des Places et des Places**

   * Ajout des extensions Places et Places Monitor pour [React Native Applications](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Ajout des extensions Places et Places Monitor pour [Applications Cordova](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Pour plus d’informations, voir : [Utilisation de l’extension Places](https://experienceleague.adobe.com/docs/places/using/places-ext-aep-sdks/places-extension/places-extension.html?lang=fr)


## 12 mai 2020

* **Places Service**

   * Importation groupée de POI à partir d’un fichier CSV à l’aide du bouton &quot;Importer les POI&quot;
   * Sélectionner plusieurs points ciblés et modifier ou ajouter en masse des valeurs de métadonnées

## 6 mai 2020

* **PlacesMonitor 2.2.1**

   * **Android**

      * Journalisation améliorée

## 5 mai 2020


* **PlacesMonitor 2.1.3**

   * **iOS**

      * Journalisation améliorée

## 20 février 2020

* **ACPPlaces 1.3.1 (iOS)**

   * L’extension Places signale désormais les informations de version au hub d’événements dans le SDK principal.
   * Les informations d’adhésion au point ciblé de l’appareil ont désormais une durée de vie par défaut d’une heure à partir du moment où elles sont collectées. Pour plus d’informations, voir [Modification de la durée de vie de l’appartenance à Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1 (Android)**

   * L’extension Places signale désormais les informations de version au hub d’événements dans le SDK principal.
   * Les informations d’adhésion au point ciblé de l’appareil ont désormais une durée de vie par défaut d’une heure à partir du moment où elles sont collectées. Pour plus d’informations, voir [Modification de la durée de vie de l’appartenance à Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 27 janvier 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Appelez la nouvelle API Places pour collecter l’état d’autorisation de l’emplacement au lancement de l’application et lorsque l’autorisation change pendant l’exécution de l’application.
      * Ajout de l’API setRequestLocationPermission et de l’API setLocationPermission obsolète.

## 9 janvier 2020

* **Places 1.4.0**

   * **Android**

      * Ajout d’une nouvelle API, `setAuthorizationStatus`, pour définir l’état d’autorisation de l’appareil pour Places Services. La valeur est stockée et utilisée dans l’état partagé Places .

## 4 décembre 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Appelez l’API Places pour collecter CLAuthorizationStatus depuis l’appareil lorsqu’il change.

## 3 décembre 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * Ajout d’une nouvelle API, `setAuthorizationStatus`, pour définir l’état d’autorisation de l’appareil pour Places Services. La valeur est stockée et utilisée dans l’état partagé Places .

## 25 novembre 2019

* **PlacesMonitor 2.1.1**

   * **iOS**

      * Correction des instructions d’importation pour les projets Cocoapods à l’aide de l’option de plusieurs projets de capsule .

## 22 novembre 2019

* **PlacesMonitor 2.1.1**

   * **Android**

      * Le moniteur reconnaît désormais le démarrage d’un appareil Android et, si nécessaire, enregistre à nouveau les clôtures virtuelles avec le système d’exploitation en fonction de l’emplacement actuel de l’appareil.
      * Correction d’une condition de concurrence en raison de laquelle les événements d’entrée/de sortie étaient parfois ignorés.

## 9er octobre 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Ajout d’une nouvelle API, `setRequestAuthorizationLevel`, pour définir le type de demande d’autorisation d’emplacement pour laquelle l’utilisateur sera invité à le faire.


   * **Android**

      * Ajout d’une nouvelle API, `setLocationPermission`, pour définir le type de demande d’autorisation d’emplacement pour laquelle l’utilisateur sera invité à le faire.
      * Le moniteur Places prend désormais en charge Android 10.

## 8 août 2019

Les mises à jour suivantes ont été apportées à cette version :

### Mises à jour de l’interface utilisateur

Voici la liste des mises à jour apportées à l’interface utilisateur de Places :

#### Nouvelles fonctionnalités

* Ajout d’une nouvelle vue de liste qui affiche les points ciblés sans la carte.
* Ajout d’options de filtrage des points ciblés pour la ville, l’État, le pays et les métadonnées.
* La première bibliothèque d’une organisation est automatiquement créée.
* Ajout du tri des points ciblés en mode Liste.

#### Mises à jour de l’interface utilisateur

* Déplacement du panneau de liste et de détails vers le côté droit de l’interface utilisateur.
* Ajout d’un nouveau panneau de recherche en haut de l’interface utilisateur.
* Si une seule bibliothèque est présente, cette bibliothèque est automatiquement sélectionnée lors de la création d’un point ciblé.
* Déplacement de la gestion des bibliothèques dans une fenêtre contextuelle.
* Ajout d’un nombre de points ciblés en regard des filtres.

## 6 août 2019

Les mises à jour suivantes ont été apportées à cette version :

### Surveillance de l’extension Launch 2.0.0

* Mise à jour des instructions d’installation d’Android et d’iOS pour le moniteur de Places 2.0.

## 31 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

### Places Monitor 2.0.0

* L’état de surveillance est maintenant conservé entre les lancements.
* La gestion du rappel, résultant d’une demande d’autorisation d’emplacement n’exige plus que vous étendiez PlacesActivity.
* Modification d’une API existante, permettant aux développeurs d’effacer toutes les données Places de l’appareil :

  Ancienne API : `public static void stop();`

  Nouvelle API : `public static void stop (final boolean clearData);`

* Mise à jour de l’utilisation de la fonction `getNearbyPointsOfInterest` API permettant de gérer plus efficacement les scénarios d’erreur.

## 25 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

### ACPPlacesMonitor 2.0.0

* Pour effacer toutes les données de Places de l&#39;appareil,

  dans ACPPlacesMonitor, remplacé une API existante `+ (void) stop;` avec`+ (void) stop: (BOOL) clearData;`.

* Mise à jour de l’utilisation des ACPPlaces `getNearbyPointsOfInterest` API permettant de gérer plus efficacement les scénarios d’erreur.

## 22 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

### Android Places 1.3.0

* Ajout d’une nouvelle API qui efface toutes les données liées à Places de l’état partagé, de la mémoire in-app et des préférences partagées.
* Correction d’un problème en raison duquel l’état partagé n’était pas mis à jour au démarrage de l’application.
* Correction d’un bogue en raison duquel `getNearbyPointsOfInterest` callback renvoyait le code d’erreur `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` sur Internet.
* `getNearbyPointsOfInterest` L’API (sans errorCallback) aura la variable `successCallback` appelé avec une liste de points ciblés vide, en cas d’erreur lors de la récupération des points ciblés proches.

## 19 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places 1.2.0**

Ajout d’une nouvelle API qui efface toutes les données liées à Places de l’état partagé, de la mémoire in-app et `NSUserDefaults`.

## 25 juin 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places Monitor 1.0.2**

* Améliorations de la qualité de vie, notamment une meilleure documentation et une meilleure journalisation du code intégré.

## 17 juin 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places 1.1.0**

* Ajout d’une nouvelle API pour renvoyer un code d’erreur en cas d’échec lors de la récupération des emplacements voisins.
* Lorsque l’état de confidentialité est défini sur exclusion, toutes les données relatives à Places sont désormais effacées de l’appareil.
* Correction d’un problème qui, après un premier lancement, entraînait parfois la perte d’événements Places en raison de mauvaises conditions réseau.
* Correction d’un problème en raison duquel, lors du traitement des événements d’entrée de point ciblé dans une succession rapide, le remplacement de jetons par le biais du moteur de règles faisait parfois référence à un point ciblé incorrect.

## 30 mai 2019

**Android Places Monitor 1.0.1**

* Correction d’un problème qui empêchait un événement d’entrée pour les points ciblés lorsque la surveillance Places était lancée.

## 28 mai 2019

Correction des problèmes suivants dans l’interface utilisateur de Places :

* Mise à jour du sélecteur de solution dans Places afin de l’aligner sur le reste de l’Experience Cloud.
* Correction d’un problème en raison duquel le classement sauvegardait les instances où aucun changement de classement n’était effectué.
* Augmentation à 10 mètres du rayon minimal autorisé dans l’interface utilisateur.
* Correction d’un problème en raison duquel, si vous supprimez tous les nombres du champ, le champ de rayon était réinitialisé à 20 mètres.

## 17 mai 2019

Les mises à jour suivantes ont été apportées à cette version :

**Android Places 1.2.0**

* Ajout d’une nouvelle API pour traiter une clôture géographique individuelle.
* Correction de bogue pour empêcher plusieurs événements d’entrée consécutifs.

**Android Places Monitor 1.0.0**

Version initiale du moniteur des Places pour Android.

Le moniteur de Places gère les API de position au niveau du système d’exploitation et communique directement avec l’extension Places. Une fois les deux extensions installées, les clients peuvent disposer d’une surveillance de région prête à l’emploi dans leur application.
Pour plus d&#39;informations sur le moniteur de Places, cliquez ici.


## 2 mai 2019

**Android Places 1.1.0**

* Introduction d’une nouvelle API pour getNearByPlaces, qui comporte un errorCallback et est appelée avec un errorCode qui indique la raison de l’erreur.
* L’extension Places met désormais les événements en file d’attente jusqu’à ce qu’une configuration soit obtenue.
* Ajout de la prise en charge des configurations basées sur l’environnement.
* Bug Fix : correction des clés pour les événements d’entrée/de sortie de région
* Le stockage du dernier emplacement connu respecte désormais correctement l’état de confidentialité de l’utilisateur.


## 9 avril 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places Monitor 1.0.1**

* Ajout d’une couverture de test unitaire complète.
* Intégration CI (CircleCI)
* Intégration de la couverture du code (codecov)

## 25 mars 2019

iOS Places Monitor 1.0.0

Version initiale du moniteur des Places pour iOS.

Le moniteur de Places gère les API de position au niveau du système d’exploitation et communique directement avec l’extension Places. Une fois les deux extensions installées, les clients peuvent disposer d’une surveillance de région prête à l’emploi dans leur application.

## 28 février 2019

### Version bêta

Il s’agit de la première version de Places Service, un ensemble d’outils qui permet aux clients d’enrichir l’expérience de leurs utilisateurs avec des données de localisation du monde réel. Pour la première version, notre cas d’utilisation Principal consiste à permettre aux applications mobiles de récupérer des données d’emplacement personnalisées et d’agir sur ces données via Adobe Experience Platform Launch.

### Principales fonctionnalités

Voici les principales fonctionnalités de cette version :

#### Interface utilisateur de Places Service

Nous avons publié une interface utilisateur de gestion dans laquelle vous pouvez afficher et gérer vos points ciblés (POI). Vous pouvez également organiser vos points ciblés en bibliothèques. Outre les métadonnées standard telles que la ville, l’état et la catégorie, nous prenons également en charge la possibilité d’ajouter des métadonnées personnalisées à vos points ciblés.

* Pour afficher l’interface utilisateur, accédez à [https://places.adobe.com](https://places.adobe.com).
* Pour commencer à utiliser l’interface utilisateur, voir [Prise en main](/help/getting-started.md).

#### Extension Places

À l’aide de l’extension Places, vous pouvez ajouter vos bibliothèques Places Service à votre application mobile et agir sur leurs points ciblés. À l’aide du créateur de règles dans Experience Platform Launch, vous pouvez déclencher des actions pour déclencher des actions lorsque les utilisateurs entrent et sortent des points ciblés.

Dans l&#39;extension Places :

* Vous pouvez choisir les bibliothèques POI à inclure dans votre application.
* Événements de règle qui se déclenchent lors de l’entrée ou de la sortie du point ciblé.
* Créez des éléments de données qui pointent vers le point ciblé actuel de l’utilisateur.

Pour plus d’informations sur l’extension Places, voir [Extension Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### API Places

Vous pouvez utiliser les API Places pour effectuer les opérations suivantes :

* Permet aux développeurs de renseigner et de mettre à jour leur liste de points ciblés.
* Créez votre propre interface utilisateur ou intégrez une base de données POI existante.
* Utilisez les points de fin de lot de l’API Places pour effectuer une importation en bloc des points ciblés.

  Vous pouvez utiliser l’utilitaire Python fourni pour terminer l’importation en bloc.

Pour plus d’informations sur les API de Places, voir [API de service Web](/help/web-service-api/places-web-services.md).

### Bientôt disponible

#### Intégration    Analytics

L’extension Analytics est en cours de mise à jour afin d’ajouter automatiquement des données contextuelles d’emplacement de votre base de données Places Service à tous les appels Analytics sortants lorsqu’un utilisateur se trouve dans un point ciblé (appels passifs). Cette mise à jour permet également à la création de règles de déclencher les appels de suivi Analytics directement à l’entrée ou à la sortie du point ciblé (appels Principaux).
