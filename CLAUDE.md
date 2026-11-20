# InvestHalal

Projet de CV de Salahdin (L2 informatique, vise une alternance en M1). Il débute : parle-lui en français simple.
Charge la skill `coder-comme-un-senior` avant de coder.

- **Au début de chaque session, lis `docs/plan.md`** (où on en est, prochaine étape). Mets-le à jour à la fin de chaque étape.
- Deux parties : (1) analyseur d'actions halal (ratios AAOIFI, données SEC EDGAR + yfinance) ; (2) simulation de stratégies d'investissement **en argent fictif uniquement**, jamais d'argent réel ni de conseil personnalisé.
- Moteur en Python, **sans appel à un modèle d'IA** (sauf éventuel résumé d'actualité avec Haiku).
- Les nombres réglables (seuils AAOIFI, frais, flat tax 31,4 %, montants) vont dans `config.py`, pas en dur.
- Dépôt GitHub **public** : jamais de clé, de jeton ou de donnée perso dans le code.
- Travaille en petites étapes : son quota Claude est serré.
