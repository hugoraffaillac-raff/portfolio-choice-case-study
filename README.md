# Portfolio Choice — Case Study

Étude de cas de **gestion de portefeuille** réalisée dans le cadre de mon Master. Le projet construit et backteste une
allocation d'actifs multi-actifs sur-mesure pour une investisseuse (Sofia
Andersen), à partir de la formalisation d'une *Investment Policy Statement*
(IPS) jusqu'à la simulation d'un *glide path* de désengagement du risque.

## Contexte

Sofia Andersen, 34 ans, résidente en Suisse, détient ~36 % de son patrimoine
concentré dans une position bloquée en actions AstraZeneca (large cap,
défensive, secteur santé). L'objectif de l'étude n'est pas de répliquer
passivement les indices mondiaux, mais de **concevoir une allocation qui
diversifie activement ce risque de concentration** et maximise la croissance
du capital sur un horizon de 33 ans, avec réduction progressive du risque à
l'approche de la retraite.

## Contenu de l'analyse

1. **Investment Policy Statement (IPS)** — profil, objectifs, contraintes
   (plancher de liquidité 5 %, plafond crypto 1,5 %, tilt factoriel
   anti-AstraZeneca, usage de rendements hebdomadaires pour neutraliser
   l'asynchronisme des bourses).
2. **Strategic Asset Allocation & sélection d'instruments** — 10 ETF / actifs
   sélectionnés sur coût (TER), liquidité et cohérence factorielle.
3. **Construction de trois portefeuilles** :
   - *Portfolio 1* — Benchmark 60/40 (VT / AGG).
   - *Portfolio 2* — Portefeuille US factoriel (Small Cap / Value / Momentum).
   - *Portfolio 3* — Portefeuille final diversifié 70/30 multi-actifs.
4. **Analyse descriptive par actif** — Sharpe, Sortino, CAGR, max drawdown,
   Calmar et matrice de corrélation (rendements hebdomadaires).
5. **Régression Fama-French 6 facteurs** sur le portefeuille US (validation des
   biais SMB, HML, Momentum ; R² ≈ 98 %).
6. **Backtest 2016–2026** avec rééquilibrage trimestriel et **glide path**
   (réduction de 1 %/an des actifs risqués jusqu'à une cible 60/40).
7. **Analyse de performance comparée** portefeuille vs benchmark
   (rendement annualisé, volatilité, Sharpe, Sortino, Calmar, drawdown,
   information ratio, alpha de Jensen).

## Univers d'investissement

| Ticker  | Classe / rôle                     |
| ------- | --------------------------------- |
| IJS     | US Small Cap                      |
| MTUM    | US Momentum                       |
| VIOV    | US Small Cap Value                |
| VEA     | Marchés développés ex-US          |
| IEMG    | Marchés émergents                 |
| GLD     | Or                                |
| VNQ     | Immobilier coté (REITs)           |
| BTC-USD | Crypto (plafonnée à 1,5 %)        |
| AGG     | Obligations Investment Grade US   |
| BIL     | Cash / T-Bills 1-3 mois           |
| VT      | Actions mondiales (benchmark)     |

## Stack technique

- **Python** — pandas, numpy, statsmodels
- **Données de marché** — [yfinance](https://github.com/ranaroussi/yfinance) (Yahoo Finance)
- **Facteurs** — [Kenneth French Data Library](https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html) (FF5 + Momentum)
- **Visualisation** — matplotlib, plotly, seaborn

## Installation

```bash
git clone https://github.com/<votre-utilisateur>/portfolio-choice-case-study.git
cd portfolio-choice-case-study
python -m venv .venv
source .venv/bin/activate      # sous Windows : .venv\Scripts\activate
pip install -r requirements.txt
```

## Utilisation

Ouvrir le notebook et exécuter les cellules dans l'ordre :

```bash
jupyter notebook "Portfolio_Choice_-_Case_study_.ipynb"
```

> Le notebook télécharge les données de marché en direct via `yfinance` et les
> facteurs Fama-French depuis le site de Kenneth French : une connexion
> internet est nécessaire à l'exécution. Les résultats peuvent varier
> légèrement selon la date d'exécution (données mises à jour).

## Structure du dépôt

```
.
├── Portfolio_Choice_-_Case_study_.ipynb   # Notebook d'analyse
├── Portfolio_Choice_-_Case_study_.docx    # Rapport rédigé
├── requirements.txt
├── .gitignore
├── LICENSE
└── README.md
```

## Auteurs

- **Baptiste Asaert** — portefeuille US factoriel, benchmark 60/40,
  régressions Fama-French, analyse comparative des performances.
- **Hugo Raffaillac** — portefeuille final diversifié, backtests, stratégie
  de glide path.

Code, rédaction et choix méthodologiques réalisés conjointement.

## Avertissement

Ce projet est un travail académique fourni à titre pédagogique uniquement.
Il ne constitue en aucun cas un conseil en investissement.
