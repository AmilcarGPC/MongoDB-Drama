# MongoDB-Drama

![MongoDB Logo](https://www.skillfinder.com.au/media/wysiwyg/mongodb-logo-skill-finder.png)

Explora y practica MongoDB con este repositorio diseñado para aprender los fundamentos y avanzados conceptos de esta base de datos NoSQL. Incluye un ejercicio práctico para consolidar tus habilidades.

## Contenido

- [Descripción_del_dataset](#Descripción_del_dataset)
- [Descripción_del_diccionario_de_datos_del_dataset](#Descripción_del_diccionario_de_datos_del_dataset)
- [Descripción_del_modelado_del_dataset](#Descripción_del_modelado_del_dataset)
- [Descripción_de_la_BD_NoSQL_y_las_herramientas_que_se_utilizaron](#Descripción_de_la_BD_NoSQL_y_las_herramientas_que_se_utilizaron)
- [Descripción_de_la_importación_de_sus datos](#Descripción_de_la_importación_de_sus_datos)
- [Definir_y_describir_al_menos_5_sentencias_para_cada_una_de_las_operaciones_CRUD_(Create,_Read,_Update,_Delete)_en_la_BD](#Definir_y_describir_al_menos_5_sentencias_para_cada_una_de_las_operaciones_CRUD_(Create,_Read,_Update,_Delete)_en_la_BD)

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

## Definir_y_describir_al_menos_5_sentencias_para_cada_una_de_las_operaciones_CRUD_(Create,_Read,_Update,_Delete)_en_la_BD

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

3. Para añadir un nuevo Cliente a la base de datos: Los clientes tienen una Address_ID como parte de sus atributos, el cual los relaciona con el arreglo de documentos Addresses, para saber su dirección, por lo que primero hay que crear una nueva Address (Direccion) para hacer referencia a esta.

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

