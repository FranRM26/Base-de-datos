#Busquedas  Condicionales

# Operadores de Comparación

| Operador | Descripción | 
|-- | -- |
| $eq | igual|
| $gt | Mayor que |
| $gte | Mayor o Igual |
| $in | Buscar un elemento en array|
| $lt| Menor que|
| $lte| Menor o igual|
| $ne | Todos los elementos que no sean iguales |
| $nin | Ninguno de los valores del arreglo|


## Busquedas

_Selecciona todos los documentos de una colección_


```m
db.libros.find()
db.libros.find({})
```

_Seleccionar todos los documentos de la coleccion libros donde la editorial sea Biblio_

```m
db.libros.find({editorial: 'Biblio'})
```

_Seleccionar todos los documentos de la coleccion libros donde el precio sea igual a 25_


```m
db.libros.find({precio: 25 })

```
## Busquedas con operadores logicos

**Sintaxi**

```
{<columna>: {<operador>:<valor>}, ...}

```

_Seleccionar todos aquellos documentos de la coleccion libros donde el precio sea mayor a 25_

```m
db.libros.find({precio: {$gt:25}})

```

_Seleccionar aquellos documentos de la coleccion libros donde el precio sean mayores o iguales a 20_

```m
 db.libros.find({precio:{$gte:20}})
```

_Seleccionar aquellos documentos sea Biblio o Planeta_

```m
db.libros.find({editorial:{$in:['Biblio','Planeta']}})
```

## Recuperar una sola fila


_Seleccionar aquellos documentos que sean biblio o planeta pero mostrando solamente el primer documento encontrado_

```m
db.libros.findOne({editorial:{$in:['Biblio','Planeta']}})
```

```m
db.libros.findOne({})
```

# Operadores lógicos

| Operador | Descripcion | 
|-- | -- |
| $and | Operador And, Devuelve los documentos que cumplen todas las condiciones|
| $or | Operador OR, Devuelve los documentos que cumplen alguna condicion|
| $not | inverte el resultado de una condicion |
| $nor | Devuelve los documentos que no cumplen las condiciones |
| $exist | Devuelve los documentos que tengan un campo concreto |
| $type|  Selecciona los documentos si un campo pertenece a un tipo especifico|

### Operador AND

**Sintaxis**
```
db.collection.find({Condicion1,Condicion2})
```

```
db.colection.find({$and:[{Condicion1},{Condicion2}]})
```
_Seleccionar todos aquellos libros que valgan mas de 25 y cuya cantidad sea inferior a 15_

```m
db.libros.find({precio:{$gt:25},cantidad:{$lt:15}})
```

```m
db.libros.find({$and:[{precio:{$gt:25}},{cantidad:{$lt:15}}]})
```

```m
db.libros.find({$and:[{precio:{$gt:25}},{cantidad:{$lt:15}}, {editorial:{$eq:'Biblio'}}]})
```

### Operador OR

**Sintaxis:**

```m
db.colection.find({$or:[{Condicion1},{Condicion2}]})
```

_Seleccionar todos aquellos libros que valgan mas de 25 o cuya cantidad sea inferior a 15_

```m
db.libros.find({$or:[{precio:{ $gt:25 }},{cantidad:{$lt:15}}]})
```

### OR y AND combinadas

_Seleccionar los documentos de la editorial Biblio con precrio mayor a 40 o libros de la Editorial planeta con precio mayor a 30_

```m
db.libros.find(
    {$or:
    [{$and:[{editorial:'Biblio'}, {precio:{ $gt:40 }}]},
    {$and:[{editorial:'Planeta'},{precio:{$gt:30}}]}]})
```

