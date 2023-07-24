# Recursividad - SHARP
Una de las características más poderosas de SHARP es su uso de pruebas recursivas. En lugar de enviar directamente las pruebas generadas al Verificador de Solidity, primero se envían a un programa Verificador STARK escrito en Cairo. Este Verificador, que también es un Programa Cairo, recibe la prueba y crea un nuevo trabajo de Cairo que se envía al Proveedor. El Proveedor luego genera una nueva prueba para confirmar que las pruebas iniciales fueron verificadas. Estas nuevas pruebas se pueden enviar de vuelta a SHARP y al Verificador STARK, reiniciando el proceso.

Este proceso continúa de forma recursiva, enviando cada nueva prueba al Verificador de Cairo hasta que se alcanza un disparador. En este punto, la última prueba de la serie se envía al Verificador de Solidity en Ethereum. Este enfoque permite una mayor paralelización de la computación y reduce el tiempo y los costos asociados con la generación y verificación de pruebas.

A primera vista, las pruebas recursivas pueden parecer más complejas y consumir más tiempo. Sin embargo, hay varios beneficios en este enfoque:

* **Paralelización:** Las pruebas recursivas permiten la paralelización del trabajo, reduciendo la latencia del usuario y mejorando la eficiencia de SHARP.
* **Menores costos en la cadena:** La paralelización permite que SHARP cree pruebas más grandes, que anteriormente se limitarían por la disponibilidad de máquinas en la nube grandes (que son escasas y limitadas). Como resultado, los costos en la cadena se reducen.
* **Menores costos en la nube:** Dado que cada trabajo es más corto, se reduce la memoria requerida para el procesamiento, lo que resulta en menores costos en la nube.
* **Optimización:** Las pruebas recursivas permiten que SHARP se optimice para varios factores, incluyendo la latencia, los costos en la cadena y el tiempo de prueba.
* **Compatibilidad con Cairo:** Las pruebas recursivas solo requieren soporte en Cairo, sin necesidad de agregar soporte en el Verificador de Solidity.

La latencia en Starknet abarca el tiempo que lleva procesar, confirmar e incluir transacciones en un bloque. Está afectada por factores como la congestión de la red, las tarifas de transacción y la eficiencia del sistema. Minimizar la latencia garantiza un procesamiento de transacciones más rápido y una retroalimentación del usuario más rápida.

El tiempo de prueba, por otro lado, se refiere específicamente a la duración requerida para generar y verificar pruebas criptográficas para transacciones u operaciones.

Desde SHARP 4.0 se agregaron dos nuevos componentes importantes: keccack y Poseidón.

Keccack es importante para las aplicaciones y Poseidon también se usa en el propio estado de Starknet (para el nuevo cálculo de hash de clases de Cairo 1 y para el nuevo estado de clases).

La arquitectura del backend de SHARP consiste en varios servicios que trabajan en conjunto para procesar trabajos de Cairo y generar pruebas. Estos servicios incluyen:

* **Gateway:** Los trabajos de Cairo ingresan a SHARP a través del gateway.
* **Job Creator:** Evita la duplicación de trabajos y garantiza que el sistema funcione de manera consistente, independientemente de las solicitudes múltiples idénticas.
* **Validator:** Este es el primer paso importante. El servicio de validación realiza verificaciones en cada trabajo para asegurarse de que cumplan con los requisitos y puedan adaptarse a las máquinas probadoras. Los trabajos inválidos se etiquetan como tales y no continúan hacia el Prover.
* **Scheduler:** El servicio de planificación crea "trains" que agregan trabajos y los envían al Prover. Los trabajos recursivos se emparejan y se envían juntos al Prover.
* **Cairo Runner:** Este servicio ejecuta Cairo para las necesidades del Prover. El servicio Cairo Runner ejecuta programas de Cairo, realizando los cálculos necesarios y generando el rastro de ejecución como resultado intermedio. El Prover luego utiliza este rastro de ejecución.
* **Prover:** El Prover calcula las pruebas para cada trains (que contiene varios trabajos).
* **Dispatcher:** El Dispatcher cumple dos funciones en el sistema SHARP.
    - En el caso de una prueba recursiva, el Dispatcher ejecuta el programa Cairo Verifier en la prueba que ha recibido del Prover, lo que resulta en un nuevo trabajo de Cairo que vuelve al Validador.

    - En el caso de una prueba que debe ir a la cadena (por ejemplo, a Ethereum), el Dispatcher crea "paquetes" a partir de la prueba, que luego se pueden enviar al Escritor de la Cadena de Bloques.
* **Blockchain Writer:** Una vez que el Dispatcher ha creado los paquetes, los envía al Escritor de la Cadena de Bloques. El Escritor de la Cadena de Bloques se encarga de enviar los paquetes a la cadena de bloques correspondiente (por ejemplo, Ethereum) para su verificación. Este es un paso importante en el sistema SHARP, ya que garantiza que las pruebas se verifiquen correctamente y que las transacciones se registren de forma segura en la cadena de bloques.
* **Catcher:** El Catcher monitorea las transacciones de la cadena de bloques (por ejemplo, Ethereum) para asegurarse de que hayan sido aceptadas. Si bien el Catcher es relevante para fines de monitoreo interno, es importante tener en cuenta que si una transacción falla, el hecho no se registrará en el registro de hechos de la cadena. Como resultado, la integridad del sistema se mantiene incluso sin el Catcher.

SHARP está diseñado para ser sin estado (cada trabajo de Cairo se ejecuta en su propio contexto y no depende de otros trabajos), lo que permite una mayor flexibilidad en el procesamiento de trabajos.

Actualmente, los principales usuarios de SHARP incluyen:

- StarkEx
- Starknet
- Usuarios externos que utilizan el Cairo Playground

Optimizar el Proveedor implica numerosos desafíos y proyectos potenciales en los que el equipo de Starkware y la comunidad están trabajando actualmente:

* **Exploración de funciones hash más eficientes:** SHARP está constantemente explorando funciones hash más eficientes para Cairo, el Proveedor y Solidity.
* **Investigación de campos más pequeños:** La investigación de campos más pequeños para los pasos de prueba recursiva podría conducir a cálculos más eficientes.
* **Ajuste de varios parámetros:** SHARP está ajustando constantemente varios parámetros del protocolo STARK, como los parámetros FRI y los factores de bloque.
* **Optimización del código de Cairo:** SHARP está optimizando el código de Cairo para hacerlo más rápido, lo que resulta en un Proveedor recursivo más rápido.
* **Desarrollo de diseños dinámicos:** Esto permitirá a los programas de Cairo adaptar los recursos según sus necesidades.

Mejora del algoritmo de programación: Este es otro camino de optimización que se puede tomar. No está dentro del Proveedor en sí.

En particular, los Dynamic Layouts o diseños dinámicos, permitirán que los programas de Cairo adapten los recursos según sus necesidades. Esto puede llevar a una computación más eficiente y a una mejor utilización de los recursos. Los diseños dinámicos permiten a SHARP determinar los recursos necesarios para un trabajo específico y ajustar el diseño en consecuencia en lugar de depender de diseños predefinidos con recursos fijos. Este enfoque puede proporcionar soluciones personalizadas para cada trabajo, mejorando la eficiencia general.