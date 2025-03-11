# Présentation sur Symfony

## 1. Qu'est-ce que Symfony ?

Symfony est un **framework PHP open-source** utilisé pour le développement d'applications web. Créé par **SensioLabs**, il suit l'**architecture MVC** (_Modèle-Vue-Contrôleur_), ce qui permet une meilleure organisation du code et une meilleure maintenabilité.

### Architecture MVC :

- **Modèle (Model)** : Gère les données et la logique métier (ex: interaction avec une base de données via Doctrine).
- **Vue (View)** : Affichage des données (ex: templates Twig).
- **Contrôleur (Controller)** : Gère la logique applicative, traite les requêtes et envoie les réponses.

### Pourquoi Symfony ?

- **Modularité** : Basé sur des **composants réutilisables**.
- **Flexibilité** : Adapté aux **petits sites comme aux grandes applications**.
- **Performance** : Optimisé pour gérer des **millions de requêtes**.
- **Sécurité** : Intègre des protections contre **les attaques CSRF, XSS, SQL Injection**.
- **Communauté active** : Support, documentation et mises à jour régulières.

---

## 2. Pourquoi utiliser Symfony ? Comparaison avec d'autres technologies

| Critères          | Symfony       | Astro                  | WordPress           | Joomla    | Vue.js             |
| ----------------- | ------------- | ---------------------- | ------------------- | --------- | ------------------ |
| **Langage**       | PHP           | JavaScript             | PHP                 | PHP       | JavaScript         |
| **Type**          | Framework     | Framework statique     | CMS                 | CMS       | Framework frontend |
| **Flexibilité**   | Très flexible | Orienté statique       | Plugins             | Modulaire | Très flexible      |
| **Performance**   | Haute         | Très rapide (statique) | Moins performant    | Bonne     | Excellente         |
| **Sécurité**      | Haute         | Dépend du backend      | Plugins nécessaires | Bonne     | Dépend du backend  |
| **Apprentissage** | Moyen/avancé  | Moyen                  | Facile              | Facile    | Moyen              |

✅ **Symfony est recommandé pour** :

- Les applications **complexes et évolutives**.
- Les **APIs et applications web** nécessitant une forte modularité.
- Les **sites sécurisés** avec gestion avancée des utilisateurs.

---

## 3. Démarrer un projet avec Symfony

### Prérequis :

- **PHP 8+**
- **Composer** (gestionnaire de dépendances PHP)
- **Symfony CLI** (facultatif mais recommandé)

### Installation :

```sh
composer create-project symfony/skeleton mon_projet
cd mon_projet
symfony serve
```

Le serveur tourne sur http://127.0.0.1:8000.

### Structure d’un projet Symfony :

```php
mon_projet/
├── src/          # Code source (Controllers, Entities…)
├── templates/    # Fichiers Twig pour l'affichage
├── config/       # Fichiers de configuration
├── public/       # Point d'entrée public (index.php)
├── migrations/   # Scripts pour la base de données
└── tests/        # Tests unitaires et fonctionnels
```

---

## 4. Installer Tailwind CSS avec Symfony

### Étapes :

1. Installer Node.js et npm
2. Ajouter Tailwind CSS :

```sh
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init
```

### Configurer tailwind.config.js :

```js
module.exports = {
  content: ["./templates/**/*.html.twig"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

### Ajouter Tailwind dans le CSS :

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Compiler les assets :

```sh
npm run dev
```

---

## 5. Utiliser des composants Symfony

Symfony propose une collection de composants indépendants que l'on peut utiliser dans ou hors d'un projet Symfony.
Exemples de composants utiles :

- HttpFoundation : Gestion des requêtes et réponses HTTP
- Routing : Définition des routes d’une application
- Validator : Validation des données (ex: emails, formulaires)
- Security : Gestion des utilisateurs et authentification

### Exemple : Utilisation du composant Validator

#### Installation :

```sh
composer require symfony/validator
```

#### Utilisation :

```php
use Symfony\Component\Validator\Validation;
use Symfony\Component\Validator\Constraints as Assert;

$validator = Validation::createValidator();
$violations = $validator->validate('test@example.com', [new Assert\Email()]);

