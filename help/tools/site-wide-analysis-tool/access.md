---
title: Accès [!DNL Site-Wide Analysis Tool]
description: Découvrez comment accéder au tableau de bord de l’outil d’analyse à l’échelle du site à partir du panneau d’administration Adobe Commerce. Découvrez les autorisations utilisateur et les exigences des rôles.
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Accès au [!DNL Site-Wide Analysis Tool]

Vous pouvez accéder au tableau de bord des [!DNL Site-Wide Analysis Tool] depuis le [!UICONTROL Admin Panel] de votre boutique.

Le service [!DNL Site-Wide Analysis Tool] est disponible en [mode de production](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/tools/developer-tools#operation-modes) pour les utilisateurs [!UICONTROL Admin] autorisés à accéder aux ressources utilisateur [rôle](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/user-accounts/permissions-user-roles).

>[!NOTE]
>
>À compter du 23 avril 2024, le [!DNL Site-Wide Analysis Tool] a été mis hors service et n’est plus disponible pour les clients sur site Adobe Commerce.


![Tableau de bord d’analyse à l’échelle du site](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Dashboard*

>[!NOTE]
>
>Votre compte doit avoir le droit de **[!DNL Support Permissions]** pour accéder au [!DNL Site-Wide Analysis Tool Dashboard].
>&#x200B;>Pour plus d’informations, consultez la section [Partager un compte [!DNL Commerce] &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html?lang=fr) dans notre guide de l’utilisateur.

## Connexion à [!DNL Site-Wide Analysis Tool Dashboard] à partir de l’[!UICONTROL Admin Panel] de votre boutique

### Étape 1 : vérifier les autorisations

Vérifiez que le compte utilisateur [!UICONTROL Admin] a l’autorisation d’accéder au [!DNL Site-Wide Analysis Tool] via son [rôle utilisateur affecté](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/user-accounts/permissions-user-roles).

>[!IMPORTANT]
>
>La ressource de rôle [!DNL Site-Wide Analysis Tool] (autorisation) n’est **pas** affectée automatiquement. Elle DOIT être activée pour le rôle d’utilisateur et le rôle affecté individuellement à chaque compte d’utilisateur dans le [!UICONTROL Admin].

Pour le rôle personnalisé nécessitant un accès [!DNL Site-Wide Analysis Tool], procédez comme suit :

1. Sélectionnez la ressource **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** le rôle .

   ![Tableau de bord d’analyse à l’échelle du site](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]autorisation sélectionnée pour le rôle*

1. Cliquez sur **[!UICONTROL Save Role]**.

1. Avertissez tous les utilisateurs et utilisatrices affectés à ce rôle de se déconnecter du [!DNL Admin] et de se reconnecter.

>[!NOTE]
>
>Si vous avez vérifié que le compte utilisateur dispose de l’autorisation d’accéder au [!DNL Site-Wide Analysis Tool] et que l’utilisateur ou l’utilisatrice reçoit une erreur 403 lors de la tentative d’accès à l’outil à partir du [!UICONTROL Admin] , le contrôle d’accès HTTP peut être activé pour votre instance d’Adobe Commerce sur l’infrastructure cloud. Le tableau de bord [!DNL Site-Wide Analysis Tool] n’est PAS pris en charge si vous avez activé l’authentification HTTP. Pour plus d’informations sur la résolution de ce problème, consultez notre article d’assistance [&#128279;](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/403-errors-when-accessing-site-wide-analysis-tool-on-magento).

### Etape 2 : Accès aux [!DNL Site-Wide Analysis Tool]

1. Dans la barre latérale *[!UICONTROL Admin]*, accédez à **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Tableau de bord d’analyse à l’échelle du site](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]emplacement dans le [!UICONTROL Admin Panel] d’Adobe Commerce*

1. Lisez les *Conditions d’utilisation* de la [!DNL Site-Wide Analysis Tool] et cliquez sur **[!UICONTROL Accept]** pour continuer.

   Chaque utilisateur est tenu d’accepter les conditions d’utilisation de la session. Cette étape est répétée pour chaque session connectée.


1. Dans la partie supérieure du tableau de bord, cliquez sur l’onglet qui vous intéresse.

   ![Tableau de bord d’analyse à l’échelle du site](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]d’informations*

## Générer des rapports à partir du [!DNL Site-Wide Analysis Tool Dashboard]

1. Dans le coin supérieur droit du tableau de bord, cliquez sur **[!UICONTROL Generate Report]**.

1. Cochez la case de chaque **[!UICONTROL Type]** et **[!UICONTROL Priority]** paramètre que vous souhaitez inclure dans le rapport.

1. Cliquez sur **[!UICONTROL Generate Report]**.

   ![Tableau de bord d’analyse à l’échelle du site](../../assets/tools/swat-report-settings.png)
   *Paramètres des rapports*

| TAB | DESCRIPTION |
| --- | --- |
| Tableau de bord | Affiche l’intégrité de votre système avec les notifications et recommandations actuelles par priorité. |
| Informations | Fournit des coordonnées du client et un résumé des tickets actuels, avec des informations détaillées sur chaque produit Adobe Commerce installé. |
| Recommendations | Répertorie les recommandations basées sur les bonnes pratiques pour résoudre les problèmes détectés sur votre site. |
| Exceptions | Répertorie les erreurs générées par l’application en raison de conditions anormales sans gestionnaire d’erreurs. |
| Extensions | Répertorie toutes les extensions et bibliothèques tierces. |

>[!NOTE]
>
>Après l’application d’une recommandation, sa mise à jour dans le rapport [!DNL Site-Wide Analysis Tool Dashboard] ou généré peut prendre quelques jours.
