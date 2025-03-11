# Première route
Maintenant que le serveur est lancé et écoute sur le port **3000**, nous allons pouvoir créer des routes.

**Ajoutons ce code dans le fichier `index.js`**
```javascript
app.get('/', (req, res) => {  
  res.send('Hello World!')  
})
```

**Rechargez la page  [http://127.0.0.1:3000]().**

**Question:** Que ce passe-t-il ?


Il faut en effet redémarrer le serveur Node puisque la nouvelle route n’était pas présente au moment où le serveur s’est lancé.

**Redémarrez le serveur.**

**Question:**  Que voyez-vous dans le navigateur ?

Pour éviter de devoir redémarrer le serveur à chaque modification, nous allons mettre en place un redémarrage automatique. Nous utilisons [nodemon](https://nodemon.io/) afin d’observer les changements dans notre code.

**Installez nodemon**
```shell
npm install -D nodemon
```
**-D** est utilisé pour indiquer que cette dépendance ne sert que pour le développement et ne sera pas installée lors du déploiement en production.

**Ajoutez la commande suivante dans les scripts  `packages.json`**
```json
{
	"dev":"nodemon index.js"
}
```

**Arrêtez le serveur**

**Lancez le mode dev**

```shell
npm run dev
```

**Ajoutez une nouvelle route**

```javascript
app.get('/no-reload', (req, res) => {  
  res.send('It works!')  
})
```

La nouvelle page est directement disponible [http://127.0.0.1:3000/no-reload]()
