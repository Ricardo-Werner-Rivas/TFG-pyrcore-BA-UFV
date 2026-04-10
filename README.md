# TFG `pyrcore`: Business Analitics UFV
Este repositorio contiene el código para el <ins>Trabajo de Fin de Grado</ins> (TFG, en adelante).

A continuación, se hace una explicación del funcionamiento del proyecto.
<details>
<summary><b>Consideraciones previas</b></summary>

El presente proyecto consiste en la creación de un paquete de Python (`pyrcore`) que permita fusionar las ventajas de los lenguajes de programación R y Python mediante la replicación de objetos R con **P**rogramación **O**rientada a **O**bjetos (**POO**, en adelante).

Si bien técnicamente es un proyecto de investigación, pues su objetivo es la creación de una herramienta, uno no podía presentar sus propios temas de investigación, sino postularse a uno de los existentes. Debido a esto, se me pidió que adaptase la estructura del trabajo al modelo de <ins>Trabajo de Consultoría</ins>.

Dadas las circunstancias mencionadas, es importante aclarar un aspecto clave: **`pyrcore`** es el **centro** de este proyecto. Eso no significa que los análisis vayan a dejarse de lado. Todas las partes del TFG conservarán su rigor académico, pero el centro de atención se desplaza hacia el paquete `pyrcore`, volviendo los análisis un aspecto menos relevante.

El análisis se realiza en calidad de prueba de contraste, comparando sintaxis de código y los resultados de su ejecución.

Dado que también se utiliza código R para el contraste, cada modelo se hará más de una vez.

Dada la naturaleza del proyecto, se elegirá un caso distinto según el modelo que se quiera comprobar.

Por último, dado que los modelos de análisis no resuelven un problema, sino que es `pyrcore` el que lo hace, para la realización de modelos se usarán casos hipotéticos creados *ad-hoc*.
</details>
<details>
<summary>Enlaces relevantes</summary>
<table>
    <thead>
        <tr>
            <th colspan="2" style="text-align: center;">Enlaces</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th style="text-align: center;"><code>pyrcore</code></th>
            <td style="text-align: center;"><a href="https://github.com/Ricardo-Werner-Rivas/pyrcore" target="_blank"><img src="https://shields.io/badge/GitHub-pyrcore-blue?logo=GitHub"></a> <a href="https://github.com/Ricardo-Werner-Rivas/pyrcore/blob/PyPI/LICENSE" target="_blank"><img src="https://shields.io/github/license/Ricardo-Werner-Rivas/pyrcore"></a></td>
        </tr>
        <tr>
            <th style="text-align: center;">Lanzamiento</th>
            <td style="text-align: center;"><a href="https://pypi.org/project/pyrcore/" target="_blank"><img src="https://img.shields.io/pypi/v/pyrcore"></a></td>
        </tr>
        <tr>
            <th style="text-align: center;">Desarrollo</th>
            <td style="text-align: center;"><a href="https://test.pypi.org/project/pyrcore/" target="_blank"><img src="https://img.shields.io/badge/dynamic/json?url=https://test.pypi.org/pypi/pyrcore/json&query=$.info.version&label=TestPyPI"></a></td>
        </tr>
    </tbody>
</table>
</details>

