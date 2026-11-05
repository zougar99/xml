# INOX.UP — thème Blogger professionnel

Refonte complète de `inox.xml` pour présenter les services d’**INOX.UP** dans un site Blogger rapide, responsive et orienté vers la demande de devis.

## Ce qui est inclus

- Accueil premium graphite et bleu acier, avec navigation fixe et menu mobile accessible.
- Interface en français, arabe et anglais, avec RTL complet, police Noto Sans Arabic, titre d’accueil localisé et annonces accessibles.
- Mode clair/sombre persistant, avec hero réellement clair ou sombre, transitions animées et couleur du navigateur synchronisée.
- Logo Blogger d’origine avec fallback automatique, favicon coordonné et liens Instagram visibles dans la barre supérieure, une bannière dédiée et le pied de page.
- Services, applications en inox, méthode de travail, avantages et FAQ.
- Galerie avec visionneuse native (`<dialog>`), navigation précédent/suivant, clavier, swipe tactile et compteur, sans bibliothèque externe.
- Animations d’apparition au scroll, navigation de section active, barre de progression et micro-interactions, sans dépendance JavaScript et avec respect de `prefers-reduced-motion`.
- Images WebP responsives (640/960/1280 px), préchargement LCP adapté à la page et police Manrope variable auto-hébergée.
- Formulaire de devis qui prépare un message WhatsApp ; aucun backend et aucune donnée enregistrée.
- Articles, pages, pagination et commentaires Blogger stylés.
- SEO renforcé : titres et descriptions d’articles, image de partage à la une, dates et étiquettes, Open Graph, Twitter Card, sitemap et données structurées `LocalBusiness`, `WebSite`, `FAQPage` et `BreadcrumbList`.
- Images optimisées, chargement différé, mise en page responsive et prise en charge de `prefers-reduced-motion`.
- Aucun framework JavaScript, aucune publicité de démonstration et aucun iframe social lourd.

## Fichiers

```text
inox.xml                    Thème à importer dans Blogger
assets/inoxup/             Images JPG/WebP et favicon utilisés par le thème
assets/inoxup/fonts/       Manrope variable et sa licence OFL
```

Les URL des visuels pointent vers :

```text
https://raw.githubusercontent.com/zougar99/xml/main/assets/inoxup/
```

**Le dossier `assets` doit donc accompagner le thème et être présent sur la branche `main`.** Ne récupérez pas `inox.xml` seul sans publier aussi les images et la police auto-hébergée. Les JPG restent utilisés pour le partage Open Graph ; les variantes WebP servent l’affichage responsive.

## Installation dans Blogger

1. Dans Blogger, sauvegardez d’abord le thème actuel : **Thème → menu ⋮ → Sauvegarder**.
2. Vérifiez que `inox.xml` et le dossier `assets/inoxup` sont bien publiés sur `main`.
3. Ouvrez **Thème → menu ⋮ → Modifier le HTML**, remplacez le contenu par celui de `inox.xml`, puis enregistrez. Vous pouvez aussi utiliser **Restaurer → Importer** si cette option est proposée.
4. Dans **Paramètres → Balises Meta**, activez la description pour les moteurs de recherche.
5. Vérifiez l’accueil, un article, une page statique et le formulaire WhatsApp sur téléphone, dans les trois langues et les deux thèmes.
6. Dans Google Search Console, ajoutez la propriété du blog puis envoyez `https://inoxup.blogspot.com/sitemap.xml`. Pour chaque article, ajoutez une image à la une et une description de recherche dans Blogger.

## PageSpeed et réglages Blogger

Les optimisations du thème ne remplacent pas les réglages du blog. Après l’import, vérifiez également :

- **Paramètres → Confidentialité** : laissez le blog visible pour les moteurs de recherche.
- **Paramètres → Balises Meta** : activez la description de recherche et rédigez une description unique pour le blog et pour les articles importants.
- **Paramètres → Robots** : ne bloquez pas l’accueil ni les articles dans les balises personnalisées ou dans `robots.txt`. N’ajoutez pas de directive sans en vérifier l’effet.
- **Search Console** : envoyez le sitemap, contrôlez l’indexation et corrigez les titres/descriptions signalés.
- **Contenu** : ajoutez des descriptions et des images à la une aux articles ; les données structurées ne compensent pas un contenu vide ou dupliqué.

