# Schéma et premières données

Nous allons créer le schéma de données de nos utilisateurs. 

**Ajoutez le modèle dans `database.js`**

```javascript
import { DataTypes, Sequelize } from 'sequelize';

export const User = sequelize.define('User', {  
  id: {  
    type: DataTypes.INTEGER,  
    primaryKey: true,  
    autoIncrement: true  
  },  
  username: {  
    type: DataTypes.STRING,  
    allowNull: false,  
    unique: true  
  },  
  email: DataTypes.STRING  
});
``` 

Le Schéma est maintenant créé. Il faut ensuite synchroniser la base:

```javascript
export const initDb = async () => {  
  try {  
    await sequelize.sync();  
    console.log('Base de données synchronisée');  
  } catch (error) {  
    console.error('Erreur de synchronisation:', error);  
  }  
};
```

**Importez cette fonction dans `index.js` afin qu’elle soit exécutée au démarrage du serveur.**

### Création d’un utilisateur

Vous aller devoir créer un utilisateur en complétant de contenu de la route précédemment créée `POST /users`

- Importer **User** issue du fichier `database.js`
- Appeler la fonction `User.create()` avec les données reçut de la requête POST
- Retourner le résultat avec une **201**
- Appeler la fonction **next(error)** en cas d’échec. L’erreur sera retournée par le middleware déjà en place.

**Vérifiez avec une requête Postman le bon fonctionnement.**

 **Vérifiez avec une requête Postman le bon traitement des erreurs retournées par User.create**
 
### CRUD

Complétez les méthodes **PUT**, **GET** et **DELETE**.

- Retournez l’objet en cas de succès
- Retournez 404 s’il n’existe pas
- Retournez 204 pour DELETE
- Renvoyez les erreurs au Middleware
- Utilisez les méthodes **User.findByPk**, **User.destroy**, **user.update**
