---
title: '[!DNL Commerce Version Tool]'
description: Découvrez l’ [!DNL Commerce Version Tool]  d’Adobe Commerce et utilisez le fournisseur/bin/patch-status pour vérifier mensuellement l’état des correctifs de sécurité.
TQID: 'https://experienceleague.adobe.com/9lDQtCrcCSIFjt3jUJkqCo-rMlIhhy3tPTtPyT4wt1Q'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 586
ht-degree: 0%

---

# [!DNL Commerce Version Tool]

Les correctifs de sécurité mensuels pour Adobe Commerce ne sont pas cumulatifs et doivent être appliqués en séquence. Le [!DNL Commerce Version Tool] ([!DNL CVT]) permet aux commerçants de vérifier la couverture des correctifs en signalant les correctifs de sécurité mensuels installés, les correctifs manquants et les fichiers CVE contre lesquels l’installation est protégée.

>[!IMPORTANT]
>
>L’outil [!DNL CVT] n’est fourni qu’à titre d’information. Il n’applique pas de correctifs, n’annule pas les correctifs et ne modifie pas les fichiers sources Adobe Commerce. Il peut écrire des fichiers cache, des fichiers temporaires d’exécution d’essai et des entrées de journal d’audit pour prendre en charge les rapports d’état de correctif.

## Présentation de l’outil

L’outil [!DNL CVT] est un exécutable autonome inclus dans chaque correctif de sécurité Adobe Commerce mensuel. Lorsque le correctif est appliqué à une installation Adobe Commerce, l’outil est installé à l’adresse `vendor/bin/patch-status`. Il nécessite PHP 8.1 ou une version ultérieure et le système `patch` binaire. Il ne nécessite pas de packages Composer, d’extensions PHP non standard, de bootstrap Adobe Commerce ou d’étape d’installation distincte.

L’outil [!DNL CVT] peut vous aider à :

- Détecter les correctifs de sécurité appliqués pour une installation Adobe Commerce prise en charge.
- Identifiez les correctifs manquants dans une séquence mensuelle de correctifs de sécurité isolés.
- Signalez l&#39;état de sécurité protégé, vulnérable ou inconnu des enregistrements CVE (Common Vulnerabilities and Expositions) liés aux correctifs.
- Produisez des sorties lisibles par machine, telles que JSON ou CSV, pour les scanners, les tableaux de bord et les rapports de conformité.
- Détectez l’état des correctifs pour les plateformes et composants pris en charge.

## Disponibilité

L’outil [!DNL CVT] prend en charge la création de rapports d’état de correctif pour les plateformes et composants ci-après lorsqu’Adobe fournit des métadonnées de correctif pour la version installée dans le fichier de registre des correctifs.

| Plateforme ou composant | Disponibilité |
| --- | --- |
| Adobe Commerce On-Premise | Pris en charge |
| [!DNL Magento Open Source] | Pris en charge |
| Adobe Commerce business-to-business (B2B) | Pris en charge lors de l’installation |
| Page Builder d’Adobe Commerce | Pris en charge lors de l’installation |
| Inventaire Adobe Commerce | Pris en charge lors de l’installation |
| Composants supplémentaires détectés depuis `composer.lock` | Pris en charge lorsqu’il est représenté dans le fichier de registre des correctifs |

{style="table-layout:auto"}

## Cas d’utilisation courants

Utilisez l’outil [!DNL CVT] lorsque vous devez :

- Vérifiez si l’installation d’Adobe Commerce comprend les correctifs de sécurité isolés requis.
- Vérifiez si les ensembles de correctifs ignorés ou incomplets laissent la couverture CVE incomplète.
- Générer une sortie JSON ou CSV pour le reporting interne ou l’analyse automatisée.
- Fournissez des informations sur l’état du correctif avant d’ouvrir une demande d’assistance ou de planifier la remédiation.

## Recommandations relatives à l’utilisation des résultats

Traitez la sortie de l’outil [!DNL CVT] comme des données de détection qui prennent en charge la planification des correctifs et la révision de la sécurité.

Suivez ces instructions :

- Exécutez l’outil [!DNL CVT] pour une installation d’Adobe Commerce stable et prise en charge.
- Examinez les correctifs manquants et inconnus avant de revendiquer le statut de sécurité.
- Conservez la sortie JSON ou CSV pour faciliter l’audit et l’automatisation.
- Traiter la sortie d&#39;analyse comme des données opérationnelles pertinentes pour la sécurité.
- Partagez uniquement les détails nécessaires à l’assistance ou à la correction.

## Détection des correctifs

L’outil [!DNL CVT] exécute la détection en deux étapes fixes. Les deux étapes s’exécutent toujours lorsque vous générez un rapport d’état des correctifs.

- **Détection du compositeur :** l’outil lit le fichier `composer.lock` pour déterminer la version de base [!DNL Adobe Commerce] et les zones de composants installées. Si l’outil ne peut pas détecter une version de base, il se ferme avec le code `1`.

- **Détection d’exécution d’essai :** pour chaque correctif applicable, l’outil applique une vérification d’exécution d’essai par rapport aux modifications apportées au correctif afin de déterminer si le correctif est déjà appliqué, s’il n’est pas appliqué ou si l’état du correctif est inconnu. L’outil gère les dépendances de correctif pendant cette vérification afin que les résultats reflètent la version du composant installé.

Le rapport inclut uniquement les correctifs qui s’appliquent à l’installation détectée et aux composants installés. Si l’outil ne peut pas confirmer la présence d’un correctif applicable, il le classe comme inconnu.

## Commencer à utiliser [!DNL CVT]

Utilisez ces rubriques pour générer, dépanner et suivre les rapports d’état des correctifs :

- [Générez un rapport d’état des correctifs](generate-report.md) pour exécuter l’outil de [!DNL CVT], passer en revue les options de commande et interpréter les résultats du rapport.
- [[!DNL Commerce Version Tool] dépannage](troubleshooting.md) pour résoudre des résultats inattendus ou des erreurs de commande.
- [[!DNL Commerce Version Tool] notes de mise à jour](release-notes.md) pour consulter les mises à jour de versions.
