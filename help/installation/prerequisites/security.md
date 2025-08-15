---
title: Sécurité de l’installation sur site
description: Découvrez comment améliorer la posture de sécurité de votre installation sur site Adobe Commerce.
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Sécurité de l’installation sur site

[Security Enhanced Linux (SELinux)](https://selinuxproject.org/page/Main_Page) permet aux administrateurs de CentOS et d&#39;Ubuntu de mieux contrôler l&#39;accès à leurs serveurs. Si vous utilisez SELinux *et* Apache doit lancer une connexion à un autre hôte, vous devez exécuter les commandes décrites dans cette section.

>[!NOTE]
>
>Adobe n’a aucune recommandation concernant l’utilisation de SELinux ; vous pouvez l’utiliser pour une sécurité renforcée si vous le souhaitez. Si vous utilisez SELinux, vous devez le configurer correctement pour que le fonctionnement d’Adobe Commerce soit imprévisible. Si vous choisissez d’utiliser SELinux, consultez une ressource telle que le wiki [CentOS](https://wiki.centos.org/HowTos/SELinux) pour configurer des règles permettant d’activer la communication.

## Suggestion d’installation avec Apache

Si vous choisissez d’activer SELinux, vous risquez de rencontrer des problèmes lors de l’exécution du programme d’installation, sauf si vous modifiez le *contexte de sécurité* de certains répertoires comme suit :

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

Les commandes précédentes ne fonctionnent qu’avec le serveur web Apache. En raison de la variété des configurations et des exigences de sécurité, nous ne garantissons pas que ces commandes fonctionnent dans toutes les situations. Pour plus d’informations, voir :

* [page man](https://linux.die.net/man/8/httpd_selinux)
* [Server Lab](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Activer la communication entre serveurs

Si Apache et le serveur de base de données se trouvent sur le même hôte, utilisez la commande suivante si vous envisagez d’utiliser des intégrations qui utilisent `curl` (par exemple, . Paypal et USPS).
Pour permettre à Apache de lancer une connexion à un autre hôte avec SELinux activé :

1. Pour déterminer si SELinux est activé, utilisez la commande suivante :

   ```bash
   getenforce
   ```

   `Enforcing` affiche pour confirmer que SELinux est en cours d’exécution.

   * CentOS : `setsebool -P httpd_can_network_connect=1`
   * Ubuntu : `setsebool -P apache2_can_network_connect=1`

## Ouverture des ports dans votre pare-feu

Selon vos exigences en matière de sécurité, vous devrez peut-être ouvrir le port 80 et d&#39;autres ports dans votre pare-feu. En raison de la nature sensible de la sécurité des réseaux, Adobe vous recommande vivement de consulter votre service informatique avant de continuer. Voici quelques références suggérées :

* Ubuntu : [page de documentation Ubuntu](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS : procédure [CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).
