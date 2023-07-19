# El algoritmo de Shor teórico y su impacto en ECDSA

El [**algoritmo de Shor**](https://en.wikipedia.org/wiki/Shor's_algorithm) es un algoritmo cuántico desarrollado por Peter Shor en 1994. Este algoritmo es conocido por su capacidad para factorizar grandes números enteros de manera mucho más eficiente que los algoritmos clásicos conocidos, lo que tiene implicaciones importantes para la seguridad de algunos sistemas criptográficos basados en la factorización de números enteros.

En el contexto de sistemas centralizados, como los sistemas bancarios, ECDSA se utiliza para garantizar la autenticidad de las transacciones, proteger la confidencialidad de la información y asegurar la integridad de los datos. En el ámbito de Bitcoin y Ethereum, si bien los algoritmos de búsqueda cuántica, como el algoritmo de Shor, podrían eventualmente romper la ECDSA, es importante destacar que estos algoritmos aún están en una etapa teórica.

Cada implementación de algoritmos o protocolos puede ser diversa, ya sea privada o abstracta. Nos hemos centrado en los principios básicos comunes de ECDSA, además se espera que la implementación práctica de algoritmos de búsqueda cuántica sea un desafío técnico debido a los requisitos de recursos y la necesidad de superar errores cuánticos.

Aquí tienes una descripción general de en qué consisten algunos problemas que se consideran complejos de resolver mediante la computación clásica.

## IFP
El IFP se refiere al desafío de descomponer un número entero grande en sus factores primos. En el caso de números pequeños, esto puede hacerse fácilmente mediante el uso de algoritmos como [el cribado de Eratóstenes](https://yosoytuprofe.20minutos.es/2022/11/09/que-es-la-criba-de-eratostenes-y-cual-es-su-importancia-en-las-matematicas/) o [el algoritmo de factorización de Pollard](https://en.wikipedia.org/wiki/Pollard%27s_rho_algorithm_for_logarithms).

A modo de ejemplo simplificado, supongamos que queremos factorizar el número compuesto `N = 35` utilizando el algoritmo de Shor. Después de aplicar el algoritmo, encontraríamos que los factores primos de `N` son `5 y 7`.

Sin embargo, a medida que los números crecen en tamaño, el IFP se vuelve cada vez más difícil de resolver. De hecho, la seguridad de muchos sistemas criptográficos se basa en la dificultad de factorizar números grandes en tiempo razonable, como el popular algoritmo RSA.

## DLP
Por otro lado, el DLP implica encontrar el exponente desconocido de una potencia modular dada. En términos más sencillos, se trata de resolver la ecuación `(y = gˣ mod p)` para el exponente desconocido `(x)`, donde `(g)` y `(p)` son números conocidos e `(y)` es el resultado de la operación de potenciación modular. Para valores pequeños de `(p)`, el DLP puede resolverse mediante la aplicación de métodos exhaustivos como la prueba y error.

A modo de ejemplo simplificado, sería encontrar el logaritmo discreto de `base 2` para el número `5` `módulo 11`. Esto implica encontrar el valor de `x` en la ecuación `2ˣ ≡ 5 (mod 11).`

Realizando los cálculos paso a paso:

* 2¹ ≡ 2 (mod 11)
* 2² ≡ 4 (mod 11)
* 2³ ≡ 8 (mod 11)
* 2⁴ ≡ 5 (mod 11)

Entonces, el valor de `x` que satisface la ecuación `2ˣ ≡ 5 (mod 11)` es `x = 4`.

## ECDLP
La seguridad de esquemas criptográficos basados en **ECC**, como **ECDSA**, se basa en la dificultad de resolución del problema del logaritmo discreto de curva elíptica o **ECDLP**. Las curvas elípticas son objetos matemáticos utilizados en criptografía de clave pública, y el **ECDLP** sería el problema de hallar el valor de `‘K’` en esta ecuación, `P =k⋅G`, donde `P` es un punto en la curva, `k` es el valor que debemos hallar y `G` es un punto base conocido (el generador).

Al igual que en el caso del **DLP**, el **ECDLP** se vuelve más difícil de resolver a medida que el tamaño de los números involucrados en esas expresiones matemáticas aumentan

## ECDSA
Por último llegamos a un algoritmo ampliamente utilizado y conocido como es el **ECDSA**, que se utiliza comúnmente en blockchain. La clave pública se obtiene multiplicando un punto base conocido (llamado generador) en la curva elíptica por un entero, que representa la llave privada. El desafío radica en encontrar ese valor privado a partir del punto público conocido en la curva.

La curva elíptica **secp256k1** está definida por la ecuación: `y² = x³ + ax + b` sobre `𝔽p` donde `p` es un número primo grande.

El algoritmo de Shor, en su versión completa y ejecutado en un computador cuántico lo suficientemente grande y estable, podría factorizar el número primo `p` en esta ecuación, lo que proporcionaría información sobre el orden del subgrupo cíclico relacionado con la curva.

Si se pudiera determinar el orden del subgrupo cíclico relacionado con la curva `secp256k1` utilizando el algoritmo de **Shor**, sería posible encontrar el valor privado a partir de la clave pública. Esto comprometería la seguridad de **ECDSA**, ya que la clave privada es fundamental para generar firmas digitales y autenticar transacciones. Es importante destacar que el algoritmo de Shor plantea un desafío para los sistemas criptográficos actuales basados en la factorización de números enteros o en el logaritmo discreto, como **RSA** y **ECDSA**.

No obstante, la implementación práctica de un algoritmo cuántico capaz de realizar estos cálculos, como los mencionados ejemplos, todavía se encuentra en desarrollo y no representa una amenaza inmediata para los sistemas criptográficos utilizados en la actualidad. La investigación y el desarrollo continuo en criptografía pos-cuántica son fundamentales para garantizar la seguridad en un entorno tecnológico en constante evolución.