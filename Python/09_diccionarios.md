# 📖 Diccionarios

## ¿Para qué sirven?

Con las listas aprendiste a guardar varios valores en una sola variable. Pero mira este ejemplo:

```python
persona = ["Julián", 26, "Guatemala", True]
```

¿Qué significa el `26`? ¿Y el `True`? Para saberlo tendrías que recordar qué hay en cada posición. Con muchos datos, eso se vuelve muy confuso.

Los **diccionarios** resuelven esto: en lugar de usar posiciones (`0`, `1`, `2`...), cada valor tiene un **nombre** que dice qué es.

---

## ¿Qué es un diccionario?

Piensa en un **diccionario de verdad**: buscas una palabra y encuentras su significado. En Python funciona igual: buscas una **clave** y encuentras su **valor**.

Otra forma de verlo es como la **ficha de contacto** de tu celular:

| Clave | Valor |
|-------|-------|
| Nombre | Julián |
| Teléfono | 5555-1234 |
| Correo | julian@correo.com |

Cada dato tiene una etiqueta que dice qué es.

### ¿Cómo se crea?

Se usan llaves `{ }`. Cada elemento es una pareja `clave: valor`, separadas por comas:

```python
persona = {
    "nombre": "Julián",
    "edad": 26,
    "pais": "Guatemala",
    "activo": True
}
```

Ahora es clarísimo qué significa cada dato.

> 💡 Las claves casi siempre son textos (`str`) entre comillas. Los valores pueden ser de cualquier tipo: números, textos, booleanos, listas, e incluso otros diccionarios.

---

## Acceder a un valor

Escribes el nombre del diccionario y la **clave** entre corchetes:

```python
persona = {
    "nombre": "Julián",
    "edad": 26,
    "pais": "Guatemala"
}

print(persona["nombre"])
print(persona["edad"])
```

Resultado en la terminal:

```
Julián
26
```

> 📌 En las listas usas la **posición**: `frutas[0]`.
> En los diccionarios usas la **clave**: `persona["nombre"]`.

### ¿Y si la clave no existe?

```python
print(persona["telefono"])   # ❌ error
```

```
KeyError: 'telefono'
```

Para evitar este error puedes usar `.get()`. Si la clave no existe, en lugar de dar error devuelve `None`, o el valor que tú le digas:

```python
print(persona.get("telefono"))
print(persona.get("telefono", "Sin teléfono"))
```

```
None
Sin teléfono
```

---

## Agregar y modificar valores

Se hace de la misma forma: escribes la clave y le asignas un valor.

- Si la clave **ya existe**, se **modifica** su valor.
- Si la clave **no existe**, se **agrega**.

```python
persona = {
    "nombre": "Julián",
    "edad": 26
}

persona["edad"] = 27              # modifica (la clave ya existía)
persona["telefono"] = "5555-1234" # agrega (la clave es nueva)

print(persona)
```

```
{'nombre': 'Julián', 'edad': 27, 'telefono': '5555-1234'}
```

> ⚠️ **Las claves no se pueden repetir.** Si escribes una clave que ya existe, no se crea otra: se reemplaza el valor anterior.

---

## Eliminar valores

| Forma | ¿Qué hace? |
|-------|------------|
| `del diccionario["clave"]` | Elimina la clave y su valor |
| `diccionario.pop("clave")` | Elimina la clave y te devuelve su valor |

```python
persona = {
    "nombre": "Julián",
    "edad": 26,
    "telefono": "5555-1234"
}

del persona["telefono"]
print(persona)

edad = persona.pop("edad")
print(edad)
print(persona)
```

```
{'nombre': 'Julián', 'edad': 26}
26
{'nombre': 'Julián'}
```

---

## Funciones y métodos más usados

| Qué quieres hacer | Cómo se hace | ¿Qué devuelve? |
|-------------------|--------------|----------------|
| Contar elementos | `len(diccionario)` | Cuántas parejas clave-valor hay |
| Saber si existe una clave | `"clave" in diccionario` | `True` o `False` |
| Obtener un valor sin riesgo de error | `diccionario.get("clave")` | El valor, o `None` si no existe |
| Ver todas las claves | `diccionario.keys()` | Todas las claves |
| Ver todos los valores | `diccionario.values()` | Todos los valores |
| Ver todo | `diccionario.items()` | Todas las parejas (clave, valor) |

**✅ Ejemplo**

