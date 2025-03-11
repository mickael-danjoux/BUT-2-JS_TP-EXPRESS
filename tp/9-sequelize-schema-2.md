# Relations
Nous allons maintenant voir comment associer des données à nos utilisateurs.
**Completez le schéma `database.js`**
```javascript
export const Post = sequelize.define('Post', {  
  id: {  
    type: DataTypes.INTEGER,  
    primaryKey: true,  
    autoIncrement: true,  
  },  
  title: {  
    type: DataTypes.STRING,  
    allowNull: false,  
  },  
  content: {  
    type: DataTypes.TEXT,  
  },  
  UserId: {  
    type: DataTypes.INTEGER,  
    allowNull: false,  
    references: {  
      model: 'Users',  
      key: 'id',  
    },  
  },  
});

// Définir la relation 
User.hasMany(Post); 
Post.belongsTo(User);
```
