# 🧱 Modularidad

## ¿Qué es la modularidad?

La modularidad es **dividir un programa en partes más pequeñas**, donde cada parte se encarga de una sola cosa.

Piensa en una **casa**: no tienes todo en un solo cuarto. La cocina es para cocinar, el baño para bañarse y el dormitorio para dormir. Si algo se daña en la cocina, sabes exactamente dónde ir a arreglarlo.

Con el código pasa lo mismo. En lugar de tener un solo archivo gigante con todo, separas el código en varios archivos, cada uno con su tarea.

### ¿Por qué es importante?

Imagina un programa de 2,000 líneas en un solo archivo. Encontrar un error sería como buscar una aguja en un pajar. Con modularidad:

- **Es más fácil de leer:** cada archivo es corto y tiene un tema claro.
- **Es más fácil de corregir:** si falla algo de los cálculos, sabes que el problema está en el archivo de cálculos.
- **Puedes reutilizar código:** un archivo que escribiste para un proyecto lo puedes usar en otro.
- **Es más fácil trabajar en equipo:** cada persona trabaja en un archivo diferente sin estorbarse (¡y con menos conflictos en Git!).

> 💡 Ya diste el primer paso hacia la modularidad con las **funciones**: separar el código en bloques con nombre. Ahora vas a separar esas funciones en **archivos**.

---

## ¿Qué es un módulo?

Un módulo es simplemente **un archivo `.py`** que tiene funciones, variables o constantes que puedes usar desde otro archivo.

Ya usaste módulos sin darte cuenta:

```python
import json
import os
```

`json` y `os` son módulos que vienen incluidos con Python. Ahora vas a aprender a **crear los tuyos**.

---

## Crear tu propio módulo

**Paso 1:** crea un archivo llamado `operaciones.py` con algunas funciones:

```python
# operaciones.py

def sumar(a, b):
    return a + b

def restar(a, b):
    return a - b

def multiplicar(a, b):
    return a * b
```

**Paso 2:** en la **misma carpeta**, crea otro archivo llamado `main.py` y usa esas funciones:

```python
# main.py

import operaciones

print(operaciones.sumar(5, 3))
print(operaciones.multiplicar(4, 2))
```

**Paso 3:** ejecuta el archivo principal:

```bash
python main.py
```

Resultado en la terminal:

```
8
8
```

La estructura de la carpeta queda así:

```
mi_proyecto/
├── main.py
└── operaciones.py
```

> ⚠️ En el `import` se escribe el nombre del archivo **sin** el `.py`. Es `import operaciones`, no `import operaciones.py`.

> 📌 Al archivo que ejecutas se le suele llamar `main.py` ("principal"). Es el que arranca el programa y usa a los demás módulos.

---

## Formas de importar

| Forma | Ejemplo | ¿Cómo se usa después? |
|-------|---------|-----------------------|
| Importar todo el módulo | `import operaciones` | `operaciones.sumar(5, 3)` |
| Importar solo lo que necesitas | `from operaciones import sumar` | `sumar(5, 3)` |
| Importar varias cosas | `from operaciones import sumar, restar` | `sumar(5, 3)` y `restar(5, 3)` |
| Ponerle un apodo al módulo | `import operaciones as op` | `op.sumar(5, 3)` |

**✅ Ejemplo**

```python
# main.py

from operaciones import sumar, restar

print(sumar(10, 5))
print(restar(10, 5))
```

```
15
5
```

### 📌 ¿Cuál forma usar?

- **`import modulo`**: queda muy claro de dónde viene cada función (`operaciones.sumar`). Es la más recomendable cuando empiezas.
- **`from modulo import funcion`**: es más corto, útil cuando solo necesitas una o dos funciones.
- **`as`**: útil cuando el nombre del módulo es muy largo.

> ⚠️ Vas a ver en algunos tutoriales `from operaciones import *` (importar todo). **Evítalo**: no sabes qué funciones trajiste y si dos módulos tienen una función con el mismo nombre, una reemplaza a la otra sin avisarte.

---

## ✅ Ejemplo completo: la lista de tareas, pero modular

¿Recuerdas la lista de tareas del README de JSON? Tenía todo en un solo archivo. Así quedaría separada en módulos:

```
tareas_app/
├── main.py            → arranca el programa
├── almacenamiento.py  → guarda y carga el archivo JSON
└── tareas.py          → agrega y muestra tareas
```

**`almacenamiento.py`** — solo se encarga de leer y escribir el archivo:

```python
import json
import os

ARCHIVO = "tareas.json"

def cargar():
    if os.path.exists(ARCHIVO):
        with open(ARCHIVO, "r", encoding="utf-8") as archivo:
            return json.loads(archivo.read())
    return []

def guardar(datos):
    texto = json.dumps(datos, indent=4, ensure_ascii=False)
    with open(ARCHIVO, "w", encoding="utf-8") as archivo:
        archivo.write(texto)
```

**`tareas.py`** — solo se encarga de manejar las tareas:

```python
def agregar(lista, texto):
    lista.append({"tarea": texto, "completada": False})

def mostrar(lista):
    print("\nTus tareas:")
    for t in lista:
        print(f"- {t['tarea']}")
```

**`main.py`** — une todo:

```python
import almacenamiento
import tareas

lista = almacenamiento.cargar()

nueva = input("Escribe una tarea: ")
tareas.agregar(lista, nueva)

almacenamiento.guardar(lista)
tareas.mostrar(lista)
```

Fíjate qué corto y fácil de leer quedó `main.py`. Casi se lee como una lista de pasos:

1. Cargar las tareas.
2. Pedir una nueva y agregarla.
3. Guardar.
4. Mostrar.

> 💡 Si mañana decides guardar las tareas en una base de datos en lugar de un JSON, **solo cambias `almacenamiento.py`**. `main.py` y `tareas.py` no se enteran. Ese es el verdadero poder de la modularidad.

---

## Buenas prácticas

- **Un archivo, un tema.** Si un archivo hace muchas cosas distintas, probablemente deberías dividirlo.
- **Nombres claros.** El nombre del archivo debe decir qué contiene: `almacenamiento.py`, `operaciones.py`, `mensajes.py`.
- **Minúsculas y guion bajo.** Igual que las variables y funciones: `manejo_usuarios.py`, no `ManejoUsuarios.py`.
- **Los `import` van al inicio del archivo.** Así se ve rápido de qué depende cada archivo.
- **Usa `if __name__ == "__main__":`** para el código de prueba.

---

## Errores comunes

| Error | Ejemplo incorrecto | Forma correcta |
|-------|-------------------|----------------|
| Poner `.py` en el import | `import operaciones.py` | `import operaciones` |
| El módulo está en otra carpeta | `ModuleNotFoundError: No module named 'operaciones'` | Poner los archivos en la misma carpeta, o ejecutar `main.py` desde la carpeta del proyecto |
| Llamar tu archivo igual que un módulo de Python | Crear un archivo `json.py` o `random.py` | Usar otro nombre: `mis_datos.py`. Si no, Python importa tu archivo en lugar del original |
| Olvidar el nombre del módulo | `import operaciones`<br>`sumar(5, 3)` → `NameError` | `operaciones.sumar(5, 3)` |
| Código de prueba que se ejecuta al importar | `print(...)` suelto en el módulo | Ponerlo dentro de `if __name__ == "__main__":` |
| Dos módulos que se importan entre sí | `a.py` importa `b.py` y `b.py` importa `a.py` | Mover lo que comparten a un tercer archivo |