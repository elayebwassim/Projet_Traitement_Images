# Projet_Traitement_Images
> Implémentation mathématique et optimisée du Filtre Guidé pour le débruitage et la régularisation de transfert de couleurs.
# Traitement d'Images : Restauration et Filtrage Guidé 

## Contexte du projet
Ce projet, réalisé dans le cadre de mon Master 1 de Mathématiques Appliquées (Université Paris-Cité), porte sur le traitement d'images et la vision par ordinateur. 

L'objectif est d'étudier et d'implémenter de zéro le **Filtre Guidé**, en se basant sur l'article de recherche fondateur de *Kaiming He, Jian Sun, et Xiaoou Tang (ECCV 2010)*. Ce filtre est particulièrement réputé pour sa capacité à lisser une image tout en préservant parfaitement les contours, surpassant les limites du filtre bilatéral classique (artefacts d'inversion de gradient).

## Technologies et Outils
* **Langage :** Python
* **Librairies :** NumPy, Matplotlib, Time (mesure de performance)
* **Concepts Mathématiques :** Régression linéaire locale, image intégrale (optimisation $\mathcal{O}(N)$ ), filtre passe-bas, régularisation.

## Démarche, Implémentation et Résultats

### 1. Implémentation et Optimisation Mathématique
Plutôt que d'utiliser des fonctions pré-codées, l'algorithme a été codé "from scratch" en traduisant directement les équations mathématiques de l'article :
* **V1 (Naïve) :** Implémentation directe avec extraction de patchs locaux (fenêtres de rayon $r$), calcul de moyenne/variance et régression linéaire. Complexité $\mathcal{O}(Nr^2)$.
* **V2 (Optimisée) :** Utilisation du concept d'**Image Intégrale** pour accélérer drastiquement les calculs et rendre la complexité indépendante de la taille du patch : $\mathcal{O}(N)$.

### 2. Validation et Étude des Hyperparamètres ($r$ et $\epsilon$)
Le filtre a été testé sur des images bruitées (ex: ajout de bruit gaussien) afin d'étudier l'impact de ses deux paramètres fondamentaux :
* **Le rayon $r$** : Définit la taille du voisinage spatial analysé.
* **La régularisation $\epsilon$** : Agit comme un seuil de détection de contour.

*(Plus* $\epsilon$ *augmente, plus le filtre moyenne et lisse l'image. Les contours forts restent préservés grâce au modèle linéaire local).*

<img width="985" height="657" alt="grille_chats" src="https://github.com/user-attachments/assets/b254a7c3-7b17-4062-a47d-c5efb5197c17" />


### 3. Application Avancée : Régularisation de Transfert de Couleurs
Pour démontrer l'utilité du filtre guidé dans des pipelines complexes de Computer Vision, il a été appliqué comme étape de **régularisation après un transfert de couleurs** entre deux images. 
Le filtre guidé utilise l'image originale comme "guide" pour lisser les artefacts de couleur tout en respectant strictement les contours et la structure de l'image.

<img width="1002" height="566" alt="color_transfer" src="https://github.com/user-attachments/assets/0d53c16a-0f4c-4da8-b49e-fdaae33aa605" />


## Compétences démontrées
* Traduction d'équations mathématiques issues de la recherche (Computer Vision) en algorithmes matriciels Python fonctionnels et optimisés.
* Manipulation avancée de tableaux multidimensionnels avec NumPy (images intégrales, padding, calculs statistiques locaux).
* Compréhension des enjeux de traitement du signal (bruit gaussien, préservation des hautes fréquences/contours, transfert de couleurs).
