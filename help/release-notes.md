---
title: Notes de mise à jour
description: Notes de mise à jour du service Places.
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
TQID: https://experienceleague.adobe.com/yo1eXPl9cKbp-EVWQT8gZHcAbSDoIFJVD6xKbdoysMc
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
feature_v2: id: b069d60e-95f3-44d6-95a8-ddc862a4bc38id: bef6f891-2e8a-425e-8f99-7ddf22070daaid: d833d0ef-8ed5-4cff-a5e7-9f12abd02a31id: e08599ea-8888-4294-ba74-3ba0a7762a46id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: d3cdead0-685a-4489-9250-4bb709942f66id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 1612
ht-degree: 5%

---

# Notes de mise à jour {#release-notes}

## 8 juillet 2020

* **Extensions Places et Places Monitor**

   * Les extensions Places et Places Monitor ont été ajoutées pour les applications [](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Des extensions Places et Places Monitor ont été ajoutées pour les applications [Cordova](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Pour plus d’informations, voir : [Utilisation de l’extension Places](https://experienceleague.adobe.com/docs/places/using/places-ext-aep-sdks/places-extension/places-extension.html?lang=fr)


## 12 Mai 2020

* **Places Service**

   * Importer en bloc des POI à partir d’un fichier CSV à l’aide du bouton Importer des POI
   * Sélection de plusieurs points d’intérêt et modification ou ajout en bloc de valeurs de métadonnées

## 6 Mai 2020

* **PlacesMonitor 2.2.1**

   * **Android**

      * Journalisation améliorée

## 5 Mai 2020


* **PlacesMonitor 2.1.3**

   * **iOS**

      * Journalisation améliorée

## 20 Février 2020

* **ACPPlaces 1.3.1 (iOS)**

   * L’extension Places signale désormais les informations de version au hub d’événements dans Core SDK.
   * Les informations d’appartenance au point d’intérêt de l’appareil ont désormais une durée de vie par défaut d’une heure à compter du moment où elles sont collectées. Pour plus d&#39;informations, voir [Modification de la durée de vie de l&#39;abonnement aux Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1 (Android)**

   * L’extension Places signale désormais les informations de version au hub d’événements dans Core SDK.
   * Les informations d’appartenance au point d’intérêt de l’appareil ont désormais une durée de vie par défaut d’une heure à compter du moment où elles sont collectées. Pour plus d&#39;informations, voir [Modification de la durée de vie de l&#39;abonnement aux Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## mardi 27 janvier 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Appelez la nouvelle API Places pour collecter le statut d’autorisation de l’emplacement au lancement de l’application et lorsque l’autorisation est modifiée pendant l’exécution de l’application.
      * Ajout de l’API setRequestLocationPermission et API setLocationPermission obsolète.

## 9 janvier 2020

* **Places 1.4.0**

   * **Android**

      * Ajout d’une nouvelle API, `setAuthorizationStatus`, pour définir le statut d’autorisation des appareils pour Places Services. La valeur est stockée et utilisée dans l&#39;état Places partagées .

## jeudi 4 décembre 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Appelez l’API Places pour collecter CLAuthorizationStatus sur l’appareil lorsqu’il change.

## mercredi 3 décembre 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * Ajout d’une nouvelle API, `setAuthorizationStatus`, pour définir le statut d’autorisation des appareils pour Places Services. La valeur est stockée et utilisée dans l&#39;état Places partagées .

## mardi 25 novembre 2019

* **PlacesMonitor 2.1.1**

   * **iOS**

      * Correction des instructions d’importation pour les projets Cocoapods à l’aide de plusieurs projets de capsule.

## samedi 22 novembre 2019

* **PlacesMonitor 2.1.1**

   * **Android**

      * Le moniteur reconnaît désormais le démarrage d’un périphérique Android et, si nécessaire, enregistre à nouveau les barrières géographiques auprès du système d’exploitation en fonction de l’emplacement actuel du périphérique.
      * Correction d’une condition de concurrence qui entraînait parfois l’abandon d’événements d’entrée/sortie.

## jeudi 9 octobre 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Ajout d’une nouvelle API, `setRequestAuthorizationLevel`, pour définir le type de demande d’autorisation d’emplacement pour laquelle l’utilisateur sera invité.


   * **Android**

      * Ajout d’une nouvelle API, `setLocationPermission`, pour définir le type de demande d’autorisation d’emplacement pour laquelle l’utilisateur sera invité.
      * Places Monitor prend désormais en charge Android 10.

## 8 Août 2019

Les mises à jour suivantes ont été apportées à cette version :

### Mises à jour des interfaces utilisateur

Voici une liste des mises à jour de l’interface utilisateur Places :

#### Nouvelles fonctionnalités

* Ajout d’une nouvelle vue Liste qui affiche les points d’intérêt sans mappage.
* Ajout d’options de filtrage des points d’intérêt pour la ville, l’État, le pays et les métadonnées.
* La première bibliothèque d’une organisation est automatiquement créée.
* Ajout du tri des points d’intérêt à la vue Liste.

#### Mises à jour des interfaces utilisateur

* Déplacement du panneau Liste et détails vers la droite de l’interface utilisateur.
* Ajout d’un nouveau panneau de recherche en haut de l’interface utilisateur.
* Si une seule bibliothèque est présente, elle est automatiquement sélectionnée lorsque vous créez un point d’intérêt.
* Déplacement de la gestion des bibliothèques dans une fenêtre contextuelle.
* Ajout d’un nombre de points d’intérêt en regard des filtres.

## 6 Août 2019

Les mises à jour suivantes ont été apportées à cette version :

### Extension Monitor Launch 2.0.0

* Mise à jour des instructions d’installation d’Android et d’iOS pour Places Monitor 2.0.

## 31 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

### Places Monitor 2.0.0

* Le statut de surveillance est désormais conservé entre les lancements.
* La gestion du rappel, qui a résulté d&#39;une demande d&#39;autorisation d&#39;emplacement, ne nécessite plus que vous étendiez PlacesActivity.
* Modification d’une API existante, permettant aux développeurs d’effacer toutes les données Places de l’appareil :

  Ancienne API : `public static void stop();`

  Nouvelle API : `public static void stop (final boolean clearData);`

* Mise à jour de l’utilisation de l’API `getNearbyPointsOfInterest` pour gérer plus efficacement les scénarios d’erreur.

## 25 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

### ACPPlacesMonitor 2.0.0

* Pour effacer toutes les données Places de l&#39;appareil,

  dans ACPPlacesMonitor, a remplacé un `+ (void) stop;` d&#39;API existant par `+ (void) stop: (BOOL) clearData;`.

* Mise à jour de l’utilisation de l’API `getNearbyPointsOfInterest` ACPPlaces pour gérer plus efficacement les scénarios d’erreur.

## mardi 22 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

### Android Places 1.3.0

* Ajout d’une nouvelle API qui efface toutes les données liées à Places des états partagés, de la mémoire in-app et des préférences partagées.
* Correction d’un problème en raison duquel l’état partagé n’était pas mis à jour au démarrage de l’application.
* Correction d’un bug en raison duquel `getNearbyPointsOfInterest` rappel renvoyait le code d’erreur `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` sur Internet.
* `getNearbyPointsOfInterest`’API (sans errorCallback) verra le `successCallback` appelé avec une liste de points d’intérêt vide, en cas d’erreur de récupération des points d’intérêt à proximité.

## samedi 19 juillet 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places 1.2.0**

Ajout d’une nouvelle API qui efface toutes les données liées à Places des états partagés, de la mémoire in-app et des `NSUserDefaults`.

## 25 juin 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places Monitor 1.0.2**

* Améliorations de la qualité de vie, notamment une meilleure documentation et une meilleure journalisation dans le code.

## 17 Juin 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places 1.1.0**

* Ajout d’une nouvelle API pour renvoyer un code d’erreur en cas d’échec de la récupération des emplacements voisins.
* Lorsque le statut de confidentialité passe à opt-out, toutes les données liées à Places sont désormais effacées de l&#39;appareil.
* Correction d’un problème qui, après un premier lancement, entraînait parfois la perte d’événements Places en raison de mauvaises conditions réseau.
* Correction d’un problème en raison duquel, lors du traitement d’événements d’entrée de point d’intérêt en succession rapide, le remplacement de jeton via le moteur de règles référençait parfois le point d’intérêt incorrect.

## 30 mai 2019

**Android Places Monitor 1.0.1**

* Correction d’un problème qui empêchait l’apparition d’un événement d’entrée pour les points d’intérêt lorsque la surveillance Places était lancée.

## 28 mai 2019

Correction des problèmes suivants dans l’interface utilisateur de Places :

* Mise à jour du sélecteur de solutions dans Places pour s’aligner sur le reste d’Experience Cloud.
* Correction d’un problème en raison duquel le classement était enregistré dans les instances où aucun changement de classement n’était effectué.
* Augmentation du rayon minimum autorisé dans l’interface utilisateur à 10 mètres.
* Correction d’un problème en raison duquel, si vous supprimez tous les nombres du champ, le champ Rayon était réinitialisé à 20 mètres.

## 17 mai 2019

Les mises à jour suivantes ont été apportées à cette version :

**Android Places 1.2.0**

* Ajout d’une nouvelle API pour le traitement d’une limite géographique individuelle.
* Correction de bugs pour empêcher plusieurs événements d’entrée consécutifs.

**Android Places Monitor 1.0.0**

Version initiale de Places Monitor pour Android.

Places Monitor gère les API de localisation au niveau du système d&#39;exploitation et communique directement avec l&#39;extension Places. Une fois les deux extensions installées, les clients peuvent disposer d’une surveillance de zone géographique prête à l’emploi dans leur application.
Pour plus d&#39;informations sur Places Monitor, cliquez ici.


## 2 Mai 2019

**Android Places 1.1.0**

* Ajout d&#39;une nouvelle API pour getNearByPlaces, qui a un errorCallback et est appelée avec un errorCode qui indique la raison de l&#39;erreur.
* L’extension Places met désormais les événements en file d’attente jusqu’à ce qu’une configuration soit obtenue.
* Ajout de la prise en charge des configurations tenant compte de l’environnement.
* Correction de bug : correction des clés pour les événements d’entrée/sortie de région
* Le stockage du dernier emplacement connu respecte désormais correctement le statut de confidentialité de l’utilisateur


## 9 avril 2019

Les mises à jour suivantes ont été apportées à cette version :

**iOS Places Monitor 1.0.1**

* Ajout de la couverture de test unitaire complète.
* Intégration d’un CI (CircleCI)
* Intégration de la couverture de code (codecov)

## mardi 25 mars 2019

iOS Places Monitor 1.0.0

Version initiale de Places Monitor pour iOS.

Places Monitor gère les API de localisation au niveau du système d&#39;exploitation et communique directement avec l&#39;extension Places. Une fois les deux extensions installées, les clients peuvent disposer d’une surveillance de zone géographique prête à l’emploi dans leur application.

## 28 février 2019

### Version de Beta

Il s&#39;agit de la première version de Places Service, un ensemble d&#39;outils qui permet aux clients d&#39;enrichir les expériences de leurs utilisateurs avec des données de localisation du monde réel. Pour la première version, notre principal cas d’utilisation consiste à permettre aux applications mobiles de récupérer des données de localisation personnalisées et d’agir sur ces données via Adobe Experience Platform Launch.

### Principales fonctionnalités

Les fonctionnalités clés de cette version sont les suivantes :

#### Interface utilisateur du service Places

Nous avons publié une interface utilisateur de gestion dans laquelle vous pouvez afficher et gérer vos points ciblés. Vous pouvez également organiser vos points d’intérêt en bibliothèques. Outre les métadonnées standard telles que la ville, l’État et la catégorie, nous prenons également en charge la possibilité d’ajouter des métadonnées personnalisées à vos points d’intérêt.

* Pour afficher l’interface utilisateur, accédez à [](https://places.adobe.com).
* Pour commencer à utiliser l’interface utilisateur, voir [Prise en main](/help/getting-started.md).

#### Extension Places

À l’aide de l’extension Places, vous pouvez ajouter vos bibliothèques Places Service à votre application mobile et agir sur leurs points d’intérêt. À l’aide du créateur de règles d’Experience Platform Launch, vous pouvez déclencher des actions à déclencher lorsque les utilisateurs accèdent aux points d’intérêt et en sortent.

Dans l’extension Places :

* Vous pouvez choisir les bibliothèques de points d’intérêt à inclure dans votre application.
* Événements de règle qui se déclenchent à l’entrée ou à la sortie d’un point d’intérêt.
* Créez des éléments de données qui pointent vers le point d’intérêt actuel de l’utilisateur.

Pour plus d’informations sur l’extension Places, voir [Extension Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### API Places

Vous pouvez utiliser les API Places pour effectuer les opérations suivantes :

* Autoriser les développeurs à renseigner et mettre à jour leur liste de points d’intérêt.
* Créez votre propre interface utilisateur ou intégrez-la à une base de données de points d’intérêt existante.
* Utilisez les points d’entrée par lot de l’API Places pour importer en bloc des points d’intérêt.

  Vous pouvez utiliser l’utilitaire Python fourni pour terminer l’importation en bloc.

Pour plus d’informations sur les API Places, voir [API de service web](/help/web-service-api/places-web-services.md).

### Bientôt disponible

#### Intégration d’Analytics

L’extension Analytics est mise à jour afin d’ajouter automatiquement des données contextuelles d’emplacement de votre base de données Places Service à tous les appels Analytics sortants lorsqu’un utilisateur se trouve dans un point d’intérêt (appels passifs). Cette mise à jour permet également la création de règles pour déclencher les appels de suivi Analytics directement à l’entrée ou à la sortie du point d’intérêt (appels actifs).
