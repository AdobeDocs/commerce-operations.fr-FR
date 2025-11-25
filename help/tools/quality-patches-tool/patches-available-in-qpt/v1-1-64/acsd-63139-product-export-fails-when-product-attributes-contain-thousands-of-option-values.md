---
title: 'ACSD-63139 : l’exportation du produit échoue lorsque les attributs du produit contiennent des milliers de valeurs d’option'
description: Appliquez le correctif ACSD-63139 pour résoudre le problème d’Adobe Commerce en raison duquel l’exportation du produit échoue lorsque les attributs du produit contiennent des milliers de valeurs d’option.
feature: Data Import/Export
role: Admin, Developer
exl-id: 785907dc-aa3f-49e2-bd52-c3afe4393456
type: Troubleshooting
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63139 : l’exportation du produit échoue lorsque les attributs du produit contiennent des milliers de valeurs d’option

Le correctif ACSD-63139 corrige le problème d’échec de l’exportation du produit lorsque les attributs du produit contiennent des milliers de valeurs d’option. Ce correctif est disponible lorsque la version 1.1.64 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63139. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exportation du produit échoue lorsque les attributs du produit contiennent des milliers de valeurs d’option.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce avec le module B2B.
1. Importez une image mémoire de base de données volumineuse avec :
   - ~7 000 produits
   - ~450 attributs de produit
   - Certains attributs ayant plus de 100 options
1. Exécutez la commande suivante pour installer cron (s’il n’est pas déjà installé) :

   ```
   bin/magento cron:install
   ```

1. Configurez [!DNL RabbitMQ] en suivant les instructions de la section [[!DNL RabbitMQ] Conditions préalables](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/message-brokers/rabbitmq).
1. Ouvrez le fichier `php.ini`, définissez la limite de mémoire sur 4G, puis redémarrez le service PHP.
1. Dans le panneau d’administration, accédez à **[!UICONTROL System]** > *[!UICONTROL Data Transfer]* > **[!UICONTROL Export]**.
1. Dans la section *[!UICONTROL Export Settings]*, définissez **[!UICONTROL Entity Type]** sur *Produits*, faites défiler la page vers le bas et cliquez sur **[!UICONTROL Continue]**.
1. Exécutez la commande suivante pour démarrer le processeur d’exportation :

   ```
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u>Résultats attendus</u> :

L’exportation du produit doit être terminée avec succès.

<u>Résultats réels</u> :

Le processus d’exportation du produit échoue et renvoie l’erreur fatale suivante :

```
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
