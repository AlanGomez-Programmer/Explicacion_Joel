# 🧩 Funciones

## ¿Qué es una función?

Una función es un **bloque de código con nombre** que hace una tarea específica. La escribes una vez y la puedes usar todas las veces que quieras.

Piensa en una función como una **receta de cocina**:

- Tiene un nombre: "Licuado de fresa".
- Necesita ingredientes: fresas, leche, azúcar.
- Sigue unos pasos.
- Al final te entrega algo: el licuado.

Una vez que tienes la receta, no necesitas inventarla de nuevo cada vez que quieras un licuado. Solo la sigues.

### ¡Ya has usado funciones!

Sin darte cuenta, en los temas anteriores ya usaste varias funciones que vienen incluidas en Python:

| Función | ¿Qué hace? |
|---------|------------|
| `print()` | Muestra algo en la terminal |
| `type()` | Te dice el tipo de dato |
| `input()` | Le pide un dato al usuario |
| `int()` | Convierte un valor a número entero |
| `range()` | Genera una serie de números |

Ahora vas a aprender a **crear tus propias funciones**.

---

## ¿Cómo crear una función?

Se usa la palabra `def` (de *define*, "definir"), el nombre de la función, paréntesis `()` y dos puntos `:`. El código de la función va con **4 espacios** de sangría.

```
def nombre_funcion():
    código de la función
```

**✅ Ejemplo**

```python
def saludar():
    print("¡Hola! Bienvenido")
```

Si ejecutas solo esto, **no pasa nada**. Solo le enseñaste la receta a Python, pero todavía no le dijiste que la prepare.

### Llamar a una función

Para que la función se ejecute, tienes que **llamarla** escribiendo su nombre con paréntesis:

```python
def saludar():
    print("¡Hola! Bienvenido")

saludar()
saludar()
```

Resultado en la terminal:

```
¡Hola! Bienvenido
¡Hola! Bienvenido
```

> ⚠️ La función se tiene que crear **antes** de llamarla. Si la llamas antes de la línea del `def`, Python da error porque todavía no la conoce (recuerda que lee de arriba hacia abajo).

---

## Parámetros: darle datos a la función

Los parámetros son los **ingredientes** de la receta. Son variables que van dentro de los paréntesis y permiten que la función trabaje con datos diferentes cada vez.

**✅ Ejemplo**

```python
def saludar(nombre):
    print(f"¡Hola, {nombre}! Bienvenido")

saludar("Ana")
saludar("Carlos")
```

Resultado en la terminal:

```
¡Hola, Ana! Bienvenido
¡Hola, Carlos! Bienvenido
```

La misma función, pero con un resultado diferente según el nombre que le pases.

### 📌 Parámetro vs argumento

Son dos palabras que vas a escuchar mucho y parecen lo mismo:

- **Parámetro:** el nombre de la variable en el `def` → `nombre`
- **Argumento:** el valor real que le mandas al llamarla → `"Ana"`

### Varios parámetros

Puedes tener todos los que necesites, separados por comas:

```python
def presentar(nombre, edad):
    print(f"Me llamo {nombre} y tengo {edad} años")

presentar("Julián", 26)
```

```
Me llamo Julián y tengo 26 años
```

> ⚠️ El orden importa. Si escribes `presentar(26, "Julián")`, el resultado sería "Me llamo 26 y tengo Julián años".

---

## `return`: que la función te devuelva algo

Hasta ahora las funciones solo **imprimían** cosas. Pero muchas veces quieres que la función haga un cálculo y te **entregue el resultado** para seguir usándolo. Para eso se usa `return`.

**✅ Ejemplo**

```python
def sumar(a, b):
    return a + b

resultado = sumar(5, 3)
print(resultado)
```

Resultado en la terminal:

```
8
```

La función calcula `5 + 3` y **devuelve** el `8`, que se guarda en la variable `resultado`.

