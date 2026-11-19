# Primeros pasos en R: de los datos al análisis

**Taller práctico de iniciación a R y RStudio · 150 minutos · V Congreso y XVI Jornadas de Usuarios de R (R Hispano), Canarias, 2026**

Este repositorio contiene el material del taller **«Primeros pasos en R: de los datos al análisis»**, dirigido a personas que quieren empezar a trabajar con datos utilizando R, sin necesidad de experiencia previa en programación.

El taller sigue una idea sencilla: **aprender R mientras respondemos preguntas reales con datos**. En lugar de estudiar funciones de manera aislada, recorreremos un análisis completo: formular una pregunta, importar datos, explorar su estructura, seleccionar información, visualizar resultados e interpretarlos.

> **No necesitas saber R para empezar a trabajar con datos. Necesitas empezar a trabajar con datos para aprender R.**

## ¿A quién va dirigido?

A personas que:

- nunca han utilizado R o tienen conocimientos muy básicos;
- han trabajado con hojas de cálculo y quieren dar sus primeros pasos en programación;
- desean aprender a explorar, transformar y visualizar datos de una forma reproducible.

No se requieren conocimientos previos de programación ni de estadística avanzada.

## ¿Qué aprenderás?

Al finalizar el taller podrás:

- distinguir entre **R**, **RStudio**, **R base** y los **paquetes** que amplían sus posibilidades;
- crear objetos, ejecutar funciones y trabajar en un proyecto de RStudio;
- importar un fichero de datos con `readr`;
- comprender qué representa cada observación y qué contienen las variables;
- seleccionar, filtrar y ordenar datos con `dplyr`;
- crear gráficos de barras y de líneas con `ggplot2`;
- interpretar resultados con cautela y documentar el análisis en **Quarto**.

Durante el taller utilizaremos principalmente el ecosistema **tidyverse**. Es una elección didáctica por su legibilidad, no porque sea la única forma de programar en R: muchas de estas tareas también pueden resolverse con R base.

## Los datos: una pregunta real sobre Canarias

Trabajaremos con el conjunto de datos **«Edad media y edad mediana según sexos y lugar de nacimiento en relación con la residencia. Canarias, islas y municipios por años»** (`E30243A_000014`), publicado por el **Instituto Canario de Estadística (ISTAC)** a partir de datos del **Instituto Nacional de Estadística (INE)**.

La copia distribuida para el taller contiene datos de **2021 a 2025** y permite investigar cuestiones como:

- ¿Cuál es la edad media de Canarias en 2025?
- ¿Qué diferencias se observan entre hombres y mujeres?
- ¿Cómo ha evolucionado la edad media desde 2021?
- ¿Qué diferencias existen entre islas?
- ¿Qué cambia según el lugar de nacimiento?
- ¿Cuentan la edad media y la mediana la misma historia?

El fichero se facilita en **TSV**, un formato de texto tabular en el que las columnas se separan mediante tabuladores. **No es necesario tener Excel** para trabajar con él.

