# Externatic - Carte Interactive des Technologies Informatiques

## 📋 Présentation

Ce projet consiste en une carte interactive qui présente un **panorama complet des technologies informatiques** regroupées par domaines (Frontend, Backend, DevOps, Cybersécurité, Développement Mobile, etc.).

### Principe

La carte fonctionne selon ces principes clés :

- **Visualisation PDF interactive** : Les cartes sont stockées sous forme de PDF et affichées de manière interactive
- **Sélection par domaine** : L'utilisateur peut choisir un domaine spécifique ou consulter la carte complète
- **Recherche multi-pages** : Moteur de recherche qui scanne toutes les pages et surligne les résultats
- **Zoom et navigation** : Zoom avant/arrière fluide avec navigation facile entre les pages
- **Responsive** : Adaptation à différentes tailles d'écran

### Fonctionnalités

- 📍 **Sélecteur de cartes** : 12 domaines technologiques différents
  - Carte complète
  - Cybersécurité
  - Base de données
  - Développement IA
  - Développement Backend
  - Développement Frontend
  - Développement Mobile
  - DevOps
  - Embarqué
  - Gestion de projet
  - Réseau
  - Outils de développement

- 🔍 **Recherche avancée** : Trouve tous les éléments correspondant à votre requête
- 🔎 **Navigation des résultats** : Boutons précédent/suivant pour naviguer entre les résultats
- 🔍 **Zoom dynamique** : Zoom automatique sur les résultats pour meilleure lisibilité
- ➕ **Contrôles de zoom** : Zoom manuel (+/-) directement accessible

---

## 🚀 Lancer en local

### Prérequis

- Un navigateur web moderne (Chrome, Firefox, Safari, Edge)
- Un serveur web local (même léger)

### Installation et lancement

#### Option 1 : Avec Python (le plus simple)

```bash
# Naviguez vers le dossier du projet
cd /chemin/vers/Externatic-Prod

# Lancer un serveur Python local
python -m http.server 8000
```

Puis ouvrez votre navigateur et allez à : **http://localhost:8000**

#### Option 2 : Avec Node.js

```bash
# Si vous avez Node.js installé
npx http-server .
```

L'application sera accessible à **http://localhost:8080**

#### Option 3 : Avec un éditeur (VS Code, etc.)

- Installez l'extension **Live Server** (si vous utilisez VS Code)
- Clic droit sur `src/index.html` → **Open with Live Server**

### Structure des fichiers

```
Externatic-Prod/
├── src/
│   ├── index.html          # Interface principale
│   └── styles.css          # Styles de la carte
├── assets/
│   ├── entire-map.pdf      # Carte complète
│   ├── cyber-map.pdf       # Cartes par domaine
│   ├── db-map.pdf
│   └── ... (autres PDF)
└── README.md               # Ce fichier
```

---

## 🌐 Intégration dans WordPress

### Approche 1 : Intégration via Iframe (Recommandée)

C'est la méthode la plus simple et la plus sûre.

#### Étapes :

1. **Hebergez le projet** sur un serveur web (même domaine ou différent)
   - Déployez les fichiers du dossier `Externatic-Prod` sur votre serveur

2. **Dans WordPress**, créez une nouvelle page et ajoutez le code suivant :

   ```html
   <iframe
       src="https://votre-domaine.com/chemin/vers/externatic/src/index.html"
       title="Carte Interactive - Technologies Informatiques"
       style="width: 100%; height: 800px; border: none; border-radius: 8px;"
       allow="fullscreen">
   </iframe>
   ```

3. **Personnalisez si besoin** :
   - Ajustez la hauteur (`height: 800px`)
   - Changez l'URL source selon votre serveur
   - Adaptez les styles CSS

#### ⚠️ Important (CORS) :

Si l'iframe affiche une erreur CORS, assurez-vous que :
- Les fichiers sont sur le même domaine que WordPress, OU
- Le serveur qui héberge Externatic autorise les requêtes cross-origin

