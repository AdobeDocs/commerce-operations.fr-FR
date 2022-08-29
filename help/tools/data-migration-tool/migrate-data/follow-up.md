---
title: Suivi de la migration des données
description: Découvrez comment vérifier que la migration des données de votre Magento 1 vers Magento 2 a réussi et que toutes les fonctionnalités fonctionnent comme prévu.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Suivi de la migration des données

Le comportement et la logique du Magento 1 ont été implémentés différemment dans le Magento 2. Le [!DNL Data Migration Tool] s&#39;en occupe. Il existe des aspects de migration que vous devez connaître et, parfois, vous devez prendre des mesures mineures pour que certaines fonctionnalités fonctionnent correctement après la migration.

## Informations

### Partage de la base de données non pris en charge

Le [!DNL Data Migration Tool] ne prend pas en charge les bases de données partagées.

### Prix de groupe convertis en prix de niveau

Lors de la migration, tous les prix de groupe sont automatiquement convertis en prix de niveau.

### Nouvelle numérotation des entités de vente

Les numéros de référence des commandes, factures, envois, notes de crédit et RAM migrent tels quels. Après la migration, les nouvelles règles d’attribution des numéros de Magento 2 s’appliquent. Le nombre des nouvelles entités de vente est différent.

## Étapes

### Réenregistrement des segments client [Adobe Commerce uniquement]

Après la migration, les segments du client doivent être récupérés dans la variable [Administration](https://glossary.magento.com/admin) Panneau pour les mettre en service.

### Configuration du fuseau horaire

L’outil ne migre pas les paramètres de fuseau horaire. Vous devez donc configurer manuellement le fuseau horaire après la migration à l’adresse **Magasins** > **Configuration** > **Options de paramètres régionaux** > **Fuseau horaire**.

Par défaut, Magento stocke les données horaires dans la zone UTC-0 de la base de données et les affiche en fonction des paramètres de fuseau horaire en cours. Si des données horaires ont déjà été enregistrées dans la base de données dans une zone autre que UTC-0, vous devez convertir l’heure existante en UTC-0 à l’aide de la variable [!DNL Data Migration Tool]&#39;s `\Migration\Handler\Timezone` gestionnaire.

Dans l&#39;exemple suivant, le Magento 1 a incorrectement gagné du temps dans la zone UTC-7 de la base de données (par exemple, en raison d&#39;une extension tierce défectueuse). Pour convertir correctement l’heure de création du compte client en fuseau UTC-0 lors de la migration, procédez comme suit :

1. Copiez le `map-customer.xml.dist` fichier de configuration à partir du répertoire approprié du fichier [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) dans le `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` fichier .

1. Mettez à jour le `<customer_map_file>` noeud dans `config.xml` et supprimez la variable `.dist` de `map-customer.xml.dist`

1. Ajoutez la règle suivante au `map-customer.xml` fichier :

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
