---

# Projet de Détection du Diabète avec Support Vector Machine (SVM)

## Presentation du diabete
[Une presentation du diabete](le_diabete.md)

## Aperçu

Ce projet a pour objectif de développer un modèle de détection du diabète à partir d'un jeu de données en utilisant un algorithme de Support Vector Machine (SVM). Les SVM sont des modèles d'apprentissage automatique efficaces pour la classification binaire.

## Dataset

Le jeu de données utilisé pour ce projet contient des informations sur des patients, notamment des mesures médicales et des données démographiques. Il est constitué de deux classes : "Diabète" (1) et "Pas de diabète" (0). Vous pouvez trouver le jeu de données dans le fichier `diabetes_dataset.csv`.
### Comprendre les caractéristiques du datatsets
Comprendre les caractéristiques d'un ensemble de données est une étape importante dans l'analyse de données. 

1. Pregnancies (Grossesses) : Il s'agit du nombre de grossesses que la personne a eues. Cela peut être un indicateur de l'histoire médicale de la patiente.

2. Glucose : C'est le taux de glucose (sucre) dans le sang, mesuré en milligrammes par décilitre (mg/dL). Il s'agit d'une mesure importante pour diagnostiquer le diabète et évaluer la glycémie.

3. BloodPressure (Pression artérielle) : C'est la pression sanguine de la personne, généralement mesurée en millimètres de mercure (mmHg). La pression artérielle est importante pour évaluer la santé cardiovasculaire.

4. SkinThickness (Épaisseur de la peau) : Il s'agit de l'épaisseur du pli cutané tricipital en millimètres. Cela peut être utilisé pour évaluer la composition corporelle.

5. Insulin (Insuline) : C'est la mesure de l'insuline sérique à jeun en microunités internationales par millilitre (uU/ml). L'insuline est une hormone produite par le pancréas et est essentielle pour réguler la glycémie.

6. BMI (Indice de masse corporelle) : C'est un indicateur du poids corporel d'une personne en fonction de sa taille. Il est calculé en divisant le poids en kilogrammes par le carré de la taille en mètres. Le BMI est utilisé pour évaluer si une personne est en surpoids ou obèse.

7. DiabetesPedigreeFunction (Fonction de généalogie du diabète) : C'est une mesure de la probabilité génétique du diabète chez les parents et les ancêtres d'une personne.

8. Age (Âge) : L'âge de la personne, généralement en années. L'âge peut être un facteur important dans le risque de diabète et de complications liées au diabète.

9. Outcome (Résultat) : C'est la variable cible, généralement binaire (0 ou 1), qui indique si la personne est atteinte de diabète (1) ou non (0). Il s'agit de la variable que l'on tente généralement de prédire à partir des autres caractéristiques.

## Techniques d'optimisation des SVM
### Choix du noyau approprié
Les SVM permettent d'utiliser différents types de noyaux, tels que linéaires, polynomiaux, RBF (Radial Basis Function), etc. Le choix du noyau dépend de la nature de vos données. Expérimentez avec différents noyaux pour voir lequel fonctionne le mieux pour votre ensemble de données.
Le choix du noyau approprié dans un modèle SVM est une étape cruciale pour obtenir de bonnes performances. Le noyau détermine comment les données sont transformées dans un espace à plus grande dimension où elles sont séparables de manière linéaire. Voici un aperçu des différents types de noyaux couramment utilisés et des considérations pour choisir le noyau approprié :

1. **Noyau linéaire** :
   - Utilisation : Le noyau linéaire est adapté lorsque les données sont linéairement séparables, c'est-à-dire que vous pouvez tracer une ligne droite pour séparer les classes.
   - Avantages : Il est simple, rapide à entraîner et fonctionne bien lorsque la relation entre les caractéristiques et les classes est linéaire.
   - Considérations : Si vos données ne sont pas linéairement séparables, l'utilisation d'un noyau linéaire peut entraîner une mauvaise performance.
```
from sklearn import datasets
from sklearn import svm

# Chargement d'un jeu de données (exemple : Iris dataset)
data = datasets.load_iris()
X = data.data
y = data.target

# Création du modèle SVM avec un noyau linéaire
model = svm.SVC(kernel='linear')

# Entraînement du modèle
model.fit(X, y)
```
2. **Noyau polynomial** :
   - Utilisation : Le noyau polynomial est utilisé lorsque les données sont modérément non linéaires. Vous pouvez ajuster le degré du polynôme (par exemple, 2 pour une parabole) pour contrôler la complexité de la séparation.
   - Avantages : Il est plus flexible que le noyau linéaire et peut modéliser des relations non linéaires.
   - Considérations : Le choix du degré du polynôme est crucial et peut conduire au surajustement si trop élevé.
