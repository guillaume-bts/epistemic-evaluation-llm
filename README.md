# epistemic-evaluation-llm

Étude exploratoire sur l'auto-évaluation de la vérifiabilité, de la plausibilité et de la croyance par un LLM local (DeepSeek-R1-Distill-Qwen-1.5B) face à des énoncés politiques du corpus LIAR2.

# Le poids de la vérifiabilité dans le jugement des LLMs

## Description du projet
Cette étude épistémique exploratoire évalue comment un modèle de langage (LLM) auto-évalue la vérifiabilité, la plausibilité et la croyance face à des énoncés politiques. L'expérience vise à déterminer si un LLM intègre des dimensions logiques pour évaluer la vérité ou s'il se laisse piéger par la cohérence sémantique des énoncés. 

## Stack Technique et Méthodologie
* **Modèle utilisé :** `deepseek-ai/DeepSeek-R1-Distill-Qwen-1.5B`.
* **Données :** 260 affirmations sous-échantillonnées à partir du jeu de test LIAR2, avec binarisation de la vérité terrain.
* **Environnement d'exécution :** Inférence locale optimisée pour Apple Silicon (MPS) en précision float16.
* **Bibliothèques principales :** Python, PyTorch, Hugging Face (Transformers, Datasets), Statsmodels, Pandas, SciPy.

## Principaux Résultats
* **Repli sur la neutralité :** Le modèle exprime une forte incertitude, donnant une note neutre de 4/7 dans 56% des cas pour la vérifiabilité et 42% pour la croyance.
* **Faible capacité de discrimination :** Le modèle distingue à peine le vrai du faux factuel, avec une Aire Sous la Courbe (AUC) de 0.57.
* **Effet de la plausibilité :** L'association entre vérifiabilité et croyance chute fortement (le coefficient passe de 0,43 à 0,17) dès que la plausibilité est ajoutée dans le modèle logit ordinal.

## Installation et Exécution
1. Clonez ce dépôt sur votre machine locale.
2. Installez les dépendances requises via la commande suivante : 
   `pip install transformers accelerate datasets statsmodels scipy pandas numpy`
3. Ouvrez le carnet interactif `.ipynb` (via Jupyter Lab, VS Code, etc.).
4. Exécutez les cellules séquentiellement. Le budget de temps d'inférence de la collecte est configuré à environ 60 minutes.

## Rapport détaillé
L'analyse statistique complète, le détail du pipeline d'extraction JSON, ainsi que la discussion sur les limites méthodologiques (notamment via les items de contrôle triviaux) sont disponibles dans le rapport PDF joint à ce dépôt : `Le_poids_de_la_vérifiabilité_dans_le_jugement_des_LLMs___Une_étude_épistémique_sur_l_évaluation_de_l_information.pdf`.
