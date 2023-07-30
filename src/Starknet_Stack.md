# Starknet Stack
TL;DR (Too Long; Didn't Read):

El Stack de Starknet está experimentando un crecimiento vertiginoso y permitirá lanzar tu propia instancia personalizada de Starknet para satisfacer tus necesidades. Starknet ya es la capa 2 más eficiente en términos de rendimiento, con la comunidad de desarrolladores de más rápido crecimiento y la pila Rollup más descentralizada, que incluye infraestructura clave desarrollada por múltiples equipos independientes. Pronto se lanzará la primera Starknet Appchain en Mainnet.

Introducción:

Actualmente, hay un renacimiento de las cadenas públicas de capa 2 sobre Ethereum. Starknet, en particular, ha florecido con una comunidad de desarrolladores activos que abordan emocionantes casos de uso en juegos, DeFi, NFTs, IA y más.

La necesidad de Appchains, cadenas de bloques específicas de aplicaciones diseñadas para satisfacer las necesidades de una aplicación específica, ha sido evidente durante varios años y ahora está recibiendo una mayor atención. La oferta de servicios SaaS de StarkWare, StarkEx, ha impulsado el éxito de las Appchains de capa 2 más exitosas en funcionamiento en Ethereum, como dYdX y Sorare. A la fecha (julio de 2023), StarkEx ha liquidado alrededor de $1 billón en operaciones acumuladas y procesado más de 500 millones de transacciones. Las Appchains de Starknet son el entorno personalizado donde las aplicaciones pueden adaptar una instancia de Starknet para lograr un mayor control sobre las especificaciones, reducir costos, aumentar la escala y ofrecer privacidad opcional. El Stack de Starknet tiene como objetivo permitir que cualquier aplicación despliegue su propia Appchain de Starknet de forma descentralizada.

El Stack de Starknet:

Los bloques de construcción de Starknet atraen a una amplia gama de aplicaciones y casos de uso, que incluyen pruebas STARK, el lenguaje de programación Cairo y Abstracción de Cuenta nativa. Con la actualización de Starknet a la versión 0.12.0 en Mainnet, Starknet se convirtió en la capa 2 más eficiente en términos de TPS. Se espera que la ventaja de rendimiento de Starknet sobre otras capas 2 y, en particular, sobre las capas 2 compatibles con EVM, aumente con el tiempo, ya que Starknet no está limitado por las restricciones heredadas impuestas por el diseño e implementación del EVM.

Sin embargo, es natural que algunas aplicaciones requieran ajustes adicionales a su plataforma. El Stack de Starknet les permitirá hacerlo.

En línea con el ecosistema de Starknet, se busca mostrar primero y contar después. Pero dado el desarrollo electrizante dentro de nuestro ecosistema y el ritmo con el que evoluciona el Stack, hemos decidido ofrecer nuestra perspectiva actual sobre el Stack de Starknet. Los esfuerzos de desarrollo están impulsados por el ecosistema de Starknet y orquestados por la Fundación Starknet a través de sus colaboraciones de desarrollo.

Beneficios:

El Stack de Starknet permite a las aplicaciones crear sus propias Appchains personalizadas. Estas proporcionarán los beneficios genéricos de las Appchains, como:

- Protección contra la congestión en la red pública de Starknet, lo que permite a los usuarios obtener un mejor rendimiento y experiencia de usuario.
- Las Appchains pueden implementar características que no son compatibles con la cadena pública, como su propia lógica de mercado de tarifas. Desde la perspectiva de la red pública, estas nuevas características implementadas en las Appchains son valiosos experimentos. Implementarlas en una Appchain proporcionaría conclusiones valiosas que podrían aplicarse a otras Appchains o a la red pública.

Además de estos beneficios, las Appchains de Starknet tendrán ventajas adicionales. Starknet es el rollup más escalable, con la opción de configurar varios parámetros, incluidos el consenso, los parámetros de la cadena de bloques y la disponibilidad de datos.

Descentralización:

El Stack de Starknet se está convirtiendo rápidamente en la pila L2 más descentralizada. Las blockchains sin permisos se centran en la descentralización como medio para lograr la seguridad y resiliencia de la red. La Fundación Starknet está enfocada en lograr esta propiedad para Starknet.

"Una pila descentralizada hace que la red sea más segura, resiliente, transparente, escalable e innovadora. Sin un único punto de falla, sin dependencia de una única entidad, sin cajas negras y mucho más constructores".

Diego Oliva
CEO, Starknet Foundation

"Starknet está logrando la descentralización orgánica de la pila: diferentes equipos están produciendo versiones optimizadas de los componentes principales, que luego vuelven a las versiones oficiales (LambdaClass Rust VM) o crean completamente nuevos componentes".

Nicolas Bacca
Cofundador y CTO, Ledger

Madara:
Un ejemplo reciente de la descentralización del Stack de Starknet es el Secuenciador de Madara. Está basado en Substrate y, como tal, se basa en mecanismos de consenso descentralizados de forma nativa. El esfuerzo de desarrollo comunitario comenzó en febrero de 2023. El esfuerzo de ingeniería incluye a 45 desarrolladores de la comunidad, que hasta la fecha (julio de 2023) han realizado más de 740 commits y más de 400 solicitudes de extracción fusionadas. Este esfuerzo ha producido un Secuenciador compatible con Starknet público, con un mempool configurable y más.

LambdaClass:
Otro esfuerzo notable en la construcción de la pila que permitirá el lanzamiento de Appchains de Starknet es el trabajo realizado por LambdaClass (que también desempeñó un papel fundamental en las mejoras manifestadas en V0.12.0). LambdaClass está construyendo un Stack de Starknet que eventualmente incluirá un probador, un secuenciador, un motor de ejecución y un explorador de red. En un futuro cercano, estos diferentes componentes podrían integrarse con otros componentes del Stack de Starknet y convertirse en una instancia funcional de Starknet.

Por la Comunidad, para la Comunidad:

El ecosistema de Starknet tiene como objetivo tener múltiples implementaciones de cada componente en el Stack. Aquí hay una muestra de los diferentes equipos y la infraestructura que están desarrollando:

| Categoría |	Proyecto | Entidad | Estado |
|Nodo completo | Pathfinder | Equilibrium |	En producción |
Juno	Nethermind	En producción
Papyrus	StarkWare	Pronto en producción
Deoxys	KasarLabs	En desarrollo
Motor de ejecución	Blockifier	StarkWare	En producción
starknet_in_rust	LambdaClass	Pronto en producción
Secuenciador	SW Sequencer	StarkWare	En producción
Madara	Comunidad	En desarrollo
LC Sequencer	LambdaClass	En desarrollo
Probador	SW Prover	StarkWare	En producción
LC Prover	LambdaClass	En desarrollo
Sandstorm	Andrew Milson	En desarrollo


Además de los componentes principales del Stack, hay componentes y servicios complementarios importantes que son necesarios para ejecutar una Appchain (todos en producción, a menos que se indique lo contrario):

Exploradores de bloques: Starkscan, ViewBlock, Voyager y Explorer de LambdaClass (en desarrollo).
Indexadores: Apibara, Checkpoint, TokenFlow.
Servicios de API: Alchemy, Infura, Blast API, Lava y Chainstack.
Puentes: LayerSwap, Orbiter, StarkGate.
Pasarelas para monedas fiduciarias: Banxa, Ramp.
Billeteras: Argent, Braavos, Cartridge y Metamask’s Snap (llegará en sep 2023).
Marco de desarrollo de aplicaciones específico de dominio: Dojo (juegos).
Oráculos: Pragma y RedStone.

Expresividad:

El Stack de Starknet está impulsado por Cairo. Su última versión, similar a Rust y ergonómica, ha generado una tremenda emoción en la comunidad de desarrolladores.

"Como alguien que nunca ha escrito Rust, lo aprendí hace unas semanas y soy tan eficiente escribiendo contratos Cairo como Solidity. Agregue la capacidad de compartir lógica entre contratos (¡próximamente!) y pruebas de fuzz incorporadas, y será mi entorno preferido para escribir contratos inteligentes".

Moody Salem
Desarrollador principal de Solidity, Uniswap

Cairo, como un lenguaje de contrato inteligente de propósito general, con la ventaja adicional de producir cálculos demostrables, es utilizado por uno de los ecosistemas de desarrollo de blockchain de más rápido crecimiento en la historia. Las aplicaciones pueden encontrar desarrolladores de Starknet con los que asociarse, contratar o externalizar.

"El ecosistema de Starknet se siente como los primeros días de Ethereum. Atrae al mejor talento en el espacio con su enfoque descentralizado para el desarrollo e innovación".

Itamar Lesuisse
Cofundador y CEO, Argent

El Camino por Delante:

El Stack de Starknet es un trabajo en progreso y continuará evolucionando y mejorando con el tiempo. Sin embargo, hoy en día, las Appchains de Starknet se pueden ejecutar como un servicio alojado, operado por StarkWare. De hecho, la primera Appchain de Starknet se lanzará pronto en una versión beta cerrada en Mainnet.

Esperamos que los equipos de desarrollo del ecosistema de Starknet, como LambdaClass, Nethermind y StarkWare, así como los proveedores de Rollup como servicio, ofrezcan servicios de alojamiento para las Appchains. Las Appchains elegirán qué componentes del Stack ejecutar por sí mismas y cuáles a través de un servicio de alojamiento (por ejemplo, SHARP de StarkWare). Pueden optar por depender de componentes de código abierto estrictamente, o de tecnología propietaria. Esta es la belleza de las Appchains: una talla única no sirve para todos. En cambio, cada aplicación tomará sus propias decisiones óptimas.

Las Appchains comenzaron como una capa 2 sobre Ethereum, pero no permanecerán allí por mucho tiempo. En 2021, StarkWare introdujo el concepto de capa 3. Creemos que, para lograr una mayor escala y menor costo por transacción, las Appchains de Starknet migrarán a la capa 3 y, como tal, se ejecutarán sobre la red pública de Starknet.

Resumen:

El Stack de Starknet está experimentando un crecimiento notable. Esperamos que domine el espacio de las Appchains debido a su rendimiento, seguridad y expresividad. El próspero ecosistema de desarrolladores de Starknet, que ha impulsado la rápida evolución de este Stack, continuará desarrollándolo y satisfaciendo las diversas necesidades de más y más aplicaciones.