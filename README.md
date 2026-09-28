# 🧪 Suite de Tests Automatisés API REST (CRUD) — Postman

## 📌 Présentation du Projet
Ce projet présente une suite complète de tests d'intégration et de bout en bout (E2E) pour valider le cycle de vie complet d'une ressource (Produit) sur l'API publique Platzi Fake Store API.

Les tests sont conçus pour s'exécuter de manière 100 % séquentielle et automatisée via le **Collection Runner** de Postman.

---

## 🛠️ Tech Stack & Concepts Clés
- **Outil :** Postman (Collection Runner)
- **Langage de script :** JavaScript (Node.js)
- **Assertions :** Chai Assertion Library (`pm.expect`)
- **Gestion d'état :** Extraction dynamique de variables d'environnement (`pm.environment.set`)
- **Format de données :** JSON

---

## 🔄 Flux de Tests (Cycle CRUDR)

| Ordre | Méthode | Endpoint | Description & Assertions |
| :---: | :---: | :--- | :--- |
| **1** | `POST` | `/products/` | **Create** : Création du produit. Extraction et stockage dynamique de `id` dans `{{productId}}`. Statut `201`. |
| **2** | `GET` | `/products/{{productId}}` | **Read** : Validation de la création. Vérification de la correspondance de l'ID et de la présence des champs. Statut `200`. |
| **3** | `PUT` | `/products/{{productId}}` | **Update** : Modification du titre du produit. Statut `200`. |
| **4** | `DELETE` | `/products/{{productId}}` | **Delete** : Suppression de la ressource. Statut `200`. |
| **5** | `GET` | `/products/{{productId}}` | **Read (Post-Delete)** : Vérification de la suppression effective en base de données. Statut `404 Not Found`. |

---

## 🚀 Comment Exécuter les Tests

1. Télécharger ou cloner ce dépôt.
2. Ouvrir **Postman**.
3. Cliquer sur **Import** et charger les deux fichiers suivants :
   - `Platzi_API_E2E.postman_collection.json`
   - `Dev_Environment.postman_environment.json`
4. Sélectionner l'environnement **Dev Environment** en haut à droite.
5. Faire un clic droit sur la collection > **Run collection**.
6. Cliquer sur **Run Platzi API E2E**.

---

## 💡 Bonnes Pratiques QA Appliquées
- **Variabilisation dynamique :** Aucun ID n'est codé en dur. Les identifiants sont propagés entre les requêtes via des scripts Postman.
- **Transtypage (Type Casting) :** Conversion explicite des variables d'environnement (stockées en string) via `Number()` pour éviter les erreurs de type lors des assertions.
- **Validation 404 post-suppression :** Vérification systématique de l'absence du produit après une opération `DELETE`.
