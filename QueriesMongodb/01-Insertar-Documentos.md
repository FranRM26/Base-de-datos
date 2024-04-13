# Insertar Documentos

---
_Insetar un solo documento_

```m
db.Alumnos.insertOne(
 {
  nombre : "Maximiliano"
});
```

_Insercion de un documento complejo con un Array_

```m
 db.Alumnos.insertOne( { nombre: "Rosa", 
 edad: 22, 
 apellido: "Cabeza de vaca" ,
 aficiones : [ "Paracaidismo", "Lectura",
 "Futbol"]
  })
```

_Insercion de Documentos con subdocumentos_

```m
 db.Alumnos.insertOne(
     {
    nombre: "Raul",
     edad: 67,
    cv: {
           "Informatica": "Bueno",
            "Marketing": "Bajo",
           "Contabilidad": "Medio"

   }
   })
```

_Insercion con ID Personalizado_

```m
 db.Alumnos.insertOne( {

   _id: 1, 
   "Nombre": "Arcadia"
   
    })
```

_Insertar Multiples Documentos_

```m
db.Alumnos.insertMany( 
  [ 
    { 
      _id:2, 
      nombre: "Diana", 
      }, 
      { 
        _id:3, 
        nombre: "Flor", edad: 43 }, { _id:4, nombre: "Francisco Jesus Uriel", edad: 34, aficion: "El agua Bendita", desgracia: "La ex" } ]);

```