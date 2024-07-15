---
title: Bonnes pratiques relatives au traitement et au stockage des paiements
description: Découvrez comment traiter et stocker en toute sécurité les informations de paiement
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: db0fce79b22d409e8d639b959dc5a04693e72659
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Bonnes pratiques en matière de traitement et de stockage des paiements

L&#39;un des principes clés de la gestion de la [conformité PCI](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) est d&#39;avoir une stratégie pour traiter et stocker correctement les paiements par carte de crédit.

Le stockage des données des titulaires de carte dans Adobe Commerce est **strictement interdit** et cela peut constituer une violation de vos obligations en tant que commerçant en vertu de la norme de sécurité des données du secteur des cartes de paiement (PCI-DSS). Vous trouverez plus d’informations sur le modèle de responsabilité partagée et les directives relatives aux obligations du commerçant dans le [Guide du modèle de responsabilité partagée Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) du Adobe Trust Center.

Suivez les bonnes pratiques ci-dessous pour vous assurer que vous traitez correctement les informations de paiement sur votre site eCommerce. Pour plus d&#39;informations sur les bonnes pratiques en matière de sécurité, voir [Sécuriser votre site et votre infrastructure](../launch/security-best-practices.md).

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

* Adobe Commerce sur l’infrastructure cloud
* Adobe Commerce sur site

## Protection des données des titulaires de carte

Si le stockage des données du détenteur de carte est nécessaire, les données du détenteur de carte doivent être stockées en dehors d’Adobe Commerce avec des protections de stockage. La mise en place de protections de stockage pour les détails de paiement, comme les données des titulaires de carte de crédit, contribue à prévenir la fraude et d&#39;autres problèmes de sécurité potentiels. En accord avec d&#39;autres normes PCI, la première ligne de défense consiste à avoir des protections en place. Certaines méthodes préférées pour améliorer la protection des données stockées incluent le cryptage, la troncation, la segmentation en unités lexicales, le hachage à sens unique et le masquage.

La protection des clés cryptographiques est essentielle aux stratégies de protection des données. Il est essentiel d&#39;avoir des gardiens compétents et fiables qui surveillent ces clés.

Enfin, un numéro de compte principal (PAN) doit être illisible pendant le stockage, par exemple masqué avec `XXX`. Cela inclut le stockage portable et les supports de sauvegarde tels que les lecteurs Flash, les disques durs USB et externes, et même les journaux d’audit.

## Chiffrer la transmission des données du détenteur de carte

La protection des données lors de la transmission est essentielle à la protection des informations de paiement, comme les données des titulaires de carte. Lorsque ces informations sont transmises par le biais de réseaux ouverts, elles peuvent devenir plus vulnérables aux problèmes de sécurité.

### Utiliser des protocoles de transmission sécurisés

Transmettez les données des titulaires de carte à l’aide de protocoles et de pratiques de transmission sécurisés, notamment :

* Clés et certificats approuvés
* Protocoles de transmission sécurisés tels que TLS, SSH ou VPN
* Algorithmes asymétriques dans le cryptage
* Tests de jeton, de masquage et de pénétration à l’aide de la transmission et de l’affichage des PAN
* Limitation de l’accès aux données des titulaires de carte
* L&#39;accès à des informations sensibles doit être restreint en fonction du besoin et ne doit être accordé qu&#39;aux personnes autorisées ayant des besoins commerciaux.

La méthode recommandée pour gérer les données des titulaires de carte consiste à segmenter les données en unités lexicales au lieu de les stocker. Jetez la carte avec un fournisseur de traitement des paiements spécifique et stockez le jeton, le type de carte et la date d’expiration chiffrée. Vous pouvez utiliser le jeton comme informations d’identification dans le fichier pour une utilisation ultérieure, car il est unique pour chaque commerçant uniquement. Comme le jeton est unique, en cas de problème de sécurité, le jeton invalidé permet d’éviter les activités frauduleuses.

## Informations supplémentaires

Si vous recherchez des solutions de paiement recommandées par Adobe, pensez aux [Services de paiement par Adobe](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
