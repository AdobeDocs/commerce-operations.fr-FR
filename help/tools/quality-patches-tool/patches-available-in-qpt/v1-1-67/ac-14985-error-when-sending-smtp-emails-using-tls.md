---
title: 'AC-14985 : erreur lors de l’envoi d’e-mails SMTP à l’aide de TLS'
description: Appliquez le correctif AC-14985 pour résoudre le problème d’Adobe Commerce en raison duquel une erreur se produit lors de l’envoi d’e-mails SMTP (Simple Mail Transfer Protocol) à l’aide de TLS (Transport Layer Security).
feature: Configuration
role: Admin, Developer
type: Troubleshooting
source-git-commit: ed50e166c1fd34f5c19066297008cd74f36ccaaa
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# AC-14985 : erreur lors de l’envoi d’e-mails SMTP à l’aide de TLS

Le correctif AC-14985 corrige un problème en raison duquel une erreur se produit lors de l’envoi d’e-mails SMTP (Simple Mail Transfer Protocol) à l’aide de TLS (Transport Layer Security). Ce correctif est disponible lorsque la version 1.1.67 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est AC-14985. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur se produit lors de l’envoi d’e-mails via SMTP avec TLS activé.

<u>Procédure à suivre </u> :

1. Paramétrez la configuration SMTP comme suit :
* Transport : SMTP
* Hôte : url.to.smtp.host
* 587 Port
* SSL : TLS

<u>Résultats attendus</u> :

L’e-mail est envoyé avec succès sans erreur.

<u>Résultats réels</u> :

L’erreur suivante s’affiche :

```
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
