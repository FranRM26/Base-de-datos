# Ree,plazar Documento

## Sustituir un documento completo

```m
db.libros.replaceOne({_id:2}, {titulo:'De la tierra a la luna'}, {autor: 'Julio Verde'}, {editorial: 'Terra'}, {precio:100})
```

# Borrar Docuementos

_Dos metodos_

1. deleteOne()
2. delteMany()

**Eliminar todo el documento con id = 2**

```m
db.libros.deleteOne({_id:2})
```

**Eliminar todos los documentos donde la cantidad sea mayor a 150**

```m
 db.libros.deleteMany({cantidad:{$gt:150}})
```

# Expresiones Regulares

**Seleccionar todos los documentos que contengan  en el Titulo una t**

```m
db.libros.find({titulo:/t/})
```

**Seleccionar todos los documentos donde el titulo se encuentre la palabra JSON**

```m
db.libros.find({titulo:/JSON/})
```


**Seleccionar todos los documentos que en donde el titulo termine con la palabra tos**

```m
db.libros.find({titulo:/tos$/})
```

**Seleccionar todos los documentos en donde el titulo termine con una " j "**

```m
db.libros.find({titulo:/J$/})
```

## Operador $regex ##

**Seleccionar todos los documentos donde el titulo contenga la palabra para**

```m
db.libros.find({titulo: {$regex: 'para' }})
```
```m
db.libros.find({titulo: /para/ })
```
**Seleccionar todos los documentos donde el titulo contengan la palabra JSON pero que sea "case sensitive"**

```m
db.libros.find({titulo: {$regex:/JSON/, $options:"i"}})
```

**Seleccionar todos los documentos de la colección libros donde el titulo contenga la palabra "tos" al final y que sea "case sensitive"**

```
db.libros.find({titulo: {$regex:/tos/, $options:"i"}})
```

## Ver solo ciertas Columnas 

```
db.libros.find({},{titulo:1})
```

**Seleccionar todos los documentos de la editorial planetal, pero mostrando solamente el titulo y la editorial**

```m
db.libros.find({editorial:'Planeta'},{titulo:1, editorial:1,_id:0})
````

```m
db.libros.find({editorial:{$regex: /Planeta/, $options:"i"}},{titulo:1, editorial:1,_id:0})
```

### Operador $exists

_Permite buscar la existencia de un columa_

```m
db.libros.find({titulo:{$exists:true}}) 
```

```m
db.libros.find({titulo:{$exists:false}})
```

## Operador $type

```m
db.libros.find({precio:{$type:16}})
```

```m
db.libros.find({precio:{$type:1}})
```
```m
db.libros.find({precio:{$type:'double'}})
```

## Tabla de tipos de datos mongodb

Aquí tienes la tabla solicitada:

| Type             | Number | Alias      |
|------------------|--------|------------|
| Double           | 1      | "double"   |
| String           | 2      | "string"   |
| Object           | 3      | "object"   |
| Array            | 4      | "array"    |
| Binary data      | 5      | "binData"  |
| Undefined        | 6      | "undefined"|
| ObjectId         | 7      | "objectId" |
| Boolean          | 8      | "bool"     |
| Date             | 9      | "date"     |
| Null             | 10     | "null"     |
| Regular Expression | 11   | "regex"    |
| DBPointer        | 12     | "dbPointer"|
| JavaScript       | 13     | "javascript"|
| Symbol           | 14     | "symbol"   |
| 32-bit integer  | 16      | "int"      |
| Timestamp        | 17      | "timestamp"|
| 64-bit integer  | 18      | "long"     |
| Decimal128       | 19      | "decimal"  |
| Min key          | -1      | "minKey"   |
| Max key          | 127     | "maxKey"   |


## Operador $set

_Sirve para cambiar el valor de un campo dentro de la colección_

```m
db.libros.updateOne({titulo:'Java como Programas'}, {$set:{titulo:'Java como Programar'}})
```

**Actualizar el valor de la cantidad a 50 y el precio a 10 donde el  id = 9**

```m
db.libros.updateOne({precio:25, cantidad: 15}, {$set:{precio: 10, cantidad: 50, _id:9}})
```
```
db.libros.update({_id:9}, {$set:{canitdad:50, precio:10}})
```
**Actuliazar todos los documentos donde el precio sea mayor a 10 por el precio a 150**

```m
db.libros.updateMany({precio:{$gt:10}},{$set:{precio:150}})
```

## Operador $sort

**Ordenar todos los documentos de forma ascendente por la editorial y mostrar solamente titulo, precio y editorial**

```m
db.libros.find({}, {titulo:1, precio:1, editorial:1, _id:1}).sort({editorial:1})
```

```m
db.libros.find({}, {titulo:1, precio:1, editorial:1, _id:1}).sort({editorial:-1})
```