---
title: Service de test et de validation des emplacements
description: Cette section fournit des informations sur la façon dont vous pouvez tester et valider le service Places.
translation-type: tm+mt
source-git-commit: 954bd9a12ede841d189138dfbe3d65ad4c1bd3c3
workflow-type: tm+mt
source-wordcount: '1735'
ht-degree: 2%

---


# Service Recommendations to test Places {#test-validate-loc-svc}

De nombreux clients et organisations définiront des points d’accès dans le monde entier. Il est donc important de disposer d’un moyen de simuler et de tester l’interaction du service Places avec votre application. Ces informations vous aident à comprendre comment tester et valider les entrées et sorties du service Lieux qui sont correctement déclenchées en fonction des points d’intérêt définis et de l’emplacement actuel d’un utilisateur.

Étant donné que les variables environnementales peuvent être un facteur de précision et de signal de localisation, nous vous recommandons d&#39;abord d&#39;établir des résultats de référence en travaillant localement avec des outils de développement et des entrées de localisation simulées. L’objectif est de vérifier que tous les événements d’emplacement fonctionnent correctement. Une fois les événements d’emplacement correctement validés, les intégrations de solution (par exemple, Analytics, Cible et Campaign) peuvent être testées. Pour aider vos activités de test, vous devez configurer des Webhooks Slack avec un postback et charger des fichiers GPX dans votre environnement de développement individuel.

>[!IMPORTANT]
>
>Ce plan suppose que les points d&#39;accès ont été créés dans l&#39;interface [du service](https://places.adobe.com) Places et que les dernières versions de l&#39;extension Places et de l&#39;extension du moniteur Places sont installées et correctement configurées. Pour plus d’informations, voir [Extension](/help/places-ext-aep-sdks/places-extension/places-extension.md) Places et Extension [](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)Places Monitor.

