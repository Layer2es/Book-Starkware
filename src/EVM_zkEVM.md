# EVM vs zkEVM
El desafío central con el enfoque zkEVM está enraizado en el plan original de EVM, este no fue diseñado para funcionar dentro de un contexto de prueba de validez. En consecuencia, los esfuerzos para reflejar su funcionalidad no logran desbloquear todo el potencial de las pruebas de validez, lo que resulta en una eficiencia menos que óptima. Tal ineficiencia finalmente pesa el rendimiento general del sistema. 

La compatibilidad del EVM con las pruebas de validez se ve obstaculizada por los siguientes factores:

* El EVM emplea un modelo basado en apilamiento, mientras que las pruebas de validez se emplean de manera más efectiva con un modelo basado en registros. La naturaleza basada en la pila del EVM hace que sea inherentemente más difícil demostrar la exactitud de su ejecución y proporcionar soporte directo para su cadena de herramientas nativa.

* El diseño de almacenamiento Ethereum depende en gran medida de Keccak y un gran árbol Merkle Patricia, que no son amigables con Validity Proof e imponen una carga de prueba sustancial. Por ejemplo, Keccak es muy rápido para las arquitecturas x86 ( sobre las cuales generalmente ejecutamos el EVM ), pero toma 90k pasos para probar ( con una construcción especial incorporada ). Mientras que Pedersen ( una función hash amigable con zk ) da 32 pasos. Incluso con compresión recursiva, el uso de Keccak en un zkEVM significa altos recursos de prover que terminan siendo pagados por el usuario.

