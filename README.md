# Traj-FM — Les ondes de Trajworld

Mini-site statique communautaire de radio, vidéo et serveur Minecraft. Réalisé en HTML, CSS et JavaScript natifs, sans framework ni ressource Mojang. Les paysages, vignettes, logo et sons sont des créations originales incluses.

## Lancer le site

Dans un terminal, placez-vous dans le dossier `traj-fm/`, puis lancez un serveur local :

```bash
python -m http.server 8000
```

Ouvrez ensuite `http://localhost:8000`. Le site dispose aussi de données de secours intégrées au JavaScript, pour rester utilisable si on ouvre `index.html` directement (`file://`). Toutefois, les fichiers JSON ne peuvent alors pas être chargés par `fetch` et certaines fonctions comme l’API de statut du serveur ne seront pas disponibles. Préférez le serveur local.

## Personnalisation

- **Radio et serveur** : modifiez `data/config.json`. Remplacez les champs `[À COMPLÉTER]` (slogan, fréquence, Discord, TikTok, IP et pseudos des animateurs), l’accent, les conseils et les splashs. Une fréquence d’exemple `104.7 FM` est fournie. Une IP non renseignée désactive proprement la vérification de statut. Quand une adresse est présente, le site interroge `api.mcsrvstat.us`.
- **Morceaux** : `data/playlist.json` contient les titres, artistes et chemins. Placez vos pistes dans `assets/audio/` et actualisez les chemins. Les quatre boucles chiptune originales sont incluses et jouables localement.
- **Vidéos** : éditez `data/videos.json`. Remplacez les IDs `placeholder-*` par les identifiants numériques des vidéos TikTok et les chemins de vignettes. Les entrées de démonstration sont explicitement marquées.
- **Visuels et styles** : les illustrations se trouvent dans `assets/img/`; les règles graphiques sont dans `css/style.css`. La police Press Start 2P / VT323 est chargée depuis Google Fonts, avec une police monospace de secours si le réseau est absent.
- Les noms de pseudos des hôtes alimentent les rendus de skin `mc-heads.net`. Une illustration locale apparaît si le service ne répond pas.

## Déploiement (au plus 5 étapes)

1. Personnalisez `data/config.json`, `data/playlist.json` et `data/videos.json`.
2. Vérifiez localement avec `python -m http.server 8000`.
3. **GitHub Pages** : poussez le dossier `traj-fm/` sur une branche, puis sélectionnez le dossier publié dans *Settings → Pages*.
4. **Netlify** : déposez le dossier `traj-fm/` dans le déploiement manuel, ou reliez le dépôt en gardant ce dossier comme répertoire publié.
5. **Vercel** : importez le dépôt, définissez `traj-fm` comme répertoire racine (sans étape de build) et déployez.

Tous les chemins sont relatifs, sans étape de compilation. Les navigateurs doivent permettre les requêtes réseau vers les services tiers pour afficher les vidéos intégrées, les rendus de skins et le statut en direct. Les sons d’interface sont désactivés par défaut; le lecteur radio ne démarre qu’après action de l’utilisateur.
