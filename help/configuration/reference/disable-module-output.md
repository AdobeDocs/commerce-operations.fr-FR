---
title: Désactiver la sortie du module
description: Découvrez comment désactiver la sortie du module.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Désactiver la sortie du module

Par défaut, tous les modules sont configurés afin que la sortie du module puisse être écrite dans une vue. La désactivation de la sortie permet de désactiver essentiellement un module qui ne peut pas être désactivé en raison de dépendances hard.

Par exemple, le module `Customer` dépend du module `Review`, de sorte que le module `Review` ne peut pas être désactivé. Cependant, si vous ne souhaitez pas que les clients fournissent des révisions, vous pouvez désactiver la sortie du module `Review`.

>[!INFO]
>
>Si un commerçant a utilisé l’Admin pour désactiver la sortie du module dans une version précédente, vous devez configurer manuellement le système pour migrer ces paramètres.

La désactivation de la sortie est effectuée dans les classes suivantes :

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>La désactivation de la sortie du module ne désactive pas le module. Le module reste activé et opérationnel, mais aucun bloc, page ou champ n’est rendu sur le serveur frontal ou le serveur principal.

## Désactivation de la sortie de module dans un déploiement de pipeline

Pour désactiver la sortie du module dans le déploiement du pipeline ou tout autre déploiement, avec plusieurs instances de l’application Commerce :

1. Modifiez le fichier `config.xml` du module `Backend`.
1. Exportez les modifications de configuration.

### Modification du fichier `Backend` module `config.xml`

1. Archivez le fichier `config.xml` d’origine.
1. Ajoutez des lignes similaires à ce qui suit au fichier `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml`, directement sous l’élément `<default>` :

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   Ici :

   - `<modules_disable_output>` contient une liste de modules.
   - `<Magento_Newsletter></Magento_Newsletter>` spécifie le module pour lequel désactiver la sortie.
   - `1` est l’indicateur qui désactive la sortie pour le module `Magento_Newsletter`.

À titre d’exemple, les clients ne peuvent plus s’inscrire pour recevoir des newsletters.

### Exporter les modifications de configuration

Exécutez la commande suivante pour exporter les modifications de configuration :

```bash
bin/magento app:config:dump
```

Les résultats sont écrits dans le fichier `<Magento_install_dir>/app/etc/config.php`.

Ensuite, effacez le cache pour activer le nouveau paramètre :

```bash
bin/magento cache:clean config
```

Voir [Exporter la configuration](../cli/export-configuration.md).

## Désactivation de la sortie de module dans un déploiement simple

La procédure de désactivation de la sortie du module sur une seule instance de Commerce est plus simple, car les modifications n’ont pas à être distribuées.

1. Archivez le fichier `<Magento_install_dir>/app/etc/config.php` d’origine.
1. Ajoutez les sections `advanced` et `modules_disable_output` au fichier `config.php` (si elles n’existent pas) :

   ```php
   'system' =>
     array (
       'websites' =>
       array (
         'base' =>
         array (
           'advanced' =>
           array (
             'modules_disable_output' =>
             array (
               'Magento_Review' => '1',
             ),
           ),
         ),
       ),
     ),
   ```

Dans cet exemple, la sortie du module `Magento_Review` a été désactivée et les clients ne peuvent plus consulter les produits.
Pour réactiver la sortie, définissez la valeur sur `0`.
