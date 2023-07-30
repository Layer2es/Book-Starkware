# Starknet Stack 

1. **Client**: Es el punto de inicio del ciclo. El cliente envía transacciones de Starknet a través de la red.

2. **Sequencer**: El secuenciador recibe las transacciones enviadas por el cliente y las organiza en bloques que contienen varias transacciones.

3. **Watcher-Prover**: Este es un servicio que actúa en dos partes: el "Watcher" y el "Prover".

   - **Watcher**: Monitorea la cadena de bloques en busca de bloques confirmados generados por el secuenciador.
   - **Prover**: Genera pruebas (STARK proofs) para cada transacción dentro de los bloques confirmados. Para hacerlo, utiliza la "Cairo VM" para ejecutar los programas Cairo asociados con cada transacción y genera las trazas correspondientes.

4. **Request blocks through RPC**: Después de que el "Watcher-Prover" identifica un nuevo bloque con transacciones confirmadas, solicita los bloques al secuenciador a través de un protocolo de comunicación remota llamado RPC (Remote Procedure Call).

5. **STARK proofs**: Una vez que el "Watcher-Prover" tiene acceso a los bloques confirmados, genera pruebas STARK para cada transacción dentro de esos bloques utilizando la información obtenida de la ejecución de los programas Cairo asociados con cada transacción.

6. **Proof Storage (Db)**: Las pruebas STARK generadas se almacenan en una base de datos (Db) para su posterior uso y consulta. Es importante destacar que el estilo de línea (stroke-dasharray: 5) indica que esta conexión es de tipo almacenamiento, es decir, una conexión de datos más permanente.

7. **Cairo Native**: Es la ejecución de los programas Cairo asociados con cada transacción dentro de los bloques confirmados. Estos programas son ejecutados en la "Cairo Native" para obtener resultados y trazas que se utilizarán para generar las pruebas STARK.

8. **Consensus (C)**: Es la fase del ciclo en la que se realiza el proceso de consenso. Aquí, se acuerda el orden y la validez de las transacciones dentro de los bloques, lo que garantiza que todos los nodos de la red estén de acuerdo con el estado actual de la cadena de bloques.

9. **Blockchain data**: Una vez que el consenso se ha alcanzado y las transacciones se han confirmado, la información sobre los bloques y las transacciones se almacena en la cadena de bloques. En este punto, la información de la cadena de bloques está disponible para ser explorada y verificada.

10. **Explorer**: Es una herramienta de exploración y verificación de la cadena de bloques. Permite a los usuarios navegar por los bloques y transacciones, así como verificar la validez de las pruebas STARK asociadas con las transacciones.

