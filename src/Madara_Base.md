# Madara - Bases de su arquitectura
Madara es mucho más que un secuenciador, ha sido diseñado por el equipo de exploración de Starkware, los poderosos [Keep Starknet Strange](https://github.com/keep-starknet-strange). Su enfoque modular, basado en Substrate (SDK) con el poder de Rust, lo convierte en un componente principal para escalar Starknet, ETH y darle al usuario y desarrollador la facilidad de adaptar sus dapps, montando capas 3, 4 o 5 modificables según su proyecto. Podrá utilizar y desplegar una pila de componentes de forma rápida y segura gracias a las STARKs y Cairo, usando la Cairo VM y el Blockifier para ejecutar programas o contratos de Cairo en Starknet.

En este capítulo, exploraremos los cimientos de Madara, definiendo conceptos esenciales que son cruciales para comprender tanto esta arquitectura como otras similares.

* **Substrate:** Es un Kit de desarrollo de software (SDK) que le permite construir cadenas de bloques específicas de la aplicación que pueden ejecutarse como servicios independientes o en paralelo con otras cadenas.

* **Blockifier:** Es una implementación de Rust para el componente de ejecución de transacciones en el secuenciador Starknet, a cargo de crear diferencias de estado `state distaff` y bloques, su función engloba:
    * Realizar la ejecución de un bloque y generar  un state distaff.
    * Integrarse con el secuenciador Starknet actual, reemplazando su componente de bloqueo de transacciones, escrito en Python.
    * Implementar la concurrencia optimista de la ejecución de transacciones.
    * Ampliar el Blockifier para convertirlo en un secuenciador Starknet completo, escrito en Rust, sustituyendo al actual en uso.

* **Pallet:** El núcleo de Madara reside en el starknet pallet, que proporciona una capa de compatibilidad Starknet para Substrate. Esto permite una ejecución fluida del código existente de Cairo. Este pallet no solo incluye un módulo RPC, sino que también posibilita la emulación de bloques Starknet, valida las transacciones codificadas por Starknet y facilita la implementación de una Starknet DApp sin necesidad de modificaciones.

* **Paridad de bloques:** Wrapper Block es una estrategia en Substrate diseñada para procesar bloques que no fueron originariamente concebidos con Substrate en mente, este enfoque fue pionero por Parity en la capa de compatibilidad EVM para Substrate.

* **Stack de Madara:** El Stack de Madara consta de tres componentes clave: Ejecución, Asentamiento y Secuenciación.

    * **Ejecución:** Define el procedimiento para la ejecución de bloques y la creación de diferencias de estado. Permite cambiar entre Blockifier (por Starkware) y starknet_in_rust (por LambdaClass) para una mayor optimización con el tiempo.
   
    * **Settlement:** Permite construir el estado de la cadena Madara solo mirando su capa de asentamiento. No hace suposiciones sobre la capa de asentamiento elegida y permite establecer la finalidad Hard y Soft según el contexto.
    
    * **Sequencing:** Realizada por Madara, se puede modificar para satisfacer diferentes necesidades. Puede ser un FCFS, PGA simple o esquemas más complejos como Narwhall & Bullshark o HotStuff, que se basa en el protocolo PBFT.

* **Gobernanza:** La gobernanza en Madara se basa principalmente en la SnapShot X, un sistema totalmente en cadena que utiliza Storage Proof. Además, se están explorando otros mecanismos de gobernanza,  como el pallet nativo de gobernanza en Substrate.

Con estos aspectos clave, hemos buscado fortalecer los fundamentos esenciales de Madara y evitar limitarnos a considerarlo únicamente como un secuenciador. Su enfoque modular, adaptado a Starknet y centrado en el concepto de escalado fractal, abre las puertas a fusiones de componentes que trascienden las expectativas convencionales. Además, esta arquitectura posibilita optimizaciones y mejoras más efectivas en diversos desarrollos, como el impresionante Starknet Stack desarrollado por Lambda, que contribuye a la eficiencia global del sistema.

Este enfoque estratégico de Madara en Substrate no solo nos permite la creación de nuevas cadenas subyacentes, abordando diversas estrategias de almacenamiento de datos y variados protocolos de consenso, incluyendo opciones como Celestia. También nos brinda la capacidad de implementar una gama diversa de arquitecturas, como la prometedora fusión potencial con Kakarot, un zkEVM que interpreta el lenguaje de programación Solidity y lo ejecuta en el entorno Cairo. Esta colaboración inteligente proporciona una mayor flexibilidad y la opción de afinarla como un zkEVM de tipo 1. Además, Madara sienta las bases para el desarrollo de motores de juegos completos al estilo de Unity, como se demuestra claramente con el ejemplo de Dojo en el entorno de Starknet. Estas capacidades no solo permiten una creación ágil y adaptable a necesidades específicas, sino que también destaca la versatilidad de Madara más allá de su papel inicial como secuenciador, tal como mencionamos al principio.