---
title: Sécurité de l’installation sur site
description: Découvrez comment améliorer la sécurité de votre installation sur site Adobe Commerce ou Magento Open Source.
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Sécurité de l’installation sur site

[Sécurité Amélioration de Linux (SELinux)](https://selinuxproject.org/page/Main_Page) permet aux administrateurs CentOS et Ubuntu de mieux contrôler l’accès à leurs serveurs. Si vous utilisez SELinux *et* Apache doit établir une connexion à un autre hôte. Vous devez exécuter les commandes décrites dans cette section.

>[!NOTE]
>
>Adobe ne recommande pas d’utiliser SELinux ; vous pouvez l’utiliser pour une sécurité renforcée si vous le souhaitez. Si vous utilisez SELinux, vous devez le configurer correctement, sinon Adobe Commerce et Magento Open Source peuvent fonctionner de manière imprévisible. Si vous choisissez d’utiliser SELinux, consultez une ressource telle que la variable [Wiki de CentOS](https://wiki.centos.org/HowTos/SELinux) pour configurer des règles pour activer la communication.

## Suggestion d’installation avec Apache

Si vous choisissez d’activer SELinux, il se peut que vous rencontriez des problèmes lors de l’exécution du programme d’installation, sauf si vous modifiez la variable *contexte de sécurité* de certains répertoires comme suit :

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

Les commandes précédentes fonctionnent uniquement avec le serveur web Apache. En raison de la variété des configurations et des exigences de sécurité, nous ne garantissons pas que ces commandes fonctionnent dans toutes les situations. Pour plus d’informations, voir :

* [page principale](https://linux.die.net/man/8/httpd_selinux)
* [Server Lab](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Activer la communication entre les serveurs

Si Apache et le serveur de base de données se trouvent sur le même hôte, utilisez la commande suivante si vous prévoyez d’utiliser des intégrations qui utilisent `curl` (ex. Paypal et USPS).
Pour permettre à Apache d’initier une connexion à un autre hôte avec SELinux activé :

1. Pour déterminer si SELinux est activé, utilisez la commande suivante :

   ```bash
   getenforce
   ```

   `Enforcing` s’affiche pour confirmer que SELinux est en cours d’exécution.

   * CentOS : `setsebool -P httpd_can_network_connect=1`
   * Ubuntu : `setsebool -P apache2_can_network_connect=1`

## Ouverture de ports dans votre pare-feu

Selon vos exigences de sécurité, vous devrez peut-être ouvrir le port 80 et d’autres ports dans votre pare-feu. En raison de la nature sensible de la sécurité du réseau, Adobe vous recommande vivement de consulter votre service informatique avant de poursuivre. Voici quelques suggestions de références :

* Ubuntu : [Page de documentation Ubuntu](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS : [Procédures relatives à CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).
