# Polinomio para nuestra traza
También en este caso definimos un polinomio `f(x)` tal que los elementos de la traza de ejecución son evaluaciones de `f` en potencias de algún generador `g`.

Recordemos que nuestro campo finito tendrá generadores, que utilizaremos para indexar los pasos de nuestra traza. Tomando una secuencia de Fibonacci podemos crear restricciones como:

* `∀ x ∈ {1,g²,g³...g⁵⁰⁹}: f(g²x) ₋ f(gx) ₋ f(x) = 0`

Esto restringe los valores entre las filas subsiguientes. También significa que los valores g son raíces de este polinomio.

Por lo tanto, podemos utilizar el enfoque que vimos anteriormente para proporcionar el polinomio de fuga utilizando el término `(x - gⁱ)` y a partir de él creamos el polinomio de composición.

El hecho básico sobre polinomios y sus raíces es que si `p(x)` es un polinomio, entonces `p(a)=0` para algún valor específico a, si y sólo si existe un polinomio `q(x)` tal que `(x-a)q(x)=p(x)`, y `deg(p)=deg(q)+1.`

Esta expresión coincide con el polinomio de grado 2 como máximo si nuestra traza de ejecución ha sido correcta, es decir, ha obedecido a la restricción de paso que hemos definido.

Si la traza difiere de eso, entonces es poco probable que esta expresión produzca un polinomio de bajo grado.

# Composición Polinomial
El Polinomio de Composición en su traducción también conocido como Composición Polinomial (CP), se realiza para demostrar eficazmente la validez del rastro de ejecución, nos esforzamos por alcanzar los dos objetivos siguientes:

1. Componer las restricciones sobre los polinomios de la traza para hacerlas cumplir en la traza.
2. Combinar las restricciones en un único polinomio (más grande), denominado Composición Polinomial, de modo que se pueda utilizar una única prueba de grado bajo para atestiguar su grado bajo.

# Ampliando el polinomio
Como hemos visto antes, los polinomios pueden utilizarse para construir buenos códigos de corrección de errores, ya que dos polinomios de grado d, evaluados en un dominio considerablemente mayor que d, son diferentes en casi todas partes.

Observando esto, podemos extender la traza de ejecución pensando en ella como una evaluación de un polinomio en algún dominio, y evaluando este mismo polinomio en un dominio mucho mayor. Extendiendo de manera similar una traza de ejecución incorrecta, se obtiene una cadena muy diferente, lo que a su vez hace posible que el verificador distinga entre estos casos utilizando un pequeño número de consultas.

## De restricciones polinómicas al problema de las pruebas de bajo grado
En general, si nuestro cálculo implica `N` pasos, la traza de ejecución estará representada por polinomios de grado inferior a `N`

* `f(X) = c₀ + c₁X + c₂X² +⋯+ cɴ-₁Xᴺ⁻¹`

Los coeficientes `cᵢ` están en el campo `𝔽` y el límite `N` en el grado es típicamente grande, quizá del orden de unos pocos millones. A pesar de ello, estos polinomios se denominan de bajo grado.

Esto se debe a que el punto de comparación es el tamaño del campo. Por interpolación, toda función sobre `𝔽` puede representarse mediante un polinomio.

La mayoría de ellos tendrán un grado igual al tamaño total del campo, por lo que, comparado con éste, `N` es realmente bajo.

Este tipo de funciones, coherentes con un polinomio de bajo grado, también se conocen como códigos `Reed-Solomon`.

Tras la generación de la traza, el prover se compromete con ella. Recordemos que no queremos enviar los polinomios al verificador como un todo, pero necesitamos que el prover se comprometa con ellos.

En todo el sistema, los compromisos se ejecutan construyendo árboles de Merkle sobre las series de elementos de campo y enviando las raíces de Merkle al verificador.

Queremos que un verificador plantee al prover un número muy reducido de preguntas y decida si acepta o rechaza la prueba con un alto nivel de precisión garantizado. Idealmente, al verificador le gustaría pedir al prover que proporcione los valores en unos pocos lugares (aleatorios) en la traza de ejecución, y comprobar que las restricciones polinómicas se mantienen para estos lugares.

Una traza de ejecución correcta pasará naturalmente esta prueba.

Sin embargo, no es difícil construir una traza de ejecución completamente errónea (especialmente si sabíamos de antemano qué puntos se comprobarían), que viole las restricciones sólo en un punto de la traza único y, al hacerlo, llegar a un resultado completamente alejado y diferente. Identificar este fallo mediante un pequeño número de consultas aleatorias es altamente improbable.

Pero recuerda que los polinomios tienen algunas propiedades útiles aquí:

* Dos polinomios (diferentes) de grado `d` evaluados en un dominio considerablemente mayor que `d` son diferentes en casi todas partes.

Así que si tenemos un prover deshonesto, que crea un polinomio de bajo grado representando su traza (que es incorrecta en algún punto) y lo evalúa en un dominio grande, será fácil ver que este es diferente al polinomio correcto.