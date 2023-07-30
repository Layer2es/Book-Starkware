# Papyrus

Papyrus es una implementación en Rust de un nodo completo de Starknet. Proporcionará las bases para el nuevo Sequencer de Starknet, que mejorará drásticamente el rendimiento de Starknet. Papyrus ayudará a mejorar el rendimiento y la descentralización de Starknet, que son las principales prioridades de desarrollo.

El nodo completo de Papyrus realizará un seguimiento del estado de Starknet a medida que evoluciona con el tiempo y permitirá a los usuarios y desarrolladores consultar este estado a través de Starknet's JSON-RPC.

Papyrus proporcionará al Sequencer de Starknet una capa de almacenamiento eficiente, lo que mejorará el rendimiento. Esto significa que el secuenciador mantendrá una base de datos local en lugar de una base de datos en la nube, y también almacenará un almacenamiento plano de clave/valor, lo que interactuará directamente con el estado.

Papyrus se une a otros nodos completos de Starknet, Pathfinder y Juno, para fortalecer la descentralización y redundancia. Al ser de código abierto, Papyrus contribuye a la variedad de implementaciones de clientes, lo que es crucial para una red descentralizada.

Actualmente, Papyrus permite sincronizarse con el estado de Starknet y acceder a toda su historia. Aunque el soporte JSON-RPC está parcialmente implementado, el equipo de Papyrus trabajará para alcanzar la compatibilidad completa y contribuirá a formar la base de la capa P2P de Starknet, lo que permitirá una mayor descentralización. El objetivo final es que diferentes nodos puedan comunicarse y sincronizarse a través de esta capa P2P, mejorando significativamente los tiempos de sincronización.

En resumen, Papyrus es el tercer nodo completo en unirse al ecosistema de Starknet. Es de código abierto bajo la licencia Apache 2.0 y será una parte crucial de la infraestructura de Starknet descentralizado.