---
title: Concepts de sécurité Adobe Commerce auto-hébergés
description: Découvrez les idées et concepts de sécurité d’auto-hébergement et les bonnes pratiques à prendre en compte. Découvrez des concepts tels que le système de fichiers en lecture seule, l’analyse de programmes malveillants et de nombreuses autres rubriques à prendre en compte lors de l’hébergement d’adobe commerce.
landing-page-description: Découvrez certains concepts et éléments de sécurité à prendre en compte lors de l’hébergement d’Adobe Commerce par vous-même.
short-description: Découvrez vous-même les stratégies et les concepts de sécurité pour héberger Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: c4912f02-0411-466f-8c77-d610de9eb35d
feature: Install, Security
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---

# Concepts de sécurité

La sécurité doit toujours être une considération forte pour tout ce qui a trait à un projet de commerce électronique. En l&#39;absence d&#39;une forte sécurité, la surface pouvant être attaquée est exponentiellement plus grande. Les concepts et les idées présentés fournissent des méthodes qui ont fait leurs preuves pour réduire les vulnérabilités communes généralement exploitées.

Les concepts suivants ne sont pas dans un ordre particulier. Ils sont censés fournir quelques idées et concepts à prendre en compte. La plupart d’entre eux sont gratuits ou nécessitent une configuration et une configuration minimales ainsi qu’une surveillance ultérieure. Consultez ces rubriques en dehors de ce tutoriel pour vous assurer d’avoir une compréhension suffisante des concepts présentés ici.

## Système de fichiers en lecture seule

