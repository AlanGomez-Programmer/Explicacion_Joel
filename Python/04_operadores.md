# ➕ Operadores

## ¿Qué es un operador?

Un operador es un **símbolo que le dice a Python que haga algo** con uno o más valores: sumar, comparar, unir, etc.

```python
resultado = 5 + 3
```

Aquí el operador es `+`, y le dice a Python que sume `5` y `3`.

En Python hay cuatro grupos principales de operadores:

1. Aritméticos (para hacer cuentas)
2. De comparación (para comparar valores)
3. Lógicos (para combinar condiciones)
4. De asignación (para guardar valores en variables)

---

## 1. Operadores aritméticos

Sirven para hacer operaciones matemáticas, como en una calculadora.

| Operador | ¿Qué hace? | Ejemplo | Resultado |
|----------|------------|---------|-----------|
| `+` | Suma | `10 + 3` | `13` |
| `-` | Resta | `10 - 3` | `7` |
| `*` | Multiplicación | `10 * 3` | `30` |
| `/` | División | `10 / 3` | `3.3333...` |
| `//` | División entera (quita los decimales) | `10 // 3` | `3` |
| `%` | Residuo (lo que sobra de una división) | `10 % 3` | `1` |
| `**` | Potencia | `10 ** 3` | `1000` |

**✅ Ejemplo**

```python
precio = 100
cantidad = 3

total = precio * cantidad
print(total)
```

Resultado en la terminal:

```
300
```

> 💡 La división con `/` **siempre** da un número decimal, aunque la división sea exacta: `10 / 2` da `5.0`, no `5`.

### 📌 ¿Para qué sirve el `%`?

Piensa en repartir 10 dulces entre 3 personas: a cada una le tocan 3 (`10 // 3`) y sobra 1 (`10 % 3`).

Se usa mucho para saber si un número es par: si al dividirlo entre 2 no sobra nada, es par.

```python
numero = 8
print(numero % 2)
```

```
0
```

Como sobra `0`, el número es par.

### El orden importa

Python respeta el mismo orden que en matemáticas: primero potencias, luego multiplicaciones y divisiones, y al final sumas y restas. Si quieres cambiar el orden, usa paréntesis.

```python
print(2 + 3 * 4)     # primero 3 * 4
print((2 + 3) * 4)   # primero 2 + 3
```

```
14
20
```

---

## 2. Operadores de comparación

Sirven para comparar dos valores. La respuesta **siempre** es `True` (verdadero) o `False` (falso).

| Operador | ¿Qué pregunta? | Ejemplo | Resultado |
|----------|----------------|---------|-----------|
| `==` | ¿Son iguales? | `5 == 5` | `True` |
| `!=` | ¿Son diferentes? | `5 != 3` | `True` |
| `>` | ¿Es mayor que? | `5 > 3` | `True` |
| `<` | ¿Es menor que? | `5 < 3` | `False` |
| `>=` | ¿Es mayor o igual que? | `5 >= 5` | `True` |
| `<=` | ¿Es menor o igual que? | `3 <= 2` | `False` |

**✅ Ejemplo**

```python
edad = 20

print(edad >= 18)
```

Resultado en la terminal:

```
True
```

> ⚠️ **No confundas `=` con `==`**
>
> `=` **guarda** un valor: `edad = 20`
>
> `==` **pregunta** si dos valores son iguales: `edad == 20`

---

## 3. Operadores lógicos

Sirven para combinar varias comparaciones en una sola.

| Operador | ¿Qué hace? | Es `True` cuando... |
|----------|------------|---------------------|
| `and` | "y" | **Todas** las condiciones se cumplen |
| `or` | "o" | **Al menos una** condición se cumple |
| `not` | "no" | Le da la vuelta al resultado: `True` pasa a `False` y viceversa |

**✅ Ejemplo**

Imagina que para entrar a un concierto necesitas ser mayor de edad **y** tener boleto:

```python
edad = 20
tiene_boleto = False

print(edad >= 18 and tiene_boleto)
```

Resultado en la terminal:

```
False
```

Aunque es mayor de edad, no tiene boleto, así que no puede entrar.

Ahora imagina que puedes pagar con efectivo **o** con tarjeta:

```python
tiene_efectivo = False
tiene_tarjeta = True

print(tiene_efectivo or tiene_tarjeta)
```

```
True
```

Con que tenga una de las dos, ya puede pagar.

Y con `not`:

```python
lloviendo = False

print(not lloviendo)
```

```
True
```

---

## 4. Operadores de asignación

Sirven para guardar un valor en una variable. El más básico es `=`, pero hay atajos para cuando quieres cambiar el valor que ya tiene la variable.

| Operador | Es lo mismo que... | Ejemplo (si `x = 10`) | Resultado |
|----------|--------------------|-----------------------|-----------|
| `=` | Guardar un valor | `x = 10` | `10` |
| `+=` | `x = x + valor` | `x += 5` | `15` |
| `-=` | `x = x - valor` | `x -= 5` | `5` |
| `*=` | `x = x * valor` | `x *= 5` | `50` |
| `/=` | `x = x / valor` | `x /= 5` | `2.0` |

**✅ Ejemplo**

```python
puntos = 0

puntos += 10
puntos += 5

print(puntos)
```

Resultado en la terminal:

```
15
```

> 💡 `+=` se usa muchísimo para contadores o para ir sumando un total, como los puntos de un juego o el total de un carrito de compras.

---

## Bonus: operadores con textos

Algunos operadores también funcionan con textos (`str`):

```python
saludo = "Hola" + " " + "Mundo"   # une textos
risa = "ja" * 3                   # repite el texto

print(saludo)
print(risa)
```

Resultado en la terminal:

```
Hola Mundo
jajaja
```