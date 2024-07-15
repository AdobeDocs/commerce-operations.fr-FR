---
title: Suivi de la migration des données
description: Découvrez comment vérifier que la migration des données de votre Magento 1 vers Magento 2 a réussi et que toutes les fonctionnalités fonctionnent comme prévu.
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Suivi de la migration des données

Le comportement et la logique du Magento 1 ont été implémentés différemment dans le Magento 2. Le [!DNL Data Migration Tool] s&#39;en occupe. Il existe des aspects de migration que vous devez connaître et, parfois, vous devez prendre des mesures mineures pour que certaines fonctionnalités fonctionnent correctement après la migration.

## Informations

### Partage de la base de données non pris en charge

[!DNL Data Migration Tool] ne prend pas en charge les bases de données partagées.

### Prix de groupe convertis en prix de niveau

Lors de la migration, tous les prix de groupe sont automatiquement convertis en prix de niveau.

### Nouvelle numérotation des entités de vente

Les numéros de référence des commandes, factures, envois, notes de crédit et RAM migrent tels quels. Après la migration, les nouvelles règles d’attribution des numéros de Magento 2 s’appliquent. Le nombre des nouvelles entités de vente est différent.

## Étapes

### Réenregistrer les segments client [Adobe Commerce uniquement]

Après la migration, les segments client doivent être récupérés à partir du panneau d’administration pour qu’ils soient opérationnels.

### Configuration du fuseau horaire

L’outil ne migre pas les paramètres de fuseau horaire. Vous devez donc configurer manuellement le fuseau horaire après la migration dans **Magasins** > **Configuration** > **Options de paramètres régionaux** > **Fuseau horaire**.

Par défaut, Magento stocke les données horaires dans la zone UTC-0 de la base de données et les affiche en fonction des paramètres de fuseau horaire en cours. Si des données temporelles ont déjà été enregistrées dans la base de données dans une zone autre que UTC-0, vous devez convertir l’heure existante en UTC-0 à l’aide du gestionnaire [!DNL Data Migration Tool]&#39;s `\Migration\Handler\Timezone`.

Dans l&#39;exemple suivant, le Magento 1 a incorrectement gagné du temps dans la zone UTC-7 de la base de données (par exemple, en raison d&#39;une extension tierce défectueuse). Pour convertir correctement l’heure de création du compte client en fuseau UTC-0 lors de la migration, procédez comme suit :

1. Copiez le fichier de configuration `map-customer.xml.dist` du répertoire approprié de [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) dans le fichier `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml`.

1. Mettez à jour le noeud `<customer_map_file>` dans `config.xml` et supprimez l’extension `.dist` de `map-customer.xml.dist`

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
