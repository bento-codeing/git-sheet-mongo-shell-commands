# Mongo Shell Commands

Cette "git sheet" regroupe toutes les commandes de bases utilisées dans le shell de MongoDB.

### Nettoyer le terminal Mongo
Pour nettoyer le terminal Mongo, nous utiliserons la commande suivante :
```markdown
> cls
```
#

### Lister nos bases de données
Cette commande permet de lister toutes les bases de données, incluant également les bases de
données contenant les metadata.
> Les bases de données telles que admin, config ou local contiennent les métadonnées concernant
la configuration du serveur, les utilisateurs et leurs rôles, etc.


La commande utilisée pour lister nos bases de données est : 
```markdown
> show dbs
```
#

### Créer une base de données
Il est possible de créer une base de données en l'utilisant simplement à travers la commande :
```markdown
> use "db_name"
```
#

### Créer une collection
You can create a collection by insert into it a new JSON object.
Il est possible de créer une collection en insérant un nouvel élément au format JSON à notre base de données :
```markdown
> db.collection_name.insertOne({foo: "bar"})
```
>Il est possible d'insérer un objet JSON sans utiliser les doubles quotes à l'unique condition
qu'il s'agisse d'une propriété clé.
Si il venait à s'agir d'une valeur de type string, les quotes auraient leur importance.
Il revient également au choix de l'utilisateur si il souhaite utiliser de simple ou double quotes.

> Ce sont des features uniquement fournient par MongoDB.
#

### Lister toutes les données d'une collection
Pour lister toutes les données présentes dans une collection, nous utiliserons la commande : 
```markdown
> db.collection_name.find()
```

> Il est possible de "prettify" le rendu d'une liste en chaînant notre méthod find() par une
autre méthod, la méthode pretty() : 

> > db.collection_name.find().pretty()
#

## CRUD Operation
### Create

### Read

### Update
##### Mettre à jour _**UN**_ unique élement

##### Mettre à jour plusieurs éléments

##### Remplacer un élément
### Delete
