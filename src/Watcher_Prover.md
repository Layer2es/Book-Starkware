# WatcherProver

Este es el servicio de watcher-prover para el sistema de pruebas.

La arquitectura consiste en un watcher que monitorea la cadena de bloques en busca de bloques confirmados y un prover que genera pruebas para cada transacción del bloque. Puede conectarse a cualquier cadena de bloques que admita contratos inteligentes.

Cuando el watcher encuentra una nueva transacción con un programa, primero llama a [cairo-rs](https://github.com/lambdaclass/cairo-rs/) para ejecutar el programa Cairo y generar la traza. Luego, esta traza se envía al prover de Lambdaworks que crea la prueba. La prueba se coloca luego en un bloque posterior en la cadena de bloques.

Inicialmente, estas operaciones se realizarán de forma secuencial. Sin embargo, en el futuro, el objetivo es realizarlas en paralelo, escalando horizontalmente.

Al ejecutar los provers en paralelo, la capacidad del sistema de pruebas será tan alta como la capacidad de la cadena de bloques. Sin embargo, existe una latencia del prover y la inclusión de las pruebas en los bloques.