Les mesures locales du thème statique donnent **100/100/100/100** sur l’accueil mobile et desktop, puis **96 en Performance** et **100 en Accessibilité, Bonnes pratiques et SEO** sur la maquette d’article mobile (Lighthouse, Performance/Accessibilité/Bonnes pratiques/SEO). Ce sont des contrôles de laboratoire sur les fichiers de cette branche, pas une garantie du score en ligne. Le PageSpeed du domaine Blogger dépend aussi du réseau, du cache, des articles réels, des commentaires, des vidéos et des scripts tiers. **Le site en ligne ne changera qu’après l’import du XML dans Blogger.**

## Personnalisation

### Langues et mode sombre

Le sélecteur **FR / AR / EN** et le bouton soleil/lune se trouvent dans l’en-tête. Le français est la langue initiale par défaut. Le changement se fait sans rechargement, avec une courte transition, et les préférences sont conservées dans le stockage local du navigateur :

```text
inoxup-language    fr, ar ou en
inoxup-theme       light ou dark
```

Les changements manuels utilisent la View Transitions API lorsqu’elle est disponible, avec un fondu WAAPI en fallback et aucune animation en mouvement réduit. Une région `aria-live` annonce la nouvelle langue ou le nouveau thème dans la langue active. Le titre de l’onglet d’accueil est localisé ; les titres d’articles restent inchangés puisque leur contenu n’est pas traduit. Le thème met aussi à jour `color-scheme` et la balise `theme-color` pour les contrôles natifs et la barre du navigateur mobile. Le hero possède des variables de surface, de texte, d’accent et de bouton distinctes en clair et en sombre afin que le changement soit visible dès le premier écran.

Sans choix de thème enregistré, le site suit `prefers-color-scheme`. Un choix manuel devient prioritaire ; pour revenir au comportement du système, supprimez la préférence du site dans les données du navigateur.

L’arabe active `lang="ar"`, `dir="rtl"`, la mise en page RTL et **Noto Sans Arabic**. Les textes de l’interface, les libellés accessibles, les placeholders, les légendes, les dates reconnues et les messages WhatsApp sont localisés. Les valeurs internes des services restent stables pour préserver la présélection et le formulaire.

Les traductions se trouvent dans `var translations` à la fin d’`inox.xml`. Les clés sont les textes français présents dans le HTML. Si vous modifiez un libellé français, modifiez aussi sa clé et ses traductions `en`/`ar`. Les messages WhatsApp sont regroupés dans `whatsappMessages` et `quoteMessages`. Les couleurs sombres sont centralisées dans `:root[data-theme='dark']`.

**Limite volontaire :** le contenu rédigé des articles, pages et commentaires n’est pas traduit automatiquement, pas plus que les messages système natifs de Blogger. Leur direction est déterminée avec `dir="auto"` pour rester lisible dans une interface RTL. Cette solution ne crée pas d’URL localisées ni de balises `hreflang` et ne duplique pas les articles.

### Animations et performances

Les animations utilisent l’API Web Animations et `IntersectionObserver`, sans bibliothèque externe. Les éléments LCP de l’accueil et des articles restent opaques : seules des transformations légères sont animées afin de ne pas retarder leur affichage. Les cartes et les sections secondaires apparaissent progressivement, le menu indique la section active et une barre indique la progression de lecture. La visionneuse permet de circuler avec ses boutons, les flèches gauche/droite du clavier ou un swipe horizontal ; son compteur et ses contrôles sont localisés.

Le système respecte `prefers-reduced-motion` et réagit à son changement. Des fallbacks gardent tout le contenu visible sans JavaScript, sans `IntersectionObserver` ou sans Web Animations. Les mises à jour au scroll sont regroupées avec `requestAnimationFrame`, les dimensions sont mises en cache et `ResizeObserver` recalcule la progression sans lecture synchrone répétée.

Manrope est une police variable auto-hébergée avec préchargement ; sa licence OFL se trouve dans `assets/inoxup/fonts/Manrope-OFL.txt`. Noto Sans Arabic reste fourni par Google Fonts pour les textes arabes. Si vous changez les animations, conservez les règles reduced-motion, les fallbacks et l’opacité initiale des titres/images LCP.

### Logo et Instagram

Le thème réutilise l’image carrée 1600 × 1600 qui était enregistrée dans le widget Header du thème d’origine. Instagram ne permettant pas de vérifier publiquement le profil depuis l’environnement de développement, **contrôlez visuellement qu’il s’agit bien du logo actuel**. Pour le remplacer, recherchez `blogger.googleusercontent.com/img/a/` dans `inox.xml` et remplacez les URL du logo par celles de votre image officielle. Les variantes `s160`, `s180`, `s320` et `s512` optimisent les différents affichages.

