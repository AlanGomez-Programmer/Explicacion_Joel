# Explicaciones sobre Python 🐍

## Python es un lenguaje de tipado dinámico

Suena complicado, pero la idea es sencilla: **no tienes que decirle a Python qué tipo de dato vas a guardar en una variable**. Python lo descubre solo, viendo el valor que le pones.

```python
nombre = "Ana"     # Python sabe que es texto
edad = 25          # Python sabe que es un número entero
precio = 9.99      # Python sabe que es un número con decimales
activo = True      # Python sabe que es verdadero/falso
```

Incluso una misma variable puede cambiar de tipo:

```python
dato = 10        # ahora es un número
dato = "hola"    # ahora es texto
```

En otros lenguajes tendrías que escribir algo como `int edad = 25` para indicar que es un número. En Python no hace falta.

---

## 📌 ¿Qué es un intérprete?

El intérprete es el programa que lee tu código y lo va ejecutando **de arriba hacia abajo, línea por línea**.

Si en alguna línea encuentra un error, se detiene ahí y te dice en qué línea fue. Las líneas que estaban antes sí se ejecutaron, pero las que siguen ya no.

```python
print("Hola")        # ✅ se ejecuta
print(10 / 0)        # ❌ error: no se puede dividir entre cero, aquí se detiene
print("Adiós")       # ⛔ nunca llega a ejecutarse
```
