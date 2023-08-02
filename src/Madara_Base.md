# Madara - Bases de su arquitectura
Madara es mucho más que un secuenciador, ha sido diseñado por el equipo de exploración de Starkware, los poderosos [Keep Starknet Strange](https://github.com/keep-starknet-strange). Su enfoque modular, basado en Substrate (SDK) con el poder de Rust, lo convierte en un componente principal para escalar Starknet, ETH y darle al usuario y desarrollador la facilidad de adaptar sus dapps, montando capas 3, 4 o 5 modificables según su proyecto. Podrá utilizar y desplegar una pila de componentes de forma rápida y segura gracias a las STARKs y Cairo, usando la Cairo VM y el Blockifier para ejecutar programas o contratos de Cairo en Starknet.

Defniamos en es capitulo sobre las bases de Madara la definicon de algunos conceptos que hemos nombrado y son importantes para este u otra arquitecutra:

* **Substrate:** es un Kit de desarrollo de software (SDK) que le permite construir cadenas de bloques específicas de la aplicación que pueden ejecutarse como servicios independientes o en paralelo con otras cadenas.

* **Blockifier:** es una implementación de Rust para el componente de ejecución de transacciones en el secuenciador Starknet, a cargo de crear diferencias de estado “state distaff”  y bloques.
    * Agregue la capacidad de ejecutar un bloque y generar un estado diff.
    * Integre con el secuenciador StarkNet existente reemplazando su componente actual de bloqueo de transacciones, que está escrito en Python.
    * Implemente la concurrencia optimista de la ejecución de transacciones.
    * Extienda el Blockifier en un secuenciador completo de StarkNet, escrito en Rust, reemplazando el que está actualmente en uso.

* **Palet:** El componente central de Madara es el starknet palet. Proporciona una capa de compatibilidad Starknet para Substrate. El código existente de El Cairo se puede ejecutar sin problemas gracias a esto. Esta paleta, además de tener un módulo RPC, permite la emulación de bloques Starknet, valida las transacciones codificadas por Starknet y permite implementar un Starknet DApp existente en Madara sin ningún cambio.

* **Paridad de bloques:** Wrapper block es una estrategia en Substrate para permitirle procesar bloques que no fueron diseñados originalmente con Substrate en mente, este método fue utilizado por primera vez por Parity en la frontera, la capa de compatibilidad EVM para Substrate.

* **Stack de Madara:** El Stack de Madara consta de tres componentes clave: Ejecución, Asentamiento y Secuenciación.

    * **Ejecución:** Define cómo se ejecutan los bloques y se producen las diferencias de estado. Permite cambiar entre Blockifier (por Starkware) y starknet_in_rust (por LambdaClass) para una mayor optimización con el tiempo.
   
    * **Settlement:** Permite construir el estado de la cadena Madara solo mirando su capa de asentamiento. No hace suposiciones sobre la capa de asentamiento elegida y permite establecer la finalidad Hard y Soft según el contexto.
    
    * **Sequencing:** Realizada por Madara, se puede modificar para satisfacer diferentes necesidades. Puede ser un FCFS, PGA simple o esquemas más complejos como Narwhall & Bullshark o HotStuff, que se basa en el protocolo PBFT.

    * **Gobernanza:** La gobernanza en Madara se basa principalmente en la SnapShot X, un sistema totalmente en cadena que utiliza pruebas de almacenamiento. Además, se están explorando otros mecanismos de gobernanza, como el sustrato nativo palet de gobernanza.

Con estos puntos clave, hemos querido reforzar los conceptos básicos de Madara y evitar enfocarlo únicamente como un secuenciador. Su enfoque modular, adaptado a Starknet y centrado en el escalado fractal, permitirá ver fusiones de componentes que superarán lo imaginado. Además, muchos desarrollos, como el Starknet Stack de Lambda, podrán ser optimizados o, al menos, facilitar el cambio entre ambas cajas de ejecución (Blockifier y Starknet_in_Rust) de manera muy eficiente.

Con este enfoque, Madara en Substrate nos brinda la posibilidad de tener nuevas cadenas subyacentes con diversas formas de almacenar datos y diferentes protocolos de consenso, como Celestia. También permite implementar diversas arquitecturas, como Kakarot, un zkEVM que interpreta el lenguaje de Solidity y lo ejecuta en Cairo. Esto proporciona una mayor compatibilidad y la opción de optimizarlo como un tipo 1 zkEVM, o incluso motores de juegos completos como Dojo, que ofrecen una creación sencilla, flexible y adaptada a sus necesidades. 

Con todas estas capacidades, Madara va mucho más allá de ser solo un secuenciador, como mencionamos al principio.