# Arquitectura Starknet y Cairo
Starknet es una solución escalabilidad de de capa 2 para ETH que ofrece transacciones rápidas, seguras y de bajo costo. Funciona como un Validity Rollup (confundidos o mal nombrados a veces como ZK Rollup) que utiliza sistemas criptográficos llamados STARKs para reducir los costos de computación.

Starknet introduce una innovadora solución de Capa 2 para ETH, que aprovecha la tecnología de STARKs para revolucionar la escalabilidad y seguridad. En este documento ofreceremos información sobre la estructura de Starknet y Cairo, en los primeros capítulos daremos una visión técnica detallada de la arquitectura de la red Starknet y sus componentes clave `Sequencers`, `Provers` y `Nodes`. Estos actores trabajan en armonía, impulsando el procesamiento eficiente de la red y asegurando la integridad de las transacciones. Aunque Starknet se encamina hacia la descentralización total, actualmente se enfoca en el desarrollo para alcanzar este objetivo final. 

## Características Generales de Starknet
Veamos algunas caráteristicas básicas antes de pasar a componente y su arquitectura.

* **Bajos costos de transacción:** Los costos de transacción en Starknet son significativamente inferiores a los de Ethereum. Con próximas mejoras como Volition (disponibilidad de datos fuera de la cadena) y la implementación de EIP 4844 en L1, se espera que estos costos disminuyan aún más.
* **Plataforma amigable para desarrolladores:** Starknet proporciona un entorno que empodera a los desarrolladores para construir aplicaciones descentralizadas utilizando STARKs y el lenguaje de programación Cairo.
* **Alto rendimiento y baja latencia:** Las futuras versiones de Starknet tienen como objetivo aumentar el rendimiento de la red, reducir la latencia de las transacciones y disminuir los costos de las mismas.
* **La Filosofía de Starknet:** La filosofía de Starknet se centra en ser amigable para los desarrolladores. La red está diseñada con un claro enfoque en proporcionar a los desarrolladores una plataforma robusta, segura y poderosa para construir el futuro de la infraestructura y las aplicaciones descentralizadas.
* **Rendimiento:** Starknet ofrece mayor rendimiento, menor latencia y costos de transacción reducidos, facilitando así la creación de aplicaciones intensivas en cómputo.
* **Cairo:** El lenguaje de programación central de Starknet, Cairo, se actualiza constantemente y se mejora para brindar a los desarrolladores las mejores herramientas para aprovechar las pruebas de validez y la tecnología zk-STARKs.
* **Enfoque en la comunidad:** Starknet mantiene canales activos de comunicación y retroalimentación con la comunidad de desarrolladores a través de plataformas como Telegram y Discord.
* **Creatividad:** Starknet tiene como objetivo eliminar limitaciones y empoderar a los desarrolladores para construir el futuro de las aplicaciones descentralizadas. Permite crear cosas que nunca antes se pudieron construir debido a las limitaciones de la tecnología subyacente.
* **Herramientas:** Starknet se compromete a proporcionar una amplia gama de herramientas de desarrollo, incluyendo SDKs para diversos lenguajes, un marco de pruebas e implementación inspirado en Foundry (Protostar) y administradores de paquetes (Scarb).

En la próxima sección, nos sumergiremos en la arquitectura de Starknet y sus componentes fundamentales para comprender cómo construir aplicaciones web3 escalables. Te proporcionaremos un conocimiento profundo de los elementos clave de Starknet, lo que te permitirá desarrollar e implementar dApps de manera eficiente. Comencemos con una breve descripción de los componentes fundamentales que desempeñarán un papel crucial en el funcionamiento de la red y asegurarán que el ciclo de las transacciones sea escalable, rápido y económico.

## Sequencers:
Los Secuenciadores (Sequencers) son componentes esenciales de la red Starknet y juegan un papel central al actuar como puntos de entrada para las transacciones. Son comparables a los validadores en Ethereum, y los ZK Rollups tienen la capacidad única de delegar ciertas tareas de la red, como la agregación y el procesamiento de transacciones, a entidades especializadas. Sin embargo, este proceso demanda recursos significativos debido a los altos requisitos de capacidad y continuidad.

En el ecosistema de Starknet y otras plataformas con ZK Rollups, se observa un paralelo similar. Estas redes externalizan el procesamiento de transacciones a estas entidades especializadas, denominadas `Sequencers`, quienes luego verifican su trabajo. La delegación de tareas a los Sequencers es clave para que los ZK Rollups puedan manejar una gran cantidad de transacciones sin poner en riesgo la seguridad de la red subyacente, y así los Sequencers desempeñan un papel esencial para lograr una mayor escalabilidad en Ethereum.

