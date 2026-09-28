# 🔁 Ciclos

## ¿Qué es un ciclo?

Un ciclo es una forma de decirle a Python: **"repite esto varias veces"**.

Imagina que tienes que escribir "Hola" 100 veces. Sin ciclos tendrías que escribir 100 líneas de `print("Hola")`. Con un ciclo, lo haces en 2 líneas.

En Python hay dos tipos de ciclos:

1. `for` → cuando **sabes cuántas veces** quieres repetir algo
2. `while` → cuando quieres repetir algo **mientras** se cumpla una condición

> 💡 Igual que en el `if`, los ciclos llevan **dos puntos `:`** al final y el código que se repite va con **4 espacios** de sangría.

---

## 1. Ciclo `for`

### Repetir un número de veces con `range()`

`range()` genera una serie de números para que el `for` los recorra uno por uno.

```
for variable in range(cantidad):
    código que se repite
```

**✅ Ejemplo**

```python
for numero in range(5):
    print(numero)
```

Resultado en la terminal:

```
0
1
2
3
4
```

En cada vuelta, la variable `numero` toma el siguiente valor: primero `0`, luego `1`, y así hasta llegar a `4`.

> ⚠️ **`range()` empieza en 0 y no incluye el último número.**
>
> `range(5)` da `0, 1, 2, 3, 4`, o sea 5 números, pero el `5` no aparece.

### Formas de usar `range()`

| Forma | ¿Qué hace? | Ejemplo | Números que genera |
|-------|------------|---------|--------------------|
| `range(fin)` | Del 0 hasta antes de `fin` | `range(5)` | `0, 1, 2, 3, 4` |
| `range(inicio, fin)` | Desde `inicio` hasta antes de `fin` | `range(1, 6)` | `1, 2, 3, 4, 5` |
| `range(inicio, fin, salto)` | Igual, pero avanzando de `salto` en `salto` | `range(0, 11, 2)` | `0, 2, 4, 6, 8, 10` |

**✅ Ejemplo: tabla de multiplicar**

```python
tabla = 5

for numero in range(1, 11):
    print(f"{tabla} x {numero} = {tabla * numero}")
```

Resultado en la terminal:

```
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
...
5 x 10 = 50
```

### Recorrer un texto

El `for` también puede recorrer un texto letra por letra:

```python
for letra in "Hola":
    print(letra)
```

```
H
o
l
a
```

### Recorrer una lista

Una lista es una variable que guarda varios valores a la vez, entre corchetes `[ ]`. El `for` puede recorrerla elemento por elemento:

```python
frutas = ["manzana", "banano", "mango"]

for fruta in frutas:
    print(f"Me gusta el {fruta}")
```

```
Me gusta el manzana
Me gusta el banano
Me gusta el mango
```

---

## 2. Ciclo `while`

Repite un bloque de código **mientras** la condición sea verdadera. Cuando la condición se vuelve `False`, el ciclo termina.

```
while condición:
    código que se repite
```

**✅ Ejemplo**

```python
contador = 1

while contador <= 5:
    print(contador)
    contador += 1
```

Resultado en la terminal:

```
1
2
3
4
5
```

Así funciona paso a paso:

1. `contador` vale `1`. ¿`1 <= 5`? Sí → imprime `1` y suma 1.
2. `contador` vale `2`. ¿`2 <= 5`? Sí → imprime `2` y suma 1.
3. ...
4. `contador` vale `6`. ¿`6 <= 5`? No → el ciclo termina.

> ⚠️ **Cuidado con los ciclos infinitos**
>
> Si olvidas la línea `contador += 1`, el contador siempre vale `1`, la condición siempre es `True` y el ciclo **nunca termina**. Si te pasa, presiona `Ctrl + C` en la terminal para detenerlo.

### ¿Cuándo usar `while`?

Cuando **no sabes cuántas veces** se va a repetir algo. Por ejemplo, pedir una contraseña hasta que el usuario la escriba bien:

```python
contrasena = ""

while contrasena != "1234":
    contrasena = input("Escribe la contraseña: ")

print("Acceso permitido")
```

Resultado en la terminal:

```
Escribe la contraseña: hola
Escribe la contraseña: 0000
Escribe la contraseña: 1234
Acceso permitido
```

No sabemos si el usuario lo va a lograr en el primer intento o en el décimo, por eso usamos `while`.

---

## `for` vs `while`

| | `for` | `while` |
|-|-------|---------|
| ¿Cuándo usarlo? | Cuando sabes cuántas veces se repite | Cuando depende de una condición |
| Ejemplo de la vida real | "Da 10 vueltas a la cancha" | "Corre hasta que te canses" |
| ¿Riesgo de ciclo infinito? | No | Sí, si la condición nunca cambia |

---

## Controlar un ciclo: `break` y `continue`

| Palabra | ¿Qué hace? |
|---------|------------|
| `break` | **Detiene** el ciclo por completo y sale de él |
| `continue` | **Salta** a la siguiente vuelta sin ejecutar lo que falta |

**✅ Ejemplo con `break`**

Buscar el primer número divisible entre 7:

```python
for numero in range(1, 100):
    if numero % 7 == 0:
        print(f"Encontrado: {numero}")
        break
```

```
Encontrado: 7
```

En cuanto lo encuentra, se detiene. No sigue revisando hasta el 99.

**✅ Ejemplo con `continue`**

Imprimir solo los números impares:

```python
for numero in range(1, 8):
    if numero % 2 == 0:
        continue
    print(numero)
```

```
1
3
5
7
```

Cuando el número es par, `continue` salta a la siguiente vuelta y el `print` no se ejecuta.

---

## Bonus: contadores y acumuladores

Son dos patrones que vas a usar muchísimo con ciclos.

**Contador:** cuenta cuántas veces pasa algo. Siempre suma 1.

**Acumulador:** va sumando valores para obtener un total.

**✅ Ejemplo**

```python
precios = [25, 40, 15, 60]

cantidad = 0   # contador
total = 0      # acumulador

for precio in precios:
    cantidad += 1
    total += precio

print(f"Productos: {cantidad}")
print(f"Total a pagar: Q{total}")
```

Resultado en la terminal:

```
Productos: 4
Total a pagar: Q140
```

> 💡 El contador y el acumulador siempre se crean **antes** del ciclo y empiezan en `0`. Si los creas dentro del ciclo, se reinician en cada vuelta.

---

## Errores comunes

| Error | Ejemplo incorrecto | Forma correcta |
|-------|-------------------|----------------|
| Olvidar los dos puntos | `for i in range(5)` | `for i in range(5):` |
| Olvidar la sangría | `for i in range(5):`<br>`print(i)` | `for i in range(5):`<br>`    print(i)` |
| Pensar que `range(5)` llega al 5 | `range(5)` → espera `1 a 5` | `range(1, 6)` → da `1 a 5` |
| Olvidar actualizar la variable en el `while` | `while x < 5:`<br>`    print(x)` | `while x < 5:`<br>`    print(x)`<br>`    x += 1` |
| Crear el acumulador dentro del ciclo | `for p in precios:`<br>`    total = 0` | `total = 0`<br>`for p in precios:` |