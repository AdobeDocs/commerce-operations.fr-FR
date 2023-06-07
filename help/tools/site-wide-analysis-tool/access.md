---
title: Accès [!DNL Site-Wide Analysis Tool]
description: Découvrez comment accéder au [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 5f9f81b930a3b23c0b334ccbea94d296338a0048
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Accès à la [!DNL Site-Wide Analysis Tool]

Vous pouvez accéder de deux manières à la variable [!DNL Site-Wide Analysis Tool Dashboard].

Vous pouvez accéder au [!DNL dashboard] de l’un des [[!DNL Site-Wide Analysis Tool] Site Web](https://supportinsights.adobe.com/commerce) directly **(pour Adobe Commerce sur l’infrastructure cloud uniquement)** et connectez-vous avec votre Adobe ID, ou accédez à via le [!DNL dashboard] de votre boutique. [!DNL Admin Panel].

Le [!DNL Site-Wide Analysis Tool] Le service est disponible dans [mode de production](https://docs.magento.com/user-guide/magento/installation-modes.html) pour [!DNL Admin] utilisateurs autorisés à accéder à [ressources de rôle](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>Si vous disposez d’une installation sur site d’Adobe Commerce, vous devez installer une [agent](../site-wide-analysis-tool/installation.md) sur votre infrastructure pour utiliser l’outil.

![Tableau de bord des analyses à l’échelle du site](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Tableau de bord*

## Option 1 : Connectez-vous à [!DNL Site-Wide Analysis Tool Dashboard] directement à partir de [!DNL Site-Wide Analysis Tool] Domaine (pour Adobe Commerce sur l’infrastructure cloud uniquement)

Un **[!DNL Adobe ID]est requis** pour accéder à un [!DNL Commerce] compte .
Si vous disposez déjà d’une [!DNL Commerce] , mais vous n’avez pas de [!DNL Adobe ID], vous pouvez en créer un au cours du processus de connexion.

1. Accédez à [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. Cliquez sur le bouton **[!UICONTROL Sign in with Adobe ID]** et suivez les invites.

   ![Tableau de bord des analyses à l’échelle du site](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]écran de connexion*

1. Acceptez les conditions générales.

1. **<u>Remarque</u>:** Votre compte doit avoir le droit de **[!DNL Support Permissions]** pour accéder à [!DNL Site-Wide Analysis Tool Dashboard].
Voir plus de détails dans [Partager une [!DNL Commerce] account](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) dans notre guide d’utilisation.

## Option 2 : Connectez-vous à [!DNL Site-Wide Analysis Tool Dashboard] de votre boutique. [!DNL Admin Panel]

### Étape 1 : Vérification des autorisations

Vérifiez que la variable [!DNL Admin] compte utilisateur autorisé à accéder à [!DNL Site-Wide Analysis Tool] à travers leur [rôle d’utilisateur attribué](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>Le [!DNL Site-Wide Analysis Tool] la ressource de rôle (autorisation) est **not** attribué automatiquement. Elle DOIT être activée pour le rôle utilisateur et le rôle affectés individuellement à chaque compte utilisateur dans la variable [!UICONTROL Admin].

Pour le rôle personnalisé qui requiert [!DNL Site-Wide Analysis Tool] accédez à , procédez comme suit :

1. Sélectionnez la **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** ressource de rôle.

   ![Tableau de bord des analyses à l’échelle du site](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]autorisation sélectionnée pour le rôle*

1. Cliquez sur **[!UICONTROL Save Role]**.

1. Informer les utilisateurs auxquels ce rôle est affecté de se déconnecter de la fonction [!DNL Admin]et reconnectez-vous.

>[!NOTE]
>
>Si vous avez vérifié que le compte utilisateur est autorisé à accéder à la variable [!DNL Site-Wide Analysis Tool] et l’utilisateur reçoit une erreur 403 lorsqu’il tente d’accéder à l’outil à partir de la fonction [!DNL Admin], le contrôle d’accès HTTP peut être activé pour votre instance d’Adobe Commerce sur l’infrastructure cloud. Le [!DNL Site-Wide Analysis Tool] Le tableau de bord n’est PAS pris en charge si l’authentification HTTP est activée. Pour plus d’informations sur la résolution de ce problème, voir notre [Article sur le support](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### Étape 2 : Accès [!DNL Site-Wide Analysis Tool]

1. Sur le *[!UICONTROL Admin]* barre latérale, accédez à **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Tableau de bord des analyses à l’échelle du site](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]dans le [!DNL Admin Panel] dans Adobe Commerce*

1. Lisez le *Conditions d’utilisation* pour le [!DNL Site-Wide Analysis Tool] et cliquez sur **[!UICONTROL Accept]** pour continuer.

   Chaque utilisateur doit accepter les Conditions d’utilisation de la session. Cette étape est répétée pour chaque session connectée.


1. Dans la partie supérieure du tableau de bord, cliquez sur l’onglet que vous souhaitez afficher.

   ![Tableau de bord des analyses à l’échelle du site](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]informations*

## Générer des rapports à partir de la variable [!DNL Site-Wide Analysis Tool Dashboard]

1. Dans le coin supérieur droit du tableau de bord, cliquez sur **[!UICONTROL Generate Report]**.

1. Cochez la case pour chaque **[!UICONTROL Type]** et **[!UICONTROL Priority]** que vous souhaitez inclure dans le rapport.

1. Cliquez sur **[!UICONTROL Generate Report]**.

   ![Tableau de bord des analyses à l’échelle du site](../../assets/tools/swat-report-settings.png)
   *Paramètres des rapports*

| ONGLET | DESCRIPTION |
| --- | --- |
| Tableau de bord | Affiche l’intégrité de votre système avec les notifications et recommandations actuelles par priorité. |
| Informations | Fournit des informations sur les contacts client et un résumé des tickets en cours, avec des informations détaillées sur chaque produit Adobe Commerce installé. |
| Recommendations | Répertorie les recommandations basées sur les bonnes pratiques pour résoudre les problèmes détectés sur votre site. |
| Exceptions | Répertorie les erreurs générées par l’application par des conditions anormales sans gestionnaire d’erreurs. |
| Extensions | Répertorie toutes les extensions tierces et bibliothèques tierces. |

>[!NOTE]
>
>Après l’application d’une recommandation, il peut s’écouler quelques jours avant qu’elle ne soit mise à jour dans la variable [!DNL Site-Wide Analysis Tool Dashboard] ou générer le rapport.