---

### Approche 2 : Intégration via Plugin personnalisé

Pour une meilleure intégration, créez un plugin WordPress minimaliste.

#### Créer le plugin :

1. **Créez le dossier du plugin** :
   ```bash
   wp-content/plugins/externatic-maps/
   ```

2. **Créez le fichier principal** `externatic-maps.php` :

   ```php
   <?php
   /**
    * Plugin Name: Externatic Maps
    * Description: Intègre la carte interactive Externatic dans WordPress
    * Version: 1.0
    * Author: Votre nom
    */

   // Enregistrer la page du plugin
   add_action('admin_menu', function() {
       add_menu_page(
           'Externatic Maps',
           'Externatic Maps',
           'manage_options',
           'externatic-maps',
           'externatic_render_page',
           'dashicons-location-alt',
           20
       );
   });

   // Rendu de la page
   function externatic_render_page() {
       echo '<div class="wrap">';
       echo '<h1>Carte Interactive - Technologies Informatiques</h1>';
       echo '<iframe src="' . esc_url(plugin_dir_url(__FILE__) . 'src/index.html') . '"
                    style="width: 100%; height: 800px; border: none;"></iframe>';
       echo '</div>';
   }

   // Enregistrer le shortcode
   add_shortcode('externatic_map', function($atts) {
       ob_start();
       echo '<iframe src="' . esc_url(plugin_dir_url(__FILE__) . 'src/index.html') . '"
                   style="width: 100%; height: 800px; border: none;"></iframe>';
       return ob_get_clean();
   });
   ?>
   ```

3. **Copiez les fichiers** :
   - Placez les dossiers `src/` et `assets/` dans le dossier du plugin

4. **Activez le plugin** dans WordPress

5. **Utilisez le shortcode** : Ajoutez `[externatic_map]` dans n'importe quelle page

---

### Approche 3 : Hébergement sur CDN

Pour plus de performance et de flexibilité :

1. **Uploadez sur un CDN** (Netlify, Vercel, GitHub Pages, etc.)
2. **Utilisez l'URL du CDN** dans votre iframe WordPress

**Exemple avec Netlify** :
```html
<iframe
    src="https://your-externatic.netlify.app"
    style="width: 100%; height: 800px; border: none;">
</iframe>
```

---

## 🔧 Configuration avancée

### Modifier les styles pour l'intégration WordPress

Créez un fichier CSS personnalisé dans `src/wordpress-custom.css` :

```css
/* Adapter la hauteur de la toolbar */
#toolbar-main {
    height: 60px;
}

/* Adapter les marges */
#pdf-container {
    top: 60px;
    bottom: 60px;
}
```

Incluez-le dans l'HTML :
```html
<link rel="stylesheet" href="wordpress-custom.css">
```

### Passer des paramètres via URL

Modifiez `index.html` pour accepter un paramètre de carte en URL :

```javascript
// Dans le script, avant la fonction init
const params = new URLSearchParams(window.location.search);
const selectedMap = params.get('map') || 'entire-map.pdf';
url = '../assets/' + encodeURIComponent(selectedMap);
```

Utilisez ensuite :
```html
<iframe src="https://votre-domaine.com/src/index.html?map=cyber-map.pdf"></iframe>
```

---

## 📱 Support et optimisation

### Pour améliorer la performance

- Compressez les PDFs avec un outil comme GhostScript
- Utilisez un CDN pour servir les assets
- Mettez en cache les PDF au niveau du serveur

### Responsive design

L'application est entièrement responsive. Pour WordPress, assurez-vous que le conteneur parent a une largeur adaptée :

```css
.externatic-container {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
}
```

---

## 🤝 Support

Pour des questions ou des améliorations, contactez l'équipe de développement.

Matisse Marsac : matisse.marsac@epitech.eu
Albane Merian : albane.merian@epitech.eu
