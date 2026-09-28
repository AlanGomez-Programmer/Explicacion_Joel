# 💾 Archivos JSON (con `dumps` y `loads`)

## ¿Para qué sirve guardar datos en un archivo?

Hasta ahora, todo lo que guardabas en variables **desaparecía** al terminar el programa. Si hacías una lista de compras y cerrabas la terminal, la próxima vez que lo ejecutaras la lista estaba vacía otra vez.

Para que los datos **se queden guardados**, hay que escribirlos en un archivo. Así, la próxima vez que abras el programa, puedes leerlos de nuevo.

---

## ¿Qué es JSON?

JSON es un formato para guardar datos en un **archivo de texto**. Es uno de los formatos más usados en el mundo: casi todas las aplicaciones y páginas web lo usan para guardar y enviar información.

La buena noticia es que **se ve casi igual que un diccionario de Python**:

```json
{
    "nombre": "Julián",
    "edad": 26,
    "activo": true,
    "hobbies": ["fútbol", "música"]
}
```

Si entendiste los diccionarios y las listas, ya entiendes JSON.

### Pequeñas diferencias entre Python y JSON

| Python | JSON |
|--------|------|
| `True` / `False` | `true` / `false` (en minúscula) |
| `None` | `null` |
| Comillas simples o dobles: `'hola'` o `"hola"` | Solo comillas dobles: `"hola"` |
| Diccionario `{ }` | Objeto `{ }` |
| Lista `[ ]` o tupla `( )` | Arreglo `[ ]` |

> 💡 No tienes que preocuparte por estas diferencias: Python las convierte automáticamente con `dumps` y `loads`.

---

## Importar el módulo `json`

Python ya trae todo lo necesario para trabajar con JSON, pero hay que **importarlo** al inicio del archivo:

```python
import json
```

> 📌 Un **módulo** es un archivo con funciones ya hechas que puedes usar en tu programa. `import` le dice a Python: "voy a usar las funciones de este módulo".

---

## `json.dumps()`: de Python a texto

`dumps` convierte un diccionario (o lista) de Python en un **texto** con formato JSON.

> 💡 **Truco para recordarlo:** `dumps` = *dump string* → "vaciar a texto". La **s** del final es de **string**.

```python
import json

persona = {
    "nombre": "Julián",
    "edad": 26,
    "activo": True
}

texto = json.dumps(persona)

print(texto)
print(type(texto))
```

Resultado en la terminal:

```
{"nombre": "Juli\u00e1n", "edad": 26, "activo": true}
<class 'str'>
```

Fíjate en dos cosas: `True` se convirtió en `true`, y el resultado ya no es un diccionario, es un **texto** (`str`).

Pero hay dos problemas: la `á` se ve rara (`\u00e1`) y todo quedó en una sola línea. Eso se arregla con dos opciones.

### Opciones de `dumps`

| Opción | ¿Qué hace? |
|--------|------------|
| `indent=4` | Acomoda el texto en varias líneas con 4 espacios, para que se lea fácil |
| `ensure_ascii=False` | Respeta las tildes y la ñ en lugar de convertirlas en códigos raros |

```python
import json

persona = {
    "nombre": "Julián",
    "edad": 26,
    "activo": True
}

texto = json.dumps(persona, indent=4, ensure_ascii=False)
print(texto)
```

```
{
    "nombre": "Julián",
    "edad": 26,
    "activo": true
}
```

> ⚠️ Como en español usamos tildes y ñ todo el tiempo, **siempre** agrega `ensure_ascii=False`.

---

## `json.loads()`: de texto a Python

`loads` hace lo contrario: toma un **texto** con formato JSON y lo convierte en un diccionario (o lista) de Python.

> 💡 **Truco para recordarlo:** `loads` = *load string* → "cargar desde texto".

```python
import json

texto = '{"nombre": "Julián", "edad": 26, "activo": true}'

persona = json.loads(texto)

print(persona)
print(type(persona))
print(persona["nombre"])
```

