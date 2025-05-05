---
title: Test et validation du service Places
description: Cette section fournit des informations sur la manière dont vous pouvez tester et valider le service Places.
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1704'
ht-degree: 1%

---

# Recommendations pour tester le service Places {#test-validate-loc-svc}

De nombreux clients et organisations définissent des points ciblés à travers le monde. Il est donc important de disposer d’un moyen de simuler et de tester la manière dont le service Places interagit avec votre application. Ces informations vous aident à comprendre comment tester et valider les entrées et les sorties du service Places qui sont correctement déclenchées en fonction des points ciblés définis et de l’emplacement actuel d’un utilisateur.

Puisque les variables environnementales peuvent être un facteur de précision et de signal de localisation, nous vous recommandons d’établir d’abord des résultats de base en travaillant localement avec les outils de développement et les entrées de localisation simulées. L’objectif est de vérifier que tous les événements d’emplacement fonctionnent correctement. Une fois les événements de localisation correctement validés, les intégrations de solutions (par exemple, Analytics, Target et Campaign) peuvent être testées. Pour faciliter vos activités de test, vous devez configurer des webhooks Slack avec un postback et charger des fichiers GPX dans votre environnement de développement individuel.

>[!IMPORTANT]
>
>Ce plan suppose que les points ciblés ont été créés dans l’[interface utilisateur du service Places](https://places.adobe.com) et que les dernières versions de l’extension Places sont installées et correctement configurées. Si vous effectuez une surveillance de région active, une solution de surveillance de région est également mise en oeuvre. Pour plus d’informations, voir [Extension Places](/help/places-ext-aep-sdks/places-extension/places-extension.md), [Documentation CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) pour iOS ou [Documentation de l’emplacement Android](https://developer.android.com/training/location/geofencing).

| Étape | Description | Résultat attendu |
|--- |--- |--- |
| 1 | Vérifiez que les clés de manifeste appropriées ont été saisies pour qu’Android accorde l’accès à l’emplacement de suivi. | Confirmé |
| 1a | Confirmez que les mises à jour de l’emplacement sont configurées dans iOS. Assurez-vous également que vous disposez des clés de liste appropriées configurées dans iOS pour demander l’autorisation à l’utilisateur de suivre l’emplacement. | Confirmé |
| 2 | Vérifiez quel mode de surveillance est défini pour iOS. Le mode continu permet une plus grande précision et une plus grande persistance, mais aussi une plus grande perte d’autonomie de la batterie. | Changements significatifs ou continus |
| 3 | Si vous utilisez plusieurs bibliothèques de points ciblés, vérifiez que les bibliothèques appropriées ont été sélectionnées dans l’extension Places pour Experience Platform Launch. | Confirmé |
| 4 | Vérifiez que les dernières versions des extensions Mobile Core et Places ont été regroupées avec l’application via Gradle ou CocoaPods. | Confirmé - pour plus d’informations sur les mises à jour récentes, voir les [notes de mise à jour.](/help/release-notes.md) |
| 5 | Vérifiez que les environnements appropriés sont configurés pour le test. L’identifiant de l’environnement Launch doit correspondre à votre environnement de développement Launch. | Confirmé |
| 6 | Créez des fichiers GPX pour chaque point ciblé que vous souhaitez tester. Les fichiers GPX peuvent être utilisés dans un environnement de développement local pour simuler une entrée d’emplacement. Pour plus d’informations sur la création et l’utilisation de fichiers GPX, voir : <br>[Fichiers GPX pour le simulateur iOS [fermé]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[TESTS D’EMPLACEMENT DANS LES APPLICATIONS MOBILES](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | Les fichiers GPX sont créés et chargés dans le projet de l’application. |
| 7 | Sans rien faire d’autre, vous devriez être en mesure de lancer l’application à partir d’Android Studio ou de XCode et de voir l’alerte appropriée pour demander l’accès à l’emplacement de suivi. Cliquez sur l’autorisation *Toujours autoriser* .<br><br>Nous vous recommandons d’utiliser un appareil réel connecté à votre ordinateur plutôt que d’utiliser un simulateur d’appareil. | L’invite de requête d’emplacement doit s’afficher sur l’application chargée via IDE |
| 8 | Une fois l’autorisation de localisation acceptée. Le SDK Places doit récupérer l’emplacement actuel de l’appareil et le code de surveillance de région doit commencer à surveiller les 20 points ciblés les plus proches de l’emplacement actuel. | Consultez l’exemple de journal sous le tableau . |
| 9 | Le passage de différents emplacements dans Xcode ou Android Studio doit produire des événements d’entrée pour des points ciblés spécifiques. Les journaux ci-dessous sont attendus lors de l’entrée dans un point ciblé. | Consultez l’exemple de journal sous le tableau . |
| 10 | Une fois que le moniteur de région a trouvé les points ciblés proches, vous devez les tester en envoyant des pings de position. Dans Launch, créez une règle qui utilise l’extension Places à déclencher en fonction d’une entrée de géo-barrière. Créez ensuite une action à l’aide de Mobile Core pour envoyer un postback. La création d’une application Webhook de Slack vous permet d’afficher les entrées et les sorties d’emplacement. Pour plus d&#39;informations sur la création d&#39;une application Webhook pour Slack, voir [Envoi de messages à l&#39;aide de webhooks entrants.](https://api.slack.com/messaging/webhooks) |  |
| 10a | Dans Launch, assurez-vous d’avoir ajouté des éléments de données pour l’extension Places, notamment les éléments suivants : <br>Nom actuel du POI<br>Nom actuel du POI<br>Long actuel du POI<br>Nom du dernier entré<br>Dernier entré lat<br>Dernier entré long<br>Nom de dernière sortie<br>Dernier entré long<br>Date de dernière sortie long<br>Horodateur |  |
| 10b | Créer une règle avec un événement = Places → Entrée dans un point ciblé |  |
| 10c | Créer une action = Mobile Core → Postback |  |
| 10d | Utilisez l’URL de webhook pour votre application de Slack, par exemple https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD..... |  |
| 10e | Le corps de la publication serait similaire à : `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Assurez-vous d’utiliser les éléments de données spécifiques que vous avez créés ici. |  |
| 10f | Assurez-vous de publier toutes les nouvelles modifications apportées aux éléments de données et aux règles dans Launch. (Vous devez sélectionner une bibliothèque de développement opérationnelle en haut à droite de l’interface de Launch.) |  |
| 11 | Lancez et testez à nouveau votre application en basculant entre les emplacements GPX dans l’IDE du développeur. | Les notifications de Slack doivent maintenant apparaître, car vous sélectionnez différents emplacements dans votre environnement de développement pour chaque point ciblé. |
|  | **POINT DE RÉSUMÉ RAPIDE**<br> Tous ces tests peuvent être effectués localement sans avoir à accéder à un emplacement POI spécifique. Les tests de validation permettent de s’assurer que votre application est correctement configurée et a reçu les autorisations appropriées pour l’emplacement. <br><br>Cette validation vous permet également de vous assurer que les points ciblés définis fonctionnent correctement avec votre implémentation de surveillance de région.  Après cette étape, nous allons commencer à tester les messages dans Campaign pour voir si les messages appropriés s’affichent en fonction des entrées et des sorties du point ciblé. |  |
|  | **Test de la messagerie in-app Adobe Campaign Standard avec le service Places.** |  |
| 12 | Dans le tableau de bord de Campaign principal, configurez un nouveau message In-App (type = diffusion). |  |
| 12a | Dans les déclencheurs, sélectionnez **Type d’événement Places - Entrée comme déclencheur**. |  |
| 12b | Sélectionnez **[!UICONTROL Places de métadonnées personnalisées]** comme filtre supplémentaire - utilisez le type POI = Dernier POI d’entrée.<br>Nous utilisons **[!UICONTROL Dernier entré]** comme type de point ciblé car, dans la plupart des cas, **[!UICONTROL Dernier entré]** sera identique au **[!UICONTROL point ciblé actuel]**. <br><br>**[!UICONTROL POI actuel &#x200B;]**&#x200B;ne doit être utilisé que dans les instances où des clôtures géographiques de POI se chevauchent. Dans ce cas, ces points ciblés doivent être classés, puis le&#x200B;**[!UICONTROL &#x200B; point ciblé actuel &#x200B;]**&#x200B;affichera le point ciblé le plus classé parmi les 2 ou 3 clôtures géographiques où se trouve actuellement un utilisateur. |  |
| 12c | Sélectionnez une clé de métadonnées personnalisée qui vous aidera à préciser les points ciblés qui recevront un message. |  |
| 12d | Pour la fréquence et la durée, ne restez qu’à un ou deux jours, de sorte que si les critères ne vous plaisent pas, vous pouvez expirer le déclencheur dans un délai plus court. |  |
| 12e | Pour Toujours/Une ou Jusqu’à un clic publicitaire, sélectionnez *TOUJOURS* afin que vous puissiez tester sur plusieurs emplacements. | Un message in-app s’affiche TOUJOURS lorsque vous simulez un changement d’emplacement qui répond aux critères de métadonnées appropriés. |
| 12f | Pour l’affichage, sélectionnez une option autre que Notification locale. Cela facilite l’affichage lors du test avec l’application au premier plan.) |  |
| 12g | Préparez/confirmez et déployez le message in-app. |  |
| 13 | Dans votre environnement de développement, pour vous assurer que les nouvelles règles de campagne sont téléchargées, quittez et relancez l’application. | N’oubliez pas que les applications doivent être complètement lancées pour que le nouveau fichier de règles Campaign soit téléchargé sur le périphérique. |
| 14 | Dans votre application de développement, changez d’emplacement à l’aide des fichiers GPX créés précédemment. | Le message in-app devrait s’afficher en fonction des critères définis précédemment. |
| 15 | Pour le prochain test, nous allons essentiellement copier les mêmes étapes que précédemment, mais cette fois nous allons tester la NOTIFICATION LOCALE. | Le résultat attendu est que les notifications locales s’affichent chaque fois que les critères correspondants sont remplis. |
| 16 | Configurez un nouveau message in-app (type = diffusion). |  |
| 16a | Dans les déclencheurs, sélectionnez **[!UICONTROL Type d’événement Places]** - **[!UICONTROL Entrée comme déclencheur]**. |  |
| 16b | Sélectionnez les métadonnées personnalisées Places comme filtre supplémentaire - utilisez **[!UICONTROL Type de POI]** = **[!UICONTROL Dernier POI d’entrée]**. |  |
| 16c | Sélectionnez une clé de métadonnées personnalisée qui vous aidera à préciser les points ciblés qui recevront un message. |  |
| 16d | Pour la fréquence et la durée, ne conservez qu’un ou deux jours, de sorte que si les critères ne vous plaisent pas, vous pouvez expirer le déclencheur dans un délai plus court. |  |
| 16e | Pour Toujours/Une ou Jusqu’à un clic publicitaire, **[!UICONTROL TOUJOURS]**. |  |
| 16f | Pour le type d’affichage, sélectionnez **[!UICONTROL Notification locale]**. |  |
| 16g | Préparez/confirmez et déployez le message in-app. |  |
| 17 | Dans l’environnement de développement, connectez votre appareil et appuyez sur **[!UICONTROL Play]** sur la version. Une fois que vous avez établi que cet emplacement fonctionne, mettez l’application en arrière-plan et continuez à changer d’emplacement dans Xcode ou Android Studio. Les lectures de la console indiquent toujours le changement d’emplacement, et les notifications locales s’affichent toujours en fonction des critères définis dans votre déclencheur. (Il peut y avoir un délai de 1 à 2 secondes.) | Le résultat attendu est que les notifications locales s&#39;affichent chaque fois que les critères correspondants sont remplis. |
|  | **POINT DE RÉSUMÉ** <br> À ce stade, nous devrions voir les entrées de points ciblés dans notre environnement local. Nous devrions également voir les messages de Campaign basés sur le fonctionnement du point ciblé. En cas d’échec, vérifiez si une notification de Slack n’a pas été envoyée. S’il n’y a pas de message de Slack, vérifiez la console de l’application, car une nouvelle entrée d’emplacement peut ne pas avoir été enregistrée. Si les résultats sont probants, nous pouvons être sûrs que l&#39;application fonctionne correctement et que le service de messagerie Places et Campaign fonctionne également correctement. |  |
|  | **TESTS SUR SITE** <br>Peu de choses devraient changer lors du test sur place. Le fait de conserver le postback de l’arrière-plan actif permet de déterminer si l’appareil obtient une entrée et une sortie pour l’emplacement. |  |
| 18 | Effectuez des tests avec les appareils commençant par le wifi et le cellulaire désactivés, puis activez-les une fois dans la région du point ciblé. | En cas d’échec, notez si vous recevez une entrée et une notification de géo-barrière en Slack. Quel est l’horodatage de la notification du Slack ? |
| 19 | Effectuez le test en n’activant que les canaux cellulaires et en désactivant la connexion Wi-Fi. |  |
| 20 | Effectuez le test avec les téléphones cellulaires et le Wi-Fi activés. |  |
|  | **POINT DE RÉSUMÉ** <br> Le test sur site doit correspondre étroitement au test de développement. Gardez à l’esprit que certains facteurs environnementaux peuvent jouer un rôle dans la détermination de l’emplacement d’un utilisateur, tels que la durée de consultation d’une géo-barrière de point d’entrée, la disponibilité du signal cellulaire et la force des points d’accès Wi-Fi à proximité. |  |

## Exemples de logs

**Étape 8 :** Journaux iOS et Android attendus lors d’une mise à jour d’emplacement

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**Étape 9 :** Journaux iOS et Android attendus lors d’un événement

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
