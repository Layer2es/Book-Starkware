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

Para `invocar` un builtin, el programa de Cairo `se comunica` con ciertas celdas de memoria, y el builtin impone algunas restricciones en esas celdas de memoria.

## Fase de Inicialización y Ejecución de Hints en la CVM
La operación de la CVM involucra dos fases cruciales: la Fase de Inicialización y la Fase de Ejecución. Durante estas etapas, se administran y ejecutan las "hints" (pistas o indicaciones) que desempeñan un papel esencial en el procesamiento eficiente y seguro de programas. Los "hints" son fragmentos de información contextual que se incorporan en el código del programa, suministrando instrucciones específicas a la CVM durante su ejecución. Estas instrucciones abarcan desde detalles sobre el flujo de ejecución hasta orientaciones sobre las operaciones a llevar a cabo. Los "hints" ofrecen un mecanismo para optimizar y agilizar la ejecución de contratos inteligentes, al tiempo que garantizan su corrección y seguridad.

En el ámbito de las pruebas en la cadena de bloques, los "hints" desempeñan un papel crucial en la generación y verificación de los STARKS. Los "hints" en este contexto proporcionan información adicional a los Provers y el Verifier, posibilitando la generación y revisión de pruebas con mayor precisión.

A continuación, se desglosan los procesos inherentes a cada una de estas fases:

### Fase de Inicialización
En esta etapa inicial, se realizan una serie de actividades fundamentales:

1. **Carga del Programa:** La fase se inicia con la disponibilidad de un archivo JSON compilado que encapsula detalles exhaustivos sobre un programa en la Máquina Virtual Cairo.

2. **Sección de Hints:** Dentro del archivo, una sección denominada "hint" alberga información detallada sobre cada "hint" presente en el programa.

3. **Detalle de Hints:** Cada "hint" contiene datos esenciales, como su código, los contextos en los que es accesible (principal, función actual, funciones integradas e incluso la ruta de importación en el caso de funciones importadas), seguimiento de flujo y las "reference_ids" que se vinculan a las variables con las que interactúa en su entorno.

4. **Almacenamiento de Información:** Al cargar el archivo JSON y crear un objeto "Program", toda la información relacionada con los "hints" se organiza en un campo llamado "hints", estructurado como un diccionario.

5. **Carga y Asociación:** En el inicio de la máquina virtual (VM) y la carga de los datos del programa a través de la función "load_program", también se ejecuta la función "load_hints". Esto da como resultado la creación de un diccionario que relaciona una dirección en el programa con una lista de "hints" compilados. Es posible que una misma dirección albergue varios "hints".

6. **Asignación de Identificadores:** Además, se establece un mapeo que conecta un "id" (identificador único del "hint") con una dirección y, en situaciones en las que existen múltiples "hints" en la misma dirección, se asigna un índice. Esta disposición facilita la identificación y gestión de los "hints".

7. **Compilación de Hints:** La obtención de los "hints" compilados se lleva a cabo mediante la función "compile" de Python en modo de ejecución, utilizando el código inherente a cada "hint".

### Fase de Ejecución
La Fase de Ejecución abarca los siguientes pasos:

1. **Gestión de Hints:** Al dar comienzo a un paso en la ejecución del programa, se inicia el manejo de los "hints".

2. **Recopilación y Exploración:** Se reúne la lista de "hints" en la dirección actual del programa (si está presente) y se procede a iterar a través de ella.

3. **Entorno de Ejecución:** Se crea un diccionario llamado "exec_locals", el cual encapsula información relevante. Esto incluye la entrada del programa, la memoria validada ("validated_memory"), los registros actuales (ap, fp, pc), el paso actual, los identificadores (que contienen memoria), ap, fp y pc como constantes, y algunas funciones específicas del programa.

4. **Ejecución de Hints:** Posteriormente, cada "hint" se ejecuta mediante la función "exec" de Python. En este contexto, el diccionario "exec_locals" se emplea como entorno de ejecución para estas operaciones.

## Versiones VM
A medida que ha transcurrido el tiempo, se han implementado una serie de optimizaciones en varias versiones de la CVM. Nuestra atención se concentrará en el contexto del ecosistema desarrollado por Starkware, específicamente, exploraremos las distintas encarnaciones de la VM dentro de este marco. Sin embargo, es importante resaltar que el tema de las relaciones con las STARKs en diversos contextos, más allá de Starknet y otras arquitecturas, es un asunto amplio y diversificado que tiene varios espacios detallados en capítulos separados.

- Inicialmente, se creó la Máquina Virtual Cairo en Python por parte de Starkware, y durante varios años, esta versión fue el núcleo del ecosistema.
- Posteriormente, con Quantum Leap y la versión 0.12, se incorporó una implementación en Rust de la VM de Cairo, conocida como [cairo-vm en Rust](/https://github.com/lambdaclass/cairo-vm). Esta implementación en Rust logró un rendimiento destacado gracias a Lambda Class.
- Además, se encuentra en desarrollo una [VM en GO](https://github.com/lambdaclass/cairo-vm.go) desde Lamda Class, esta implementación en curso de la Máquina Virtual Cairo en Go tiene múltiples objetivos, pero podemos destacar la **Diversidad de Implementaciones**. Contar con varias implementaciones contribuye a la detección de errores y fortalece todo el ecosistema, además de poder documentar ampliamente la Máquina Virtual en su conjunto.