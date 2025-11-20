---
audience: end-user
user-guide-title: Guide de Places Service
user-guide-description: Places Service est un service de géolocalisation qui permet aux applications mobiles dotées de géolocalisation de comprendre le contexte de la localisation.
feature: Places
source-git-commit: 9f2c6fee6e0d6d075b662cc0b6cbee49cf05ee55
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 18%

---


# Places Service {#using}

+ [Présentation du service Places](home.md)
+ [Notes de mise à jour](release-notes.md)
+ [Commencer](getting-started.md)
+ [Accéder au service Places](places-gain-access.md)
+ Interface utilisateur du service Places {#poi-mgmt-ui}
   + [Présentation de l’interface utilisateur du service Places](poi-mgmt-ui/poi-mgmt-ui-overview.md)
   + [Créer un point d’intérêt](poi-mgmt-ui/create-a-poi-ui.md)
   + [Gérer les POI créés précédemment](poi-mgmt-ui/managing-pois-in-the-places-ui.md)
   + [Stratégies d’utilisation des métadonnées avec les points d’intérêt](poi-mgmt-ui/metadata-with-pois.md)
   + [Chargement en masse des points d’intérêt](poi-mgmt-ui/bulk-upload-pois.md)
   + [Gestion de plusieurs bibliothèques](poi-mgmt-ui/manage-libraries-in-the-places-ui.md)
+ API de service web {#web-service-api}
   + [Présentation de l’API de service web](web-service-api/places-web-services.md)
   + [Conditions préalables à l’intégration](web-service-api/adobe-i-o-integration.md)
   + Utilisation de l’API {#api-usage}
      + [Vue d’ensemble de l’utilisation de l’API](web-service-api/api-usage/api-usage-overview.md)
      + [En-têtes et paramètres](web-service-api/api-usage/headers-and-parameters.md)
      + Gestion des bibliothèques {#manage-libraries}
         + [Présentation de la gestion des bibliothèques](web-service-api/api-usage/manage-libraries/manage-libraries.md)
         + [créer une bibliothèque ;](web-service-api/api-usage/manage-libraries/create-a-library.md)
         + [Lire une bibliothèque](web-service-api/api-usage/manage-libraries/read-a-library.md)
         + [Mise à jour d’une bibliothèque](web-service-api/api-usage/manage-libraries/update-a-library.md)
         + [Suppression d’une bibliothèque](web-service-api/api-usage/manage-libraries/delete-a-library.md)
         + [Lire toutes les bibliothèques de votre organisation](web-service-api/api-usage/manage-libraries/read-all-libraries-in-your-organization.md)
         + [Définition d’un classement sur vos bibliothèques](web-service-api/api-usage/manage-libraries/set-a-ran-on-your-libraries.md)
         + [Obtenir le rang d&#39;une bibliothèque](web-service-api/api-usage/manage-libraries/get-a-librarys-rank.md)
      + Gestion des points ciblés {#manage-pois}
         + [Présentation de la gestion des points d’intérêt](web-service-api/api-usage/manage-pois/manage-pois.md)
         + [Créer un point d’intérêt](web-service-api/api-usage/manage-pois/create-a-poi.md)
         + [Lire un point d’intérêt](web-service-api/api-usage/manage-pois/read-a-poi.md)
         + [Mettre à jour un point d’intérêt](web-service-api/api-usage/manage-pois/update-a-poi.md)
         + [Supprimer un point d’intérêt](web-service-api/api-usage/manage-pois/delete-a-poi.md)
         + [Lire tous les POI d’une bibliothèque](web-service-api/api-usage/manage-pois/read-all-pois-in-a-library.md)
         + [Lire tous les points d’intérêt de votre organisation](web-service-api/api-usage/manage-pois/read-all-pois-in-your-organization.md)
         + API Batch {#batch-apis}
            + [Présentation des API Batch](web-service-api/api-usage/manage-pois/batch-apis/batch-apis.md)
            + [Création de plusieurs points d’intérêt](web-service-api/api-usage/manage-pois/batch-apis/create-multiple-pois.md)
            + [Mettre à jour plusieurs points d’intérêt](web-service-api/api-usage/manage-pois/batch-apis/update-multiple-pois.md)
            + [Supprimer plusieurs points d’intérêt](web-service-api/api-usage/manage-pois/batch-apis/delete-multiple-pois.md)
      + [API de requête](web-service-api/api-usage/query-apis.md)
+ Extensions pour les SDK mobiles {#places-ext-aep-sdks}
   + [Extension Places](places-ext-aep-sdks/places-extension/places-extension.md)
+ [Utilisation de Places Service avec votre propre solution de surveillance](using-your-own-monitor.md)
+ [Utilisation du service Places sans surveillance active des régions](use-places-without-active-monitoring.md)
+ Utilisation du service Places dans le cadre du workflow Experience Platform Launch {#use-places-launch-workflow}
   + [Utilisation du service Places dans le cadre du workflow Experience Platform Launch](use-places-launch-workflow/places-launch-workflow.md)
   + [Définition des éléments de données](use-places-launch-workflow/define-data-elements.md)
   + [Créer des règles d’entrée et de sortie](use-places-launch-workflow/create-rule-places-property.md)
+ Utilisation du service Places avec d’autres solutions Adobe {#use-places-with-other-solutions}
   + Adobe Analytics {#places-adobe-analytics}
      + [Utilisation du service Places avec Adobe Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)
      + [Envoyer les données d’entrée et de sortie de point d’intérêt à Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)
      + [Ajout du contexte d’emplacement aux requêtes Analytics](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)
      + [Rapport sur les données de localisation dans Analytics Workspace](use-places-with-other-solutions/places-adobe-analytics/places-in-workspace.md)
   + Adobe Mobile Services {#places-mobile-svcs-messaging}
      + [Adobe Mobile Services](use-places-with-other-solutions/places-mobile-svcs-for-messaging/use-places-mobie-svcs-messaging.md)
      + [Notifications push](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-push.md)
      + [Notifications In-App](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-inapp.md)
   + Adobe Campaign Standard {#places-acs}
      + [Utilisation du service Places avec Adobe Campaign Standard](use-places-with-other-solutions/places-acs/places-acs-overview.md)
      + [Notifications push](use-places-with-other-solutions/places-acs/places-acs-push-notifications.md)
      + [Messages In-App](use-places-with-other-solutions/places-acs/places-acs-in-app-messages.md)
   + Adobe Target {#places-target}
      + [Utilisation du service Places avec Adobe Target](use-places-with-other-solutions/places-target/places-target.md)
+ Tests et validation {#places-testing-validation}
   + [Test et validation du service Places](places-testing-validation/test-validate-places.md)
+ [Questions fréquentes](places-faqs.md)
