# Secuenciadores
Los secuenciadores desempeñan un papel crucial en las soluciones blockchain y de Capa 2, ya que son responsables de gestionar el orden y la ejecución de las transacciones. En Starknet, los secuenciadores garantizan que las transacciones se ejecuten en un orden específico para prevenir el doble gasto y mantener la consistencia del estado de la red.

Los secuenciadores reciben transacciones, las procesan según reglas predefinidas y producen una serie de acciones u cambios de estado ordenados. Estas acciones se agrupan en bloques y se incluyen en la cadena de bloques.

Los secuenciadores desempeñan un papel vital en el rendimiento y la seguridad de Starknet al ejecutar transacciones y aplicar cambios de estado según las reglas y requisitos del protocolo.

El secuenciador de Starknet es especialmente relevante debido al uso de pruebas de conocimiento cero (ZKPs, por sus siglas en inglés). El correcto funcionamiento del secuenciador garantiza que las transacciones se ejecuten de manera compatible con la generación de ZKPs, lo que contribuye a la escalabilidad y seguridad general de Starknet. Los usuarios interactúan con los secuenciadores al enviar transacciones a Starknet, siendo este el primer paso hacia el escalado de STARK. Una vez que un secuenciador ensambla un bloque, el protocolo de consenso lo aprueba y los probadores generan una prueba para la Capa 1 (L1).

En Ethereum, los mineros ordenan y ejecutan las transacciones, mientras que los secuenciadores cumplen un propósito similar en Starknet. Los secuenciadores procesan las transacciones, las agregan y producen bloques, lo que los convierte en una pieza fundamental de la infraestructura del ecosistema de Starknet.

A medida que Starknet evoluciona, es crucial mejorar el rendimiento de los secuenciadores. Aquí es donde se vuelve fundamental la transición a secuenciadores basados en Rust. Al reescribir los componentes principales del secuenciador en Rust, la red puede lograr un mejor rendimiento, mayor capacidad y mayor resistencia.

Algunos ejemplos de implementaciones de secuenciadores incluyen [Starknet Tendermint Sequencer de LambdaClass](https://github.com/lambdaclass/starknet_tendermint_sequencer) y [Madara](https://github.com/keep-starknet-strange/madara), un secuenciador de Starknet impulsado por Rust utilizando Substrate.