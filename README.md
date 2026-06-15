# TFG `pyrcore`: Business Analitics UFV
Este proyecto ha cambiado mucho desde su concepción en el anteproyecto. En un inicio consistía en fusionar dos lenguajes de programación ligeramente para aprovechar sus puntos fuertes. Actualmente se ha convertido en un proyecto orientado a la creación de un producto, aunque este sea de código abierto, que permita integrar ambos lenguajes de programación, R y Python, a nivel sintáctico para permitir a los equipos de analistas trabajar con los puntos fuertes de ambos en un solo lenguaje. La eficiencia no es prioridad para este proyecto, por cuestiones de tiempo, aunque pretendo corregirlo en el futuro.

El paquete `pyrcore` replica los vectores, matrices y series temporales univariantes de R mediante **P**rogramación **O**rientada a **O**bjetos (**POO**). Los detalles se encuentran más adelante. Los objetos tienen attributos de R como propiedades y poseen algunas de las características de algunos objetos de *Pandas* para facilitar su integración con librerías de análisis de datos, a pesar de que la librería `pandas` no se ha usado para programar las funcionalidades no relacionadas con transformar el objeto a objeto `pandas`, sino que estas características se han replicado independientemente.

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
El paquete `pyrcore` es una librería programada en Python puro que aporta a Python clases basadas en diversos objetos R y algunas de sus funciones. Las clases envuelven `arrays` de `NumPy` u otras clases de la librería y tienen métodos y propiedades que imitan varias funciones de R relacionadas con los atributos de los objetos. Los atributos de R de las instancias se almacenan en un diccionario que es un atributo de instancia, pero también son accesibles mediante la sintaxis `<instancia>.<atributo>` como si fueran atributos de instancia. Así, por ejemplo, para obtener o modificar los nombres de un vector `v` llamaríamos a `v.names` en lugar de `names(v)`.

