# Installer Express js  
  
```shell  
npm install express
```  
  
  
## Instancier le serveur (fichier index.js)  
  
### Initialisation du serveur  
  Nous allons créer une instance d’express afin qu’il écoute les requetes entrantes sur le port **3000**.

**Ajoutez ce code dans le fichier `index.js`.**
```javascript  
import express from 'express'  
  
const app = express()  
const port = 3000  
  
app.listen(port, () => {  
  console.log(`Hello World! I’m an API running on port ${port}`)  
})
```  
  
### Execution du fichier `index.js`  
  
Pour indiquer à node d’exécuter notre fichier et lancer le serveur, nous allons rajouter une commande dans la  partie `scripts` du fichier `packages.json`  
 
 **Ajoutez ce code dans les scripts du fichier `packages.json`.**
```json  
{  
 "start": "node index.js"
}  
```  
  
**Exécutez la commande suivante dans un terminal.**
  
```shell  
npm start
```  

**Question:**  Que voyez-vous s’afficher dans la console ?


L’API est disponible sur [http://127.0.0.1:3000]()

**Question:** Que voyez-vous s’afficher dans le navigateur?

**Question:** Pourquoi l’API renvoie-t-elle cette réponse ?
