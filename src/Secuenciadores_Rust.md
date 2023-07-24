# Secuenciadores Basados en Rust
Originalmente, los secuenciadores se escribieron en Python, que resultó ineficiente para operaciones a gran escala. A medida que la red alcanzó su capacidad, los desarrolladores buscaron mejorar el rendimiento del secuenciador. El primer hito fue establecer una cadena de bloques en pleno funcionamiento, seguida de un enfoque en la optimización del rendimiento.

La mejora inicial del rendimiento implicó la implementación de una concurrencia optimista para la ejecución de transacciones paralelas. Sin embargo, el avance más significativo provino de la reescritura de secuenciadores en Rust, un lenguaje más eficiente y más rápido.

La reescritura de secuenciadores en Rust ha mostrado resultados prometedores en rendimiento y escalabilidad. Se espera que el rendimiento y la latencia de la red Starknet mejoren dramáticamente, beneficiando a la red y a aquellos que trabajan con infraestructura relacionada y herramientas de desarrollo.

Uno de los nuevos secuenciadores se basa en Papyrus, un nodo completo Starknet de código abierto responsable de la gestión del estado. Los primeros puntos de referencia para proyectos como Madara revelan una notable transacción de 76 TPS ( por segundo ) para transferencias ERC20, mostrando las posibles mejoras que los secuenciadores basados en el óxido aportan al ecosistema Starknet.

La implementación de concurrencia optimista también contribuye a las mejoras en el rendimiento del secuenciador al ejecutar transacciones en paralelo, verificar conflictos en las celdas de almacenamiento tocadas e invalidar transacciones posteriores cuando sea necesario.

A medida que Starknet evoluciona, el desarrollo del secuenciador progresará, enfocándose en mejorar las capacidades y garantizar una integración perfecta con la red. Los desarrolladores trabajarán en nuevas características, como los mecanismos de tarifas, que se implementarán en los próximos lanzamientos como Memphis.

La mejora continua y la optimización de los secuenciadores son vitales para el crecimiento sostenido de Starknet. La transición a secuenciadores basados en Rust y los esfuerzos continuos para mejorar su desempeño indudablemente contribuirán.