---
title: Suivi de la migration des données
description: Découvrez comment vérifier que la migration de vos données Magento 1 vers Magento 2 a réussi et que toutes les fonctionnalités fonctionnent comme prévu.
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Suivi de la migration des données

Certains comportements et logiques de Magento 1 ont été implémentés différemment dans Magento 2. Le [!DNL Data Migration Tool] s&#39;en occupe. Vous devez connaître certains aspects de la migration et parfois, vous devez prendre des mesures mineures pour que certaines fonctionnalités fonctionnent correctement après la migration.

## Informations

### Base de données fractionnée non prise en charge

Le [!DNL Data Migration Tool] ne prend pas en charge les bases de données fractionnées.

### Prix du groupe convertis en prix de niveau

Tous les prix de groupe sont automatiquement convertis en prix de niveau lors de la migration.

### Nouvelle numérotation des entités de vente

Les numéros de référence pour les commandes, les factures, les expéditions, les avoirs et les retours client sont migrés en l&#39;état. Après la migration, les nouvelles règles d’attribution de numéros Magento 2 s’appliquent. La numération des nouvelles entités de vente est différente.

## Étapes

### Réenregistrer les segments de clients [Adobe Commerce uniquement]

Après la migration, les segments de clients doivent être enregistrés à partir du panneau d’administration pour être opérationnels.

### Configurer le fuseau horaire

L’outil ne migre pas les paramètres de fuseau horaire. Vous devez donc configurer manuellement le fuseau horaire après la migration sur **Magasins** > **Configuration** > **Options de paramètres régionaux** > **Fuseau horaire**.

Par défaut, Magento stocke les données horaires dans le fuseau UTC-0 dans la base de données et les affiche en fonction des paramètres de fuseau horaire actuels. Si les données de temps ont déjà été enregistrées dans la base de données dans une zone autre que UTC-0, vous devez convertir l’heure existante en UTC-0 à l’aide du gestionnaire de [!DNL Data Migration Tool] de l’`\Migration\Handler\Timezone`.

Dans l’exemple suivant, Magento 1 a enregistré un gain de temps incorrect dans la zone UTC-7 de la base de données (en raison, par exemple, d’une extension tierce défectueuse). Pour convertir correctement l’heure de création du compte client dans la zone UTC-0 lors de la migration, procédez comme suit :

1. Copiez le fichier de configuration `map-customer.xml.dist` du répertoire approprié du [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) dans le fichier `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml`.

1. Mettez à jour le nœud `<customer_map_file>` dans `config.xml` et supprimez l’extension `.dist` de `map-customer.xml.dist`

1. Ajoutez la règle suivante au fichier `map-customer.xml` :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="../map.xsd">
  <!--...-->
  <destination>
      <field_rules>
          <!--...-->
          <transform>
              <field>customer_entity.created_at</field>
              <handler class="\Migration\Handler\Timezone">
                  <param name="offset" value="-7" />
              </handler>
          </transform>
      </field_rules>
  </destination>
</map>
```
