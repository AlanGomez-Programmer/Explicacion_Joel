# 📋 Listas y tuplas

## ¿Para qué sirven?

Hasta ahora cada variable guardaba **un solo valor**. Pero, ¿qué pasa si quieres guardar los nombres de 30 estudiantes? Crear 30 variables sería muy incómodo:

```python
estudiante1 = "Ana"
estudiante2 = "Carlos"
estudiante3 = "María"
# ... y así hasta 30 😩
```

Las **listas** y las **tuplas** resuelven esto: te permiten guardar **varios valores en una sola variable**.

---

# Listas

## ¿Qué es una lista?

Una lista es como una **lista del supermercado**: tiene varios elementos en orden, y puedes agregar, quitar o cambiar cosas cuando quieras.

Se crea con corchetes `[ ]` y los elementos se separan con comas:

```python
frutas = ["manzana", "banano", "mango"]
numeros = [10, 20, 30, 40]
mezcla = ["Ana", 25, True, 9.99]
vacia = []
```

> 💡 Una lista puede guardar cualquier tipo de dato, incluso mezclados. Pero lo más común es que todos sean del mismo tipo.

---

## Acceder a un elemento (índices)

Cada elemento tiene una **posición**, llamada **índice**. Para obtener un elemento, escribes el nombre de la lista y el índice entre corchetes.

```python
frutas = ["manzana", "banano", "mango"]

print(frutas[0])
print(frutas[2])
```

Resultado en la terminal:

```
manzana
mango
```

> ⚠️ **Los índices empiezan en 0, no en 1.**
>
> | Elemento | `"manzana"` | `"banano"` | `"mango"` |
> |----------|-------------|------------|-----------|
> | Índice | `0` | `1` | `2` |
>
> Es igual que con `range()`: se empieza a contar desde cero.

### Índices negativos

Si usas números negativos, cuentas **desde el final**. Es muy útil para obtener el último elemento sin saber cuántos hay.

```python
frutas = ["manzana", "banano", "mango"]

print(frutas[-1])   # el último
print(frutas[-2])   # el penúltimo
```

```
mango
banano
```

---

## Modificar un elemento

Solo indicas la posición y le asignas el nuevo valor:

```python
frutas = ["manzana", "banano", "mango"]

frutas[1] = "fresa"

print(frutas)
```

```
['manzana', 'fresa', 'mango']
```

---

## Funciones y métodos más usados

Un **método** es una función que le pertenece a un tipo de dato. Se usa escribiendo un punto después de la variable: `lista.metodo()`.

| Qué quieres hacer | Cómo se hace | ¿Qué hace? |
|-------------------|--------------|------------|
| Contar elementos | `len(lista)` | Dice cuántos elementos tiene |
| Agregar al final | `lista.append(valor)` | Agrega un elemento al final |
| Agregar en una posición | `lista.insert(índice, valor)` | Agrega un elemento en la posición que digas |
| Quitar por valor | `lista.remove(valor)` | Quita el primer elemento con ese valor |
| Quitar por posición | `lista.pop(índice)` | Quita el elemento de esa posición y te lo devuelve |
| Quitar el último | `lista.pop()` | Quita el último elemento y te lo devuelve |
| Ordenar | `lista.sort()` | Ordena la lista de menor a mayor (o alfabéticamente) |
| Saber si existe | `valor in lista` | Devuelve `True` o `False` |

**✅ Ejemplo: lista del supermercado**

```python
compras = ["leche", "pan"]

compras.append("huevos")          # agrega al final
compras.insert(0, "café")         # agrega al inicio
print(compras)

compras.remove("pan")             # quita el pan
print(compras)

print(len(compras))               # cuántos hay
print("leche" in compras)         # ¿hay leche?
print("arroz" in compras)         # ¿hay arroz?
```

Resultado en la terminal:

```
['café', 'leche', 'pan', 'huevos']
['café', 'leche', 'huevos']
3
True
False
```

**✅ Ejemplo: ordenar**

```python
notas = [85, 60, 92, 78]

notas.sort()
print(notas)
```

```
[60, 78, 85, 92]
```

> 💡 Si quieres ordenar de mayor a menor, usa `notas.sort(reverse=True)`.

---

## Obtener una parte de la lista (slicing)

Puedes "cortar" una lista para quedarte solo con una parte, usando `[inicio:fin]`. Funciona igual que `range()`: **el `fin` no se incluye**.

```python
numeros = [10, 20, 30, 40, 50]

print(numeros[1:4])   # del índice 1 al 3
print(numeros[:3])    # desde el inicio hasta el índice 2
print(numeros[2:])    # desde el índice 2 hasta el final
```

```
[20, 30, 40]
[10, 20, 30]
[30, 40, 50]
```

---

## Recorrer una lista con `for`

