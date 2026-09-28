# Ejercicio 1

Una tienda necesita de un sistema `CRUD` donde debes almacenar los datos en un diccionario con el nombre `productos`

## Requisitos

- Debe de haber un menú con estas opciones:

    1. Agregar Producto
    2. Listar productos
    3. Modificar Producto
    4. Eliminar producto
    5. Salir

- Los Datos los debes de guardar en un diccionario con la siguiente estructura: 

    ```json
        {
            "1": {
                "nombre": "tortrix",
                "precio": 2.00,
                "stock": 10
            }, 
            "2": {
                "nombre": "coca-cola",
                "precio": 5.00,
                "stock": 15
            }
        }
    ```

- La opción `1. Agregar producto` debes perdirle al usuario que ingrese el nombre, el precio y el stock del nuevo producto.

- La opción `2. Listar productos`  debe listar y mostrar los productos de la siguiente manera: 

    ```bash
        --> Producto No.1
        Nombre: Tortrix
        precio: Q2.00
        stock: 10
    ```

- La opción `3. Modificar producto` para esta opcion solo se podra modificar el stock de un producto con el id del producto

- La opción `4. Eliminar producto` debe pedirle el id del producto al usuario para poder eliminarlo 