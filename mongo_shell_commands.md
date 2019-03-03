# Mongo Shell Commands

Cette "cheat sheet" regroupe toutes les commandes de bases utilisées dans le shell de MongoDB.

## # _Les bases_

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


### Utiliser/Créer une base de données
Il est possible de créer une base de données en l'utilisant simplement à travers la commande :
```markdown
> use "db_name"
```
#


### Lister nos collections
La commande utilisée pour lister nos collections est : 
```markdown
> show collections
```
> Attention, il est important de pointer déjà sur une base de données
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




## # _Opérations CRUD_
### Create
##### Insérer une donnée
`insertOne(data, options)`

```markdown
> db.collection_name.insertOne({foo: bar})
```

##### Insérer plusieurs données
`insertMany(data, options)`

```markdown
> db.collection_name.insertMany([
{foo1: bar1}, 
{foo2: bar2}
])
```

> Cette méthode requiert un tableau en tant que paramètre `data`




### Read
##### Trouver une donnée
`findOne(filter, options)`

```markdown
> db.collection_name.findOne({foo: bar})
```
> Ici, notre filter itérera sur le premier élément dont la propriété foo sera égale à la valeur
bar.

##### Trouver plusieurs données
`find(filter, options)`

```markdown
> db.collection_name.findOne({foo: bar})
```
> Ici, notre filter itérera sur le premier élément dont la propriété foo sera égale à la valeur
bar.


### Update

##### Mettre à jour _**UN**_ unique élement
`updateOne(filter, data, options)`

```markdown
> db.collection_name.updateOne({foo: bar}, {$set: {a: "b"}})
```
> Ici, notre filter itérera sur le premier élément dont la propriété foo sera égale à la valeur
bar. Enfin, pour updater notre élément nous avons besoin d'un opérateur mongo tel que $set
pour préciser à MongoDB que nous souhaitons mettre à jour la propriété "a" de notre élément.

> À savoir que : si la propriété "a" ne venait à ne pas exister, MongoDB se permet de la rajouter
à notre élément.
 
 
##### Mettre à jour plusieurs éléments
`updateMany(filter, data, options)`

```markdown
> db.collection_name.updateMany({}, {$set: {a: "b"}})
```
> À savoir que : si un objet vide est passé à notre filter comme présenter ici, toutes les
données seront donc mises à jour.

##### Remplacer un élément
`replaceOne(filter, data, options)`




### Delete
##### Supprimer un élément
`deleteOne(filter, options)`

```markdown
> db.collection_name.deleteOne({foo: bar})
```
> Ici, notre filter itérera sur le premier élément dont la propriété foo sera égale à la valeur
bar.

##### Supprimer plusieurs éléments
`deleteMany(filter, options)`

Supprimer tous les éléments dont la propriété foo est égale à la valeur bar :
```markdown
> db.collection_name.deleteMany({foo: bar})
```
Supprimer tous les éléments :
```markdown
> db.collection_name.deleteMany({})
```



#
## # _Opérateurs_
#### Sélecteurs de requêtage (ou Query selectors)

##### Comparaison 
- `$gt` (greater than) : matches les valeurs plus grande que la valeur de base spécifiée
    ```
    db.collection_name.find({ age: {$gt: 18} })
    ``` 