Como viste en el tema de ciclos, el `for` puede pasar por cada elemento de una lista:

```python
estudiantes = ["Ana", "Carlos", "María"]

for estudiante in estudiantes:
    print(f"Hola, {estudiante}")
```

```
Hola, Ana
Hola, Carlos
Hola, María
```

**✅ Ejemplo: calcular el promedio de notas**

```python
notas = [85, 60, 92, 78]

total = 0
for nota in notas:
    total += nota

promedio = total / len(notas)
print(f"Promedio: {promedio}")
```

```
Promedio: 78.75
```

> 💡 Python también tiene la función `sum()` que suma todos los elementos de una vez: `sum(notas) / len(notas)` da el mismo resultado.

---

# Tuplas

## ¿Qué es una tupla?

Una tupla es muy parecida a una lista, con una diferencia importante: **una vez creada, no se puede cambiar**. No puedes agregar, quitar ni modificar elementos.

Si la lista es una lista del supermercado que vas tachando y cambiando, la tupla es como tu **fecha de nacimiento**: se escribe una vez y no cambia.

Se crea con paréntesis `( )`:

```python
fecha_nacimiento = (15, 8, 1998)
coordenadas = (14.6349, -90.5069)
colores = ("rojo", "verde", "azul")
```

## Acceder a los elementos

Funciona **exactamente igual** que en las listas: con índices que empiezan en 0.

```python
colores = ("rojo", "verde", "azul")

print(colores[0])
print(colores[-1])
print(len(colores))
print("verde" in colores)
```

```
rojo
azul
3
True
```

También puedes recorrerla con `for` y usar slicing, igual que una lista.

## Intentar modificar una tupla

```python
colores = ("rojo", "verde", "azul")

colores[0] = "amarillo"   # ❌ error
```

```
TypeError: 'tuple' object does not support item assignment
```

Python no te deja, porque las tuplas no se pueden cambiar. Tampoco tienen `append()`, `remove()` ni `sort()`.

> ⚠️ **Tupla de un solo elemento**
>
> Si tu tupla tiene un solo elemento, debes poner una coma al final. Sin la coma, Python piensa que son paréntesis normales.
>
> ```python
> a = ("hola")    # esto es un str, no una tupla
> b = ("hola",)   # esto sí es una tupla
> ```

## Desempaquetar una tupla

Puedes sacar todos los valores de una tupla y guardarlos en variables separadas en una sola línea:

```python
fecha_nacimiento = (15, 8, 1998)

dia, mes, anio = fecha_nacimiento

print(f"Día: {dia}")
print(f"Mes: {mes}")
print(f"Año: {anio}")
```

```
Día: 15
Mes: 8
Año: 1998
```

> 💡 Esto también funciona con listas, pero se usa mucho más con tuplas. Por ejemplo, cuando una función necesita devolver más de un valor:
>
> ```python
> def dividir(a, b):
>     return a // b, a % b    # devuelve una tupla
>
> cociente, residuo = dividir(10, 3)
> print(cociente, residuo)
> ```
>
> ```
> 3 1
> ```

---

## Listas vs tuplas

| | Lista | Tupla |
|-|-------|-------|
| Se crea con | Corchetes `[ ]` | Paréntesis `( )` |
| ¿Se puede modificar? | ✅ Sí | ❌ No |
| ¿Se puede agregar o quitar elementos? | ✅ Sí | ❌ No |
| Índices, `len()`, `in`, `for`, slicing | ✅ Sí | ✅ Sí |
| ¿Cuándo usarla? | Cuando los datos van a cambiar | Cuando los datos son fijos |
| Ejemplo de la vida real | Lista de compras, carrito de una tienda | Fecha de nacimiento, coordenadas de un lugar, días de la semana |

> 💡 **Regla fácil:** si no estás seguro, usa una lista. Usa una tupla cuando quieras asegurarte de que nadie cambie esos datos por error.

---

## Errores comunes

| Error | Ejemplo incorrecto | Forma correcta |
|-------|-------------------|----------------|
| Pensar que el primer elemento es el índice 1 | `frutas[1]` para la primera | `frutas[0]` |
| Pedir un índice que no existe | `frutas[3]` en una lista de 3 → `IndexError` | `frutas[2]` o `frutas[-1]` |
| Intentar modificar una tupla | `colores[0] = "amarillo"` | Usar una lista si necesitas cambiarla |
| Olvidar la coma en una tupla de un elemento | `("hola")` | `("hola",)` |
| Usar `remove()` con un valor que no está | `frutas.remove("uva")` → `ValueError` | Revisar antes con `if "uva" in frutas:` |
| Guardar el resultado de `sort()` | `ordenada = notas.sort()` → `None` | `notas.sort()` y luego usar `notas` |