# Groupe Génération Ndiemane – Cotisations (Firebase + GitHub Pages)

Fichiers : `index.html` (l'application), `firestore.rules` (règles de sécurité), ce `README.md`.

## 1. Firebase (console.firebase.google.com)
1. **Créer un projet** (ex. `generation-ndiemane`).
2. **Authentication** > Commencer > **E-mail/Mot de passe** > Activer.
3. Onglet **Utilisateurs** > Ajouter :
   - `admin@generation-ndiemane.com` + mot de passe fort (Administrateur)
   - `tresorier@generation-ndiemane.com` + mot de passe fort (Trésorier)
   (Ces e-mails n'ont pas besoin d'exister vraiment. Si vous en changez, modifiez-les aussi dans `index.html` et `firestore.rules`.)
4. **Firestore Database** > Créer une base > mode **production** > région proche (ex. `eur3`).
5. Onglet **Règles** > coller le contenu de `firestore.rules` > **Publier**.
6. **Paramètres du projet** (roue dentée) > **Vos applications** > icône Web `</>` > enregistrer l'app > copier l'objet `firebaseConfig`.
7. Ouvrir `index.html`, remplacer les valeurs de `const FB={...}` (début du script) par celles copiées.

## 2. GitHub Pages
1. Créer un compte/dépôt sur github.com (ex. `cotisations-ndiemane`), public.
2. **Add file > Upload files** : envoyer `index.html` > Commit.
3. **Settings > Pages** > Source : *Deploy from a branch* > branche `main`, dossier `/ (root)` > Save.
4. Le lien sera `https://VOTRE-NOM.github.io/cotisations-ndiemane/` (1 à 2 minutes).
5. Retour sur Firebase : **Authentication > Paramètres > Domaines autorisés** > ajouter `VOTRE-NOM.github.io`.

## 3. Premier lancement
Ouvrez le lien, connectez-vous en **Administrateur** : les 26 membres et les paramètres (cotisation 1 000 F, carte 1 000 F) sont créés automatiquement dans Firestore. Ensuite, tous les appareils sont synchronisés en temps réel.

## Droits
- **Administrateur** : tout (membres, suppressions, réglages).
- **Trésorier** : encaisser cotisations et cartes, ajouter dépenses/recettes, exporter les récaps.
Les droits sont appliqués par Firestore (`firestore.rules`), pas seulement par l'interface.

## Sécurité
Ne publiez jamais les mots de passe. La clé `apiKey` Firebase n'est pas secrète : la protection vient des règles Firestore.
