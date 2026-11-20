# Plan — InvestHalal

## Où on en est
- Dossier, git et dépôt GitHub **public** créés : https://github.com/dindinou/InvestHalal
- Choix faits : moteur **Python**, données **SEC EDGAR + yfinance**, tableau de bord **Streamlit**.
- En attente du « go » de Salahdin sur la version 1 ci-dessous.

## Prochaine étape : version 1 (la plus simple)

**Partie 1 — Analyseur halal** (`invest_halal/screener.py`)
- ~20 grandes actions américaines (Apple, Microsoft, Nvidia…) listées dans `config.py`.
- Bilans : API gratuite SEC EDGAR « companyfacts » (dette, trésorerie, placements, revenus d'intérêts, chiffre d'affaires). Capitalisation : yfinance.
- 4 tests AAOIFI : dette à intérêt < 30 % de la capitalisation ; trésorerie + placements à intérêt < 30 % ; revenus d'intérêts < 5 % du chiffre d'affaires (approximation des revenus non conformes) ; secteur non interdit (banque, assurance, alcool, tabac, jeux, armement…).
- Résultat : un tableau « conforme / non conforme » avec les ratios.

**Partie 2 — Simulation en argent fictif** (`invest_halal/backtest.py`)
- ETF iShares MSCI World Islamic (IE00B27YCN58, cours yfinance converti en euros), depuis 2015.
- Stratégie A : 70 €/mois chaque mois.
- Stratégie B : « acheter au bon moment » = on garde l'argent tant que le cours est au-dessus de sa moyenne sur 200 jours, on achète tout quand il passe dessous.
- Résultat : capital final, gain, **après frais** (réglables) et **après flat tax 31,4 %**, avec une courbe.
- Les copies de dépôts 13F viendront en V2.

**Tableau de bord** (`app.py`, Streamlit) : un onglet par partie.

**Tests** (`pytest`) : calculs de ratios et de simulation sur de petites données inventées, sans internet.

**Note** : la SEC demande une adresse de contact dans les requêtes. Elle ira dans un fichier `.env` local, jamais envoyé sur GitHub.

## Plus tard (V2 et fin du projet)
- Stratégie C : copier les dépôts 13F de grands investisseurs (filtrés halal).
- Résumé d'actualité optionnel avec Haiku 5.5 (~0,10 $/mois).
- README pour recruteur : captures, résultats chiffrés, lien de démo (Streamlit Community Cloud, gratuit).

## Décisions prises
- Argent **fictif uniquement**, aucun ordre réel, aucun conseil personnalisé.
- Pas d'appel IA dans le moteur de calcul.
- Nombres réglables (seuils, frais, taxe, montant mensuel) dans `config.py`.
- Dépôt public : aucune clé ni donnée perso dans le code.
