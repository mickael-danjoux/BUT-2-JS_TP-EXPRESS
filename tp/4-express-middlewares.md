# Middleware

Les middlewares sont des fonctions qui ont accès aux objets requête (req), réponse (res) et à la fonction suivante (next). Ils peuvent exécuter du code, modifier les objets req/res et terminer le cycle requête-réponse.

## Middleware global

**Ajoutez ce middleware au début de votre application :**

```javascript
app.use((req, res, next) => {  
  console.log(`MIDDLEWARE: ${req.method} ${req.url}`);  
  next();  
});
```
**Faites un appel sur une route de votre application.**

**Question:**  Que voyez-vous dans la console?

Le middleware global s'applique à toutes les requêtes. La fonction `next()` passe au middleware suivant.

## Middleware spécifique

Les middlewares spécifiques ne s'appliquent qu'aux routes désignées.

**Créez un middleware d'authentification :**

```javascript
const verifierAuth = (req, res, next) => {
    const token = req.headers.authorization;
    if (!token) {
        return res.status(401).json({ message: 'Non autorisé' });
    }
    next();
};

app.get('/admin', verifierAuth, (req, res) => {
    res.send('Zone admin');
});
```

**Dans un navigateur, visitez [http://127.0.0.1:3000/admin]().** 

**Question:**  Quel est la réponse?

**Testez cette même route avec [Postman](https://www.postman.com/)  en ajoutant un header Authorization quelconque**

**Question:** Quel est la réponse?

