# 🧠 Fashion Item Recognition Prototype (DNN)

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.0+-orange.svg)

## 📘 Description

Prototype de réseau de neurones profond (DNN) pour la reconnaissance automatique d'articles vestimentaires (T-shirt, pantalon, chaussures, etc.). Ce projet valide la faisabilité technique d'un système de classification d'images avant l'investissement dans des architectures plus complexes (CNN).

## 🎯 Objectifs

- **Valider leS étapes complet** : Données → Modèle → Métriques
- **Atteindre ≥ 80% d'accuracy** sur les données de test
- 
## 🧩 Contexte Business

L'entreprise e-commerce souhaite automatiser la classification d'articles de mode mais ne dispose d'aucun modèle interne. Ce prototype permettra de :

- ✅ Estimer la qualité des prédictions
- ✅ Prouver la faisabilité technique
- ✅ Décider d'un investissement dans des modèles avancés
## 📊 Dataset

**Fashion MNIST** - 70 000 images en niveaux de gris (28x28 pixels)

| Classe | Label | Article |
|--------|-------|---------|
| 0 | T-shirt/top |
| 1 | Pantalon |
| 2 | Pull |
| 3 | Robe |
| 4 | Manteau |
| 5 | Sandale |
| 6 | Chemise |
| 7 | Basket |
| 8 | Sac |
| 9 | Bottine |

- **Training set** : 60 000 images
- **Test set** : 10 000 images

## 🚀 Installation

### Prérequis

- Python 3.8+
- Google Colab (recommandé)

### Setup local

```bash
# Cloner le projet
git clone https://github.com/<username>/fashion-recognition-dnn.git
cd fashion-recognition-dnn

# Créer un environnement virtuel
python -m venv venv
source venv/bin/activate  # Linux/Mac
# ou
venv\Scripts\activate     # Windows

# Installer les dépendances
pip install python tensorflow 
```

### Lancer sur Google Colab

1. Ouvrir le notebook `fashion_recognition.ipynb`
2. Menu : **Fichier → Ouvrir dans Colab**
3. Exécuter toutes les cellules

## 💻 Utilisation

### Entraînement rapide

```python
from tensorflow.keras.datasets import fashion_mnist
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Flatten, Dense

# Charger les données
(train_images, train_labels), (test_images, test_labels) = fashion_mnist.load_data()

# Normaliser
train_images = train_images / 255.0
test_images = test_images / 255.0

# Créer le modèle
model = Sequential([
    Flatten(input_shape=(28, 28)),
    Dense(128, activation='relu'),
    Dense(64, activation='relu'),
    Dense(10, activation='softmax')
])

# Compiler
model.compile(
    optimizer='adam',
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy']
)

# Entraîner
history = model.fit(
    train_images, train_labels,
    epochs=10,
    validation_split=0.1
)

# Évaluer
test_loss, test_acc = model.evaluate(test_images, test_labels)
print(f"Test accuracy: {test_acc:.2%}")
```

## 🧠 Méthodologie

### 1️⃣ Préparation des données

- **Chargement** : Fashion MNIST via `tensorflow.keras.datasets`
- **Normalisation** : Division par 255 → valeurs entre [0,1]
- **Labels** : Conserver les entiers (0–9) pour `sparse_categorical_crossentropy`

### 2️⃣ Architecture du modèle

```
Input (28x28) → Flatten() → Dense(128, relu) → Dense(64, relu) → Dense(10, softmax)
```

**Compilation** :
- Optimizer : `adam`
- Loss : `sparse_categorical_crossentropy`
- Metrics : `accuracy`

**Bonus** : `EarlyStopping` sur `val_loss` avec `restore_best_weights=True`

### 3️⃣ Entraînement

- **Époques** : 5–10
- **Validation split** : 10%
- **Visualisation** : Courbes d'accuracy et loss (train/val)

### 4️⃣ Évaluation

- Performance sur le jeu de test avec `model.evaluate()`
- **Objectif** : ≥ 80% d'accuracy
- Matrice de confusion pour analyser les erreurs

