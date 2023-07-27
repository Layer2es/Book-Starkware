## STARKS eficientes
En este capítulo, llegó el momento de comprender cómo los STARKs representan una versión más eficiente de los [**(PCP)**](https://en.wikipedia.org/wiki/Probabilistically_checkable_proof), un protocolo que permite establecer la exactitud de las declaraciones de **CI**, mediante una verificación aleatoria local en una prueba larga. Este protocolo se lleva a cabo entre un prover **PCP** y un verificador **PCP**.

En esta versión, se han realizado ajustes para mejorar la cohesión y la fluidez del texto. Se ha utilizado un lenguaje más claro y directo para explicar la relación entre los STARKs y los PCP, así como su función en la verificación de declaraciones de información computacional.

El prover **PCP** produce una cadena de prueba `𝚿` que codifica el seguimiento de cálculo de la declaración de `CI`, a pesar de que `𝚿` es más larga que la traza de cálculo de pasos `T`. Sin embargo, la cadena de prueba `𝚿` tiene la propiedad especial de que puede ser validada a través de una prueba probabilística que lee solo una pequeña parte de `𝚿`.

El verifier **PCP**, al recibir la misma declaración de **CI** `(A, x, y, T)`, puede validar la cadena de prueba `𝚿` leyendo aleatoriamente unas pocas ubicaciones de `𝚿` y luego realizar una **"verificación local"** económica en los valores leídos. El número de ubicaciones de lectura puede ser una pequeña constante, como 3, independientemente de la longitud de la traza de cálculo `T`.

Si la declaración de CI es verdadera, el verifier siempre aceptará. Sin embargo, si la declaración de CI es falsa, el verificador la rechazará con alta probabilidad, sin importar cómo se haya elegido la cadena de prueba `𝚿`.

![graph](./assets/Stark_Sudoku.gif)
<div align="center">
<em></em>
</div>

En la imagen animada podemos ver un ejemplo de **PCP** con un conjunto de resticciones un sudoku y ahora veremos como los STARKs eficiente pueden mejorar la eficiencia de las **PCP** y **MPCP** con **IOPs**.