| Étape  | Description | Résultat attendu |
|--- |--- |--- |
| 1 | Confirmez que les clés de manifeste appropriées ont été saisies pour Android afin d’accorder l’accès à l’emplacement de suivi. Pour plus d’informations, voir [Ajouter les autorisations d’accès au manifeste](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest). | Confirmé |
| 1a | Vérifiez que les mises à jour de l’emplacement sont configurées dans iOS. Assurez-vous également que vous disposez des clés de liste appropriées configurées dans iOS pour demander à l’utilisateur l’autorisation d’effectuer le suivi de l’emplacement. Pour plus d’informations, voir [Activation des mises à jour d’emplacement en arrière-plan.](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | Confirmé |
| 2 | Vérifiez quel mode de surveillance est défini pour iOS. Le mode continu permet une plus grande précision et une plus grande persistance, mais aussi une plus grande perte de vie de la batterie. Pour plus d’informations, voir Mode de [surveillance (iOS uniquement).](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | Changements importants ou continus |
| 3 | Si vous utilisez plusieurs bibliothèques d’objets d’intérêt, vérifiez que les bibliothèques appropriées ont été sélectionnées dans l’extension Places pour Experience Platform Launch. | Confirmé |
| 4 | Vérifiez que les dernières versions des extensions Mobile Core et Places/Places Monitor ont été fournies avec l&#39;application via Gradle ou CocoaPods. | Confirmé : pour plus d&#39;informations sur les mises à jour récentes, consultez les notes de [mise à jour.](/help/release-notes.md) |
| 5 | Vérifiez que les environnements appropriés sont configurés pour le test. L’ID d’environnement de lancement doit correspondre à votre environnement de développement de lancement. | Confirmé |
| 6 | Créez des fichiers GPX pour chaque point d’intérêt à tester. Les fichiers GPX peuvent être utilisés dans l’environnement de développement local pour simuler une entrée d’emplacement. Pour plus d’informations sur la création et l’utilisation de fichiers GPX, voir ce qui suit : <br>[Fichiers GPX pour le simulateur iOS [fermée]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.](https://mapstogpx.com/mobiledev.php)<br>[phpLOCATION TESTING IN MOBILE APPS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | Les fichiers GPX sont créés et chargés dans le projet d’application. |
| 7 | Sans rien faire d’autre, vous devriez être en mesure de lancer l’application à partir d’Android Studio ou XCode et de voir l’alerte appropriée pour demander l’accès à l’emplacement de suivi. Cliquez sur l’autorisation *Toujours autoriser* .<br><br>Nous vous recommandons d&#39;utiliser un périphérique réel connecté à votre ordinateur plutôt que d&#39;utiliser un simulateur de périphérique. | L&#39;invite de demande d&#39;emplacement doit s&#39;afficher sur l&#39;application chargée via IDE |
| 8 | Une fois l’autorisation d’emplacement acceptée. Le SDK Places va récupérer l&#39;emplacement actuel du périphérique et l&#39;extension Places Monitor va début la surveillance des 20 points d&#39;intérêt les plus proches de l&#39;emplacement actuel. | Consultez l’exemple de journal sous le tableau. |
| 9 | Le passage d’un emplacement à un autre dans XCode ou Android studio devrait produire des événements d’entrée pour des points d’intérêt spécifiques. Les journaux ci-dessous sont attendus à l’entrée d’un point d’intérêt. | Consultez l’exemple de journal sous le tableau. |
| 10 | Une fois que vous avez vu le moniteur des emplacements trouver des points d’intérêt proches, vous devez effectuer un test en envoyant des pings d’emplacement. Dans Lancer, créez une règle qui utilise l’extension Lieux pour se déclencher en fonction d’une entrée de géolocalisation. Créez ensuite une nouvelle action en utilisant Mobile Core pour envoyer un postback. La création d’une application Slack Webhook vous permet de voir les entrées et les sorties d’emplacement. Pour plus d&#39;informations sur la création d&#39;une application Slack Webhook, consultez [Envoi de messages à l&#39;aide de hameçons Web entrants.](https://api.slack.com/messaging/webhooks) |  |
| 10a | Dans Lancement, veillez à ajouter des éléments de données pour l’extension Places, notamment : <br><br>Nom actuel de l&#39;API<br>actuel de l&#39;API en<br>dernier<br>nomDernière entréeDernière entrée<br>Dernière entrée<br><br>longueDernière sortie NomDernière sortie DernièreDernière sortie long Horodatage<br><br> |  |
| 10b | Créer une règle avec un Événement = Lieux → Entrer dans le POI |  |
| 10c | Créer une action = Mobile Core → Postback |  |
| 10d | Utilisez l’URL Webhook pour votre application Slack, par exemple, https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD..... |  |
| 10e | Le corps du poste serait semblable à ce qui suit : `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Assurez-vous d’utiliser les éléments de données spécifiques que vous avez créés ici. |  |
| 10f | Assurez-vous de publier toutes les modifications des nouveaux éléments de données et des règles dans Lancement. (Vous devez sélectionner une bibliothèque de développement opérationnelle dans l’angle supérieur droit de l’interface de lancement.) |  |
| 11 | Lancez et testez à nouveau votre application en basculant entre les emplacements GPX dans l&#39;IDE du développeur. | Les notifications des Slack doivent maintenant s’afficher, indiquant les entrées pour chaque point d’intérêt, lorsque vous sélectionnez différents emplacements dans votre environnement de développement. |
|  | **SOMMAIRE RAPIDE**<br> POINTAtous ces essais peuvent être effectués localement sans avoir à se rendre à un endroit précis de l&#39;IPE. Les tests de validation permettent de s’assurer que votre application est correctement configurée et a reçu les autorisations appropriées pour l’emplacement. <br><br>Cette validation vous permet également de vous assurer que les points d’intérêt définis fonctionnent correctement avec l’extension d’écran des emplacements.  Après cette étape, nous allons commencer à tester les messages dans Campaign pour voir si les messages appropriés s&#39;affichent en fonction des entrées et sorties d&#39;API. |  |
|  | **Test de la messagerie intégrée Adobe Campaign Standard avec le service Places.** |  |
| 12 | Sur le tableau de bord Campaign principal, configurez un nouveau message intégré (type = diffusion). |  |
| 12a | Dans les déclencheurs, sélectionnez **Lieux type d&#39;événement - Entrée comme déclencheur**. |  |
| 12b | Sélectionnez **[!UICONTROL Places Custom metadata]** comme filtre supplémentaire - utilisez le type POI = Dernier POI saisi.<br>Nous utilisons **[!UICONTROL Last Entered]** comme type de point d’accès car, dans la plupart des cas, **[!UICONTROL Last Entered]** il sera identique à **[!UICONTROL Current POI]**. <br><br>**[!UICONTROL Current POI]**ne doit être utilisée que dans les cas où des clôtures de point d’accès se chevauchent. Dans ce cas, ces points d’intérêt doivent être classés et le **[!UICONTROL Current POI]**premier affichera le point d’intérêt le mieux classé parmi les 2 ou 3 clôtures géographiques dans lesquelles un utilisateur peut se trouver actuellement. |  |
| 12c | Sélectionnez une clé de métadonnées personnalisée qui vous aidera à préciser les points de contact qui recevront un message. |  |
| 12d | Pour la fréquence et la durée, restez à un ou deux jours, de sorte que si vous n’aimez pas les critères, vous pouvez faire expirer le déclencheur dans un laps de temps plus court. |  |
| 12e | Pour les clics publicitaires Toujours/Une ou Jusqu’à, sélectionnez *TOUJOURS* pour pouvoir tester à plusieurs emplacements. | Un message intégré s’affiche TOUJOURS lorsque vous simulez un changement d’emplacement qui répond aux critères de métadonnées appropriés. |
| 12f | Pour l’affichage, sélectionnez une option autre que Notification locale. Cela facilite l’affichage des tests avec l’application au premier plan.) |  |
| 12g | Préparez/confirmez et déployez le message in-app. |  |
| 13 | Dans votre environnement de développement, pour vous assurer que les nouvelles règles de campagne sont téléchargées, quittez l’application et relancez-la. | N&#39;oubliez pas que les applications doivent être entièrement relancées pour que le nouveau fichier de règles Campaign soit téléchargé sur le périphérique. |
| 14 | Dans votre application de développement, changez d’emplacement en utilisant les fichiers GPX précédemment créés. | Le message in-app doit s’afficher en fonction des critères définis précédemment. |
| 15 | Pour le prochain test, nous copierons essentiellement les mêmes étapes qu&#39;avant, mais cette fois nous testerons la NOTIFICATION LOCALE. | Le résultat attendu est que les notifications locales s’affichent chaque fois que les critères correspondants sont satisfaits. |
| 16 | Configurez un nouveau message intégré (type = diffusion). |  |
| 16a | Dans les déclencheurs, sélectionnez **[!UICONTROL Places event type]** - **[!UICONTROL Entry as the trigger]**. |  |
| 16b | Sélectionnez Places Custom metadata comme filtre supplémentaire - utilisez **[!UICONTROL POI type]** = **[!UICONTROL Last Entered POI]**. |  |
| 16c | Sélectionnez une clé de métadonnées personnalisée qui vous aidera à préciser les points de contact qui recevront un message. |  |
| 16d | Pour la fréquence et la durée, ne conservez qu’un ou deux jours, de sorte que si vous n’aimez pas les critères, vous pouvez faire expirer le déclencheur dans un laps de temps plus court. |  |
| 16e | Pour Toujours/Une ou Jusqu&#39;au clic publicitaire, **[!UICONTROL ALWAYS]**. |  |
| 16f | Pour le type d’affichage, sélectionnez **[!UICONTROL Local Notification]**. |  |
| 16g | Préparez/confirmez et déployez le message in-app. |  |
| 17 | Dans l’environnement développeur, connectez votre périphérique et appuyez sur **[!UICONTROL Play]** la compilation. Une fois que vous avez établi que l’emplacement fonctionne, mettez l’application en arrière-plan et continuez à changer d’emplacement dans Xcode ou Android Studio. Les lectures de la console indiquent toujours le changement d’emplacement et les notifications locales s’affichent en fonction des critères définis dans votre trigger. (Il peut y avoir un retard de 1 à 2 secondes.) | Le résultat attendu est que les notifications locales s’affichent chaque fois que les critères correspondants sont satisfaits. |
|  | **RÉSUMÉ POINT** <br>À ce stade, nous devrions voir des entrées d&#39;IPE dans notre environnement local. Nous devrions également voir les messages de Campaign basés sur le travail de l&#39;API. En cas d’échec, vérifiez si une notification de Slack n’a pas été envoyée. S’il n’y a pas de message de Slack, vérifiez la console de l’application, car une nouvelle entrée d’emplacement n’a peut-être pas été enregistrée. Si les résultats sont réussis, nous pouvons être sûrs que l&#39;application fonctionne correctement et que le service de messagerie Places et Campaign fonctionne également correctement. |  |
|  | **TEST** SUR PLACE <br>Pas grand chose ne devrait changer lors des tests sur place. Le maintien de la principale de postback de la barre oblique devrait aider à déterminer si l&#39;appareil obtient une entrée et une sortie pour l&#39;emplacement. |  |
| 18 | Effectuez des tests avec les périphériques commençant par le wifi et les appareils cellulaires désactivés, puis activez-les une fois dans la région POI. | En cas d’échec, notez si vous recevez une entrée et une notification de géolocalisation en Slack. Quel est l’horodatage de la notification du Slack ? |
| 19 | Exécutez le test avec uniquement les téléphones cellulaires activés et le wifi désactivé. |  |
| 20 | Effectuer un test avec les téléphones cellulaires et le Wi-Fi activés. |  |
|  | **SYNTHÈSE Les tests** <br>sur site devraient correspondre étroitement aux tests de développement. Gardez à l’esprit que certains facteurs environnementaux peuvent jouer un rôle dans la détermination de l’emplacement d’un utilisateur, comme la durée de la visite d’une clôture d’accès aux ordinateurs, la disponibilité du signal cellulaire et la force des points d’accès Wi-Fi à proximité. |  |

## Exemples de journaux

**Étape 8 :** Journaux iOS et Android prévus lors d’une mise à jour d’emplacement

**iOS**

```
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Authorization status changed: Always
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Received a new list of POIs from Places: (
<ACPPlacePoi: 0x600002b75a40> Name: <poi name>; ID:<poi id>; Center: (<lat>, <long>); Radius: <radius>
..
..)   
```

**Android**

```
PlacesMonitor - All location settings are satisfied to monitor location
PlacesMonitor - PlacesMonitorInternal : New location obtained: <latitude> <longitude> Attempting to get the near by pois
PlacesExtension - Dispatching nearby places event with n POIs
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
...
...
PlacesMonitor - Successfully added n fences for monitoring
```

**Étape 9 :** Journaux iOS et Android prévus pendant un événement

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
