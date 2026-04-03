# ⚽ n8n Premier League Standings & AI Analysis

Ce dépôt contient un workflow d'automatisation **n8n** professionnel conçu pour récupérer, traiter et analyser le classement de la Premier League anglaise en temps réel grâce à l'Intelligence Artificielle (Mistral AI).

## 🚀 À propos du projet

Ce workflow automatisé a pour objectif d'extraire les données du classement officiel via l'API [football-data.org](https://www.football-data.org/), de formater les statistiques, puis de générer automatiquement un bref résumé analytique des performances de chaque équipe grâce au LLM de **Mistral AI**.

### Fonctionnalités principales :
- ⏱️ **Exécution planifiée** : Mise à jour régulière et automatique du classement via un *Schedule Trigger*.
- 📥 **Ingestion de données** : Connexion à l'API de football pour extraire le classement JSON brut.
- ⚙️ **Traitement et formatage** : Structuration de données complexes avec les nœuds *Split Out* et *Set* (position, points, victoires, défaites, buts, etc.).
- 🤖 **Analyse IA** : Évaluation footballistique sur-mesure générée par Mistral AI (modèle `mistral-small-latest`) pour chaque club de la ligue.

## 📂 Structure du Répertoire

- `workflows/` : Contient les définitions JSON des workflows n8n (ex: `PL.json`), prêtes à être importées. *(Note : Pensez à y déplacer votre fichier PL.json !)*
- `.github/workflows/` : Pipelines CI/CD configurés pour automatiser le déploiement sur votre instance n8n.
- `docs/` : Documentation détaillée et architecture technique complète.

## 🛠️ Prérequis et Installation

Pour utiliser et déployer ce workflow sur votre propre instance n8n, vous aurez besoin de :
1. Une instance **n8n** en cours d'exécution.
2. Une clé API valide pour [football-data.org](https://www.football-data.org/).
3. Une clé API pour [Mistral AI](https://mistral.ai/).

### Comment importer le workflow :
1. Ouvrez votre interface web n8n.
2. Allez dans l'onglet **Workflows** et cliquez sur **Add workflow**.
3. Depuis le menu des options en haut à droite (trois points), sélectionnez **Import from File** et choisissez le fichier `PL.json`.
4. ⚠️ **Sécurité** : Pensez à créer et assigner des variables sécurisées (*Credentials*) dans n8n pour vos identifiants d'API, afin de remplacer les clés d'API insérées "en dur" dans les requêtes HTTP du workflow !

## 📖 Pour aller plus loin

Pour approfondir le fonctionnement, l'architecture et les recommandations de sécurisation du workflow, consultez la [Documentation technique](./docs/index.md).