```python
producto = {
    "nombre": "Camisa",
    "precio": 150,
    "talla": "M"
}

print(len(producto))
print("precio" in producto)
print("color" in producto)
print(producto.keys())
print(producto.values())
```

Resultado en la terminal:

```
3
True
False
dict_keys(['nombre', 'precio', 'talla'])
dict_values(['Camisa', 150, 'M'])
```

> ⚠️ `in` busca en las **claves**, no en los valores. `"Camisa" in producto` da `False`, porque `"Camisa"` es un valor, no una clave.

---

## Recorrer un diccionario con `for`

### Solo las claves

Si recorres el diccionario directamente, el `for` te da las **claves**:

```python
producto = {"nombre": "Camisa", "precio": 150, "talla": "M"}

for clave in producto:
    print(clave)
```

```
nombre
precio
talla
```

### Claves y valores juntos

Usando `.items()` obtienes las dos cosas en cada vuelta. Aquí se usa el **desempaquetado** que viste en el tema de tuplas:

```python
producto = {"nombre": "Camisa", "precio": 150, "talla": "M"}

for clave, valor in producto.items():
    print(f"{clave}: {valor}")
```

```
nombre: Camisa
precio: 150
talla: M
```

---

## Listas de diccionarios

Esta es una de las combinaciones más usadas en programación. Cada diccionario representa **una cosa** (un estudiante, un producto, un usuario) y la lista los agrupa a todos.

**✅ Ejemplo: lista de estudiantes**

```python
estudiantes = [
    {"nombre": "Ana", "nota": 85},
    {"nombre": "Carlos", "nota": 60},
    {"nombre": "María", "nota": 92}
]

for estudiante in estudiantes:
    if estudiante["nota"] >= 70:
        print(f"{estudiante['nombre']}: Aprobado")
    else:
        print(f"{estudiante['nombre']}: Reprobado")
```

Resultado en la terminal:

```
Ana: Aprobado
Carlos: Reprobado
María: Aprobado
```

> 💡 Fíjate que dentro del f-string usamos comillas simples `'nombre'`. Es porque el f-string ya usa comillas dobles `" "`, y en versiones de Python anteriores a la 3.12 repetir las mismas comillas da error. Usar comillas simples adentro funciona en todas las versiones.

**✅ Ejemplo: carrito de compras**

Aquí se juntan varios temas: diccionarios, listas, ciclos, acumuladores y funciones.

```python
def calcular_total(carrito):
    total = 0
    for producto in carrito:
        total += producto["precio"] * producto["cantidad"]
    return total

carrito = [
    {"nombre": "Camisa", "precio": 150, "cantidad": 2},
    {"nombre": "Pantalón", "precio": 250, "cantidad": 1},
    {"nombre": "Calcetines", "precio": 25, "cantidad": 3}
]

print(f"Total a pagar: Q{calcular_total(carrito)}")
```

```
Total a pagar: Q625
```

> 💡 Esta estructura (lista de diccionarios) es muy parecida a como llegan los datos desde internet o desde una base de datos. Si la entiendes bien, vas a tener una gran ventaja más adelante.

---

## Listas vs diccionarios

| | Lista | Diccionario |
|-|-------|-------------|
| Se crea con | Corchetes `[ ]` | Llaves `{ }` |
| ¿Cómo se accede a un dato? | Por posición: `lista[0]` | Por clave: `dic["nombre"]` |
| ¿Cuándo usarlo? | Varios datos **del mismo tipo** | Varios datos **que describen una misma cosa** |
| Ejemplo | Lista de nombres: `["Ana", "Carlos", "María"]` | Ficha de una persona: `{"nombre": "Ana", "edad": 20}` |

> 💡 **Regla fácil:** si te preguntas "¿qué significa este dato?", probablemente necesitas un diccionario.

---

## Errores comunes

| Error | Ejemplo incorrecto | Forma correcta |
|-------|-------------------|----------------|
| Pedir una clave que no existe | `persona["telefono"]` → `KeyError` | `persona.get("telefono")` |
| Olvidar las comillas en la clave | `persona[nombre]` | `persona["nombre"]` |
| Usar posición en vez de clave | `persona[0]` | `persona["nombre"]` |
| Olvidar los dos puntos entre clave y valor | `{"nombre" "Ana"}` | `{"nombre": "Ana"}` |
| Buscar un valor con `in` | `"Ana" in persona` → `False` | `"Ana" in persona.values()` |
| Repetir comillas dobles dentro de un f-string (error en Python anterior a 3.12) | `f"{persona["nombre"]}"` | `f"{persona['nombre']}"` |