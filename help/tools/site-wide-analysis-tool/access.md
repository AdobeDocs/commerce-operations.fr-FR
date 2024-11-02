---
title: Comment y accéder [!DNL Site-Wide Analysis Tool]
description: Découvrez comment accéder au [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Comment accéder à l&#39; [!DNL Site-Wide Analysis Tool]

Vous pouvez accéder à [!DNL Site-Wide Analysis Tool Dashboard] de deux façons.

Vous pouvez accéder à [!DNL dashboard] à partir du [[!DNL Site-Wide Analysis Tool] site Web](https://supportinsights.adobe.com/commerce) directement **(pour Adobe Commerce sur l’infrastructure cloud uniquement)** et vous connecter avec votre Adobe ID, ou accéder à l’aide de l’ [!DNL dashboard] à partir de [!DNL Admin Panel] de votre boutique.

Le service [!DNL Site-Wide Analysis Tool] est disponible en [mode de production](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#operation-modes) pour les utilisateurs [!DNL Admin] autorisés à accéder aux ressources de rôle [ de l’utilisateur ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles).

>[!NOTE]
>
>À compter du 23 avril 2024, le [!DNL Site-Wide Analysis Tool] a été mis hors service et n’est plus disponible pour les clients Adobe Commerce sur site.


![Tableau de bord de l’analyse à l’échelle du site](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Tableau de bord*

## Option 1 : connexion à votre [!DNL Site-Wide Analysis Tool Dashboard] directement à partir du domaine [!DNL Site-Wide Analysis Tool] (pour Adobe Commerce sur l’infrastructure cloud uniquement)

Un **[!DNL Adobe ID]est requis** pour accéder à un compte [!DNL Commerce].
Si vous disposez déjà d’un compte [!DNL Commerce], mais que vous n’avez pas de compte [!DNL Adobe ID], vous pouvez en créer un pendant le processus de connexion.

1. Accédez à [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. Cliquez sur le bouton **[!UICONTROL Sign in with Adobe ID]** et suivez les invites.

   ![Tableau de bord de l’analyse à l’échelle du site](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]écran de connexion*

1. Acceptez les termes et conditions.

1. **<u>Remarque</u> :** Votre compte devrait être autorisé **[!DNL Support Permissions]** à pour accéder [!DNL Site-Wide Analysis Tool Dashboard]à .
Consultez plus de détails dans [Partager un [!DNL Commerce] compte](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) dans notre guide de l’utilisateur.

## Option 2 : Connexion à votre à partir [!DNL Site-Wide Analysis Tool Dashboard] du [!DNL Admin Panel]

### Étape 1 : Vérifier les autorisations

Vérifiez que le compte d’utilisateur dispose de l’autorisation [!DNL Admin] d’accéder [!DNL Site-Wide Analysis Tool] au via le rôle](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles) d’utilisateur qui lui [a été attribué.

>[!IMPORTANT]
>
>La [!DNL Site-Wide Analysis Tool] ressource de rôle (autorisation) n’est **pas** attribuée automatiquement. Il DOIT être activé pour le rôle d’utilisateur et le rôle attribué individuellement à chaque compte d’utilisateur dans le [!UICONTROL Admin].

Pour le rôle personnalisé nécessitant un [!DNL Site-Wide Analysis Tool] accès, procédez comme suit :

1. Sélectionnez la ressource > *[!UICONTROL System Insights]* > **[!UICONTROL Reports]** **[!UICONTROL Site-Wide Analysis Tool]** rôle.

   ![Tableau de bord Analyse à l’échelle du site](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]permission sélectionnée pour le rôle*

1. Cliquez sur **[!UICONTROL Save Role]**.

1. Avertissez les utilisateurs auxquels ce rôle est affecté de se déconnecter de [!DNL Admin] et de se reconnecter.

>[!NOTE]
>
>Si vous avez vérifié que le compte utilisateur est autorisé à accéder à [!DNL Site-Wide Analysis Tool] et que l’utilisateur reçoit une erreur 403 lorsqu’il tente d’accéder à l’outil à partir de [!DNL Admin], le contrôle d’accès HTTP peut être activé sur votre instance d’Adobe Commerce sur l’infrastructure cloud. Le tableau de bord [!DNL Site-Wide Analysis Tool] n’est PAS pris en charge si l’authentification HTTP est activée. Pour plus d’informations sur la résolution de ce problème, consultez notre [article d’assistance](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### Étape 2 : Accès à [!DNL Site-Wide Analysis Tool]

1. Sur la barre latérale *[!UICONTROL Admin]*, accédez à **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Tableau de bord de l’analyse à l’échelle du site](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]emplacement dans le [!DNL Admin Panel] dans Adobe Commerce*

1. Lisez les *Conditions d’utilisation* pour le [!DNL Site-Wide Analysis Tool] et cliquez sur **[!UICONTROL Accept]** pour continuer.

   Chaque utilisateur doit accepter les Conditions d’utilisation de la session. Cette étape est répétée pour chaque session connectée.


1. En haut du tableau de bord, cliquez sur l’onglet à afficher.

   ![Tableau de bord Analyse à l’échelle du site](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]information*

## Générez des rapports à partir du [!DNL Site-Wide Analysis Tool Dashboard]

1. Dans l’angle supérieur droit du tableau de bord, cliquez sur **[!UICONTROL Generate Report]**.

1. Cochez la case correspondant à chaque **[!UICONTROL Type]** paramètre **[!UICONTROL Priority]** à inclure dans le rapport.

1. Cliquez sur **[!UICONTROL Generate Report]**.

   ![Tableau de bord de l’analyse à l’échelle du site](../../assets/tools/swat-report-settings.png)
   *Paramètres de rapport*

| ONGLET | DESCRIPTION |
| --- | --- |
| Tableau de bord | Affiche l’intégrité de votre système avec les notifications et recommandations actuelles par priorité. |
| Informations | Fournit des informations sur les contacts client et un résumé des tickets en cours, avec des informations détaillées sur chaque produit Adobe Commerce installé. |
| Recommendations | Répertorie les recommandations basées sur les bonnes pratiques pour résoudre les problèmes détectés sur votre site. |
| Exceptions | Répertorie les erreurs générées par l’application provoquées par des conditions anormales sans gestionnaire d’erreurs. |
| Extensions | Répertorie toutes les extensions et bibliothèques tierces. |

>[!NOTE]
>
>Après l’application d’une recommandation, il peut s’écouler quelques jours avant qu’elle ne soit mise à jour dans le rapport [!DNL Site-Wide Analysis Tool Dashboard] ou généré.
