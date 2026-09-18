# Tetris-C-

Jeu Tetris développé en C++ avec SFML. Ce dépôt contient le code source, les ressources et les tests unitaires de la logique du jeu.

**Table des matières**
- **Description**: Aperçu du projet
- **Prérequis**: dépendances système
- **Compilation**: instructions pour compiler avec CMake
- **Exécution**: lancer le jeu et options courantes
- **Contrôles**: commandes clavier et manette
- **Tests**: exécution des tests unitaires
- **Structure**: organisation du code
- **Développement**: guide rapide pour contribuer

**Description**

Tetris-C- est une implémentation du célèbre jeu Tetris écrite en C++17 et utilisant la bibliothèque SFML pour l'affichage et la gestion des entrées. La logique du jeu est séparée dans une librairie statique testable indépendamment, ce qui facilite l'écriture de tests unitaires.

**Prérequis**

- Système: Linux (compatible), Windows et macOS en théorie
- CMake >= 3.16
- Compilateur C++17 (g++, clang, MSVC)
- SFML 2.5 (packages: libsfml-dev sur Debian/Ubuntu)

Sur Debian/Ubuntu, installez les paquets requis :

```bash
sudo apt update
sudo apt install build-essential cmake libsfml-dev
```

**Compilation**

1. Créez un dossier de build et entrez dedans :

```bash
cd <chemin_vers_le_projet>
mkdir -p build && cd build
```

2. Configurez et compilez avec CMake :

```bash
cmake ..
cmake --build . --config Release
```

Options CMake utiles :
- `-DTETRIS_SANITIZERS=ON` : active AddressSanitizer/UBSan (débogage)
- `-DTETRIS_TESTS=ON|OFF` : compiler ou non les tests (par défaut ON)
- `-DTETRIS_NATIF=ON` : activer `-march=native` (binaire non portable)

Après la compilation, l'exécutable `Tetris` se trouve dans le dossier de build et le répertoire `asset/` est copié à côté de l'exécutable.

**Exécution**

Depuis le répertoire `build` :

```bash
./Tetris
```

Sur Windows, exécutez `Tetris.exe` depuis l'explorateur ou la console.

**Contrôles**

- Flèches gauche/droite : déplacer la pièce
- Flèche bas : accélérer la descente
- Flèche haut / X / Z : rotation (selon configuration)
- Espace : drop instantané
- P : pause
- Échap : quitter

La gestion de la manette est prévue dans `src/Manette.*`.

**Tests**

Le projet contient des tests pour la logique du jeu (`tests/test_logique.cpp`). Pour exécuter les tests après compilation :

```bash
cd build
ctest --output-on-failure
```

ou lancer directement l'exécutable de tests :

```bash
./tests_logique
```

**Structure du projet**

- `CMakeLists.txt` : configuration de build
- `asset/` : ressources (images, polices, sons)
- `src/` : code source
	- `Application.*`, `main.*` : point d'entrée et boucle principale
	- `Rendu.*`, `Ressources.*`, `Texte.*` : rendu et gestion des ressources
	- `Jeu.*`, `Piece.*`, `Sac.*`, `Repetition.*` : logique du jeu (lib `tetris_logique`)
	- `Manette.*`, `Touches.*` : saisie utilisateur
- `tests/` : tests unitaires pour la logique

**Guide de développement**

1. Fork/clone le dépôt et créez une branche dédiée pour votre fonctionnalité :

```bash
git checkout -b feat/ma-fonctionnalite
```

2. Respectez la séparation entre la logique (`tetris_logique`) et la partie graphique pour faciliter les tests.

3. Ajoutez des tests pour toute modification de la logique de jeu. Placez-les dans `tests/` et assurez-vous qu'ils compilent.

4. Utilisez les options CMake pour activer les sanitizers lors du développement :

```bash
cmake -DTETRIS_SANITIZERS=ON -DTETRIS_TESTS=ON ..
cmake --build .
ctest --output-on-failure
```

5. Style et conventions :
- C++17, évitez les extensions spécifiques à un compilateur si possible
- Respectez l'organisation actuelle des fichiers dans `src/`

6. Proposer une Pull Request : décrivez la fonctionnalité/bogue, indiquez comment tester et mentionnez les tests ajoutés.

**Contribuer**

Les contributions sont bienvenues. Ouvrez une issue pour discuter des changements majeurs avant d'implémenter.

**Licence**

Vérifiez le fichier `LICENSE` si présent. Si aucune licence n'est fournie, contactez l'auteur pour clarifier les droits.

---

Fichier principal de travail : [README.md](README.md)

Pour toute question ou aide supplémentaire, dites-moi ce que vous voulez que j'ajoute ou modifie dans la documentation.

