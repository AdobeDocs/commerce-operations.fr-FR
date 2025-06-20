---
title: Désactiver la sortie du module
description: Découvrez comment désactiver la sortie du module.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: fee09845777e23717e618ac57df4158d6b172d4f
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Désactiver la sortie du module

Par défaut, tous les modules sont configurés de sorte que la sortie du module puisse être écrite dans une vue. La désactivation de la sortie offre un moyen de désactiver un module qui ne peut pas être désactivé en raison de dépendances difficiles.

Par exemple, le module de `Customer` dépend du module de `Review`, le module de `Review` ne peut donc pas être désactivé. Cependant, si vous ne souhaitez pas que les clients fournissent des commentaires, vous pouvez désactiver la sortie du module `Review`.

>[!INFO]
>
>Si un commerçant a utilisé Admin pour désactiver la sortie du module dans une version précédente, vous devez configurer manuellement le système pour migrer ces paramètres.

La désactivation de Output est effectuée dans les classes suivantes :

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>La désactivation de la sortie du module ne désactive pas le module. Le module reste activé et fonctionnel, mais aucun bloc, page ou champ n’est rendu sur le front-end ou le serveur principal.

## Désactiver la sortie du module dans un déploiement de pipeline

Pour désactiver la sortie du module dans le déploiement du pipeline ou tout autre déploiement, avec plusieurs instances de l’application Commerce :

1. Modifiez le fichier `config.xml` du module `Backend`.
1. Exportez les modifications de configuration.

### Modifier le fichier `config.xml` du module `Backend`

1. Archivez le fichier `config.xml` d’origine.
1. Ajoutez au fichier `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` des lignes similaires aux suivantes, directement sous l’élément `<default>` :

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

Suite à cet exemple de configuration, les clients ne peuvent plus s’inscrire pour recevoir des newsletters.

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

Voir [ Exporter la configuration ](../cli/export-configuration.md).

## Désactiver la sortie du module dans un déploiement simple

La procédure de désactivation de la sortie du module sur une seule instance de Commerce est plus facile, car les modifications n’ont pas besoin d’être distribuées.

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

Dans cet exemple, la sortie du module `Magento_Review` a été désactivée et les clients ne peuvent plus passer en revue les produits.

### Réactiver la sortie du module

Pour réactiver la sortie, définissez la valeur du module sur `0` ou supprimez la ligne/le module du fichier `config.php`.