if (count($violations) > 0) {
    echo "Email invalide";
} else {
    echo "Email valide";
}
```

---

## 6. Aller plus loin avec Symfony

### 🛠 Outils et bonnes pratiques :

- Twig : Moteur de template pour séparer la logique et l'affichage.
- Doctrine ORM : Gestion avancée des bases de données.
- API Platform : Création d’APIs REST et GraphQL performantes.
- Tests avec PHPUnit : Assurer la qualité du code.
- CI/CD : Déploiement automatisé avec GitHub Actions, GitLab CI.

### 🎯 Conclusion

- Symfony est un framework puissant, sécurisé et modulaire.
- Il convient aux projets complexes nécessitant flexibilité et scalabilité.
- Il dispose d'une grande communauté et d’une documentation riche.

### 🔗 Ressources utiles :

- Site officiel
- Documentation
- Tutoriels SymfonyCasts

🚀 Symfony : Le choix idéal pour développer des applications web robustes et évolutives !

---

# 1. Création du contrôleur BlogController.php

- Emplacement du fichier <br/>
  Le fichier BlogController.php doit être placé dans le répertoire src/Controller/ de votre projet Symfony.

- Code du contrôleur <br/>
  Voici le contenu du fichier BlogController.php que vous devez créer :

```php
<?php

namespace App\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Annotation\Route;

class BlogController extends AbstractController
{
    #[Route('/blog', name: 'blog_index')]
    public function index(): Response
    {
        $articles = [
            ['title' => 'Introduction à Symfony', 'content' => 'Symfony est un framework PHP puissant...'],
            ['title' => 'Pourquoi utiliser Twig ?', 'content' => 'Twig permet de séparer le HTML du PHP...'],
            ['title' => 'Les bases de Doctrine', 'content' => 'Doctrine est un ORM utilisé avec Symfony...'],
        ];

        return $this->render('blog/index.html.twig', [
            'pageTitle' => 'Liste des articles',
            'articles' => $articles,
        ]);
    }
}
```

- Namespace : Le contrôleur se trouve dans le namespace App\Controller, ce qui signifie qu'il doit être dans le dossier src/Controller.

- Route : La méthode index() est liée à l'URL /blog, grâce à l'annotation #[Route('/blog', name: 'blog_index')]. Cela signifie que lorsque l'utilisateur accède à /blog, la méthode index() sera appelée.

- Logique de l'action : Dans la méthode index(), une liste d'articles est définie sous forme de tableau associatif avec un titre et du contenu. Ensuite, la méthode render() est utilisée pour rendre le template Twig, en passant les données des articles et un titre de page.

# 2. Création du template Twig

- Emplacement du fichier Twig <br/>
  Le fichier Twig index.html.twig doit être placé dans le répertoire templates/blog/ de votre projet Symfony.

- Code du fichier index.html.twig <br/>
  Voici le code à ajouter dans le fichier templates/blog/index.html.twig :

```twig
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ pageTitle }}</title>
</head>
<body>
    <h1>{{ pageTitle }}</h1>
    <ul>
        {% for article in articles %}
            <li>
                <h2>{{ article.title }}</h2>
                <p>{{ article.content }}</p>
            </li>
        {% endfor %}
    </ul>