## `pyrcore`
El paquete `pyrcore` es una librería programada en Python puro, basado en `arrays` de **NumPy**, que importa objetos R tales como vectores y su función de combinación (`c()`), matrices (`matrix`) y series temporales (`ts`) a Python mediante POO con abstracción y estructura modular. Aunque el paquete es de código abierto, amparado bajo una licencia [MIT](https://github.com/Ricardo-Werner-Rivas/pyrcore/blob/PyPI/LICENSE), ha sido creado expresamente para este TFG y, de hecho, es su núcleo.

El paquete se está diseñando en un repositorio de GitHub aparte, al que se puede acceder mediante este [enlace](https://github.com/Ricardo-Werner-Rivas/pyrcore). El motivo de esto es que se espera que su vida útil se prolongue más allá de la duración de este TFG y que, por tanto, se le dé soporte. También se puede consultar el proyecto `pyrcore` en [PyPI](https://pypi.org/project/pyrcore/) o en [TestPyPI](https://test.pypi.org/project/pyrcore/).

Debido a que es un proyecto de código abierto, aunque las contribuciones están limitadas a mí hasta que el TFG sea evaluado, tanto la documentación como los comentarios del código como los *commits* están en **inglés**.
### Funcionalidades
El paquete `pyrcore` aspira a implementar las siguientes funcionalidades:
* Vectores atómicos de R: **Estable** (clase `Vector`)
* Función de combinación `c()`, para la creación de vectores: **Estable** (función `c()`)
* Matrices de R y función `matrix()`: **Estable** (clase `matrix`)
* Clase `ts` (*time-series*: serie temporal) de R: <ins>**En desarrollo**</ins> (clase `TimeSeries`)
* Clase `mts` (*multivariate time-series*: serie temporal multivariante)
* Función `ts()`, constructora de `ts` y `mts`
* Herramientas de integración con los algoritmos de los modelos en Python
## Proyecto
El proyecto consta de tres partes claramente diferenciadas:
### 1. Ingeniería del Dato
La parte de **Ingeniería del Dato** consiste en la extracción y limpieza de los datos que van a utilizarse y será algo distinta en este TFG.
<details>
<summary><b>Esquema</b>:</summary>

1. Se decidirá qué casos hipotéticos se estudiarán en el TFG.

2. Se seleccionarán los *datasets* que se usarán para tal fin, preferiblemente de entre los que ya han sido preseleccionados.
3. Se extraerán los *datasets* seleccionados. Los *datasets* preseleccionados ya han sido extraídos para la entrega del anteproyecto, pero volverán a extraerse si siguen disponibles en sus fuentes.
</details>

#### Casos de estudio
Se ha asignado un caso de estudio a cada una de las funcionalidades relevantes (`ts` y `mts`):
1. Para series temporales univariantes, se aplica el siguiente caso de estudio: *Análisis temporal de las series de producción de gas de esquisto en varios sitios de EEUU para el periodo enero de 2000 a agosto de 2022 (2000.01-2022.08).* Modelo *ARIMA*.
2. Para series temporales multivariantes, se aplica el siguiente caso de estudio: *Análisis temporal de una serie temporal multivariante de la bolsa china para crear un modelo capaz de predecir su comportamiento.* Modelo *VAR*.
### 2. Análisis del Dato
La parte de **Análisis del Dato** consiste en la aplicación de los conocimientos estadísticos adquiridos durante el grado mediante la aplicación de modelos automatizados en lenguajes como Python o R, que son los dos lenguajes de programación enseñados durante el grado. En el caso de esta segunda parte, el procedimiento se realiza normalmente, sin perjuicio de que haya ligeras variaciones.
<details>
<summary><b>Esquema</b>:</summary>

1. Se decidirá normalmente el modelo apropiado para el caso hipotético escogido.

2. Se realizará el modelo en su lenguaje de programación nativo. Si dicho lenguaje es R, que es lo más probable, también se realizará su equivalente en Python. En tal caso, se hará un análisis de la sintaxis del código de ambos lenguajes y se compararán. En el caso de los modelos *ARIMA*, la función `auto.arima()`, del paquete `forecast` de R, y la función `auto_arima()`, del paquete `pmdarima` de Python, se usarán solo para validación de resultados y no se considerará el modelo como apropiadamente aplicado por su uso, si no que se realizará el análisis paso a paso.
3. Se interpretará cada modelo de cada lenguaje, observando discrepancias entre resultados si las hubiera. Esto prepara el terreno para usar el paquete `pyrcore` el análisis de su utilidad en la tercera parte, a entregar en mayo.
</details>

### 3. Análisis de Negocio
En esta última parte se concreta una conclusión final del trabajo hecho y se introduce el uso del paquete `pyrcore`. Con `pyrcore` se replican los pasos de los modelos hechos con Python, comparando la sintaxis del código y los resultados. A continuación, y nuevamente, se exponen las diferencias de este TFG con un Trabajo de Consultoría clásico.
<details>
<summary><b>Esquema</b>:</summary>

1. Se dará una conclusión por cada modelo realizado sobre un mismo *dataset*. Si se hubiere realizado múltiples veces un mismo modelo, por haberlo realizado en distintos lenguajes se dará una conclusión **por cada repetición** del modelo y se compararán.

2. Se utiliza `pyrcore` para repetir los modelos hechos en Python y se comparan sintaxis, resultados y conclusiones. Este paso es pura repetición, y no requiere esfuerzo lógico alguno, motivo por el que lo ubico en este punto, dado que organizarlo así permite que ninguna de las tres partes quede muy sobrecargada.
3. En base a lo anterior, se extraerá una conclusión sobre la utilidad del paquete `pyrcore` para el análisis, y/o ciencia, de datos.
4. Finalmente, se dará una conclusión final sobre la utilidad del paquete `pyrcore` en el ámbito del negocio. En la conclusión se mencionará explícitamente si se ha solucionado el problema o no o, en su defecto, si se ha visto mitigado y en qué medida.
</details>

## Resultado esperado
Se espera que `pyrcore` pueda aportar al mundo de la ciencia y el análisis de datos mediante la integración, total o parcial, de la potencia estadística de R en el lenguaje escalable Python.

Sin embargo, <ins>no favorable</ins> sería un resultado válido para el TFG, pues se pretende estudiar su impacto para el análisis y la ciencia de datos. Dicho lo cual, un servidor considera este resultado altamente improbable, puesto que, en el peor de los casos, se concluiría que las herramientas de integración con las librerías de modelización no funcionan correctamente, lo que no vuelve el paquete `pyrcore` una solución inútil.

Evidentemente, una de las conclusiones será que se debe seguir trabajando en la eficiencia, hablando de tiempo de ejecución del código, de las clases y funciones del paquete, ya que lo ideal es usar extensiones de C/C++, leguaje que no forma parte del contenido del grado, para un paquete así. En su lugar se utilizan, como base de los objetos, `arrays` de la librería **NumPy**, que funcionan de forma aritméticamente similar a los vectores y matrices de R y están programados con C/C++, que son altamente eficientes.
## Política de uso de Inteligencia Artificial
El uso de **I**nteligencia **A**rtificial (**IA**, en adelante) generativa está estrictamente limitado a mi aprendizaje. Gracias a su uso, refiriéndome especialmente a ChatGPT, he podido aprender extremadamente rápido a aplicar conceptos de programación que a un estudiante que solo ha tenido tres asignaturas cuatrimestrales de programación con lenguajes distintos le resultarían increíblemente complejas. Los modelos LLM proporcionan un hilo del que tirar, pero no pueden ni deben programar en lugar del programador. El *vibe coding* no es solo imposible en la práctica sino que es una lacra para los profesionales serios.

El verdadero uso de la IA reside en sintetizar y acceder a información. Si se le pide a ChatGPT que escriba código para una funcionalidad compleja y este utiliza librerías y funciones que al programador le resultan nuevas, este puede seguir preguntando por esos elementos concretos hasta tener una idea más o menos clara y, entonces, leer la documentación relacionada y ponerse a experimentar. Es ahí donde reside el valor de la IA generativa y los modelos LLM. Lo mismo puede aplicarse a la estadística, pero un analista se verá en problemas en más ocasiones por cuestiones relacionadas a la programación.

La IA generativa puede usarse en el presente proyecto para, por ejemplo, estructurar la ejecución de una idea, obtener información sobre el uso de una librería que me sea desconocida, obtener rápidamente información de estadística avanzada o estructurar con mayor comodidad los entregables del TFG. Incluso si se copiare código directamente devuelto por IA, siempre comento mi código y doy explicaciones y/o expongo razonamientos en celdas de *Markdown*.
