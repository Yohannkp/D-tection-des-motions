# 🎭 Projet d'Analyse d'Émotions en Temps Réel avec PyTorch

Un système de reconnaissance d'émotions en temps réel utilisant un réseau de neurones convolutionnel (CNN) avec PyTorch et OpenCV pour la détection via webcam.

## 📋 Description

Ce projet implémente un modèle de deep learning capable de détecter et classifier 7 émotions différentes à partir d'images de visages en temps réel. Le système utilise une architecture CNN personnalisée entraînée sur vos données locales et une interface webcam pour la détection en direct.

## 🎯 Émotions Détectées

- **Angry** (Colère) 😠
- **Disgusted** (Dégoût) 🤢
- **Fearful** (Peur) 😨
- **Happy** (Joie) 😊
- **Neutral** (Neutre) 😐
- **Sad** (Tristesse) 😢
- **Surprised** (Surprise) 😲

## 🚀 Fonctionnalités

### ✅ Entraînement du Modèle
- Architecture CNN optimisée avec 3 blocs convolutionnels
- Augmentation de données pour améliorer la généralisation
- Early stopping et réduction adaptative du learning rate
- Batch normalization et dropout pour éviter l'overfitting
- Sauvegarde automatique du meilleur modèle

### ✅ Évaluation Complète
- Métriques détaillées (accuracy, precision, recall, F1-score)
- Matrice de confusion interactive
- Analyse des classifications incorrectes
- Visualisation des résultats d'entraînement

### ✅ Détection en Temps Réel
- Interface webcam en temps réel
- Détection automatique des visages avec OpenCV
- Affichage des émotions avec niveau de confiance
- Top 3 des probabilités d'émotions
- Indicateur FPS
- Option de sauvegarde vidéo

## 📁 Structure du Projet

```
Analyse sentiments/
├── train/                     # Données d'entraînement
│   ├── angry/
│   ├── disgusted/
│   ├── fearful/
│   ├── happy/
│   ├── neutral/
│   ├── sad/
│   └── surprised/
├── test/                      # Données de test
│   ├── angry/
│   ├── disgusted/
│   ├── fearful/
│   ├── happy/
│   ├── neutral/
│   ├── sad/
│   └── surprised/
├── Projet.ipynb              # Notebook principal
├── requirements.txt          # Dépendances
├── README.md                 # Ce fichier
└── emotion_model.pth         # Modèle sauvegardé (généré après entraînement)
```

## 🛠️ Installation

### Prérequis
- Python 3.7+
- Webcam fonctionnelle
- GPU CUDA (optionnel mais recommandé)

### 1. Cloner le projet
```bash
git clone <votre-repo>
cd "Analyse sentiments"
```

### 2. Installer les dépendances
```bash
pip install -r requirements.txt
```

### 3. Vérifier la structure des données
Assurez-vous que vos dossiers `train/` et `test/` contiennent les sous-dossiers pour chaque émotion avec les images correspondantes.

## 🚀 Utilisation

### 1. Ouvrir le Notebook
```bash
jupyter notebook Projet.ipynb
```

### 2. Exécuter les cellules dans l'ordre

1. **Cellule 1-2** : Imports et configuration
2. **Cellule 3-5** : Exploration et visualisation des données
3. **Cellule 6-7** : Création des datasets et architecture du modèle
4. **Cellule 8-10** : Entraînement du modèle
5. **Cellule 11-12** : Évaluation et métriques
6. **Cellule 13-15** : Détection en temps réel

### 3. Lancer la Détection en Temps Réel

#### Option 1 : Fonction simple
Dans la cellule 15, décommentez :
```python
start_realtime_detection()
```

#### Option 2 : Avec options avancées
```python
# Détection sans limite de temps
emotion_detector.run_realtime_detection()

# Détection limitée à 30 secondes
emotion_detector.run_realtime_detection(duration=30)

# Détection avec sauvegarde vidéo
emotion_detector.run_realtime_detection(save_video=True)
```

