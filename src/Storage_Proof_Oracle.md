# Storage Proof Vs Oracle
Las cadenas de bloques están diseñadas para no generar confianza, lo que significa que no pueden acceder intrínsecamente a datos fuera de la cadena. Esta limitación afecta a la capacidad de los contratos inteligentes para tomar decisiones basadas en eventos del mundo real o en información histórica de la cadena de bloques. Como solución, se introdujeron los oráculos para proporcionar a los contratos inteligentes datos fuera de la cadena o resultados de cálculos fuera de la cadena que consumen muchos recursos.

Los oráculos suelen requerir que un tercero, como una institución o una red descentralizada de operadores de nodos, envíe datos a la cadena. Aunque esto introduce un nivel de confianza, varios equipos, como Pragma, están trabajando para minimizar este requisito de confianza.

Chainlink es un conocido oráculo de blockchain que proporciona datos del mundo real, servicios de cálculo fuera de la cadena y servicios entre cadenas. Dado que los contratos inteligentes dependen actualmente de los oráculos para obtener datos del mundo real, los oráculos se han convertido en una parte crucial del ecosistema blockchain.

## ¿Pueden los oráculos ser sustituidos o mejorados por Storage Proof?

En algunos casos, las Storage Proof pueden sustituir a los oráculos. Algunos datos proporcionados por los oráculos ya están disponibles en la cadena, y una prueba de almacenamiento puede eliminar la necesidad de confiar en un tercero, permitiendo que los contratos inteligentes se basen por completo en la seguridad de los compromisos criptográficos. Sin embargo, en otros casos en los que las Storage Proof  no pueden sustituir completamente a los oráculos, pueden mejorarlos con una funcionalidad adicional:

* Las Storage Proof permiten realizar cálculos sobre datos de diferentes fuentes y exportar los resultados a otras cadenas, haciendo posible que los oráculos transmitan información a través de múltiples cadenas.
* Las Storage Proof pueden facilitar una validación rentable en las cadenas de destino, ya que la cadena de origen preferida suele tener un cálculo barato.
* Líderes en investigación, como Herodotus, permiten el acceso a datos entre dominios a través de cadenas Ethereum utilizando Storage Proof y matemáticas ZK. Pragma planea asociarse con Herodotus para soportar oráculos entre cadenas en un futuro próximo.
* Las Storage Proof pueden unificar el estado de múltiples rollups e incluso permitir lecturas síncronas entre capas Ethereum.
* La recuperación fiable de datos históricos de la cadena es otra mejora posible gracias a las Storage Proof . Las cadenas de bloques con estado, como Ethereum y Starknet, preservan criptográficamente su estado a través de estructuras de datos especializadas, lo que permite probar la inclusión de datos. Esto permite a los contratos inteligentes acceder a información que se remonta al bloque de génesis.

Pragma está explorando el desarrollo de un oráculo L3 en Starknet, que podría permitir a otras cadenas extraer y verificar datos utilizando Storage Proof. Los beneficios de tener un oráculo L3 en una red computacionalmente barata como Starknet incluyen:

* Consenso más rápido en bloques debido a la cadena L3 altamente personalizable, reduciendo significativamente la latencia de datos para el oráculo.
* Transferencia asíncrona de datos de baja latencia a otras cadenas al alcanzar el consenso en la cadena de origen, en combinación con Storage Proof .
* Mayor confianza en los datos mediante un sistema incorporado para penalizar a los proveedores de datos deshonestos. Los proveedores de datos en la L3 podrían poner en juego sus activos como garantía de la exactitud de los datos. Como toda la red L3 debe alcanzar un consenso antes de que otras cadenas puedan utilizar los datos, los datos del oráculo pueden considerarse garantizados por la apuesta de los validadores en L3.

La creciente adopción de soluciones L2 de Ethereum, como Starknet, Optimism y Arbitrum, ha permitido vislumbrar el futuro del sector. Sin embargo, un reto clave que impide un mayor crecimiento es la implementación de un sistema descentralizado de mensajería entre cadenas, las Storage Proof tienen un enorme potencial para resolver este problema.

En algunos casos, las Storage Proof pueden sustituir o mejorar los oráculos, facilitando una comunicación entre cadenas más eficiente y el acceso a datos históricos. Al reducir la dependencia de la confianza en terceros, las Storage Proof  pueden reforzar significativamente la seguridad y la eficiencia de las aplicaciones de blockchain.

A medida que el panorama de las cadenas de bloques siga evolucionando, podemos anticipar nuevos desarrollos e innovaciones en Storage Proof, oráculos y comunicación entre cadenas. Aprovechando estas tecnologías, el ecosistema blockchain puede mantener su crecimiento y ofrecer más valor tanto a los usuarios como a los desarrolladores.