**Fuente y consulta del conjunto de datos:** [Visualizador estadístico del ISTAC](https://www3.gobiernodecanarias.org/istac/statistical-visualizer/visualizer/data.html?resourceType=dataset&agencyId=ISTAC&resourceId=E30243A_000014&version=%7Elatest#visualization/table).

**Referencia de la copia utilizada:** dataset `E30243A_000014`, versión 2.0 del recurso JSON-stat consultado, actualizado el **14 de enero de 2026**. El fichero del repositorio es una descarga para uso didáctico, por lo que los datos oficiales disponibles en línea pueden actualizarse posteriormente.

## Estructura del repositorio

```text
primeros-pasos-r/
├── README.md
├── primeros-pasos-r.qmd
├── datos/
│   └── dataset-ISTAC-E30243A_000014.tsv
└── LICENSE
```

- **`primeros-pasos-r.qmd`**: guía principal del taller, con explicaciones, código ejecutable, ejercicios y soluciones plegables.
- **`datos/`**: copia local del TSV, que permite seguir las actividades sin depender de una conexión a Internet.
- **`LICENSE`**: condiciones de reutilización de los materiales originales del taller; las fuentes de datos se rigen por sus propias condiciones.

## Antes del taller: prepara tu ordenador

### 1. Instala R

Descarga e instala R desde [CRAN](https://cran.r-project.org/), el repositorio oficial de R.

### 2. Instala RStudio Desktop

Descarga la versión gratuita de [RStudio Desktop](https://posit.co/download/rstudio-desktop/).

**Instala primero R y después RStudio.**

### 3. Instala tidyverse

Abre RStudio y ejecuta en la consola:

```r
install.packages("tidyverse")
```

Este paso solo es necesario si todavía no tienes instalado el paquete. Se necesita conexión a Internet durante la instalación.

### 4. Descarga este repositorio

En GitHub, selecciona **Code → Download ZIP**, descomprime el archivo en una carpeta de tu ordenador y abre el proyecto desde esa carpeta en RStudio (**File → New Project → Existing Directory**, si no existe todavía un archivo `.Rproj`).

También puedes clonar el repositorio si ya sabes utilizar Git, pero **no hace falta conocer Git ni GitHub** para realizar el taller.

### 5. Abre el material y comienza

Abre `primeros-pasos-r.qmd` desde RStudio. Ejecuta los bloques de código en orden y realiza las actividades propuestas.

Para empezar a utilizar las funciones del taller, ejecuta:

```r
library(tidyverse)
```

El conjunto de datos se importa con:

```r
edad_canarias <- readr::read_tsv(
  "datos/dataset-ISTAC-E30243A_000014.tsv"
)
```

> **Importante:** el archivo `primeros-pasos-r.qmd` contiene rutas relativas. Mantén la estructura de carpetas del repositorio y trabaja desde la carpeta raíz del proyecto.

**Quarto:** si quieres generar una página HTML con los textos, resultados y gráficos, necesitas tener instalado [Quarto](https://quarto.org/docs/get-started/). Para seguir el taller y ejecutar los bloques de R en RStudio puedes trabajar directamente sobre el archivo `.qmd`.

## ¿Cómo está organizado el taller?

| Bloque | Actividad |
| --- | --- |
| Bienvenida y entorno | R, RStudio, R base, paquetes y Quarto |
| Primeros pasos | Objetos, funciones, vectores y ayuda |
| Nuestros datos | Importación y exploración del TSV del ISTAC |
| Preguntas a los datos | Filtrado, comparaciones y ordenación |
| Visualización | Gráficos de barras y de evolución temporal |
| Interpretación | Qué podemos concluir y qué no |
| Mini-análisis | Resolver una pregunta con autonomía |

El taller combina explicaciones breves, ejemplos ejecutables, pequeños ejercicios y soluciones que puedes consultar cuando lo necesites. Está diseñado para durar **2 horas y 30 minutos**, pero también puedes seguirlo a tu ritmo.

## ¿Y el acceso mediante API?

El taller utiliza principalmente el fichero local para evitar problemas de conectividad durante la sesión. El material incluye además una breve referencia a cómo obtener datos directamente desde la API del ISTAC mediante el paquete [`istacr`](https://cran.r-project.org/package=istacr) disponible en CRAN.

**No es necesario instalar `istacr` para completar las actividades principales.**

## Autoría y reconocimiento

**Elisa Jorge González**  
Taller organizado en el contexto del **V Congreso y XVI Jornadas de Usuarios de R (R Hispano)**, celebrado en Canarias en 2026.

Los materiales docentes se comparten como recurso educativo reutilizable. La autoría de las explicaciones, ejercicios y ejemplos del taller no debe confundirse con la titularidad de los datos estadísticos oficiales.

## Licencia y reutilización

Los **materiales docentes originales** de este repositorio se distribuyen bajo **Creative Commons Atribución 4.0 Internacional (CC BY 4.0)**. Puedes copiarlos, compartirlos y adaptarlos, citando la autoría, indicando la licencia y señalando los cambios realizados.

El **fichero de datos del ISTAC está excluido de esa licencia de autoría**: su reutilización se sujeta a las condiciones de la fuente oficial. Al reutilizarlo, debe citarse **«Fuente: Instituto Canario de Estadística (ISTAC)»**, mencionar su fecha de actualización cuando esté disponible y no sugerir que el ISTAC patrocina o avala esta reutilización.

Consulta las [condiciones de reutilización del ISTAC](https://www.gobiernodecanarias.org/istac/aviso_legal.html).

Los ejemplos de código incluidos en el documento forman parte del material docente. Si este repositorio incorpora en el futuro scripts o software independiente para su reutilización, podrá añadirse para ellos una licencia específica de software, como **MIT**.

---

**El objetivo no es memorizar funciones: es empezar a pensar y trabajar con datos usando R.**