```
# Création du modèle SVM avec un noyau polynomial de degré 3
model = svm.SVC(kernel='poly', degree=3)

# Entraînement du modèle
model.fit(X, y)

```

3. **Noyau RBF (Radial Basis Function)** :
   - Utilisation : Le noyau RBF est l'un des noyaux les plus polyvalents et est approprié pour des données non linéaires et complexes. Il est souvent utilisé par défaut.
   - Avantages : Il peut modéliser efficacement des relations complexes entre les caractéristiques et les classes.
   - Considérations : Le paramètre gamma doit être réglé avec soin, car il contrôle la forme de la frontière de décision.
```
# Création du modèle SVM avec un noyau RBF
model = svm.SVC(kernel='rbf')

# Entraînement du modèle
model.fit(X, y)

```

4. **Noyau sigmoïde** :
   - Utilisation : Le noyau sigmoïde est adapté lorsque les données ont une forme en S ou sont similaires à des fonctions sigmoïdes.
   - Avantages : Il peut être utilisé pour modéliser des fonctions non linéaires complexes.
   - Considérations : Comme le noyau sigmoïde peut être sensible aux valeurs atypiques, il est important de traiter les valeurs aberrantes correctement.
``# Création du modèle SVM avec un noyau sigmoïde
model = svm.SVC(kernel='sigmoid')

# Entraînement du modèle
model.fit(X, y)
```
Le choix du noyau dépend de la nature de vos données et de la forme de la relation entre les caractéristiques et les classes. Il est recommandé d'expérimenter avec différents noyaux et de les ajuster à l'aide de la validation croisée pour déterminer celui qui fonctionne le mieux pour votre ensemble de données. Une recherche en grille (Grid Search) avec une combinaison de paramètres de noyau et d'hyperparamètres (tels que C et gamma) peut vous aider à trouver la meilleure configuration.

En fin de compte, il n'y a pas de noyau universellement optimal, car il dépend de la spécificité de vos données. La compréhension de votre ensemble de données et de la nature du problème est essentielle pour faire un choix éclairé.
### Augmentation des données
L'augmentation des données (data augmentation) est une technique couramment utilisée pour améliorer les performances des modèles d'apprentissage automatique, y compris les SVM. Cette technique consiste à créer de nouveaux exemples d'entraînement en appliquant des transformations aux données d'origine. Dans le contexte d'un modèle SVM, cela peut aider à augmenter la diversité des exemples d'entraînement, ce qui peut améliorer la généralisation du modèle. Voici comment vous pouvez mettre en œuvre l'augmentation des données en Python à l'aide de la bibliothèque Scikit-Learn et la bibliothèque d'augmentation de données `Augmentor` :

1. Commencez par installer la bibliothèque `Augmentor` si vous ne l'avez pas déjà fait :

```bash
pip install Augmentor
```

2. Créez un script Python pour augmenter vos données. Voici un exemple :

```python
import Augmentor

# Chemin vers le répertoire contenant vos données d'origine
data_directory = "/chemin/vers/vos/donnees"

# Créez un objet Pipeline d'augmentation de données
p = Augmentor.Pipeline(data_directory)

# Ajoutez des opérations d'augmentation que vous souhaitez appliquer, par exemple, rotation, miroir, recadrage, etc.
p.rotate(probability=0.7, max_left_rotation=25, max_right_rotation=25)
p.flip_left_right(probability=0.5)
p.zoom_random(probability=0.5, percentage_area=0.8)
# Vous pouvez ajouter d'autres opérations selon vos besoins

# Définissez le nombre d'exemples augmentés que vous souhaitez générer
num_samples = 1000

# Générez les exemples augmentés
p.sample(num_samples)
```

3. Après avoir généré les exemples augmentés, vous pouvez les combiner avec vos données d'origine pour former un nouvel ensemble de données d'entraînement. Assurez-vous de maintenir l'équilibre entre les classes, en augmentant proportionnellement chaque classe.

4. Ensuite, vous pouvez utiliser cet ensemble de données augmenté pour entraîner votre modèle SVM, comme dans les exemples précédents.

L'augmentation des données peut être particulièrement utile lorsque vous avez un ensemble de données limité ou que les classes sont déséquilibrées. Cela permet d'augmenter la diversité des exemples et peut améliorer la capacité de généralisation du modèle. Assurez-vous de personnaliser les opérations d'augmentation en fonction de votre problème spécifique.
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

