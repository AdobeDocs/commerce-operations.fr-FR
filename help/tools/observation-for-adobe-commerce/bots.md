---
title: Onglet [!UICONTROL bots]
description: Découvrez l’onglet [!UICONTROL bots] de [!DNL Observation for Adobe Commerce].
exl-id: 741310ca-28fb-4b08-95c7-e8d1fb952018
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1905'
ht-degree: 0%

---

# Onglet [!UICONTROL bots]

Cet onglet contient des informations qui expliquent comment identifier si et ce que [!DNL bots] causent des problèmes sur le site.

## Présentation générale de [!DNL bots] :

* Un [!DNL bot] est un logiciel qui exécute des tâches automatisées répétitives. Avec l’intelligence artificielle et l’évolution de l’apprentissage automatique, les tâches, les méthodes et les interactions de [!DNL bots] changent. Il existe *good* [!DNL bots] qui bénéficient aux sites en les analysant et en les ajoutant aux moteurs de recherche sur Internet. Les internautes sont ainsi guidés vers le site par les résultats des moteurs de recherche. Un *bon* [!DNL bot] respecte généralement les limites placées sur le [!DNL bot] par un fichier `robots.txt` ou des paramètres dans une console de moteur de recherche. Les limites peuvent restreindre l’accès au site ou à certaines parties du site.
* Malveillant [!DNL bots] ignorez le fichier `robots.txt` ou ils peuvent fausser un [!DNL bot] correct par le biais du champ de l’agent utilisateur de requête des données de requête HTTP. Certaines choses que malveillant [!DNL bots] font :
   * Ajoutez la charge à un site pour refuser aux utilisateurs légitimes l’accès au site.
   * Videz et réutilisez du contenu sans autorisation.
   * Enregistrez des faux comptes pour inonder les services de messagerie ou les adresses ou rediriger vers d’autres sites ([!DNL SPAM bots]).
   * Créez des vues falsifiées ([!DNL Viewbots]).
   * Achetez des produits ou des billets ([!DNL Focused bots]).
* Gestion de [!DNL bots]
   * [!DNL Observation for Adobe Commerce] a des vues du trafic [!DNL bot] :
      * Il affiche l’activité [!DNL bot] totale non mise en cache qui affiche la charge qu’un [!DNL bot] est en train d’ajouter à un site et le moment où cette charge est en cours.
      * Il affiche les [!DNL bots] qui génèrent des erreurs. En règle générale, si un [!DNL bot] ajoute une charge qui entraîne des problèmes sur le site, cette [!DNL bot] ou adresse IP a la fréquence d&#39;erreurs la plus élevée.
      * Il affiche [!DNL bot] noms (valeurs de champ de l’agent utilisateur de requête) et adresses IP à gérer par :
         * [!DNL Fastly] (limitation de débit ou [!DNL VCLs] qui bloquent les adresses IP, les plages ou [!DNL bots] par valeur de nom).
         * Ajout de bonnes [!DNL bot] informations à `robots.txt field` pour restreindre ou limiter le taux d&#39;accès au site.
         * Gérer [!DNL Bing] ou [!DNL Google bots] via la console du moteur de recherche.

## [!UICONTROL Experimental Potential Malicious Bots frame]

![Cadre de robots malveillants potentiels expérimentaux](../../assets/tools/observation-for-adobe-commerce/experimental-potential-malicious-bots-frame-new.jpg)

L’image **[!UICONTROL Experimental Potential Malicious Bots frame]** s’exécute sur 12 requêtes complexes et distinctes. Il détecte les signatures de requête IP malveillantes, puis agrège les résultats, les additionne et les trie par nombre dans l’ordre décroissant. Les requêtes contiennent une multitude de signatures de données d’exploits CVE et d’autres requêtes malveillantes. Même lorsque les exploits sont bloqués par des correctifs ou correctifs de sécurité et ne constituent pas une menace pour le site, la demande doit toujours être traitée par le site web. Le volume de demandes peut devenir très important en peu de temps. Ce cadre n’affiche pas le nombre total de demandes provenant de l’adresse IP, mais plutôt les demandes qui contiennent des signaux indiquant que la demande a eu des intentions suspectes.

Veillez à vérifier que le trafic est suspect et qu&#39;il ne provient pas d&#39;une adresse [!DNL Content Distributed Network] (CDN) qui peut également diffuser des requêtes valides. Si les demandes sont déterminées comme provenant d&#39;une adresse IP du réseau CDN, veuillez contacter ce fournisseur de services pour aider à bloquer le trafic suspect via leur réseau. Si vous devez bloquer l’adresse ou l’URL de demande, reportez-vous à la section [Bloquer le trafic malveillant pour Adobe Commerce sur [!DNL Fastly] level](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level.html?lang=fr) dans la base de connaissances de prise en charge d’Adobe Commerce.

