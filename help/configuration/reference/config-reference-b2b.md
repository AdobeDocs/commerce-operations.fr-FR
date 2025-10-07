---
title: Référence des chemins de configuration de l’extension B2B
description: Découvrez les chemins et les valeurs de configuration de l’extension B2B pour Adobe Commerce. Découvrez les options de configuration spécifiques à l’entreprise, au paiement, au devis et au B2B.
feature: Configuration, B2B, Companies, Payments, Quotes
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 0%

---

# Référence des chemins de configuration de l’extension B2B

_Cette option est disponible pour les instances où le B2B pour Adobe Commerce est installé._

Cette rubrique répertorie les chemins de configuration pour l’extension Commerce Enterprise B2B. La commande [`magento app:config:dump` écrit ](../cli/export-configuration.md) ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit se trouver dans le contrôle de code source.

>[!INFO]
>
>Cette référence répertorie _uniquement_ les chemins de configuration uniques au B2B pour Adobe Commerce. Cette extension comprend tous les chemins de configuration pour Adobe Commerce.

Pour ces chemins de configuration, voir :

- [Chemins de configuration des paiements](config-reference-payment.md)
- [Référence des chemins de configuration sensibles et spécifiques au système](config-reference-sens.md)

Pour remplacer éventuellement des paramètres de configuration ou définir des paramètres sensibles, voir [Utiliser des variables d’environnement pour remplacer des paramètres de configuration](override-config-settings.md#environment-variables).

## Catégorie générale

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **[!UICONTROL Stores]** > Paramètres > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### Chemins d’accès aux fonctionnalités B2B

Ces valeurs de configuration sont disponibles dans Admin dans **[!UICONTROL Stores]** > Paramètres > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensible ? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Activer la société | `btob/website_configuration/company_active` | | | |
| Activer le catalogue partagé | `btob/website_configuration/sharedcatalog_active` | | | |
| Activer le devis B2B | `btob/website_configuration/negotiablequote_active` | | | |
| Activer la commande rapide | `btob/website_configuration/quickorder_active` | | | |
| Activer la liste des demandes d&#39;approvisionnement | `btob/website_configuration/requisition_list_active` | | | |
| Modes de paiement applicables | `btob/default_b2b_payment_methods/applicable_payment_methods` | | | |
| Modes de paiement | `btob/default_b2b_payment_methods/available_payment_methods` | | | |

{style="table-layout:auto"}

## Catégorie de clients

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **[!UICONTROL Stores]** > Paramètres > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### Chemins de configuration d’entreprise

Ces valeurs de configuration sont disponibles dans Admin dans **[!UICONTROL Stores]** > Paramètres > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|
| Autoriser l’enregistrement d’entreprise à partir du storefront | `company/general/allow_company_registration` | | | |
| Destinataire de l&#39;e-mail d&#39;enregistrement de l&#39;entreprise | `company/email/company_registration` | | | ![ Sensible ](/help/assets/configuration/cloud-sens.png) |
| Envoyer La Copie De L&#39;E-Mail D&#39;Enregistrement De L&#39;Entreprise À | `company/email/company_registration_copy` | | | ![ Sensible ](/help/assets/configuration/cloud-sens.png) |
| Méthode envoi de copie d’e-mail | `company/email/company_copy_method` | | | |
| E-mail d&#39;enregistrement d&#39;entreprise par défaut | `company/email/company_notify_admin_template` | | | |
| E-Mails Relatifs Aux Clients | `company/email/heading_customer` | | | |
| Adresse e-mail par défaut du représentant commercial affecté | `company/email/customer_sales_representative_template` | | | |
| E-mail Affecter une entreprise par défaut au client | `company/email/customer_company_customer_assign_template` | | | |
| E-mail par défaut Affecter un administrateur d’entreprise | `company/email/customer_assign_super_user_template` | | | |
| E-mail inactif d’administration de société par défaut | `company/email/customer_inactivate_super_user_template` | | | |
| L’Administrateur D’Entreprise Par Défaut A Été Remplacé Par L’Adresse E-Mail Du Membre | `company/email/customer_remove_super_user_template` | | | |
| E-mail actif du statut client par défaut | `company/email/customer_account_activated_template` | | | |
| E-mail de statut client par défaut inactif | `company/email/customer_account_locked_template` | | | |
| Changement de statut de l&#39;entreprise | `company/email/heading_company_status` | | | |
| Destinataire de l&#39;e-mail de changement de statut de l&#39;entreprise | `company/email/company_status_change` | | | |
| Envoyer La Copie D&#39;E-Mail De Changement De Statut De La Société À | `company/email/company_status_change_copy` | | | ![ Sensible ](/help/assets/configuration/cloud-sens.png) |
| Méthode envoi de copie d’e-mail | `company/email/company_status_copy_method` | | | |
| Le Statut Par Défaut De La Société Est Remplacé Par Actif 1 E-Mail | `company/email/company_status_pending_approval_to_active_template` | | | |
| Le Statut D&#39;Entreprise Par Défaut Est Remplacé Par Actif 2 E-Mail | `company/email/company_status_rejected_blocked_to_active_template` | | | |
| Le Statut D&#39;Entreprise Par Défaut Est Remplacé Par E-Mail Rejeté | `company/email/company_status_rejected_template` | | | |
| Le Statut Par Défaut De L’Entreprise Est Remplacé Par E-Mail Bloqué | `company/email/company_status_blocked_template` | | | |
| Le Statut Par Défaut De La Société A Été Remplacé Par E-Mail En Attente D&#39;Approbation | `company/email/company_status_pending_approval_template` | | | |
| Crédit d&#39;entreprise | `company/email/heading_company_credit` | | | |
| Modifier le crédit de la société pour l&#39;expéditeur de l&#39;e-mail | `company/email/company_credit_change` |  | | ![ Sensible ](/help/assets/configuration/cloud-sens.png) |
| Envoyer La Copie D&#39;E-Mail De Modification Du Crédit De La Société À | `company/email/company_credit_change_copy` | | | |
| Méthode envoi de copie d’e-mail | `company/email/company_credit_copy_method` | | | |
| Modèle d’e-mail alloué | `company/email/credit_allocated_email_template` | | | |
| Modèle d’e-mail mis à jour | `company/email/credit_updated_email_template` | | | |
| Modèle d’e-mail de remboursement | `company/email/credit_reimbursed_email_template` | | | |
| Modèle d’e-mail de remboursement | `company/email/credit_refunded_email_template` | | | |
| Modèle d’e-mail annulé | `company/email/credit_reverted_email_template` | | | |

{style="table-layout:auto"}

### Chemins d&#39;accès aux listes de demandes d&#39;approvisionnement

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Clients** > **Listes de demandes**.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensible ? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Nombre de listes de demandes internes | `requisitionlist/general/number_requisition_lists` | | | |

{style="table-layout:auto"}

## Catégorie de vente

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Ventes**.

### Chemins d’accès aux e-mails de vente

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Emails commerciaux**.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensible ? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Activé | `sales_email/quote/enabled` | | | |
| Modèle de devis mis à jour (pour l&#39;acheteur) | `sales_email/quote/updated_buyer_template` | | | |
| Modèle de devis refusé (à l&#39;acheteur) | `sales_email/quote/declined_buyer_template` | | | |
| Nouveau modèle de devis (au vendeur) | `sales_email/quote/new_seller_template` | | | |
| Modèle de devis mis à jour (pour le vendeur) | `sales_email/quote/updated_seller_template` | | | |
| Expiration du devis (dans 48 heures) | `sales_email/quote/expire_two_days_template` | | | |
| Expiration du devis (dans 24 heures) | `sales_email/quote/expire_one_day_template` | | | |
| Date d’expiration réinitialisée | `sales_email/quote/expire_reset_template` | | | |
| Envoyer La Copie De L&#39;E-Mail Du Devis À | `sales_email/quote/copy_to` | | | ![ Sensible ](/help/assets/configuration/cloud-sens.png) |
| Méthode de copie d&#39;e-mail de devis d&#39;envoi | `sales_email/quote/copy_method` | | | |

{style="table-layout:auto"}

### Chemins d’accès aux citations

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Devis**.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensible ? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Montant minimal | `quote/general/minimum_amount` | | | |
| Message relatif au montant minimum | `quote/general/minimum_amount_message` | | | |
| Délai d’expiration par défaut | `quote/general/default_expiration_period` | | | |
| Formats de fichiers pour le chargement | `quote/attached_files/file_formats` | | | |
| Taille de fichier maximale | `quote/attached_files/maximum_file_size` | | | |
| Montant minimal | `quote/general/minimum_amount` | | | |
| Message relatif au montant minimum | `quote/general/minimum_amount_message` | | | |
| Délai d’expiration par défaut | `quote/general/default_expiration_period` | | | |
| Formats de fichiers pour le chargement | `quote/attached_files/file_formats` | | | |
| Taille de fichier maximale | `quote/attached_files/maximum_file_size` | | | |

{style="table-layout:auto"}

## Chemins d’accès au mode de paiement

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Modes de paiement**.

>[!INFO]
>
>Les chemins disponibles sont déterminés par votre choix de pays marchand.

| Nom | Chemin de configuration | Chiffré ? | Spécifique au système ? | Sensible ? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Activé | `payment/au/companycredit/active` | | | |
| Titre | `payment/au/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/au/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/au/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/au/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/au/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/au/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/au/companycredit/sort_order` | | | |
| Activé | `payment/es/companycredit/active` | | | |
| Titre | `payment/es/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/es/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/es/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/es/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/es/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/es/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/es/companycredit/sort_order` | | | |
| Activé | `payment/companycredit/active` | | | |
| Titre | `payment/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/companycredit/sort_order` | | | |
| Activé | `payment/nz/companycredit/active` | | | |
| Titre | `payment/nz/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/nz/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/nz/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/nz/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/nz/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/nz/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/nz/companycredit/sort_order` | | | |
| Activé | `payment/us/companycredit/active` | | | |
| Titre | `payment/us/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/us/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/us/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/us/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/us/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/us/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/us/companycredit/sort_order` | | | |
| Activé | `payment/gb/companycredit/active` | | | |
| Titre | `payment/gb/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/gb/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/gb/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/gb/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/gb/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/gb/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/gb/companycredit/sort_order` | | | |
| Activé | `payment/de/companycredit/active` | | | |
| Titre | `payment/de/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/de/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/de/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/de/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/de/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/de/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/de/companycredit/sort_order` | | | |
| Activé | `payment/other/companycredit/active` | | | |
| Titre | `payment/other/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/other/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/other/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/other/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/other/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/other/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/other/companycredit/sort_order` | | | |
| Activé | `payment/ca/companycredit/active` | | | |
| Titre | `payment/ca/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/ca/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/ca/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/ca/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/ca/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/ca/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/ca/companycredit/sort_order` | | | |
| Activé | `payment/hk/companycredit/active` | | | |
| Titre | `payment/hk/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/hk/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/hk/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/hk/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/hk/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/hk/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/hk/companycredit/sort_order` | | | |
| Activé | `payment/jp/companycredit/active` | | | |
| Titre | `payment/jp/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/jp/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/jp/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/jp/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/jp/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/jp/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/jp/companycredit/sort_order` | | | |
| Activé | `payment/fr/companycredit/active` | | | |
| Titre | `payment/fr/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/fr/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/fr/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/fr/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/fr/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/fr/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/fr/companycredit/sort_order` | | | |
| Activé | `payment/it/companycredit/active` | | | |
| Titre | `payment/it/companycredit/title` | | | |
| Statut de la nouvelle commande | `payment/it/companycredit/order_status` | | | |
| Paiement des pays applicables | `payment/it/companycredit/allowspecific` | | | |
| Paiement de pays spécifiques | `payment/it/companycredit/specificcountry` | | | |
| Nombre total minimum de commandes | `payment/it/companycredit/min_order_total` | | | |
| Nombre total maximal de commandes | `payment/it/companycredit/max_order_total` | | | |
| Ordre de tri | `payment/it/companycredit/sort_order` | | | |

{style="table-layout:auto"}
