# VM de Cairo

La Máquina Virtual Cairo (CVM) es un componente esencial del lenguaje de programación Cairo, utilizado para desarrollar y ejecutar contratos inteligentes en la cadena de bloques. Su arquitectura eficiente y sofisticada permite una gestión avanzada de la memoria, validación de instrucciones y deducción de valores.

La CVM forma el núcleo del lenguaje Cairo, brindando capacidades avanzadas de ejecución de contratos inteligentes y permitiendo el desarrollo de aplicaciones descentralizadas seguras y eficientes en la cadena de bloques. Su diseño técnico y eficiente hace posible la ejecución de programas complejos y la validación precisa de memoria, garantizando la confiabilidad y precisión en la ejecución de los contratos inteligentes.

A continuación, se detalla su funcionamiento y estructura técnica:

## Gestión de Memoria y Segmentos

La memoria de Cairo es de solo lectura, y las direcciones de memoria que el programa accede deben ser continuas. Los posibles huecos entre las direcciones son llenados con valores arbitrarios.

La memoria se organiza en segmentos continuos, cuyo tamaño varía y solo se conoce al finalizar la ejecución del programa. Las direcciones absolutas de cada celda dentro de un segmento se determinan utilizando valores `Relocatable`, que indican el número de segmento y el desplazamiento.

Los diferentes segmentos son:

1. **Segmento del Programa:** Contiene el bytecode de Cairo, con el `Program Counter (pc)` iniciando al principio de este segmento.
2. **Segmento de Ejecución:** Aquí se generan datos durante la ejecución del programa Cairo y su longitud es variable según la entrada del programa. Los `Allocation Pointer (ap)` y `Frame Pointer (fp)` comienzan aquí.
3. **Segmento Incorporado:** Cada función incorporada tiene su propio espacio continuo en memoria. La longitud es variable.

## Registros

Los registros son fundamentales para el funcionamiento de la Máquina Virtual Cairo:

1. **Allocation Pointer (ap):** Apunta a una celda de memoria sin usar.
2. **Frame Pointer (fp):** Apunta al marco de la función actual. Las direcciones de todas las variables locales y argumentos son relativas al valor de este registro. Al inicio de una **function1**, `fp` es igual a `ap` y permanece constante durante su ejecución. Cuando una **function2** se llama dentro de una **function1**, el valor de `fp` cambia para **function2** pero se restaura a su valor original al finalizar **function2** (esto permite rastrear el valor original de **function1**).
3. **Program Counter (pc):** Apunta a la instrucción actual. Cada instrucción toma 1 o 2 `felts`, y `pc` avanza 1 o 2 después de cada instrucción. Los saltos pueden cambiar el valor del `pc` a un valor absoluto o relativo, según las operaciones de salto.

## Validación y Deducción de Valores

La Máquina Virtual Cairo es capaz de deducir valores de memoria y validar la ejecución de instrucciones para asegurar la integridad y correctitud del programa. Utiliza pruebas recursivas para optimizar y paralelizar la ejecución, lo que mejora la eficiencia y escalabilidad del sistema.

## Jerarquía de Estructuras

La Máquina Virtual Cairo se basa en una jerarquía de estructuras que permiten un manejo complejo de la memoria y las operaciones:

1. **`VirtualMachineBase`:** Proporciona la base para la Máquina Virtual Cairo, con atributos importantes como el contexto de ejecución, registros, funciones incorporadas y más.
2. **`ValidatedMemoryDict`:** Contiene una memoria validada con reglas de validación y auto-deducción de valores.
3. **`auto_deduction`**: Es un diccionario que mapea un índice de memoria segmento a una lista de reglas para deducir el valor de una celda de memoria.

## Representación del Programa

El programa Cairo se representa mediante la estructura `ProgramBase`, que contiene información sobre funciones, referencias, constantes y otros elementos del programa. Esta estructura es serializable, lo que facilita su almacenamiento y distribución en la cadena de bloques.

## AIR y Builtins

Profundizaremos en la arquitectura de la CVM y su funcionamiento a nivel de ejecutar AIR, optimizaciones usando builtins, instrucciones y sus diseños para mejorar pasos y potenciar sus funciones. En ellos, estará cómo se organizan los diseños lineales o dinámicos para optimizar el rendimiento de un programa de Cairo, y revisaremos las celdas traza.

Este conjunto minimalista de instrucciones se denomina `RISC algebraico` (Computadora de conjunto de instrucciones reducidas); `Algebraico` se refiere al hecho de que las operaciones admitidas son operaciones de campo. El uso de un `RISC algebraico` nos permite construir un AIR para Cairo con solo 51 celdas traza por paso.

Uno de los mejores ejemplos es [RISC Zero](https://www.risczero.com/), que detallaremos más en otras arquitecturas. Básicamente, `RISC Zero zkVM` es un ordenador verificable que funciona como un microprocesador `RISC-V` real integrado, lo que permite a los programadores escribir pruebas ZK como si escribieran cualquier otro código. También destaca que soporta Rust para escribir pruebas ZK y puede admitir cualquier lenguaje que compile en RISC-V.

### Builtin

Los builtins son unidades de ejecución de bajo nivel optimizadas predefinidas que se agregan a la placa de la CPU de Cairo para realizar cálculos predefinidos que son costosos de realizar en vainilla Cairo (por ejemplo, verificaciones de rango, hash de Pedersen, ECDSA, ...).

Poseidon es una familia de funciones hash diseñadas para ser muy eficientes como circuitos algebraicos. Como tales, pueden ser muy útiles en sistemas de prueba ZK como STARK y otros.

La comunicación entre la CPU y los builtins se realiza a través de la memoria: a cada builtin se le asigna un área continua en la memoria y aplica algunas restricciones (dependiendo de la definición del builtin) en las celdas de memoria en esa área. En términos de construcción del AIR, significa que agregar builtins no afecta las restricciones de la CPU. Simplemente significa que la misma memoria se comparte entre la CPU y los builtins.

Para `invocar` un builtin, el programa de Cairo `se comunica` con ciertas celdas de memoria, y el builtin impone algunas restricc

iones en esas celdas de memoria.

**Gas por builtin:** [Mecanismo de tarifas](https://docs.starknet.io/documentation/architecture_and_concepts/Fees/fee-mechanism/#general_case)

**VM CPU AIR:** Circuitos integrados en Cairo, no hace falta Circom, la aritmética se hace nativa con builtins, Dynamic layout (bosque oscuro...).

Desde Lambda se hicieron pruebas para exportar Circom, Snark, Groth16, Plonk.

Circom: [Export to Cairo](https://github.com/lambdaclass/circom_export_to_cairo)

Vm en Rust con sequencer en Rust, mejoras de 10x (lanzado en v.0.12 haremos pruebas TPS y MPS en el explorador) posible consenso BFT.