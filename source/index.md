---
title: "OmbuShop REST API: Referencia"

language_tabs:
  - http
  - shell

toc_footers:
  - <a href='http://www.ombushop.com/partners'>Registrate en OmbuShop</a>

includes:
  - errors

search: true
---

# Introducción

Bienvenido a la API REST de OmbuShop. Aquí puedes ver la documentación para
todos los endpoints de la API de OmbuShop.

# Para hacer pedidos

Para realizar pedidos a la API REST, se debe pasar la API key de tu tienda
como parámetro `secret`. La API key la encontrarás en el panel de administración
de tu tienda, en la sección ["Mi Cuenta"](https://secure.ombushop.com/admin/configurations).

# Productos

## Obtener todos los productos

```http
GET /api/products HTTPS/1.1
Host: secure.ombushop.com
```

```shell
curl "https://secure.ombushop.com/api/products?secret=abcdef1234567890"
```

> Devuelve un JSON con la siguiente estructura:

```json
[
  {
    "id": 120,
    "name": "Botas Leñador",
    "description": "Confeccionadas en gamuza",
    "created_at": "2015-06-25 14:43:51 -0300",
    "updated_at": "2015-07-03 17:17:40 -0300",
    "permalink": "botas-lenador",
    "deleted_at": null,
    "meta_description": "Descripción",
    "meta_keywords": "Palabras clave",
    "count_on_hand": 10,
    "seller_id": 24,
    "currency": "ARS",
    "images": [
      {
        "id": 15877,
        "viewable_id": 120,
        "viewable_type": "Product",
        "attachment_content_type": "image/jpg",
        "attachment_file_name": "0.jpg",
        "position": 1,
        "attachment_width": 836,
        "attachment_height": 494,
        "urls": {
          "mini": "http://s3.amazonaws.com/ombu_store_production/images/products/15877/mini/0.jpg",
          "small": "http://s3.amazonaws.com/ombu_store_production/images/products/15877/small/0.jpg",
          "product": "http://s3.amazonaws.com/ombu_store_production/images/products/15877/product/0.jpg",
          "original": "http://s3.amazonaws.com/ombu_store_production/images/products/15877/original/0.jpg"
        }
      }
    ],
    "variants": [
      {
        "id": 437,
        "product_id": 120,
        "sku": "PROD001",
        "price": "2050.0",
        "is_master": true,
        "count_on_hand": 10,
        "created_at": "2015-06-25T14:43:51-03:00",
        "updated_at": "2015-07-03T17:17:25-03:00",
        "wholesale_price": "1550.0"
      }
    ]
  },
  {
    "id": 121,
    "name": "Remera",
    "description": "<p>Remera blanca</p>",
    "created_at": "2015-06-25 14:43:51 -0300",
    "updated_at": "2015-07-03 17:17:40 -0300",
    "permalink": "remera",
    "deleted_at": null,
    "meta_description": "Descripción",
    "meta_keywords": "Palabras clave",
    "count_on_hand": 20,
    "seller_id": 24,
    "currency": "ARS",
    "variants": [
      {
        "id": 438,
        "product_id": 121,
        "sku": "PROD002",
        "price": "500.0",
        "is_master": true,
        "count_on_hand": 20,
        "created_at": "2015-06-25T14:43:51-03:00",
        "updated_at": "2015-07-03T17:17:25-03:00",
        "wholesale_price": "400.0"
      }
    ]
  }
]
```

Obtener un JSON con todos los productos y sus imágenes.

### Atributos de producto

Atributo | Descripción
--------- | -----------
id | Identificador del producto
name | Nombre del producto
description | Descripción del producto
created_at | Fecha de creación del producto
updated_at | Fecha de ultima información del producto
permalink | Nombre amigable utilizado para la URL del producto
deleted_at | Fecha de borrado del producto, si este hubiera sido borrado
meta_description | Descripción que puede ayudar a los buscadores web a tener informacion relevante sobre el producto
meta_keywords | Palabras clave que pueden ayudar en la búsqueda del producto
count_on_hand | Cantidad de unidades disponibles del producto
seller_id | Identificador del vendedor del producto
currency | Moneda utilizada por la tienda
images | Imágenes del producto

### Atributos de imagen

Atributo | Descripción
--------- | -----------
id | Identificador de la imagen
viewable_id | Identificador del producto/variante al que pertenece la imagen
viewable_type | Puede ser "Product" o "Variant"
attachment_content_type | Tipo de archivo de imagen (jpg, png, gif, etc.)
attachment_file_name | Nombre de archivo de la imagen
position | Posición de la imagen según su importancia, siendo 1 la posición más importante
attachment_width | Ancho de la imagen en píxeles
attachment_height | Altura de la imagen en píxeles
image_paths | URLs de las distintas versiones de la imagen, ordenadas por tamaño

### Atributos de variante

Atributo | Descripción
--------- | ----------
id | Identificador de la variante
product_id | Identificador del producto al que pertenece la variante
sku | Identificador ingresado por el administrador de la tienda para identificar al producto/variante (Stock-keeping unit)
price | Precio de la variante que se muestra al público
is_master | Al crear un producto, se crea tambien una variante que contiene algunos datos del producto. Este valor indica con un valor booleano si esta variante es la que se creo con el producto.
count_on_hand | Cantidad de unidades disponibles de la variante
created_at | Fecha de creación de la variante
updated_at | Fecha de ultima actualización de la variante
wholesale_price | Precio de la variante que se muestra a los usuarios mayoristas

### Pedido HTTP

`GET https://secure.ombushop.com/api/products?secret=abcdef1234567890`

### Parámetros de la URL

Parámetro | Descripción
--------- | -----------
secret | API key del vendedor, la encontrarás [aquí](https://secure.ombushop.com/admin/configurations).

# Categorías

## Obtener todas las categorías

```http
GET /api/taxons HTTPS/1.1
Host: secure.ombushop.com
```

```shell
curl "https://secure.ombushop.com/api/taxons?secret=abcdef1234567890"
```

> Devuelve un JSON con la siguiente estructura:

```json
[
  {
    "id": 15,
    "parent_id": null,
    "name": "Calzado",
    "created_at": "2015-07-03 13:03:27 -0300",
    "updated_at": "2015-07-03 13:03:27 -0300",
    "permalink": "calzado/"
  },
  {
    "id": 16,
    "parent_id": 15,
    "name": "Calzado Casual",
    "created_at": "2015-07-03 13:14:40 -0300",
    "updated_at": "2015-07-03 13:14:40 -0300",
    "permalink": "calzado/calzado-casual/"
  },
  {
    "id": 17,
    "parent_id": 15,
    "name": "Calzado Deportivo",
    "created_at": "2015-07-03 13:14:44 -0300",
    "updated_at": "2015-07-03 13:14:44 -0300",
    "permalink": "calzado/calzado-deportivo/"
  },
  {
    "id": 18,
    "parent_id": null,
    "name": "Remeras",
    "created_at": "2015-07-03 13:14:57 -0300",
    "updated_at": "2015-07-03 13:14:57 -0300",
    "permalink": "remeras/"
  }
]
```

Obtener un JSON con todas las categorías.

### Atributos de categoría

Atributo | Descripción
--------- | -----------
id | Identificador de la categoría
parent_id | Identificador de la categoría padre
name | Nombre de la categoría
created_at | Fecha de creación de la categoría
updated_at | Fecha de ultima actualización de la categoría
permalink | Nombre amigable utilizado para la URL de la categoría

### Pedido HTTP

`GET https://secure.ombushop.com/api/taxons?secret=abcdef1234567890`

### Parámetro de la URL

Parámetro | Descripción
--------- | -----------
secret | API key del vendedor, la encontrarás [aquí](https://secure.ombushop.com/admin/configurations).