## 📈 Résultats

| Métrique | Valeur |
|----------|--------|
| **Test Accuracy** | [À compléter] % |
| **Test Loss** | [À compléter] |
| **Époques entraînées** | [À compléter] |
| **Temps d'entraînement** | [À compléter] min |

### Matrice de confusion

[Insérer l'image de la matrice de confusion]

### Courbes d'entraînement

[Insérer les graphiques accuracy/loss]

## 🔍 Choix techniques

### Loss Function

| Loss | Usage | Avantages |
|------|-------|-----------|
| `sparse_categorical_crossentropy` | Labels entiers (0–9) | ✅ Utilisé ici - Pas besoin d'encoder |
| `categorical_crossentropy` | Labels one-hot encodés | Nécessite preprocessing supplémentaire |

### Hyperparamètres testés

- **Neurones couche 1** : [64, 128, 256]
- **Neurones couche 2** : [32, 64, 128]
- **Activation** : [relu, tanh]
- **Optimizer** : [adam, sgd]
- **Batch size** : [32, 64, 128]

## 🔄 Benchmark IA (Bonus)

### Comparaison avec Hugging Face Image Classification API

| Critère | DNN Custom | Hugging Face API |
|---------|------------|------------------|
| **Performance** | [À compléter] % | ~90%+ (modèles pré-entraînés) |
| **Temps d'inférence** | [À compléter] ms | ~200ms (API) |
| **Coût** | Gratuit (compute local) | Freemium → Payant à grande échelle |
| **Contrôle** | Total | Limité |
| **Personnalisation** | Totale | Difficile |
| **Dépendance** | Aucune | Cloud/Internet requis |

**Conclusion** : Le DNN custom offre plus de contrôle et aucun coût récurrent, mais les services cloud comme Hugging Face proposent des performances supérieures grâce aux modèles pré-entraînés.

## 🛠️ Technologies

- **TensorFlow / Keras** : Deep Learning framework
- **NumPy** : Manipulation de données
- **Pandas** : Analyse de données
- **Matplotlib, Seaborn** : Visualisation
- **Scikit-learn** : Matrice de confusion, métriques

## 📂 Structure du projet

```
fashion-recognition-dnn/
│
├── notebooks/
│   └── fashion_recognition.ipynb    # Notebook principal
│
├── src/
│   ├── data_loader.py               # Chargement des données
│   ├── model.py                     # Architecture du modèle
│   └── utils.py                     # Fonctions utilitaires
│
├── results/
│   ├── confusion_matrix.png         # Matrice de confusion
│   └── training_history.png         # Courbes d'entraînement
│
├── requirements.txt                 # Dépendances
└── README.md                        # Documentation
```

## 🗓️ Planning

- **Durée** : 5 jours
- **Présentation orale** : 20–30 minutes
  - Démonstration du code
  - Analyse des résultats
  - Questions/Réponses

## ✅ Livrables

- [x] Notebook fonctionnel et structuré
- [x] README complet
- [x] Synthèse des résultats
- [x] Analyse des limites
- [x] Perspectives d'amélioration

## 🚧 Limites et améliorations

### Limites actuelles

- Architecture simple (DNN) moins performante que les CNN
- Pas de data augmentation
- Pas de fine-tuning ou transfer learning

### Perspectives d'amélioration

1. **Architectures CNN** : Meilleure extraction de features spatiales
2. **Transfer Learning** : Utiliser des modèles pré-entraînés (ResNet, VGG16)
3. **Data Augmentation** : Rotation, zoom, flip pour augmenter la robustesse
4. **Hyperparameter Tuning** : Grid Search ou Random Search
5. **Déploiement** : API REST avec FastAPI ou Flask

## 👤 Auteur

[Ton nom] - AI Engineer

## 📄 Licence

MIT License - voir le fichier LICENSE pour plus de détails

---

⭐ **N'oublie pas de star le projet si tu le trouves utile !**
