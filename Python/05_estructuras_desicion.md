# 🔀 Estructuras de decisión

## ¿Qué es una estructura de decisión?

Es una forma de decirle a Python: **"si pasa esto, haz esto; si no, haz otra cosa"**.

Todos los días tomamos decisiones así:

> Si está lloviendo, llevo paraguas. Si no, lo dejo en casa.

En programación funciona igual. Python revisa una condición y, dependiendo de si es `True` o `False`, decide qué código ejecutar.

Las estructuras de decisión en Python son:

1. `if` → "si"
2. `else` → "si no"
3. `elif` → "si no, pero si..."

---

## 1. `if` (si)

Ejecuta un bloque de código **solo si** la condición es verdadera.

```
if condición:
    código que se ejecuta si la condición es True
```

**✅ Ejemplo**

```python
edad = 20

if edad >= 18:
    print("Eres mayor de edad")
```

Resultado en la terminal:

```
Eres mayor de edad
```

Si `edad` fuera `15`, no se imprimiría nada, porque la condición sería `False`.

### 📌 Dos reglas muy importantes

**1. Los dos puntos `:`**

Después de la condición siempre van dos puntos. Si los olvidas, Python da error.

**2. La sangría (los espacios al inicio)**

El código que va "dentro" del `if` debe tener **4 espacios** al inicio (o un Tab). Así Python sabe qué líneas pertenecen al `if` y cuáles no.

```python
edad = 15

if edad >= 18:
    print("Eres mayor de edad")   # está dentro del if
print("Fin del programa")          # está fuera del if, siempre se ejecuta
```

Resultado en la terminal:

```
Fin del programa
```

> 💡 En otros lenguajes se usan llaves `{ }` para marcar los bloques. En Python se usa la sangría, por eso es tan importante.

---

## 2. `else` (si no)

Ejecuta un bloque de código cuando la condición del `if` **no se cumple**. Es el "plan B".

```
if condición:
    código si es True
else:
    código si es False
```

**✅ Ejemplo**

```python
edad = 15

if edad >= 18:
    print("Puedes entrar")
else:
    print("No puedes entrar")
```

Resultado en la terminal:

```
No puedes entrar
```

> 💡 El `else` no lleva condición. Simplemente atrapa todo lo que no cumplió el `if`.

---

## 3. `elif` (si no, pero si...)

Se usa cuando hay **más de dos caminos posibles**. Python revisa las condiciones de arriba hacia abajo y ejecuta **solo la primera** que se cumpla.

```
if condición1:
    código
elif condición2:
    código
elif condición3:
    código
else:
    código si ninguna se cumplió
```

**✅ Ejemplo**

Imagina que quieres mostrar el resultado de un examen según la nota:

```python
nota = 75

if nota >= 90:
    print("Excelente")
elif nota >= 70:
    print("Aprobado")
elif nota >= 60:
    print("Casi, necesitas repasar")
else:
    print("Reprobado")
```

Resultado en la terminal:

```
Aprobado
```

La nota `75` no cumple `>= 90`, pero sí cumple `>= 70`, así que imprime "Aprobado" y **ya no revisa las demás**, aunque `75 >= 60` también sea verdadero.

> ⚠️ **El orden importa**
>
> Si pusieras primero `nota >= 60`, una nota de `95` diría "Casi, necesitas repasar", porque sería la primera condición que se cumple. Pon siempre las condiciones más específicas arriba.

---

## Combinar condiciones

Puedes usar los operadores lógicos (`and`, `or`, `not`) dentro de un `if` para revisar varias cosas a la vez.

**✅ Ejemplo**

```python
edad = 20
tiene_boleto = True

if edad >= 18 and tiene_boleto:
    print("Bienvenido al concierto")
else:
    print("No puedes entrar")
```

Resultado en la terminal:

```
Bienvenido al concierto
```

---

## Decisiones dentro de decisiones

También puedes poner un `if` dentro de otro. Solo recuerda agregar 4 espacios más por cada nivel.

**✅ Ejemplo**

```python
tiene_cuenta = True
contrasena_correcta = False

if tiene_cuenta:
    if contrasena_correcta:
        print("Bienvenido")
    else:
        print("Contraseña incorrecta")
else:
    print("Primero debes registrarte")
```

Resultado en la terminal:

```
Contraseña incorrecta
```

> 💡 Si empiezas a tener muchos `if` uno dentro de otro, el código se vuelve difícil de leer. Muchas veces se puede simplificar usando `and` o `elif`.

---

## Bonus: pedirle datos al usuario

Con `input()` puedes pedir que el usuario escriba algo en la terminal y tomar una decisión con eso.

```python
edad = int(input("¿Cuántos años tienes? "))

if edad >= 18:
    print("Eres mayor de edad")
else:
    print("Eres menor de edad")
```

Resultado en la terminal (si el usuario escribe `16`):

```
¿Cuántos años tienes? 16
Eres menor de edad
```

> ⚠️ `input()` **siempre** devuelve texto (`str`), aunque el usuario escriba un número. Por eso usamos `int()` para convertirlo a número entero y poder compararlo con `>=`.

---

## Errores comunes

| Error | Ejemplo incorrecto | Forma correcta |
|-------|-------------------|----------------|
| Olvidar los dos puntos | `if edad >= 18` | `if edad >= 18:` |
| Olvidar la sangría | `if edad >= 18:`<br>`print("Hola")` | `if edad >= 18:`<br>`    print("Hola")` |
| Usar `=` en vez de `==` | `if edad = 18:` | `if edad == 18:` |
| Poner condición en el `else` | `else edad < 18:` | `else:` |