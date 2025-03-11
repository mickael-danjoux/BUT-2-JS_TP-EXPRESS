# Refactorisation avec Express Router

Pour mieux organiser notre code, nous allons utiliser Express Router. Voici les étapes à suivre :

**1. Créez une structure de dossiers**

-   Créez un dossier `routes` pour vos routes
-   Créez un dossier `middlewares` pour vos middlewares

**2. Réorganisez les middlewares**

-   Dans le dossier `middlewares`, créez un fichier `auth.middleware.js`
-   Déplacez-y la fonction de vérification d'authentification
-   N'oubliez pas d'exporter la fonction

**3. Créez des routes modulaires**

Dans chacun des fichiers, vous devrez maintenant importer Router et exporter en fin de fichier:

```javascript
// routes/users.router.js
import  {  Router  }  from  'express'; 
const router =  Router();

router.get('/', (req, res) => {});
router.get('/:id', (req, res) => {});

export default router;

//index.js
import userRoutes from './routes/users.router.js';
const app = express();
app.use('/api/users', userRoutes);
``` 

-   Dans `routes`, créez deux fichiers : `users.routes.js` et `forms.routes.js`
-   Dans `users.routes.js`, créez un router pour gérer :
    -   La récupération d'un utilisateur (GET)
    -   La création d'un utilisateur (POST)
    -   La modification d'un utilisateur (PUT)
    -   La suppression d'un utilisateur (DELETE)
-   Dans `forms.route.js`, gérez :
    -   La soumission du formulaire (POST)

**4. Points techniques importants**

-   Utilisez `express.Router()`
-   Importez correctement vos middlewares

**5. Modification du fichier principal**

-   Importez vos routers
-   Utilisez `app.use()` pour les connecter
-   Définissez un préfixe pour chaque router

**6. Tests à effectuer**

-   Vérifiez que toutes vos anciennes routes fonctionnent avec les nouveaux chemins
-   Testez l'authentification
-   Vérifiez le formulaire

Le but est d'avoir un code plus maintenable et plus professionnel, tout en conservant les fonctionnalités existantes.
