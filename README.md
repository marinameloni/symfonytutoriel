# Présentation sur Symfony

## 1. Qu'est-ce que Symfony ?
Symfony est un **framework PHP open-source** utilisé pour le développement d'applications web. Créé par **SensioLabs**, il suit l'**architecture MVC** (*Modèle-Vue-Contrôleur*), ce qui permet une meilleure organisation du code et une meilleure maintenabilité.

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

| Critères       | Symfony | Astro | WordPress | Joomla | Vue.js |
|---------------|---------|-------|----------|--------|--------|
| **Langage** | PHP | JavaScript | PHP | PHP | JavaScript |
| **Type** | Framework | Framework statique | CMS | CMS | Framework frontend |
| **Flexibilité** | Très flexible | Orienté statique | Plugins | Modulaire | Très flexible |
| **Performance** | Haute | Très rapide (statique) | Moins performant | Bonne | Excellente |
| **Sécurité** | Haute | Dépend du backend | Plugins nécessaires | Bonne | Dépend du backend |
| **Apprentissage** | Moyen/avancé | Moyen | Facile | Facile | Moyen |

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
Structure d’un projet Symfony :
```php
mon_projet/
├── src/          # Code source (Controllers, Entities…)
├── templates/    # Fichiers Twig pour l'affichage
├── config/       # Fichiers de configuration
├── public/       # Point d'entrée public (index.php)
├── migrations/   # Scripts pour la base de données
└── tests/        # Tests unitaires et
 fonctionnels
```
