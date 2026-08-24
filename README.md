# JUDE FILMS — site statique

Architecture : 1 page (`index.html`) + fenêtres JS (pas de pages projet séparées).
HTML + CSS + JS vanilla, aucun build, compatible GitHub Pages gratuit.

## Fichiers à déposer avant mise en ligne

### `assets/videos/` (snippets preview, légers — pas les films complets)
```
Cannibale - Furies-preview.mp4
Bain Rouge - JUDE-preview.mp4
Kill You Till You Die - Chey’N’Shiners-preview.mp4
I AM - JUDE-preview.mp4
Last Night Was a Better Night - Chey’N’Shiners-preview.mp4
Hexed - Hunters-preview.mp4
Resurrection - Black Rain-preview.mp4
Unleash the Fury - Black Rain-preview.mp4
Showreel 2026.mp4
```
Recommandation non vérifiée par test réel sur ce repo, à valider empiriquement :
3–6 s, 720p, H.264, sans audio, viser <10 Mo/fichier.

### `assets/images/`
```
Photodeprofil-sitevideo.jpg
```
⚠️ Extension supposée `.jpg` — si ton fichier est en `.png` ou `.webp`,
remplace l'extension dans `index.html` (recherche `Photodeprofil-sitevideo`).

## À compléter manuellement dans `js/main.js`

Chaque objet du tableau `PROJECTS` contient des champs `"À COMPLÉTER"` :
- `ytUrl` : URL YouTube complète du film (`https://www.youtube.com/watch?v=...` ou `https://youtu.be/...`).
  Tant que ce champ vaut `"#"`, la fenêtre détail retombe sur la lecture du
  snippet local au lieu d'un embed YouTube.
- `role`, `year`, `tools` : specs affichées dans la fenêtre détail du projet.

Dans `index.html`, le lien YouTube du header (`.social`) pointe vers
`https://www.youtube.com/@judefilmsoff` — à remplacer par l'URL réelle de la chaîne
une fois le choix de username tranché.

## Déploiement GitHub Pages

1. Créer un repo (ex. `jude-films`), pousser tout ce dossier à la racine.
2. Repo → *Settings* → *Pages* → *Source* : `Deploy from a branch`, branche `main`, dossier `/root`.
3. Le fichier `assets/videos/*.mp4` doit passer par `git add` / `git push`
   en ligne de commande (ou GitHub Desktop) si un fichier dépasse la limite
   de l'upload web du navigateur (25 Mo) — la limite de `git push` classique
   est plus haute (100 Mo/fichier) mais reste à vérifier selon config du repo.
4. Domaine personnalisé `jude-films.com` : *Settings → Pages → Custom domain*,
   puis configurer les enregistrements DNS chez le registrar (CNAME vers
   `<ton-user>.github.io`, ou enregistrements A vers les IPs GitHub Pages).
   Non testé ici — suivre la doc GitHub Pages au moment de la config DNS.

## Ce qui n'est PAS dans ce repo par choix

Les films complets ne sont pas hébergés en local : ils restent sur YouTube,
et la fenêtre détail projet les affiche en `<iframe>` embed dès que `ytUrl`
est renseigné. Seuls les snippets preview + le showreel sont dans `assets/videos/`.
