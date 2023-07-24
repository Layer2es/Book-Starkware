# Cairo Native - MLIR
MLIR significa `(Intermediate Representation for Multi-Level Intermediate Representations)`, (Representación Intermedia MúltiNivel). Se refiere a un lenguaje de representación intermedia diseñado para ser flexible y adaptable a diferentes requisitos en una infraestructura unificada.

A diferencia de [LLVM IR](https://llvm.org/docs/LangRef.html#introduction), que tiene una única representación intermedia central que abarca un conjunto completo de instrucciones para representar programas de CPU/GPU, MLIR adopta un enfoque diferente. En MLIR, no existe una única representación intermedia unificada.

> MLIR tiene como objetivo abordar la fragmentación del software, mejorar la compilación de hardware heterogéneo, reducir significativamente el costo de construir compiladores específicos de dominio y ayudar a conectar compiladores existentes.

En su lugar, MLIR introduce conceptos abstractos como dialectos, operaciones y regiones. Estos conceptos permiten la definición de diferentes dialectos o lenguajes especializados, cada uno con su propio conjunto de operaciones y reglas semánticas específicas.

La idea detrás de MLIR es brindar una infraestructura flexible que pueda adaptarse a múltiples requisitos y necesidades en el ámbito de la representación intermedia. Esto significa que se pueden definir dialectos específicos para diferentes dominios, como procesadores específicos, aceleradores o incluso lenguajes de programación específicos.

En resumen, MLIR busca proporcionar una forma flexible y modular de representar programas en un nivel intermedio, permitiendo la adaptabilidad a diferentes requisitos y escenarios mediante el uso de dialectos y operaciones específicas de cada dominio.

> En otras palabras, si LLVM IR está centralizado por la naturaleza y favorece los flujos unificados del compilador, la infraestructura MLIR y su ecosistema de dialecto están descentralizados por la naturaleza y favorecen los diversos flujos del compilador. Lo que es bastante poderoso es que MLIR permite representar diferentes niveles utilizando la misma infraestructura, para que el flujo entre diferentes niveles pueda ser continuo.

La mayoría de los protocolos ZKP implican aritmetización, que es el proceso de representar el cálculo en un formato numérico que puede utilizar el sistema de prueba, generalmente tomando las instrucciones en el cálculo y construyendo un gráfico de expresión de operaciones en bits llamado circuito aritmético y luego generando un seguimiento de ejecución, que muy brevemente es una matriz de elementos de campo que representan la evolución del cálculo a lo largo del tiempo. Este rastro de ejecución se alimenta al probador.

Para encapsular estos procesos, las máquinas virtuales se han diseñado e implementado para generar estos rastros de ejecución numéricos y proporcionar garantías computacionales, como [Miden](https://github.com/0xPolygonMiden/miden-vm?ref=notamonadtutorial.com) y [cairo-rs](https://github.com/lambdaclass/cairo-rs/pulls?ref=notamonadtutorial.com). Una vez que tenga una máquina virtual, necesita un compilador y una representación intermedia.

Tampoco puede aceptar ningún programa, ya que necesita saber que su ejecución es demostrable a menos que esté dispuesto a asumir la posibilidad de programas no terminales, transacciones inválidas que consumen gas excesivo, la producción de trazas inválidas o incompletas, y que el probador simplemente renuncie en el medio. La teoría de tipos y las representaciones intermedias dentro de los compiladores se han convertido en una de las herramientas más potentes para producir código que tiene propiedades que podemos razonar y verificar mecánicamente.

En resumen, la necesidad de ejecutar hardware más diverso, incorporar tecnología de lenguaje de programación, para permitir el uso fácil de primitivas criptográficas complejas, Para transportar garantías de herramientas de desarrolladores a capas de ejecución, todos se han unido para lograr un pequeño renacimiento de la implementación del lenguaje en el mundo criptográfico.

