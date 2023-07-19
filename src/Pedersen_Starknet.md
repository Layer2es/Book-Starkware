# Pedersen Hash Starknet
El [Pedersen hash](https://docs.starknet.io/documentation/architecture_and_concepts/Hashing/hash-functions/#pedersen_hash) es una función hash criptográfica utilizada en criptografía propuesta por Torben Pedersen en 1991.

Uno de los aspectos interesantes del [esquema de compromiso de Pedersen](https://en.wikipedia.org/wiki/Commitment_scheme) es su propiedad homomórfica, que permite realizar la adición entre dos compromisos. En otras palabras, dados dos mensajes `m₁` y `m₂`, y sus respectivas aleatoriedades `r₁` y `r₂`, el Pedersen hash permite combinarlos de manera segura.

La función Pedersen Hash utilizada en Starknet es resistente a colisiones para entradas de longitud fija, siempre y cuando la función de codificación subyacente sea inyectiva. Una función inyectiva asigna elementos distintos de su dominio a elementos distintos de su codominio, esto hace que el Pedersen hash sea resistente a ciertos tipos de ataques, como colisiones y preimágenes.

Sin embargo, es importante destacar que la implementación y el contexto en el que se utilice esta función pueden influir en su resistencia. Para obtener más información se recomienda realizar una lectura sobre [Pedersen hashes in Practice](https://research.nccgroup.com/2023/03/22/breaking-pedersen-hashes-in-practice/).

En Starknet, se utiliza la EC amigable STARK curve sobre el campo finito `𝔽ₚ` para calcular el Pedersen hash de manera eficiente y segura.

![graph](./assets/Pedersen_Starknet.png)
<div align="center">
<em></em>
</div>

* α = 1
* β = 31415926535897932384626433832795028841971693993751058209749 44592307816406665

Los parámetros `α` y `β` de la curva son importantes en términos de seguridad y eficiencia en los algoritmos utilizados en la construcción del Pedersen hash y los protocolos de ZKP o basados en STARK.

Dada una entrada `(a, b) ∈ 𝔽²p`, se divide en `alow`, `ahigh`, `blow` y `bhigh`, donde la parte `low` consiste en los **248 bits menos significativos del elemento** y la parte `high` consiste en los **4 bits más significativos del elemento.** El cálculo del Pedersen hash se define de la siguiente manera:

![graph](./assets/Pedersen_Starknet1.png)
<div align="center">
<em></em>
</div>

En esta fórmula, `[P]x` denota la coordenada `x` del punto `P`. Para calcular el hash, se realiza una combinación lineal de los puntos `P0, P1, P2 y P3`, ponderados por los valores `alow`, `ahigh`, `blow` y `bhigh`, respectivamente. Luego, se suma el punto `shift_point` y se extrae la coordenada `x` del resultado.

Los valores de las constantes `shift_point`, `P0`, `P1`, `P2` y `P3` se encuentran en el archivo [fast_pedersen_hash.py](https://github.com/starkware-libs/cairo-lang/blob/master/src/starkware/crypto/signature/fast_pedersen_hash.py). Este archivo contiene la implementación específica del algoritmo necesario para calcular el Pedersen hash.

No se trata de puntos en la EC en sí misma, sino de valores específicos que se han elegido para el cálculo del hash y tampoco están relacionadas con la EC ni con el punto generador `G`, revise minuciosamente la información oficial en caso de querer hacer pruebas sobre Stark Curve o Hash en Starknet. Estas constantes se eligen de forma independiente para el cálculo del hash y se utilizan en combinación con los valores de entrada para obtener el hash resultante.