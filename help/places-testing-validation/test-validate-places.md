---
title: Test et validation du service Places
description: Cette section fournit des informations sur la manière dont vous pouvez tester et valider Places Service.
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
TQID: https://experienceleague.adobe.com/nO4tOQW9rp3zjkHT6aJ5IcXHcD9heOaRAJiEchiz1Fk
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1id: dfc56824-e8b9-499e-85d4-21aedb507314id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: c93393a4-e558-47e1-992e-c91ed4d480ceid: d5ef99fa-df0c-4153-bf94-105ad0724167id: daec7ead-f475-492a-a3b3-02ae08565d6fid: e08599ea-8888-4294-ba74-3ba0a7762a46id: eb9732ab-8232-4b21-bc4c-89de86dbe4d7id: ed0d8d0e-04b9-4326-be72-a0fbca265377id: f7c7de77-382f-4f48-8b36-61a170f06d3did: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2: id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 1748
ht-degree: 2%

---

# Recommandations pour tester le service Places {#test-validate-loc-svc}

De nombreux clients et organisations définiront des points d’intérêt dans le monde entier. Il est donc important de pouvoir simuler et tester la manière dont le service Places interagit avec votre application. Ces informations vous aident à comprendre comment tester et valider les entrées et sorties du service Places correctement déclenchées en fonction des points d’intérêt définis et de l’emplacement actuel d’un utilisateur.

Comme les variables environnementales peuvent être un facteur de signal et de précision de l’emplacement, nous vous recommandons d’établir d’abord des résultats de base en travaillant localement avec des outils de développement et des entrées d’emplacement simulées. L’objectif est de vérifier que tous les événements d’emplacement fonctionnent correctement. Une fois les événements d’emplacement correctement validés, les intégrations de solutions (par exemple, Analytics, Target et Campaign) peuvent être testées. Pour faciliter vos activités de test, vous devez configurer les Webhooks Slack avec une publication (postback) et charger les fichiers GPX dans votre environnement de développement individuel.

