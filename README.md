# 📚 Cómo utilizar este repositorio

¡Bienvenido! Este repositorio es una guía para aprender programación **desde cero**, paso a paso y con explicaciones sencillas.

Aquí vas a encontrar explicaciones de cada tema con ejemplos que puedes copiar y probar, y ejercicios para practicar lo que aprendiste.

---

## 🗂️ ¿Cómo está organizado?

En la parte principal del repositorio vas a encontrar **una carpeta por cada tema**. Cada carpeta tiene archivos numerados, para que sepas en qué orden leerlos.

```
Explicacion_Joel/
├── README.md          → Esta guía (lo que estás leyendo)
├── git/               → Tema: Git y GitHub
├── Python/            → Tema: Python
│   └── Ejercicios/    → Ejercicios para practicar Python
│       └── Resoluciones/  → Soluciones de los ejercicios
├── PDF's/             → Explicaciones en formato PDF
└── imgs/              → Imágenes que usan las explicaciones
```

| Carpeta | ¿Qué tiene? |
|---------|-------------|
| 📁 `git/` | Qué es Git, cómo funcionan las ramas y los pasos para usarlo en un proyecto real. |
| 📁 `Python/` | Todos los temas de Python, desde instalarlo hasta manejar errores. |
| 📁 `Python/Ejercicios/` | Problemas para que practiques lo que aprendiste. |
| 📁 `PDF's/` | Versiones en PDF de algunas explicaciones, por si prefieres leerlas o imprimirlas. |
| 📁 `imgs/` | Las imágenes que aparecen dentro de las explicaciones. **No necesitas abrir esta carpeta**, las imágenes se ven solas en cada tema. |

### 🔜 Próximamente

Estos temas se van a agregar más adelante, cada uno con su propia carpeta:

- 🌐 **HTML**: la estructura de una página web.
- 🎨 **CSS**: los estilos de una página web (colores, tamaños, posiciones).

---

## 🧭 ¿Por dónde empiezo?

Te recomiendo seguir este orden. Cada tema usa cosas del anterior, así que es mejor no saltarse ninguno.

### 1️⃣ Git

Empieza por aquí. Git es la herramienta que vas a usar para guardar tu trabajo y para practicar los ejercicios.

| # | Tema | ¿Qué vas a aprender? |
|---|------|----------------------|
| 01 | [Guía de Git](git/01_git.md) | Qué es Git, repositorios, commits, ramas y los comandos principales |
| 02 | [Pasos para usar Git](git/02_pasos.md) | Crear un repositorio en GitHub, clonarlo y trabajar con ramas paso a paso |

