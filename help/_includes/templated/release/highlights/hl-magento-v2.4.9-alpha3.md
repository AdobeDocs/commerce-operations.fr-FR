---
source-git-commit: 233ff6d5de2f4da3d477e70d066dd5cd46c771ee
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---
# Notes de mise à jour de Magento Open Source (v2.4.9-alpha3)

## Caractéristiques de la version v2.4.9-alpha3

Les points forts suivants s’appliquent à la version 2.4.9-alpha3 de Magento Open Source.

### Braintree

#### Mise en chambre forte de Google Pay via la zone Compte

Dans Magento 2.4.9-alpha3, les clients peuvent désormais archiver leurs cartes Google Pay dans la zone de compte lorsque Google Pay Vault est activé dans Braintree. Les cartes voûtées apparaissent sous les modes de paiement stockés, peuvent être utilisées pour les achats futurs au moment du passage en caisse et peuvent être supprimées par le client. Cela étend la prise en charge des coffres-forts au-delà des cartes et de PayPal à Google Pay.

_LOT-3459_

#### Lier la commande Magento à la commande du portail Braintree

Dans Magento 2.4.9-alpha3, un lien de portail Braintree est désormais ajouté aux détails de la commande dans l’Administration Magento. Cliquez sur le lien pour ouvrir la transaction associée sur le portail Braintree (dans un nouvel onglet), à l’aide des identifiants de commerçant et de transaction de la commande Magento. Cela permet des références croisées directes sans se connecter séparément aux deux systèmes.

_LOT-3461_

#### Real-Time Account Updater (RTAU)

La fonction Real-Time Account Updater (RTAU) de Magento 2.4.9-alpha3 for Braintree garantit que les informations de carte Visa, Mastercard et Discover sont automatiquement mises à jour lorsque les cartes expirent ou sont remplacées. Cela réduit les paiements en échec, maintient Magento Vault à jour et ignore les types non pris en charge (prépayé, Apple Pay, Google Pay) sans erreur.

_LOT-3462_

#### Prise en charge du type de carte ELO pour les paiements par carte Braintree

Dans Magento 2.4.9-alpha3, la prise en charge du type de carte ELO a été ajoutée à Braintree Payments. Les administrateurs peuvent désormais activer l’ELO dans la configuration des cartes de crédit et les clients peuvent passer des commandes avec les cartes ELO au moment du passage en caisse, ce qui garantit des transactions transparentes via Braintree.

_LOT-3464_

### Framework

#### Migration de RabbitMQ vers Apache ActiveMQ

_AC-14558_

#### Mettez à niveau la dépendance chart.js vers la dernière version

La dépendance chart.js est mise à niveau vers la dernière version 4.5.0

_AC-15133 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Migration depuis Laminas MVC

Adobe Commerce a introduit une implémentation native de MVC, qui remplace l’ancien MVC Laminas, afin d’assurer la compatibilité et la stabilité à long terme au-delà de PHP 8.5. Cette modification renforce les performances, réduit les dépendances externes et fournit une base plus évolutive pour Commerce

_AC-15160_
