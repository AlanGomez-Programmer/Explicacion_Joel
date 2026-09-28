# 🚨 Manejo de excepciones (errores)

## ¿Qué es una excepción?

Una excepción es un **error que ocurre mientras el programa se está ejecutando**. Cuando pasa, Python detiene el programa y muestra un mensaje en rojo.

Ya viste varias en los temas anteriores:

```python
print(10 / 0)              # ZeroDivisionError
edad = int("hola")         # ValueError
frutas = ["manzana"]
print(frutas[5])           # IndexError
```

El problema es que, si un error aparece, **todo el programa se cae**. Imagina que un usuario escribe "veinte" en lugar de "20" cuando le pides su edad, y tu aplicación se cierra de golpe. No es una buena experiencia.

El manejo de excepciones te permite **atrapar esos errores** y decidir qué hacer con ellos, en lugar de dejar que el programa se caiga.

> 💡 Piénsalo como la **red de seguridad de un trapecista**: si se cae, la red lo atrapa y el espectáculo continúa.

---

## Leer un mensaje de error

Antes de atrapar errores, es útil saber leerlos. Cuando Python da un error, muestra algo así:

```
Traceback (most recent call last):
  File "main.py", line 3, in <module>
    edad = int("hola")
ValueError: invalid literal for int() with base 10: 'hola'
```

Lo más importante está en dos lugares:

- **`line 3`**: la línea donde ocurrió el error.
- **La última línea**: el **tipo de error** (`ValueError`) y una explicación de qué pasó.

> 📌 Cuando algo falle, lee siempre **la última línea primero**. Ahí está la pista principal.

---

## Errores más comunes

| Error | ¿Cuándo pasa? | Ejemplo |
|-------|---------------|---------|
| `ValueError` | El valor no tiene el formato correcto | `int("hola")` |
| `ZeroDivisionError` | Divides entre cero | `10 / 0` |
| `TypeError` | Mezclas tipos que no se pueden combinar | `"Edad: " + 26` |
| `NameError` | Usas una variable o función que no existe | `print(nombre)` sin haber creado `nombre` |
| `IndexError` | Pides una posición que no existe en una lista | `frutas[10]` en una lista de 3 |
| `KeyError` | Pides una clave que no existe en un diccionario | `persona["telefono"]` |
| `FileNotFoundError` | Intentas abrir un archivo que no existe | `open("no_existe.json", "r")` |

---

## `try` y `except`

Es la forma de atrapar un error.

```
try:
    código que podría fallar
except:
    código que se ejecuta si hubo un error
```

- En el `try` ("intentar") pones el código que **podría** dar error.
- En el `except` ("excepto") pones qué hacer **si** ocurre el error.

**✅ Ejemplo**

```python
try:
    edad = int(input("¿Cuántos años tienes? "))
    print(f"Tienes {edad} años")
except ValueError:
    print("Eso no es un número válido")

print("El programa sigue funcionando")
```

Resultado en la terminal (si el usuario escribe `veinte`):

```
¿Cuántos años tienes? veinte
Eso no es un número válido
El programa sigue funcionando
```

Resultado en la terminal (si el usuario escribe `20`):

```
¿Cuántos años tienes? 20
Tienes 20 años
El programa sigue funcionando
```

Así funciona:

1. Python **intenta** ejecutar el código del `try`.
2. Si todo sale bien, se **salta** el `except`.
3. Si hay un error, deja de ejecutar el `try` en esa línea y **salta** al `except`.
4. En los dos casos, el programa **continúa** normalmente después.

> 💡 Igual que el `if`, el `try` y el `except` llevan **dos puntos `:`** y el código de adentro va con **4 espacios** de sangría.

---

## Atrapar errores específicos

Fíjate que en el ejemplo escribimos `except ValueError:` y no solo `except:`. Es muy recomendable indicar **qué error** esperas.

> ⚠️ **Evita el `except:` solo (sin tipo de error).**
>
> Atrapa **cualquier** error, incluso los que no esperabas, como escribir mal el nombre de una variable. El programa no se cae, pero tampoco te enteras de que tienes un error en tu código, y es muy difícil encontrarlo después.

### Varios `except`

Si el código puede fallar de diferentes formas, puedes poner un `except` para cada una:

```python
try:
    numero = int(input("Escribe un número: "))
    resultado = 100 / numero
    print(f"100 / {numero} = {resultado}")
except ValueError:
    print("Eso no es un número")
except ZeroDivisionError:
    print("No se puede dividir entre cero")
```

```
Escribe un número: 0
No se puede dividir entre cero
```

```
Escribe un número: abc
Eso no es un número
```

---

## Ver el mensaje del error con `as`

Si quieres saber exactamente qué pasó, puedes guardar el error en una variable con `as`:

```python
try:
    edad = int("hola")
except ValueError as error:
    print(f"Ocurrió un error: {error}")
```

```
Ocurrió un error: invalid literal for int() with base 10: 'hola'
```

> 💡 Es muy útil mientras estás programando para entender qué salió mal. Para el usuario final, normalmente es mejor mostrar un mensaje más amigable.

---

## `else` y `finally`

Además de `try` y `except`, hay dos partes opcionales:

