---
title: Calendrier de publication des correctifs
description: Découvrez quand Adobe prévoit d’annoncer la publication de nouveaux patchs et correctifs de sécurité pour Adobe Commerce.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 0f46bdfd0afbca07e0d60e995ee9426f5408671d
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 4%

---


# Calendrier de publication des correctifs

Adobe s’efforce en permanence de trouver le bon équilibre entre la simplicité et la prévisibilité des mises à niveau de produits et l’accélération des améliorations pour les utilisateurs précoces (voir [politique de version](versioning-policy.md)).

L’objectif de ce planning est de fournir les dates auxquelles Adobe prévoit d’annoncer la publication des [correctifs](versioning-policy.md#patch-release) pour chaque ligne de version prise en charge de l’application principale Adobe Commerce PHP. Les versions de correctifs sont l’occasion de mettre à niveau la base de code principale pour garantir la sécurité, la fiabilité et les performances de votre plateforme.

>[!NOTE]
>
>Pour en savoir plus sur les nouvelles fonctionnalités, l’infrastructure cloud et les versions d’extensibilité, consultez la documentation de la version [Adobe Commerce Services](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all).

Outre les correctifs de qualité, de sécurité et Beta planifiés répertoriés sur cette page, Adobe permet d’accéder à des [correctifs individuels](versioning-policy.md#individual-patch) via l’[outil de correctifs de qualité](../tools/quality-patches-tool/usage.md). Cet outil vous permet d’appliquer, d’annuler et d’afficher des informations générales sur tous les correctifs individuels disponibles pour la version installée d’Adobe Commerce.

Les versions des correctifs Adobe Commerce sont publiées conformément aux directives suivantes :

- **Fichier de correctifs de sécurité isolé**—Les fichiers de correctifs de sécurité individuels [non cumulatifs](versioning-policy.md#isolated-security-patch-file) sont publiés indépendamment pour permettre une correction plus rapide et sont intégrés au correctif de sécurité complet suivant. Pour appliquer un fichier de correctif de sécurité isolé, les clients doivent disposer de la dernière version du correctif de sécurité uniquement (la dernière version -p) pour leur ligne de version prise en charge, car les correctifs de sécurité isolés sont testés exclusivement par rapport à cette version.

- **Correctifs de sécurité** : au minimum, les [correctifs de sécurité](versioning-policy.md#security-patch-release) sont publiés chaque année pour toutes les lignes de version [prises en charge](lifecycle-policy.md). Ces correctifs comprennent tous les correctifs de sécurité, de conformité et de qualité publiés précédemment.  Adobe peut publier des correctifs de sécurité supplémentaires si nécessaire, mais cela n’est pas garanti.

- **Patch**—Un [patch](versioning-policy.md#patch-release) complet pour la ligne de version Adobe Commerce 2.4.x LTS (période de prise en charge de 3 ans) est publié chaque année (mai).

- **Le correctif Alpha patches**-One [alpha](versioning-policy.md#alpha-patch-release) pour la ligne de mise à jour Adobe Commerce 2.4.x LTS est publié chaque année.

- **Correctifs**—Un [correctifs bêta](versioning-policy.md#beta-patch-release) pour la ligne de version Adobe Commerce 2.4.x LTS est publié chaque année.

Voir l’image suivante pour plus de détails :

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![Calendrier des versions d’Adobe Commerce 2026](../assets/release/release-calendar.png)


## Canaux de notification de publication

Adobe informe ses clients des nouvelles versions de correctifs par le biais des canaux suivants :

- [Bulletins et conseils de sécurité ](https://helpx.adobe.com/security/security-bulletin.html#magento)
- E-mail
- Alertes intégrées au produit

>[!NOTE]
>
> Pour connaître les dates de publication de chaque version mineure, correctif ou de sécurité, ainsi que les dates de fin de la prise en charge standard, consultez [Versions publiées](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions).