Resultado en la terminal:

```
{'nombre': 'Julián', 'edad': 26, 'activo': True}
<class 'dict'>
Julián
```

Ahora sí es un diccionario de verdad, y puedes usarlo como aprendiste en el tema anterior.

### Resumen

```
  Diccionario de Python  ── json.dumps() ──▶  Texto JSON
  Diccionario de Python  ◀── json.loads() ──  Texto JSON
```

---

## Trabajar con archivos

`dumps` y `loads` solo convierten entre diccionario y texto. Para **guardar** ese texto en un archivo o **leerlo**, necesitas abrir el archivo con `open()`.

### Abrir un archivo con `with open()`

```
with open("nombre_archivo", "modo", encoding="utf-8") as archivo:
    código que usa el archivo
```

- **`"nombre_archivo"`**: el nombre del archivo, por ejemplo `"datos.json"`.
- **`"modo"`**: qué quieres hacer con el archivo (ver tabla abajo).
- **`encoding="utf-8"`**: para que las tildes y la ñ se guarden bien.
- **`as archivo`**: el nombre de la variable con la que vas a usar el archivo.

| Modo | Significa | ¿Qué hace? |
|------|-----------|------------|
| `"r"` | *read* (leer) | Abre el archivo para leerlo. Si no existe, da error. |
| `"w"` | *write* (escribir) | Abre el archivo para escribir. Si no existe, lo crea. Si ya existe, **borra todo** lo que tenía. |
| `"a"` | *append* (agregar) | Escribe al final del archivo sin borrar lo que ya tenía. |

> 💡 **¿Por qué `with`?** Cuando terminas de usar un archivo, hay que cerrarlo. `with` lo cierra automáticamente cuando termina el bloque con sangría, así no tienes que acordarte.

---

## Guardar datos en un archivo JSON

Son dos pasos:

1. Convertir el diccionario a texto con `json.dumps()`.
2. Escribir ese texto en el archivo con `archivo.write()`.

**✅ Ejemplo**

```python
import json

persona = {
    "nombre": "Julián",
    "edad": 26,
    "hobbies": ["fútbol", "música"]
}

texto = json.dumps(persona, indent=4, ensure_ascii=False)

with open("persona.json", "w", encoding="utf-8") as archivo:
    archivo.write(texto)

print("Datos guardados")
```

Resultado en la terminal:

```
Datos guardados
```

Y en la misma carpeta aparece un archivo nuevo llamado `persona.json` con esto:

```json
{
    "nombre": "Julián",
    "edad": 26,
    "hobbies": [
        "fútbol",
        "música"
    ]
}
```

---

## Leer datos de un archivo JSON

También son dos pasos, pero al revés:

1. Leer el texto del archivo con `archivo.read()`.
2. Convertir ese texto a diccionario con `json.loads()`.

**✅ Ejemplo**

```python
import json

with open("persona.json", "r", encoding="utf-8") as archivo:
    texto = archivo.read()

persona = json.loads(texto)

print(persona["nombre"])
print(persona["hobbies"])
```

Resultado en la terminal:

```
Julián
['fútbol', 'música']
```

### Resumen de los dos procesos

| | Guardar | Leer |
|-|---------|------|
| Paso 1 | `texto = json.dumps(datos)` | `texto = archivo.read()` |
| Paso 2 | `archivo.write(texto)` | `datos = json.loads(texto)` |
| Modo del archivo | `"w"` | `"r"` |

---

## ¿Y si el archivo no existe?

Si intentas leer un archivo que no existe, Python da error:

```
FileNotFoundError: [Errno 2] No such file or directory: 'persona.json'
```

Esto pasa mucho la primera vez que ejecutas un programa, porque todavía no has guardado nada. Para evitarlo, puedes revisar primero si el archivo existe con `os.path.exists()`:

