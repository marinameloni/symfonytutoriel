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

📌 Ce document est **prêt à être utilisé** pour ton oral et tes slides ! Il est structuré, clair et adapté.
