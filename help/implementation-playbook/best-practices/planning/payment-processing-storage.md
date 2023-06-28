---
title: Bonnes pratiques relatives au traitement et au stockage des paiements
description: Découvrez comment traiter et stocker en toute sécurité les informations de paiement
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Bonnes pratiques en matière de traitement et de stockage des paiements

L&#39;un des principes clés du maintien de la paix [Conformité PCI](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) dispose d’une stratégie pour traiter et stocker correctement les paiements par carte de crédit.

Le stockage des données des titulaires de carte dans Adobe Commerce est **strictement interdit** et cela pourrait être une violation de vos obligations en tant que commerçant en vertu de la norme de sécurité des données du secteur des cartes de paiement (PCI-DSS). Vous trouverez plus d’informations sur notre modèle de responsabilité partagée et sur les directives relatives aux obligations des commerçants dans notre [guide de responsabilité partagée pour Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) sur le Centre de gestion de l’Adobe.

Nous vous recommandons de suivre les bonnes pratiques ci-dessous pour vous assurer que vous traitez correctement les informations de paiement sur votre site eCommerce. Vous trouverez des conseils supplémentaires sur les bonnes pratiques générales de sécurité dans notre [guide des bonnes pratiques de sécurité pour Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) sur le Centre de gestion de l’Adobe

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

* Adobe Commerce sur l’infrastructure cloud
* Adobe Commerce sur site

## Protection des données des titulaires de carte

Si le stockage des données du détenteur de carte est nécessaire, les données du détenteur de carte doivent être stockées en dehors d’Adobe Commerce avec des protections de stockage. La mise en place de protections de stockage pour les détails de paiement, comme les données des titulaires de carte de crédit, contribue à prévenir la fraude et d&#39;autres problèmes de sécurité potentiels. En accord avec d&#39;autres normes PCI, la première ligne de défense consiste à avoir des protections en place. Certaines méthodes préférées pour améliorer la protection des données stockées incluent le cryptage, la troncation, la segmentation en unités lexicales, le hachage à sens unique et le masquage.

La protection des clés cryptographiques est essentielle aux stratégies de protection des données. Il est essentiel d&#39;avoir des gardiens compétents et fiables qui surveillent ces clés.

Enfin, un Principal numéro de compte (PAN) doit être illisible pendant le stockage (par exemple, masqué tel que XXX). Cela inclut le stockage portable et les supports de sauvegarde tels que les lecteurs Flash, les disques durs USB et externes, et même les journaux de contrôle.

## Chiffrer la transmission des données du détenteur de carte

La protection des données lors de la transmission est essentielle à la protection des informations de paiement, comme les données des titulaires de carte. Lorsque ces informations sont transmises par le biais de réseaux ouverts, elles peuvent devenir plus vulnérables aux problèmes de sécurité.

### Utiliser des protocoles de transmission sécurisés

Transmettez les données des titulaires de carte à l’aide de protocoles et de pratiques de transmission sécurisés, notamment :

* Clés et certificats approuvés
* Protocoles de transmission sécurisés tels que TLS, SSH ou VPN
* Algorithmes asymétriques dans le cryptage
* Tests de jeton, de masquage et de pénétration avec transmission et affichage des PAN
* Limitation de l’accès aux données des titulaires de carte
* L&#39;accès à des informations sensibles doit être restreint en fonction du besoin et ne doit être accordé qu&#39;aux personnes autorisées ayant des besoins commerciaux.

La méthode recommandée pour gérer les données des titulaires de carte consiste à ne pas stocker le numéro de compte Principal (PAN), mais à segmenter en unités la carte avec un fournisseur de traitement des paiements spécifique, et à stocker le jeton, le type de carte et la date d’expiration chiffrée. Vous pouvez utiliser le jeton comme informations d’identification dans le fichier pour une utilisation ultérieure, car il est unique pour chaque commerçant uniquement. Comme le jeton est unique, en cas de problème de sécurité, le jeton invalidé permet d’éviter les activités frauduleuses.

## Informations supplémentaires

Si vous recherchez des solutions de paiement recommandées par Adobe, envisagez [Adobe des services de paiement](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