```python
import json
import os

if os.path.exists("persona.json"):
    with open("persona.json", "r", encoding="utf-8") as archivo:
        persona = json.loads(archivo.read())
    print(persona)
else:
    print("Todavía no hay datos guardados")
```

---

## ✅ Ejemplo completo: lista de tareas que se guarda

Este programa carga las tareas guardadas, agrega una nueva y las vuelve a guardar. Cada vez que lo ejecutes, las tareas anteriores seguirán ahí.

```python
import json
import os

ARCHIVO = "tareas.json"

def cargar_tareas():
    if os.path.exists(ARCHIVO):
        with open(ARCHIVO, "r", encoding="utf-8") as archivo:
            return json.loads(archivo.read())
    return []

def guardar_tareas(tareas):
    texto = json.dumps(tareas, indent=4, ensure_ascii=False)
    with open(ARCHIVO, "w", encoding="utf-8") as archivo:
        archivo.write(texto)

# 1. Cargar lo que ya estaba guardado
tareas = cargar_tareas()

# 2. Pedir una tarea nueva y agregarla
nueva = input("Escribe una tarea: ")
tareas.append({"tarea": nueva, "completada": False})

# 3. Guardar todo de nuevo
guardar_tareas(tareas)

# 4. Mostrar todas las tareas
print("\nTus tareas:")
for t in tareas:
    print(f"- {t['tarea']}")
```

Resultado en la terminal (ejecutándolo dos veces):

```
Escribe una tarea: Estudiar Python

Tus tareas:
- Estudiar Python
```

```
Escribe una tarea: Hacer ejercicio

Tus tareas:
- Estudiar Python
- Hacer ejercicio
```

Y el archivo `tareas.json` queda así:

```json
[
    {
        "tarea": "Estudiar Python",
        "completada": false
    },
    {
        "tarea": "Hacer ejercicio",
        "completada": false
    }
]
```

> 💡 Fíjate que usamos el modo `"w"` y no `"a"`. Como `json.dumps()` convierte **toda** la lista cada vez, lo correcto es reemplazar el archivo completo. Si usaras `"a"`, se pegaría un JSON detrás de otro y el archivo quedaría dañado.

---

## Bonus: `dump` y `load` (sin la "s")

Existen también `json.dump()` y `json.load()`, que hacen los dos pasos en uno: trabajan directamente con el archivo, sin pasar por el texto.

| Con la "s" (esta guía) | Sin la "s" |
|------------------------|------------|
| `archivo.write(json.dumps(datos))` | `json.dump(datos, archivo)` |
| `json.loads(archivo.read())` | `json.load(archivo)` |

Hacen lo mismo. Aprender primero con `dumps` y `loads` ayuda a entender qué pasa en cada paso. Además, `dumps` y `loads` también sirven cuando los datos no vienen de un archivo, por ejemplo cuando llegan desde internet.

---

## Errores comunes

| Error | Ejemplo incorrecto | Forma correcta |
|-------|-------------------|----------------|
| Olvidar importar `json` | `json.dumps(datos)` → `NameError` | Escribir `import json` al inicio |
| Escribir el diccionario directo al archivo | `archivo.write(persona)` → `TypeError` | `archivo.write(json.dumps(persona))` |
| Usar el diccionario sin convertirlo | `texto["nombre"]` sobre el texto leído | `json.loads(texto)["nombre"]` |
| Tildes que se ven raras (`\u00e1`) | `json.dumps(datos)` | `json.dumps(datos, ensure_ascii=False)` |
| Leer un archivo que no existe | `open("x.json", "r")` → `FileNotFoundError` | Revisar antes con `os.path.exists()` |
| Usar `"a"` para guardar JSON | `open("datos.json", "a")` | `open("datos.json", "w")` |
| Confundir cuál es cuál | Usar `loads` para guardar | `dumps` → guardar, `loads` → leer |