Le concept de système de fichiers en lecture seule a été emprunté à [Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. Cela supprime complètement un domaine majeur utilisé par un mauvais acteur. De nombreux exploits ont profité de la modification d’un fichier qui doit se trouver dans l’application Commerce pour éviter toute détection. Au lieu d’en créer un, le mauvais acteur modifie le contenu d’un fichier existant pour effectuer une action inattendue. La lecture seule du système de fichiers réduit considérablement ce vecteur d’attaque.

## Utiliser les gestionnaires d’authentification à deux facteurs et de mot de passe

Ne partagez jamais de mots de passe. Chaque utilisateur administrateur doit disposer de son propre compte avec une liste de contrôle d’accès appropriée. Assurez-vous que deux facteurs d’identification ne sont jamais désactivés ou supprimés. Si vous accordez l’accès administrateur à un tiers, assurez-vous que le mot de passe est généré par un gestionnaire de mot de passe et qu’il n’est jamais réutilisé.

## Analyses de programmes malveillants

Les analyses de programmes malveillants sont généralement trouvées auprès d’un fournisseur d’hébergement qui tente de se spécialiser dans Adobe Commerce. Cette bibliothèque de programmes malveillants et d&#39;exploits connus est une liste de plus en plus longue à mesure que de nouvelles menaces sont découvertes, triées et diagnostiquées. Demandez si le fournisseur d&#39;hébergement dispose d&#39;un tel service et s&#39;il peut être exécuté automatiquement ou uniquement sur demande. Il existe également des services auxquels vous pouvez vous abonner qui peuvent utiliser leur propre bibliothèque d’exploits connus pour vérifier constamment votre application commerciale à la recherche d’exploits. Certaines d’entre elles sont externes uniquement, d’autres peuvent être ajoutées à l’infrastructure afin de fournir une analyse interne approfondie de tous les dossiers, fichiers et même de la base de données. Il y a quelques fournisseurs avec des années d&#39;expérience dans ce domaine, de Sansec.io à Sucuri et bien sûr MageReport. Certaines sont gratuites, d&#39;autres sont associées à un coût. Savoir cela est disponible et avoir une conversation réfléchie avec votre architecte Adobe Commerce et votre équipe DevOps vous assurera de trouver la bonne solution.

## Outil d’analyse à l’échelle du site pour Commerce

Le [Outil d’analyse à l’échelle du site](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} est un outil en libre-service proactif et un référentiel central qui comprend des informations détaillées sur le système et des recommandations pour garantir la sécurité et la maniabilité de votre installation Adobe Commerce. Il fournit 24/7 surveillance des performances, rapports et conseils en temps réel afin d’identifier les problèmes potentiels et d’améliorer la visibilité sur l’intégrité, la sécurité et les configurations d’application du site. Cela permet de réduire le temps de résolution et d’améliorer la stabilité et les performances du site.

## Activation et vérification des paramètres pour la journalisation des actions d’administration

Vous pouvez le trouver après vous être connecté à l’administrateur Adobe Commerce et avoir accédé à Magasins > Configuration > Avancé > Admin > Journalisation des actions d’administration. Vous obtenez ainsi une liste des événements surveillés et enregistrés. Il est utile lors de l’analyse médico-légale sur un site exploité, si la suspicion est qu’ils ont eu accès à l’administrateur Commerce. Cette journalisation et ce rapport peuvent s’avérer utiles pour déterminer les événements que le mauvais acteur a effectués. Si une journalisation des actions d’administration est désactivée, cela signifie que quelqu’un peut les avoir désactivés pour la couverture, supprimez la journalisation lors de l’exécution de certaines actions.

## Serveur bastion pour l’accès ssh

Il est plus difficile d’expliquer que la plupart des rubriques du tutoriel Concepts de sécurité . L’idée de base est de fournir un serveur qui agit comme intermédiaire pour l’accès ssh. Ainsi, vos serveurs de production n’autorisent jamais les connexions ssh externes. Vous pouvez créer ce serveur bastion et utiliser un masque IP local pour vous assurer que seuls les serveurs désignés sont autorisés à y SSH.

## Vérification des rôles et autorisations ACL

Un rôle ACL est affecté à chaque utilisateur administrateur d’Adobe Commerce. Ce rôle doit être créé pour fournir uniquement les fonctionnalités qui doivent effectuer la tâche. Les rôles ACL doivent être souvent évalués, afin de s’assurer qu’ils ne procurent pas plus d’autorité que nécessaire. Si nécessaire, créez de nombreux rôles ACL avec des responsabilités. Si l’accès est accordé à un tiers pour une raison quelconque, il doit être désactivé dès que possible. Demandez-leur combien de temps ils ont absolument besoin d’accéder à et définissez une date d’expiration automatique lors de la création de leur utilisateur administrateur.

## Vérifier l’accès fréquent des utilisateurs administrateurs et des utilisateurs SSH

Pour détecter une création d’utilisateurs administrateurs non souhaitée ou non autorisée, la liste des utilisateurs administrateurs doit faire l’objet d’un audit fréquent. Une bonne règle consiste à vérifier tous les mois qui dispose d’un accès SSH et administrateur à l’application Adobe Commerce. Si de nouveaux utilisateurs sont détectés, désactivez leur compte et suivez la politique et la procédure de l’entreprise pour un tel incident. Il est plus facile de rétablir l’accès d’un utilisateur que de récupérer d’un exploit.

## Nettoyage de la base

Limitez l’accès aux données de production. Ces coéquipiers désignés devraient avoir la possibilité de retirer les bases de données de production et de les nettoyer des données réelles. Si la suppression des données est une option, tronquez les tableaux appropriés tels que les commandes, les devis et les clients. Cependant, il arrive parfois que vous souhaitiez l’ensemble complet des données, mais les valeurs peuvent être rendues anonymes. Cela est généralement vrai dans un environnement d’évaluation. Elle est également utile avant les mises à niveau. En disposant du volume réel de données, mais en étant anonyme, vous êtes certain de tester et de valider le temps d’exécution d’un déploiement en vue de la mise à niveau. Si vous disposez d’un ensemble limité de données, vous pouvez sous-estimer le processus de mise à niveau et le timing.

+++Exemple d’informations sur les clients de manière aléatoire Voici un exemple pour savoir comment modifier l’adresse email des clients avec une chaîne aléatoire et tous les champs de prénom et de dernier cri dans certaines tables standard où Adobe Commerce stocke des données. **N’oubliez pas de vérifier toutes les tables pour les données sensibles. Cette liste n’inclut pas toutes les tables susceptibles de stocker les données clients.**

```SQL
SET FOREIGN_KEY_CHECKS=0;
UPDATE customer_entity SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE email_contact SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE sales_invoice_grid SET customer_email = 'customer@example.com', customer_name  = 'Jack Smith';
UPDATE sales_order SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Smith', remote_ip = '127.0.0.1';
UPDATE sales_order_address SET region = 'Ohio', postcode = '12345-1234', lastname = 'Smith', street = '123 Main street', region_id = 44, city = 'Phoenix', telephone = NULL, firstname = 'Jane', company = NULL;
UPDATE sales_order_grid SET customer_email = 'customer@example.com', shipping_name = 'Jack', billing_name = 'Jack Smith', billing_address = '123 Main Street', shipping_address = '321 Pine Street', customer_name = 'Jane Smith';
UPDATE sales_shipment_grid SET customer_email = 'customer@example.com', customer_name = 'Jane Smith', billing_address = '123 Main street', billing_name = 'Jack Doe', shipping_name = 'Susie Smith';
UPDATE quote SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Jones', customer_dob = NULL, remote_ip = '127.0.0.1';
UPDATE quote_address SET email = 'customer@example.com', firstname = 'Jack', lastname = 'Smith', company = NULL, street = '123 Main st', city = 'AnyCity', region = 'Some State', region_id = 44, postcode = '12345-1234', telephone = NULL;
UPDATE magento_rma SET customer_custom_email = 'customer@example.com' WHERE customer_custom_email IS NOT NULL;
UPDATE customer_address_entity SET firstname = 'Jack', lastname = 'Smith', telephone = '909-555-1212', postcode = NULL,  region = NULL, street = '123 Main street', city = 'Anycity', company = NULL;
UPDATE customer_grid_flat SET name = 'Jane Doe', email = 'customer@example.com', dob = NULL, gender = NULL, taxvat = NULL, shipping_full = '', billing_full = '', billing_firstname = 'Jack', billing_lastname = 'Smith', billing_telephone = NULL, billing_postcode = NULL, billing_country_id = NULL, billing_region = NULL, billing_street = '123 Main street', billing_city = 'Anycity', billing_fax = NULL, billing_vat_id = NULL, billing_company = NULL;
UPDATE sales_creditmemo_grid SET billing_name = 'Sally', billing_address = '123 Main Street', customer_name = 'Jack Smith', customer_email = 'customer@example.com';
    
UPDATE magento_rma_grid SET customer_name = 'Jack Smith';
SET FOREIGN_KEY_CHECKS=1;
```

+++


+++Vous pouvez également tronquer les tableaux au lieu d’essayer d’anonymiser

```SQL
SET FOREIGN_KEY_CHECKS=0;
TRUNCATE customer_log;  
TRUNCATE customer_visitor;  
TRUNCATE magento_logging_event;
TRUNCATE oauth_consumer;
TRUNCATE oauth_nonce;
TRUNCATE oauth_token;
TRUNCATE password_reset_request_event;
TRUNCATE acknowledgement;
TRUNCATE acknowledgement_report;
TRUNCATE avatax_log;
TRUNCATE avatax_queue;
TRUNCATE cron_schedule;
SET FOREIGN_KEY_CHECKS=1;
```

+++

+++Supprimer complètement les informations Exemple Voici un exemple pour supprimer toutes les commandes, devis, notes de crédit, etc. avant le lancement ou pour un environnement de développement inférieur.

```SQL
DELETE FROM `gift_message`;
DELETE FROM `inventory_reservation`;
DELETE FROM `quote`;
DELETE FROM `quote_address`;
DELETE FROM `quote_address_item`;
DELETE FROM `quote_id_mask`;
DELETE FROM `quote_item`;
DELETE FROM `quote_item_option`;
DELETE FROM `quote_payment`;
DELETE FROM `quote_shipping_rate`;
DELETE FROM `reporting_orders`;
DELETE FROM `sales_bestsellers_aggregated_daily`;
DELETE FROM `sales_bestsellers_aggregated_monthly`;
DELETE FROM `sales_bestsellers_aggregated_yearly`;
DELETE FROM `sales_creditmemo`;
DELETE FROM `sales_creditmemo_comment`;
DELETE FROM `sales_creditmemo_grid`;
DELETE FROM `sales_creditmemo_item`;
DELETE FROM `sales_invoice`;
DELETE FROM `sales_invoiced_aggregated`;
DELETE FROM `sales_invoiced_aggregated_order`;
DELETE FROM `sales_invoice_comment`;
DELETE FROM `sales_invoice_grid`;
DELETE FROM `sales_invoice_item`;
DELETE FROM `sales_order`;
DELETE FROM `sales_order_address`;
DELETE FROM `sales_order_aggregated_created`;
DELETE FROM `sales_order_aggregated_updated`;
DELETE FROM `sales_order_grid`;
DELETE FROM `sales_order_item`;
DELETE FROM `sales_order_payment`;
DELETE FROM `sales_order_status_history`;
DELETE FROM `sales_order_tax`;
DELETE FROM `sales_order_tax_item`;
DELETE FROM `sales_payment_transaction`;
DELETE FROM `sales_refunded_aggregated`;
DELETE FROM `sales_refunded_aggregated_order`;
DELETE FROM `sales_shipment`;
DELETE FROM `sales_shipment_comment`;
DELETE FROM `sales_shipment_grid`;
DELETE FROM `sales_shipment_item`;
DELETE FROM `sales_shipment_track`;
DELETE FROM `sales_shipping_aggregated`;
DELETE FROM `sales_shipping_aggregated_order`;
DELETE FROM `tax_order_aggregated_created`;
DELETE FROM `tax_order_aggregated_updated`;
DELETE FROM `magento_rma`;
DELETE FROM `magento_rma_grid`;
DELETE FROM `magento_rma_item_entity`;
DELETE FROM `magento_rma_status_history`;
DELETE FROM `magento_sales_creditmemo_grid_archive`;
DELETE FROM `magento_sales_invoice_grid_archive`;
DELETE FROM `magento_sales_order_grid_archive`;
DELETE FROM `magento_sales_shipment_grid_archive`;
DELETE FROM `sequence_creditmemo_0`;
DELETE FROM `sequence_creditmemo_1`;
DELETE FROM `sequence_creditmemo_2`;
DELETE FROM `sequence_creditmemo_7`;
DELETE FROM `sequence_invoice_0`;
DELETE FROM `sequence_invoice_1`;
DELETE FROM `sequence_invoice_2`;
DELETE FROM `sequence_invoice_7`;
DELETE FROM `sequence_order_0`;
DELETE FROM `sequence_order_1`;
DELETE FROM `sequence_order_2`;
DELETE FROM `sequence_order_7`;
DELETE FROM `sequence_rma_item_0`;
DELETE FROM `sequence_rma_item_1`;
DELETE FROM `sequence_rma_item_2`;
DELETE FROM `sequence_rma_item_7`;
DELETE FROM `sequence_shipment_0`;
DELETE FROM `sequence_shipment_1`;
DELETE FROM `sequence_shipment_2`;
DELETE FROM `sequence_shipment_7`;

## USE THE FOLLOWING WITH CAUTION - CAN CAUSE ISSUES WITH TAX/PAYMENT PROCESSORS IF YOU REUSE ORDER NUMBERS, ETC.

ALTER TABLE sequence_creditmemo_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_7 AUTO_INCREMENT=1;
```

+++

## Utilisation des variables d’environnement

[!BADGE Adobe Commerce dans le cloud uniquement]{type=Informative}

L’utilisation de variables d’environnement vous permet de définir certaines valeurs qui peuvent et doivent être modifiées pour chaque environnement. Par exemple, vous souhaitez peut-être avoir une URL d’administration différente pour chaque environnement. En définissant cette valeur comme variable d’environnement, vous pouvez la configurer et la référencer rapidement à partir de l’interface utilisateur de Cloud, le cas échéant.

Vous pouvez en savoir plus sur ce sujet dans Experience League [Variables d’environnement de l’infrastructure Commerce on Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## Outils d’analyse des vulnérabilités des logiciels

Le pipeline CI/CD peut être un outil puissant qui permet d’automatiser certaines tâches. En particulier, la possibilité pour un développeur de valider un code qui peut être exploitable est toujours une possibilité réelle. Les examens de code par les pairs capturent normalement de tels éléments, mais comme c&#39;est un être humain, des erreurs se produisent. L’analyse automatisée du code permet de réduire les risques de vulnérabilités inattendues au sein d’une nouvelle fonctionnalité introduite. Ces outils peuvent même être en place pour bloquer la fusion du code dans le code base en direct. Il existe de nombreuses façons et outils d’offrir la sécurité du code automatisée et des analyses de qualité. Il peut exister des outils développés personnalisés robustes, mais ils nécessitent des mises à jour et des ajustements constants. Une alternative consiste à appliquer des outils mis à jour de manière proactive tels que synk.io et l’Inspecteur de code Amazon.

## Pare-feu d’applications web

Un pare-feu d’application web ou WAF, comme il est souvent utilisé lors de la communication avec DevOps ou un fournisseur d’hébergement.

Les pare-feu d’applications web (WAF) empêchent le trafic malveillant d’entrer sur les sites et les réseaux en filtrant le trafic par rapport à un ensemble de règles de sécurité. Le trafic qui déclenche l’une des règles est bloqué avant qu’il puisse endommager vos sites ou votre réseau.

Adobe Commerce cloud WAF fournit une stratégie WAF avec un ensemble de règles conçu pour protéger vos applications web Adobe Commerce d’un large éventail d’attaques. Si vous choisissez une option d’auto-hébergement, il vous appartient de trouver un WAF et de configurer les règles. Certains fournisseurs d’hébergement et fournisseurs WAF disposent d’un ensemble générique de règles qui sont un bon début, mais attendez-vous à ce que certains travaux fonctionnent pour votre projet.

Le WAF examine le trafic Web et administratif pour identifier toute activité suspecte. Il évalue le trafic de GET et de POST (appels API HTTP) et applique l’ensemble de règles pour déterminer le trafic à bloquer. La WAF peut bloquer un large éventail d’attaques, y compris des attaques par injection SQL, des attaques par script intersite, des attaques par exfiltration de données et des violations de protocole HTTP.

En tant que service basé sur le cloud, le WAF ne nécessite aucun matériel ou logiciel à installer ou à gérer. Rapidement, un partenaire technologique existant, fournit le logiciel et l&#39;expertise. Leur haute performance, le WAF toujours actif, réside dans chaque noeud de cache sur le réseau de diffusion global de Fastly.

Pour plus d’informations sur la méthode WAF sur Adobe Commerce sur le cloud fourni par Fastly, consultez la [FAQ sur la base de connaissances Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
