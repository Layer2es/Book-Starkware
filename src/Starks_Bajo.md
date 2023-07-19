# Pruebas de Bajo Grado
Las pruebas de bajo grado son realmente el corazón del proceso de verificación.

El supuesto de comprobación de bajo grado establece la existencia de un verificador probabilístico que comprueba si una función f es de grado como máximo d ≪ |𝔽|. El verificador debe distinguir entre los dos casos siguientes:

1. **La función `f` es igual a un polinomio de bajo grado:** es decir, existe un polinomio `p(x)` sobre `𝔽`, de grado menor que `d`, que coincide con `f` en todas partes.
2. **La función `f` está lejos de TODOS los polinomios de bajo grado:** por ejemplo, necesitamos modificar al menos el **10%** de los valores de `f` antes de obtener una función que concuerde con un polinomio de grado inferior a `d`.

La aritmetización muestra que un prover honesto que trate con una afirmación verdadera caerá en el primer caso, mientras que un prover (posiblemente malicioso) que intente **"probar"** una afirmación falsa caerá, con alta probabilidad, en el segundo caso.

Otra forma de ver esto es que el polinomio de traza correcto combinado con las restricciones será necesariamente de grado bajo, el grado proviene del número de pasos en nuestra traza (probablemente unos pocos millones), y la combinación de esto con los polinomios de restricción (probablemente < 10).

En general, cabría esperar que los polinomios **"correctos"** tuvieran un grado de alrededor de `10⁷` , mientras que un prover tramposo que eligiera puntos al azar del campo `𝔽` obtendría, tras la interpolación, polinomios de grado comparable al tamaño del campo, es decir, del orden de `2²⁵⁶`

