---
title: 'ACSD-67039 : les enregistrements du client n''ont pas été enregistrés en raison de la validation des attributs du système rp_token'
description: Appliquez le correctif ACSD-67039 pour résoudre le problème d’Adobe Commerce où les signes diacritiques de codage provoquent des interruptions de validation sur rp_token.
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 231555e071ebc5edb36182f6b8d4f60acee4f61e
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-67039 : les enregistrements client n&#39;ont pas été enregistrés en raison de `rp_token` validation des attributs système

Le correctif ACSD-67039 corrige le problème où les enregistrements des clients n’étaient pas enregistrés en raison de la validation de l’attribut système `rp_token` et la validation des diacritiques n’était appliquée qu’à l’e-mail du client résultant. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-67039. Ce problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p9

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les diacritiques de codage entraînent des échecs de validation sur `rp_token`, qui est exclu de la validation. Les signes diacritiques ne sont autorisés que pour les adresses e-mail, comme prévu.

<u>Procédure à suivre </u> :

1. Installez la version 2.4.4 d’Adobe Commerce.
1. Créez un client.
1. Mettez à niveau Adobe Commerce vers la version 2.4.6 à partir de la version 2.4.4 antérieure où le client était déjà créé.
1. Définissez la clé de chiffrement sur `env.php` =
   *d337b914e91ff703b1e94ba4156aadf0*
1. Définissez les valeurs ci-dessous dans la base de données pour tout client figurant dans le tableau `customer_entity` :
*`rp_token` = *incr4869*
*`rp_token_created_at` = *2021-04-29 20:06:14*
1. Dans le panneau d’administration, accédez à **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifiez le client pour lequel vous venez de mettre à jour les valeurs ci-dessus.
1. Cliquez sur **[!UICONTROL Save Customer]** ou **[!UICONTROL Save and Continue Edit]**.

<u>Résultats attendus</u> :

Les valeurs client ont été enregistrées.

<u>Résultats réels</u> :

L’enregistrement du client n’est pas enregistré et l’utilisateur administrateur voit le message d’erreur *Un problème est survenu lors de l’enregistrement du client.*
Le `system.log` contient l’erreur suivante :

```
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [&#x200B; Mises à niveau et correctifs > Appliquer des correctifs &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