## [!UICONTROL Rate of HTTP request per second (top 25) during requested time period]

![Taux de requêtes HTTP par seconde (25 premières) pendant la période demandée](../../assets/tools/observation-for-adobe-commerce/rate-of-http-request-per-second.jpg)

L’image **[!UICONTROL Rate of HTTP request per second (top 25) during requested time period]** affiche les demandes les plus élevées par seconde d’adresses IP au cours de la période sélectionnée. Si ces adresses figurent également dans le tableau ci-dessus, vérifiez qu’elles ne sont pas des adresses CDN et malveillantes et bloquez-les via [!DNL Fastly].

## [!UICONTROL Total Bot traffic by bot name] :

![Trafic total de robots par nom de robot pendant la période sélectionnée :](../../assets/tools/observation-for-adobe-commerce/total-bot-traffic-bot-name.png)

La table **[!UICONTROL Total Bot traffic by bot name during selected time period]** contient le nombre agrégé de requêtes non mises en cache où le champ [!UICONTROL request_user_agent] a une chaîne [!DNL bots] dans la valeur. Il peut s’agir de la valeur [!DNL bot] nommée, car la valeur de champ [!UICONTROL request_user_agent] peut être mise en file d’attente. La valeur sous la colonne [!UICONTROL Count] est la plus importante.

## [!UICONTROL Total Bot Traffic by Bot name/IP address]

![Trafic total de robots par nom/adresse IP pendant la période sélectionnée Comment bloquer le trafic de robots à un niveau Fastly OU gérer les robots par le biais de votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/best-practices-adobecommerce-robots.png)

