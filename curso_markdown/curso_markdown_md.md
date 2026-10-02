<div align="center">

<h1> 📚 Curso de Markdown </h1>

*Guía completa para aprender a escribir en Markdown, desde lo básico hasta lo avanzado.*

</div>

<br>

## Índice

- [Índice](#índice)
- [1. ¿Qué es Markdown?](#1-qué-es-markdown)
- [2. Encabezados](#2-encabezados)
- [3. Énfasis (negrita, cursiva, tachado)](#3-énfasis-negrita-cursiva-tachado)
- [4. Listas](#4-listas)
  - [Listas no ordenadas](#listas-no-ordenadas)
  - [Listas ordenadas](#listas-ordenadas)
  - [Listas anidadas](#listas-anidadas)
- [5. Enlaces](#5-enlaces)
- [6. Imágenes](#6-imágenes)
- [7. Citas](#7-citas)
- [8. Código](#8-código)
  - [Código en línea](#código-en-línea)
  - [Bloques de código](#bloques-de-código)
- [9. Líneas horizontales](#9-líneas-horizontales)
- [10. Tablas](#10-tablas)
  - [Alineación de columnas](#alineación-de-columnas)
- [11. Tareas (checklists)](#11-tareas-checklists)
- [12. Notas al pie](#12-notas-al-pie)
- [13. Escapar caracteres](#13-escapar-caracteres)
- [14. HTML dentro de Markdown](#14-html-dentro-de-markdown)
- [15. Buenas prácticas](#15-buenas-prácticas)
- [16. Ejercicios finales](#16-ejercicios-finales)

<br>

## 1. ¿Qué es Markdown?

Markdown es un lenguaje de marcado ligero creado por John Gruber en 2004. Permite dar formato a texto plano usando símbolos simples, que luego se convierten en HTML u otros formatos.

**¿Por qué usarlo?**

- Es fácil de leer incluso sin renderizar.
- Se usa en GitHub, GitLab, Notion, Discord, foros, blogs, documentación técnica, etc.
- Se puede convertir a PDF, HTML, Word y más.

Los archivos Markdown usan la extensión `.md` o `.markdown`.

---

## 2. Encabezados

Se crean con el símbolo `#`. Cuantos más `#`, menor el nivel del encabezado (de H1 a H6).

```markdown
# Encabezado 1
## Encabezado 2
### Encabezado 3
#### Encabezado 4
##### Encabezado 5
###### Encabezado 6
```

**Resultado:**

- # Encabezado 1
- ## Encabezado 2
- ### Encabezado 3

> 💡 Deja siempre un espacio entre `#` y el texto.

---

## 3. Énfasis (negrita, cursiva, tachado)

| Estilo | Sintaxis | Resultado |
|---|---|---|
| Cursiva | `*texto*` o `_texto_` | *texto* |
| Negrita | `**texto**` o `__texto__` | **texto** |
| Negrita + cursiva | `***texto***` | ***texto*** |
| Tachado | `~~texto~~` | ~~texto~~ |

```markdown
Esto es *cursiva*, esto es **negrita**, y esto es ~~tachado~~.
```

---

## 4. Listas

### Listas no ordenadas

Se usan `-`, `*` o `+` (elige uno y sé consistente):

```markdown
- Manzana
- Banana
- Naranja
```

- Manzana
- Banana
- Naranja

### Listas ordenadas

```markdown
1. Primero
2. Segundo
3. Tercero
```

1. Primero
2. Segundo
3. Tercero

### Listas anidadas

```markdown
- Frutas
  - Manzana
  - Banana
- Verduras
  - Zanahoria
  - Espinaca
```

- Frutas
  - Manzana
  - Banana
- Verduras
  - Zanahoria
  - Espinaca

---

## 5. Enlaces

```markdown
[Texto del enlace](https://www.ejemplo.com)
[Enlace con título](https://www.ejemplo.com "Título al pasar el mouse")
```

[Texto del enlace](https://www.ejemplo.com)

También existen enlaces de referencia:

```markdown
Visita [este sitio][1] para más información.

[1]: https://www.ejemplo.com
```

---

## 6. Imágenes

Igual que los enlaces, pero con `!` al inicio:

```markdown
![Texto alternativo](https://ejemplo.com/imagen.png)
```

Con título:

```markdown
![Texto alternativo](https://ejemplo.com/imagen.png "Título de la imagen")
```

---

## 7. Citas

Se usan con `>`:

```markdown
> Esto es una cita.
> Puede tener varias líneas.
>
> Y párrafos separados.
```

> Esto es una cita.
> Puede tener varias líneas.

Las citas se pueden anidar:

```markdown
> Cita nivel 1
>> Cita nivel 2
```

---

## 8. Código

### Código en línea

Se usa una comilla invertida (backtick):

```markdown
Usa la función `print()` para mostrar texto.
```

Usa la función `print()` para mostrar texto.

### Bloques de código

Se usan tres backticks, opcionalmente con el nombre del lenguaje para resaltado de sintaxis:

````markdown
```python
def saludo(nombre):
    print(f"Hola, {nombre}")
```
````

```python
def saludo(nombre):
    print(f"Hola, {nombre}")
```

---

## 9. Líneas horizontales

Se crean con tres o más guiones, asteriscos o guiones bajos:

```markdown
---
***
___
```

---

## 10. Tablas

```markdown
| Nombre | Edad | Ciudad |
|--------|------|--------|
| Ana    | 28   | Madrid |
| Luis   | 34   | Bogotá |
```

| Nombre | Edad | Ciudad |
|--------|------|--------|
| Ana    | 28   | Madrid |
| Luis   | 34   | Bogotá |

### Alineación de columnas

```markdown
| Izquierda | Centro | Derecha |
|:----------|:------:|--------:|
| A         | B      | C       |
```

- `:---` alinea a la izquierda
- `:---:` centra
- `---:` alinea a la derecha

---

## 11. Tareas (checklists)

Muy usado en GitHub:

```markdown
- [x] Tarea completada
- [ ] Tarea pendiente
- [ ] Otra tarea pendiente
```

- [x] Tarea completada
- [ ] Tarea pendiente
- [ ] Otra tarea pendiente

---

## 12. Notas al pie

```markdown
Este es un texto con una nota al pie[^1].

[^1]: Esta es la explicación de la nota.
```

> ⚠️ No todos los procesadores de Markdown soportan esta sintaxis (por ejemplo, GitHub sí, pero otros no).

---

## 13. Escapar caracteres

Para mostrar un símbolo especial sin que se interprete como formato, usa `\` antes del símbolo:

```markdown
\*Esto no será cursiva\*
\# Esto no será un encabezado
```

\*Esto no será cursiva\*

Caracteres que suelen necesitar escape: `\ ` `` ` `` `*` `_` `{ }` `[ ]` `( )` `#` `+` `-` `.` `!`

---

## 14. HTML dentro de Markdown

La mayoría de los procesadores permiten mezclar HTML directamente:

```markdown
Este texto es <strong>negrita usando HTML</strong>.

<br>

<details>
<summary>Haz clic para expandir</summary>
Contenido oculto aquí.
</details>
```

Esto es útil para cosas que Markdown no soporta nativamente, como detalles colapsables o saltos de línea forzados.

---

## 15. Buenas prácticas

- Usa un solo `#` por documento como título principal (H1).
- Sé consistente con el símbolo de listas (`-` o `*`, no mezcles).
- Deja líneas en blanco entre bloques (párrafos, listas, encabezados) para evitar errores de renderizado.
- Usa nombres de lenguaje en los bloques de código para resaltado de sintaxis.
- Evita saltos de línea simples para separar párrafos; usa una línea en blanco.
- Verifica el resultado renderizado antes de publicar (por ejemplo, con la vista previa de GitHub o VS Code).

---

## 16. Ejercicios finales

Practica escribiendo un archivo Markdown que incluya:

1. Un título principal y al menos dos subtítulos.
2. Un párrafo con texto en negrita, cursiva y tachado.
3. Una lista ordenada y una no ordenada anidada.
4. Un enlace y una imagen.
5. Una tabla con al menos 3 columnas.
6. Un bloque de código en el lenguaje de tu preferencia.
7. Una checklist con al menos 3 tareas.
8. Una cita.

Cuando termines, revisa el resultado en un visor de Markdown (GitHub, VS Code, Typora, o cualquier editor online como [StackEdit](https://stackedit.io/)).

<br>

---

<div align="center">

<h2> Developer </h2>

<h3> Felipe Andrés Ruiz Rojas </h3>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-linkedin.com%2Fin%2Fruizrojasfel-blue)](https://www.linkedin.com/in/ruizrojasfel) [![Website](https://img.shields.io/badge/Website-felruiz--dev.netlify.app-lightblue)](https://felruiz-dev.netlify.app/)

Copyright © 2026 Fel Ruiz
</div>
