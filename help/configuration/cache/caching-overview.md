---
title: Configuration de la mise en cache
description: Découvrez les mécanismes de mise en cache et les options de configuration des applications Adobe Commerce. Découvrez des alternatives à la mise en cache du système de fichiers par défaut.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Configuration de la mise en cache

[!DNL Commerce] vous permet de configurer des alternatives à la mise en cache du système de fichiers par défaut. Le présent guide présente certaines de ces alternatives, à savoir :

- Configurez les mécanismes de cache suivants dans la configuration [!DNL Commerce] :

   - [ Base de données ](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Système de fichiers (par défaut) : aucune configuration n’est nécessaire pour utiliser la mise en cache du système de fichiers par défaut.

- Configurez le [vernis](config-varnish.md) sans modifier la configuration du [!DNL Commerce].

## Terminologie de mise en cache

[!DNL Commerce] utilise la terminologie de mise en cache suivante :

- **Frontend** : similaire à une interface ou une passerelle pour le stockage en cache, implémenté par [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Types de cache**—Il peut s&#39;agir de l&#39;un des types fournis avec [!DNL Commerce] ou vous pouvez [créer le vôtre](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Serveur principal** : spécifie des détails sur le [stockage en cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implémenté par [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Serveur principal à deux niveaux** : stocke les enregistrements du cache dans deux serveurs principaux : un plus rapide et un plus lent.

  >[!INFO]
  >
  >La configuration du cache principal à deux niveaux dépasse le cadre de ce guide.

## Options de configuration

- Modification du front-end du cache de `default` fourni—

  Vous modifiez uniquement le fichier `<magento_root>/app/etc/di.xml`, la configuration d’injection de dépendance globale de l’application Commerce.

- Configurer votre propre cache frontal personnalisé—

  Vous modifiez uniquement le fichier `<magento_root>/app/etc/env.php`, car il remplace la configuration équivalente dans le fichier `di.xml`.

>[!TIP]
>
>Le vernis ne nécessite pas de modifications de la configuration [!DNL Commerce]. Voir [Configurer et utiliser le vernis](config-varnish.md).
