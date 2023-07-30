# Starknet Kraken Sequencer

Una implementación descentralizada del secuenciador de Starknet.

## Para empezar

> **Nota:** El código actual de consenso se basa en gran medida en la implementación de [Albert Sonnino's (asonnino)  implementation](https://github.com/asonnino/hotstuff/), que se centró en la investigación en lugar de en la aplicación. Las modificaciones fueron realizadas por Lambda Class principalmente en la estructura del nodo para permitir el procesamiento de transacciones para bloques confirmados.

El objetivo de este proyecto es desplegar fácilmente un secuenciador descentralizado de capa 2 para Starknet. Esta será una de las múltiples implementaciones que seguirán al secuenciador descentralizado.

El secuenciador se puede dividir en (aproximadamente) 3 módulos intercambiables:

- Mempool (Narwhal), que almacena las transacciones recibidas.
- Consensus (Bullshark, Tendermint, Hotstuff), que ordena las transacciones almacenadas por el mempool.
- Motor de ejecución, que ejecuta las transacciones en la máquina de estado. El sistema operativo es proporcionado por Starknet en Rust y la ejecución se delega en Cairo Native o Cairo-rs.

Con módulos intercambiables nos referimos a que la implementación del algoritmo subyacente en la comunicación del Mempool, el protocolo de Consenso o el Motor de ejecución se pueden cambiar y configurar.

Además, para mantener y persistir el estado, hay un módulo de Estado que implementa  [PhotonDB](https://github.com/photondb/photondb) en una primera iteración.