### 4. Contrôles
- **Appuyez sur 'q'** dans la fenêtre vidéo pour arrêter
- **Positionnez votre visage** face à la caméra pour de meilleurs résultats

## 📊 Performance

### 🖼️ Résultat de l'Application

![Détection d'Émotions en Temps Réel](resultat.png)

*Exemple de détection d'émotion en temps réel avec affichage de la confiance et des probabilités*

### Métriques Attendues
- **Accuracy** : 60-80% (selon la qualité des données)
- **Temps de traitement** : ~30-60 FPS selon le matériel
- **Taille du modèle** : ~1.5M paramètres

### Optimisations Incluses
- ✅ Augmentation de données
- ✅ Batch normalization
- ✅ Dropout layers
- ✅ Early stopping
- ✅ Learning rate scheduling
- ✅ Détection de visages optimisée

## 🎨 Interface Utilisateur

### Affichage en Temps Réel
- **Rectangle coloré** autour du visage détecté
  - 🟢 Vert : Confiance élevée (>70%)
  - 🟡 Jaune : Confiance moyenne (50-70%)
  - 🔴 Rouge : Confiance faible (<50%)
- **Texte principal** : Émotion + confiance
- **Top 3 émotions** avec probabilités
- **Compteur FPS** en temps réel

## 🔧 Configuration

### Hyperparamètres (modifiables dans la cellule 3)
```python
BATCH_SIZE = 32          # Taille des batches
LEARNING_RATE = 0.001    # Taux d'apprentissage
NUM_EPOCHS = 20          # Nombre d'époques
IMG_SIZE = 48            # Taille des images (48x48)
PATIENCE = 5             # Patience pour early stopping
```

### Chemins des données
```python
TRAIN_PATH = 'train'     # Dossier d'entraînement
TEST_PATH = 'test'       # Dossier de test
```

## 📈 Améliorations Possibles

### 🔮 Fonctionnalités Futures
1. **Transfer Learning** avec ResNet/EfficientNet
2. **Détection multi-visages** simultanée
3. **Interface graphique** avec Tkinter/Streamlit
4. **API REST** pour intégration web
5. **Détection d'émotions** dans les vidéos
6. **Analyse de sentiment** textuel combinée

### 🚀 Optimisations Performance
1. **Quantification du modèle** pour mobile
2. **ONNX** pour déploiement cross-platform
3. **TensorRT** pour GPU NVIDIA
4. **Détection de visages** avec MTCNN/RetinaFace

## 🐛 Résolution de Problèmes

### Problèmes Communs

#### Webcam non détectée
```python
# Vérifier les caméras disponibles
import cv2
for i in range(5):
    cap = cv2.VideoCapture(i)
    if cap.isOpened():
        print(f"Caméra {i} disponible")
        cap.release()
```

#### Erreurs CUDA
```bash
# Vérifier l'installation PyTorch
python -c "import torch; print(torch.cuda.is_available())"
```

#### Performance lente
- Réduire `IMG_SIZE` à 32x32
- Utiliser CPU si GPU insuffisant
- Réduire `BATCH_SIZE`

## 📝 Logs et Sauvegarde

### Fichiers générés
- `emotion_model.pth` : Modèle entraîné
- `emotion_detection.avi` : Vidéo sauvegardée (si activée)

### Métriques sauvegardées
- Historique des pertes d'entraînement/validation
- Courbes de précision
- Matrice de confusion
- Rapport de classification détaillé

## 🤝 Contribution

### Pour contribuer :
1. Fork le projet
2. Créer une branche feature
3. Commit vos changements
4. Push vers la branche
5. Ouvrir une Pull Request

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.

## 👨‍💻 Auteur

Votre nom - [Votre email]

## 🙏 Remerciements

- **PyTorch** pour le framework de deep learning
- **OpenCV** pour la vision par ordinateur
- **scikit-learn** pour les métriques d'évaluation
- La communauté open source pour les outils utilisés

---

**🎭 Détectez les émotions en temps réel avec l'IA ! 🚀**
