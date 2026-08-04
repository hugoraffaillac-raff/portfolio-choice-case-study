# Guide — Pusher le projet sur GitHub

## 0. Prérequis
- Avoir un compte GitHub et Git installé (`git --version` pour vérifier).
- Placer tous les fichiers dans un même dossier : le notebook, le .docx,
  `README.md`, `.gitignore`, `requirements.txt`, `LICENSE`.

## 1. Créer le dépôt sur GitHub
Sur github.com → bouton **New repository** :
- Name : `portfolio-choice-case-study`
- Visibilité : Public ou Private
- **Ne cochez PAS** "Add a README" / .gitignore / license (vous les avez déjà).
- Cliquez sur **Create repository**.

## 2. Initialiser le dépôt local et pousser
Dans un terminal, depuis le dossier du projet :

```bash
git init
git add .
git commit -m "Initial commit : case study choix de portefeuille"
git branch -M main
git remote add origin https://github.com/<votre-utilisateur>/portfolio-choice-case-study.git
git push -u origin main
```

Remplacez `<votre-utilisateur>` par votre identifiant GitHub.

## 3. Authentification
Au `git push`, GitHub demande vos identifiants. Le mot de passe classique
n'est plus accepté : utilisez un **Personal Access Token**.
- GitHub → Settings → Developer settings → Personal access tokens →
  Tokens (classic) → Generate new token → cochez `repo` → générez.
- Collez ce token quand le terminal demande le mot de passe.

(Alternative : configurer une clé SSH et utiliser l'URL
`git@github.com:<votre-utilisateur>/portfolio-choice-case-study.git`.)

## 4. Mettre à jour plus tard
Après toute modification :

```bash
git add .
git commit -m "Description de la modification"
git push
```

## Astuce — notebook propre
Pour éviter de versionner les sorties volumineuses (graphiques encodés) du
notebook, vous pouvez le nettoyer avant de committer :

```bash
jupyter nbconvert --clear-output --inplace "Portfolio_Choice_-_Case_study_.ipynb"
```
