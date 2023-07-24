# Playground
El Playground de Cairo es una herramienta que te permite crear y probar códigos de Cairo de manera interactiva. Con esta plataforma, puedes desarrollar y probar tus programas de Cairo antes de implementarlos en una cadena de bloques.

El proceso de prueba en el Playground de Cairo consta de varios pasos. Primero, cuando escribes tu código en Cairo, el Playground lo compila y ejecuta para crear un rastro de ejecución. Este rastro se envía a la red de Cairo para su evaluación.

En la etapa de prueba, el sistema de Cairo, conocido como SHARP, recopila múltiples trazas de ejecución de programas (incluso programas no relacionados) y los combina en un lote llamado "tren". Al igual que un tren no sale de la estación a pedido, el tren de Cairo puede tardar un tiempo en ser enviado al probador. SHARP esperará hasta acumular un lote lo suficientemente grande de trazas de programas o hasta que haya transcurrido cierto tiempo, lo que ocurra primero.

Una vez que se ha formado el tren de pruebas, SHARP envía este conjunto al verificador en cadena (actualmente en Goerli). Para cada programa en el tren, el contrato SHARP registra un hecho en el Registro de hechos que certifica la validez de la ejecución y su salida particular. Con esto, se cierra el ciclo y tu aplicación en la cadena de bloques puede utilizar la salida del programa.

Durante todo este proceso, puedes monitorear el estado de tu trabajo haciendo clic en el enlace en el panel de salida del Playground. Se abrirá una nueva pestaña que se actualizará automáticamente y te mostrará en qué etapa se encuentra tu trabajo.

Además, puedes acceder al contrato compartido para ver el hecho de tu trabajo utilizando el método isValid().