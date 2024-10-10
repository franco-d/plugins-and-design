
---

# OTP Verification Page

Cette page de vérification utilise une interface simple permettant de saisir un code de validation (OTP) envoyé par email. L'application comprend une logique de gestion de la saisie utilisateur, y compris le collage de l'OTP et la navigation entre les champs. La mise en page est construite à l'aide de **Bootstrap 5** et le code JavaScript gère l'activation et la désactivation des champs.

## 🛠 Technologies Utilisées

- **HTML5** pour la structure de la page.
- **CSS3** pour le style personnalisé des champs de saisie.
- **Bootstrap 5** pour le layout et les composants de la page.
- **JavaScript Vanilla** pour la gestion dynamique des champs de saisie.

## 📜 Instructions

### Prérequis
Aucun prérequis particulier, il suffit d'avoir un navigateur web moderne et une connexion internet pour charger Bootstrap via le CDN.

### Structure du projet

```plaintext
project/
│
├── index.html           # Page principale du projet
├── README.md            # Documentation du projet
└── assets/              # Dossier contenant les fichiers CSS et JS supplémentaires, si nécessaire
```

### Explication des Composants

- **HTML** : La page contient une section principale avec une disposition centrale pour le formulaire de saisie de l'OTP. Le formulaire est entouré d'une carte (`card`) avec un titre et une description expliquant l'envoi de l'OTP par email.
  
- **CSS** : Les champs OTP sont stylisés pour ressembler à des boîtes uniformes, avec des bordures arrondies et une hauteur fixe, et sont espacés de manière égale.

- **JavaScript** : Le script gère plusieurs comportements clés :
  - **Gestion de la saisie utilisateur** : Le script écoute les événements de saisie (`keyup`) et de collage (`paste`) pour gérer le passage d'un champ à un autre.
  - **Activation/Désactivation des champs** : Chaque champ est initialement désactivé (sauf le premier). Lorsqu'un utilisateur tape un chiffre valide, le champ suivant s'active automatiquement.
  - **Gestion du bouton de vérification** : Le bouton de validation reste désactivé tant que tous les champs ne sont pas remplis correctement.

### 🔧 Comment Utiliser

1. **Ouvrir le fichier `index.html`** dans un navigateur.
2. **Saisir le code OTP** (de 6 chiffres) dans les champs fournis.
3. Le bouton "Verify" s'activera une fois que tous les champs sont remplis.
4. **Coller un OTP** dans le premier champ pour le remplir automatiquement.

### 🎯 Fonctionnalités Principales

1. **Navigation automatique** : Lorsqu'un chiffre est saisi dans un champ, le curseur se déplace automatiquement vers le champ suivant.
2. **Collage de l'OTP** : Coller un code de 6 chiffres dans le premier champ répartit automatiquement les chiffres dans les champs successifs.
3. **Gestion de la suppression** : La suppression d'un chiffre efface le contenu du champ actuel et déplace le curseur vers le champ précédent.

### 🗂️ Structure des champs

- **HTML Structure** :
  ```html
  <div class="otp-field mb-4">
    <input type="number" />
    <input type="number" disabled />
    <input type="number" disabled />
    <input type="number" disabled />
    <input type="number" disabled />
    <input type="number" disabled />
  </div>
  ```

- **JavaScript** :
  ```javascript
  const inputs = document.querySelectorAll(".otp-field > input");
  // Activation du premier champ
  window.addEventListener("load", () => inputs[0].focus());

  inputs[0].addEventListener("paste", function (event) {
    // Gestion du collage de l'OTP
  });

  inputs.forEach((input, index1) => {
    input.addEventListener("keyup", (e) => {
      // Gestion de la navigation automatique
    });
  });
  ```

### 📌 Notes Importantes

- Ce projet est conçu pour fonctionner sur les navigateurs modernes prenant en charge `event.clipboardData` et `window.clipboardData` pour la gestion des événements de collage.
- Si l'OTP est de longueur différente (par exemple, 4 chiffres), ajustez le nombre d'`<input>` dans la section HTML.