Le compte [instagram.com/inox_up](https://www.instagram.com/inox_up/) est présent dans la barre supérieure, la bannière sociale, le pied de page et les données structurées. La bannière ouvre le profil officiel ; elle ne prétend pas charger automatiquement les Reels. L’intégration d’une vidéo Instagram précise nécessite l’URL ou le code d’intégration de cette publication.

### Téléphone et WhatsApp

Recherchez `212688913311` dans `inox.xml` et remplacez-le par le numéro international, sans `+`, espaces ni tirets dans les liens `wa.me`. Modifiez également le numéro affiché dans les liens `tel:` et les textes.

### Horaires et réseaux sociaux

Les horaires figurent dans la barre supérieure, le pied de page et le JSON-LD. Les liens Instagram et Facebook sont regroupés dans le pied de page et les données structurées.

### Images

Les visuels actuels sont des **images d’ambiance générées pour la maquette**, pas des réalisations certifiées d’INOX.UP. Avant la mise en ligne définitive, remplacez-les idéalement par de vraies photos de projets :

1. Préparez chaque visuel en JPG de référence et en WebP aux largeurs 640, 960 et 1280 px, puis publiez-les dans `assets/inoxup` ou sur votre hébergement.
2. Dans le hero et la galerie, remplacez ensemble `src`, `srcset`, `sizes` et `data-full`. Pour une image du hero, mettez aussi à jour le préchargement conditionnel dans `<head>`.
3. Conservez les attributs `alt`, `width`, `height`, `decoding` et `loading` pour l’accessibilité et la stabilité visuelle. L’image LCP ne doit pas être différée.
4. Mettez aussi à jour l’image JPG Open Graph dans `<head>`. Les images insérées par Blogger dans les articles utilisent automatiquement des tailles `resizeImage` responsives.

### Formulaire de devis

Le formulaire utilise uniquement JavaScript pour construire une URL `wa.me`. Il n’envoie rien à un serveur et ne stocke aucune donnée. Les champs saisis ne sont transmis que lorsque le visiteur envoie le message dans WhatsApp.

## Vérifications effectuées

- XML bien formé et structure Blogger conservée pour les articles/commentaires.
- Syntaxe JavaScript et quatre blocs JSON-LD (`LocalBusiness`, `WebSite`, `FAQPage`, `BreadcrumbList`) validés.
- Chargement du logo et fonctionnement du fallback testés.
- Contrôle visuel sur desktop, mobile et tablette, y compris l’arabe RTL et le mode sombre.
- Aucun débordement horizontal ni chevauchement des contrôles aux largeurs 320, 390, 600, 768, 1024, 1080, 1081 et 1440 px.
- Douze combinaisons langue/thème testées sur l’accueil en desktop et mobile, puis douze sur la maquette article/commentaires.
- Persistance après rechargement, retour FR → AR → EN → FR, suivi du thème système et changement de langue sans rechargement testés.
- Transitions de langue/thème avec View Transitions, fallback WAAPI, reduced-motion et absence des deux APIs testées ; annonces localisées, titre d’accueil, `theme-color`, `color-scheme`, couleurs distinctes du hero et conservation des champs du formulaire vérifiés.
- Menu mobile, galerie et changement de langue pendant la visionneuse, présélection des services et composition des messages WhatsApp FR/AR/EN testés.
- Contenu Blogger non traduit et direction automatique des articles/commentaires vérifiés.
- Audits automatisés WCAG 2 A/AA et WCAG 2.1 A/AA sans violation détectée sur les 24 combinaisons accueil/article, desktop/mobile, langue et thème.
- Animations, progression de lecture, navigation active, préférences reduced-motion et fallbacks sans JavaScript/IntersectionObserver/Web Animations testés sur desktop et mobile.
- Navigation dans la visionneuse par boutons, clavier et swipe, compteur, traduction des contrôles et absence d’animation en mouvement réduit vérifiés ; deux audits axe supplémentaires avec la visionneuse ouverte, sans violation.
- Chargement des WebP adaptés au viewport, préchargement LCP, absence de reflow synchrone au scroll et stabilité des images vérifiés.
- Lighthouse local : 100 dans les quatre catégories sur l’accueil mobile et desktop ; 96 en Performance et 100 dans les trois autres catégories sur l’article mobile. Rapports conservés hors du dépôt pour ne pas alourdir le thème.
