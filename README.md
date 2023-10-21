---

# Projet de Détection du Diabète avec Support Vector Machine (SVM)

## Presentation du diabete
[Une presentation du diabete](le_diabete.md)

## Aperçu

Ce projet a pour objectif de développer un modèle de détection du diabète à partir d'un jeu de données en utilisant un algorithme de Support Vector Machine (SVM). Les SVM sont des modèles d'apprentissage automatique efficaces pour la classification binaire.

## Dataset

Le jeu de données utilisé pour ce projet contient des informations sur des patients, notamment des mesures médicales et des données démographiques. Il est constitué de deux classes : "Diabète" (1) et "Pas de diabète" (0). Vous pouvez trouver le jeu de données dans le fichier `diabetes_dataset.csv`.

## Prérequis

Avant de commencer, assurez-vous d'avoir installé les bibliothèques Python nécessaires en utilisant la commande suivante :

```bash
pip install pandas scikit-learn jupyter
```

## Structure du Projet

Le projet est organisé de la manière suivante :

```
diabetes_detection_project/
    ├── diabetes_detection.ipynb
    ├── diabetes_dataset.csv
    ├── le_diabete.md
    └── README.md
```

- `diabetes_detection.ipynb` : Le notebook Jupyter principal contenant le code pour la préparation des données, l'entraînement du modèle SVM, et l'évaluation de la performance du modèle.
- `diabetes_dataset.csv` : Le jeu de données au format CSV.
- `le_diabete.md` : une description de ce qu'est le diabete en tant que maladie
- `README.md` (ce fichier) : La documentation du projet.

## Utilisation

1. Clonez ce dépôt sur votre ordinateur :

   ```bash
   git clone https://github.com/noungajo/diabetes_detection_project.git
   cd diabetes_detection_project
   ```

2. Exécutez le notebook Jupyter `diabetes_detection.ipynb` pour travailler sur le projet. Vous pouvez utiliser Jupyter Notebook ou JupyterLab pour cela.

3. Suivez les étapes dans le notebook pour charger les données, préparer les caractéristiques, entraîner le modèle SVM, et évaluer ses performances.

4. Une fois le modèle formé, vous pouvez l'utiliser pour prédire si un patient est diabétique ou non en fonction des caractéristiques médicales fournies.

## Contribution

Les contributions à ce projet sont les bienvenues. Si vous souhaitez contribuer, veuillez ouvrir une "issue" pour discuter de votre proposition ou soumettre une "pull request" pour ajouter des fonctionnalités ou résoudre des problèmes.

## Licence

Ce projet est sous licence MIT. Vous êtes libre de l'utiliser et de le modifier comme bon vous semble.

---

