# Componentes
Aprendamos como a medida que te embarcas en el viaje para construir aplicaciones web3 escalables, es esencial comprender la arquitectura de donde estás construyendo, en este caso tendrás que formarte sobre Starknet y sus diversos componentes. Este capítulo tiene como objetivo proporcionar una comprensión profunda de los elementos clave de construcción de Starknet, lo que te permitirá desarrollar e implementar aplicaciones descentralizadas (dApps) de manera eficiente.

En este capítulo, abordaremos temas como:

* **Nodos L2:** Una visión general de alto nivel de los diferentes nodos de Starknet (Secuenciador, Full Nodes, Prover e Indexer) y sus funciones dentro de la red.

* **Ciclo de Vida de Transacciones:** Una explicación detallada de los diferentes estados por los que pasa una transacción L2, discutiendo los beneficios y riesgos de considerar un state en particular como **finality**, como se añadido con la 0.12.0 directamente el **Accepted_On_L2** eliminando el estado **Pending** y como la 0.12.1 empezará a cobrar y añadir las **tx Rejected** en el bloque, mejorando la eficiencia y seguridad de la red.

* **SHARP:** veremos el flujo de trabajo del SHARP, un componente en Starknet que actúa como un transporte público para las pruebas, permitiendo la agregación de múltiples programas Cairo para reducir costos y aumentar la eficiencia.

    Utilizando SHARP, se generan pruebas STARK para programas combinados, lo que facilita el envío de transacciones a una prueba común. La demostración recursiva de SHARP permite la paralelización y optimización, brindando escalabilidad a todas las aplicaciones, y su personalización.

* **Stack de Starknet:** permite crear sus propias Appchains personalizadas, lo que les proporciona beneficios como protección contra la congestión en la red pública y la capacidad de implementar características que no son compatibles con la cadena pública, como su propia lógica de mercado de tarifas. Lo que permite valiosos experimentos que pueden aplicarse a otras Appchains o a la red pública.

* **VM de Cairo:** 

Storage Proof:

Cairo:


Al final de este capítulo, tendrás un conocimiento profundo de la arquitectura y los componentes del ecosistema Starknet, lo que te permitirá tomar decisiones informadas al construir e implementar dApps en la plataforma.