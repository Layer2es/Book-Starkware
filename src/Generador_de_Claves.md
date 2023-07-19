# Key generator
Tenemos que entender cómo el generador de claves [**(Key generator)**](https://en.wikipedia.org/wiki/Key_generator) genera el Keypair, para lograrlo, es necesario trabajar con valores pseudoaleatorios que se utilizan en la generación de la private key. Un Key generator se puede implementar en un sistema con el propósito de generar y autenticar claves.

Key generator puede implementarse en cualquier sistema criptográfico que utilice la curva elíptica, como es el caso de `secp256k1` (una curva optimizada basada en las propiedades matemáticas de las curvas elípticas para proporcionar un esquema de firma digital seguro y eficiente), como Bitcoin y Ethereum.

Este generador de claves garantiza que, con alta probabilidad, las claves privadas generadas sean únicas y seguras, lo que a su vez respalda la integridad y autenticidad de las transacciones realizadas en la red.

## Generadores de números pseudoaleatorios
Para garantizar la seguridad usando la pseudoaleatoriedad estadística de un **PRNG -** [**Pseudorandom number generator**](https://en.wikipedia.org/wiki/Pseudorandom_number_generator), es crucial contar con una semilla inicial. Si la semilla es fácilmente predecible, generará valores predecibles de números y todo el proceso será inseguro.

Para lograr una inicialización segura del generador pseudoaleatorio, es necesario recolectar [**Entropía**](https://en.wikipedia.org/wiki/Entropy_(computing)), que representa la aleatoriedad necesaria en el proceso.

## Entropía
La entropía o aleatoriedad impredecible en computación, generalmente se mide en bits. Tenemos varios ejemplos para entender el concepto y grado de aleatoriedad. Si mueve el mouse de su computadora, generará algunos eventos difíciles de predecir, como la ubicación de inicio y la ubicación final del cursor del mouse.

> Si suponemos que el mouse ha cambiado su posición en el rango de `[ 0 ... 255 píxeles ]`, la entropía recolectada de este movimiento del mouse debe ser de aproximadamente **8 bits**, porque `2⁸ = 255`

> Si se le pide al usuario que piense en un número en el rango `[ 0 ... 1000 ]`, este número tendrá alrededor de **9-10 bits** de entropía porque, `2¹⁰ = 1024`

Para recolectar 256 bits de entropía, es decir, para generar de forma segura un número entero de 256 bits, deberá tener en cuenta una secuencia de varios eventos similares (como movimientos del mouse e interracidades del teclado del usuario).

Aquí la importancia de dónde y cómo hemos generado nuestras claves privadas y públicas y las posibles vulnerabilidades en algunos malos usos.