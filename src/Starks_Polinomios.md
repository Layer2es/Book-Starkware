## Polinomios
Los polinomios son una poderosa herramienta algebraica que se utiliza en diversas ramas de las matemáticas y la física. Estas expresiones algebraicas están formadas por términos que contienen variables y coeficientes. Los términos son la suma o resta de monomios, que son productos de constantes y variables elevadas a exponentes enteros no negativos.

Un polinomio puede tener una o varias variables, y su grado está determinado por el exponente más alto presente en los términos del polinomio. Por ejemplo, el polinomio `3x² - 2x + 1`  es un polinomio de grado 2, ya que el término de mayor grado tiene un exponente de 2.

Los polinomios se pueden sumar, restar, multiplicar y dividir, y se emplean en ecuaciones algebraicas, cálculo, geometría y muchas otras ramas de las ciencias exactas.

**¿Por qué no evalúa el verifier los propios polinomios?**

* Prque, en realidad, el prover no envía todos los polinomios al verificador, si lo hiciera perderíamos sucintez, contienen más información que nuestra declaración original, por lo que el prover sólo proporciona un compromiso con los polinomios.

**¿Qué propiedades de los polinomios son importantes en este caso?**

* Los polinomios son buenos códigos de corrección de errores.

Si tenemos polinomios de grado `d` sobre un dominio de codificación `D`, y dos mensajes `m₁` y `m₂`, entonces  `m₁` y `m₂` diferirán en `|D|-d` puntos. Esto es importante porque queremos que la diferencia entre una declaración correcta y una incorrecta sea grande, de modo que sea fácil de encontrar.

Esto conduce a un buen muestreo, lo que ayuda a la sucintez, sólo necesitamos muestrear unos pocos valores para estar seguros de que la probabilidad de error es lo suficientemente baja como para ser insignificante.

* Disponer de pruebas eficaces de lote cero mantiene la sucintez.

Tener la capacidad de realizar pruebas de lote cero eficaces es fundamental. Esto nos permite demostrar de manera conjunta que un conjunto de elementos cumple con una determinada propiedad, en lugar de tener que probar cada elemento de forma individual, esta técnica de prueba en lote nos permite lograr una mayor concisión y eficiencia en la verificación.

Imaginemos que queremos demostrar que un polinomio de grado grande `P(x) (grado ~ 10 millones)` evalúa a `0` en los puntos `1...1 millón`, pero queremos hacerlo con una sola consulta.

Imaginemos que nuestra afirmación es que `P` desaparece en estos puntos. Si el verifier sólo utiliza el muestreo, el prover podría hacer trampas fácilmente proporcionando un punto que se evalúe como `0`, pero los otros `999.999` podrían ser distintos de `0`.

## Resolviendo el problema

Consideremos un conjunto `S = 1...10⁶`

Definir `V` como el polinomio que se anula en estos puntos, es decir: `(x - 1)(x - 2)(x - 3)...` el grado de `V = tamaño de S` y esto es beneficioso porque:

1. `P(x) = P'(x) • V(x)`
2. `Grado de P = Grado de P' - Tamaño de S.`

La introducción de `V(x)` nos permite verificar en todo el dominio.

* Estos polinomios tienen una propiedad **"multiplicadora"**. Podemos **"envolver"** una restricción alrededor de un polinomio.

Por ejemplo, si tenemos la restricción **C**, que indica que nuestra evaluación siempre será 0 o 1, podríamos expresarla como `C(x) = x • (x - 1)`. Esto se podría interpretar como restringir una salida para que sea un booleano, lo cual es útil en términos de integridad computacional.

En lugar de tener `x` como un simple punto, podríamos considerar la evaluación de un  de un polinomio `P₁(x)` en un punto específico, es decir, `C(P₁(x)) = P₁(x)•(P₁(x)-1)`

Los grados de los polinomios resultantes de la multiplicación son aditivos, por lo que el grado de `C(x) = 2 • grado de P₁(x)`

Podemos afirmar que si `P₁(x)` cumple con esta restricción para nuestro conjunto `S`, entonces, como mencionamos anteriormente, existe un polinomio `P'(x)` tal que:

* `C(P₁(x)) = P'(x) • V(x)`

Si `P₁(x)` no cumpliera con la restricción (por ejemplo, si para un valor de `x, P₁(x) = 93`), entonces no podríamos encontrar esos polinomios, la igualdad no se cumpliría y habría un residuo en la ecuación anterior.