
# 🧠 Fashion Item Recognition Prototype (DNN)

## 📘 Contexte du projet

Tu es **AI Engineer** dans une équipe d'e-commerce spécialisée dans la **mode**.
L'entreprise souhaite **prototyper rapidement** une fonctionnalité de **reconnaissance d'articles vestimentaires** (T-shirt, pantalon, chaussure, etc.) avant d'investir dans des architectures plus complexes comme les **CNN** ou le **transfert learning**.

🎯 **Objectif principal :**
Valider le pipeline complet :
**données → modèle → métrique**

et obtenir une **accuracy > 80 %** avec un modèle DNN simple.

---

## 🧩 Objectifs du projet

### 🎯 Ce qu'on doit livrer :

* Un **prototype DNN simple et reproductible**.
* Une **accuracy test > 80 %**.
* Un **notebook clair, commenté et structuré**.
* Une **planification complète sur Jira**.

### 💡 Pourquoi ce projet :

* **Prouver la faisabilité** du modèle de classification.
* **Évaluer la qualité des résultats.**
* **Décider** d'un éventuel investissement dans des modèles plus puissants (CNN, transfert learning).

---

## ⚙️ Étapes du projet

### 1️⃣ Chargement et préparation des données

* Utilisation du dataset **Fashion MNIST** via `tensorflow.keras.datasets`.
* Vérification :
  * Dimensions : `(60000, 28, 28)` pour train, `(10000, 28, 28)` pour test.
  * 10 classes : `['T-shirt/top', 'Trouser', 'Pullover', 'Dress', 'Coat', 'Sandal', 'Shirt', 'Sneaker', 'Bag', 'Ankle boot']`.
* **Normalisation des pixels** :
  Division par 255 → valeurs entre `[0, 1]`.
* **Labels** : entiers (0–9)
  → Utilisation de `sparse_categorical_crossentropy`.

---

### 2️⃣ Construction du modèle (DNN)

### 3️⃣ Entraînement du modèle

* Entraînement sur **5 à 10 époques**.
* Suivi du `history` (loss, accuracy, val_loss, val_accuracy).
* Visualisation graphique des performances.

---

### 4️⃣ Évaluation du modèle

* Évaluation sur le jeu de test :

```python
test_loss, test_acc = model.evaluate(test_images, test_labels, verbose=2)
print("Test accuracy:", test_acc)
```

✅ **Objectif :** obtenir **une précision supérieure à 80 %**.

---

### 5️⃣ Documentation & Synthèse

#### 🔧 Hyperparamètres testés :

* Nombre de neurones :  128 
* Optimizers : Adam
* Batch size : 32 
* Epochs : 10 

#### 🎯 Choix de la loss :

* `sparse_categorical_crossentropy` utilisée car les **labels sont entiers (0–9)**.
* `categorical_crossentropy` serait utilisée si les labels étaient **one-hot encodés**.

---

## 🧰 Outils & Librairies

* **Google Colab**
* **TensorFlow / Keras**
* **numpy, pandas**
* **matplotlib, seaborn**
* **scikit-learn**
* **Jira** pour la planification

---

## 🚀 Installation & Exécution

### 📋 Prérequis

* Python 3.8+
* Compte Google (pour Colab)

---

### 💻 Option : Exécution sur Google Colab (Recommandé)

1. **Ouvrir le notebook dans Colab**
   
   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)
   
   Ou aller sur : [https://colab.research.google.com](https://colab.research.google.com)

2. **Importer le notebook**
   * Cliquer sur **Fichier → Ouvrir le notebook**
   * Sélectionner l'onglet **GitHub** ou **Charger**
   * Importer `FashionMNIST_DNN.ipynb`

3. **Exécuter toutes les cellules**
   * Menu : **Exécution → Tout exécuter**

```

#### 3. Installer les dépendances

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

**Contenu de `requirements.txt` :**

```txt
tensorflow>=2.13.0
numpy>=1.24.0
pandas>=2.0.0
matplotlib>=3.7.0
seaborn>=0.12.0
scikit-learn>=1.3.0
jupyter>=1.0.0
```

#### 4. Lancer Jupyter Notebook

```bash
jupyter notebook
```

#### 5. Ouvrir le fichier

* Dans l'interface Jupyter, ouvrir `FashionMNIST_DNN.ipynb`
* Exécuter les cellules une par une ou toutes en même temps

---

## 🗓️ Modalités pédagogiques

* **Travail individuel**
* **Durée :** 5 jours
* **Présentation orale :** 20–30 minutes
  * Exécution du code
  * Analyse des résultats
  * Session Q&A

---

## 🧾 Modalités d'évaluation

| Critère                 | Description                 |
| ----------------------- | --------------------------- |
| ✅ Pipeline complet      | Données → Modèle → Métrique |
| 🧹 Clarté du code       | Notebook bien commenté      |
| 📊 Performance          | Accuracy > 80 %             |
| 🧠 Synthèse comparative | Benchmark clair et concis   |
| 📅 Planification        | Utilisation de Jira         |
| ⭐ Bonus                 | EarlyStopping / model.save  |

---

## 🎯 Critères de réussite

✅ Modèle fonctionnel (>80% de précision)
✅ Notebook clair et structuré
✅ Benchmark IA présenté et comparé
✅ Planification Jira terminée
⭐ (Bonus) EarlyStopping ou sauvegarde du modèle

---


## 👤 Auteur

Maryem Elbergui



---

⭐ **N'oublie pas de star le projet si tu le trouves utile !**
