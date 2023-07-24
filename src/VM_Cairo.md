# VM de Cairo
Profundizaremos en la arquitecura de CVM y como es su funcionamiento a nivel de ejecutar AIR, optimizaciones usando built, instrucciones y sus diseños para mejorar pasos y potenicar sus funciones, en ellos estaran como se organizan los diseños lineales o dynamicos para optimizar el rendimiento de un progrma de Cairo, el cual revisaremos las trace celd.

Este conjunto minimalista de instrucciones se denomina `RISC algebraico` (Computadora de conjunto de instrucciones reducidas); `Algebraico` se refiere al hecho de que las operaciones admitidas son operaciones de field. El uso de un `RISC algebraico` nos permite construir un AIR para Cairo con solo 51 celdas traza por paso. 

Un de los mejores ejemplos es [RISC Zero](https://www.risczero.com/), que detallaremos más en otras arquitecturas pero básicamente `RISC Zero zkVM` es un ordenador verificable que funciona como un microprocesador `RISC-V` real integrado, lo que permite a los programadores escribir pruebas ZK como si escribieran cualquier otro código. También destacamos que soporta Rust para escribir pruebas ZK y puede admitir cualquier lenguaje que compile en RISC-V.

## Builtin
Los builtins son unidades de ejecución de bajo nivel optimizadas predefinidas que se agregan a la placa de la CPU de Cairo para realizar cálculos predefinidos que son caros de realizar en vainilla Cairo (por ejemplo, verificaciones de rango, hash de Pedersen, ECDSA, ... ).

Poseidón es una familia de funciones hash diseñadas para ser muy eficientes como circuitos algebraicos. Como tales, pueden ser muy útiles en sistemas de prueba ZK como STARK y otros

La comunicación entre la CPU y los builds se realiza a través de la memoria: a cada incorporado se le asigna un área continua en la memoria y aplica algunas restricciones (dependiendo de la definición incorporada) en las celdas de memoria en esa área. En términos de construcción del AIR, significa que agregar incorporaciones no afecta las restricciones de la CPU. Simplemente significa que la misma memoria se comparte entre la CPU y las incorporaciones.

Para `invocar` un incorporado, el programa de El Cairo `se comunica` con ciertas celdas de memoria, y el incorporado impone algunas restricciones en esas celdas de memoria.

Gas por built = https://docs.starknet.io/documentation/architecture_and_concepts/Fees/fee-mechanism/#general_case

VM cpu AIR = circuitos integrados en cairo, no hace falta circom, aritmet se hace nativo, builtin, Dynamic layout (bosque oscuro....)

Desde Lambda se hicieron pruebas para exportar Circom, Snark, Groth16, Plonk

Circom = https://github.com/lambdaclass/circom_export_to_cairo

Vm en rust con sequencer en rust, mejoras de 10 x (lanzado en v.0.12 haremos pruebas tps y mps en explorador) posible consenso BFT