A diferencia de los mineros, cuya función es brindar seguridad en otras redes, los Sequencers no aportan seguridad, sino que ofrecen capacidad de transacción. Su labor consiste en agrupar múltiples transacciones en un solo batch, procesarlas y generar un bloque. Este bloque será luego verificado por el Verificador, al cual se le proporcionará una zk Proof que garantiza la **`Validez`** o **`Integridad`** de los datos, conocida como `Validity Proof`, y más concretamente un `STARK` específico de Starknet. El Prover es el encargado de generar este STARK y se asegura de que todos los datos de las transacciones sean correctos. Posteriormente, el Sequencer enviará todo a la red de Capa 1 como un `rollup`, una prueba única y compacta para que el Verificador compruebe que los datos son correctos y actualice el nuevo estado de la red.

Los Sequencers siguen un método sistemático para el procesamiento de transacciones:

1. **Agregación:** Recopilan transacciones de los usuarios.
2. **Procesamiento:** Los Sequencers procesan estas transacciones de acuerdo con las reglas definidas por la red.
3. **Agrupación:** Las transacciones se agrupan en batchs o bloques para mayor eficiencia.
4. **Producción de Bloques:** Los Sequencers producen bloques que contienen lotes de transacciones procesadas.

Los Sequencers deben ser confiables y estar altamente disponibles, ya que su función es fundamental para el buen funcionamiento de la red. Necesitan máquinas potentes y bien conectadas para desempeñar su papel de manera efectiva, ya que deben procesar transacciones de manera rápida y continua.

La hoja de ruta actual de Starknet incluye la descentralización del rol de secuenciador. Este cambio hacia la descentralización permitirá que más participantes se conviertan en Sequencers, contribuyendo a la robustez y seguridad de la red.

## Provers:
En Starknet, el SHARP (Shared Prover) desempeña un papel esencial al realizar múltiples tareas, incluida la generación de la Validity Proof. Detallaremos estas diversas funciones en capítulos posteriores para comprender su importancia. Podemos entender al Prover como un componente que actúa en la segunda línea de verificación del sistema, y una de sus tareas principales es validar el trabajo de los Sequencers, especialmente cuando estos reciben el bloque producido por el Sequencers. Además, los Provers también tienen la responsabilidad de generar pruebas que demuestren que todos estos procesos se llevaron a cabo de manera correcta.

Los Provers necesitan incluso más potencia computacional que los Sequencers, ya que deben calcular y generar pruebas, un proceso que es computacionalmente pesado. Sin embargo, el trabajo de los Provers se puede dividir en varias partes, lo que permite la paralelización y la generación eficiente de pruebas. El proceso de generación de pruebas es asincrónico, lo que significa que no es necesario que ocurra de inmediato o en tiempo real. Esta flexibilidad permite distribuir la carga de trabajo entre varios Provers, cada uno trabajando en un bloque diferente, lo que facilita la paralelización y una generación más eficiente de pruebas.

El diseño de Starknet se basa en dos tipos de actores: los Sequencers y los Provers, que trabajan en conjunto para garantizar un procesamiento eficiente y una verificación segura de las transacciones.

En cuanto a las funciones de un Prover, podemos destacar:

1. **Recepción de Bloques:** Los Provers obtienen bloques de transacciones procesadas de los Sequencers.
2. **Procesamiento:** Los Provers vuelven a procesar estos bloques para asegurarse de que todas las transacciones dentro del bloque se hayan manejado correctamente.
3. **Generación de Pruebas:** Después del procesamiento, los Provers generan una Validity Proof que demuestra el correcto procesamiento de las transacciones.
4. **Envío de Prueba a Ethereum:** Finalmente, la Validity Proof se envía a la red de Ethereum para su validación. Si la Validity Proof es correcta, la red Ethereum acepta el bloque de transacciones.

## Nodos:
Cuando se trata de definir qué hacen los nodos en Bitcoin o Ethereum, a menudo se interpreta erróneamente su papel como mantener un registro de cada transacción dentro de la red. Sin embargo, esto no es del todo preciso.

Los nodos actúan como auditores de la red, manteniendo el estado de la red, como cuánto Bitcoin posee cada participante o el estado actual de un contrato inteligente específico. Logran esto procesando transacciones y conservando un registro de todas las transacciones, pero eso es un medio para un fin, no el fin en sí mismo.

En el caso de Validity Rollup, específicamente dentro de Starknet, este concepto se invierte en cierta medida. Los nodos no necesariamente tienen que procesar todas las transacciones para obtener el estado. A diferencia de Ethereum o Bitcoin, los nodos de Starknet no están obligados a procesar cada transacción para mantener el estado de la red.

