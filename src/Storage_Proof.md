# Herodotus - Storage Proof
En el mundo de los sistemas descentralizados y la tecnología blockchain, garantizar la precisión y autenticidad de los datos es de suma importancia. A medida que el ecosistema evoluciona, se hace cada vez más necesario compartir información a través de diferentes cadenas, lo que lleva al desarrollo de soluciones innovadoras para verificar la integridad de los datos sin sacrificar la seguridad o la eficiencia. Una de esas soluciones es el uso de Storage Proof .

Las Storage Proof  ofrecen un método criptográfico para rastrear y compartir información de blockchain a través de cadenas, similar a los oráculos. Sin embargo, la diferencia clave radica en el modelo de confianza.

Las Storage Proof  proporcionan inherentemente una prueba de autenticidad sin depender de la confianza de terceros. En algunas situaciones, incluso pueden reemplazar o complementar los oráculos, allanando el camino para nuevos casos de uso y aplicaciones en el ecosistema blockchain.

Imagina que tienes un libro gigante lleno de información y quieres demostrar que un dato concreto está en ese libro, en lugar de pedir a alguien que revise todo el libro para encontrar la información, se utiliza un sistema inteligente (en nuestro caso, la criptografía) para crear una pequeña prueba que pueda demostrar fácilmente la presencia de la información en el libro. Esta prueba es lo que llamamos una Storage Proof.

En el contexto de las cadenas de bloques, estos libros gigantes son las bases de datos que almacenan todas las transacciones y datos de la red. Las Storage Proof permiten crear una prueba pequeña y verificable de que ciertos datos existen dentro del estado del blockchain en un momento determinado. Para ello se utilizan técnicas criptográficas incorporadas al propio almacenamiento.

Las cadenas de bloques utilizan varias estructuras de datos, como los árboles Merkle, los árboles Merkle Patricia y los árboles Verkle, para comprometer criptográficamente sus datos. Utilizando estas estructuras de datos, se pueden generar Storage Proof  para demostrar que una información específica forma parte de un estado determinado. Sin embargo, cuando se utilizan solas, estas pruebas pueden llegar a ser bastante grandes, lo que las hace poco prácticas para la verificación en cadena. Para superar este problema, las Storage Proof  suelen combinarse con técnicas criptográficas avanzadas, como STARK o SNARK, para crear pruebas más pequeñas y eficientes que puedan verificarse en cualquier dominio sin confiar en terceros. En su lugar, la seguridad y la confianza proceden de la propia blockchain subyacente.

Las Storage Proof  le permiten abrir compromisos criptográficos de estado. Se pueden optimizar al unirlos con S [ N / T ] ARKS. . Estas pruebas de validez prueban que existía un estado en particular y que era válido en un bloque en particular en el pasado.

Fundamentalmente, las cadenas de bloques son bases de datos que contienen datos comprometidos criptográficamente utilizando (árboles Merkle, árboles Merkle Patricia, árboles Verkle, etc. ). Como todos los datos están comprometidos, podemos demostrar que cierta información está encapsulada en un estado dado. Sin embargo, con esquemas de compromiso simples, el tamaño de esta prueba se vuelve más prominente a medida que el tamaño de los datos que incluye se hace más grande. Verificar tales pruebas en cadena se vuelve demasiado costoso para ser práctico.

Las Storage Proof , por otro lado, cuando se usan junto con `STARK` o `SNARK`, pueden ser relativamente pequeñas y le permiten verificar un estado específico, en un momento específico y en cualquier dominio,  `sin confiar en un tercero`. En su lugar, confían en la seguridad de la cadena subyacente.

¿Por qué es esto importante? Ethereum hoy no es la cadena monolítica simple (L1) que era hace varios años. Con el advenimiento de las soluciones L2, los datos ahora se distribuyen en múltiples cadenas.

Ya no se pueden hacer suposiciones sincrónicas sobre el estado de la cadena. Muchas soluciones para compartir datos ahora están en vivo, como los sistemas de mensajería `L1 -> L2`, puentes entre cadenas y oráculos. Pero el problema con estas soluciones actuales es que incluyen la confianza en un tercero, como los relevistas, los firmantes multisig y los comités. Las Storage Proof  nos permiten validar el estado de una cadena de bloques en cualquier momento utilizando compromisos criptográficos sin asumir la confianza de un tercero.

