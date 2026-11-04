# INOX.UP — thème Blogger professionnel

Refonte complète de `inox.xml` pour présenter les services d’**INOX.UP** dans un site Blogger rapide, responsive et orienté vers la demande de devis.

## Ce qui est inclus

- Accueil premium graphite et bleu acier, avec navigation fixe et menu mobile accessible.
- Logo Blogger d’origine avec fallback automatique, favicon coordonné et liens Instagram visibles dans la barre supérieure, une bannière dédiée et le pied de page.
- Services, applications en inox, méthode de travail, avantages et FAQ.
- Galerie avec visionneuse native (`<dialog>`), sans bibliothèque externe.
- Formulaire de devis qui prépare un message WhatsApp ; aucun backend et aucune donnée enregistrée.
- Articles, pages, pagination et commentaires Blogger stylés.
- SEO renforcé : titres et descriptions d’articles, image de partage à la une, dates et étiquettes, Open Graph, Twitter Card, sitemap et données structurées `LocalBusiness`, `WebSite`, `FAQPage` et `BreadcrumbList`.
- Images optimisées, chargement différé, mise en page responsive et prise en charge de `prefers-reduced-motion`.
- Aucun framework JavaScript, aucune publicité de démonstration et aucun iframe social lourd.

## Fichiers

```text
inox.xml                    Thème à importer dans Blogger
assets/inoxup/             Images et favicon utilisés par le thème
```

Les URL des visuels pointent vers :

```text
https://raw.githubusercontent.com/zougar99/xml/main/assets/inoxup/
```

**Le dossier `assets` doit donc accompagner le thème et être présent sur la branche `main`.** Ne récupérez pas `inox.xml` seul sans publier aussi les images.

## Installation dans Blogger

1. Dans Blogger, sauvegardez d’abord le thème actuel : **Thème → menu ⋮ → Sauvegarder**.
2. Vérifiez que `inox.xml` et le dossier `assets/inoxup` sont bien publiés sur `main`.
3. Ouvrez **Thème → menu ⋮ → Modifier le HTML**, remplacez le contenu par celui de `inox.xml`, puis enregistrez. Vous pouvez aussi utiliser **Restaurer → Importer** si cette option est proposée.
4. Dans **Paramètres → Balises Meta**, activez la description pour les moteurs de recherche.
5. Vérifiez l’accueil, un article, une page statique et le formulaire WhatsApp sur téléphone.
6. Dans Google Search Console, ajoutez la propriété du blog puis envoyez `https://inoxup.blogspot.com/sitemap.xml`. Pour chaque article, ajoutez une image à la une et une description de recherche dans Blogger.

## Personnalisation

### Logo et Instagram

Le thème réutilise l’image carrée 1600 × 1600 qui était enregistrée dans le widget Header du thème d’origine. Instagram ne permettant pas de vérifier publiquement le profil depuis l’environnement de développement, **contrôlez visuellement qu’il s’agit bien du logo actuel**. Pour le remplacer, recherchez `blogger.googleusercontent.com/img/a/` dans `inox.xml` et remplacez les URL du logo par celles de votre image officielle. Les variantes `s160`, `s180`, `s320` et `s512` optimisent les différents affichages.

Le compte [instagram.com/inox_up](https://www.instagram.com/inox_up/) est présent dans la barre supérieure, la bannière sociale, le pied de page et les données structurées. La bannière ouvre le profil officiel ; elle ne prétend pas charger automatiquement les Reels. L’intégration d’une vidéo Instagram précise nécessite l’URL ou le code d’intégration de cette publication.

### Téléphone et WhatsApp

Recherchez `212688913311` dans `inox.xml` et remplacez-le par le numéro international, sans `+`, espaces ni tirets dans les liens `wa.me`. Modifiez également le numéro affiché dans les liens `tel:` et les textes.

### Horaires et réseaux sociaux

Les horaires figurent dans la barre supérieure, le pied de page et le JSON-LD. Les liens Instagram et Facebook sont regroupés dans le pied de page et les données structurées.

### Images

Les visuels actuels sont des **images d’ambiance générées pour la maquette**, pas des réalisations certifiées d’INOX.UP. Avant la mise en ligne définitive, remplacez-les idéalement par de vraies photos de projets :

1. Téléversez vos photos dans Blogger ou sur votre hébergement d’images.
2. Remplacez les URL dans le hero et la galerie.
3. Conservez les attributs `alt`, `width`, `height` et `loading` pour l’accessibilité et la stabilité visuelle.
4. Mettez aussi à jour l’image Open Graph dans `<head>`.

### Formulaire de devis

Le formulaire utilise uniquement JavaScript pour construire une URL `wa.me`. Il n’envoie rien à un serveur et ne stocke aucune donnée. Les champs saisis ne sont transmis que lorsque le visiteur envoie le message dans WhatsApp.

## Vérifications effectuées

- XML bien formé et structure Blogger conservée pour les articles/commentaires.
- Syntaxe JavaScript et quatre blocs JSON-LD (`LocalBusiness`, `WebSite`, `FAQPage`, `BreadcrumbList`) validés.
- Chargement du logo et fonctionnement du fallback testés.
- Contrôle visuel sur desktop et mobile.
- Aucun débordement horizontal aux largeurs 320, 390, 768, 1024 et 1440 px.
- Menu mobile, galerie, présélection des services et composition du message WhatsApp testés.
- Audit automatisé WCAG 2 A/AA et WCAG 2.1 A/AA sans violation détectée sur la maquette desktop et mobile.
