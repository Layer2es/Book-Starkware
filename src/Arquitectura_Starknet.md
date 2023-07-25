# Arquitectura Starknet y Cairo
Starknet es una solución de de capa 2 para ETH, que aprovecha la tecnología de zk-STARKs para lograr escalabilidad, privacidad y seguridad. Como solución de escalabilidad de Capa 2 para Ethereum, Starknet ofrece transacciones rápidas, seguras y de bajo costo. Funciona como un Validity Rollup (comúnmente conocido como Rollup de conocimiento cero) que utiliza sistemas criptográficos llamados STARKs para reducir los costos de computación.

## Características Generales de Starknet
Veamos algunas caráteristicas báscicas antes de pasar cada componente de su arquitectura.

* **Bajos costos de transacción:** Los costos de transacción en Starknet son significativamente inferiores a los de Ethereum. Con próximas mejoras como Volition (disponibilidad de datos fuera de la cadena) y la implementación de EIP 4844 en L1, se espera que estos costos disminuyan aún más.
* **Plataforma amigable para desarrolladores:** Starknet proporciona un entorno que empodera a los desarrolladores para construir aplicaciones descentralizadas utilizando STARKs y el lenguaje de programación Cairo.
* **Alto rendimiento y baja latencia:** Las futuras versiones de Starknet tienen como objetivo aumentar el rendimiento de la red, reducir la latencia de las transacciones y disminuir los costos de las mismas.
* **La Filosofía de Starknet:** Un Enfoque Amigable para Desarrolladores
La filosofía de Starknet se centra en ser amigable para los desarrolladores. La red está diseñada con un claro enfoque en proporcionar a los desarrolladores una plataforma robusta, segura y poderosa para construir el futuro de la infraestructura y las aplicaciones descentralizadas. Los principios fundamentales de este enfoque incluyen:
* **Rendimiento:** Starknet ofrece mayor rendimiento, menor latencia y costos de transacción reducidos, facilitando así la creación de aplicaciones intensivas en cómputo.
* **Cairo:** El lenguaje de programación central de Starknet, Cairo, se actualiza constantemente y se mejora para brindar a los desarrolladores las mejores herramientas para aprovechar las pruebas de validez y la tecnología zk-STARKs.
* **Enfoque en la comunidad:** Starknet mantiene canales activos de comunicación y retroalimentación con la comunidad de desarrolladores a través de plataformas como Telegram y Discord.
* **Creatividad:** Starknet tiene como objetivo eliminar limitaciones y empoderar a los desarrolladores para construir el futuro de las aplicaciones descentralizadas. Permite crear cosas que nunca antes se pudieron construir debido a las limitaciones de la tecnología subyacente.
* **Herramientas:** Starknet se compromete a proporcionar una amplia gama de herramientas de desarrollo, incluyendo SDKs para diversos lenguajes, un marco de pruebas e implementación inspirado en Foundry (Protostar) y administradores de paquetes (Scarb).

En este apartado exploraremos la arquitectura de Starknet y sus componentes fundamentales para comprender como es la construcción de aplicaciones web3 escalables. Te proporcionaremos un conocimiento profundo de los elementos clave de Starknet, permitiéndote desarrollar e implementar dApps de manera eficiente.

A lo largo de este documento, abordaremos los siguientes temas: (MAL)

* **Nodos de L2:** Una descripción general de los diferentes nodos de Starknet (Secuenciador, Verificador, Nodos completos e Indexador) y sus roles dentro de la red.
* **Ciclo de vida de las transacciones:** Una explicación detallada de los diferentes estados por los que pasa una transacción de capa 2, discutiendo los beneficios y riesgos de considerar un estado en particular como "finalidad".
* **Starknet OS:** Una exploración de cómo el Secuenciador valida y ejecuta transacciones, y su conexión con la AA.
* **SHARP:** Un exámen del flujo de trabajo del Verificador para generar pruebas para Starknet y Starkex utilizando la recursividad, centrándose en el flujo de trabajo en lugar de las matemáticas detrás de STARKs.
* **DA o Disponibilidad de datos:** Una discusión sobre la Disponibilidad de Datos en Starknet en diversos modos.
* **Componentes de L1:** Un análisis exhaustivo del Verificador en la cadena y el Registro de Hechos,
* **Puentes:** Una explicación de cómo funciona la comunicación entre capa 1 y capa 2, y cómo se pueden crear puentes entre redes.