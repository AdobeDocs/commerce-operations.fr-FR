---
title: Référence sur les chemins de configuration de l’extension B2B
description: Consultez la liste des valeurs de configuration liées à B2B.
feature: Configuration, B2B, Companies, Payments, Quotes
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# Référence sur les chemins de configuration de l’extension B2B

_Cette option est disponible pour les instances avec B2B pour Adobe Commerce installées._

Cette rubrique répertorie les chemins de configuration de l’extension Commerce Enterprise B2B. La variable [`magento app:config:dump` command](../cli/export-configuration.md) écrit ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit être dans le contrôle source.

>[!INFO]
>
>Ces listes de référence _only_ chemins de configuration uniques à B2B pour Adobe Commerce. Cette extension comprend tous les chemins de configuration pour Adobe Commerce.

Pour ces chemins de configuration, voir :

- [Chemins de configuration des paiements](config-reference-payment.md)
- [Référence des chemins de configuration sensibles et spécifiques au système](config-reference-sens.md)

Pour éventuellement remplacer des paramètres de configuration ou définir des paramètres sensibles, voir [Utilisation des variables d’environnement pour remplacer les paramètres de configuration](override-config-settings.md#environment-variables).

## Catégorie générale

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’Admin sous **[!UICONTROL Stores]** > Paramètres > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### Chemins des fonctionnalités B2B

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **[!UICONTROL Stores]** > Paramètres > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensibles ? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Activer la société | `btob/website_configuration/company_active` | | | |
| Activation du catalogue partagé | `btob/website_configuration/sharedcatalog_active` | | | |
| Activer les guillemets B2B | `btob/website_configuration/negotiablequote_active` | | | |
| Activer l’ordre rapide | `btob/website_configuration/quickorder_active` | | | |
| Activer la liste de demandes | `btob/website_configuration/requisition_list_active` | | | |
| Méthodes de paiement applicables | `btob/default_b2b_payment_methods/applicable_payment_methods` | | | |
| Méthodes de paiement | `btob/default_b2b_payment_methods/available_payment_methods` | | | |

{style="table-layout:auto"}

## Catégorie de clients

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’Admin sous **[!UICONTROL Stores]** > Paramètres > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### Chemins de configuration de l’entreprise

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **[!UICONTROL Stores]** > Paramètres > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|
| Autorisation de l’enregistrement des entreprises à partir de Storefront | `company/general/allow_company_registration` | | | |
| Destinataire de l’e-mail d’enregistrement de société | `company/email/company_registration` | | | ![Sensibilité](/help/assets/configuration/cloud-sens.png) |
| Envoyer une copie de courrier électronique d’enregistrement de société à | `company/email/company_registration_copy` | | | ![Sensibilité](/help/assets/configuration/cloud-sens.png) |
| Méthode d’envoi de copie de courrier électronique | `company/email/company_copy_method` | | | |
| Email d’enregistrement de société par défaut | `company/email/company_notify_admin_template` | | | |
| Emails liés au client | `company/email/heading_customer` | | | |
| Adresse électronique du représentant commercial par défaut | `company/email/customer_sales_representative_template` | | | |
| Attribuer la société par défaut à l’adresse électronique du client | `company/email/customer_company_customer_assign_template` | | | |
| Adresse électronique de l’administrateur de la société d’affectation par défaut | `company/email/customer_assign_super_user_template` | | | |
| Email inactif de l’administrateur de société par défaut | `company/email/customer_inactivate_super_user_template` | | | |
| L’administrateur de la société par défaut a été remplacé par Email de membre. | `company/email/customer_remove_super_user_template` | | | |
| Email actif d’état client par défaut | `company/email/customer_account_activated_template` | | | |
| Email inactif d’état client par défaut | `company/email/customer_account_locked_template` | | | |
| Changement d’état de la société | `company/email/heading_company_status` | | | |
| Destinataire de l’email de changement d’état de la société | `company/email/company_status_change` | | | |
| Envoyer la copie de l’état de la société | `company/email/company_status_change_copy` | | | ![Sensibilité](/help/assets/configuration/cloud-sens.png) |
| Méthode d’envoi de copie de courrier électronique | `company/email/company_status_copy_method` | | | |
| Par Défaut, Changement De L’État De L’Entreprise En 1 Courrier Électronique Actif | `company/email/company_status_pending_approval_to_active_template` | | | |
| La Modification De L’État De L’Entreprise Par Défaut A Été Actif 2 Email. | `company/email/company_status_rejected_blocked_to_active_template` | | | |
| Changement de l’état de l’entreprise par défaut en email rejeté | `company/email/company_status_rejected_template` | | | |
| Modification de l’état de l’entreprise par défaut pour bloquer l’adresse électronique | `company/email/company_status_blocked_template` | | | |
| Par Défaut, Changement D’État De L’Entreprise En Attente D’Un Email D’Approbation | `company/email/company_status_pending_approval_template` | | | |
| Crédit de la société | `company/email/heading_company_credit` | | | |
| Changement de crédit d’entreprise Expéditeur d’email | `company/email/company_credit_change` |  | | ![Sensibilité](/help/assets/configuration/cloud-sens.png) |
| Envoyer la copie de courrier électronique du crédit de la société | `company/email/company_credit_change_copy` | | | |
| Méthode d’envoi de copie de courrier électronique | `company/email/company_credit_copy_method` | | | |
| Modèle de courrier électronique attribué | `company/email/credit_allocated_email_template` | | | |
| Modèle de courrier électronique mis à jour | `company/email/credit_updated_email_template` | | | |
| Modèle d&#39;email remboursé | `company/email/credit_reimbursed_email_template` | | | |
| Modèle de courrier électronique remboursé | `company/email/credit_refunded_email_template` | | | |
| Modèle de courrier électronique rétabli | `company/email/credit_reverted_email_template` | | | |

{style="table-layout:auto"}

### Chemins des listes de demandes

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Clients** > **Listes de demandes**.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensibles ? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Nombre de listes de demandes d’approvisionnement | `requisitionlist/general/number_requisition_lists` | | | |

{style="table-layout:auto"}

## Catégorie de ventes

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’Admin sous **Magasins** > Paramètres > **Configuration** > **Ventes**.

### Chemins des emails de vente

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Ventes** > **Courriers électroniques de vente**.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensibles ? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Activé | `sales_email/quote/enabled` | | | |
| Modèle de devis mis à jour (pour l’achat) | `sales_email/quote/updated_buyer_template` | | | |
| Modèle de devis décliné (à l’achat) | `sales_email/quote/declined_buyer_template` | | | |
| Nouveau modèle de devis (au vendeur) | `sales_email/quote/new_seller_template` | | | |
| Mise à jour du modèle de devis (au vendeur) | `sales_email/quote/updated_seller_template` | | | |
| Expiration des citations (en 48 heures) | `sales_email/quote/expire_two_days_template` | | | |
| Expiration des citations (en 24 heures) | `sales_email/quote/expire_one_day_template` | | | |
| Réinitialisation de la date d’expiration | `sales_email/quote/expire_reset_template` | | | |
| Envoyer une copie de devis à | `sales_email/quote/copy_to` | | | ![Sensibilité](/help/assets/configuration/cloud-sens.png) |
| Méthode Envoyer une copie de courrier électronique citée | `sales_email/quote/copy_method` | | | |

{style="table-layout:auto"}

### Chemins des citations

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Ventes** > **Guillemets**.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensibles ? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Quantité minimale | `quote/general/minimum_amount` | | | |
| Message Montant minimum | `quote/general/minimum_amount_message` | | | |
| Période d’expiration par défaut | `quote/general/default_expiration_period` | | | |
| Formats de fichier à charger | `quote/attached_files/file_formats` | | | |
| Taille maximale du fichier | `quote/attached_files/maximum_file_size` | | | |
| Quantité minimale | `quote/general/minimum_amount` | | | |
| Message Montant minimum | `quote/general/minimum_amount_message` | | | |
| Période d’expiration par défaut | `quote/general/default_expiration_period` | | | |
| Formats de fichier à charger | `quote/attached_files/file_formats` | | | |
| Taille maximale du fichier | `quote/attached_files/maximum_file_size` | | | |

{style="table-layout:auto"}

## Chemins des méthodes de paiement

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Ventes** > **Méthodes de paiement**.

>[!INFO]
>
>Les chemins disponibles sont déterminés par votre choix de pays marchand.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensibles ? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Activé | `payment/au/companycredit/active` | | | |
| Titre | `payment/au/companycredit/title` | | | |
| New Order Status | `payment/au/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/au/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/au/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/au/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/au/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/au/companycredit/sort_order` | | | |
| Activé | `payment/es/companycredit/active` | | | |
| Titre | `payment/es/companycredit/title` | | | |
| New Order Status | `payment/es/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/es/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/es/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/es/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/es/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/es/companycredit/sort_order` | | | |
| Activé | `payment/companycredit/active` | | | |
| Titre | `payment/companycredit/title` | | | |
| New Order Status | `payment/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/companycredit/sort_order` | | | |
| Activé | `payment/nz/companycredit/active` | | | |
| Titre | `payment/nz/companycredit/title` | | | |
| New Order Status | `payment/nz/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/nz/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/nz/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/nz/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/nz/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/nz/companycredit/sort_order` | | | |
| Activé | `payment/us/companycredit/active` | | | |
| Titre | `payment/us/companycredit/title` | | | |
| New Order Status | `payment/us/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/us/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/us/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/us/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/us/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/us/companycredit/sort_order` | | | |
| Activé | `payment/gb/companycredit/active` | | | |
| Titre | `payment/gb/companycredit/title` | | | |
| New Order Status | `payment/gb/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/gb/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/gb/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/gb/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/gb/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/gb/companycredit/sort_order` | | | |
| Activé | `payment/de/companycredit/active` | | | |
| Titre | `payment/de/companycredit/title` | | | |
| New Order Status | `payment/de/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/de/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/de/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/de/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/de/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/de/companycredit/sort_order` | | | |
| Activé | `payment/other/companycredit/active` | | | |
| Titre | `payment/other/companycredit/title` | | | |
| New Order Status | `payment/other/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/other/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/other/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/other/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/other/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/other/companycredit/sort_order` | | | |
| Activé | `payment/ca/companycredit/active` | | | |
| Titre | `payment/ca/companycredit/title` | | | |
| New Order Status | `payment/ca/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/ca/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/ca/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/ca/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/ca/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/ca/companycredit/sort_order` | | | |
| Activé | `payment/hk/companycredit/active` | | | |
| Titre | `payment/hk/companycredit/title` | | | |
| New Order Status | `payment/hk/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/hk/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/hk/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/hk/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/hk/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/hk/companycredit/sort_order` | | | |
| Activé | `payment/jp/companycredit/active` | | | |
| Titre | `payment/jp/companycredit/title` | | | |
| New Order Status | `payment/jp/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/jp/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/jp/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/jp/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/jp/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/jp/companycredit/sort_order` | | | |
| Activé | `payment/fr/companycredit/active` | | | |
| Titre | `payment/fr/companycredit/title` | | | |
| New Order Status | `payment/fr/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/fr/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/fr/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/fr/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/fr/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/fr/companycredit/sort_order` | | | |
| Activé | `payment/it/companycredit/active` | | | |
| Titre | `payment/it/companycredit/title` | | | |
| New Order Status | `payment/it/companycredit/order_status` | | | |
| Paiement par les pays applicables | `payment/it/companycredit/allowspecific` | | | |
| Paiement par pays spécifique | `payment/it/companycredit/specificcountry` | | | |
| Total de la commande minimale | `payment/it/companycredit/min_order_total` | | | |
| Total de la commande maximale | `payment/it/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/it/companycredit/sort_order` | | | |

{style="table-layout:auto"}