El paquete se está desarrollando en un repositorio de GitHub aparte, al que se puede acceder mediante este [enlace](https://github.com/Ricardo-Werner-Rivas/pyrcore). El motivo de esto es que se espera que su vida útil se prolongue más allá de la duración de este TFG y que, por tanto, se le dé soporte y siga siendo de **código abierto**. También se puede consultar el proyecto `pyrcore` en [PyPI](https://pypi.org/project/pyrcore/) o en [TestPyPI](https://test.pypi.org/project/pyrcore/).

### Funcionalidades
Los objetos aportados por `pyrcore` son:
* Clase `Vector`: vectores atómicos, aunque se permiten vectores multitipo si se pasa el tipo `object`. Utilizan un `array` unidimensional como núcleo y admite nombres.

* Función `c()`: función de combinación `c()` para la creación de vectores.
* Clase `matrix`: matrices. Utilizan un `array` bidimensional como núcleo y también puede ser multitipo si se pasa el tipo `object`.
* Clase `TimeSeries`: series temporales univariantes (`ts` en R). Usan vectores como núcleo.
* ~~Clase `MultiVariateTimeSeries`~~: series temporales multivariantes (`mts` en R). Usan matrices como núcleo. Implementan las propiedades `loc` y `iloc` de los `DataFrame`s de *Pandas*. Aún están en desarrollo y no van a usarse en el proyecto por ese motivo.
* Función `ts()`: Función constructora de series temporales, que distinguirá cuál de los dos tipos de serie debe crear. Se ha implementado una versión provisional que solo construye series univariantes mientras se termina el desarrollo de las series multivariantes.
* Las clases `TimeSeries` y `MultiVariateTimeSeries` implementan el método `to_pandas` como herramienta provisional de integración con librerías de análisis de datos, que podrían esperar objetos `pandas.Series` o `pandas.DataFrame`.

## Proyecto
El proyecto se divide en tres partes:
1. Ingeniería del Dato.

2. Análisis del Dato.
3. Análisis de Negocio.

Estas partes se desarrollarán sobre un caso de estudio que ha sido escogido para ilustrar la diferencia sintáctica entre R y Python y la comodidad que puede aportar `pyrcore` al análisis de datos en Python, especialmente en proyectos en los que normalmente se usarían ambos lenguajes o en los que R no se puede utilizar, aunque sería lo más sencillo, por su falta de escalabilidad y se acaban utilizando herramientas como *PySpark*.

El caso de estudio es el siguiente: *Análisis temporal de las series de producción de gas de esquisto en varios sitios de EEUU para el periodo enero de 2000 a agosto de 2022 (2000.01-2022.08).* Modelo *ARIMA*. Para ello se dispone de un *dataset* con distintas series temporales de la producción de gas de esquisto. Este *dataset* se obtuvo en la asignatura de Econometría como parte del trabajo final de la asignatura. Debe elegirse una serie temporal del *dataset* y aplicar un modelo *ARIMA* sobre ella. Utilizaré una serie temporal distinta de la que escogí para dicho proyecto final de Econometría.

### 1. Ingeniería del Dato
1. Extracción de la serie temporal escogida desde el fichero proporcionado.

2. Correcciones de formato y tipado de los datos.
3. Análisis exploratorio de los datos con R.
4. Anotación de las transformaciones requeridas para el modelo *ARIMA*.

### 2. Análisis del Dato
1. Aplicación del modelo *ARIMA* en R.

2. Aplicación del modelo *ARIMA* en Python.
3. Interpretación del resultado del modelo para cada lenguaje (que debería ser la misma).
4. Comparación sintáctica del código de ambos procedimientos.
<details>
<summary><b>NOTA</b>:</summary>

La función `auto.arima()` del paquete `forecast` de R y la función `auto_arima()` del paquete `pmdarima` de Python se usarán solo para validación de resultados y no se considerará el modelo como apropiadamente aplicado por su uso, si no que se realizará el análisis paso a paso.
</details>

### 3. Análisis de Negocio
1. Se utiliza `pyrcore` para repetir el modelo *ARIMA* hecho en Python y se comparan sintaxis, resultados y conclusiones. Este paso es pura repetición, y no requiere esfuerzo lógico alguno, motivo por el que lo ubico en esta parte, dado que organizarlo así permite que ninguna de las tres partes quede muy sobrecargada.

2. En base a lo anterior, se extraerá una conclusión sobre la utilidad del paquete `pyrcore` para el análisis, y/o ciencia, de datos.
3. Finalmente, se dará una conclusión final sobre la utilidad del paquete `pyrcore` en el ámbito del negocio. En la conclusión se mencionará explícitamente si se ha solucionado el problema o no o, en su defecto, si se ha visto mitigado y en qué medida.

## Resultado esperado
Se espera que `pyrcore` pueda aportar al mundo de la ciencia y el análisis de datos mediante la integración, total o parcial, de la potencia estadística de R en el lenguaje escalable Python.

Sin embargo, <ins>no favorable</ins> sería un resultado válido para el TFG, pues se pretende estudiar su impacto para el análisis y la ciencia de datos. Dicho lo cual, un servidor considera este resultado altamente improbable, puesto que, en el peor de los casos, se concluiría que las herramientas de integración con las librerías de modelización no funcionan correctamente, lo que no vuelve el paquete `pyrcore` una solución inútil.

Evidentemente, una de las conclusiones será que se debe seguir trabajando en la eficiencia, hablando de tiempo de ejecución del código, de las clases y funciones del paquete, ya que lo ideal es usar extensiones de C/C++, leguaje que no forma parte del contenido del grado, para un paquete así. En su lugar se utilizan, como base de los objetos, `arrays` de la librería **NumPy**, que funcionan de forma aritméticamente similar a los vectores y matrices de R y están programados con C/C++, que son altamente eficientes.

## Política de uso de Inteligencia Artificial
El uso de **I**nteligencia **A**rtificial (**IA**, en adelante) generativa está estrictamente limitado a mi aprendizaje. Gracias a su uso, refiriéndome especialmente a ChatGPT, he podido aprender extremadamente rápido a aplicar conceptos de programación que a un estudiante que solo ha tenido tres asignaturas cuatrimestrales de programación con lenguajes distintos le resultarían increíblemente complejas. Los modelos LLM proporcionan un hilo del que tirar, pero no pueden ni deben programar en lugar del programador. El *vibe coding* no es solo imposible en la práctica sino que es una lacra para los profesionales serios.

El verdadero uso de la IA reside en sintetizar y acceder a información. Si se le pide a ChatGPT que escriba código para una funcionalidad compleja y este utiliza librerías y funciones que al programador le resultan nuevas, este puede seguir preguntando por esos elementos concretos hasta tener una idea más o menos clara y, entonces, leer la documentación relacionada y ponerse a experimentar. Es ahí donde reside el valor de la IA generativa y los modelos LLM. Lo mismo puede aplicarse a la estadística, pero un analista se verá en problemas en más ocasiones por cuestiones relacionadas a la programación.

La IA generativa puede usarse en el presente proyecto para, por ejemplo, estructurar la ejecución de una idea, obtener información sobre el uso de una librería que me sea desconocida, obtener rápidamente información de estadística avanzada o estructurar con mayor comodidad los entregables del TFG. Incluso si se copiare código directamente devuelto por IA, siempre comento mi código y doy explicaciones y/o expongo razonamientos en celdas de *Markdown*.