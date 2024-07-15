---
title: Bonnes pratiques relatives à la configuration des moteurs de recherche Web
description: Découvrez comment transmettre des instructions sur votre site Adobe Commerce aux développeurs Web à l’aide de fichiers `robots.txt` et `sitemap.xml`.
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: e1e7ad76b1df8e920ab7f9740fd4be8dc7335954
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Bonnes pratiques relatives à la configuration des moteurs de recherche Web

Cet article fournit les bonnes pratiques pour l&#39;utilisation des fichiers `robots.txt` et `sitemap.xml` dans Adobe Commerce, y compris la configuration et la sécurité. Ces fichiers enseignent aux robots de moteur de recherche (généralement les robots de recherche) comment analyser les pages d’un site web. La configuration de ces fichiers peut améliorer les performances du site et l’optimisation du moteur de recherche.

>[!NOTE]
>
>Ces bonnes pratiques s’appliquent uniquement aux projets utilisant le storefront natif d’Adobe Commerce. Elles ne s’appliquent pas aux projets Adobe Commerce qui utilisent d’autres solutions de storefront (par exemple, Adobe Experience Manager, headless).

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Adobe Commerce sur l’infrastructure cloud

Un projet Adobe Commerce par défaut contient une hiérarchie qui inclut un seul site web, un seul magasin et une seule vue de magasin. Pour les implémentations plus complexes, vous pouvez créer des sites web, des magasins et des vues de magasin supplémentaires pour une vitrine _multi-site_.

### Devanteries sur site unique

Suivez les bonnes pratiques suivantes lors de la configuration des fichiers `robots.txt` et `sitemap.xml` pour les vitrines à site unique :

- Assurez-vous que votre projet utilise la version 2002.0.12 de [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) ou une version ultérieure.
- Utilisez l’application d’administration pour ajouter du contenu au fichier `robots.txt`.

  >[!TIP]
  >
  >Affichez le fichier `robots.txt` généré automatiquement pour votre magasin sur `<domain.your.project>/robots.txt`.

- Utilisez l’application d’administration pour générer un fichier `sitemap.xml`.

  >[!IMPORTANT]
  >
  >En raison du système de fichiers en lecture seule sur Adobe Commerce sur les projets d’infrastructure cloud, vous devez spécifier le chemin d’accès `pub/media` avant de générer le fichier.

- Utilisez un extrait de code VCL Fastly personnalisé pour rediriger la racine de votre site vers l’emplacement `pub/media/` pour les deux fichiers :

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Testez la redirection en affichant les fichiers dans un navigateur web. Par exemple, `<domain.your.project>/robots.txt` et `<domain.your.project>/sitemap.xml`. Assurez-vous d’utiliser le chemin racine pour lequel vous avez configuré la redirection et non un autre chemin.

>[!INFO]
>
>Voir [Ajout de robots de moteur de recherche et de carte de site](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) pour obtenir des instructions détaillées.


### Bannières de magasin multi-site

Vous pouvez configurer et exécuter plusieurs magasins avec une seule mise en oeuvre d’Adobe Commerce sur l’infrastructure cloud. Voir [Configuration de plusieurs sites Web ou magasins](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

Les mêmes bonnes pratiques pour la configuration des fichiers `robots.txt` et `sitemap.xml` pour les [ vitrines à site unique ](#single-site-storefronts) s’appliquent aux vitrines à plusieurs sites avec deux différences importantes :

- Assurez-vous que les noms des fichiers `robots.txt` et `sitemap.xml` contiennent les noms des sites correspondants. Par exemple :
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Utilisez un extrait de code VCL personnalisé légèrement modifié pour rediriger la racine de vos sites vers l’emplacement `pub/media` pour les deux fichiers sur vos sites :

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerce sur site

Utilisez l’application d’administration pour configurer les fichiers `robots.txt` et `sitemap.xml` afin d’empêcher les robots d’analyser et d’indexer le contenu inutile (voir [Robots de moteur de recherche](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Pour les déploiements sur site, où vous écrivez les fichiers, cela dépend de la manière dont vous avez installé Adobe Commerce. Écrivez les fichiers sur `/path/to/commerce/pub/media/` ou `/path/to/commerce/media`, selon ce qui convient à votre installation.

## Sécurité

N’exposez pas votre chemin d’accès administrateur dans votre fichier `robots.txt`. Le chemin d’accès administrateur est exposé à une vulnérabilité de piratage de site et de perte potentielle de données. Supprimez le chemin d’accès administrateur du fichier `robots.txt`.

Pour les étapes de modification du fichier `robots.txt` et de suppression de toutes les entrées du chemin d’accès administrateur, voir [ Guide de l’utilisateur marketing > SEO et recherche > Robots du moteur de recherche](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Si vous avez besoin d’aide, [soumettez un ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Informations supplémentaires

- [Comprendre les sites web, les magasins et les vues de magasin](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Ajout de sites Web](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Utilisez Fastly pour bloquer le trafic malveillant de vos sites Adobe Commerce](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt renvoie une erreur 404 dans Adobe Commerce sur l’infrastructure cloud 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
