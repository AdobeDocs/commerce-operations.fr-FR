---
title: Onglet [!UICONTROL bots]
description: En savoir plus sur l’onglet [!UICONTROL bots] de  [!DNL Observation for Adobe Commerce].
exl-id: 741310ca-28fb-4b08-95c7-e8d1fb952018
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1905'
ht-degree: 0%

---

# Onglet [!UICONTROL bots]

Cet onglet contient des informations qui expliquent comment identifier et quelles [!DNL bots] provoquent des problèmes sur le site.

## Vue d’ensemble de haut niveau des [!DNL bots] :

* Un [!DNL bot] est un logiciel qui exécute des tâches automatisées répétitives. Avec l’intelligence artificielle et l’évolution du machine learning, les tâches, les méthodes et les interactions des [!DNL bots] évoluent. Il existe de *bonnes* [!DNL bots] qui profitent aux sites en les explorant et en les ajoutant aux moteurs de recherche Internet. Ainsi, les internautes sont guidés vers le site par le biais des résultats des moteurs de recherche. Une *bonne* [!DNL bot] respecte généralement les limites placées sur le [!DNL bot] par un fichier `robots.txt` ou des paramètres dans une console de moteur de recherche. Les limites peuvent restreindre l’accès au site ou à des parties du site.
* Les [!DNL bots] malveillants ignorent le fichier `robots.txt` ou peuvent usurper une bonne [!DNL bot] par le biais du champ agent utilisateur de requête des données de requête HTTP. Certaines choses que les [!DNL bots] malveillants font :
   * Ajoutez une charge à un site pour refuser aux utilisateurs légitimes l’accès au site.
   * Gratter et réutiliser du contenu sans autorisation.
   * Enregistrez de faux comptes pour inonder les services de messagerie ou les adresses ou redirigez-les vers d&#39;autres sites ([!DNL SPAM bots]).
   * Créez de fausses vues ([!DNL Viewbots]).
   * Acheter des produits ou des billets ([!DNL Focused bots]).
* Gestion des [!DNL bots]
   * [!DNL Observation for Adobe Commerce] offre une vue sur le trafic [!DNL bot] :
      * Il affiche l’activité [!DNL bot] totale non mise en cache qui affiche la charge qu’un [!DNL bot] ajoute à un site et le moment où cette charge se produit.
      * Il affiche les [!DNL bots] qui génèrent des erreurs. En règle générale, si un [!DNL bot] ajoute une charge qui entraîne des problèmes de site, cette adresse [!DNL bot] ou IP présente la fréquence d’erreurs la plus élevée.
      * Elle affiche les noms de [!DNL bot] (valeurs de champ Demander l’agent utilisateur) et les adresses IP à gérer via :
         * [!DNL Fastly] (limitation du débit ou [!DNL VCLs] qui bloque les adresses IP, les plages ou les [!DNL bots] par valeur de nom).
         * Ajout d’informations de bonne [!DNL bot] au `robots.txt field` pour restreindre ou limiter le taux d’accès au site.
         * Gestion des [!DNL Bing] ou des [!DNL Google bots] via la console du moteur de recherche.

## [!UICONTROL Experimental Potential Malicious Bots frame]

