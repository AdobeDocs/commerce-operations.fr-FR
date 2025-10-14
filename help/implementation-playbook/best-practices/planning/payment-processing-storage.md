---
title: Bonnes pratiques de traitement et de stockage des paiements
description: Découvrez comment traiter et stocker les informations de paiement en toute sécurité.
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Bonnes pratiques de traitement et de stockage des paiements

L’un des principes clés du maintien de la conformité [PCI](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html?lang=fr) est d’avoir une stratégie pour traiter et stocker correctement les paiements par carte de crédit.

Le stockage des données des titulaires de carte dans Adobe Commerce est **strictement interdit** et cela pourrait constituer une violation de vos obligations en tant que commerçant en vertu de la norme PCI-DSS (Payment Card Industry Data Security Standard). Pour plus d’informations sur le modèle de responsabilité partagée et les directives relatives aux obligations des commerçants, consultez le [Guide du modèle de responsabilité partagée d’Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) dans le Centre de gestion de la confidentialité d’Adobe.

Suivez les bonnes pratiques ci-dessous pour vous assurer que vous traitez correctement les informations de paiement sur votre site d’e-commerce. Pour obtenir des conseils supplémentaires sur les bonnes pratiques de sécurité, voir [&#x200B; Sécurisation de votre site et de votre infrastructure &#x200B;](../launch/security-best-practices.md).

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

* Adobe Commerce sur les infrastructures cloud
* Adobe Commerce On-Premise

## Protection des données des titulaires de carte

Si le stockage des données du titulaire de carte est nécessaire, ces dernières doivent être stockées en dehors d’Adobe Commerce avec des mesures de sauvegarde. La mise en place de mesures de protection du stockage des informations de paiement, telles que les données des titulaires de carte de crédit, contribue à prévenir la fraude et d’autres problèmes de sécurité potentiels. Conformément aux autres normes PCI, la mise en place de protections est la première ligne de défense. Certaines méthodes préférées pour améliorer la protection des données stockées comprennent le chiffrement, la troncature, la segmentation en unités lexicales, le hachage unidirectionnel et le masquage.

Les protections des clés cryptographiques sont essentielles aux stratégies de protection des données. Il est essentiel d&#39;avoir des gardiens compétents et dignes de confiance qui supervisent ces clés.

Enfin, un numéro de compte principal (PAN) doit être illisible pendant le stockage, par exemple masqué avec `XXX`. Cela inclut les supports de stockage et de sauvegarde portables tels que les lecteurs flash, les disques durs USB et externes, et même les journaux d’audit.

## Chiffrer la transmission des données du détenteur de carte

La protection des données lors de leur transmission est essentielle pour protéger les informations de paiement, comme les données des titulaires de carte. Lorsque ces informations sont transmises sur des réseaux ouverts, elles peuvent devenir plus vulnérables aux problèmes de sécurité.

### Utiliser des protocoles de transmission sécurisés

Transmettre les données des titulaires de carte à l&#39;aide de protocoles et de pratiques de transmission sécurisés, notamment :

* Clés et certificats de confiance
* Protocoles de transmission sécurisés tels que TLS, SSH ou VPN
* Algorithmes asymétriques dans le chiffrement
* Test d&#39;émission de jetons, de masquage et de pénétration avec transmission et affichage de PAN
* Limiter l’accès aux données du titulaire de carte
* L&#39;accès aux informations sensibles devrait être limité en fonction du besoin d&#39;en connaître et ne devrait être accordé qu&#39;au personnel autorisé ayant un besoin opérationnel

La méthode recommandée pour gérer les données du titulaire de carte consiste à segmenter les données en unités lexicales au lieu de les stocker. Jetez la carte avec un fournisseur de traitement des paiements spécifique et stockez le jeton, le type de carte et la date d&#39;expiration chiffrée. Vous pouvez utiliser le jeton comme informations d’identification dans le fichier pour une utilisation ultérieure, car il est unique à chaque commerçant uniquement. Puisque le jeton est unique, en cas de problème de sécurité, le jeton est invalidé, ce qui permet d’empêcher toute activité frauduleuse.

## Informations supplémentaires

Si vous recherchez des solutions de paiement recommandées par Adobe, pensez à [Adobe Payment Services](https://experienceleague.adobe.com/docs/commerce/payment-services/overview.html?lang=fr).
