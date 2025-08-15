---
title: 'ACSD-62212 : [!UICONTROL Forgot Password] e-mail non traduit en langue de vue de magasin'
description: Appliquez le correctif ACSD-62212 pour résoudre le problème d’Adobe Commerce en raison duquel le contenu de l’e-mail *[!UICONTROL Forgot Password]* n’est pas traduit dans la langue de la vue du magasin.
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62212 : *[!UICONTROL Forgot Password]* e-mail non traduit en langue de vue de magasin

Le correctif ACSD-62212 corrige le problème où le contenu de l’e-mail *[!UICONTROL Forgot Password]* n’est pas traduit dans la langue d’affichage du magasin. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) est installée. L’ID du correctif est ACSD-62212. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la réinitialisation du mot de passe via GraphQL dans une vue de magasin autre que celle enregistrée, le lien de réinitialisation du mot de passe ne correspond pas à la vue de magasin à partir de laquelle il a été initié.

<u>Procédure à suivre </u> :

1. Créez une vue de magasin secondaire sous le *[!UICONTROL Main Website Store]* .
1. Basculez *[!UICONTROL Locale]* sur *[!UICONTROL French (France)]* dans la portée d’affichage du magasin secondaire.
1. Installez le pack de langue français pour les traductions.
1. Créez un compte client.
1. Utilisez la mutation GraphQL suivante avec l’en-tête *store* et le code d’affichage du magasin secondaire.

   ```
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. Vérifiez l’e-mail.

<u>Résultats attendus</u> :

* La langue de l’objet, du lien et du contenu de l’e-mail est cohérente avec les paramètres régionaux d’affichage du magasin.
* La demande de réinitialisation du mot de passe est envoyée à partir du magasin où le compte du client est réellement enregistré, quel que soit l’en-tête du magasin dans la demande.

<u>Résultats réels</u> :

Voici ce qui peut être observé dans l’e-mail :

* Le lien de réinitialisation du mot de passe contient le code de magasin « par défaut ».
* Le sujet est en anglais.
* Le contenu est en français.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
