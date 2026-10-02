<div align="center">

<h1> 📚 Python aplicado a finanzas </h1>

*Curso introductorio de programación · 14 módulos*

![Python](https://img.shields.io/badge/python-3.11%2B-blue)
![Licencia](https://img.shields.io/badge/licencia-MIT-green)

Curso de Python **desde cero** con aplicaciones financieras. Cubre los elementos del lenguaje —variables, tipos de datos, operadores, condicionales, bucles, estructuras de datos y funciones—, las librerías de análisis numérico y gráfico, y los cálculos financieros que se resuelven con ellas.

No se requiere experiencia previa en programación.

</div>


<br>


## Contenidos

| # | Módulo | Temas |
|---|--------|-------|
| 0 | [Preparación](#módulo-0--preparación) | Instalación, primer programa |
| 1 | [Variables](#módulo-1--variables) | Asignación, nombres, memoria |
| 2 | [Tipos de datos](#módulo-2--tipos-de-datos) | Numéricos, texto, booleanos, `None` |
| 3 | [Operadores](#módulo-3--operadores) | Aritméticos, comparación, lógicos |
| 4 | [Condicionales](#módulo-4--condicionales) | `if`, `elif`, `else` |
| 5 | [Bucles](#módulo-5--bucles) | `for`, `while`, `break`, `continue` |
| 6 | [Estructuras de datos](#módulo-6--estructuras-de-datos) | Listas, tuplas, diccionarios, conjuntos |
| 7 | [Funciones](#módulo-7--funciones) | Definición, parámetros, alcance |
| 8 | [Librerías](#módulo-8--librerías) | Importación, catálogo financiero |
| 9 | [NumPy](#módulo-9--numpy) | Arreglos y cálculo vectorizado |
| 10 | [pandas](#módulo-10--pandas) | Series, DataFrames, archivos |
| 11 | [Gráficos con matplotlib](#módulo-11--gráficos-con-matplotlib) | Los siete gráficos principales |
| 12 | [Cálculos financieros fundamentales](#módulo-12--cálculos-financieros-fundamentales) | Interés, VAN, TIR, retornos, riesgo, bonos |
| 13 | [Proyecto final](#módulo-13--proyecto-final) | Integración |

Anexos: [Símbolos](#anexo-a--tabla-de-símbolos) · [Errores frecuentes](#anexo-b--errores-frecuentes-y-cómo-leerlos) · [Comportamientos que sorprenden](#anexo-c--quince-comportamientos-que-sorprenden) · [Convenciones de escritura](#anexo-d--convenciones-de-escritura) · [Formulario](#anexo-e--formulario) · [Qué sigue](#qué-sigue)


<br>


## Cómo usar este material

Cada módulo tiene la misma organización:

1. **Explicación** con ejemplos ejecutables.
2. **Cómo funciona por dentro** — qué hace Python realmente al correr esa línea.
3. **Errores frecuentes** — las equivocaciones habituales y su causa.
4. **Ejercicios** — de menor a mayor dificultad.

Todo el código está pensado para escribirse y ejecutarse. Leer programación sin escribirla no funciona: abra el intérprete, pruebe cada ejemplo y modifíquelo para ver qué cambia.

---

## Módulo 0 — Preparación

### Instalación

Descargue Python 3.11 o superior desde [python.org](https://www.python.org/downloads/), o instale [Anaconda](https://www.anaconda.com/download), que ya incluye las librerías del curso. Verifique en la terminal:

```bash
python --version
# Python 3.11.8
```

Instale el entorno de trabajo y las librerías:

```bash
pip install jupyterlab numpy pandas matplotlib seaborn scipy numpy-financial openpyxl
jupyter lab
```

### Dónde escribir el código

| Entorno | Cuándo conviene |
|---|---|
| **Jupyter Notebook** | Análisis exploratorio, mezclar código con texto y gráficos. El del curso. |
| **Archivo `.py`** | Programas completos y reutilizables. |
| **Consola interactiva** | Probar una línea suelta. |

### Primer programa

```python
print("Hola")

precio = 2340
cantidad = 150
print(precio * cantidad)        # 351000
```

### Tres reglas de escritura

**1. La indentación forma parte del programa.** Los bloques se delimitan con espacios —cuatro por nivel—, no con llaves.

```python
if precio > 100:
    print("Caro")        # dentro del if
    print("Vender")      # dentro del if
print("Fin")             # fuera del if
```

**2. Los dos puntos abren un bloque.** Todo `if`, `for`, `while`, `def` y `class` termina en `:` y la línea siguiente va indentada.

**3. El numeral inicia un comentario.** Python ignora el resto de la línea.

```python
precio = 100    # precio de cierre en dólares
```

### Cómo funciona por dentro

Python lee el archivo **línea por línea, de arriba hacia abajo**, y ejecuta cada una antes de pasar a la siguiente. No hay compilación previa.

```python
print(precio)     # NameError: 'precio' todavía no existe
precio = 100
print(precio)     # 100
```

Esto tiene una consecuencia práctica en Jupyter: lo que manda es el **orden en que ejecutó las celdas**, no el orden en que se ven. Si ejecuta la celda 5 y después la 2, Python obedece esa secuencia. Antes de entregar cualquier trabajo use `Kernel → Restart & Run All` y confirme que todo corre limpio de arriba abajo.

### Errores frecuentes

```python
# Olvidar los dos puntos
if precio > 100
    print("caro")       # SyntaxError: expected ':'

# Indentar sin motivo
precio = 100
    print(precio)       # IndentationError: unexpected indent

# Mezclar tabulaciones y espacios → TabError
```

Configure el editor para insertar 4 espacios al presionar Tab. JupyterLab ya lo hace.

### Ejercicios

1. Calcule e imprima el valor de 150 acciones a $2.340 cada una.
2. Provoque a propósito un `SyntaxError`, un `IndentationError` y un `NameError`, y copie los tres mensajes.
3. En un notebook escriba `x = 1` en una celda y `print(x + y)` en otra. Ejecute la segunda primero y explique el mensaje.

---

## Módulo 1 — Variables

Una variable es un **nombre** asociado a un valor, para poder reutilizarlo.

```python
precio = 2340
cantidad = 150
ticker = "SQM-B"

valor_posicion = precio * cantidad
print(valor_posicion)          # 351000
```

El signo `=` no es una igualdad matemática: es una **instrucción de asignación** que se lee de derecha a izquierda. "Calcula lo de la derecha y llámalo con el nombre de la izquierda".

```python
saldo = 1000
saldo = saldo + 500        # válido: calcula 1500 y lo vuelve a llamar 'saldo'
```

### Reglas para los nombres

```python
# Válidos
precio_cierre = 2340
tasa_2024 = 0.045
_interno = "auxiliar"

# Inválidos
2024_tasa = 0.045      # SyntaxError: no puede empezar con un número
precio-cierre = 2340   # SyntaxError: el guión es el operador resta
class = "A"            # SyntaxError: 'class' es palabra reservada
```

Las **mayúsculas importan**: `Precio` y `precio` son variables distintas.

Convención: minúsculas con guión bajo (`precio_cierre`) para variables, y mayúsculas para valores fijos (`TASA_MAXIMA = 0.30`).

### Un nombre descriptivo ahorra horas

```python
# Ilegible
x = 2340
y = 150
z = x * y

# Claro
precio_unitario = 2340
cantidad_acciones = 150
valor_total = precio_unitario * cantidad_acciones
```

### Cómo funciona por dentro

Esta parte no es un detalle técnico: explica la mitad de los errores difíciles de Python.

Cuando escribe `precio = 100`, Python hace dos cosas: crea un **objeto** con el valor 100 en la memoria, y ata el **nombre** `precio` a ese objeto, como una etiqueta pegada encima. El nombre no contiene el valor: **apunta** a él. Y dos nombres pueden apuntar al mismo objeto.

```python
a = [10, 20, 30]      # crea una lista y le pega la etiqueta 'a'
b = a                 # NO copia la lista: le pega una segunda etiqueta

b.append(40)          # modifica el objeto

print(a)              # [10, 20, 30, 40]  ← 'a' también cambió
```

Con números y texto el problema no aparece, porque esos objetos no se pueden modificar: al operar sobre ellos, Python crea uno nuevo.

```python
a = 100
b = a
b = b + 50
print(a)              # 100  ← intacto
```

La diferencia depende de si el objeto es **modificable** (listas, diccionarios, conjuntos) o **no modificable** (números, texto, booleanos, tuplas).

Para obtener una copia real de una lista:

```python
original = ["AAPL", "MSFT"]

copia = original.copy()       # también sirve list(original) u original[:]
copia.append("TSLA")
print(original)               # ['AAPL', 'MSFT']  ← intacto
```

### Errores frecuentes

```python
# 1. Creer que asignar copia
saldos_iniciales = [1000, 2000]
saldos_finales = saldos_iniciales      # no es una copia
saldos_finales[0] = 0
print(saldos_iniciales[0])             # 0  ← el "inicial" ya no es inicial

# 2. Usar nombres que Python ya ocupa
list = [1, 2, 3]      # ahora list() deja de funcionar
sum = 0               # ahora sum() no puede sumar
# Evite: list, dict, sum, max, min, type, str, int, id, input, next
```

### Ejercicios

1. Cree variables para tres acciones con su precio y cantidad, y calcule el valor total invertido.
2. Prediga la salida antes de ejecutar, y luego compruebe:
   ```python
   x = [1, 2]
   y = x
   z = x.copy()
   x.append(3)
   print(y, z)
   ```
3. Explique por qué `a = 5; b = a; b = 10` deja `a` en 5, pero `a = [5]; b = a; b[0] = 10` deja `a` en `[10]`.

---

## Módulo 2 — Tipos de datos

Cada valor pertenece a un tipo, que determina qué operaciones admite.

| Tipo | Nombre | Ejemplo | Uso financiero |
|---|---|---|---|
| Entero | `int` | `150` | Cantidad de acciones, número de períodos |
| Decimal | `float` | `2340.50` | Precios, tasas, retornos |
| Texto | `str` | `"SQM-B"` | Tickers, nombres, fechas en bruto |
| Lógico | `bool` | `True` | Condiciones, filtros |
| Nulo | `NoneType` | `None` | Dato ausente o no calculado |

Consulte el tipo de cualquier valor con `type()`:

```python
type(150)          # <class 'int'>
type(2340.50)      # <class 'float'>
type("SQM-B")      # <class 'str'>
type(True)         # <class 'bool'>
type(None)         # <class 'NoneType'>
```

### Números

```python
cantidad = 150               # int: entero, sin límite de tamaño
precio = 2340.50             # float: con decimales
capital = 1_000_000          # el guión bajo es solo legibilidad: vale 1000000
notacion = 1.5e6             # 1500000.0
```

**Los decimales no son exactos.** Se almacenan en binario, y muchos números decimales no tienen representación binaria finita, igual que 1/3 no la tiene en decimal:

```python
0.1 + 0.2                # 0.30000000000000004
0.1 + 0.2 == 0.3         # False
```

No es un defecto de Python: ocurre en todo lenguaje que use el estándar de punto flotante. La consecuencia práctica es que **nunca se comparan decimales con `==`**:

```python
import math
math.isclose(0.1 + 0.2, 0.3)          # True
abs((0.1 + 0.2) - 0.3) < 1e-9         # True
```

Cuando el resultado debe cuadrar al peso —una liquidación, una factura, una conciliación— use `Decimal`:

```python
from decimal import Decimal, ROUND_HALF_UP

Decimal("0.1") + Decimal("0.2") == Decimal("0.3")     # True

monto = Decimal("1234.5678")
monto.quantize(Decimal("0.01"), rounding=ROUND_HALF_UP)   # Decimal('1234.57')
```

> Criterio: `float` para modelar y estimar, `Decimal` para dinero que se paga.

Cuidado también con el redondeo: Python resuelve los empates hacia el número par, que es el estándar internacional pero no el que se enseña en la escuela.

```python
round(2.5)      # 2   ← no 3
round(3.5)      # 4
```

### Texto

```python
ticker = "SQM-B"
nombre = 'Soquimich'          # comillas simples o dobles: equivalentes
largo = """Texto de
varias líneas"""
```

El texto es **no modificable**: todos sus métodos devuelven una cadena nueva.

```python
nombre = "soquimich"
nombre.upper()          # 'SOQUIMICH'
print(nombre)           # 'soquimich'  ← sin cambios

nombre = nombre.upper() # para conservar el resultado hay que reasignar
```

**Posiciones y trozos.** Se cuenta desde cero, y el límite superior no se incluye:

```python
codigo = "CL0000001980"
#         012345678901

codigo[0]        # 'C'
codigo[-1]       # '0'            última posición
codigo[0:2]      # 'CL'           desde 0 hasta 2 sin incluir el 2
codigo[2:]       # '0000001980'
codigo[-4:]      # '1980'         últimos cuatro
```

Regla útil: `codigo[a:b]` devuelve exactamente `b - a` caracteres.

**Métodos habituales:**

```python
texto = "  aapl , 189.50  "

texto.strip()                 # quita espacios de los extremos
texto.upper()                 # a mayúsculas
texto.lower()                 # a minúsculas
texto.replace(",", ";")       # sustituye
texto.split(",")              # divide en lista: ['  aapl ', ' 189.50  ']
"-".join(["AAPL", "MSFT"])    # une una lista: 'AAPL-MSFT'
"AAPL".startswith("AA")       # True
len("AAPL")                   # 4
```

Los métodos se encadenan de izquierda a derecha:

```python
linea = "  aapl , 189.50  "
ticker = linea.split(",")[0].strip().upper()      # 'AAPL'
```

### Formato de texto con f-strings

Es la herramienta que convierte números en reportes legibles. Se antepone `f` y se escriben las expresiones entre llaves:

```python
ticker = "AAPL"
precio = 189.4567
variacion = 0.0234

print(f"{ticker}: {precio:.2f}")             # AAPL: 189.46
print(f"Variación: {variacion:.2%}")         # Variación: 2.34%
print(f"Monto: {1234567.891:,.2f}")          # Monto: 1,234,567.89
print(f"{precio:>12.2f}")                    #       189.46   (alineado a la derecha)
print(f"{ticker:<8}|")                       # AAPL    |      (a la izquierda)
print(f"{variacion:+.2%}")                   # +2.34%          (con signo)
```

| Código | Efecto | Resultado |
|---|---|---|
| `.2f` | Dos decimales | `189.46` |
| `.1%` | Porcentaje | `2.3%` |
| `,` | Separador de miles | `1,234,567` |
| `>10` | Ancho 10, a la derecha | `    189.46` |
| `,.0f` | Miles, sin decimales | `1,234,568` |
| `.2e` | Notación científica | `1.23e+04` |

### Booleanos

```python
supera_umbral = True
mercado_cerrado = False        # con mayúscula inicial
```

Suelen surgir de una comparación:

```python
precio = 189.45
es_caro = precio > 150         # True
```

Y se comportan como números al sumarlos, lo que permite contar:

```python
True + True        # 2
```

### `None`: ausencia de valor

```python
precio_cierre = None      # todavía no se conoce

if precio_cierre is None:
    print("Dato pendiente")
```

`None` **no es cero ni cadena vacía**: representa que el dato no existe. Distinguirlo importa: un retorno de 0 % significa que el precio no se movió; un retorno `None` significa que no se sabe.

Se compara con `is None`, no con `== None`.

### Conversión entre tipos

```python
float("189.50")        # 189.5
int("150")             # 150
int(189.7)             # 189       trunca, no redondea
str(189.5)             # '189.5'
bool(0)                # False

int("150.7")           # ValueError: int() no acepta texto con decimales
int(float("150.7"))    # 150       primero a decimal, luego truncar
```

Los datos leídos de un archivo llegan **siempre como texto**: convertirlos es el primer paso de cualquier análisis.

```python
float("189,50")                          # ValueError: separador latino
float("189,50".replace(",", "."))        # 189.5
```

### Errores frecuentes

```python
"150" + 50            # TypeError: no se suma texto con número
int("150") + 50       # 200

"AAPL" * 3            # 'AAPLAAPLAAPL'  ← válido, rara vez lo buscado

precio = 100
print("El precio es {precio}")     # El precio es {precio}  ← falta la f
print(f"El precio es {precio}")    # El precio es 100
```

### Ejercicios

1. Dado `"2024-03-15"`, extraiga año, mes y día, y recompóngalo como `"15/03/2024"`.
2. Convierta `"$ 1.234.567,89"` a un número decimal utilizable.
3. Dada la línea `"SQM-B;150;41250.5"`, sepárela y muestre el valor de la posición con separador de miles y dos decimales.
4. Explique la diferencia entre `0`, `None` y `""` al representar un precio faltante.

---

## Módulo 3 — Operadores

### Aritméticos

| Operador | Operación | Ejemplo | Resultado |
|---|---|---|---|
| `+` | Suma | `100 + 50` | `150` |
| `-` | Resta | `100 - 50` | `50` |
| `*` | Multiplicación | `100 * 3` | `300` |
| `/` | División | `7 / 2` | `3.5` |
| `//` | División entera | `7 // 2` | `3` |
| `%` | Resto | `7 % 2` | `1` |
| `**` | Potencia | `1.05 ** 10` | `1.6289` |

```python
capital = 1_000_000
tasa = 0.045
anios = 5

valor_futuro = capital * (1 + tasa) ** anios
print(round(valor_futuro, 2))          # 1246181.94
```

`//` y `%` sirven para repartir cantidades enteras:

```python
presupuesto = 5_000_000
precio = 2340

acciones = presupuesto // precio        # 2136 acciones completas
sobrante = presupuesto % precio         # 1.760 pesos sin invertir
```

**Tres comportamientos que conviene conocer:**

```python
6 / 3            # 2.0  ← la división siempre entrega decimal, aunque sea exacta
-7 // 2          # -4   ← redondea hacia abajo, no hacia cero
-7 % 2           # 1    ← el resto toma el signo del divisor
```

### Precedencia

Python respeta el orden matemático: primero `**`, luego `*` `/` `//` `%`, después `+` `-`.

```python
100 + 50 * 2          # 200, no 300
(100 + 50) * 2        # 300
-2 ** 2               # -4   ← la potencia se aplica antes que el signo
(-2) ** 2             # 4
```

> Use paréntesis aunque sobren. No cuestan nada y eliminan la ambigüedad para quien lea el código.

### Asignación

```python
saldo = 1000
saldo += 100       # equivale a saldo = saldo + 100
saldo -= 50
saldo *= 1.05
saldo /= 2
```

### Comparación

Devuelven siempre `True` o `False`.

```python
precio > 100       # mayor
precio < 100       # menor
precio >= 100      # mayor o igual
precio <= 100      # menor o igual
precio == 100      # igual  ← dos signos
precio != 100      # distinto
```

`=` asigna, `==` compara. Es el error de escritura más común de la primera semana.

Python permite encadenar comparaciones tal como se escriben en matemáticas:

```python
0 < variacion < 0.05          # equivale a: 0 < variacion and variacion < 0.05
```

### Lógicos

```python
and    # verdadero si ambos lo son
or     # verdadero si al menos uno lo es
not    # invierte el valor
```

```python
comprar = (precio < 100) and (volumen > 1_000_000)
alerta = (variacion > 0.05) or (variacion < -0.05)
```

### Pertenencia e identidad

```python
"AAPL" in ["AAPL", "MSFT"]        # True
"GOOGL" not in ["AAPL", "MSFT"]   # True

precio is None                     # ¿es el objeto None?
precio is not None
```

### Cómo funciona por dentro

**Cualquier valor puede evaluarse como verdadero o falso.** Se consideran falsos el cero, el texto vacío y las colecciones vacías:

```python
False, None, 0, 0.0, "", [], {}, ()
```

Todo lo demás es verdadero. Esto permite escribir:

```python
cartera = []
if not cartera:              # en vez de: if len(cartera) == 0
    print("Cartera vacía")
```

**`and` y `or` no devuelven `True`/`False`: devuelven uno de los operandos**, y evalúan solo lo necesario.

```python
0 or 100           # 100      ← el primer valor verdadero
None or "N/D"      # 'N/D'    ← patrón útil para valores por defecto
100 and 200        # 200
0 and 200          # 0        ← ni siquiera evalúa el segundo
```

Esa evaluación parcial permite proteger operaciones riesgosas:

```python
if divisor != 0 and monto / divisor > 100:      # si el divisor es 0, nunca divide
    ...
```

### Errores frecuentes

```python
# Comparar decimales con ==
if 0.1 + 0.2 == 0.3:                     # False siempre
if math.isclose(0.1 + 0.2, 0.3):         # correcto

# Encadenar mal con or
if ticker == "AAPL" or "MSFT":           # SIEMPRE verdadero
# porque "MSFT" es texto no vacío, y eso ya cuenta como verdadero
if ticker in ("AAPL", "MSFT"):           # correcto

# Comparar tipos distintos
"100" > 50                                # TypeError
```

### Ejercicios

1. Calcule cuántos lotes completos de 100 acciones caben en $5.000.000 a $2.340 la acción y cuánto efectivo queda sin invertir.
2. Escriba la condición que aprueba una orden si la cantidad es positiva, múltiplo de 100 y el monto no supera el saldo.
3. Explique por qué `-7 // 2` da `-4` y no `-3`.
4. Determine el resultado de `0 or [] or "vacío" or 100` y justifíquelo.

---

## Módulo 4 — Condicionales

Permiten que el programa tome caminos distintos según se cumpla o no una condición.

```python
variacion = 0.032

if variacion > 0.02:
    señal = "Compra fuerte"
elif variacion > 0:
    señal = "Compra"
elif variacion == 0:
    señal = "Neutral"
else:
    señal = "Venta"

print(señal)          # Compra fuerte
```

- `if` — condición inicial, obligatoria.
- `elif` — condiciones alternativas, opcionales y en cualquier cantidad.
- `else` — qué hacer si ninguna se cumplió, opcional.

### Cómo funciona por dentro

Python evalúa las condiciones **en orden** y ejecuta **solo el primer bloque verdadero**; el resto se ignora aunque también sea cierto. Por eso el orden es parte de la lógica, no un detalle de presentación.

```python
# Mal ordenado: la primera condición se lleva todos los casos
if variacion > 0:
    señal = "Compra"
elif variacion > 0.02:        # ← nunca se alcanza
    señal = "Compra fuerte"
```

Escriba siempre de la condición más restrictiva a la más general.

### Condiciones combinadas

```python
if precio < 100 and volumen > 1_000_000:
    print("Oportunidad")

if variacion > 0.05 or variacion < -0.05:
    print("Movimiento atípico")

if not mercado_abierto:
    print("Orden en cola")
```

### Condicionales anidados

```python
if mercado_abierto:
    if saldo >= monto_orden:
        print("Orden ejecutada")
    else:
        print("Saldo insuficiente")
else:
    print("Mercado cerrado")
```

Cuando la anidación pasa de dos niveles suele ser más claro descartar casos primero:

```python
if not mercado_abierto:
    print("Mercado cerrado")
elif saldo < monto_orden:
    print("Saldo insuficiente")
else:
    print("Orden ejecutada")
```

### Condicional en una línea

```python
señal = "Compra" if variacion > 0 else "Venta"
```

Útil para asignaciones simples. Con más de una condición, use el `if` completo.

### Ejemplo

```python
def clasificar_riesgo(volatilidad_anual, caida_maxima):
    """Clasifica una cartera según volatilidad y pérdida máxima."""
    if volatilidad_anual > 0.30 or caida_maxima < -0.40:
        return "Alto"
    elif volatilidad_anual > 0.15 or caida_maxima < -0.20:
        return "Medio"
    else:
        return "Bajo"

print(clasificar_riesgo(0.22, -0.18))     # Medio
```

### Errores frecuentes

```python
if precio = 100:              # SyntaxError: = asigna, == compara
if precio > 100 and < 200:    # SyntaxError: falta repetir la variable
if precio > 100 and precio < 200:      # correcto
if 100 < precio < 200:                 # mejor
```

### Ejercicios

1. Escriba una función que reciba un retorno diario y devuelva `"Normal"`, `"Atípico"` o `"Extremo"` según supere 2 o 4 desviaciones (use σ = 0,015).
2. Clasifique un bono en `"Grado de inversión"` o `"Especulativo"` a partir de su clasificación de riesgo en texto.
3. Corrija el orden de este bloque para que funcione:
   ```python
   if monto > 0:
       categoria = "Chica"
   elif monto > 1_000_000:
       categoria = "Grande"
   ```
4. Escriba la validación de una orden que devuelva el primer motivo de rechazo entre cuatro posibles.

---

## Módulo 5 — Bucles

Repiten un bloque de instrucciones.

### `for`: repetir sobre una colección

```python
precios = [100.5, 101.2, 99.8]

for p in precios:
    print(p * 1.19)
```

A diferencia de otros lenguajes, el `for` de Python **entrega directamente cada elemento**, no un contador.

```python
# Innecesariamente complicado
for i in range(len(precios)):
    print(precios[i])

# Natural
for p in precios:
    print(p)
```

Si además necesita la posición, pídala con `enumerate`:

```python
for i, p in enumerate(precios):
    print(f"Día {i}: {p}")

for dia, p in enumerate(precios, start=1):     # empezando a contar en 1
    print(f"Día {dia}: {p}")
```

### `range`: repetir una cantidad de veces

```python
range(5)            # 0, 1, 2, 3, 4       ← el 5 no se incluye
range(1, 6)         # 1, 2, 3, 4, 5
range(0, 10, 2)     # 0, 2, 4, 6, 8       ← de dos en dos
range(10, 0, -1)    # 10, 9, ..., 1       ← hacia atrás
```

```python
capital = 1_000_000
for anio in range(1, 6):
    capital *= 1.045
    print(f"Año {anio}: {capital:,.0f}")
```

`range` no construye la lista en memoria: genera los números a medida que se piden, por lo que `range(1_000_000_000)` es instantáneo.

### `zip`: recorrer dos colecciones a la vez

```python
tickers = ["AAPL", "MSFT", "JPM"]
cantidades = [150, 80, 200]
precios = [189.45, 412.30, 198.20]

for t, c, p in zip(tickers, cantidades, precios):
    print(f"{t:<6}{c:>6}{c * p:>14,.2f}")
```

`zip` se detiene al agotarse la colección más corta, en silencio. Si esa diferencia de largo indicaría un error de datos, exíjalo explícitamente:

```python
for t, c in zip(tickers, cantidades, strict=True):     # Python 3.10+
    ...     # ValueError si tienen distinto largo
```

### `while`: repetir mientras se cumpla una condición

```python
saldo = 1000.0
tasa = 0.05
anios = 0

while saldo < 2000:
    saldo *= (1 + tasa)
    anios += 1

print(f"El capital se duplica en {anios} años")      # 15
```

Use `for` cuando sepa cuántas repeticiones habrá y `while` cuando dependa de una condición. Todo `while` necesita que algo dentro del bloque acerque la condición a hacerse falsa; si no, el programa no termina nunca (`Kernel → Interrupt` en Jupyter).

### `break` y `continue`

```python
for i, r in enumerate(retornos):
    if r < -0.10:
        print(f"Caída superior al 10 % en el día {i}")
        break                # abandona el bucle por completo

for r in retornos:
    if r is None:
        continue             # salta a la siguiente vuelta
    procesar(r)
```

Un `for` puede llevar `else`, que se ejecuta **solo si el bucle terminó sin `break`**:

```python
for r in retornos:
    if r < -0.10:
        print("Alerta de riesgo")
        break
else:
    print("Ningún día superó el umbral")
```

### Bucles anidados

```python
carteras = {"Conservadora": [0.01, -0.005], "Agresiva": [0.03, -0.02]}

for nombre, retornos in carteras.items():
    acumulado = 1.0
    for r in retornos:
        acumulado *= (1 + r)
    print(f"{nombre:<15}{acumulado - 1:>8.2%}")
```

### Ejemplo: tabla de amortización

```python
monto = 10_000_000
tasa_mensual = 0.01
n_cuotas = 12

cuota = monto * tasa_mensual / (1 - (1 + tasa_mensual) ** -n_cuotas)
saldo = monto

print(f"{'N°':>3}{'Cuota':>14}{'Interés':>14}{'Amortiz.':>14}{'Saldo':>16}")
print("-" * 61)

for n in range(1, n_cuotas + 1):
    interes = saldo * tasa_mensual
    amortizacion = cuota - interes
    saldo -= amortizacion
    print(f"{n:>3}{cuota:>14,.0f}{interes:>14,.0f}{amortizacion:>14,.0f}{saldo:>16,.0f}")
```

El saldo final queda en cero, lo que confirma que la cuota está bien calculada.

### Errores frecuentes

```python
# 1. Olvidar el avance en un while
i = 0
while i < 10:
    print(i)          # falta i += 1 → bucle infinito

# 2. Acumular sobre una variable inexistente
for p in precios:
    total += p        # NameError: falta total = 0 antes del bucle

# 3. Modificar la lista mientras se recorre
for t in tickers:
    if t == "AAPL":
        tickers.remove(t)     # salta elementos
for t in tickers.copy():      # correcto: recorra una copia
    ...

# 4. Suponer que range llega al límite
for i in range(1, 12):        # llega hasta 11
```

### Ejercicios

1. Calcule el retorno acumulado de una lista de retornos diarios y muestre la evolución de $1 invertido.
2. Encuentre el primer día con caída acumulada superior al 20 % usando `break` y el `else` del bucle.
3. Determine con `while` cuántos meses toma juntar $5.000.000 ahorrando $150.000 al mes con 0,4 % de rentabilidad mensual.
4. Construya la tabla de amortización de un crédito a 24 meses y verifique que la suma de las amortizaciones iguale el capital.

---

## Módulo 6 — Estructuras de datos

Guardan varios valores bajo un mismo nombre. Python trae cuatro, y elegir bien la estructura simplifica el resto del programa.

| Estructura | Escritura | Ordenada | Modificable | Se accede por | Uso típico |
|---|---|---|---|---|---|
| **Lista** | `[ ]` | Sí | Sí | Posición | Serie de precios |
| **Tupla** | `( )` | Sí | No | Posición | Un registro fijo |
| **Diccionario** | `{clave: valor}` | Sí | Sí | Clave | Cartera por ticker |
| **Conjunto** | `{ }` | No | Sí | — | Universo de activos |

---

### Listas

```python
precios = [100.5, 101.2, 99.8, 102.3, 103.1]
tickers = ["AAPL", "MSFT", "JPM"]
vacia = []
mixta = ["AAPL", 150, 189.45]        # Python no exige un tipo único
anidada = [["AAPL", 150], ["MSFT", 80]]
```

**Acceso**, igual que en el texto: desde cero y con el límite superior excluido.

```python
precios[0]        # 100.5     primero
precios[-1]       # 103.1     último
precios[1:3]      # [101.2, 99.8]
precios[:3]       # [100.5, 101.2, 99.8]
precios[2:]       # [99.8, 102.3, 103.1]
precios[::-1]     # invertida
precios[10]       # IndexError: fuera de rango
```

**Modificación:**

```python
precios = [100.5, 101.2]

precios.append(99.8)              # agrega al final
precios.insert(0, 98.0)           # inserta en una posición
precios.extend([102.3, 103.1])    # concatena otra lista
precios.remove(99.8)              # elimina la primera ocurrencia de ese valor
ultimo = precios.pop()            # saca y devuelve el último
precios.sort()                    # ordena la lista misma
precios.reverse()                 # la invierte
```

**Consulta:**

```python
len(precios)                  # cantidad de elementos
sum(precios)                  # suma
max(precios), min(precios)    # extremos
sum(precios) / len(precios)   # promedio

99.8 in precios               # True
precios.index(99.8)           # posición
precios.count(99.8)           # ocurrencias

[1, 2] + [3, 4]               # [1, 2, 3, 4]  concatena
[0] * 5                       # [0, 0, 0, 0, 0]  repite
```

**Ordenar por un criterio:**

```python
posiciones = [("AAPL", 189.45), ("MSFT", 412.30), ("JPM", 198.20)]

sorted(posiciones, key=lambda x: x[1])                  # por precio, ascendente
sorted(posiciones, key=lambda x: x[1], reverse=True)    # descendente
```

`key` recibe una función que se aplica a cada elemento para decidir el orden; `lambda x: x[1]` significa "de cada elemento, usa su segundo componente".

> **Detalle que cuesta caro:** `precios.sort()` ordena la lista y devuelve `None`. Si escribe `precios = precios.sort()`, pierde la lista. Para obtener una lista nueva sin tocar la original, use `sorted(precios)`.

---

### Tuplas

Iguales a las listas, pero **no se pueden modificar** después de creadas.

```python
posicion = ("AAPL", 150, 189.45)
posicion[0]                  # 'AAPL'  se lee igual que una lista
posicion[0] = "MSFT"         # TypeError

una_sola = ("AAPL",)         # la coma es obligatoria
no_es_tupla = ("AAPL")       # esto es solo el texto 'AAPL'
```

Use lista cuando la colección vaya a cambiar y sus elementos sean del mismo tipo; use tupla cuando el contenido sea fijo y cada posición signifique algo distinto: `(ticker, cantidad, precio)`.

**Desempaquetado:**

```python
ticker, cantidad, precio = ("AAPL", 150, 189.45)

a, b = b, a                             # intercambio sin variable auxiliar
primero, *medio, ultimo = [1, 2, 3, 4, 5]     # medio = [2, 3, 4]
ticker, _, precio = ("AAPL", 150, 189.45)     # _ descarta ese valor
```

---

### Diccionarios

Asocian una **clave** con un **valor**. Son la estructura más usada en análisis financiero, porque los datos casi siempre vienen etiquetados.

```python
precios = {"AAPL": 189.45, "MSFT": 412.30, "JPM": 198.20}

precios["AAPL"]              # 189.45
precios["AAPL"] = 190.00     # actualiza
precios["TSLA"] = 245.60     # agrega
del precios["JPM"]           # elimina
"AAPL" in precios            # True  ← busca en las claves
len(precios)                 # cantidad de pares
```

**Acceso seguro.** Pedir una clave inexistente detiene el programa:

```python
precios["GOOGL"]                # KeyError
precios.get("GOOGL")            # None  ← no falla
precios.get("GOOGL", 0.0)       # 0.0   ← valor por defecto
```

Use `.get()` cuando la ausencia sea un caso posible, y los corchetes cuando la ausencia sea un error que quiera detectar de inmediato.

**Recorrer:**

```python
for ticker in precios:                    # recorre las claves
    print(ticker)

for precio in precios.values():           # los valores
    ...

for ticker, precio in precios.items():    # ambos: la forma más usada
    print(f"{ticker}: {precio:,.2f}")
```

**Otras operaciones:**

```python
precios.update({"JPM": 198.20})        # agrega o sobrescribe varios
precios.pop("AAPL")                    # saca y devuelve
list(precios.keys())                   # claves como lista
sum(precios.values())                  # suma de valores
max(precios, key=precios.get)          # clave con el mayor valor
```

**Diccionarios anidados** — la forma natural de guardar una cartera:

```python
cartera = {
    "AAPL": {"cantidad": 150, "precio": 189.45, "sector": "Tecnología"},
    "MSFT": {"cantidad": 80,  "precio": 412.30, "sector": "Tecnología"},
    "JPM":  {"cantidad": 200, "precio": 198.20, "sector": "Financiero"},
}

cartera["AAPL"]["cantidad"]                # 150
cartera["AAPL"]["cantidad"] += 50          # ahora 200

# Valor total
total = 0
for ticker, datos in cartera.items():
    total += datos["cantidad"] * datos["precio"]

# Agrupar por sector
por_sector = {}
for ticker, datos in cartera.items():
    sector = datos["sector"]
    valor = datos["cantidad"] * datos["precio"]
    por_sector[sector] = por_sector.get(sector, 0) + valor

for sector, valor in por_sector.items():
    print(f"{sector:<15}{valor:>15,.2f}{valor / total:>8.1%}")
```

Las claves deben ser valores no modificables —texto, números o tuplas—; una lista no puede ser clave.

---

### Conjuntos

Colección **sin orden** y **sin duplicados**. Su utilidad principal es comparar universos.

```python
sectores = {"Tecnología", "Financiero", "Tecnología"}
print(sectores)              # {'Tecnología', 'Financiero'}  ← duplicado eliminado

vacio = set()                # ojo: {} crea un diccionario vacío, no un conjunto
```

```python
cartera_enero = {"AAPL", "MSFT", "JPM"}
cartera_junio = {"MSFT", "JPM", "XOM"}

cartera_enero & cartera_junio     # {'MSFT', 'JPM'}   se mantuvieron
cartera_enero - cartera_junio     # {'AAPL'}          se vendieron
cartera_junio - cartera_enero     # {'XOM'}           se compraron
cartera_enero | cartera_junio     # todos los activos del período
```

```python
# Eliminar duplicados de una lista
tickers = ["AAPL", "MSFT", "AAPL", "JPM"]
unicos = sorted(set(tickers))        # ['AAPL', 'JPM', 'MSFT']
```

---

### Comprensiones: construir una colección en una línea

Muy usadas en análisis de datos. Equivalen a un bucle que va llenando una lista.

```python
# Con bucle
con_iva = []
for p in precios:
    con_iva.append(p * 1.19)

# Con comprensión: lo mismo
con_iva = [p * 1.19 for p in precios]
```

Se lee "para cada `p` en `precios`, entrégame `p * 1.19`", con el resultado adelantado al principio.

**Con filtro**, agregando `if` al final:

```python
retornos = [0.02, -0.01, 0.03, -0.005, 0.015]

positivos = [r for r in retornos if r > 0]              # [0.02, 0.03, 0.015]
en_texto = [f"{r:.2%}" for r in retornos if r > 0]
```

**Para transformar sin descartar**, el condicional va antes del `for`:

```python
[r if r > 0 else 0 for r in retornos]        # reemplaza negativos por cero
```

La distinción que más cuesta al principio: `if` al final **filtra**; `if ... else` al principio **transforma**.

**También funcionan con diccionarios y conjuntos:**

```python
dic = {t: p for t, p in zip(tickers, precios)}
caros = {t: p for t, p in dic.items() if p > 200}
sectores = {datos["sector"] for datos in cartera.values()}
```

**Ejemplos:**

```python
precios = [100.0, 102.5, 101.3, 104.8, 103.2]

# Retornos entre días consecutivos
retornos = [precios[i] / precios[i-1] - 1 for i in range(1, len(precios))]
# [0.025, -0.0117, 0.0346, -0.0153]

# Lo mismo, más legible
retornos = [b / a - 1 for a, b in zip(precios, precios[1:])]

# Pesos de una cartera
valores = {t: d["cantidad"] * d["precio"] for t, d in cartera.items()}
total = sum(valores.values())
pesos = {t: v / total for t, v in valores.items()}

# Factores de descuento a 10 años al 5 %
descuentos = [1 / 1.05 ** t for t in range(1, 11)]
```

> Si la comprensión no cabe cómodamente en una línea, escríbala como bucle. Es una herramienta de claridad; cuando deja de serlo, deja de convenir.

### Errores frecuentes

```python
# 1. Perder la lista al ordenar
precios = precios.sort()      # None
precios.sort()                # correcto

# 2. Repetir una lista anidada
matriz = [[0] * 3] * 2        # las dos filas son el MISMO objeto
matriz[0][0] = 1
print(matriz)                 # [[1, 0, 0], [1, 0, 0]]
matriz = [[0] * 3 for _ in range(2)]     # correcto

# 3. Buscar un valor en un diccionario
189.45 in precios             # False: 'in' revisa las claves
189.45 in precios.values()    # True

# 4. Indexar un conjunto
{"a", "b"}[0]                 # TypeError: los conjuntos no tienen posición
```

### Ejercicios

1. Construya un diccionario con cinco acciones (cantidad, precio, sector) y calcule el peso porcentual de cada una y el total por sector.
2. Dadas dos carteras como conjuntos, informe qué activos se compraron, cuáles se vendieron y cuáles se mantuvieron.
3. Reescriba con comprensión un bucle que arme la lista de tickers en mayúsculas cuyo precio supere 200.
4. Explique por qué `[[0]*3]*2` falla y `[[0]*3 for _ in range(2)]` funciona.

---

## Módulo 7 — Funciones

Una función agrupa instrucciones bajo un nombre, para ejecutarlas cuantas veces haga falta con datos distintos.

```python
def valor_futuro(capital, tasa, anios):
    """Calcula el valor futuro con interés compuesto anual."""
    return capital * (1 + tasa) ** anios


vf = valor_futuro(1_000_000, 0.045, 5)
print(round(vf, 2))          # 1246181.94
```

Sus partes:

- `def` — palabra que inicia la definición.
- `valor_futuro` — el nombre con que se llamará.
- `(capital, tasa, anios)` — los **parámetros**: los datos que recibe.
- El texto entre comillas triples — la **documentación**, opcional pero recomendada.
- `return` — el valor que **devuelve** a quien la llamó.

### Cómo funciona por dentro

`def` crea la función y le pone nombre, pero **no ejecuta el cuerpo**. Este solo corre cuando alguien la llama con paréntesis.

```python
valor_futuro                       # <function valor_futuro at 0x...>
valor_futuro(1000, 0.05, 3)        # 1157.625
```

`return` termina la función de inmediato: lo que venga después no se ejecuta.

```python
def clasificar(retorno):
    if retorno > 0:
        return "Positivo"          # sale aquí
    return "No positivo"           # solo si el if fue falso
```

Una función sin `return` devuelve `None`:

```python
def resumen(precios):
    print(f"Media: {sum(precios)/len(precios)}")

resultado = resumen([1, 2, 3])
print(resultado)          # None
```

> Distinga `print` de `return`. `print` muestra algo en pantalla; `return` entrega un valor al programa. Una función que solo imprime no sirve para seguir calculando con su resultado.

Para devolver varios valores, retorne una tupla:

```python
def estadisticas(precios):
    return min(precios), max(precios), sum(precios) / len(precios)

minimo, maximo, media = estadisticas([100, 102, 98])
```

### Parámetros

```python
def valor_futuro(capital, tasa, anios=1, capitalizaciones=1):
    """Los dos últimos parámetros tienen valor por defecto."""
    return capital * (1 + tasa / capitalizaciones) ** (capitalizaciones * anios)


valor_futuro(1_000_000, 0.045)                     # usa anios=1
valor_futuro(1_000_000, 0.045, 5)                  # por posición
valor_futuro(1_000_000, 0.045, anios=5)            # por nombre: más legible
valor_futuro(capital=1_000_000, tasa=0.045, anios=5, capitalizaciones=12)
```

Los parámetros con valor por defecto van **después** de los que no lo tienen:

```python
def f(tasa=0.05, capital):     # SyntaxError
def f(capital, tasa=0.05):     # correcto
```

Para aceptar una cantidad indeterminada de argumentos:

```python
def total(*valores):
    return sum(valores)

total(100, 200, 300)          # 600
```

### Alcance de las variables

Las variables creadas dentro de una función **existen solo ahí**:

```python
def calcular(capital):
    factor = 1.05           # variable local
    return capital * factor

calcular(1000)              # 1050.0
print(factor)               # NameError: no existe fuera de la función
```

Una función puede **leer** variables definidas fuera, pero al asignarles algo crea una variable local nueva, sin tocar la de afuera:

```python
tasa = 0.05

def cambiar():
    tasa = 0.10        # crea una variable local
    return tasa

cambiar()              # 0.10
print(tasa)            # 0.05  ← la de afuera no cambió
```

> Buena práctica: una función debe recibir todo lo que necesita como parámetro y entregar su resultado con `return`. Depender de variables externas hace que el resultado cambie según un estado invisible.

### Cuidado con los objetos modificables

Si una función recibe una lista o un diccionario y lo modifica, el cambio afecta al original:

```python
def aplicar_comision(precios):
    for i in range(len(precios)):
        precios[i] *= 1.005        # modifica la lista original
    return precios

originales = [100.0, 200.0]
aplicar_comision(originales)
print(originales)                  # [100.5, 201.0]  ← cambiaron

# Sin efectos colaterales: trabajar sobre una copia
def aplicar_comision(precios):
    return [p * 1.005 for p in precios]
```

Y nunca use una lista o diccionario como valor por defecto:

```python
def agregar(ticker, cartera=[]):     # el [] se crea UNA vez, al definir
    cartera.append(ticker)
    return cartera

agregar("AAPL")      # ['AAPL']
agregar("MSFT")      # ['AAPL', 'MSFT']  ← la misma lista de antes

# Correcto
def agregar(ticker, cartera=None):
    if cartera is None:
        cartera = []
    cartera.append(ticker)
    return cartera
```

### Documentar la función

```python
def duracion_macaulay(flujos: list[float], tiempos: list[float], tasa: float) -> float:
    """Calcula la duración de Macaulay de un bono.

    Parámetros
    ----------
    flujos : list[float]
        Monto de cada flujo, incluido el nominal al vencimiento.
    tiempos : list[float]
        Momento de cada flujo, en años.
    tasa : float
        Tasa de descuento anual en decimal (0.05 = 5 %).

    Retorna
    -------
    float
        Duración en años.
    """
    vp = [f / (1 + tasa) ** t for f, t in zip(flujos, tiempos)]
    return sum(t * v for t, v in zip(tiempos, vp)) / sum(vp)


duracion_macaulay([50, 50, 1050], [1, 2, 3], 0.05)     # 2.8594
```

Las anotaciones `: float` y `-> float` indican qué tipo se espera. **Son documentación, no verificación**: Python no las obliga, pero orientan a quien lee y al editor.

Consulte la ayuda con `help(duracion_macaulay)` o, en Jupyter, escribiendo `duracion_macaulay?`.

### Validar las entradas

```python
def retorno_simple(precio_inicial, precio_final):
    """Retorno porcentual entre dos precios."""
    if precio_inicial <= 0:
        raise ValueError(f"El precio inicial debe ser positivo: {precio_inicial}")
    return precio_final / precio_inicial - 1
```

Detener el programa con un mensaje claro es mejor que arrastrar un número absurdo por veinte líneas de cálculo.

### Errores frecuentes

```python
# 1. Olvidar el return
def total(precios):
    suma = sum(precios)        # la función devuelve None

# 2. Llamar sin paréntesis
resultado = valor_futuro       # guarda la función, no la ejecuta
resultado = valor_futuro(1000, 0.05, 3)      # correcto

# 3. Confundir print con return
def calcular(a, b):
    print(a + b)               # muestra pero no entrega
x = calcular(2, 3)             # x queda en None
```

### Ejercicios

1. Escriba `media`, `varianza` y `desviacion` sin usar librerías, con documentación completa.
2. Escriba `cuota_credito(monto, tasa_mensual, n_cuotas)` y compruebe que el saldo llegue a cero al final de la tabla de amortización.
3. Demuestre con un ejemplo propio el problema del valor por defecto modificable y corríjalo.
4. Convierta en funciones los cálculos que hizo en los módulos 3 a 5 y reúnalos en un archivo `finanzas.py`.

---

## Módulo 8 — Librerías

Una librería es un conjunto de código ya escrito que se incorpora al programa. Python trae muchas incluidas y hay miles disponibles para instalar; en finanzas se trabaja casi siempre sobre las mismas cinco o seis.

### Cómo se importan

```python
import math                      # el módulo completo
math.sqrt(16)                    # se usa con el prefijo

import numpy as np               # con alias, para escribir menos
np.sqrt(16)

from math import sqrt, log       # solo algunos nombres
sqrt(16)                         # se usa sin prefijo

from math import *               # evítelo: trae todo y provoca conflictos
```

Los alias son convencionales: se escriben siempre igual y conviene respetarlos, porque cualquier ejemplo que encuentre los usará.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

Las importaciones van **al inicio del archivo**, todas juntas.

### Instalar una librería

```bash
pip install nombre_libreria
```

Desde un notebook, anteponiendo un signo de exclamación:

```python
!pip install numpy-financial
```

### Librerías incluidas en Python

No requieren instalación.

| Librería | Para qué sirve |
|---|---|
| `math` | Raíz, logaritmo, exponencial, constantes |
| `statistics` | Media, mediana, desviación estándar |
| `datetime` | Fechas, plazos, diferencias entre días |
| `decimal` | Aritmética decimal exacta para montos |
| `random` | Números aleatorios |
| `csv`, `json` | Leer y escribir archivos de texto estructurado |

```python
import math

math.sqrt(16)          # 4.0
math.log(2.718)        # 0.999...   ← logaritmo natural
math.log10(100)        # 2.0
math.exp(1)            # 2.718...
math.floor(3.9)        # 3
math.ceil(3.1)         # 4
math.pi                # 3.14159...
```

**Fechas**, indispensables para calcular plazos:

```python
from datetime import date, timedelta

hoy = date.today()
vencimiento = date(2026, 12, 31)

dias = (vencimiento - hoy).days      # diferencia en días
anios = dias / 365                   # plazo en años

manana = hoy + timedelta(days=1)

# De texto a fecha y de vuelta
from datetime import datetime
d = datetime.strptime("2024-03-15", "%Y-%m-%d").date()
d.strftime("%d/%m/%Y")               # '15/03/2024'
```

Códigos de formato: `%Y` año de cuatro dígitos, `%m` mes, `%d` día, `%H:%M` hora y minutos.

### Librerías de análisis y finanzas

| Librería | Para qué sirve | Módulo del curso |
|---|---|---|
| **NumPy** | Cálculo numérico sobre vectores y matrices | 9 |
| **pandas** | Tablas de datos y series de tiempo | 10 |
| **matplotlib** | Gráficos | 11 |
| **seaborn** | Gráficos estadísticos sobre matplotlib | 11 |
| **numpy-financial** | VAN, TIR, cuota, valor futuro | 12 |
| **SciPy** | Optimización, estadística, resolución de ecuaciones | 12 |
| **statsmodels** | Regresión y series de tiempo | Avanzado |
| **yfinance** | Descarga precios históricos desde Yahoo Finance | 10 |
| **openpyxl** | Leer y escribir archivos Excel (lo usa pandas) | 10 |
| **mplfinance** | Gráficos de velas y volumen | 11 |

### Un ejemplo de cada una

```python
# math: matemática básica
import math
volatilidad_anual = 0.012 * math.sqrt(252)          # 0.1905

# statistics: estadística descriptiva sencilla
import statistics
retornos = [0.02, -0.01, 0.03, -0.005, 0.015]
statistics.mean(retornos)          # 0.010
statistics.stdev(retornos)         # 0.0164

# numpy-financial: fórmulas financieras estándar
import numpy_financial as npf
npf.npv(0.10, [-1000, 450, 450, 450])     # 119.08
npf.irr([-1000, 450, 450, 450])           # 0.166487
npf.pmt(0.01, 12, 10_000_000)             # -888487.89  (negativo: es un pago)

# scipy: resolver ecuaciones sin fórmula cerrada
from scipy.optimize import brentq
tir = brentq(lambda r: sum(f / (1+r)**t for t, f in
                           enumerate([-1000, 450, 450, 450])), -0.99, 10)
```

> `numpy-financial` devuelve los pagos con signo negativo, siguiendo la convención de Excel: los flujos que salen del bolsillo son negativos. Si le extraña el signo, ese es el motivo.

### Errores frecuentes

```python
# 1. Usar la librería sin importarla
sqrt(16)              # NameError
import math
math.sqrt(16)         # correcto

# 2. Olvidar el prefijo
import numpy as np
array([1, 2, 3])      # NameError
np.array([1, 2, 3])   # correcto

# 3. Nombrar un archivo propio igual que una librería
# Un archivo llamado math.py o random.py impide importar el original.

# 4. Editar un archivo propio y no ver el cambio
# En Jupyter, los módulos se cargan una sola vez. Reinicie el kernel, o use:
%load_ext autoreload
%autoreload 2
```

### Ejercicios

1. Calcule con `math` la volatilidad anualizada a partir de una volatilidad diaria de 1,2 %.
2. Calcule el plazo en años entre dos fechas con `datetime` y úselo para descontar un flujo.
3. Compare el resultado de `npf.irr` con el de la función `brentq` de SciPy sobre los mismos flujos.
4. Instale `yfinance` y descargue un año de precios de una acción.

---

## Módulo 9 — NumPy

Una lista de Python puede contener cualquier cosa y no sabe hacer aritmética elemento por elemento. NumPy aporta el **arreglo**: una colección de números del mismo tipo sobre la que las operaciones se aplican a todos los elementos a la vez.

```python
import numpy as np

# Con listas hay que recorrer
precios = [100, 102, 105]
con_iva = [p * 1.19 for p in precios]

# Con arreglos, la operación se aplica sola
precios = np.array([100, 102, 105])
con_iva = precios * 1.19          # array([119. , 121.38, 124.95])
```

La diferencia se ve con claridad aquí:

```python
[1, 2, 3] * 2                 # [1, 2, 3, 1, 2, 3]  ← repite la lista
np.array([1, 2, 3]) * 2       # array([2, 4, 6])    ← multiplica cada elemento
```

Además de la comodidad, NumPy es entre diez y cien veces más rápido que un bucle, porque opera en bloque.

### Crear arreglos

```python
np.array([100, 102, 105])              # desde una lista
np.array([[1, 2], [3, 4]])             # matriz de 2×2
np.zeros(5)                            # cinco ceros
np.ones((2, 3))                        # matriz 2×3 de unos
np.arange(0, 10, 2)                    # [0, 2, 4, 6, 8]
np.linspace(0, 1, 5)                   # [0, 0.25, 0.5, 0.75, 1]

rng = np.random.default_rng(42)        # generador con semilla fija
rng.normal(0, 0.01, 100)               # 100 valores de una normal
```

> Fijar la semilla (`default_rng(42)`) hace que los números aleatorios sean **los mismos en cada ejecución**. Es indispensable para que un resultado sea reproducible.

### Propiedades

```python
a = np.array([[1, 2, 3], [4, 5, 6]])

a.shape       # (2, 3)   filas y columnas
a.ndim        # 2        dimensiones
a.size        # 6        elementos totales
a.dtype       # dtype('int64')  tipo de los elementos
```

Todos los elementos comparten tipo, y NumPy convierte sin avisar:

```python
a = np.array([1, 2, 3])        # entero
a[0] = 1.9
print(a)                        # [1 2 3]  ← el 1.9 se truncó

a = np.array([1.0, 2, 3])      # decimal
a[0] = 1.9
print(a)                        # [1.9 2.  3. ]
```

Si va a trabajar con precios o tasas, asegure el tipo: `np.array([1, 2, 3], dtype=float)`.

### Operaciones

```python
precios = np.array([100.0, 102.5, 101.3, 104.8, 103.2])

precios + 10          # suma 10 a cada elemento
precios * 2
precios ** 2
np.log(precios)       # logaritmo de cada elemento
np.sqrt(precios)

cantidades = np.array([150, 80, 200, 50, 120])
valores = precios * cantidades          # elemento por elemento
```

**Desplazamientos**, la técnica central para trabajar con series:

```python
precios[1:]       # desde el segundo   [102.5, 101.3, 104.8, 103.2]
precios[:-1]      # hasta el penúltimo [100.0, 102.5, 101.3, 104.8]

retornos = precios[1:] / precios[:-1] - 1
# array([ 0.025, -0.01171, 0.03455, -0.01527])

log_retornos = np.diff(np.log(precios))     # retornos logarítmicos
```

### Resúmenes estadísticos

```python
retornos.mean()          # media
retornos.std(ddof=1)     # desviación estándar muestral
retornos.sum()
retornos.min(), retornos.max()
np.median(retornos)
np.percentile(retornos, 5)          # percentil 5
retornos.cumsum()                   # suma acumulada
(1 + retornos).cumprod()            # producto acumulado: valor de $1
```

> `std()` divide por *n* si no se indica nada. La estadística financiera usa la versión muestral, que divide por *n − 1*: escriba `ddof=1` siempre.

En matrices, `axis` indica la dirección del cálculo:

```python
m = np.array([[1, 2, 3], [4, 5, 6]])
m.sum()            # 21          todo
m.sum(axis=0)      # [5, 7, 9]   por columna
m.sum(axis=1)      # [6, 15]     por fila
```

Regla para recordarlo: `axis` señala el eje que **desaparece** del resultado.

### Filtrar con condiciones

```python
retornos = np.array([0.02, -0.01, 0.03, -0.005, 0.015])

retornos > 0              # array([True, False, True, False, True])
retornos[retornos > 0]    # array([0.02, 0.03, 0.015])   ← solo los positivos
(retornos > 0).sum()      # 3     ← True cuenta como 1
(retornos > 0).mean()     # 0.6   ← proporción de días positivos

# Combinar condiciones: & y |, con paréntesis obligatorios
retornos[(retornos > -0.01) & (retornos < 0.02)]

# Elegir entre dos valores según la condición
np.where(retornos > 0, "Alza", "Baja")
```

Dentro de NumPy se usan `&`, `|` y `~` en lugar de `and`, `or` y `not`, porque estas últimas exigen un único valor de verdad y aquí hay un arreglo completo:

```python
if retornos > 0:               # ValueError: the truth value of an array is ambiguous
if (retornos > 0).any():       # ¿alguno?
if (retornos > 0).all():       # ¿todos?
```

### Cómo funciona por dentro

Un trozo de arreglo (`a[1:3]`) **no es una copia**: es una ventana sobre la misma memoria. Modificarlo modifica el original. Esto difiere de las listas de Python, donde el trozo sí es una copia.

```python
a = np.array([1, 2, 3, 4])
b = a[1:3]        # ventana sobre 'a'
b[0] = 999
print(a)          # [1, 999, 3, 4]  ← el original cambió

c = a[1:3].copy() # copia independiente
```

En cambio, filtrar con una condición sí devuelve una copia:

```python
d = a[a > 2]      # copia
```

### Operar entre arreglos de distinta forma

NumPy extiende automáticamente las dimensiones compatibles:

```python
precios = np.array([[100.0, 200.0],       # 3 días
                    [102.0, 198.0],       # 2 activos
                    [101.0, 205.0]])

pesos = np.array([0.6, 0.4])              # un peso por activo

valor_cartera = (precios * pesos).sum(axis=1)     # [140.0, 140.4, 142.6]
```

El vector de pesos se aplica a cada fila. Las dimensiones se comparan de derecha a izquierda y deben ser iguales o valer 1.

### Ejemplo completo

```python
import numpy as np

rng = np.random.default_rng(11)
retornos = rng.normal(0.0004, 0.012, 252)          # un año de retornos diarios

valor = (1 + retornos).cumprod()
maximo = np.maximum.accumulate(valor)
caida = valor / maximo - 1

print(f"Retorno del período: {valor[-1] - 1:>8.2%}")     # 13.55%
print(f"Volatilidad anual:   {retornos.std(ddof=1) * np.sqrt(252):>8.2%}")   # 17.59%
print(f"Días positivos:      {(retornos > 0).mean():>8.1%}")                 # 52.8%
print(f"Máxima caída:        {caida.min():>8.2%}")                           # -10.54%
print(f"Mejor día:           {retornos.max():>8.2%}")                        # 3.12%
print(f"Peor día:            {retornos.min():>8.2%}")                        # -2.74%
```

### Ejercicios

1. Genere 500 retornos aleatorios y cuente cuántos superan dos desviaciones estándar en valor absoluto.
2. Con una matriz de 250×4 de retornos, calcule media y volatilidad de cada activo.
3. Demuestre con un ejemplo la diferencia entre `lista[1:3]` y `arreglo[1:3]`.
4. Explique por qué `if retornos > 0:` falla y cuáles son las dos formas correctas de escribirlo.

---

## Módulo 10 — pandas

pandas agrega **etiquetas** a los datos: en vez de la posición 3, la fila del 15 de marzo; en vez de la columna 2, la columna "precio". Es la librería con la que se hace el trabajo diario de análisis.

### Las dos estructuras

```python
import pandas as pd

# Series: un vector con etiquetas
precios = pd.Series([189.45, 412.30, 198.20], index=["AAPL", "MSFT", "JPM"])

# DataFrame: una tabla con filas y columnas etiquetadas
cartera = pd.DataFrame({
    "cantidad": [150, 80, 200],
    "precio":   [189.45, 412.30, 198.20],
    "sector":   ["Tec", "Tec", "Fin"],
}, index=["AAPL", "MSFT", "JPM"])
```

Un DataFrame es, en el fondo, un diccionario de Series que comparten las mismas etiquetas de fila.

### Primeros comandos ante cualquier tabla

```python
cartera.head()        # primeras cinco filas
cartera.tail(3)       # últimas tres
cartera.shape         # (filas, columnas)
cartera.info()        # tipos y datos presentes por columna
cartera.describe()    # estadística descriptiva de las columnas numéricas
cartera.columns       # nombres de columnas
cartera.dtypes        # tipo de cada columna
cartera.isna().sum()  # datos faltantes por columna
```

### Selección

| Quiero… | Se escribe | Devuelve |
|---|---|---|
| Una columna | `df["precio"]` | Series |
| Varias columnas | `df[["precio", "cantidad"]]` | DataFrame |
| Una fila por etiqueta | `df.loc["AAPL"]` | Series |
| Una fila por posición | `df.iloc[0]` | Series |
| Una celda por etiqueta | `df.loc["AAPL", "precio"]` | valor |
| Filas que cumplen algo | `df[df["precio"] > 200]` | DataFrame |

La regla que ordena todo: **los corchetes solos seleccionan columnas**; `.loc` y `.iloc` seleccionan **filas**, y tras la coma, columnas.

```python
cartera["precio"]              # columna
cartera.loc["AAPL"]            # fila por nombre
cartera.iloc[0]                # fila por número
cartera.loc["AAPL":"MSFT"]     # rango por etiqueta: INCLUYE el extremo
cartera.iloc[0:2]              # rango por posición: lo EXCLUYE
```

Esa asimetría es deliberada: con etiquetas no se sabe cuál sería "la siguiente", así que `.loc` incluye el extremo. Conviene memorizarla.

### Filtrar

```python
cartera[cartera["precio"] > 200]
cartera[(cartera["precio"] > 200) & (cartera["cantidad"] > 50)]     # & en vez de and
cartera[cartera["sector"] == "Tec"]
cartera[cartera["sector"].isin(["Tec", "Fin"])]
cartera.query("precio > 200 and sector == 'Tec'")
```

### Crear y modificar columnas

```python
cartera["valor"] = cartera["cantidad"] * cartera["precio"]
cartera["peso"] = cartera["valor"] / cartera["valor"].sum()

cartera = cartera.drop(columns=["peso"])
cartera = cartera.rename(columns={"precio": "precio_cierre"})
```

### Agrupar y resumir

```python
cartera.groupby("sector")["valor"].sum()
cartera.groupby("sector").agg({"valor": "sum", "precio": "mean"})
cartera.groupby("sector").size()

cartera.sort_values("valor", ascending=False)
cartera.nlargest(3, "valor")
```

### Cómo funciona por dentro

Las operaciones entre Series **alinean por etiqueta**, no por posición:

```python
a = pd.Series([1, 2, 3], index=["AAPL", "MSFT", "JPM"])
b = pd.Series([10, 20, 30], index=["JPM", "AAPL", "MSFT"])

a + b
# AAPL    21     ← 1 + 20, no 1 + 10
# JPM     13
# MSFT    22
```

Es una gran ventaja —nunca sumará el precio de una acción con el de otra— y desconcierta la primera vez. Si una etiqueta no está en ambas, el resultado es `NaN`.

### Datos faltantes

`NaN` marca un dato ausente.

```python
df.isna().sum()               # cuántos faltan por columna
df.dropna()                   # elimina filas con algún faltante
df.dropna(subset=["precio"])  # solo si falta en esa columna
df.fillna(0)                  # reemplaza
df["precio"].ffill()          # arrastra el último valor válido
```

Las funciones de resumen **ignoran los faltantes**, a diferencia de NumPy:

```python
s = pd.Series([1, 2, np.nan, 4])
s.mean()                      # 2.333  ← promedia sobre tres valores
np.mean([1, 2, np.nan, 4])    # nan
```

Y `NaN` no es igual a nada, ni siquiera a sí mismo, así que se detecta con `.isna()`:

```python
np.nan == np.nan     # False
s.isna()             # forma correcta
```

### Leer y escribir archivos

```python
df = pd.read_csv("precios.csv")

# Archivos exportados por Excel en configuración regional latinoamericana
df = pd.read_csv("precios.csv", sep=";", decimal=",",
                 parse_dates=["fecha"], index_col="fecha", encoding="utf-8")

df = pd.read_excel("cartera.xlsx", sheet_name="Posiciones")

df.to_csv("salida.csv", index=False)
df.to_excel("salida.xlsx", index=False)
```

Descargar precios de mercado:

```python
import yfinance as yf

datos = yf.download(["AAPL", "MSFT"], start="2023-01-01", end="2024-12-31")
precios = datos["Close"]
```

### Series de tiempo

Con un índice de fechas, pandas permite seleccionar por período y calcular sobre ventanas móviles:

```python
precios = pd.read_csv("precios.csv", parse_dates=["fecha"], index_col="fecha")

precios.loc["2024"]                  # todo el año
precios.loc["2024-03"]               # un mes
precios.loc["2024-01":"2024-06"]     # un rango

precios["retorno"] = precios["cierre"].pct_change()        # variación respecto al día anterior
precios["media_20"] = precios["cierre"].rolling(20).mean() # media móvil de 20 días
precios["vol_20"] = precios["retorno"].rolling(20).std() * np.sqrt(252)

mensual = precios["cierre"].resample("ME").last()          # último precio de cada mes
```

- `.pct_change()` calcula la variación porcentual respecto de la fila anterior; la primera queda `NaN`.
- `.shift(1)` desplaza la serie un período: así se accede al dato anterior sin usar información futura.
- `.rolling(n)` define una ventana móvil de n períodos.

### Encadenar operaciones

Cada método devuelve una tabla nueva, lo que permite escribir el análisis como una secuencia legible:

```python
resumen = (
    cartera
    .assign(valor=lambda d: d["cantidad"] * d["precio"])
    .query("valor > 10000")
    .groupby("sector")
    .agg(total=("valor", "sum"), n=("valor", "size"))
    .sort_values("total", ascending=False)
)
```

### Errores frecuentes

```python
# 1. Usar and en vez de &
df[(df["a"] > 1) and (df["b"] > 2)]      # ValueError
df[(df["a"] > 1) & (df["b"] > 2)]        # correcto

# 2. Modificar el resultado de un filtro
subset = df[df["precio"] > 100]
subset["nueva"] = 1                       # SettingWithCopyWarning
subset = df[df["precio"] > 100].copy()    # correcto
df.loc[df["precio"] > 100, "nueva"] = 1   # o modificar el original directamente

# 3. Nombres de columna con espacios ocultos
df.columns = df.columns.str.strip()       # revise siempre df.columns
```

### Ejemplo completo

```python
import pandas as pd
import numpy as np

fechas = pd.date_range("2024-01-01", periods=252, freq="B")     # días hábiles
rng = np.random.default_rng(11)
df = pd.DataFrame(
    {"cierre": 100 * (1 + rng.normal(0.0004, 0.012, 252)).cumprod()},
    index=fechas,
)

df["retorno"] = df["cierre"].pct_change()
df["media_50"] = df["cierre"].rolling(50).mean()
df["señal"] = np.where(df["cierre"] > df["media_50"], "Sobre media", "Bajo media")

print(f"Retorno del período: {df['cierre'].iloc[-1] / df['cierre'].iloc[0] - 1:.2%}")
print(f"Volatilidad anual:   {df['retorno'].std() * np.sqrt(252):.2%}")
print(df.groupby("señal")["retorno"].agg(["count", "mean"]))
```

### Ejercicios

1. Lea un archivo CSV con separador `;` y decimal `,`, y verifique que las columnas queden con el tipo correcto.
2. Calcule retorno diario, media móvil de 50 días y volatilidad móvil de 20 días para una acción.
3. Agrupe una tabla de posiciones por sector e informe valor total, cantidad de activos y peso porcentual.
4. Sume dos Series con etiquetas parcialmente distintas y explique el resultado.

---

## Módulo 11 — Gráficos con matplotlib

matplotlib genera los gráficos; seaborn agrega estilos y gráficos estadísticos. En un notebook las figuras aparecen bajo la celda.

### Estructura de una figura

```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(10, 5))     # fig: la lámina; ax: los ejes
ax.plot(fechas, precios)
ax.set_title("Evolución del precio")
ax.set_xlabel("Fecha")
ax.set_ylabel("Precio (USD)")
plt.show()
```

Dos formas de trabajar conviven en los ejemplos que encontrará:

```python
plt.plot(x, y)          # rápida, dibuja sobre la figura "actual"
ax.plot(x, y)           # explícita, sobre unos ejes concretos
```

La segunda es preferible: al tener varios gráficos en una misma lámina, deja claro cuál se está modificando.

### Preparación de los datos de ejemplo

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

rng = np.random.default_rng(11)
fechas = pd.date_range("2024-01-01", periods=252, freq="B")

precios = pd.DataFrame({
    "ACCION_A": 100 * (1 + rng.normal(0.0006, 0.012, 252)).cumprod(),
    "ACCION_B": 100 * (1 + rng.normal(0.0003, 0.018, 252)).cumprod(),
    "ACCION_C": 100 * (1 + rng.normal(0.0004, 0.009, 252)).cumprod(),
}, index=fechas)

retornos = precios.pct_change().dropna()
```

---

### 1. Línea — evolución en el tiempo

El gráfico financiero por excelencia: precios, índices, patrimonio acumulado.

```python
fig, ax = plt.subplots(figsize=(11, 5))

for columna in precios.columns:
    ax.plot(precios.index, precios[columna], label=columna, linewidth=1.5)

ax.set_title("Evolución de precios", fontsize=13, fontweight="bold")
ax.set_ylabel("Precio (base 100)")
ax.legend()
ax.grid(alpha=0.3)
plt.tight_layout()
plt.show()
```

Para comparar activos de precios muy distintos, llévelos a base 100:

```python
base_100 = precios / precios.iloc[0] * 100
```

Elementos útiles sobre una serie:

```python
ax.axhline(100, color="gray", linestyle="--", linewidth=1)     # línea horizontal
ax.axvline(pd.Timestamp("2024-06-01"), color="red", alpha=0.5) # línea vertical
ax.fill_between(precios.index, precios["ACCION_A"], 100, alpha=0.2)
```

---

### 2. Barras — comparar categorías

```python
retorno_total = (precios.iloc[-1] / precios.iloc[0] - 1)

fig, ax = plt.subplots(figsize=(8, 5))
colores = ["seagreen" if r > 0 else "indianred" for r in retorno_total]
barras = ax.bar(retorno_total.index, retorno_total.values, color=colores)

ax.set_title("Retorno acumulado del período")
ax.set_ylabel("Retorno")
ax.axhline(0, color="black", linewidth=0.8)
ax.yaxis.set_major_formatter(lambda x, p: f"{x:.0%}")

for barra, valor in zip(barras, retorno_total.values):
    ax.text(barra.get_x() + barra.get_width() / 2, valor,
            f"{valor:.1%}", ha="center",
            va="bottom" if valor > 0 else "top")

plt.tight_layout()
plt.show()
```

Use `ax.barh()` para barras horizontales, más legibles cuando hay muchas categorías con nombres largos.

---

### 3. Histograma — distribución de retornos

Muestra con qué frecuencia ocurre cada rango de valores. Es la forma de ver que los retornos financieros no se distribuyen normalmente.

```python
fig, ax = plt.subplots(figsize=(9, 5))

ax.hist(retornos["ACCION_A"], bins=40, color="steelblue",
        edgecolor="white", alpha=0.85)

ax.axvline(retornos["ACCION_A"].mean(), color="black",
           linestyle="--", label="Media")
ax.axvline(retornos["ACCION_A"].quantile(0.05), color="red",
           linestyle="--", label="Percentil 5 %")

ax.set_title("Distribución de retornos diarios")
ax.set_xlabel("Retorno diario")
ax.set_ylabel("Frecuencia")
ax.legend()
plt.tight_layout()
plt.show()
```

El número de intervalos (`bins`) cambia mucho la lectura: pocos ocultan la forma, demasiados la vuelven ruido. Entre 30 y 50 suele funcionar para un año de datos diarios.

---

### 4. Dispersión — relación entre dos variables

Para ver si dos activos se mueven juntos, y estimar la beta.

```python
x = retornos["ACCION_B"]
y = retornos["ACCION_A"]

fig, ax = plt.subplots(figsize=(7, 7))
ax.scatter(x, y, alpha=0.5, s=18, color="steelblue")

# Recta de regresión
beta, alfa = np.polyfit(x, y, 1)
linea_x = np.array([x.min(), x.max()])
ax.plot(linea_x, alfa + beta * linea_x, color="red", linewidth=2,
        label=f"Beta = {beta:.2f}")

ax.set_title("Relación entre retornos diarios")
ax.set_xlabel("Retorno ACCION_B")
ax.set_ylabel("Retorno ACCION_A")
ax.axhline(0, color="gray", linewidth=0.5)
ax.axvline(0, color="gray", linewidth=0.5)
ax.legend()
plt.tight_layout()
plt.show()
```

`np.polyfit(x, y, 1)` ajusta una recta y devuelve la pendiente y la intersección: la pendiente es la beta del activo respecto del otro.

---

### 5. Torta — composición de una cartera

```python
valores = {"Renta variable": 450_000, "Renta fija": 300_000,
           "Efectivo": 150_000, "Alternativos": 100_000}

fig, ax = plt.subplots(figsize=(7, 7))
ax.pie(valores.values(), labels=valores.keys(), autopct="%1.1f%%",
       startangle=90, counterclock=False,
       wedgeprops={"edgecolor": "white", "linewidth": 2})
ax.set_title("Composición de la cartera")
plt.tight_layout()
plt.show()
```

Sirve para pocas categorías —hasta cinco o seis—. Con más, el ojo no compara bien los ángulos y conviene un gráfico de barras horizontales.

---

### 6. Caja — dispersión y valores atípicos

Resume una distribución en cinco números: mínimo, primer cuartil, mediana, tercer cuartil y máximo, marcando aparte los valores extremos.

```python
fig, ax = plt.subplots(figsize=(8, 5))
ax.boxplot([retornos[c] for c in retornos.columns],
           tick_labels=retornos.columns)
ax.set_title("Dispersión de retornos diarios por activo")
ax.set_ylabel("Retorno diario")
ax.axhline(0, color="gray", linewidth=0.8)
ax.grid(axis="y", alpha=0.3)
plt.tight_layout()
plt.show()
```

Es el gráfico más eficiente para comparar el riesgo de varios activos de un vistazo: la altura de la caja es la dispersión y los puntos sueltos son los días excepcionales.

> En versiones de matplotlib anteriores a la 3.9 el parámetro se llama `labels` en vez de `tick_labels`. Si obtiene un error ahí, ese es el motivo.

---

### 7. Mapa de calor — matriz de correlaciones

Con seaborn, que agrega gráficos estadísticos sobre matplotlib.

```python
import seaborn as sns

correlaciones = retornos.corr()

fig, ax = plt.subplots(figsize=(7, 6))
sns.heatmap(correlaciones, annot=True, fmt=".2f", cmap="RdBu_r",
            vmin=-1, vmax=1, center=0, square=True,
            linewidths=0.5, cbar_kws={"label": "Correlación"}, ax=ax)
ax.set_title("Correlación entre retornos diarios")
plt.tight_layout()
plt.show()
```

`vmin=-1, vmax=1, center=0` fija la escala de color: sin eso, una correlación de 0,3 puede verse tan intensa como una de 0,9 y engañar al lector.

---

### Varios gráficos en una lámina

```python
fig, axes = plt.subplots(2, 2, figsize=(13, 9))

axes[0, 0].plot(precios.index, precios["ACCION_A"], color="steelblue")
axes[0, 0].set_title("Precio")

axes[0, 1].hist(retornos["ACCION_A"], bins=40, color="steelblue",
                edgecolor="white")
axes[0, 1].set_title("Distribución de retornos")

valor = (1 + retornos["ACCION_A"]).cumprod()
caida = valor / valor.cummax() - 1
axes[1, 0].fill_between(caida.index, caida, 0, color="indianred", alpha=0.5)
axes[1, 0].set_title("Caída desde el máximo")

axes[1, 1].plot(retornos["ACCION_A"].rolling(20).std() * np.sqrt(252),
                color="darkorange")
axes[1, 1].set_title("Volatilidad móvil (20 días)")

fig.suptitle("Panel de análisis — ACCION_A", fontsize=15, fontweight="bold")
plt.tight_layout()
plt.show()
```

`axes` es una matriz: `axes[fila, columna]` selecciona cada gráfico.

### Gráficos directos desde pandas

Para explorar rápido, pandas dibuja sin escribir matplotlib:

```python
precios.plot(figsize=(11, 5), title="Precios")
retornos["ACCION_A"].hist(bins=40)
precios["ACCION_A"].plot.area(alpha=0.4)
retornos.plot.box()
```

Sirve para mirar; para un informe conviene la versión explícita, que permite controlar cada elemento.

### Guardar la figura

```python
fig.savefig("grafico.png", dpi=300, bbox_inches="tight")
fig.savefig("grafico.pdf", bbox_inches="tight")     # vectorial, para imprimir
```

`bbox_inches="tight"` recorta el margen sobrante, que de otro modo deja los títulos cortados.

### Gráfico de velas

Requiere `mplfinance`, especializada en gráficos bursátiles:

```python
# pip install mplfinance
import mplfinance as mpf

# ohlc debe tener columnas Open, High, Low, Close y opcionalmente Volume
mpf.plot(ohlc, type="candle", volume=True, style="yahoo",
         mav=(20, 50), title="Precio diario")
```

### Recomendaciones de presentación

| Regla | Motivo |
|---|---|
| Siempre título y etiquetas en los ejes | Un gráfico sin ejes rotulados no informa nada |
| Indique las unidades (%, USD, miles) | Evita interpretaciones erróneas del orden de magnitud |
| Use `.grid(alpha=0.3)` | Ayuda a leer valores sin competir con los datos |
| No empiece el eje en cero al graficar precios | Exagera visualmente las variaciones |
| Sí empiece en cero al graficar barras | No hacerlo distorsiona la comparación |
| Verde/rojo solo para positivo/negativo | Es la convención financiera |
| `tight_layout()` antes de mostrar | Impide que los rótulos se superpongan |

### Errores frecuentes

```python
# 1. Olvidar plt.show() en un archivo .py
# En Jupyter la figura aparece igual; en un script, no.

# 2. Dibujar sobre la figura anterior
plt.plot(x1, y1)
plt.plot(x2, y2)          # se superponen en la misma figura
fig, ax = plt.subplots()  # cree una figura nueva para cada gráfico

# 3. Fechas ilegibles amontonadas en el eje
fig.autofmt_xdate()       # las inclina automáticamente
```

### Ejercicios

1. Grafique tres activos en base 100 con leyenda, título, grilla y eje con formato de porcentaje.
2. Construya un histograma de retornos con líneas verticales en la media y en los percentiles 1 % y 5 %.
3. Haga un gráfico de dispersión entre un activo y un índice, agregue la recta de regresión y muestre la beta en la leyenda.
4. Arme una lámina de cuatro paneles con precio, distribución, caída desde el máximo y volatilidad móvil, y guárdela en PNG a 300 dpi.

---

## Módulo 12 — Cálculos financieros fundamentales

Reúne los cálculos que se resuelven una y otra vez en la práctica, escritos con las herramientas de los módulos anteriores.

### Valor del dinero en el tiempo

```python
import math

def valor_futuro_simple(capital, tasa, periodos):
    """Interés simple: los intereses no generan intereses."""
    return capital * (1 + tasa * periodos)


def valor_futuro_compuesto(capital, tasa, periodos):
    """Interés compuesto."""
    return capital * (1 + tasa) ** periodos


def valor_futuro_capitalizado(capital, tasa_anual, anios, m):
    """Capitalización m veces al año."""
    return capital * (1 + tasa_anual / m) ** (m * anios)


def valor_futuro_continuo(capital, tasa_anual, anios):
    """Capitalización continua."""
    return capital * math.exp(tasa_anual * anios)


capital, tasa, anios = 1_000_000, 0.045, 5

print(f"Simple:      {valor_futuro_simple(capital, tasa, anios):>14,.2f}")     # 1,225,000.00
print(f"Compuesto:   {valor_futuro_compuesto(capital, tasa, anios):>14,.2f}")  # 1,246,181.94
print(f"Mensual:     {valor_futuro_capitalizado(capital, tasa, anios, 12):>14,.2f}")  # 1,251,795.82
print(f"Continua:    {valor_futuro_continuo(capital, tasa, anios):>14,.2f}")   # 1,252,322.72
```

**Valor presente** y **tasa efectiva**:

```python
def valor_presente(monto_futuro, tasa, periodos):
    return monto_futuro / (1 + tasa) ** periodos


def tasa_efectiva_anual(tasa_nominal, m):
    """Convierte una tasa nominal capitalizable m veces en tasa efectiva anual."""
    return (1 + tasa_nominal / m) ** m - 1


tasa_efectiva_anual(0.045, 12)      # 0.04594  → 4,594 % efectivo
```

Comparar dos créditos con distinta frecuencia de capitalización exige llevarlos a tasa efectiva anual; comparar las nominales induce a error.

### Valor actual neto y tasa interna de retorno

```python
def van(flujos, tasa):
    """Valor actual neto. flujos[0] es el desembolso inicial, en negativo."""
    return sum(f / (1 + tasa) ** t for t, f in enumerate(flujos))


flujos = [-1000, 450, 450, 450]
van(flujos, 0.10)          # 119.08  → el proyecto crea valor
van(flujos, 0.20)          # -52.08  → a esa tasa, destruye valor
```

La TIR es la tasa que anula el VAN. No tiene fórmula cerrada, así que se busca numéricamente:

```python
from scipy.optimize import brentq

def tir(flujos):
    """Tasa interna de retorno."""
    return brentq(lambda r: van(flujos, r), -0.99, 10)

tir([-1000, 450, 450, 450])        # 0.166487  → 16,65 %
```

O directamente con la librería especializada:

```python
import numpy_financial as npf

npf.npv(0.10, [-1000, 450, 450, 450])     # 119.08
npf.irr([-1000, 450, 450, 450])           # 0.166487
```

> La TIR puede no ser única si los flujos cambian de signo más de una vez. Ante flujos irregulares, decida con el VAN.

### Anualidades y créditos

```python
def cuota_credito(monto, tasa_periodo, n_cuotas):
    """Cuota fija de un crédito con amortización francesa."""
    return monto * tasa_periodo / (1 - (1 + tasa_periodo) ** -n_cuotas)


def valor_presente_anualidad(cuota, tasa, n):
    return cuota * (1 - (1 + tasa) ** -n) / tasa


def valor_presente_perpetuidad(flujo, tasa, crecimiento=0.0):
    """Perpetuidad, con crecimiento constante opcional."""
    if tasa <= crecimiento:
        raise ValueError("La tasa debe superar al crecimiento")
    return flujo / (tasa - crecimiento)


cuota = cuota_credito(10_000_000, 0.01, 12)
print(f"Cuota: {cuota:,.2f}")                          # 888,487.89
print(f"Total pagado: {cuota * 12:,.2f}")              # 10,661,854.64
print(f"Intereses: {cuota * 12 - 10_000_000:,.2f}")    # 661,854.64

valor_presente_perpetuidad(100, 0.08)             # 1250.0
valor_presente_perpetuidad(100, 0.08, 0.03)       # 2000.0
```

**Tabla de amortización** completa:

```python
def tabla_amortizacion(monto, tasa, n):
    """Devuelve una lista de diccionarios con el detalle de cada cuota."""
    cuota = cuota_credito(monto, tasa, n)
    saldo = monto
    filas = []
    for periodo in range(1, n + 1):
        interes = saldo * tasa
        amortizacion = cuota - interes
        saldo -= amortizacion
        filas.append({
            "periodo": periodo,
            "cuota": cuota,
            "interes": interes,
            "amortizacion": amortizacion,
            "saldo": max(saldo, 0),
        })
    return filas


import pandas as pd
tabla = pd.DataFrame(tabla_amortizacion(10_000_000, 0.01, 12))
print(tabla.round(0).to_string(index=False))
```

### Retornos

```python
import numpy as np

def retorno_simple(precios):
    """Variación porcentual entre períodos consecutivos."""
    precios = np.asarray(precios, dtype=float)
    return precios[1:] / precios[:-1] - 1


def retorno_logaritmico(precios):
    return np.diff(np.log(np.asarray(precios, dtype=float)))


def retorno_acumulado(retornos):
    return (1 + np.asarray(retornos)).prod() - 1


def retorno_anualizado(retornos, periodos_por_anio=252):
    """Retorno compuesto anual equivalente."""
    retornos = np.asarray(retornos)
    acumulado = (1 + retornos).prod()
    anios = len(retornos) / periodos_por_anio
    return acumulado ** (1 / anios) - 1
```

Diferencia entre los dos tipos de retorno, que conviene tener clara:

| | Retorno simple | Retorno logarítmico |
|---|---|---|
| Fórmula | $P_t/P_{t-1} - 1$ | $\ln(P_t/P_{t-1})$ |
| Se suman en el tiempo | No | **Sí** |
| Se suman entre activos | **Sí** | No |
| Uso habitual | Componer carteras, informar rentabilidad | Modelar y simular series |

```python
precios = [100.0, 102.5, 101.3, 104.8, 103.2]
retorno_simple(precios)          # [0.025, -0.0117, 0.0346, -0.0153]
retorno_acumulado(retorno_simple(precios))     # 0.032  = 103.2/100 - 1
```

### Riesgo

```python
def volatilidad(retornos, periodos_por_anio=252):
    """Desviación estándar anualizada."""
    return np.std(retornos, ddof=1) * np.sqrt(periodos_por_anio)


def sharpe(retornos, tasa_libre=0.0, periodos_por_anio=252):
    """Retorno en exceso por unidad de riesgo."""
    exceso = np.asarray(retornos) - tasa_libre / periodos_por_anio
    return exceso.mean() / np.std(retornos, ddof=1) * np.sqrt(periodos_por_anio)


def maxima_caida(retornos):
    """Peor pérdida desde un máximo previo."""
    valor = (1 + np.asarray(retornos)).cumprod()
    return float((valor / np.maximum.accumulate(valor) - 1).min())


def valor_en_riesgo(retornos, confianza=0.95):
    """Pérdida que no se supera con la confianza indicada (método histórico)."""
    return -np.percentile(retornos, (1 - confianza) * 100)
```

La anualización multiplica por la raíz del número de períodos, no por el número de períodos: la volatilidad crece con la raíz del tiempo.

```python
volatilidad_diaria = 0.012
volatilidad_anual = 0.012 * np.sqrt(252)      # 0.1905  → 19,05 %
```

### Relación entre activos y cartera

```python
def correlacion(retornos_a, retornos_b):
    return float(np.corrcoef(retornos_a, retornos_b)[0, 1])


def beta(retornos_activo, retornos_mercado):
    """Sensibilidad del activo a los movimientos del mercado."""
    cov = np.cov(retornos_activo, retornos_mercado, ddof=1)[0, 1]
    return float(cov / np.var(retornos_mercado, ddof=1))


def capm(tasa_libre, beta_activo, retorno_mercado):
    """Retorno exigido según el modelo de valoración de activos de capital."""
    return tasa_libre + beta_activo * (retorno_mercado - tasa_libre)


def riesgo_cartera_dos_activos(w1, vol1, vol2, correlacion):
    """Volatilidad de una cartera de dos activos."""
    w2 = 1 - w1
    varianza = (w1 * vol1) ** 2 + (w2 * vol2) ** 2 + 2 * w1 * w2 * vol1 * vol2 * correlacion
    return math.sqrt(varianza)
```

El efecto de la diversificación se aprecia de inmediato:

```python
# Dos activos con 20 % de volatilidad cada uno, 50 % y 50 %
riesgo_cartera_dos_activos(0.5, 0.20, 0.20, 1.0)     # 0.20   sin diversificación
riesgo_cartera_dos_activos(0.5, 0.20, 0.20, 0.0)     # 0.1414
riesgo_cartera_dos_activos(0.5, 0.20, 0.20, -1.0)    # 0.0    riesgo eliminado
```

Con más activos conviene la forma matricial:

```python
def riesgo_cartera(pesos, matriz_covarianzas):
    pesos = np.asarray(pesos)
    return float(np.sqrt(pesos @ matriz_covarianzas @ pesos))


retornos = df_retornos.values                # matriz de días × activos
covarianzas = np.cov(retornos, rowvar=False) * 252
pesos = np.array([0.4, 0.35, 0.25])

riesgo_cartera(pesos, covarianzas)
```

### Valoración de acciones

```python
def gordon(dividendo_proximo, tasa_exigida, crecimiento):
    """Valor de una acción con dividendos que crecen a tasa constante."""
    if tasa_exigida <= crecimiento:
        raise ValueError("La tasa exigida debe superar al crecimiento")
    return dividendo_proximo / (tasa_exigida - crecimiento)


gordon(2.0, 0.09, 0.04)          # 40.0
```

### Valoración de bonos

```python
def precio_bono(nominal, tasa_cupon, tasa_mercado, anios, frecuencia=2):
    """Valor presente de los cupones y del nominal."""
    cupon = nominal * tasa_cupon / frecuencia
    n = int(anios * frecuencia)
    precio = 0.0
    for periodo in range(1, n + 1):
        flujo = cupon + (nominal if periodo == n else 0)
        precio += flujo / (1 + tasa_mercado / frecuencia) ** periodo
    return precio


precio_bono(1000, 0.05, 0.04, 5)     # 1044.91  ← sobre la par
precio_bono(1000, 0.05, 0.05, 5)     # 1000.00  ← a la par
precio_bono(1000, 0.05, 0.06, 5)     #  957.35  ← bajo la par
```

La relación inversa entre tasa y precio queda a la vista: cuando la tasa de mercado supera al cupón, el bono vale menos que su nominal.

**Duración**, que mide la sensibilidad del precio ante cambios en la tasa:

```python
def duracion(nominal, tasa_cupon, tasa_mercado, anios, frecuencia=2):
    """Duración de Macaulay y modificada, en años."""
    cupon = nominal * tasa_cupon / frecuencia
    n = int(anios * frecuencia)

    valores_presentes = []
    tiempos = []
    for periodo in range(1, n + 1):
        flujo = cupon + (nominal if periodo == n else 0)
        vp = flujo / (1 + tasa_mercado / frecuencia) ** periodo
        valores_presentes.append(vp)
        tiempos.append(periodo / frecuencia)

    precio = sum(valores_presentes)
    macaulay = sum(t * vp for t, vp in zip(tiempos, valores_presentes)) / precio
    modificada = macaulay / (1 + tasa_mercado / frecuencia)

    return {"precio": precio, "macaulay": macaulay, "modificada": modificada}


resultado = duracion(1000, 0.05, 0.05, 5)
print(f"Precio:     {resultado['precio']:,.2f}")         # 1,000.00
print(f"Macaulay:   {resultado['macaulay']:.4f} años")   # 4.4854
print(f"Modificada: {resultado['modificada']:.4f}")      # 4.3760
```

La duración modificada estima el cambio porcentual del precio ante una variación de la tasa:

```python
cambio_tasa = 0.01                      # sube 100 puntos base
cambio_precio = -resultado["modificada"] * cambio_tasa
print(f"Caída estimada del precio: {cambio_precio:.2%}")     # -4.38%
```

Es una aproximación lineal: sirve para movimientos pequeños y subestima el precio en movimientos grandes, porque la relación real es curva.

### Resumen de una serie de retornos

Función que reúne todo lo anterior en una sola salida:

```python
def resumen_desempeno(retornos, tasa_libre=0.0, periodos_por_anio=252):
    """Métricas habituales de rentabilidad y riesgo."""
    retornos = np.asarray(retornos, dtype=float)
    return {
        "Retorno acumulado": retorno_acumulado(retornos),
        "Retorno anualizado": retorno_anualizado(retornos, periodos_por_anio),
        "Volatilidad anual": volatilidad(retornos, periodos_por_anio),
        "Sharpe": sharpe(retornos, tasa_libre, periodos_por_anio),
        "Máxima caída": maxima_caida(retornos),
        "VaR 95 % diario": valor_en_riesgo(retornos, 0.95),
        "Días positivos": float((retornos > 0).mean()),
    }


rng = np.random.default_rng(11)
r = rng.normal(0.0004, 0.012, 252)

for nombre, valor in resumen_desempeno(r).items():
    print(f"{nombre:<22}{valor:>10.2%}" if abs(valor) < 10
          else f"{nombre:<22}{valor:>10.2f}")
```

### Ejercicios

1. Compare el valor futuro de $1.000.000 al 6 % anual durante 10 años con capitalización anual, mensual, diaria y continua. Grafique la diferencia.
2. Evalúe un proyecto con inversión de $50.000.000 y flujos irregulares durante seis años: calcule VAN a tres tasas de descuento y la TIR.
3. Construya la tabla de amortización de un crédito hipotecario a 20 años y grafique cómo se reparte cada cuota entre interés y amortización.
4. Calcule volatilidad, Sharpe, máxima caída y VaR de dos activos y decida cuál prefiere, justificando con las cifras.
5. Calcule el precio y la duración de un bono a 10 años y verifique la estimación de la duración contra el recálculo exacto del precio con la tasa 100 puntos base más alta.

---

## Módulo 13 — Proyecto final

### Enunciado

Construya un **analizador de carteras** que integre lo visto en el curso, entregado como repositorio con código y un informe breve.

### Requisitos

**Parte 1 — Archivo de funciones (`finanzas.py`)**

- [ ] `cargar_precios(ruta)` — lee un archivo CSV o Excel y devuelve una tabla con índice de fechas.
- [ ] `calcular_retornos(precios)` — agrega la columna de retorno diario.
- [ ] `resumen_desempeno(retornos)` — retorno acumulado y anualizado, volatilidad, Sharpe, máxima caída.
- [ ] `valorizar(cartera, precios)` — valor total y peso de cada posición.
- [ ] Todas con documentación, y con validación de las entradas mediante `raise`.

**Parte 2 — Análisis (`analisis.ipynb`)**

- [ ] Cargue precios de al menos cinco activos (descargados con `yfinance` o desde un CSV).
- [ ] Calcule retornos y el resumen de desempeño de cada uno.
- [ ] Construya la matriz de correlaciones.
- [ ] Compare una cartera equiponderada contra los activos individuales.
- [ ] Presente los resultados en tablas formateadas con f-strings.

**Parte 3 — Gráficos**

Al menos cuatro, cada uno con título, ejes rotulados y leyenda cuando corresponda:

- [ ] Evolución de precios en base 100.
- [ ] Distribución de retornos de un activo.
- [ ] Mapa de calor de correlaciones.
- [ ] Uno a elección: barras de retorno, caja comparativa, dispersión con recta de regresión o caída desde el máximo.

**Parte 4 — Cálculo financiero aplicado**

- [ ] Un análisis a elección: evaluación de un proyecto con VAN y TIR, tabla de amortización de un crédito, o precio y duración de un bono.

**Parte 5 — Documentación (`README.md`)**

- [ ] Qué hace el proyecto, qué archivos lo componen y cómo ejecutarlo.

### Evaluación

| Dimensión | % | Criterio |
|---|---|---|
| Funcionamiento | 30 | El código corre completo sin errores y los números son correctos. |
| Uso del lenguaje | 25 | Estructuras adecuadas al problema, funciones bien definidas, sin repetición innecesaria. |
| Gráficos | 20 | Legibles, rotulados y pertinentes a lo que se quiere mostrar. |
| Claridad | 15 | Nombres descriptivos, código ordenado, documentación de las funciones. |
| Interpretación | 10 | Las conclusiones se desprenden de los resultados obtenidos. |

> Se evalúa el código y su claridad, no la sofisticación del modelo. Un análisis simple, correcto y bien presentado vale más que uno ambicioso y desordenado.

---

## Anexo A — Tabla de símbolos

| Símbolo | Nombre | Qué hace |
|---|---|---|
| `=` | Igual | Asigna un valor a un nombre |
| `==` | Doble igual | Compara si dos valores son iguales |
| `!=` | Distinto | Compara si son diferentes |
| `is` | Es | Verifica si son el mismo objeto |
| `:` | Dos puntos | Abre un bloque indentado |
| `#` | Numeral | Inicia un comentario |
| `()` | Paréntesis | Llama funciones, agrupa operaciones, crea tuplas |
| `[]` | Corchetes | Crea listas, accede por posición |
| `{}` | Llaves | Crea diccionarios y conjuntos |
| `.` | Punto | Accede a un método o atributo |
| `**` | Doble asterisco | Potencia |
| `//` | Doble barra | División entera |
| `%` | Porcentaje | Resto de la división |
| `_` | Guión bajo | Descarta un valor; separa miles en números |
| `f"..."` | f-string | Texto con valores insertados |
| `r"..."` | Texto crudo | Texto sin interpretar las barras invertidas |
| `->` | Flecha | Indica qué tipo devuelve una función |
| `@` | Arroba | Decorador |
| `&` `\|` `~` | Y, o, no | Operadores lógicos en NumPy y pandas |

---

## Anexo B — Errores frecuentes y cómo leerlos

El mensaje de error se lee **de abajo hacia arriba**: la última línea dice qué pasó, las anteriores dónde ocurrió.

```
Traceback (most recent call last):
  File "analisis.py", line 12, in <module>
    resultado = calcular_retorno(0, 105)
  File "analisis.py", line 5, in calcular_retorno
    return precio_final / precio_inicial - 1
ZeroDivisionError: division by zero
```

Lectura: el error es una división por cero, ocurrió en la línea 5 dentro de `calcular_retorno`, y esa función fue llamada desde la línea 12.

| Mensaje | Significa | Qué revisar |
|---|---|---|
| `SyntaxError: invalid syntax` | Python no entiende la escritura | Falta `:`, paréntesis o comilla, en esa línea **o la anterior** |
| `IndentationError` | Indentación inconsistente | Espacios de más o de menos; tabulaciones mezcladas |
| `NameError: name 'x' is not defined` | El nombre no existe | Error de tipeo, mayúsculas, o celda sin ejecutar |
| `TypeError: can only concatenate str` | Suma de texto con número | Convierta con `int()`, `float()` o `str()` |
| `TypeError: 'int' object is not callable` | Intentó llamar a un número | Paréntesis de más, o una variable que pisó una función |
| `ValueError: could not convert string to float` | Texto no numérico | Separador decimal, espacios, símbolo de moneda |
| `IndexError: list index out of range` | Posición inexistente | El último índice válido es `len(x) - 1` |
| `KeyError: 'AAPL'` | La clave no está en el diccionario | Use `.get()`, o revise mayúsculas y espacios |
| `AttributeError: 'list' object has no attribute...` | Ese método no existe para ese tipo | Verifique el tipo con `type()` |
| `ZeroDivisionError` | División por cero | Valide el denominador antes de dividir |
| `FileNotFoundError` | El archivo no existe | Revise la ruta y el nombre exacto |
| `ValueError: truth value of an array is ambiguous` | Un `if` sobre un arreglo completo | Use `.any()`, `.all()`, o `&` y `\|` |
| `SettingWithCopyWarning` | Modificando una posible copia en pandas | Agregue `.copy()` o use `.loc` |

### Manejar un error sin detener el programa

```python
lineas = ["AAPL;189.45", "MSFT;error", "JPM;198.20", "XOM;"]

precios = {}
rechazadas = []

for linea in lineas:
    try:
        ticker, valor = linea.split(";")
        precios[ticker] = float(valor)
    except ValueError:
        rechazadas.append(linea)

print(precios)         # {'AAPL': 189.45, 'JPM': 198.2}
print(rechazadas)      # ['MSFT;error', 'XOM;']
```

El bucle procesa lo procesable y **deja registro de lo descartado**. Ese registro es parte del resultado.

> Nunca escriba `except: pass`. Convierte un error visible en un resultado silenciosamente incorrecto, que es mucho peor.

---

## Anexo C — Quince comportamientos que sorprenden

1. **Asignar no copia.** `b = a` con una lista crea una segunda etiqueta sobre el mismo objeto.
2. **Los métodos que ordenan o invierten devuelven `None`.** `lista = lista.sort()` destruye la lista.
3. **Un valor por defecto modificable se comparte entre llamadas.** `def f(x=[])` acumula resultados.
4. **`/` siempre devuelve decimal**, aunque la división sea exacta.
5. **`//` redondea hacia abajo**, no hacia cero: `-7 // 2` da `-4`.
6. **Los decimales no son exactos.** Nunca compare con `==`.
7. **`round()` resuelve los empates hacia el par.** `round(2.5)` da `2`.
8. **El límite superior de un trozo se excluye**, salvo en `.loc` de pandas, que lo incluye.
9. **El texto es inmodificable.** Todo método devuelve una copia nueva.
10. **`and` y `or` devuelven un operando**, no `True` ni `False`.
11. **Asignar dentro de una función crea una variable local**, aunque exista una externa con el mismo nombre.
12. **Los trozos de un arreglo de NumPy son ventanas**, no copias; los de una lista sí son copias.
13. **pandas alinea por etiqueta**, no por posición, al operar entre Series.
14. **`NaN` no es igual a sí mismo.** Se detecta con `.isna()`.
15. **En NumPy y pandas se usan `&`, `|` y `~`**, no `and`, `or` ni `not`.

---

## Anexo D — Convenciones de escritura

Python tiene una guía de estilo oficial. Seguirla hace que cualquiera pueda leer su código.

```python
# Nombres
precio_cierre = 100          # variables y funciones: minúsculas con guión bajo
TASA_MAXIMA = 0.30           # valores fijos: mayúsculas
class CarteraInversion:      # clases: iniciales mayúsculas, sin guiones

# Espacios
x = 1                        # espacios alrededor del =
f(a, b)                      # espacio tras la coma, no antes del paréntesis
lista[0]                     # sin espacio antes del corchete
def f(x, y=1):               # sin espacios alrededor del = de un parámetro

# Longitud de línea: hasta 79-100 caracteres

# Importaciones al inicio, agrupadas:
import math                  # 1. incluidas en Python

import numpy as np           # 2. de terceros
import pandas as pd

from finanzas import van     # 3. propias
```

Formateo automático:

```bash
pip install ruff
ruff format archivo.py       # corrige el formato
ruff check archivo.py        # detecta problemas
```

---

## Anexo E — Formulario

| Concepto | Fórmula | Función del curso |
|---|---|---|
| Interés simple | $VF = VP(1 + i \cdot n)$ | `valor_futuro_simple` |
| Interés compuesto | $VF = VP(1 + i)^n$ | `valor_futuro_compuesto` |
| Capitalización m veces | $VF = VP(1 + i/m)^{m \cdot n}$ | `valor_futuro_capitalizado` |
| Capitalización continua | $VF = VP \cdot e^{i \cdot n}$ | `valor_futuro_continuo` |
| Tasa efectiva anual | $TEA = (1 + i/m)^m - 1$ | `tasa_efectiva_anual` |
| Valor actual neto | $VAN = \sum_{t=0}^{n} \dfrac{F_t}{(1+i)^t}$ | `van` |
| Tasa interna de retorno | $VAN(TIR) = 0$ | `tir` |
| Cuota de crédito | $C = \dfrac{P \cdot i}{1 - (1+i)^{-n}}$ | `cuota_credito` |
| Valor presente de anualidad | $VP = C \cdot \dfrac{1 - (1+i)^{-n}}{i}$ | `valor_presente_anualidad` |
| Perpetuidad creciente | $VP = \dfrac{F}{i - g}$ | `valor_presente_perpetuidad` |
| Retorno simple | $r_t = \dfrac{P_t}{P_{t-1}} - 1$ | `retorno_simple` |
| Retorno logarítmico | $r_t = \ln\left(\dfrac{P_t}{P_{t-1}}\right)$ | `retorno_logaritmico` |
| Retorno anualizado | $\left(\prod(1+r_t)\right)^{1/a} - 1$ | `retorno_anualizado` |
| Volatilidad anualizada | $\sigma_{anual} = \sigma_{diaria} \cdot \sqrt{252}$ | `volatilidad` |
| Ratio de Sharpe | $S = \dfrac{r_p - r_f}{\sigma_p}$ | `sharpe` |
| Beta | $\beta = \dfrac{Cov(r_i, r_m)}{Var(r_m)}$ | `beta` |
| CAPM | $E(r_i) = r_f + \beta_i(E(r_m) - r_f)$ | `capm` |
| Riesgo de dos activos | $\sigma_p = \sqrt{w_1^2\sigma_1^2 + w_2^2\sigma_2^2 + 2w_1w_2\sigma_1\sigma_2\rho}$ | `riesgo_cartera_dos_activos` |
| Riesgo de cartera | $\sigma_p = \sqrt{w^{T} \Sigma\, w}$ | `riesgo_cartera` |
| Valoración por dividendos | $P_0 = \dfrac{D_1}{k - g}$ | `gordon` |
| Precio de un bono | $P = \sum \dfrac{C}{(1+y)^t} + \dfrac{N}{(1+y)^n}$ | `precio_bono` |
| Duración de Macaulay | $D = \dfrac{\sum t \cdot VP(F_t)}{P}$ | `duracion` |
| Duración modificada | $D_{mod} = \dfrac{D}{1 + y/m}$ | `duracion` |

---

## Qué sigue

Este curso cubre el lenguaje, las librerías de análisis y los cálculos financieros básicos. Las continuaciones naturales, en orden de dificultad:

1. **Programación orientada a objetos** — clases propias para modelar instrumentos y carteras.
2. **Optimización de carteras** — frontera eficiente, mínima varianza, máximo Sharpe con SciPy.
3. **Modelos de factores y regresión** — CAPM multifactorial con `statsmodels`.
4. **Valoración de derivados** — árboles binomiales, Black-Scholes, simulación de Monte Carlo.
5. **Medición de riesgo** — VaR y Expected Shortfall con validación estadística.
6. **Series de tiempo financieras** — modelos de volatilidad y pronóstico.

Todos ellos se construyen sobre las mismas herramientas de este curso: son aplicaciones de NumPy, pandas y SciPy, no un lenguaje distinto.

### Lecturas recomendadas

- Matthes, E. (2023). *Python Crash Course* (3ª ed.). No Starch Press.
- McKinney, W. (2022). *Python for Data Analysis* (3ª ed.). O'Reilly. Disponible gratis en [wesmckinney.com/book](https://wesmckinney.com/book/).
- Sweigart, A. (2019). *Automate the Boring Stuff with Python* (2ª ed.). Gratuito en [automatetheboringstuff.com](https://automatetheboringstuff.com/).

### Documentación oficial

[Tutorial de Python en español](https://docs.python.org/es/3/tutorial/) · [NumPy](https://numpy.org/doc/stable/user/absolute_beginners.html) · [pandas](https://pandas.pydata.org/docs/user_guide/10min.html) · [matplotlib](https://matplotlib.org/stable/tutorials/index.html)

---

## Licencia

MIT. Material de libre uso y adaptación con atribución.

## Contribuciones

Correcciones, ejercicios adicionales y mejoras vía *pull request* o *issue*.

<br>

---

<div align="center">

<h2> Developer </h2>

<h3> Felipe Andrés Ruiz Rojas </h3>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-linkedin.com%2Fin%2Fruizrojasfel-blue)](https://www.linkedin.com/in/ruizrojasfel) [![Website](https://img.shields.io/badge/Website-felruiz--dev.netlify.app-lightblue)](https://felruiz-dev.netlify.app/)

Copyright © 2026 Fel Ruiz
</div>
