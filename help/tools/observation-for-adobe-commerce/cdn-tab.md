---
title: Le [!UICONTROL CDN] tab
description: En savoir plus sur les [!UICONTROL CDN] de [!DNL Observation for Adobe Commerce].
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# Le [!UICONTROL CDN] tab

Cet onglet contient des informations relatives à la variable [!DNL content delivery network (CDN)]. Dans le cas de Adobe Commerce Cloud, il s’agit de la variable [!DNL Fastly] service.

## [!UICONTROL HIT rate]

![Taux d’accès](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

Le **[!UICONTROL HIT rate]** frame affiche le nombre de requêtes pouvant être mises en cache qui ont entraîné [!UICONTROL HITS] à la dernière minute. Cela indique une mise en cache réussie. La flèche vers la droite affiche le pourcentage au-dessus ou en dessous à la même heure il y a une semaine.

## [!UICONTROL HIT Processing]

![Traitement des accès](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

Ceci **[!UICONTROL HIT processing]** indique le nombre de requêtes pouvant être mises en cache qui ont entraîné [!UICONTROL HITS] pendant la semaine.

## [!UICONTROL MISS rate]

![Taux MISS](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

Ceci **[!UICONTROL MISS rate]** indique le nombre d’échecs de requêtes pouvant être mises en cache à la dernière minute. Une erreur se produit lorsque la requête n’est pas mise en cache et que la requête doit être transmise au serveur d’origine pour diffuser le contenu. La valeur à droite est la comparaison entre augmentation/diminution et nombre de minutes par minute une semaine auparavant.

## [!UICONTROL MISS time]

![Heure DE LA MISE À JOUR](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![Rapport d’accès](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![Pourcentage d’erreur](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

Le **[!UICONTROL Error Percentage]** affiche la valeur du pourcentage ERROR des requêtes et affiche l’augmentation/diminution relative par rapport à la même période une semaine auparavant.

## [!UICONTROL Total Requests]

![Nombre total de requêtes](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![Taux d’erreur](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![Réponse moyenne de mise en cache rapide pour la période sélectionnée en secondes](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

Ce cadre affiche la durée en secondes des requêtes pouvant être mises en cache, ce qui signifie que si un événement `cache_response` est un [!UICONTROL MISS], il affiche la moyenne des réponses mises en cache manquées pour le temps sélectionné.

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![Réponse moyenne de mise en cache rapide pour la période sélectionnée en secondes facettée par POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![Bande passante totale (tous les POP) pendant la période sélectionnée, par rapport à 1 semaine auparavant (% d’augmentation/diminution)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![Demandes : depuis la période sélectionnée par rapport à la semaine précédente.](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

Ce cadre est similaire à la zone de résumé pour [!UICONTROL Total Requests] dans la partie supérieure, mais affiche le nombre de requêtes des semaines précédentes. Il s’agit de toutes les requêtes, et pas seulement des requêtes pouvant être mises en cache (où `is_cacheable` est vrai).

## [!UICONTROL Response Count]

![Nombre de réponses](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![Bande passante par POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![5 premières URL (codes d’état 5xx ou 3xx)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

Le **[!UICONTROL Top 5 URLs]** affiche les 5 premières URL qui rencontrent des réponses d’erreur 5xx ou 3xx. En raison de la contrainte d’espace, vous devrez placer le pointeur de la souris sur l’URL pour afficher le code d’erreur spécifique associé à cette URL. (exemple dans la zone rouge de la figure ci-dessus).

## [!UICONTROL Top 25 URLs (200 status)]

![25 premières URL (état 200)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

Le **[!UICONTROL Top 25 URLs]** Le cadre affiche les URL qui ont renvoyé un état 200 par nombre au cours de la période sélectionnée.

## [!UICONTROL Duration by Response Status]

![Durée par état de réponse](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

Le **[!UICONTROL Duration by Response Status]** Le graphique affiche les réponses d’erreur par nombre au cours de la période sélectionnée, facettées par le code d’état d’erreur.

## [!UICONTROL Duration by Response Status, top 25 urls]

![Durée par état de réponse, 25 premières URL](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

Le **[!UICONTROL Duration by Response Status, top 25 URLs]** Le graphique affiche les 25 premières URL selon la durée de la réponse en secondes. Il se peut que vous deviez placer le pointeur de la souris sur l’URL pour afficher l’intégralité du chemin. En outre, pour supprimer toutes les URL, sauf une, cliquez sur cette URL. Vous pouvez ensuite réajouter d’autres URL en cliquant dessus individuellement. Si vous souhaitez supprimer des URL individuelles, vous pouvez maintenir la touche enfoncée et cliquer sur chaque URL pour la supprimer du graphique.

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![Durée par état de réponse, 25 premiers états non-200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

Le **[!UICONTROL Duration by Response Status, top 25 non-200 status]** Le graphique est similaire au dernier, sauf que l’accent est mis sur les codes d’état non-200 ou les codes d’état d’erreur. Il affiche le code d’erreur, puis l’URL. Il se peut que vous deviez placer le pointeur de la souris sur l’URL pour afficher l’intégralité du chemin. En outre, pour supprimer toutes les URL, sauf une, cliquez sur cette URL. Vous pouvez ensuite réajouter d’autres URL en cliquant dessus individuellement. Si vous souhaitez supprimer des URL individuelles, vous pouvez maintenir la touche enfoncée et cliquer sur chaque URL pour la supprimer du graphique.

## [!UICONTROL Error Count by POP timeline]

![Nombre d’erreurs par journal POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

Le **[!UICONTROL Error Count by POP timeline]** Le graphique affiche le nombre d’états d’erreur le long de la chronologie sélectionnée, facettée par le code d’erreur.

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![Durée par état de réponse, 25 premières adresses IP du client, état non 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

Le **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** Le graphique présente les adresses IP selon la durée moyenne pendant la période sélectionnée, où il y a eu des codes d’erreur d’état.

## [!UICONTROL IP Frequency]

![Fréquence des adresses IP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

Le **[!UICONTROL IP Frequency]** frame comptabilise les états (&#39;MISS&#39; et &#39;PASS&#39;) pour chaque IP de la variable [!DNL Fastly] journaux. Les requêtes Web avec ces états atteignent le serveur d’origine et ajoutent de la charge au serveur. Il affiche les vingt premières adresses en fréquence. Ce cadre peut être utilisé pour détecter les attaques IP ou les sources de charge importante sur un site web. Ce graphique est également présent dans l’onglet Résumé et est placé ici pour faciliter la comparaison avec plus de détails sur la variable [!DNL Fastly] les informations du journal affichées sur cet onglet.
