---
title: Bonnes pratiques de configuration des robots d’exploration web
description: Découvrez comment transmettre des instructions sur votre site Adobe Commerce à des robots d’exploration web à l’aide de fichiers « robots.txt » et « sitemap.xml ».
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Bonnes pratiques de configuration des robots d’exploration web

Cet article fournit les bonnes pratiques relatives à l’utilisation des fichiers `robots.txt` et `sitemap.xml` dans Adobe Commerce, y compris la configuration et la sécurité. Ces fichiers indiquent aux robots d’exploration web (généralement des robots de moteurs de recherche) comment analyser les pages d’un site web. La configuration de ces fichiers peut améliorer les performances du site et l’optimisation du moteur de recherche.

>[!NOTE]
>
>Ces bonnes pratiques s’appliquent aux projets utilisant le storefront natif d’Adobe Commerce uniquement. Elles ne s’appliquent pas aux projets Adobe Commerce qui utilisent d’autres solutions de storefront (par exemple, Adobe Experience Manager, découplé).

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Adobe Commerce sur les infrastructures cloud

Un projet Adobe Commerce par défaut contient une hiérarchie qui comprend un seul site web, magasin et vue de magasin. Pour les implémentations plus complexes, vous pouvez créer d’autres sites web, magasins et vues de magasin pour un storefront _multisite_.

### Vitrines à site unique

Suivez ces bonnes pratiques lors de la configuration des fichiers `robots.txt` et `sitemap.xml` pour les storefronts à site unique :

- Assurez-vous que votre projet utilise [`ece-tools`](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) version 2002.0.12 ou ultérieure.
- Utilisez l’application d’administration pour ajouter du contenu au fichier `robots.txt`.

  >[!TIP]
  >
  >Affichez le fichier `robots.txt` généré automatiquement pour votre boutique sur `<domain.your.project>/robots.txt`.

- Utilisez l’application Admin pour générer un fichier `sitemap.xml`.

  >[!IMPORTANT]
  >
  >En raison du système de fichiers en lecture seule sur Adobe Commerce pour les projets d’infrastructure cloud, vous devez spécifier le chemin d’accès au `pub/media` avant de générer le fichier.

- Utilisez un fragment de code VCL Fastly personnalisé pour rediriger depuis la racine de votre site vers l’emplacement `pub/media/` pour les deux fichiers :

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Testez la redirection en affichant les fichiers dans un navigateur web. Par exemple, `<domain.your.project>/robots.txt` et `<domain.your.project>/sitemap.xml`. Assurez-vous d’utiliser le chemin racine pour lequel vous avez configuré la redirection et non un chemin différent.

>[!INFO]
>
>Voir [Ajouter un plan du site et des robots de moteurs de recherche](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) pour obtenir des instructions détaillées.


### Storefronts multisites

Vous pouvez configurer et exécuter plusieurs magasins avec une seule implémentation d’Adobe Commerce sur l’infrastructure cloud. Voir [Configuration de plusieurs sites web ou magasins](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites).

Les mêmes bonnes pratiques pour la configuration des fichiers `robots.txt` et `sitemap.xml` pour les [storefronts à site unique](#single-site-storefronts) s’appliquent aux storefronts multisites avec deux différences importantes :

- Assurez-vous que les noms de fichier `robots.txt` et `sitemap.xml` contiennent les noms des sites correspondants. Par exemple :
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Utilisez un fragment de code VCL Fastly personnalisé légèrement modifié pour rediriger de la racine de vos sites vers l’emplacement `pub/media` pour les deux fichiers de vos sites :

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerce On-Premise

Utilisez l’application d’administration pour configurer les fichiers `robots.txt` et `sitemap.xml` afin d’empêcher les robots d’analyser et d’indexer le contenu inutile (voir [Robots de moteurs de recherche](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Pour les déploiements sur site, l’endroit où vous écrivez les fichiers dépend de la manière dont vous avez installé Adobe Commerce. Écrivez les fichiers sur `/path/to/commerce/pub/media/` ou `/path/to/commerce/media`, selon ce qui convient à votre installation.

## Sécurité

N’exposez pas le chemin d’accès d’administrateur dans votre fichier `robots.txt`. L’exposition du chemin d’accès d’administration entraîne une vulnérabilité pour le piratage du site et une perte potentielle de données. Supprimez le chemin d’accès Administrateur du fichier `robots.txt`.

Pour connaître la procédure de modification du fichier `robots.txt` et de suppression de toutes les entrées du chemin d’accès administrateur, voir [Guide de l’utilisateur marketing > SEO et recherche > Robots de moteurs de recherche](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Si vous avez besoin d’aide, [envoyez un ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Informations supplémentaires

- [Présentation des sites web, des boutiques et des affichages de boutique](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [Ajout de sites web](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [Utilisez Fastly pour bloquer le trafic malveillant sur vos sites Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [robots.txt renvoie une erreur 404 dans Adobe Commerce sur cloud infrastructure 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
