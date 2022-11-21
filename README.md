# Most (24 h) recent research paper 

Ce projet consiste à developper un web app qui permet de consulter les denières articles publiés sur arxiV.

## Periodic scripts

1. `server/src/update_recent_papers.py` : télécharge les articles les plus récents, calcule leurs embeddings et enregistre le tout.
2. `server/src/update_all_papers.py` : utilise les données téléchargées par le script ci-dessus et met à jour les données historiques, contenant initialement chaque article de 2021.
3. `server/src/update_model.py` : utilise les données historiques (mises à jour par le script juste au-dessus) pour mettre à jour notre modèle de clustering.
4. `server/src/update_front_end_data.py` : met à jour les données à afficher sur le site Web. Ce prétraitement permet un petit temps de réponse du serveur.

Ces quatre scripts sont exécutés dans cet ordre, continuellement, grâce au script `server/update_all_data.sh`, combiné avec un service systemd.

## Exécuter le serveur

Vous devez avoir installé Flask avec Python.

Ensuite, allez dans le répertoire `server` et lancez le serveur avec la commande `python -m flask run` (ajoutez `--host 0.0.0.0` si vous voulez ouvrir le serveur au monde, via votre port 5000).