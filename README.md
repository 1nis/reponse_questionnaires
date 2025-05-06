# Automa – Remplissage automatique de questionnaire

Ce workflow **Automa** (Chrome) permet de :

1. **Cocher** la case “Aucun” pour la question 23 (cases à cocher).  
2. **Cocher** “J’en ai parlé à l’enseignant(e)” pour la question 25.  
3. **Remplir** la question 27 avec un nombre aléatoire entre 1 et 5.  
4. **Sélectionner** pour certaines questions (6,7,8,13–20,22,26,28,29) uniquement parmi un ensemble de réponses autorisées.  
5. **Choisir** aléatoirement pour toutes les autres questions à boutons radio.

---

## 📋 Prérequis

- Chrome (ou Chromium)  
- Extension **Automa** (v1.29.9 ou supérieure)  

---

## 🚀 Installation

1. **Importer le workflow**  
   - Dans Automa → **Workflows** → **Importer**  
   - Coller le JSON exporté (ou copier le contenu du fichier `.automa.json`)  

2. **Configurer**  
   - Si vous souhaitez ouvrir automatiquement la page du questionnaire, insérez un bloc **“Nouvel onglet”** (Actions → Page → Nouvel onglet) avant le **Run JavaScript**, avec l’URL de votre formulaire.
   - Vérifiez que le bouton **“Soumettre”** est bien ciblé si vous ajoutez un bloc **Click element** à la fin.

---

## 📖 Usage

1. Ouvrez la page du questionnaire (ou laissez le workflow l’ouvrir).  
2. Lancez le workflow manuellement.  
3. Toutes les réponses seront automatiquement cochées/remplies selon les règles définies.  
4. (Optionnel) Le workflow peut cliquer automatiquement sur “Soumettre”.

---

## ⚙️ Détail du script

- **Q23** : on repère le container via `<span class="itemnr">23.</span>` et on coche la case “Aucun”.  
- **Q25** : on repère le container via `<span class="itemnr">25.</span>` et on coche “J’en ai parlé à l’enseignant(e)”.  
- **Q27** : on repère dynamiquement l’`<input>` lié à `<span class="itemnr">27.</span>` et on injecte `Math.floor(Math.random()*5)+1`.  
- **Questions restreintes (radios)** : pour les questions 6,7,8,13–20,22,26,28,29, on ne choisit que parmi un tableau de libellés autorisés.  
- **Autres questions (radios)** : choix aléatoire parmi toutes les options visibles.

---

## 🔧 Personnalisation

- **Modifier la liste des questions restreintes** : éditer l’objet `allowed` dans le code JS.  
- **Changer la plage de Q27** : ajuster `Math.floor(Math.random()*5)+1` pour passer sur une autre fourchette.  
- **Ajouter/supprimer** des règles spéciales : insérer d’autres blocs IIFE similaires à ceux de Q23/Q25.

---

## 🛠️ Dépannage

- **Q23/Q25 non cochées** : vérifier que `data-groupname` et `.itemnr` sont présents dans le DOM.  
- **Q27 non rempli** : ouvrir la console (Ctrl+Shift+J) pour voir les erreurs `Label Q27 introuvable` ou `Input Q27 introuvable`.  
- **Sélecteurs CSS** : adapter si votre formulaire utilise d’autres classes ou structures.

---

> **Note** : ce workflow ne gère que les boutons radio et cases à cocher/textes spécifiés. Les autres champs (textes libres, menus déroulants, etc.) sont ignorés.

---

*Créé automatiquement avec Automa + JavaScript.*  
