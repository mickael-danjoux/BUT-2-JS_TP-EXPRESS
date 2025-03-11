# Traitement de formulaires

Pour traiter les données de formulaires, nous avons besoin de body-parser qui analyse le corps des requêtes.

**Installez body-parser :**

```shell
npm install body-parser
```

**Configurez body-parser dans votre application :**

```javascript
import bodyParser from 'body-parser'

app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());
```
`extended: true` permet de traiter des données complexes dans les formulaires.

## Gestion d’un formulaire

**Créez un formulaire HTML dans  /public/form.html**
- Créer une page HTML
- Créer un formulaire avec `action="/submit"` et  `method="POST"`
- Créer un champs `name` et `email`

**Ajoutez la route pour traiter le formulaire :**

On va indiquer que tous ce qui se trouve dans le dossier `public` est une ressource static qu'on pourra envoyer tel quelle.

```javascript
app.use(express.static('public'));
```

**Depuis un navigateur visitez [http://127.0.0.1:3000/form.html]()**

```javascript
app.post('/submit', (req, res) => {
    const { name, email } = req.body;
    res.json({
        message: 'Formulaire reçu',
        data: { name, email }
    });
});
```

# Gestion des erreurs

La gestion des erreurs est cruciale pour maintenir la stabilité de l'application.

**Ajoutez ce middleware d'erreur à la fin de votre application :**

```javascript
app.use((err, req, res, next) => {  
  console.error(err.stack);  
  res.status(500).json({   
    message: 'Erreur serveur',   
    error: err.message
  });  
});
```

Ce middleware capture toutes les erreurs non gérées. En développement, il affiche les détails de l'erreur.

**Créez une route qui lève une Erreur avec un message personnalisé**

**Attention:** Veillez à placer cette route avant votre middleware !

**Visitez votre nouvelle route.**

**Question:** Quel est le message affiché?
