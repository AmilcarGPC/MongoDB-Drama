# MongoDB-Drama

![MongoDB Logo](https://www.skillfinder.com.au/media/wysiwyg/mongodb-logo-skill-finder.png)

Explora y practica MongoDB con este repositorio diseñado para aprender los fundamentos y avanzados conceptos de esta base de datos NoSQL. Incluye un ejercicio práctico para consolidar tus habilidades.

## Contenido

- [Descripción_del_dataset](#Descripción_del_dataset)
- [Descripción_del_diccionario_de_datos_del_dataset](#Descripción_del_diccionario_de_datos_del_dataset)
- [Descripción_del_modelado_del_dataset](#Descripción_del_modelado_del_dataset)
- [Descripción_de_la_BD_NoSQL_y_las_herramientas_que_se_utilizaron](#Descripción_de_la_BD_NoSQL_y_las_herramientas_que_se_utilizaron)
- [Descripción_de_la_importación_de_sus datos](#Descripción_de_la_importación_de_sus_datos)
- [Definir_y_describir_al_menos_5_sentencias_para_cada_una_de_las_operaciones_CRUD_en_la_BD](#Definir_y_describir_al_menos_5_sentencias_para_cada_una_de_las_operaciones_CRUD_en_la_BD)

## Descripción_del_dataset

El dataset contiene información sobre diferentes entidades relacionadas con un negocio de fotografía y dramaturgia, así como productos asociados. Cada entidad tiene sus propios atributos y se identifica por un código o un ID, algunas otras se relacionan entre sí mediante claves foráneas. Este dataset sirve para muchas cosas en el negocio, como saber más de los clientes, los servicios, las reservas y el dinero que entra y sale. Además, ayuda a la gestión de clientes, pues proporciona un gran panorama sobre el contacto, las preferencias y los pedidos realizados con anterioridad (incluye información sobre tipos de servicios, precios y asignación de recursos).  En términos de contabilidad y finanzas, registra transacciones financieras, métodos de pago y detalles de facturación. También ayuda a controlar los productos que hay (rastreando reservas, órdenes y detalles de facturación), los artistas que trabajan y las zonas donde se ofrece el negocio. Con este dataset se puede hacer análisis para mejorar el negocio, conocer el mercado, planear el futuro y satisfacer al público. 

## Descripción_del_diccionario_de_datos_del_dataset

### Ref_Payment_Methods
Contiene información sobre métodos de pago.

*Ejemplo*: Método de pago "American E" con descripción "credit"
| ATTRIBUTE NAME            | payment_method_code         | payment_method_description   |
|:-------------------------:|:---------------------------:|:-----------------------------:|
| CONTENTS                        | Código del método de pago      | Descripción del método      |
| TYPE                                 | String                                        | String                                 |
| REQUIRED                      | Y                                              | Y                                          | 
| PK or FK                        | PK                                           |                                               |
| FK  REFERENCED TABLE |                                              |                                               |

### Ref_Service_Types
Describe tipos de servicios.

*Ejemplo*: Servicio de código "1" que implica proporcionar un servicio fotográfico.
| ATTRIBUTE NAME           | Service_Type_Code        | Parent_Service_Type_Code       | Service_Type_Description |
|:------------------------:|:------------------------:|:--------------------------------:|:----------------------------------:|
| CONTENTS                       | Código del tipo de servicio      | Código del tipo de servicio principal      | Descrición del tipo de servicio
| TYPE                                | String                                       | String                                                 | String                                              |
| REQUIRED                     | Y                                              | Y                                                           | Y                                                       |
| PK or FK                       | PK                                            |                                                              |                                                              |
| FK  REFERENCED TABLE |                                              |                                                               |                                                              |

### Addresses
Almacena información de direcciones.

*Ejemplo*: Dirección con ID "110" en "4753 Dach Highway, Suite 846, Feliciaberg, Florida".
| ATTRIBUTE NAME        | Address_ID             | Line_1                            | Line_2                        | City_Town                     | State_County                |
|:---------------------:|:----------------------:|:----------------------------------:|:------------------------------:|:------------------------------:|:----------------------------:|
| CONTENTS                   | ID de la dirección     | Línea 1 de la dirección      | Línea 2 de la dirección  | Ciudad o Pueblo        | Estado o Condado       |
| TYPE                           | String                          | String                                  | String                             | String                              | String                           |
| REQUIRED                 | Y                                | Y                                        |  Y                                    | Y                                        | Y                                   |
| PK or FK                   | PK                             |                                              |                                      |                                           |                                      |
| FK  REFERENCED TABLE |                                  |                                              |                                      |                                           |                                      |

### Products
Contiene detalles sobre productos.

*Ejemplo*: Producto con ID "11" llamado "photo" con precio "4448536".
| ATTRIBUTE NAME    | Product_ID          | Product_Name         | Product_Price     |
|:-----------------:|:-------------------:|:---------------------:|:-----------------:|
| CONTENTS               | ID del producto      | Nombre del producto | Precio del producto |
| TYPE                       | String                      | String                        | Decimal                    |
| REQUIRED             | Y                              | Y                                | Y                               |
| PK or FK               | PK                            |                                   |                                   |
| FK  REFERENCED TABLE |                                 |                                   |                                   |

### Marketing_Regions
Representa regiones de marketing.

*Ejemplo*: Región de marketing "CA" (Canadá) con descripción "Our target market".
| ATTRIBUTE NAME            | Marketing_Region_Code     | Marketing_Region_Name | Marketing_Region_Descriptrion |
|:-------------------------:|:--------------------------:|:------------------------:|:--------------------------------:|
| CONTENTS                        | Código de la región            | Nombre de la región   | Descripción de la región
| TYPE                                 | String                                     | String                             | String
| REQUIRED                      | Y                                           | Y                                      | 
| PK or FK                        | PK                                        |                                            |
| FK  REFERENCED TABLE |                                            |                                            |

### Clients
Información sobre clientes.

*Ejemplo*: Cliente con ID "423" llamado "Clifford" en "branson94@example.net".
| ATTRIBUTE NAME              | Client_ID               | Address_ID                  | Customer_Email_Address      | Customer_Name       | Customer_Phone                 | Other_Details    |
|:---------------------------:|:-----------------------:|:---------------------------:|:----------------------------:|:-------------------:|:--------------------------------:|:----------------:|
| CONTENTS                          | ID del cliente            | ID de la dirección      | Correo electrónico del cliente | Nombre del cliente | Número de teléfono del cliente | Otros detalles   |
| TYPE                                 | Integer                       | Integer                          | String                                       | String                     | String                                      | String                  |
| REQUIRED                       | Y                                  | Y                                    | Y                                                | Y                             | Y                                               |                                      |
| PK or FK                         | PK                               | FK                                    |                                                    |                                |                                                  |                                      |
| FK  REFERENCED TABLE |                                      | Addresses (Address_ID)                   |                                                  |                                |                                                  |                                      |

### Drama_Workshop_Groups
Detalles sobre grupos de talleres de drama.

*Ejemplo*: Grupo con ID "136" en "Amely Cafe" en la región de marketing "FR".
| ATTRIBUTE NAME                 | Workshop_Group_ID     | Address_ID                   | Currency_Code            | Marketing_Region_Code | Store_Name              | Store_Phone                | Store_Email_Address         | Other_Details    |
|:------------------------------:|:----------------------:|:-----------------------------:|:------------------------:|:----------------------:|:-----------------------:|:-----------------------------:|:-----------------------------:|:----------------:|
| CONTENTS                           | ID del grupo              | ID de la dirección     | Código de moneda    | Código de la región   | Nombre de la tienda  | Teléfono de la tienda    | Correo electrónico de la tienda  | Otros detalles   |
| TYPE                                  | Integer                       | Integer                         | String                      | String                         | String                     | String                               | String | String                  |                              |
| REQUIRED                        | Y                                 | Y                                 | Y                               | Y                                  | Y                              | Y                                       | Y                                       |  |
| PK or FK                          | PK                              | FK                                   |                                   | FK                                       |                                     |                                         |                                         | |
| FK  REFERENCED TABLE  |                                     | Addresses (Address_ID)                  |                                   | Marketing_Regions (Marketing_Region_Code)  |                                     |                                         |                                         | |

### Performers
Datos sobre artistas o ejecutantes.

*Ejemplo*: Artista con ID "153" llamado "Shawna" con información de contacto.
| ATTRIBUTE NAME            | Performer_ID          | Address_ID               | Customer_Name         | Customer_Phone     | Customer_Email_Address     | Other_Details    |
|:-------------------------:|:---------------------:|:------------------------:|:----------------------:|:-------------------:|:---------------------------:| :----------------:|
| CONTENTS                        | ID del artista         | ID de la dirección     | Nombre del artista   | Teléfono del artista | Correo electrónico del artista | Otros detalles   |
| TYPE                                 | Integer                     | Integer                        | String                       | String                     | String                               | String                  |
| REQUIRED                      | Y                              | Y                               | Y                                | Y                             | Y                                       | |
| PK or FK                        | PK                           | FK                               |                                   |                                |                                        | |
| FK  REFERENCED TABLE |                                  | Addresses (Address_ID)                 |                                   |                                   |                                        | |

### Customers
Detalles sobre clientes.

*Ejemplo*: Cliente con ID "240" llamado "Harold" con información de contacto.
| ATTRIBUTE NAME          | Customer_ID          | Address_ID               | Customer_Name       | Customer_Phone     | Customer_Email_Address | Other_Details    |
|:-----------------------:|:--------------------:|:------------------------:|:---------------------:|:-------------------:|:------------------------:| :----------------:|
| CONTENTS                     | ID del cliente        | ID de la dirección     | Nombre del cliente | Teléfono del cliente | Correo electrónico del cliente | Otros detalles   |
| TYPE                             | String                   | Integer                        | String                     | String                   | String                               | String                  |
| REQUIRED                   | Y                           | Y                                | Y                                | Y                             | Y                                       | |
| PK or FK                   | PK                        | FK                               |                                   |                                |                                        | |
| FK  REFERENCED TABLE |                             | Addresses (Address_ID)                  |                                   |                                   |                                        | |

### Stores
Información sobre tiendas.

*Ejemplo*: Tienda con ID "150" llamada "FJA Filming" en la región de marketing "IN".
| ATTRIBUTE NAME          | Store_ID               | Address_ID              | Marketing_Region_Code | Store_Name            | Store_Phone             | Store_Email_Address  | Other_Details    |
|:-----------------------:|:----------------------:|:------------------------:|:----------------------:|:---------------------:|:-------------------------:|:----------------------:| :----------------:|
| CONTENTS                     | ID de la tienda       | ID de la dirección     | Código de la región   | Nombre de la tienda  | Teléfono de la tienda | Correo electrónico de la tienda | Otros detalles   |
| TYPE                             | String                   | Integer                        | String                       | String                     | String                             | String                           | String                  |
| REQUIRED                   | Y                           | Y                                | Y                               | Y                              | Y                                      | Y                                   | |
| PK or FK                   | PK                        | FK                               | FK                                   |                                   |                                      |                                        | |
| FK  REFERENCED TABLE |                             | Addresses (Address_ID)                  | Marketing_Regions (Marketing_Region_Code)  |                                   |                                      |                                        | |

### Bookings
Registra información sobre reservas.

*Ejemplo*: Reserva con ID "1" realizada por el cliente con ID "938" en la tienda con ID "8".
| ATTRIBUTE NAME        | Booking_ID            | Customer_ID        | Workshop_Group_ID | Status_Code        | Store_ID               | Order_Date            | Planned_Delivery_Date   | Actual_Delivery_Date    |
|:---------------------:|:---------------------:|:------------------:|:-----------------:|:------------------:|:-----------------------:|:----------------------:|:------------------------:|:-------------------------:|
| CONTENTS                   | ID de la reserva   | ID del cliente    | ID del grupo         | Código de estado | ID de la tienda       | Fecha de la orden  | Fecha de entrega planificada | Fecha de entrega real     |
| TYPE                           | Integer                   | Integer                  | String                  | String                   | Integer                        | Date                          | Date                             | Date                             |
| REQUIRED                 | Y                           | Y                           | Y                           | Y                           | Y                                 | Y                                | Y                                   | Y                                     |
| PK or FK                 | PK                        | FK                                | FK                                |                                | FK                                     |                                    |                                      |                                      |
| FK  REFERENCED TABLE |                             | Customers (Customer_ID)          | Drama_Workshop_Groups (Workshop_Group_ID) |                                | Stores (Store_ID)                      |                                   |                                    |                                    |

### Performers_in_Bookings
Relaciona artistas con reservas.

*Ejemplo*: Artista con ID "153" en la reserva con ID "1".
| ATTRIBUTE NAME           | Order_ID               | Performer_ID      |
|:------------------------:|:----------------------:|:------------------:|
| CONTENTS                      | ID de la orden     | ID del artista   |
| TYPE                              | Integer                  | Integer                |
| REQUIRED                    | Y                          | Y                          |
| PK or FK                    | PK                        | FK                            |
| FK  REFERENCED TABLE | | Performers (Performer_ID)         |

### Customer_Orders
Detalles sobre órdenes realizadas por clientes.

*Ejemplo*: Orden con ID "1" realizada por el cliente con ID "516" en la tienda con ID "231".
| ATTRIBUTE NAME           | Order_ID               | Customer_ID        | Store_ID              | Order_Date            | Planned_Delivery_Date   | Actual_Delivery_Date    |
|:------------------------:|:----------------------:|:------------------:|:---------------------:|:----------------------:|:------------------------:|:-------------------------:|
| CONTENTS                      | ID de la orden     | ID del cliente    | ID de la tienda       | Fecha de la orden  | Fecha de entrega planificada | Fecha de entrega real     |
| TYPE                              | Integer                  | Integer                | Integer                       | Date                          | Date                              | Date                              |
| REQUIRED                    | Y                          | Y                          | Y                               | Y                                | Y                                    |  Y                                    |
| PK or FK                    | PK                       | FK                            | FK                                 |                                    |                                       |                                      |
| FK  REFERENCED TABLE |                              | Customers (Customer_ID)         | Stores (Store_ID)                     |                                   |                                       |                                       |

### Order_Items
Detalles sobre los artículos de una orden.

*Ejemplo*: Ítem con ID "1" en la orden con ID "3", que incluye el producto con ID "233".
| ATTRIBUTE NAME            | Order_Item_ID       | Order_ID               | Product_ID            | Order_Quantity      |
|:-------------------------:|:-------------------:|:----------------------:|:---------------------:|:-------------------:|
| CONTENTS                     | ID del ítem         | ID de la orden     | ID del producto    | Cantidad de la orden  |
| TYPE                             | Integer                  | Integer                  | Integer                       | String                     |
| REQUIRED                   | Y                          | Y                          | Y                               | Y                                |
| PK or FK                   | PK                       | FK                            |  FK                               |                                    |
| FK  REFERENCED TABLE |                              | Customer_Orders (Order_ID) | Products (Product_ID)                  |                                    |

### Invoices
Información detallada sobre facturas.

*Ejemplo*: Factura con ID "128" relacionada con la orden con ID "14" y utilizando el método de pago "MasterCard".
| ATTRIBUTE NAME           | Invoice_ID           | Order_ID               | payment_method_code   | Product_ID            | Order_Quantity      | Order_Item_ID       |
|:------------------------:|:---------------------:|:----------------------:|:----------------------:|:---------------------:|:-------------------:|:-------------------:|
| CONTENTS                      | ID de la factura   | ID de la orden     | Código del método de pago | ID del producto    | Cantidad de la orden  | ID del ítem         |
| TYPE                              | Integer                  | Integer                  | String                          | Integer                       | String                     | Integer                     |
| REQUIRED                    | Y                          | Y                          | Y                                | Y                               | Y                                | Y                               |
| PK or FK                    | PK                       |  FK                           |  FK                                  |     FK                             |                                   |   FK                                |
| FK  REFERENCED TABLE |                              | Customer_Orders (Order_ID) | Ref_Payment_Methods (payment_method_code) | Products (Product_ID)             |                                    | Order_Items (Order_Item_ID)            |

### Services
Detalles sobre servicios ofrecidos.

*Ejemplo*: Servicio con ID "191" del tipo "film" con precio "58932775.8822".
| ATTRIBUTE NAME           | Service_ID           | Service_Type_Code  | Workshop_Group_ID   | Product_Name         | Product_Price     |
|:------------------------:|:---------------------:|:---------------------:|:---------------------:|:---------------------:|:-----------------:|
| CONTENTS                      | ID del servicio    | Código del tipo de servicio | ID del grupo         | Nombre del producto | Precio del producto |
| TYPE                              | Integer                  | String                          | Integer                  | String                     | Decimal                   |
| REQUIRED                    | Y                          | Y                                | Y                              | Y                               | Y                               |
| PK or FK                    | PK                       | FK          | FK                             |                |                                 |
| FK  REFERENCED TABLE |                              | Ref_Service_Types (Service_Type_Code)                             | Drama_Workshop_Groups (Workshop_Group_ID) |                                    |                                   |

### Bookings_Services
Relaciona reservas con servicios.

*Ejemplo*: Reserva con ID "1" y producto con ID "396".
| ATTRIBUTE NAME           | Order_ID               | Product_ID            |
|:------------------------:|:---------------------:|:---------------------:|
| CONTENTS                      | ID de la orden     | ID del producto    |
| TYPE                              | Integer                  | Integer                      |
| REQUIRED                    | Y                          | Y                              |
| PK or FK                    | FK                       | FK                                 |
| FK  REFERENCED TABLE |     Customer_Orders (Order_ID)  | Products (Product_ID)                 |

### Invoice_Items
Detalles sobre los artículos de una factura.

*Ejemplo*: Ítem con ID "1" en la factura con ID "128" relacionado con la orden con ID "1" y el producto con ID "396".
| ATTRIBUTE NAME            | Invoice_Item_ID      | Invoice_ID           | Order_ID               | Order_Item_ID       | Product_ID            | Order_Quantity      | Other_Item_Details |
|:-------------------------:|:-------------------:|:---------------------:|:----------------------:|:-------------------:|:---------------------:|:-------------------:| :-------------------:|
| CONTENTS                      | ID del ítem         | ID de la factura   | ID de la orden     | ID del ítem         | ID del producto    | Cantidad de la orden  | Otros detalles del ítem |
| TYPE                              | Integer                  | Integer                  | Integer                  | Integer                     | Integer                       | Integer                     | String |
| REQUIRED                    | Y                          | Y                          | Y                          | Y                               | Y                                 | Y                               | |
| PK or FK                    | PK                       | FK                             | FK                               | FK                                |FK                                    |                                   | |
| FK  REFERENCED TABLE |                              | Invoices (Invoice_ID)               | Customer_Orders (Order_ID)  | Order_Items (Order_Item_ID)             | Products (Product_ID)                 |              | |

## Descripción_del_modelado_del_dataset


## Descripción_de_la_BD_NoSQL_y_las_herramientas_que_se_utilizaron

## Descripción_de_la_importación_de_sus_datos

## Definir_y_describir_al_menos_5_sentencias_para_cada_una_de_las_operaciones_CRUD_en_la_BD

## Create
1. Para añadir un nuevo método de pago al sistema. (Crear un nuevo documento en el arreglo de documentos Ref_Payment_Methods)

![Imagen_1](https://i.ibb.co/N14zKpP/MDB1.png)
Originalmente hay tres métodos de pago en el sistema. Ingresamos la siguiente sentencia CRUD en el Shell de MongoDB Compass:
```
db.drama.updateOne(
  { "_id": ObjectId("656bea965b9551f20b20a053") },
  { 
    $push: {
      "Ref_Payment_Methods": {
        "payment_method_code": "Efectivo",
        "payment_method_description": "Ahora se puede pagar con efectivo"
      }
    }
  }
)
```
Podemos ver los cambios reflejados en la base de datos:
![Imagen_2](https://i.ibb.co/VV5YpNJ/MDB2.png)

2. Para añadir nuevas regiones en las que se podrán hacer negocios, originalmente el dataset maneja 8 regiones:

![Imagen_3](https://i.ibb.co/0YhR6TB/MDB3.png)
Para añadir una nueva región como Yucatán por ejemplo usamos la siguiente sentencia:
```
db.drama.updateOne(
  { "_id": ObjectId("656bea965b9551f20b20a053") },
  { 
    $push: {
      "Marketing_Regions": {
        "Marketing_Region_Code": "YU",
        "Marketing_Region_Name": "Merida Yucatan",
        "Marketing_Region_Description": "Mercado local"
      }
    }
  }
)
```
Podemos ver los cambios reflejados en el dataset: hemos creado una nueva región.
![Imagen_4](https://i.ibb.co/rFShyhP/MDB4.png)

3. Para añadir un nuevo Cliente a la base de datos: Los clientes tienen una Address_ID como parte de sus atributos, el cual los relaciona con el arreglo de documentos Addresses, para saber su dirección, por lo que primero hay que crear una nueva Address (Dirección) para hacer referencia a esta.

Usamos el siguiente comando para añadir una nueva Address al dataset:
```
db.drama.updateOne(
  { "_id": ObjectId("656bea965b9551f20b20a053") },
  { 
    $push: {
      "Addresses": {
        "Address_ID": "973",
        "Line_1": "Avenida 7",
        "Line_2": "Numero 345 entre 21 y 23",
        "City_Town": "Merida",
        "State_County": "Yucatan"
      }
    }
  }
)
```
Después usamos el siguiente comando para añadir un nuevo cliente con la Address_ID : 973 el cual hace referencia a la Address que acabamos de crear:
```
db.drama.updateOne(
  { "_id": ObjectId("656bea965b9551f20b20a053") },
  { 
    $push: {
      "Clients": {
	"Client_ID": "223",
        "Address_ID": "973",
        "Customer_Email_Address": "safs99@hotmail.com",
	"Customer_Name": "Gerardo",
	"Customer_Phone": "9992602264"
      }
    }
  }
)
```
Como podemos ver se ha añadido un nuevo cliente al dataset: 
![Imagen_5](https://i.ibb.co/2gH8SpD/MDB5.png)

4. Para crear un nuevo grupo de practica de Drama ingresamos la siguiente sentencia:

```
db.drama.updateOne(
  { "_id": ObjectId("656bea965b9551f20b20a053") },
  { 
    $push: {
      "Drama_Workshop_Groups": {
        "Workshop_Group_ID": "966",
        "Address_ID": "973",
        "Currency_Code": "MXN",
        "Marketing_Region_Code": "YU",
        "Store_Name": "Grupo de dramatizacion Pensiones",
        "Store_Phone": "9827382",
        "Store_Email_Adresss": "dramapensiones@gmail.com"
      }
    }
  }
)
```

5. Para añadir un nuevo producto al dataset usamos la siguiente sentencia CRUD:

```
db.drama.updateOne(
  { "_id": ObjectId("656bea965b9551f20b20a053") },
  { 
    $push: {
      "Products": {
        "Product_ID": "332",
        "Product_Name": "Cursos de improvisacion",
        "Product_Price": 460
      }
    }
  }
)
```
### Read

1. Para leer todos los documentos que existen en el dataset usamos la siguiente sentencia:

```
db.drama.find({})
```
Al no marcar ningún filtro de búsqueda entre las llaves este comando nos devuelve todos los documentos que encuentra en la base de datos drama, incluyendo los anidados.
![Imagen_6](https://i.ibb.co/5YDXnkJ/MDB6.png)
Como podemos observar la salida es muy grande.

2. Para leer el arreglo de documentos que incluye los documentos con todos los Métodos de pago usamos la siguiente sentencia:

```
db.drama.aggregate([
  {
    $project: {
	"_id": 0,  //para que no nos muestre la ID del objeto
	"Ref_Payment_Methods": 1   // para que nos muestre solo los métodos de pago
    }
  }
])
```
El método aggregate de MongoDB nos permite trabajar con arreglos de objectos y el comando $project: nos define que solo nos muestre los contenidos del arreglo Ref_Payment_Methods:
![Imagen_7](https://i.ibb.co/B3CXRTb/MDB7.png)
Como podemos observar la salida nos muestra las cuatro colecciones que se encuentran en el arreglo de colecciones de Ref_Payment_Methods.

3. Para leer todos los Grupos de Drama que estén en Yucatán: Podemos realizar una búsqueda sobre el arreglo de colecciones Drama_Workshop_Groups el cual contiene todas las colecciones con la información de los Grupos de Drama, y filtrar los resultados que tengan como uno de sus valores la región YU con la siguiente sentencia:

```
db.drama.aggregate([
  {
    $project: {
      "_id": 0, 
      "Drama_Workshop_Groups": {
        $filter: {
          input: "$Drama_Workshop_Groups",
          as: "region",
          cond: {
            $eq: ["$$region.Marketing_Region_Code", "YU"]
          }
        }
      }
    }
  }
])
```
El comando $filter nos ayuda a filtrar los resultados, solo regresando los cuales cumplan la condición de que su región (Marketing_Region_Code) sea igual a “YU”, gracias al comando $eq:
![Imagen_8](https://i.ibb.co/3S56KSt/MDB8.png)
Podemos observar que en la terminal solo nos regresó una colección que cumple la condición, la cual fue el Grupo de Drama que añadimos anteriormente en las sentencias Create.

4. Para ver todas las Facturas que fueron pagadas con MasterCard. Usamos el siguiente comando para filtrar entre el arreglo de Facturas las que fueron pagadas con MasterCard y mostrar estas facturas que cumplen la condición:

```
db.drama.aggregate([
  {
    $unwind: "$Invoices"
  },
  {
    $match: {
      "Invoices.payment_method_code": "MasterCard"
    }
  },
  {
    $group: {
      _id: "$_id",
      Invoices: { $push: "$Invoices" }
    }
  },
  {
    $project: {
      _id: 0,
      Invoices: 1
    }
  }
])
```
Usamos el comando $unwind para deconstruir el arreglo de Facturas(Invoices) en documentos individuales, luego usa el comando $match para solo tomar en cuenta las facturas que cumplen la condición de que su payment_method_code es MasterCard, después usa el comando $group junto con el comando $push para reconstruir el arreglo de Facturas que cumplen la condicion y finalmente el comando $project para regresar (leer) este nuevo arreglo de Facturas, ignorando su id.
![Imagen_9](https://i.ibb.co/xYY8R2t/MDB9.png)
Podemos observar que en la salida de la consola nos muestra todos los objetos (colecciones) del arreglo de colecciones Invoices que cumplen la condicion que su método de pago fue MasterCard. 

5. Para encontrar al cliente que se llama Gerardo. Usamos el siguiente comando:

```
db.drama.find(
  { },
  { "_id": 0, "Clients": { $elemMatch: { "Customer_Name": "Gerardo" } } }
)
```
Busca entre todos los documentos, al primer documento en la colección de documentos Clients que tenga como Customer_Name a Gerardo, podemos ver en la salida de la consola que si lo encontró (pues lo añadimos anteriormente)
![Imagen_10](https://i.ibb.co/vJDx189/MDB10.png)

### Update

1. Para actualizar el nombre de un Cliente. Para cambiar el nombre del cliente Gerardo a Gerardo Diaz usamos la siguiente sentencia update:

```
db.drama.updateOne( { "Clients.Customer_Name" : "Gerardo"},
                   {$set: { "Clients.$.Customer_Name" : "Gerardo Diaz"}})
```

2. Para actualizar el nombre del documento que contiene un arreglo de documentos en MongoDB usamos el siguiente comando:

```
db.drama.update(
  { }, 
  { $rename: { "Services": "Servicios" } },
  { multi: true } 
)
```
![Imagen_11](https://i.ibb.co/f2R2YJ2/MDB11.png)
Podemos observar en la imagen que ahora el documento que antes se llamaba Services ahora se llama Servicios y que el Cliente que antes tenía como nombre(Customer_Name) a Gerardo ahora tiene como nombre a Gerardo Diaz.

3. Para modificar algún servicio ya ingresado usamos la siguiente sentencia CRUD para modificar múltiples valores de un documento:

```
db.drama.updateOne( { "Servicios.Service_ID" : 421},
                   {$set: { "Servicios.$.Product_Name" : "fotos grupales",
															"Servicios.$.Product_Price": 1200}})
```
Usamos el método updateOne para actualizar el Servicio el cual se encuentra en el arreglo de documentos Servicios (le actualizamos el nombre anteriormente) cuyo Service_ID es igual a 421, y usamos el comando $set para establecerle nuevos valores a su Product_Name y Product_Price a “fotos grupales” y 1200 respectivamente.
![Imagen_12](https://i.ibb.co/0VV2Sbp/MDB12.png)
Podemos ver en la imagen que se reflejaron los cambios sobre el Servicio con ID 421 correctamente. 

4. Para actualizar el primer documento que cumpla con una condición usamos la siguiente sentencia:

```
db.drama.replaceOne(
  { "Clients.Customer_Name" : "Gerardo" },
  {
    "newField1": "new value 1",
    "newField2": "new value 2",
  }
)
```
A diferencia del método updateOne() el método replaceOne() solo va a actualizar el primer documento que cumpla con la condición establecida en las primeras llaves, después va a remplazar los valores del documento por los nuevos que le estamos dando en newField y new value.

5. Para actualizar el nombre de la colección en la que estamos trabajando usamos el siguiente comando:

```
db.drama.renameCollection("DramaCollection")
```
En donde drama es el nombre de la colección actual en la que estamos trabajando y en el parámetro de renameCollection() ponemos el nuevo nombre que le queremos poner. 

### Delete

1. Para eliminar un Cliente cuyo nombre sea igual a Gerardo Diaz usamos la siguiente sentencia:

```
db.DramaCollection.updateOne(
  { "Clients.Customer_Name": "Gerardo Diaz" },
  { $pull: { "Clients": { "Customer_Name": "Gerardo Diaz" } } }
)
```
Esta sentencia elimina un documento en el arreglo de Clients (Clientes) usando el comando $pull el cual cumpla las condiciones, en este caso que su Customer_Name sea Gerardo Diaz. 

2. Para eliminar la descripción de un método de pago: MongoDB Compass nos permite eliminar valores ingresados a un documento directamente desde el GUI:

![Imagen_13](https://i.ibb.co/sJC7V7Y/MDB13.jpg)
Hay que hacer click en el botón que dice Edit document marcado en rojo.
![Imagen_14](https://i.ibb.co/jbWVFCN/MDB14.png)
Después en el botón que dice Remove field para eliminar un campo de un documento directamente desde la GUI.

3. Para eliminar el documento Servicios: Para eliminar un documento el cual contiene otros documentos anidados: Lo podemos hacer directamente desde el GUI también

![Imagen_15](https://i.ibb.co/V22hBGH/MDB15.png)
Después de seleccionar el botón de Edit document mostrado anteriormente, hay que seleccionar el botón Remove field marcado en rojo alado del documento que queramos eliminar, en este caso Servicios. Esta operación va a remover los 15 documentos anidados dentro del documento Servicios.
![Imagen_16](https://i.ibb.co/2N2qT9n/MDB16.png)
Para confirmar los cambios hay que presionar en el botón UPDATE.

4. Para eliminar el documento en el que se encuentran anidados todos los demás documentos: Se puede hacer directamente desde el GUI también, hay que presionar el botón que dice Remove document marcado en rojo para realizar esta operación.

![Imagen_17](https://i.ibb.co/7XjCgLr/MDB17.png)
Y finalmente presionar el botón DELETE para confirmar los cambios y eliminar el documento.
![Imagen_18](https://i.ibb.co/6WP4BV8/MDB18.png)

5. Para eliminar la colección en la que estamos trabajando: usamos la sentencia db.collection.drop() donde collection es el nombre de la colección que queremos eliminar, en nuestro caso será:

```
db.DramaCollection.drop()
```
También se puede hacer desde la GUI de Compass: 
![Imagen_19](https://i.ibb.co/8M20zdV/MDB19.png)
Hay que hacer clic en el botón con los tres puntos para desplegar el menú que contiene la opción Drop Collection.
![Imagen_20](https://i.ibb.co/fxG1f3D/MDB20.png)
Para confirmar es necesario escribir el nombre de la colección en la caja y hacer clic en el botón Drop Collection. 