| Parte | ¿Cuándo se ejecuta? |
|-------|---------------------|
| `try` | Siempre se intenta |
| `except` | Solo si **hubo** un error |
| `else` | Solo si **no hubo** ningún error |
| `finally` | **Siempre**, haya error o no |

```python
try:
    numero = int(input("Escribe un número: "))
except ValueError:
    print("❌ Eso no es un número")
else:
    print(f"✅ Escribiste el número {numero}")
finally:
    print("Gracias por participar")
```

```
Escribe un número: 7
✅ Escribiste el número 7
Gracias por participar
```

```
Escribe un número: siete
❌ Eso no es un número
Gracias por participar
```

> 💡 `finally` se usa para cosas que **deben pasar sí o sí**, como mostrar un mensaje de cierre o liberar algún recurso. Cuando empiezas, lo vas a usar poco; `try` y `except` son lo principal.

---

## Pedir un dato hasta que sea válido

Combinando `while` con `try`, puedes pedir un dato **hasta que el usuario lo escriba bien**. Es uno de los usos más comunes.

```python
while True:
    try:
        edad = int(input("¿Cuántos años tienes? "))
        break
    except ValueError:
        print("Por favor, escribe solo números")

print(f"Perfecto, tienes {edad} años")
```

Resultado en la terminal:

```
¿Cuántos años tienes? veinte
Por favor, escribe solo números
¿Cuántos años tienes? 20a
Por favor, escribe solo números
¿Cuántos años tienes? 20
Perfecto, tienes 20 años
```

Así funciona:

- `while True` repite para siempre.
- Si `int()` funciona, se ejecuta el `break` y sale del ciclo.
- Si `int()` falla, salta al `except`, nunca llega al `break` y vuelve a preguntar.

---

## ✅ Ejemplo: cargar un JSON de forma segura

En el README de JSON revisábamos si el archivo existía con `os.path.exists()`. Con excepciones se puede hacer de otra forma, y además atrapar el caso de que el archivo esté **dañado**:

```python
import json

def cargar_tareas():
    try:
        with open("tareas.json", "r", encoding="utf-8") as archivo:
            return json.loads(archivo.read())
    except FileNotFoundError:
        print("No hay tareas guardadas, empezamos desde cero")
        return []
    except json.JSONDecodeError:
        print("El archivo de tareas está dañado, empezamos desde cero")
        return []

tareas = cargar_tareas()
```

| Situación | ¿Qué pasa? |
|-----------|------------|
| El archivo existe y está bien | Devuelve las tareas |
| El archivo no existe | Atrapa `FileNotFoundError` y devuelve una lista vacía |
| El archivo tiene un JSON mal escrito | Atrapa `json.JSONDecodeError` y devuelve una lista vacía |

> 📌 `json.JSONDecodeError` es el error que da `json.loads()` cuando el texto no tiene un formato JSON válido, por ejemplo si le falta una llave `}` o una coma.

---

## Lanzar tus propios errores con `raise`

A veces el valor es del tipo correcto, pero **no tiene sentido** para tu programa. Por ejemplo, una edad negativa: `int("-5")` funciona sin error, pero nadie tiene -5 años.

Con `raise` puedes **provocar** un error a propósito:

```python
def registrar_edad(edad):
    if edad < 0:
        raise ValueError("La edad no puede ser negativa")
    print(f"Edad registrada: {edad}")

try:
    registrar_edad(-5)
except ValueError as error:
    print(f"Error: {error}")
```

```
Error: La edad no puede ser negativa
```

> 💡 `raise` es útil dentro de funciones: la función avisa que algo está mal, y quien la llamó decide qué hacer con ese error.

---

## Buenas prácticas

- **Atrapa errores específicos.** Usa `except ValueError:` en lugar de `except:`.
- **Pon en el `try` solo lo necesario.** Si pones 50 líneas dentro del `try`, no vas a saber cuál de todas falló.
- **No escondas los errores.** Un `except` que no hace nada (`pass`) hace que el programa falle en silencio y es muy difícil de depurar.
- **Muestra mensajes claros.** "Por favor, escribe solo números" ayuda más al usuario que "Error".
- **No uses `try` para todo.** Si puedes evitar el error con un simple `if` (por ejemplo, revisar si una clave existe con `in`), muchas veces es más claro.

---

## Errores comunes

| Error | Ejemplo incorrecto | Forma correcta |
|-------|-------------------|----------------|
| Usar `except` sin tipo de error | `except:` | `except ValueError:` |
| Olvidar los dos puntos | `try` / `except ValueError` | `try:` / `except ValueError:` |
| Escribir mal el nombre del error | `except valueerror:` | `except ValueError:` (con mayúsculas) |
| Poner `except` sin `try` | Solo `except ValueError:` | Siempre va después de un `try:` |
| Esconder el error sin hacer nada | `except ValueError:`<br>`    pass` | Mostrar un mensaje o manejar el caso |
| Meter todo el programa en un `try` | 50 líneas dentro del `try` | Solo las líneas que pueden fallar |
| Usar la variable del `try` si falló | `try: edad = int("x")`<br>`except: ...`<br>`print(edad)` → `NameError` | Usar la variable en el `else` o dentro del `try` |