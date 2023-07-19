# Starknet y Funciones Hash
Hemos visto la importancia de las firmas, el poder de AA y la asociación de los hash dentro del ecosistema de Starknet y StarkEx. Ahora, profundicemos en cómo se utilizan y los diferentes tipos de hash que podemos encontrar.

## Dominio y rango
Todas las salidas de las funciones de hash se mapean eventualmente a elementos en `𝔽ₚ` con `p = 2²⁵¹ + 17 ⋅ 2¹⁹² + 1` como vimos en la Stark Curve.

Las funciones hash son componentes clave en las especificaciones de Starknet, y se utilizan para mapear las salidas de los cálculos a elementos en el campo finito `𝔽ₚ`. A continuación, explicaremos las tres funciones hash utilizadas en Starknet de manera más clara:

![graph](./assets/Stark_func_hash.png)
<div align="center">
<em>Ciclo completo de una firma y validación de una trnasacción</em>
</div>

1. [**sn_keccak:**](https://docs.starknet.io/documentation/architecture_and_concepts/Hashing/hash-functions/#starknet_keccak) Esta función hash se basa en el algoritmo KECCAK, que es una familia de funciones hash criptográficas como vimos antes. Su dominio es el conjunto de cadenas de bits compuestas por ceros y unos `{0,1}*` y su rango es el campo finito `𝔽ₚ` La función toma una cadena de bits como entrada y produce una salida en el campo finito `𝔽ₚ`.
2. [**Pedersen:**](https://docs.starknet.io/documentation/architecture_and_concepts/Hashing/hash-functions/#pedersen_hash) La función hash Pedersen es una función hash computacionalmente segura que se utiliza en la construcción de criptografía de compromiso cero y otras primitivas criptográficas. Su dominio es el conjunto de pares de elementos del campo finito `𝔽²p`, donde `p` es un número primo, y su rango es el campo finito `𝔽p`. La función toma un par de elementos del campo finito `𝔽²p` como entrada y produce una salida en el campo finito `𝔽p`.
3. [**Poseidon:**](https://docs.starknet.io/documentation/architecture_and_concepts/Hashing/hash-functions/#poseidon_hash) La función hash Poseidon es una función hash criptográfica. Su dominio es un conjunto de elementos del campo finito `𝔽p`, que incluye el cero y los elementos inversos multiplicativos, y su rango también es el campo finito `𝔽p`. La función toma un conjunto de elementos del campo finito `𝔽p` como entrada y produce una salida en el campo finito `𝔽p`.

Las funciones de hash mencionadas son añadidas como [**Builtin**](https://mirror.xyz/0x7D1c14939AcEE5ca141c8beDF3474AFBf3884041/RTgQnMxeVGRCczih1pGXKy2KGFcU_xmf2NMx52wDgH0) (AIR integradas específicas de aplicaciones), que se utilizan como herramientas adicionales en el protocolo para garantizar la seguridad y la integridad de las transacciones y los datos.

Estas funciones hash desempeñan un papel fundamental en las operaciones de Starknet al garantizar la integridad y seguridad de los cálculos realizados en el sistema.