# Initialisation de Sequelize

Sequelize est un ORM (Object-Relational Mapping) pour Node.js. Il permet de :

-   Manipuler une base de données via des objets JavaScript
-   Définir les relations entre les tables
-   Gérer les migrations de base de données

## Création de la base

**Installation des dépendances nécessaires :**

```shell
npm install sequelize mysql2
```

Nous allons utiliser une BDD via Docker pour éviter certaines configuration.

**Démarrer la BDD**
```shell
docker compose up -d
```
(Stopper la BDD)
```shell
docker compose down --remove-orphans
```

**Créez un fichier `database.js` :**

```javascript
import { Sequelize } from 'sequelize';  
  
export const sequelize = new Sequelize(  
  'database',  
  'user',  
  'password',  
  {  
    host: 'localhost',  
    dialect: 'mysql',  
    logging: true,
  },  
);  
```

**Dans un fichier database.route.js, ajoutez la route de test :**
```javascript
import { Router } from 'express';  
import sequelize from '../database.js';  
  
const router = new Router();  
  
router.get('/test-connection', async (req, res, next) => {  
  try {  
    await sequelize.authenticate();  
    res.json({ message: 'Connexion à la base de données réussie' });  
  } catch (error) {  
    next(error);  
  }  
});  
  
export default router;
```

**Actions :**

1.  Créez database.js avec vos identifiants de connexion
2.  Importez et utilisez la route  dans index.js
3.  Testez la route dans votre navigateur
4.  Modifiez volontairement les données de `database.js` et observez l'erreur générée

**Question :** Quels erreurs sont renvoyées quand la connexion échoue ?