>[!IMPORTANT]
>
>Ce plan suppose que les points d’intérêt ont été créés dans l’[interface utilisateur du service Places](https://places.adobe.com) et que les dernières versions de l’extension Places sont installées et correctement configurées. Si vous effectuez une surveillance active des zones géographiques, cela suppose également qu’une solution de surveillance des zones géographiques est mise en œuvre. Pour plus d’informations, voir [Extension Places](/help/places-ext-aep-sdks/places-extension/places-extension.md), [Documentation CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) pour iOS ou [Documentation sur l’emplacement Android](https://developer.android.com/training/location/geofencing).

| Étape | Description | Résultat attendu |
|--- |--- |--- |
| 1 | Vérifiez que les clés de manifeste appropriées ont été saisies pour qu’Android accorde l’accès à l’emplacement du suivi. | Confirmé |
| 1 bis | Vérifiez que les mises à jour des emplacements sont configurées dans iOS. Assurez-vous également que vous disposez des clés de liste appropriées configurées dans iOS pour demander l’autorisation à l’utilisateur de suivre l’emplacement. | Confirmé |
| 2 | Vérifiez quel mode de surveillance est défini pour iOS. Le mode continu permet une plus grande précision et une plus grande persistance, mais également une plus grande perte d&#39;autonomie de la batterie. | Changements importants ou continus |
| 3 | Si vous utilisez plusieurs bibliothèques de points d’intérêt, vérifiez que les bibliothèques appropriées ont été sélectionnées dans l’extension Places pour Experience Platform Launch. | Confirmé |
| 4 | Vérifiez que les dernières versions des extensions Mobile Core et Places ont été groupées avec l&#39;application via Gradle ou CocoaPods. | Confirmé - pour plus d’informations sur les mises à jour récentes, consultez les [notes de mise à jour.](/help/release-notes.md) |
| 5 | Vérifiez que les environnements appropriés sont configurés pour les tests. L’identifiant d’environnement Launch doit correspondre à votre environnement de développement Launch. | Confirmé |
| 6 | Créez des fichiers GPX pour chaque point d’intérêt que vous souhaitez tester. Les fichiers GPX peuvent être utilisés dans l’environnement de développement local pour simuler une entrée d’emplacement. Pour plus d’informations sur la création et l’utilisation des fichiers GPX, voir : <br>[Fichiers GPX pour le simulateur iOS [fermé]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[TEST D’EMPLACEMENT DANS LES APPLICATIONS MOBILES](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | Les fichiers GPX sont créés et chargés dans le projet d’application. |
| 7 | Sans rien faire d’autre, vous devriez être en mesure de lancer l’application à partir d’Android Studio ou de XCode et de voir l’alerte appropriée pour demander l’accès à l’emplacement de suivi. Cliquez sur l’autorisation *Toujours autoriser*.<br><br>Nous vous recommandons d’utiliser un appareil réel connecté à votre ordinateur au lieu d’utiliser un simulateur d’appareil. | L’invite de requête d’emplacement doit s’afficher sur l’application chargée via l’IDE |
| 8 | Une fois l’autorisation d’emplacement acceptée. Places SDK doit récupérer l&#39;emplacement actuel de l&#39;appareil et le code de surveillance de la région doit commencer à surveiller les 20 POI les plus proches de l&#39;emplacement actuel | Voir l’exemple de journal sous la table . |
| 9 | Le changement d’emplacement dans XCode ou Android Studio doit produire des événements d’entrée pour des points d’intérêt spécifiques. Les journaux ci-dessous sont attendus lors de l’entrée dans un point d’intérêt. | Voir l’exemple de journal sous la table . |
| 10 | Une fois que le moniteur de région a trouvé les points d’intérêt à proximité, vous devez tester en envoyant des pings vers l’emplacement. Dans Launch, créez une règle qui utilise l’extension Places pour déclencher en fonction d’une entrée de clôture géographique. Créez ensuite une action à l’aide de Mobile Core pour envoyer un postback. La création d’une application Slack Webhook vous permet d’afficher les entrées et les sorties d’emplacement. Pour plus d’informations sur la création d’une application Slack Webhook, voir [Envoi de messages à l’aide de Webhooks entrants.](https://api.slack.com/messaging/webhooks) |  |
| 10 bis | Dans Launch, assurez-vous d’avoir ajouté des éléments de données pour l’extension Places, notamment les éléments suivants : <br>Nom actuel du point d’entrée<br>Dernier point d’entrée actuel lat<br>Dernier point d’entrée actuel long<br><br> Dernier nom entré lat<br>Dernier entré long<br>Dernier sorti<br>Dernier sorti lat<br>Dernier sorti long<br>Horodatage |  |
| 10b | Créez une règle avec un Événement = Emplacements → saisir un point ciblé |  |
| 10 quater | Créer une action = Mobile Core → Postback |  |
| 10 j | Utilisez l’URL Webhook pour votre application Slack, par exemple https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD.... |  |
| 10e | Le corps de la publication serait similaire à : `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Veillez à utiliser les éléments de données spécifiques que vous avez créés ici. |  |
| 10f | Veillez à publier toutes les nouvelles modifications apportées aux éléments de données et aux règles dans Launch. (Vous devez sélectionner une bibliothèque de développement fonctionnelle dans le coin supérieur droit de l’interface de Launch.) |  |
| 11 | Lancez et testez à nouveau votre application en basculant entre les emplacements GPX dans l’IDE de développement. | Vous devriez maintenant voir les notifications Slack affichant les entrées de chaque point d’intérêt lorsque vous sélectionnez différents emplacements dans votre environnement de développement. |
|  | **RÉSUMÉ RAPIDE**<br> Tous ces tests peuvent être effectués localement sans avoir à se rendre à un point d’intérêt spécifique. Les tests de validation permettent de s’assurer que votre application est correctement configurée et a reçu les autorisations appropriées pour l’emplacement. <br><br>Cette validation vous permet également de vous assurer que les points d’intérêt définis fonctionnent correctement avec la mise en œuvre de la surveillance de votre région.  Après cette étape, nous allons commencer à tester la messagerie dans Campaign pour voir si les messages appropriés apparaissent en fonction des entrées et des sorties de POI. |  |
|  | **Test de la messagerie in-app Adobe Campaign Standard avec Places Service.** |  |
| 12 | Configurez un nouveau Message In-App (type = broadcast) dans le tableau de bord principal de Campaign |  |
| 12 bis | Dans Déclencheurs, sélectionnez **Type d’événement Places - Entrée comme déclencheur**. |  |
| 12b | Sélectionnez **[!UICONTROL Emplacements des métadonnées personnalisées]** comme filtre supplémentaire - utilisez le type de point d’intérêt = Dernier point d’intérêt saisi. <br>Nous utilisons **[!UICONTROL Dernière saisie]** comme type de point d’intérêt, car dans la plupart des cas, **[!UICONTROL Dernière saisie]** sera le même que **[!UICONTROL Point d’intérêt actuel]**. Le <br><br>**[!UICONTROL point d’intérêt actuel ]**ne doit être utilisé que dans les instances où les clôtures géographiques des points d’intérêt se chevauchent. Dans ce cas, ces points d’intérêt doivent être CLASSÉS, puis le**[!UICONTROL  point d’intérêt actuel ]**affichera le point d’intérêt le mieux classé parmi les 2 ou 3 clôtures géographiques dans lesquelles un utilisateur peut se trouver actuellement. |  |
| 12c | Sélectionnez une clé de métadonnées personnalisée qui vous aidera à déterminer les points d’intérêt qui recevront un message. |  |
| 12 j | Pour la fréquence et la durée, limitez-les à un ou deux jours. Si les critères ne vous conviennent pas, vous pouvez faire expirer le déclencheur plus rapidement. |  |
| 12e | Pour Toujours/Une ou Jusqu’au clic publicitaire, sélectionnez *TOUJOURS* afin de pouvoir effectuer des tests à plusieurs emplacements. | Un message in-app s’affiche TOUJOURS lorsque vous simulez un changement d’emplacement qui répond aux critères de métadonnées appropriés. |
| 12f | Pour l’affichage, sélectionnez une option autre que Notification locale. Cela facilite la visibilité lors du test avec l’application au premier plan.) |  |
| 12g | Préparez/confirmez et déployez le message in-app. |  |
| 13 | Dans votre environnement de développement, pour vous assurer que les nouvelles règles de campagne sont téléchargées, quittez et relancez l’application. | N’oubliez pas que les applications doivent être complètement relancées pour que le nouveau fichier de règles de Campaign soit téléchargé sur l’appareil. |
| 14 | Dans votre application de développement, changez d’emplacement à l’aide des fichiers GPX créés précédemment. | Le message in-app devrait s’afficher en fonction des critères précédents qui ont été définis. |
| 15 | Pour le test suivant, nous allons copier les mêmes étapes que précédemment, mais cette fois, nous allons tester la NOTIFICATION LOCALE. | Le résultat attendu est que les notifications locales s’affichent chaque fois que les critères correspondants sont remplis. |
| 16 | Configurez un nouveau message In-App (type = broadcast). |  |
| 16 bis | Dans Déclencheurs, sélectionnez **[!UICONTROL Type d’événement Places]** - **[!UICONTROL Entrée comme déclencheur]**. |  |
| 16b | Sélectionnez les Métadonnées personnalisées des emplacements comme filtre supplémentaire. Utilisez **[!UICONTROL Type de point d’intérêt]** = **[!UICONTROL Dernier point d’intérêt saisi]**. |  |
| 16 quater | Sélectionnez une clé de métadonnées personnalisée qui vous aidera à déterminer les points d’intérêt qui recevront un message. |  |
| 16 j | Pour la fréquence et la durée, conservez seulement un ou deux jours. Si les critères ne vous conviennent pas, vous pouvez faire expirer le déclencheur plus rapidement. |  |
| 16 sexies | Pour Toujours/Une ou Jusqu’au clic publicitaire, **[!UICONTROL TOUJOURS]**. |  |
| 16f | Pour le type d’affichage , sélectionnez **[!UICONTROL Notification locale]**. |  |
| 16g | Préparez/confirmez et déployez le message in-app. |  |
| 17 | Dans l’environnement de développement, connectez votre appareil et appuyez sur **[!UICONTROL Lire]** sur la version. Une fois que vous avez établi que cet emplacement fonctionne, placez l’application en arrière-plan et continuez à changer d’emplacement dans Xcode ou Android Studio. Vous devriez toujours voir des lectures de console indiquant le changement d’emplacement, et vous devriez également voir des notifications locales affichées selon les critères définis dans votre déclencheur. (Il peut y avoir un délai de 1 à 2 secondes.) | Le résultat attendu est que des notifications locales s’affichent chaque fois que les critères correspondants sont remplis. |
|  | **POINT DE RÉSUMÉ** <br>À ce stade, nous devrions voir les entrées de point d’intérêt dans notre environnement local. Nous devrions également voir les messages de Campaign basés sur le travail du point d’intérêt. En cas d’échec, vérifiez si une notification Slack n’a pas été envoyée. S’il n’existe aucun message Slack, vérifiez la console de l’application, car il se peut qu’une nouvelle entrée d’emplacement n’ait pas été enregistrée. Si les résultats sont positifs, nous pouvons être à peu près sûrs que l’application fonctionne correctement et que le service Places et le service de messagerie de Campaign fonctionnent également correctement. |  |
|  | **TEST SUR SITE** <br>Peu de choses doivent changer lors du test sur site. Garder le postback slack actif devrait aider à comprendre si l&#39;appareil obtient une entrée et une sortie pour l&#39;emplacement. |  |
| 18 | Effectuez des tests avec les appareils dont le wifi et le cellulaire sont désactivés, puis activez-les une fois dans la région du point d’intérêt. | En cas d’échec, notez si vous obtenez une entrée de clôture géographique et une notification dans Slack. Quelle est la date et l’heure sur la notification Slack ? |
| 19 | Effectuez le test avec seulement le cellulaire activé et le wifi désactivé. |  |
| 20 | Effectuez les tests en utilisant à la fois le réseau cellulaire et le réseau wifi. |  |
|  | **RÉSUMÉ** <br>Les tests sur site doivent correspondre étroitement aux tests de développement. Gardez à l&#39;esprit que certains facteurs environnementaux peuvent entrer en jeu dans la détermination de l&#39;emplacement d&#39;un utilisateur, comme la durée de séjour dans une clôture géographique de point d&#39;intérêt, la disponibilité du signal cellulaire et la force des points d&#39;accès wifi à proximité. |  |

## Exemples de journaux

**Étape 8 :** journaux iOS et Android attendus lors d’une mise à jour de l’emplacement

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**Étape 9 :** journaux iOS et Android attendus lors d’un événement

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
