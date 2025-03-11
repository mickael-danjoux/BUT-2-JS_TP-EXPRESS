# Routes et méthodes HTTP

Les routes permettent de définir comment votre application répond aux requêtes des clients. Express.js offre différentes méthodes pour gérer les requêtes HTTP.

## GET avec paramètres

Les paramètres d'URL permettent de capturer des valeurs dans l'URL elle-même.

**Créez un fichier routes.js et ajoutez le code suivant :**
```javascript
// Route avec paramètre URL
app.get('/users/:id', (req, res) => {
    const id = req.params.id;
    res.send(`Utilisateur ${id}`);
});

// Route avec query string
app.get('/search', (req, res) => {
    const terme = req.query.q;
    res.send(`Recherche: ${terme}`);
});
```

**Testez les routes :**

-   Accédez à `http://localhost:3000/users/123`
-   Accédez à `http://localhost:3000/search?q=express`

## POST, PUT, DELETE

Ces méthodes HTTP permettent de créer (POST), modifier (PUT) et supprimer (DELETE) des ressources.

**Ajoutez ces routes dans votre fichier :**

```javascript
// Création
app.post('/users', (req, res) => {
    res.status(201).json({ message: 'Utilisateur créé' });
});

 // Modification
app.put('/users/:id', (req, res) => {
    res.json({ message: 'Utilisateur modifié' });
});
// Suppression
app.delete('/users/:id', (req, res) => {
    res.status(204).send();
});
```

**Testez avec un outil comme [Postman](https://www.postman.com/) pour envoyer des requêtes non-GET.**
