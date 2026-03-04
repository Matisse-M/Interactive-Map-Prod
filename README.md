# Guide des Technologies Informatiques

Application web interactive permettant d'explorer et de naviguer dans différentes cartes de technologies informatiques.

## 📋 Présentation

Ce projet propose une interface intuitive pour visualiser et rechercher dans des cartes PDF de technologies informatiques couvrant différents domaines :
- **Cybersécurité**
- **Base de données**
- **Développement IA**
- **Développement Backend**
- **Développement Frontend**
- **Développement Mobile**
- **DevOps**
- **Embarqué**
- **Gestion de projet**
- **Réseau**
- **Outils de développement**

## 🚀 Comment lancer le site

### Prérequis
- Un navigateur web moderne (Chrome, Firefox, Safari, Edge)
- Un serveur local pour servir les fichiers (nécessaire pour le fonctionnement de PDF.js)

### Méthode 1 : Avec Python (Recommandé)

Si vous avez Python installé sur votre machine :

**Python 3.x :**
```bash
# Depuis le répertoire racine du projet
python -m http.server 8000
```

**Python 2.x :**
```bash
# Depuis le répertoire racine du projet
python -m SimpleHTTPServer 8000
```

Ensuite, ouvrez votre navigateur et accédez à :
```
http://localhost:8000/src/index.html
```

### Méthode 2 : Avec Node.js

Si vous avez Node.js installé :

```bash
# Installer http-server globalement (une seule fois)
npm install -g http-server

# Lancer le serveur depuis le répertoire racine
http-server -p 8000
```

Accédez ensuite à :
```
http://localhost:8000/src/index.html
```

### Méthode 3 : Avec l'extension Live Server (VS Code)

1. Installer l'extension "Live Server" dans VS Code
2. Faire un clic droit sur `src/index.html`
3. Sélectionner "Open with Live Server"

## 📖 Comment utiliser le site

### Navigation dans les cartes

#### Sélection de la carte
- Utilisez le **menu déroulant** en haut à gauche pour choisir la carte à afficher
- Les cartes disponibles couvrent différents domaines technologiques

#### Zoom et navigation
- **Boutons + / - :** Zoomer et dézoomer sur la carte
- **Molette de la souris + Ctrl/Cmd :** Zoom fluide
- **Clic et glisser :** Déplacer la carte pour explorer différentes zones
- **Scroll :** Navigation verticale et horizontale

### Recherche de technologies

#### Effectuer une recherche
1. Entrez un mot-clé dans le **champ de recherche** (ex: "Python", "Docker", "React")
2. Cliquez sur le bouton **"Rechercher"** ou appuyez sur **Entrée**
3. Le nombre de résultats s'affiche au centre de la barre de recherche

#### Navigation dans les résultats
- **Boutons ← / →** : Naviguer entre les différentes occurrences trouvées
- **Flèches du clavier** : Même fonctionnalité (←/→)
- L'élément actuel est surligné en **bleu clair**
- Les autres occurrences sont surlignées en **jaune**
- La carte zoome et se centre automatiquement sur chaque résultat

### Raccourcis clavier

| Touche | Action |
|--------|--------|
| `Entrée` | Lancer la recherche |
| `→` | Résultat suivant |
| `←` | Résultat précédent |
| `Ctrl/Cmd + Molette` | Zoom |

## 🗂️ Structure du projet

```
Externatic/
├── src/
│   ├── index.html      # Page principale
│   └── styles.css      # Styles de l'application
├── assets/
│   ├── entire-map.pdf  # Carte complète
│   ├── cyber-map.pdf   # Carte cybersécurité
│   ├── db-map.pdf      # Carte base de données
│   └── ...             # Autres cartes thématiques
└── README.md           # Ce fichier
```

## 🛠️ Technologies utilisées

- **HTML5** : Structure de l'application
- **CSS3** : Styles et mise en page responsive
- **JavaScript (ES6+)** : Logique applicative
- **PDF.js** : Rendu et manipulation des fichiers PDF

## ⚠️ Note importante

Le site doit être servi via un serveur HTTP local. L'ouverture directe du fichier HTML dans le navigateur (protocole `file://`) ne fonctionnera pas correctement en raison des restrictions de sécurité CORS nécessaires pour charger les fichiers PDF.

## 📱 Compatibilité

- ✅ Chrome / Chromium
- ✅ Firefox
- ✅ Safari
- ✅ Edge
- ✅ Responsive (Mobile, Tablette, Desktop)

## 🎯 Fonctionnalités principales

- ✨ Affichage interactif de cartes PDF
- 🔍 Recherche textuelle avec surlignage
- 🔎 Zoom et navigation fluides
- 📱 Interface responsive
- ⌨️ Support des raccourcis clavier
- 🎨 Design moderne et intuitif

---

**Développé pour faciliter l'exploration des technologies informatiques**