</body>
</html>
```

Variables passées depuis le contrôleur :

    - {{ pageTitle }} : Cette variable est passée du contrôleur et est utilisée dans le titre de la page (<title>) ainsi que dans le titre principal (<h1>).

    - {{ article.title }} et {{ article.content }} : Ces variables représentent le titre et le contenu de chaque article dans la liste d'articles. Le contrôle de l'affichage est fait à l'aide d'une boucle for pour afficher chaque article.

# 3. Explication du fonctionnement

- Contrôleur : Le contrôleur BlogController est responsable de récupérer la liste des articles et de les passer à la vue Twig. La route /blog est associée à la méthode index(), qui crée un tableau d'articles et utilise la méthode render() pour afficher le template Twig index.html.twig.

- Twig : Le template index.html.twig utilise la syntaxe de Twig pour afficher dynamiquement les données passées par le contrôleur. La boucle for parcourt les articles et les affiche dans une liste.

# 4. Test de l'application avec Composer (sans Symfony CLI)

**1.**
Si vous n’utilisez pas la CLI Symfony (symfony serve), vous pouvez lancer un serveur de développement PHP intégré directement avec Composer.

    Démarrer le serveur intégré de PHP
    Symfony repose sur PHP, donc vous pouvez utiliser le serveur intégré de PHP en exécutant la commande suivante depuis le répertoire de votre projet :

    ```bash
    php -S localhost:8000 -t public
    ```

    - -S localhost:8000 : Démarre un serveur local sur le port 8000.
    - -t public : Définit le dossier public comme racine du serveur (où se trouve index.php de Symfony).

**2.**
Accéder à la page
Ouvrez un navigateur et allez à l’adresse suivante :

```
http://localhost:8000/blog
```

Vous devriez voir votre liste d’articles s’afficher correctement.

# 1. Installer Composer

Avant de pouvoir installer Symfony, vous devez avoir Composer installé sur votre machine. Composer est un gestionnaire de dépendances PHP. Si vous ne l'avez pas déjà installé, vous pouvez le faire en suivant les instructions de la documentation officielle de Composer : https://getcomposer.org/download/.

# 2. Créer un projet Symfony

Une fois Composer installé, vous pouvez créer un nouveau projet Symfony en utilisant la commande suivante dans votre terminal ou ligne de commande :

```bash
composer create-project symfony/skeleton nom_du_projet
```

- symfony/skeleton : Il s'agit du paquet de base de Symfony, qui vous permet de commencer avec une installation minimale.
- nom_du_projet : Remplacez cela par le nom du répertoire où vous souhaitez installer votre projet.

Cette commande va télécharger et installer la dernière version stable de Symfony, ainsi que les dépendances de base pour commencer à travailler sur votre projet.

# 3. Naviguer dans le répertoire du projet

Une fois l'installation terminée, allez dans le répertoire du projet que vous venez de créer :

```bash
cd nom_du_projet
```

# 4. Vérification de l'installation

Pour vérifier que Symfony est installé correctement, vous pouvez utiliser la commande suivante :

```bash
php bin/console --version
```

Cela affichera la version de Symfony installée si tout est en place.

# 5. Installer des composants supplémentaires (si nécessaire)

Si vous avez besoin d'ajouter des composants spécifiques à votre projet Symfony, vous pouvez les installer avec Composer. Par exemple, pour installer le composant web, vous pouvez utiliser :

```bash
composer require symfony/web-server-bundle
```

Cela va télécharger et installer le composant Web Server Bundle de Symfony, qui permet de servir votre application localement.

# 6. Lancer le serveur de développement Symfony

Si vous avez installé le serveur de développement, vous pouvez lancer votre application avec la commande suivante :

```bash
php bin/console server:start
```

Cela va démarrer le serveur web intégré de Symfony et vous pourrez voir votre application en ouvrant votre navigateur à l'adresse http://localhost:8000.

# 7. Mettre à jour les dépendances (si nécessaire)

Si vous souhaitez mettre à jour les dépendances de votre projet à tout moment, vous pouvez utiliser la commande suivante :

```bash
composer update
```

Cela mettra à jour toutes les dépendances à leur dernière version compatible.

# Installation de TailwindCSS avec Webpack Encore

1. Installer Webpack Encore (si ce n'est pas déjà fait) :

```
composer require symfony/webpack-encore-bundle
```

2. Installer les dépendances Node :

- Dans le répertoire de votre projet, lancez :

```
npm install
```

3. Installer Tailwind CSS et ses dépendances :

```
npm install -D tailwindcss postcss autoprefixer
```

4. Générer le fichier de configuration Tailwind :

```
npx tailwindcss init
```

5. Configurer Tailwind :

- Dans le fichier tailwind.config.js, indiquez les chemins vers vos templates et fichiers JS pour activer le purge (exemple) :

```js
module.exports = {
  content: ["./templates/**/*.html.twig", "./assets/**/*.js"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

6. Ajouter les directives Tailwind dans votre CSS :

- Dans votre fichier CSS principal (par exemple assets/app.css), ajoutez :

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

7. Compiler vos assets :
   Pour compiler et vérifier que tout fonctionne, lancez :

```bash
npm run dev
```

## Si besoin :

Installer le module manquant

Si, pour une raison spécifique, vous souhaitez conserver l’import de @symfony/stimulus-bundle, vous pouvez installer le package manquant. Cependant, il est recommandé d’utiliser @symfony/stimulus-bridge dans un projet Symfony moderne.
Pour installer le module (si besoin) :

```
npm install -D @symfony/stimulus-bundle
```

Puis lancez :

```
npm run dev
```

Document réalisé par M MELONI
