---
title: Test et validation du service Places
description: Cette section fournit des informations sur la manière dont vous pouvez tester et valider le service Places.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Recommandations pour tester le service Places {#test-validate-loc-svc}

De nombreux clients et organisations définiront des points d’intérêt dans le monde entier. Il est donc important de disposer d’un moyen de simuler et de tester l’interaction du service Places avec votre application. Ces informations vous aident à comprendre comment tester et valider les entrées et sorties du service Places qui sont correctement déclenchées en fonction des points d’intérêt définis et de l’emplacement actuel d’un utilisateur.

Comme les variables environnementales peuvent être un facteur de précision et de signal d’emplacement, nous vous recommandons d’abord d’établir des résultats de base en utilisant localement les outils de développement et les entrées d’emplacement simulées. L’objectif est de vérifier que tous les événements d’emplacement fonctionnent correctement. Une fois les événements d’emplacement correctement validés, les intégrations de solution (par exemple, Analytics, Target et Campaign) peuvent être testées. Pour faciliter vos activités de test, vous devez configurer des hameçons Web Spénurie avec un postback et charger des fichiers GPX dans votre environnement de développement individuel.

>[!IMPORTANT]
>
>Ce plan suppose que les points d’accès ont été créés dans l’interface utilisateur [du service](https://places.adobe.com) Places et que les dernières versions de l’extension Places et de l’extension du moniteur Places sont installées et correctement configurées. Pour plus d’informations, voir [Extension](/help/places-ext-aep-sdks/places-extension/places-extension.md) Places et Extension [du moniteur](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)Places.

| Étape  | Description | Résultat attendu |
|--- |--- |--- |
| 1 | Vérifiez que les clés de manifeste appropriées ont été saisies pour Android afin d’octroyer l’accès à l’emplacement du suivi. Pour plus d’informations, voir [Ajout d’autorisations au manifeste](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest). | Confirmé |
| 1a | Vérifiez que les mises à jour de l’emplacement sont configurées dans iOS. Assurez-vous également que vous disposez des clés de liste appropriées configurées dans iOS pour demander à l’utilisateur l’autorisation de suivre l’emplacement. Pour plus d’informations, voir [Activation des mises à jour d’emplacement en arrière-plan.](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | Confirmé |
| 2 | Vérifiez quel mode de surveillance est défini pour iOS. Le mode continu permet une plus grande précision et une plus grande persistance, mais aussi une plus grande autonomie de la batterie. Pour plus d’informations, voir Mode [de surveillance (iOS uniquement).](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | Changements significatifs ou continus |
| 3 | Si vous utilisez plusieurs bibliothèques d’API, vérifiez que les bibliothèques appropriées ont été sélectionnées dans l’extension Places pour le lancement de la plateforme d’expérience. | Confirmé |
| 4 | Vérifiez que les dernières versions des extensions Mobile Core et Places/Places Monitor ont été intégrées à l’application via Gradle ou CocoaPods. | Confirmé : pour plus d&#39;informations sur les mises à jour récentes, consultez les notes de [mise à jour.](/help/release-notes.md) |
| 5 | Vérifiez que les environnements appropriés sont configurés pour le test. L’ID d’environnement de lancement doit correspondre à l’environnement de développement de lancement. | Confirmé |
| 6 | Créez des fichiers GPX pour chaque point d’intérêt à tester. Les fichiers GPX peuvent être utilisés dans l’environnement de développement local pour simuler une entrée d’emplacement. Pour plus d’informations sur la création et l’utilisation de fichiers GPX, voir : Fichiers <br>[GPX pour le simulateur iOS [fermée]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.](https://mapstogpx.com/mobiledev.php)<br>[phpLOCATION TESTING IN MOBILE APPS (TESTING DANS LES APPLICATIONS MOBILES)](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | Les fichiers GPX sont créés et chargés dans le projet d’application. |
| 7 | Sans rien faire d’autre, vous devez être en mesure de lancer l’application à partir d’Android Studio ou de XCode et de voir l’alerte appropriée pour demander l’accès à l’emplacement de suivi. Cliquez sur l’autorisation *Toujours autoriser* .<br><br>Nous vous recommandons d’utiliser un périphérique réel connecté à votre ordinateur plutôt que d’utiliser un simulateur de périphérique. | L’invite de requête d’emplacement doit s’afficher sur l’application chargée via IDE |
| 8 | Une fois l’autorisation d’emplacement acceptée. Le SDK Places récupère l’emplacement actuel du périphérique et l’extension Places Monitor commence à surveiller les 20 points d’intérêt les plus proches de l’emplacement actuel. | Voir l’exemple de journal sous le tableau. |
| 9 | Le passage d’un emplacement à un autre dans XCode ou Android studio doit générer des événements d’entrée pour des points d’intérêt spécifiques. Les journaux ci-dessous sont attendus à l’entrée d’une API. | Voir l’exemple de journal sous le tableau. |
| 10 | Une fois que vous avez vu le moniteur de lieux trouver des points d’intérêt proches, vous devez effectuer un test en envoyant des pings d’emplacement. Dans Lancer, créez une règle qui utilise l’extension Lieux pour se déclencher en fonction d’une entrée de géolocalisation. Créez ensuite une nouvelle action en utilisant Mobile Core pour envoyer un postback. La création d’une application Sind Webhook vous permet de voir les entrées et les sorties des emplacements. Pour plus d’informations sur la création d’une application Sloss Webhook, voir [Envoi de messages à l’aide de hameçons Web entrants.](https://api.slack.com/messaging/webhooks) |  |
| 10a | Dans Lancer, assurez-vous d’avoir ajouté des éléments de données pour l’extension Places, notamment : <br>Nom<br>actuel de l&#39;APINom actuel de l&#39;API<br>Dernière entrée<br>longueDernière entréeDernière entrée<br>longueDernière entrée<br><br>longueDernière entrée longueDernière sortieDernière sortie latDernière sortie longueHorodatage<br><br><br> |  |
| 10b | Créez une règle avec un événement = Lieux → Entrer dans un point d’intérêt |  |
| 10c | Créer une action = Mobile Core → Postback |  |
| 10d | Utilisez l’URL Webhook pour votre application Slack, par exemple, https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD....... |  |
| 10e | Le corps du poste serait le suivant : `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Veillez à utiliser les éléments de données spécifiques que vous avez créés ici. |  |
| 10f | Assurez-vous de publier toutes les modifications apportées aux nouveaux éléments de données et aux règles dans Lancement. (Vous devez sélectionner une bibliothèque de développement opérationnelle dans l’angle supérieur droit de l’interface de lancement.) |  |
| 11 | Lancez et testez à nouveau votre application en basculant entre les emplacements GPX dans l’IDE du développeur. | Vous devriez maintenant voir les notifications Sless qui affichent les entrées pour chaque point d’accès pendant que vous sélectionnez différents emplacements dans votre environnement de développement. |
|  | **SOMMAIRE RAPIDE**<br> Tous ces tests peuvent être effectués localement sans avoir à se rendre à un endroit spécifique de l&#39;IVP. Les tests de validation permettent de s’assurer que votre application est correctement configurée et a reçu les autorisations appropriées pour l’emplacement. <br><br>Cette validation vous donne également la certitude que les points d’intérêt définis fonctionnent correctement avec l’extension du moniteur de lieux.  Après cette étape, nous allons commencer à tester la messagerie dans Campaign pour voir si les messages appropriés s’affichent en fonction des entrées et des sorties d’API. |  |
|  | **Test de la messagerie intégrée Adobe Campaign Standard avec le service Places.** |  |
| 12 | Sur le tableau de bord de campagne principal, configurez un nouveau message in-app (type = diffusion). |  |
| 12a | Dans les déclencheurs, sélectionnez **Places type d’événement - Entrée comme déclencheur**. |  |
| 12b | Sélectionnez **[UICONTROL place les métadonnées]**personnalisées comme filtre supplémentaire - utilisez le type de point d’entrée = dernier point d’entrée.<br>Nous utilisons**[!UICONTROL Last Entered]** comme type de point d’accès car, dans la plupart des cas, **[!UICONTROL Last Entered]**il s’agit de la même valeur que**[!UICONTROL Current POI]**. <br><br>**[!UICONTROL Current POI]** ne doit être utilisée que dans les cas où des clôtures de point d’entrée se chevauchent. Dans ce cas, ces points d’intérêt doivent être classés, puis le **[!UICONTROL Current POI]**montre les points d’intérêt les plus classés parmi les 2 ou 3 géo-clôtures dans lesquelles un utilisateur peut se trouver actuellement. |  |
| 12c | Sélectionnez une clé de métadonnées personnalisée qui vous aidera à préciser les points de contact qui recevront un message. |  |
| 12d | Pour la fréquence et la durée, ne restez qu’à un ou deux jours, de sorte que si vous n’aimez pas les critères, vous pouvez faire expirer le déclencheur dans un délai plus court. |  |
| 12e | Pour un clic publicitaire Toujours/Une ou Jusqu’à, sélectionnez *TOUJOURS* pour que vous puissiez effectuer un test à plusieurs emplacements. | Un message intégré s’affiche TOUJOURS lorsque vous simulez un changement d’emplacement qui répond aux critères de métadonnées appropriés. |
| 12f | Pour l’affichage, sélectionnez une option autre que Notification locale. Cela facilite l’affichage des tests avec l’application au premier plan.) |  |
| 12g | Préparez/confirmez et déployez le message in-app. |  |
| 13 | Dans votre environnement de développement, pour vous assurer que les nouvelles règles de campagne sont téléchargées, quittez et lancez de nouveau l’application. | N’oubliez pas que les applications doivent être complètement lancées à nouveau pour que le nouveau fichier de règles de campagne soit téléchargé sur le périphérique. |
| 14 | Dans votre application de développement, changez d’emplacement en utilisant les fichiers GPX précédemment créés. | Le message in-app doit s’afficher en fonction des critères définis précédemment. |
| 15 | Pour le prochain test, nous copierons essentiellement les mêmes étapes qu&#39;avant, mais cette fois nous testerons la NOTIFICATION LOCALE. | Le résultat attendu est que les notifications locales sont affichées chaque fois que les critères correspondants sont satisfaits. |
| 16 | Configurez un nouveau message intégré (type = diffusion). |  |
| 16a | Dans les déclencheurs, sélectionnez **[!UICONTROL Places event type]**-**[!UICONTROL Entry as the trigger]**. |  |
| 16b | Sélectionnez Places Custom metadata comme filtre supplémentaire - use **[!UICONTROL POI type]**=**[!UICONTROL Last Entered POI]**. |  |
| 16c | Sélectionnez une clé de métadonnées personnalisée qui vous aidera à préciser les points de contact qui recevront un message. |  |
| 16d | Pour la fréquence et la durée, ne conservez qu’un ou deux jours, de sorte que si vous n’aimez pas les critères, vous pouvez faire expirer le déclencheur dans un délai plus court. |  |
| 16e | Pour Toujours/Une ou Jusqu’au clic publicitaire, **[!UICONTROL ALWAYS]**. |  |
| 16f | Pour le type d’affichage, sélectionnez **[!UICONTROL Local Notification]**. |  |
| 16g | Préparez/confirmez et déployez le message in-app. |  |
| 17 | Dans l’environnement du développeur, connectez votre périphérique et appuyez sur **[!UICONTROL Play]**la compilation. Une fois que vous avez établi que l’emplacement fonctionne, mettez l’application en arrière-plan et continuez à changer d’emplacement dans Xcode ou Android Studio. Les lectures de la console indiquent toujours le changement d’emplacement et les notifications locales s’affichent en fonction des critères définis dans votre déclencheur. (Il peut y avoir un délai de 1 à 2 secondes.) | Le résultat attendu est que les notifications locales sont affichées chaque fois que les critères correspondants sont satisfaits. |
|  | **SOMMAIRE POINT** À <br>ce stade, nous devrions voir des entrées d’IPE dans notre environnement local. Nous devrions également voir les messages de la campagne basés sur le travail de l’API. En cas d’échec, vérifiez si une notification SBlack n’est pas sortie. S’il n’y a pas de message de panne, vérifiez la console d’application, car une nouvelle entrée d’emplacement n’a peut-être pas été enregistrée. Si les résultats sont réussis, nous pouvons être sûrs que l&#39;application fonctionne correctement et que le service Places et le service de messagerie Campaign fonctionnent également correctement. |  |
|  | **TEST** SUR LE SITE <br>Pas grand chose ne devrait changer lors des tests sur place. Le fait de maintenir la barre oblique postback active devrait aider à comprendre si le périphérique obtient une entrée et une sortie pour l’emplacement. |  |
| 18 | Effectuez des tests avec les périphériques commençant par le wifi et les appareils cellulaires désactivés, puis activez-les une fois dans la région de l’API. | En cas d’échec, notez si vous recevez une entrée et une notification de géolocalisation dans Spénurie. Quel est l’horodatage de la notification Slack ? |
| 19 | Exécutez le test avec uniquement les services cellulaires activés et le wifi désactivé. |  |
| 20 | Effectuez un test avec les fonctions cellulaire et wifi activées. |  |
|  | **SYNTHÈSE Les tests** <br>sur site doivent correspondre étroitement aux tests de développement. Gardez à l’esprit que certains facteurs environnementaux peuvent jouer un rôle dans la détermination de l’emplacement d’un utilisateur, comme la durée de consultation d’une clôture d’accès Internet, la disponibilité du signal cellulaire et la puissance des points d’accès Wi-Fi à proximité. |  |

## Exemples de journaux

**** Étape 8 : Journaux iOS et Android prévus lors d’une mise à jour d’emplacement

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

**** Étape 9 : Journaux iOS et Android prévus pendant un événement

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