La table **[!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche les mêmes données que la table précédente, mais ajoute des adresses IP effectuant les demandes pour le compte du nom [!DNL bot]. Comme [!DNL bots] est malveillant [!DNL bots], la ou les adresses IP doivent être vérifiées par le biais de sites web qui identifient les adresses IP abusives ou par les services *whois* ou [!DNL DNS lookups]. Par exemple, [!DNL Google] publie ses [[!DNL googlebot] adresses IP](https://developers.google.com/search/apis/ipranges/googlebot.json) et [!DNL Microsoft] dispose d’un outil de vérification pour [[!DNL Bingbots]](https://www.bing.com/webmasters/help/Verify-Bingbot-2195837f).

## [!UICONTROL Graph - Bots with HTTP status errors]

![Graphique - Robots avec erreurs d’état HTTP pendant la période sélectionnée Comment bloquer le trafic de robots à un niveau Fastly OU gérer les robots par le biais de votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/bots-with-http-status-errors.png)

Le graphique **[!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche des erreurs sur [!DNL bots] qui se déclarent dans le champ de l’agent utilisateur de requête. Cela ne signifie pas nécessairement que l’erreur est provoquée par le volume de [!DNL bot] ou d’un autre trafic. Les erreurs peuvent être que le [!DNL bot] demande des informations qui n’existent pas ou qu’il y a un autre problème dans la requête.

S’il y a un pic d’erreurs sur les adresses IP en cas d’instabilité ou de panne du site, elles peuvent être suspectées d’affecter le problème du site.

## [!UICONTROL Table - IPs that do not identify as bots]

![Tableau : adresses IP qui ne s’identifient pas comme des robots avec des erreurs d’état HTTP au cours de la période sélectionnée Comment bloquer le trafic de robots à un niveau rapide OU gérer des robots par le biais de votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt ](../../assets/tools/observation-for-adobe-commerce/ips-http-errors.png)

La table **[!UICONTROL Table - IPs that do not identify as bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affichera les requêtes IP avec des codes d’état http non-200 qui NE S’auto-identifient PAS comme [!DNL bots] dans le champ de l’agent utilisateur de requête. Ces adresses IP peuvent être des adresses IP malveillantes, en particulier si le nombre est élevé pour la période sélectionnée.

Si le nombre de codes d’état http non 200 est faible et que les plages d’adresses IP ne sont pas similaires, les adresses peuvent ne pas contribuer aux problèmes du site.

## [!UICONTROL Table – Cache Status 'ERROR']

![Table - Tableau détaillé &#39;ERROR&#39; du statut du cache (que font ces adresses IP ?) Comment bloquer le trafic de robots à un niveau Fastly OU gérer les robots par le biais de votre fichier robots.txt Bonnes pratiques pour les robots Adobe Commerce.txt](../../assets/tools/observation-for-adobe-commerce/cache-status-errors.png)

Lorsque les adresses IP génèrent une fréquence élevée d’erreurs, demandez-vous ce qu’elles font ? La table **[!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affichera l’URL demandée avec la valeur d’état HTTP pour les requêtes ayant un état de cache [!UICONTROL ERROR]. La fréquence est facettée par l’URL, de sorte que le nombre peut être faible. N’oubliez pas que l’adresse IP peut effectuer des milliers de demandes pendant la période sélectionnée. Il s’agit d’une vue par rapport à 2 000 demandes au cours de la période (limite d’affichage des enregistrements).

## [!UICONTROL Show 5XX status distribution]

![Afficher la distribution de statut 5XX sur les adresses IP (200 premières adresses) Comment bloquer le trafic de robots sur un niveau Fastly OU gérer les robots via votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt ](../../assets/tools/observation-for-adobe-commerce/5xx-status.png)

L’image **[!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** est puissante. Elle affiche les adresses IP qui comportent des codes d’état http 5XX au cours de la période sélectionnée. Si une adresse IP effectue un volume élevé de requêtes et que le site est affecté au point où il ne peut pas gérer le trafic, alors les adresses IP qui enregistrent la fréquence la plus élevée des requêtes auront généralement le volume d’erreurs le plus élevé. Les codes d’état http 5XX indiquent généralement un site qui a du mal à répondre aux requêtes.

Plus la barre est grande, plus le pourcentage d’erreurs de l’adresse IP est élevé dans le nombre total d’erreurs 5xx durant cette période. Remarque : une adresse IP peut comporter plusieurs segments dans le graphique si elle comporte plusieurs codes d’état http (par exemple, 502 et 503 états http).

Une distribution type serait indiquée vers la droite de la barre où les adresses IP sont égales en largeur ou il y aurait quelques barres larges avec des valeurs très faibles.

Si vous passez la souris sur le segment à barres, le nombre d’erreurs indiquées s’affichera au cours de la période sélectionnée.

## [!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status]

![État du cache IP (MISS, PASS, ERROR) et état http pendant la période sélectionnée Comment bloquer le trafic de robots à un niveau plus rapide OU gérer les robots par le biais de votre fichier robots.txt Bonnes pratiques pour les robots Adobe Commerce.txt](../../assets/tools/observation-for-adobe-commerce/ip-cache-status-miss-pass-error.png)

Cette image **[!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche le nombre de codes d’état HTTPS et de requêtes non mises en cache par IP sur la période sélectionnée. Cela indique la charge proportionnelle provenant de chaque adresse IP et le volume total. Les adresses IP présentant le plus de requêtes sont alors affichées.

## [!UICONTROL Fastly Cache Summary for selected time period]

![Résumé du cache le plus rapide pour la période sélectionnée](../../assets/tools/observation-for-adobe-commerce/fastly-cache-summary.png)

Si vous cliquez sur l’icône [!UICONTROL Error] du graphique ci-dessous, vous pouvez comparer les deux derniers graphiques l’un à l’autre. Cela peut aider à indiquer où la charge contribue aux problèmes du site.

![Vérification d’erreur rapide](../../assets/tools/observation-for-adobe-commerce/compare-fastly.png)

## [!UICONTROL Graph - IPs that do not identify as bots]

![IP qui ne s’identifient pas comme robots sans erreur pendant la période sélectionnée Comment bloquer le trafic de robots à un niveau rapide OU gérer les robots par le biais de votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/ips-that-do-not-identify-as-bots.png)

L’image **[!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche le champ de l’agent utilisateur de requête, l’adresse IP et le code d’état pour les demandes pour lesquelles le champ de l’agent utilisateur de requête n’indique pas de [!DNL bot]. Ce cadre peut afficher des demandes à haute fréquence provenant de n’importe quelle adresse IP, mais prêter attention aux demandes à haute fréquence, en particulier pendant une période où le site peut rencontrer des problèmes.

## [!UICONTROL Graph - Suspicious Non-Bot traffic]

![Trafic non bot suspect pendant la période sélectionnée](../../assets/tools/observation-for-adobe-commerce/suspicious-non-bot-traffic.png)

Le graphique **[!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]** recherche une valeur d’agent utilisateur de demande Go-http-client, mais sera étendu pour examiner d’autres valeurs d’agent utilisateur de demande suspectes. Cette valeur de l’agent utilisateur de requête est utilisée par les sites pour se connecter à partir de services et peut être valide, mais elle est également utilisée par le malveillant [!DNL bots].

## [!UICONTROL Graph - Bot traffic by Bot name]

![Graphique - Trafic de robots par nom de robot pendant la période sélectionnée)](../../assets/tools/observation-for-adobe-commerce/bot-traffic-bot-name.png)

L’image **[!UICONTROL Graph - Bot traffic by Bot name during selected time period]** affiche les mêmes données que le nom du trafic total de robots [!DNL Bot] lors de la période sélectionnée dans la partie supérieure de l’onglet. Il affiche les données via la chronologie afin que vous puissiez voir le moment où les requêtes de [!DNL bots] sont effectuées et leur distribution.

## [!UICONTROL Graph - Top 250 Bot Names and IP addresses]

![Top 250 des noms de robots et des adresses IP durant une période sélectionnée Comment bloquer le trafic de robots à un niveau rapide OU gérer les robots par le biais de votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/top-250-bot-names-ip-addresses.png)

L’image **[!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche les mêmes données que le trafic total [!DNL Bot] par nom de robot/adresse IP lors de la période sélectionnée dans la partie supérieure de l’onglet. Il affiche les données via la chronologie et les facette par adresse IP. Cela indique le moment où les requêtes de [!DNL bots] sont effectuées, l’adresse IP qui effectue des requêtes et la distribution des requêtes.

## [!UICONTROL Blocked Bot name / IP addresses (in Fastly)]

![Nom de robot/adresses IP bloquées (en Fastly) pendant la période sélectionnée. Ce graphique affiche le trafic de robots et les adresses IP qui ont été renvoyées avec un code d’état HTTP 403 interdit](../../assets/tools/observation-for-adobe-commerce/blocked-bot-name-ip-addresses-403-code2.png)

Le cadre **[!UICONTROL Blocked Bot name / IP addresses (in Fastly) during selected time period. This graph displays bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** affiche le nom du robot et les adresses IP bloquées. Vous pouvez voir dans ce graphique comment toutes les demandes sont bloquées dans [!DNL Fastly] à l’avenir.

## [!UICONTROL Blocked non-Bot name / IP addresses (in Fastly)]

![ Nom de robot/adresses IP non bloquées (en Fastly) pendant la période sélectionnée. Ce graphique affiche le trafic non robots et les adresses IP qui ont été renvoyées avec un code d’état HTTP 403 interdit ](../../assets/tools/observation-for-adobe-commerce/blocked-non-bot-name-ip-addresses.png)

L’image **[!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** affiche les adresses IP qui ne s’identifient pas comme [!DNL bot] et qui ont été bloquées via [!DNL Fastly].

## [!UICONTROL This table shows the number of user agents per IP address, number of successful, unsuccessful and blocked requests:]

![Ce tableau indique le nombre d’agents utilisateur par adresse IP, le nombre de demandes bloquées, ayant réussi et ayant échoué : ](../../assets/tools/observation-for-adobe-commerce/unsuccessful-attempts.png)

Les [!DNL bots] malveillants faussent souvent d&#39;autres [!DNL bots] par le biais de la valeur du champ [!UICONTROL Request User Agent]. Ce tableau indique le nombre de valeurs uniques de l’adresse IP dans ce champ. Plus la valeur du champ [!UICONTROL Request User Agent] est élevée, plus l’adresse IP est suspicieuse.

## [!UICONTROL IP with non-200 status errors]

![IP avec des erreurs d’état non 200 - sans état 403](../../assets/tools/observation-for-adobe-commerce/ip-non-200-status-errors.png)

L’image **[!UICONTROL IP with non-200 status errors – without 403 status]** montre la distribution sur la période sélectionnée des adresses IP avec des codes d’état HTTP autres que 200. Lorsque des valeurs plus élevées s’affichent sur une seule adresse IP ou un groupe d’adresses IP, elles doivent faire l’objet d’une enquête plus approfondie.

## [!UICONTROL IP with 403 status codes:]

![IP avec des codes d’état 403 :](../../assets/tools/observation-for-adobe-commerce/ip-403-status-code2.png)

L’image **[!UICONTROL IP with 403 status codes]** affiche les requêtes non mises en cache sans [!UICONTROL cache_status=ERROR] dont l’état HTTP est 403. Cela peut indiquer que le serveur d’origine est la source du 403 (non autorisé) plutôt qu’un bloc de [!DNL Fastly].

## [!UICONTROL Top 5 with non-200 status codes]

![Top 5 avec des codes d’état non-200 indiquant cache_status :](../../assets/tools/observation-for-adobe-commerce/top-5-non-200-status-code-status.png)

La table **[!UICONTROL Top 5 with non-200 status codes showing cache_status]** affiche, au niveau de l’IP/de l’état, les nombres de chacun avec la valeur [!UICONTROL cache_status].

## [!UICONTROL Pageview Latency will show as spikes]

![La latence des pages vues s’affichera comme des pics sur ce graphique :](../../assets/tools/observation-for-adobe-commerce/pageview-latency.png)

L’image **[!UICONTROL Pageview Latency will show as spikes on this graph:]** affiche la latence de chargement de page/réponse de l’API qui peut être en ligne avec le trafic [!DNL bot].