> 📄 También puedes leer la explicación de Git en PDF: [Git.pdf](PDF's/Git.pdf)

### 2️⃣ Python

| # | Tema | ¿Qué vas a aprender? |
|---|------|----------------------|
| 01 | [Instalación](Python/01_instalacion.md) | Instalar Python en Windows o Linux |
| 02 | [¿Qué es Python?](Python/02_explicacion.md) | Tipado dinámico y qué es un intérprete |
| 03 | [Variables](Python/03_variables.md) | Guardar datos y los tipos de datos básicos |
| 04 | [Operadores](Python/04_operadores.md) | Hacer cuentas, comparar valores y combinar condiciones |
| 05 | [Estructuras de decisión](Python/05_estructuras_desicion.md) | `if`, `elif` y `else`: que el programa tome decisiones |
| 06 | [Ciclos](Python/06_ciclos.md) | `for` y `while`: repetir código |
| 07 | [Funciones](Python/07_funciones.md) | Crear bloques de código reutilizables |
| 08 | [Listas y tuplas](Python/08_listas.md) | Guardar varios valores en una sola variable |
| 09 | [Diccionarios](Python/09_diccionarios.md) | Guardar datos con nombre (clave y valor) |
| 10 | [Archivos JSON](Python/10_archivos_texto.md) | Guardar y leer datos en archivos con `dumps` y `loads` |
| 11 | [Modularidad](Python/11_modularidad.md) | Dividir un programa en varios archivos |
| 12 | [Manejo de excepciones](Python/12_excepcion_errores.md) | Atrapar errores para que el programa no se caiga |

---

## 📖 ¿Cómo estudiar cada tema?

1. **Lee la explicación con calma.** No tienes que memorizar todo; la idea es entender para qué sirve cada cosa.
2. **Copia los ejemplos y ejecútalos.** Crea un archivo `.py`, pega el ejemplo y ejecútalo en la terminal. Ver el resultado con tus propios ojos ayuda mucho más que solo leerlo.
3. **Cambia los ejemplos.** Pon otros números, otros textos, quita una línea... y mira qué pasa. Equivocarse es parte de aprender.
4. **Revisa la sección "Errores comunes".** Casi todos los temas la tienen al final. Si algo no te funciona, probablemente la respuesta esté ahí.

### Lo que significan los íconos

En las explicaciones vas a ver estos íconos:

| Ícono | Significado |
|-------|-------------|
| ✅ | Ejemplo de código que puedes probar |
| 💡 | Un consejo o dato útil |
| ⚠️ | Cuidado: algo que suele causar errores |
| 📌 | Una aclaración importante |

---

## 🏋️ Ejercicios

En la carpeta [`Python/Ejercicios/`](Python/Ejercicios/) hay ejercicios para que pongas en práctica todo lo que aprendiste. Cada ejercicio es un problema de la vida real que tienes que resolver escribiendo tu propio programa.

| Ejercicio | ¿De qué trata? | Temas que necesitas |
|-----------|----------------|---------------------|
| [Ejercicio 1](Python/Ejercicios/Ejercicio1.md) | Un sistema para que una tienda pueda agregar, ver, modificar y eliminar productos | Variables, decisiones, ciclos, funciones y diccionarios |

> 📌 **CRUD** significa *Create, Read, Update, Delete* (Crear, Leer, Actualizar, Eliminar). Son las cuatro operaciones básicas que hace casi cualquier sistema con datos.

### ¿Cómo resolver un ejercicio?

1. **Lee todo el enunciado** antes de empezar a escribir código. Fíjate bien en los requisitos.
2. **Divide el problema en partes.** Por ejemplo, en el Ejercicio 1 primero haz solo el menú, luego la opción de agregar, después la de listar, y así.
3. **Prueba cada parte** antes de pasar a la siguiente.
4. **Si te trabas, regresa a la explicación del tema.** Por ejemplo, si no recuerdas cómo recorrer un diccionario, vuelve a leer [Diccionarios](Python/09_diccionarios.md).
5. **Cuando termines, compara** tu respuesta con la de la carpeta `Resoluciones/`.

> ⚠️ **Intenta resolverlo antes de ver la solución.** Aunque te tardes, es la mejor forma de aprender. No hay una sola respuesta correcta: si tu programa hace lo que pide el ejercicio, está bien, aunque sea diferente a la solución.

### 💡 Practica Git mientras resuelves

Aprovecha los ejercicios para practicar también lo que aprendiste de Git:

1. Crea **tu propio repositorio** en GitHub para guardar tus soluciones (sigue los pasos de [Pasos para usar Git](git/02_pasos.md)).
2. Crea la rama `develop`.
3. Para cada ejercicio, crea una rama nueva desde `develop`, por ejemplo `feature/ejercicio-1`.
4. Ve haciendo **commits** cada vez que termines una parte (el menú, agregar productos, listar...).
5. Cuando termines, une tu rama a `develop` con un **merge**.

Así, al final vas a tener tus ejercicios guardados en la nube y un historial de todo tu avance.

---

## 💻 ¿Cómo tener este repositorio en tu computadora?

Tienes dos opciones:

**Opción 1: Descargarlo como ZIP (la más fácil)**

1. En la página del repositorio en GitHub, da clic en el botón verde **`<> Code`**.
2. Elige **Download ZIP**.
3. Descomprime el archivo en tu computadora.

**Opción 2: Clonarlo con Git (recomendada después de leer el tema de Git)**

```bash
git clone https://github.com/AlanGomez-Programmer/Explicacion_Joel.git
```

> 💡 Si lo clonas con Git, cada vez que se agreguen temas o ejercicios nuevos solo tienes que entrar a la carpeta y escribir `git pull` para recibirlos.

### Leer las explicaciones

- **En GitHub:** da clic en cualquier archivo `.md` y se verá con formato, tablas e imágenes.
- **En Visual Studio Code:** abre el archivo `.md` y presiona `Ctrl` + `Shift` + `V` para ver la vista previa con formato.

---

## 🙋 ¿Tienes dudas?

Es normal no entender todo a la primera. Si algo no queda claro:

- Vuelve a leer el tema con calma y prueba los ejemplos otra vez.
- Revisa la sección de **errores comunes** del tema.
- Y si sigues con dudas, ¡pregunta! es un gusto ayudarte. 😄

**¡Mucho éxito aprendiendo! 🚀**