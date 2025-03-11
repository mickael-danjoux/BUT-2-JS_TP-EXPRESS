# Express.js

## Requis 
- [node](https://nodejs.org/fr/download)

## Créer un projet Node

Créer un projet node avec la commande ci-dessous.  

```shell
npm init
```

#### Compléter les valeurs demandées.  
#### Indiquer ``module`` pour le ``type`` de projet.


## Installer Express js

```shell
npm install express
```

## TP

### Première étape (fichier index.js)
- Initialisation du serveur
```javascript
import express from 'express'

const app = express()

app.listen(3000, () => {
  console.log('Server is listening on port 3000 !')
})

```
