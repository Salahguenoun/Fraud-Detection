# Détection de Fraude en E-commerce 🛒

## Objectif

L’objectif est de construire un modèle permettant de prédire si une transaction e-commerce est frauduleuse, à partir de données simulées mais représentatives de comportements réels.

## Données

Les données sont stockées dans une base Snowflake (table `transactions`), et ont été analysées avec des requêtes SQL exécutées directement depuis l’interface de Snowflake.  
Elles comprennent des informations sur les transactions : montant, heure, méthode de paiement, ancienneté du compte, etc.

## Étapes du projet

1. **Exploration via SQL**  
   - Analyse de la fréquence des fraudes par méthode de paiement, catégorie de produit, heure de transaction, etc.
   - Visualisation des taux de fraudes par dimensions clés.

2. **Préparation des données**
   - Nettoyage, encodage des variables catégorielles, normalisation.
   - Séparation en `train` / `test`.

3. **Traitement du déséquilibre**
   - Utilisation de **SMOTE** et **ADASYN** pour équilibrer la classe minoritaire (fraude).
   - Comparaison avec la pondération via `scale_pos_weight`.

4. **Modélisation**
   - Modèles testés : `Random Forest`, `XGBoost`, et un **modèle hybride** combinant les deux.
   - Optimisation des hyperparamètres (manuelle).
   - Ajustement du `threshold` basé sur le `F1-score` pour améliorer la détection de fraude sans trop de faux positifs.

5. **Évaluation**
   - Utilisation des métriques : `accuracy`, `recall`, `precision`, `f1-score`, `matrice de confusion`.
   - Un tableau synthétique compare les résultats de tous les modèles testés.

## Résultat final

Le meilleur modèle est un **ensemble pondéré XGBoost + Random Forest** avec :
- Pondération XGBoost = 87%, RF = 13%
- Threshold = 0.49
- F1-score = 0.29  
Ce modèle atteint un `recall` de 35% sur la classe fraude, tout en conservant une précision globale élevée.

## Remarques

- Les cellules de connexion à Snowflake ont été volontairement masquées pour préserver les identifiants.
- Le notebook est consultable sans exécution.

---

_Projet réalisé par Salah Guenoun._