Existen dos formas principales de acceder a los datos del estado de la red:
- A través de una puerta de enlace de API.
- Mediante el protocolo RPC para comunicarse con un nodo.

Operar su propio nodo suele ser más rápido que usar una arquitectura compartida, como la puerta de enlace. A medida que avanza el tiempo, Starknet planea descontinuar las API y reemplazarlas por un estándar JSON RPC, lo que hará que operar su propio nodo sea aún más beneficioso.

Vale la pena señalar que alentar a más personas a ejecutar nodos aumenta la resistencia de la red y evita la sobrecarga del servidor, un problema que ha afectado a otras redes de Capa 2.

Actualmente, existen principalmente tres métodos principales para que un nodo lleve un registro del estado de la red: 

1. **Reproducción de Transacciones Antiguas:** Al igual que en Ethereum o Bitcoin, un nodo puede tomar todas las transacciones y volver a ejecutarlas. Aunque este enfoque es preciso, no es escalable a menos que se tenga una máquina potente capaz de manejar la carga. Si se pueden volver a reproducir todas las transacciones, el nodo puede convertirse en un Sequencer, como puede ser el caso del nuevo enfoque adaptado a Madara con Substrate, actuando como un Sequencer, Full Node o mucho más como veremos en su momento.
2. **Confiar en el Consenso de Capa 2:** Los nodos pueden confiar en que los Secuencer ejecutan la red correctamente. Cuando el Secuencer actualiza el estado y agrega un nuevo bloque, los nodos aceptan la actualización como precisa.
3. **Verificación de la Validación de Pruebas en L1:** Los nodos pueden monitorear el estado de la red observando L1 y asegurándose de que cada vez que se envía una prueba, reciben el estado actualizado. De esta manera, no tienen que confiar en nadie y solo necesitan realizar un seguimiento de la última transacción válida para Starknet.

Podemos encontrarnos una variedad de tipos de nodos, cada uno desempeñando un papel esencial en el funcionamiento y cada tipo de configuración de nodo presenta sus propios desafíos y oportunidades, ya que vienen acompañados de requisitos de hardware y suposiciones de confianza únicas.

A medida que nos adentramos en este universo descentralizado, es crucial entender cómo estos nodos interactúan y cómo contribuyen a la eficiencia y seguridad de Starknet. Desde aquellos que reproducen transacciones con potencia de procesamiento masiva, hasta los que confían en el consenso de Capa 2 con menor carga computacional, y aquellos que verifican la validación de pruebas en L1 con una huella más liviana, cada nodo tiene su lugar y su relevancia en esta red en constante evolución.

### Nodos que Reproducen Transacciones:
Los nodos que reproducen transacciones requieren máquinas potentes para rastrear y ejecutar todas las transacciones. Estos nodos no tienen suposiciones de confianza, únicamente confían en las transacciones que ejecutan, garantizando que el estado en cualquier momento sea válido.

### Nodos que Confian en el Consenso de Capa 2:
Los nodos que confían en el consenso de Capa 2 representan una opción de menor exigencia en cuanto a potencia computacional. Aunque necesitan un almacenamiento adecuado para mantener el estado, su carga de procesamiento de transacciones es más liviana, dado que se basan en una suposición de confianza. Inicialmente, Starknet estuvo centrado en un solo secuenciador, pero ha evolucionado hacia una red más descentralizada con la incorporación de componentes como Madara y Secuencers de Rust mejorados por Lambda, entre otros, los cuales serán detallados en la sección de Sequencers.

En este contexto, estos nodos depositan su confianza en que Starkware no interferirá con la red. Sin embargo, a medida que se implemente un mecanismo de consenso y selección de líderes entre los Sequencers, el nivel de confianza se modificará. En ese futuro escenario, los nodos solo necesitarán confiar en que un Sequencer que ha comprometido su participación para producir un bloque no estará dispuesto a perderla.

### Nodos que Verifican la Validación de Pruebas en L1:
Los nodos que actualizan su estado basándose únicamente en la validación de pruebas en L1 requieren menos hardware y comparten los mismos requisitos que un nodo de Ethereum. Con la futura existencia de nodos ligeros de Ethereum, mantener un nodo de este tipo podría ser tan sencillo como usar un teléfono inteligente. No obstante, existe un compromiso a considerar `la latencia`. Las pruebas no se envían a Ethereum en cada bloque de manera constante, sino de forma intermitente, lo que provoca actualizaciones de estado retrasadas.

Para aumentar la frecuencia de las pruebas, incluso si no se envían a Ethereum de inmediato, se espera que un avance en el futuro permita que estos nodos reduzcan significativamente su latencia. Sin embargo, es importante tener en cuenta que este desarrollo aún está lejos en la hoja de ruta de Starknet