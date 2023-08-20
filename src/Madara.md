# Madara - Exploración de su Arquitectura 🚧
En este capítulo realizaremos un análisis exhaustivo de la arquitectura de Madara, este componente fundamental desempeñará un papel vital en el ecosistema de Starknet, destacándose por su enfoque en el escalado fractal y la modularidad dentro del mundo de las blockchains. Antes de sumergirnos en las intrincadas capas de Madara, es recomendable revisar los cimientos y las definiciones clave, las cuales están detalladas en el apartado [Base Madara](/Book-Starkware/src/Madara_Base.md#madara---bases-de-su-arquitectura) de la Parte 2 del Libro de L2 sobre la Arquitectura de Starknet y Cairo.

La esencia de Madara se fusiona con la plataforma Substrate, un framewrok de innovación en la cadena de bloques que se erige como el fundamento de Madara. Las Chains montadas con Substrate se representan como una combinación de tres tecnologías fundamentales: 

- **WebAssembly:** Wasm es un formato binario de instrucciones diseñado para una máquina virtual basada en pilas. Su principal propósito es servir como un objetivo de compilación portátil para diversos lenguajes de programación, lo que facilita su implementación en aplicaciones tanto de cliente como de servidor en la web.
- **Libp2p:** Es una colección de protocolos, especificaciones y herramientas que facilitan la construcción de redes descentralizadas y resistentes a la censura en el ámbito de la web. Esta biblioteca está diseñada para brindar una capa de comunicación peer-to-peer eficiente y flexible, permitiendo que los nodos se conecten y se comuniquen de manera segura a través de una variedad de redes y protocolos subyacentes. Libp2p se adapta a una amplia gama de aplicaciones, desde sistemas de almacenamiento distribuido hasta redes de transmisión de datos, lo que lo convierte en un componente esencial para la arquitectura de Madara y su integración con Starknet.
- **GRANDPA:** Es la abreviatura de (GHOST-based Recursive Ancestor Deriving Prefix Agreement), un componente de vital importancia que desempeña un rol crucial similar a una "llave maestra" para los clientes de cadenas de bloques basadas en Substrate. Podemos definir este algoritmo de finalización que intenta conseguirel  equilibrio perfecto entre velocidad y seguridad en el intrincado proceso de consenso. Su enfoque innovador se centra en el concepto de votar por bloques válidos y, de manera progresiva y transitiva, aplicar esos votos a lo largo de las generaciones de bloques ancestrales. Esta estrategia inteligente permite la finalización de bloques al lograr una supermayoría de votos, lo que asegura una finalidad asincrónica y, además, otorga adaptabilidad ante diversas condiciones de la red.

    La distinción de GRANDPA se manifiesta en su capacidad excepcional para finalizar múltiples bloques de manera simultánea, una característica que confirma su resiliencia incluso en circunstancias de particiones prolongadas en la red. En un esfuerzo por mantener la integridad del proceso, aquellos participantes que emiten votos contradictorios son detectados y enfrentan consecuencias mediante un protocolo meticuloso de desafío y respuesta. Un aspecto digno de mención es la flexibilidad de GRANDPA para asignar pesos individuales a nodos, considerando factores como la cantidad apostada en el protocolo. Esta capacidad de personalización potencia la influencia de los nodos en el proceso de finalización, contribuyendo a un consenso robusto y equilibrado.

    En esencia, GRANDPA fusiona magistralmente la estructura misma de la cadena de bloques con el intrincado proceso de consenso, generando así un mecanismo seguro y responsable de finalización. La habilidad para concluir múltiples bloques, adaptarse ágilmente a condiciones cambiantes en la red y otorgar a los nodos la posibilidad de influir en el proceso, lo sitúa como un pilar esencial en la arquitectura dinámica de Polkadot y en la evolución continua de las cadenas de bloques hacia un futuro prometedor.

## Substrate
Las cadenas Substrate presentan tres características distintivas que las califican como "de próxima generación":

- Una función de transición de estado dinámica y autodefinida.
- Funcionalidad de cliente ligero desde el primer día.
- Un algoritmo de consenso progresivo con una rápida producción de bloques y una finalidad adaptativa y definida.

La función de transición de estado (STF), codificada en WebAssembly, se conoce como el "tiempo de ejecución" (runtime). Esta define la función `execute_block`, y puede especificar desde el algoritmo de staking, la semántica de transacciones, los mecanismos de registro y los procedimientos para reemplazar cualquier aspecto de sí misma o del estado de la cadena (gobernanza). Debido a la total dinamicidad del tiempo de ejecución, todos estos elementos pueden cambiarse o actualizarse en cualquier momento. En esencia, una cadena Substrate es comparable a un "organismo vivo".

Para obtener más información sobre Substrate, puedes [consultar este enlace.](https://www.parity.io/what-is-substrate/).

### Explorando las Posibilidades de Substrate
Substrate está diseñado para ser utilizado de tres maneras diferentes:

1. **Sencilla:** Se ejecuta el binario Substrate y se configura con un bloque génesis que incluye el tiempo de ejecución de demostración actual. En este caso, simplemente construyes Substrate, configuras un archivo JSON y lanzas tu propia cadena de bloques. Esto te brinda un nivel mínimo de personalización, permitiéndote principalmente cambiar los parámetros génesis de los diversos módulos de tiempo de ejecución, como balances, staking, período de bloque, tarifas y gobernanza.

2. **Modular:** Se ensamblan paquetes (pallets) con Substrate FRAME para crear un nuevo tiempo de ejecución, posiblemente alterando o reconfigurando la lógica de generación de bloques del cliente Substrate. Esto te otorga una gran cantidad de libertad sobre la lógica de tu cadena de bloques, permitiéndote cambiar los tipos de datos, añadir o quitar módulos y, crucialmente, agregar tus propios módulos. Gran parte puede modificarse sin afectar la lógica de generación de bloques (pues es genérica). En este caso, el binario Substrate existente puede usarse para la generación de bloques y sincronización. Si es necesario ajustar la lógica de generación de bloques, será necesario construir un nuevo binario de generación de bloques modificado como proyecto independiente y utilizarlo para los validadores. Este enfoque se utiliza para la cadena de relés de Polkadot y debería ser adecuado para la mayoría de las circunstancias a corto y mediano plazo.

3. **Genérico:** Es posible ignorar completamente FRAME y diseñar e implementar el tiempo de ejecución desde cero. Si se desea, esto puede hacerse en un lenguaje distinto de Rust, siempre y cuando pueda apuntar a WebAssembly. Si el tiempo de ejecución es compatible con la lógica de generación de bloques del cliente existente, simplemente puedes construir un nuevo bloque génesis a partir de tu fragmento de WebAssembly (Wasm) y lanzar tu cadena con el cliente Substrate existente basado en Rust. Si no es así, será necesario ajustar la lógica de generación de bloques del cliente según corresponda. Esta opción es probablemente la menos utilizada por la mayoría de los proyectos, pero ofrece una flexibilidad completa que permite un camino de actualización a largo plazo y de amplio alcance para el paradigma Substrate.

Sin embargo, es importante destacar que Substrate también establece normas y convenciones, especialmente en relación con la Biblioteca de Módulos de Runtime. En términos generales, estos tipos de datos fundamentales se corresponden con interfaces ("traits") en lo que respecta al estándar no negociable y estructuras genéricas ("structs") en lo que respecta a la convención.

- **Encabezado:** = Padre + ExtrinsicsRoot + StorageRoot + Digest
- **Bloque:** = Encabezado + Extrinsics + Justificaciones

Con este conocimiento en mente, podemos sumergirnos en las complejidades de Madara y comprender mejor cómo Substrate proporciona una base sólida para su construcción.

## Execution
En la base de esta fascinante estructura se encuentra la capa de Ejecución (Execution). Aquí, la ejecución de los bloques y la evolución del state distaf toman forma. Lo impresionante de Madara es su habilidad para transitar sin esfuerzo entre dos enfoques de ejecución: [Blockifier] de Starkware y [starknet_in_rust] de LambdaClass. Esta flexibilidad promete optimizaciones en constante evolución, con la posibilidad de consolidar en un único enfoque a medida que el tiempo avance.

## Settlement Eficiente
En la dinámica de un Validity Rollup, podemos usar la arquitectura de Madara se despliega magistralmente desde su estrato de Settlement. En esta genialidad técnica, Madara no impone restricciones sobre las opciones disponibles para esta capa. 

Para ilustrarlo con un ejemplo concreto, consideremos un escenario de nivel L3. 

> Madara tiene la capacidad de orquestar la transmisión de pruebas periódicas hacia Starknet, específicamente para un conjunto de bloques L3. El intervalo de aproximadamente ~ 5 horas para la liquidación en Starknet, un parámetro influenciado por los costos asociados con la liquidación en Ethereum, adquiere un matiz de eficiencia extraordinaria. En contraposición, en una configuración L3, se abre la posibilidad de establecer la liquidación en Starknet en intervalos aún más frecuentes, lo cual conlleva una disminución significativa en los costos operativos.

Madara es el arquitecto de la cadena que permite erigir la totalidad de su estructura a partir de su capa de asentamiento. Se distingue por su enfoque agnóstico respecto a las capas de asentamiento, ofreciendo así un lienzo en blanco para las decisiones de diseño. Asimismo, dentro de este ecosistema, Madara proporciona el marco para establecer tanto la finalidad Hard como la Soft, una dualidad contextual que aporta versatilidad y adaptabilidad a la plataforma.

## Sequencing Adaptativa
La Secuenciación (Sequencing), vital en el funcionamiento de Madara, es moldeable según las necesidades. Las posibilidades son infinitas: desde esquemas sencillos First-Come-First-Served (FCFS) hasta enfoques más sofisticados como Narwhall & Bullshark o el intrigante HotStuff.

- **HotStuff:** Basado en el protocolo de consenso PBFT (Practical Byzantine Fault Tolerance), HotStuff es una evolución de PBFT diseñada para optimizar el rendimiento y la latencia. Introduce el "consensus certificate" y utiliza una estructura de árbol llamada "fair chain" para agilizar el proceso de consenso. Este enfoque permite lograr consenso con menor latencia y número reducido de mensajes.

En el contexto de la secuenciación, el orden de las transacciones desempeña un papel crucial para proteger contra ataques MEV y asegurar una distribución equitativa. Las aplicaciones específicas pueden incluso implementar estrategias como memorias encriptadas para garantizar un orden equitativo.

## Fundamentos de Disponibilidad de Datos
En Madara, se están explorando diversos esquemas de DA para garantizar la integridad y accesibilidad de la información.

- **Validium:** Este enfoque implica datos con disponibilidad off-chain, administrados por un Comité conocido como Data Availability Committee (DAC). Este comité se encarga de asegurar que los datos estén disponibles y se mantengan fuera de la cadena principal.
- **Rollup:** Aquí, los datos tienen disponibilidad on-chain, siguiendo una dinámica similar a lo que estamos familiarizados con los Validity Rollup. En este caso, se almacena la diferencia de estado (state delta) en la cadena Ethereum.
- **Volition:** Ofrece una alternativa personalizada y híbrida, permitiendo a los usuarios decidir qué datos desean guardar en la capa L1 de Ethereum y cuáles mantener off-chain, esto empodera a los desarrolladores para seleccionar el nivel de disponibilidad de datos más adecuado para sus aplicaciones, ya sea en la L1 de Ethereum para una seguridad sólida o en la L2 de Starknet para reducción de costos. Adicionalmente, Volition brinda la opción de autohospedar sus propios datos o alojarlos en otros esquemas de gestión de datos, como **Celestia** o **Eigen DA.**   

Estos enfoques en la disponibilidad de datos no solo demuestran la versatilidad y capacidad de adaptación de Madara, sino que también allanan el camino hacia soluciones más eficientes y escalables dentro del ecosistema de Starknet y otros entornos. En estos contextos, Madara puede ser empleada como punto de entrada para capitalizar la potencia de Cairo y los STARKs, brindando nuevas oportunidades para impulsar la innovación y el crecimiento tecnológico.

## Diseño de Gobernanza Robusta en Madara y Starknet
En el contexto de Starknet y Madara, se está llevando a cabo un proceso de descentralización tanto en la infraestructura de red como en la toma de decisiones del protocolo. Esta iniciativa tiene como objetivo primordial fortalecer la participación y el empoderamiento de la comunidad en el desarrollo y las decisiones clave.

Uno de los elementos esenciales de Madara es Snapshot X, que establece un sistema completamente en cadena basado en sólidas pruebas de almacenamiento. Esta estrategia de gobernanza ha demostrado su efectividad en diversas situaciones, incluyendo casos como el de Turbo VM. Las pruebas de almacenamiento se presentan como el principal mecanismo de conexión en el ecosistema de Madara, garantizando la integridad de las resoluciones tomadas por la comunidad.

Además, Madara se encuentra en proceso de exploración de alternativas, tales como el módulo de gobernanza nativa de Substrate. Aprendiendo de lecciones valiosas provenientes de plataformas exitosas, Madara reconoce la trascendencia de mantener una gobernanza en cadena, en línea con la filosofía observada en ecosistemas como Cosmos y Polkadot.

En busca de una gobernanza más inclusiva y efectiva, Madara considera la adopción de herramientas avanzadas como [OpenGov](https://wiki.polkadot.network/docs/learn-polkadot-opengov) y [Pallet Democracy](https://docs.rs/pallet-democracy/latest/pallet_democracy/). Estas herramientas permiten una toma de decisiones participativa y adaptable a través de la delegación y la participación directa de la comunidad.

* **OpenGov:** Dentro del ecosistema de Polkadot, OpenGov promueve la inclusión al permitir que cualquier miembro de la comunidad proponga y vote en referendos. Basado en 15 Trayectorias únicas, cada una con reglas predefinidas, OpenGov permite que las propuestas sean evaluadas y votadas por expertos en áreas específicas. Esto asegura que incluso aquellos menos familiarizados con los aspectos técnicos puedan influir en las decisiones clave.

* **Pallet Democracy:** Este paquete se encarga de la administración de las votaciones generales de los stakeholders. A través de un proceso en dos colas, las propuestas son transformadas en referendos. Cualquier titular de tokens puede votar, utilizando un sistema de bloqueo temporal para expresar su convicción en las decisiones. La flexibilidad y la adaptabilidad son elementos clave de este enfoque.

Esta convergencia entre Madara y Starknet resalta la vital importancia de la descentralización y la gobernanza activa en la evolución de estos ecosistemas. La prometedora trayectoria de ambas plataformas se moldea a través de la colaboración y la participación comunitaria en la toma de decisiones.