### 📌 ¿Cuál es la diferencia entre `print` y `return`?

Esta es una de las dudas más comunes al empezar:

| | `print` | `return` |
|-|---------|----------|
| ¿Qué hace? | **Muestra** el valor en la terminal | **Entrega** el valor a quien llamó la función |
| ¿Puedo guardar el resultado en una variable? | No | Sí |
| En la receta sería... | Enseñarle el licuado a alguien | Darle el licuado para que se lo tome |

```python
def sumar_con_print(a, b):
    print(a + b)

def sumar_con_return(a, b):
    return a + b

x = sumar_con_print(5, 3)    # imprime 8, pero x queda vacía
y = sumar_con_return(5, 3)   # no imprime nada, pero y vale 8

print(x)
print(y)
```

```
8
None
8
```

`x` vale `None`, que en Python significa "nada", porque esa función no devolvió ningún valor.

> 💡 Cuando Python llega a un `return`, la función **termina en ese momento**. Cualquier línea que esté debajo del `return` ya no se ejecuta.

**✅ Ejemplo práctico: calcular el total con IVA**

```python
IVA = 0.12

def calcular_total(precio):
    return precio + (precio * IVA)

total = calcular_total(100)
print(f"Total a pagar: Q{total}")
```

```
Total a pagar: Q112.0
```

---

## Parámetros con valor por defecto

Puedes darle un valor "de reserva" a un parámetro. Si al llamar la función no le mandas ese dato, usa el valor por defecto.

```python
def saludar(nombre="amigo"):
    print(f"¡Hola, {nombre}!")

saludar("Ana")
saludar()
```

```
¡Hola, Ana!
¡Hola, amigo!
```

> ⚠️ Los parámetros con valor por defecto van **al final**. `def presentar(nombre="Ana", edad)` da error; lo correcto es `def presentar(edad, nombre="Ana")`.

---

## Variables dentro y fuera de una función

Las variables que creas **dentro** de una función solo existen ahí adentro. Cuando la función termina, desaparecen.

```python
def calcular():
    resultado = 10 * 2
    return resultado

calcular()
print(resultado)   # ❌ error: resultado no existe aquí afuera
```

Si quieres usar ese valor afuera, tienes que usar `return` y guardarlo en una variable:

```python
def calcular():
    resultado = 10 * 2
    return resultado

valor = calcular()
print(valor)   # ✅ 20
```

> 💡 Piensa que la función es una cocina cerrada: lo que pasa adentro se queda adentro. Lo único que sale es lo que entregas con `return`.

---

## ¿Por qué usar funciones?

- **No repites código.** Escribes la lógica una vez y la usas muchas veces.
- **Es más fácil de leer.** `calcular_total(100)` se entiende mejor que ver la fórmula completa.
- **Es más fácil de corregir.** Si hay un error, lo arreglas en un solo lugar y se corrige en todas partes.

> 💡 Ponle a tus funciones nombres que digan **qué hacen**, usando un verbo: `calcular_total`, `saludar`, `validar_contrasena`. Igual que las variables, se escriben en minúsculas con guion bajo.

---

## Errores comunes

| Error | Ejemplo incorrecto | Forma correcta |
|-------|-------------------|----------------|
| Olvidar los dos puntos | `def saludar()` | `def saludar():` |
| Olvidar la sangría | `def saludar():`<br>`print("Hola")` | `def saludar():`<br>`    print("Hola")` |
| Llamarla sin paréntesis | `saludar` | `saludar()` |
| Llamarla antes de crearla | `saludar()`<br>`def saludar():` | `def saludar():`<br>`    ...`<br>`saludar()` |
| Olvidar mandar un argumento | `presentar("Ana")` (pide 2) | `presentar("Ana", 20)` |
| Usar `print` cuando necesitas el valor | `x = sumar_con_print(2, 3)` → `None` | `x = sumar_con_return(2, 3)` → `5` |