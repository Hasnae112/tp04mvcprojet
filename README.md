# Projet JEE – MVC1 : Gestion des Produits

## Description

Application web Java EE de gestion CRUD des produits, basée sur l'architecture **MVC1 + 3-Tiers**.

- **Formateur** : Mohamed CHERRADI – TDIA, ENSA Hoceima, UAE

---

## Technologies utilisées

| Technologie | Version |
|-------------|---------|
| Java | 11+ |
| Servlet API | 4.0.1 |
| JSP API | 2.3.3 |
| JSTL | 1.2 |
| Apache Tomcat | 9.x |
| Maven | 3.x |

---

## Architecture

```
[Browser]
   |
   v
[Controller – Servlets]  (package web)
   |
   v
[Service – Métier]       (package services)
   |
   v
[DAO – Accès données]    (package dao)
   |
   v
[Modèle – Produit]       (classe dao.Produit)
```

### Servlets (MVC1 – une servlet par opération)

| URL            | Servlet               | Rôle                          |
|----------------|-----------------------|-------------------------------|
| /listProduits  | ListProduitServlet    | Afficher tous les produits    |
| /addProduit    | AddProduitServlet     | Ajouter un produit            |
| /deleteProduit | DeleteProduitServlet  | Supprimer un produit          |
| /editProduit   | EditProduitServlet    | Charger un produit à modifier |
| /updateProduit | UpdateProduitServlet  | Mettre à jour un produit      |

---

## Structure du projet

```
GestionDesProduitsMVC1/
├── pom.xml
└── src/
    └── main/
        ├── java/
        │   ├── dao/
        │   │   ├── Produit.java
        │   │   ├── ProduitDAO.java
        │   │   └── ProduitImpl.java
        │   ├── services/
        │   │   ├── ProduitMetier.java
        │   │   └── ProduitMetierImpl.java
        │   └── web/
        │       ├── ListProduitServlet.java
        │       ├── AddProduitServlet.java
        │       ├── DeleteProduitServlet.java
        │       ├── EditProduitServlet.java
        │       └── UpdateProduitServlet.java
        └── webapp/
            ├── index.jsp
            └── WEB-INF/
                └── web.xml
```

---

## Installation et déploiement

### Prérequis

- JDK 11 ou supérieur
- Apache Maven 3.x
- Apache Tomcat 9.x

### Étapes

1. **Cloner / extraire** le projet dans votre workspace
2. **Importer** dans Eclipse comme *Existing Maven Project*
3. **Builder** le projet :
   ```bash
   mvn clean package
   ```
4. **Déployer** le `.war` généré dans `target/` sur Tomcat
5. **Accéder** à l'application :
   ```
   http://localhost:8080/GestionDesProduitsMVC1/listProduits
   ```

### Avec Eclipse + Tomcat

1. Importer le projet Maven dans Eclipse
2. Configurer un serveur Tomcat 9 dans Eclipse
3. Clic droit sur le projet → *Run As* → *Run on Server*

---

## Fonctionnalités

- ✅ Afficher la liste des produits
- ✅ Ajouter un produit
- ✅ Modifier un produit (formulaire pré-rempli)
- ✅ Supprimer un produit (avec confirmation)
- ✅ Rechercher un produit par ID

---

## Notes

- Les données sont stockées **en mémoire** (liste Java). Elles sont réinitialisées à chaque redémarrage du serveur.
- Pour persister les données, remplacer `ProduitImpl` par une implémentation JDBC ou JPA.
- Le pattern **Singleton** est utilisé dans `ProduitMetierImpl` pour partager la même instance entre toutes les servlets.