![&#x200B; Cadre de robots malveillants potentiels expérimentaux &#x200B;](../../assets/tools/observation-for-adobe-commerce/experimental-potential-malicious-bots-frame-new.jpg)

Le cadre **[!UICONTROL Experimental Potential Malicious Bots frame]** exécute plus de 12 requêtes distinctes et complexes. Il détecte les signatures de requêtes IP malveillantes, puis agrège les résultats, les additionne et les trie par nombre dans l’ordre décroissant. Les requêtes contiennent une multitude de signatures de données d’exploits CVE et d’autres requêtes malveillantes. Même lorsque les exploits sont bloqués par des correctifs/correctifs de sécurité et ne constituent pas une menace pour le site, la demande doit toujours être traitée par le site web. Le volume des demandes peut devenir assez important en peu de temps. Cette trame n’affiche pas le nombre total de requêtes provenant de l’adresse IP, mais plutôt les requêtes qui comportent des signaux indiquant que la requête avait une intention suspecte.

Assurez-vous que le trafic est suspect et qu’il ne provient pas d’une adresse [!DNL Content Distributed Network] (CDN) qui peut également diffuser des requêtes valides. Si les requêtes proviennent d’une adresse IP de réseau CDN, contactez ce fournisseur de services pour l’aider à bloquer le trafic suspect via son réseau. Si vous devez bloquer l’adresse ou l’URL de requête, reportez[vous à la section  [!DNL Fastly] Bloquer le trafic malveillant pour Adobe Commerce au niveau &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level.html?lang=fr) de la base de connaissances du support technique d’Adobe Commerce.

## [!UICONTROL Rate of HTTP request per second (top 25) during requested time period]

![Taux de requêtes HTTP par seconde (les 25 premières) pendant la période demandée](../../assets/tools/observation-for-adobe-commerce/rate-of-http-request-per-second.jpg)

La période **[!UICONTROL Rate of HTTP request per second (top 25) during requested time period]** affiche les demandes les plus élevées par seconde d’adresses IP pendant la période sélectionnée. Si ces adresses se trouvent également dans le tableau ci-dessus, assurez-vous qu’elles ne sont pas des adresses CDN ni malveillantes et bloquez-les via [!DNL Fastly].

## [!UICONTROL Total Bot traffic by bot name] :

![Trafic total de robots par nom de robot au cours de la période sélectionnée :](../../assets/tools/observation-for-adobe-commerce/total-bot-traffic-bot-name.png)

La table **[!UICONTROL Total Bot traffic by bot name during selected time period]** contient le nombre agrégé de requêtes non mises en cache où le champ [!UICONTROL request_user_agent] contient une chaîne de [!DNL bots] dans la valeur . Il peut s’agir ou non du [!DNL bot] nommé, car la valeur du champ [!UICONTROL request_user_agent] peut être usurpée. La valeur située sous la colonne [!UICONTROL Count] est la plus importante.

## [!UICONTROL Total Bot Traffic by Bot name/IP address]

![Total du trafic de robots par nom/adresse IP de robot pendant la période sélectionnée Comment bloquer le trafic de robots au niveau Fastly OU gérer les robots via votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/best-practices-adobecommerce-robots.png)

Le tableau **[!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche les mêmes données que le tableau précédent, mais ajoute des adresses IP qui effectuent les requêtes au nom du [!DNL bot] nommé. Comme les [!DNL bots] malveillants usurpent de bonnes [!DNL bots], les adresses IP doivent être vérifiées par le biais de sites web qui identifient les adresses IP abusives ou par le biais de services ou de ** whois[!DNL DNS lookups]. Par exemple, [!DNL Google] publie ses [[!DNL googlebot] adresses IP](https://developers.google.com/search/apis/ipranges/googlebot.json) et [!DNL Microsoft] dispose d’un outil de vérification pour les [[!DNL Bingbots]](https://www.bing.com/webmasters/help/Verify-Bingbot-2195837f).

## [!UICONTROL Graph - Bots with HTTP status errors]

![Graphique - Robots avec des erreurs de statut HTTP pendant la période sélectionnée Comment bloquer le trafic de robots au niveau Fastly OU gérer les robots via votre fichier robots.txt Bonnes pratiques pour les robots Adobe Commerce.txt](../../assets/tools/observation-for-adobe-commerce/bots-with-http-status-errors.png)

Le graphique **[!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche les erreurs sur les [!DNL bots] qui se déclarent dans le champ Demander l’agent utilisateur . Cela ne signifie pas nécessairement que l’erreur est due au volume du [!DNL bot] ou à d’autres trafics. Les erreurs peuvent être que le [!DNL bot] demande des informations qui n’existent pas ou qu’il y a un autre problème dans la demande.

En cas de pic d’erreurs sur les adresses IP lors de l’instabilité ou de la panne du site, elles peuvent être suspectées d’être responsables du problème de site.

## [!UICONTROL Table - IPs that do not identify as bots]

![Tableau - Adresses IP qui ne s’identifient pas comme des robots avec des erreurs de statut HTTP pendant la période sélectionnée Comment bloquer le trafic des robots au niveau Fastly OU gérer les robots via votre fichier robots.txt Bonnes pratiques pour les &#x200B;](../../assets/tools/observation-for-adobe-commerce/ips-http-errors.png) robots.txt d’Adobe Commerce

Le tableau **[!UICONTROL Table - IPs that do not identify as bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche les requêtes IP avec des codes d’état HTTP autres que 200 qui NE S’auto-identifient PAS comme [!DNL bots] dans le champ Demander l’agent utilisateur . Ces adresses IP peuvent être des adresses IP malveillantes, en particulier si le nombre est élevé pour la période sélectionnée.

Si le nombre de codes d’état http non 200 est faible et que les plages d’adresses IP ne sont pas similaires, les adresses peuvent ne pas contribuer aux problèmes de site.

## [!UICONTROL Table – Cache Status 'ERROR']

![Table - Table des détails du statut du cache &#39;ERROR&#39; (que font ces adresses IP ?) Comment bloquer le trafic de robots au niveau Fastly OU gérer les robots via votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/cache-status-errors.png)

Lorsque les adresses IP génèrent une fréquence d’erreurs élevée, demandez-vous ce qu’elles font ? Le tableau **[!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche l’URL demandée avec la valeur de statut HTTP pour les requêtes dont la valeur de [!UICONTROL ERROR] de statut du cache. La fréquence est facettisée par l’URL, de sorte que le nombre peut être faible. N’oubliez pas que l’adresse IP peut envoyer des milliers de requêtes au cours de la période sélectionnée. Il s’agit d’une vue par rapport à 2 000 requêtes au maximum pendant la période (limite d’affichage des enregistrements).

## [!UICONTROL Show 5XX status distribution]

![Afficher la répartition de statut 5XX entre les adresses IP (les 200 meilleures adresses) Comment bloquer le trafic de robots au niveau Fastly OU gérer les robots via votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt &#x200B;](../../assets/tools/observation-for-adobe-commerce/5xx-status.png)

Le cadre **[!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** est puissant. Elle affiche les adresses IP qui possèdent des codes d’état HTTP 5XX au cours de la période sélectionnée. Si une adresse IP effectue un volume élevé de requêtes et que le site est affecté au point où il ne peut pas gérer le trafic, les adresses IP qui effectuent la fréquence de requêtes la plus élevée auront généralement le volume d’erreurs le plus élevé. Les codes d’état http 5XX indiquent généralement un site qui a du mal à répondre aux requêtes.

Plus la barre est large, plus le pourcentage d&#39;erreurs que l&#39;adresse IP a dans le nombre total d&#39;erreurs 5xx pendant cette période est élevé. Remarque : une adresse IP peut comporter plusieurs segments dans le graphique si elle comporte plusieurs codes d’état http (par exemple, les états 502 et 503 http).

La répartition type est indiquée vers la droite de la barre lorsque les adresses IP sont égales en largeur ou il y a quelques barres larges avec des nombres très faibles.

Si vous pointez sur le segment de barre, le nombre d’erreurs indiquées pendant la période sélectionnée s’affiche.

## [!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status]

![Statut du cache IP (MISS, PASS, ERROR) et le statut http pendant la période sélectionnée Comment bloquer le trafic des robots au niveau Fastly OU gérer les robots via votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/ip-cache-status-miss-pass-error.png)

Ce cadre **[!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche le nombre de codes d’état HTTPS et les requêtes non mises en cache par adresse IP sur la période sélectionnée. Indique la charge proportionnelle de chaque adresse IP et le volume total. Elle affiche les adresses IP qui ont le plus de requêtes.

## [!UICONTROL Fastly Cache Summary for selected time period]

![Résumé du cache rapide pour la période sélectionnée](../../assets/tools/observation-for-adobe-commerce/fastly-cache-summary.png)

Si vous cliquez sur l’icône [!UICONTROL Error] dans le graphique ci-dessous, vous pouvez comparer les deux derniers graphiques. Cela peut aider à indiquer où la charge contribue aux problèmes du site.

![Vérification des erreurs Fastly](../../assets/tools/observation-for-adobe-commerce/compare-fastly.png)

## [!UICONTROL Graph - IPs that do not identify as bots]

![IP qui ne s&#39;identifient pas comme des robots sans erreur pendant la période sélectionnée Comment bloquer le trafic des robots au niveau Fastly OU gérer les robots via votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/ips-that-do-not-identify-as-bots.png)

Le cadre **[!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche le champ Demander l’agent utilisateur, l’adresse IP et le code d’état pour les demandes pour lesquelles le champ Demander l’agent utilisateur n’indique pas de [!DNL bot]. Cette trame peut afficher des requêtes haute fréquence provenant de n&#39;importe quelle adresse IP mais prêter attention aux requêtes haute fréquence, en particulier pendant une période où le site peut avoir des problèmes.

## [!UICONTROL Graph - Suspicious Non-Bot traffic]

![Trafic suspect non lié aux robots pendant la période sélectionnée](../../assets/tools/observation-for-adobe-commerce/suspicious-non-bot-traffic.png)

Le graphique **[!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]** recherche une valeur d’agent utilisateur de requête de Go-http-client, mais sera étendu pour examiner d’autres valeurs d’agent utilisateur de requête suspectes. Cette valeur de l’agent utilisateur de requête est utilisée par les sites pour la connexion à partir des services et peut être valide, mais elle est également utilisée par des [!DNL bots] malveillants.

## [!UICONTROL Graph - Bot traffic by Bot name]

![Graphique - Trafic de robots par nom de robot au cours de la période sélectionnée)](../../assets/tools/observation-for-adobe-commerce/bot-traffic-bot-name.png)

Le cadre **[!UICONTROL Graph - Bot traffic by Bot name during selected time period]** affiche les mêmes données que le trafic total de robots par nom de [!DNL Bot] au cours de la période sélectionnée dans le tableau en haut de l’onglet. Il affiche les données via la chronologie de sorte que vous puissiez voir à quel moment les requêtes du [!DNL bots] sont effectuées et leurs distributions.

## [!UICONTROL Graph - Top 250 Bot Names and IP addresses]

![250 premiers noms et adresses IP de robots au cours de la période sélectionnée Comment bloquer le trafic de robots au niveau Fastly OU gérer les robots via votre fichier robots.txt Bonnes pratiques pour Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/top-250-bot-names-ip-addresses.png)

Le cadre **[!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** affiche les mêmes données que le trafic [!DNL Bot] total par nom/adresse IP de robot au cours de la période sélectionnée dans le tableau en haut de l’onglet. Il affiche les données via la chronologie et les facette par adresse IP. Cela indique le moment où les requêtes du [!DNL bots] sont effectuées, l’adresse IP qui effectue les requêtes et les distributions des requêtes.

## [!UICONTROL Blocked Bot name / IP addresses (in Fastly)]

![Nom de robot bloqué/adresses IP (dans Fastly) pendant la période sélectionnée. Ce graphique affiche le trafic des robots et les adresses IP auxquelles un code d’état HTTP 403 Interdit a été renvoyé](../../assets/tools/observation-for-adobe-commerce/blocked-bot-name-ip-addresses-403-code2.png)

Le cadre **[!UICONTROL Blocked Bot name / IP addresses (in Fastly) during selected time period. This graph displays bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** affiche le nom et les adresses IP des robots qui sont bloqués. Vous pouvez voir dans ce graphique comment toutes les requêtes sont bloquées dans [!DNL Fastly] à l’avenir.

## [!UICONTROL Blocked non-Bot name / IP addresses (in Fastly)]

![Nom/adresses IP non-robots bloqués (dans Fastly) pendant la période sélectionnée. Ce graphique affiche le trafic non bot et les adresses IP auxquelles un code d’état HTTP 403 Interdit a été renvoyé &#x200B;](../../assets/tools/observation-for-adobe-commerce/blocked-non-bot-name-ip-addresses.png)

La trame **[!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** affiche les adresses IP qui ne s’identifient pas comme un [!DNL bot] qui ont été bloquées via [!DNL Fastly].

## [!UICONTROL This table shows the number of user agents per IP address, number of successful, unsuccessful and blocked requests:]

![Ce tableau indique le nombre d’agents utilisateurs par adresse IP, le nombre de requêtes réussies, non réussies et bloquées :](../../assets/tools/observation-for-adobe-commerce/unsuccessful-attempts.png)

Les [!DNL bots] malveillants usurpent souvent d’autres [!DNL bots] par la valeur du champ [!UICONTROL Request User Agent]. Ce tableau indique le nombre de valeurs uniques de l’adresse IP dans ce champ. Plus la valeur du champ [!UICONTROL Request User Agent] est élevée, plus l’adresse IP est suspecte.

## [!UICONTROL IP with non-200 status errors]

![IP avec erreurs de statut non-200 - sans statut 403](../../assets/tools/observation-for-adobe-commerce/ip-non-200-status-errors.png)

L’image **[!UICONTROL IP with non-200 status errors – without 403 status]** affiche la répartition, sur la période sélectionnée, des adresses IP avec des codes d’état HTTP autres que 200. Lorsque des valeurs plus élevées sont affichées sur une seule adresse IP ou sur un groupe d’adresses IP, une enquête plus approfondie est nécessaire.

## [!UICONTROL IP with 403 status codes:]

![IP avec codes d’état 403 :](../../assets/tools/observation-for-adobe-commerce/ip-403-status-code2.png)

Le cadre **[!UICONTROL IP with 403 status codes]** affiche les requêtes non mises en cache sans [!UICONTROL cache_status=ERROR] ayant un statut HTTP défini sur 403. Cela peut indiquer que le serveur d’origine est la source de l’adresse 403 (non autorisée) plutôt qu’un bloc de l’adresse [!DNL Fastly].

## [!UICONTROL Top 5 with non-200 status codes]

![Top 5 avec des codes d’état autres que 200 affichant cache_status:](../../assets/tools/observation-for-adobe-commerce/top-5-non-200-status-code-status.png)

Le tableau **[!UICONTROL Top 5 with non-200 status codes showing cache_status]** indique, au niveau de l’adresse IP/du statut, le nombre de chaque avec la valeur [!UICONTROL cache_status].

## [!UICONTROL Pageview Latency will show as spikes]

![La latence de la page vue s’affichera sous forme de pics sur ce graphique :](../../assets/tools/observation-for-adobe-commerce/pageview-latency.png)

Le cadre **[!UICONTROL Pageview Latency will show as spikes on this graph:]** affiche la latence de réponse du chargement de page/de l’API qui peut correspondre au trafic [!DNL bot].
