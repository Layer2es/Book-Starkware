# SHARP
SHARP (SHARed Prover) opera como el transporte público para las pruebas en Starknet, permitiendo la agregación de múltiples programas Cairo con el fin de reducir costos y aumentar la eficiencia. Mediante SHARP, se generan pruebas STARK para los programas de Cairo combinados, lo que facilita que cualquier aplicación pueda enviar transacciones a la misma prueba. Además, SHARP emplea pruebas recursivas que permiten la paralelización y optimización, lo que lo convierte en una opción más accesible para todos los usuarios.

> Imagina que SHARP funciona como un servicio de reparto tipo StarknetUber para las Pruebas STARK. Es como cuando un grupo de amigos se reúne y cada uno realiza compras en diferentes tiendas, pero todos comparten el mismo servicio de entrega para recibir sus pedidos y compartir el gasto. 

De manera similar, SHARP permite que múltiples programas Cairo se unan y compartan el mismo proceso de generación de pruebas STARK. Cada programa puede ser como una compra individual en diferentes tiendas, pero al utilizar el servicio de reparto compartido de SHARP, los costos de generación de la prueba se distribuyen entre todos los programas. Esta dinámica de "reparto de entregas" garantiza que incluso las aplicaciones más pequeñas puedan acceder al enorme poder de escalabilidad que ofrece STARK. Si un programa está escrito en Cairo, SHARP puede demostrarlo, sin importar qué tan diversas sean las aplicaciones (dApps) que lo utilizan

- El procesamiento de SHARP agrupa aproximadamente 220,000 transacciones en una sola prueba en la red Ethereum Mainnet. 
- La demostración recursiva con SHARP permite el procesamiento y la verificación paralela de múltiples pruebas STARK, mejorando la escalabilidad y la eficiencia. 
- La personalización de SHARP, `Dynamic Layouts`, promete una reducción adicional de hasta un 30% en las tarifas de gas.

Veamos una analogía para ilustrar cómo funciona SHARP, según un documento oficial de StarkWare:

> Imagina que tú y tu hermana están comprando regalos para tus padres: un nuevo teléfono, una taza y una camiseta. Cada regalo se ordena en línea a un minorista diferente y se entregará en sus respectivos hogares en diferentes fechas, variando en tamaño y embalaje. Su plan es envolver cada artículo y enviarlos a sus padres por correo.

> Sin embargo, hay un problema en la oficina de correos. Las cajas pequeñas y medianas no están disponibles, solo hay cajas grandes de tamaño único. Esto presenta dos opciones:

* **Opción 1:** Empacar y enviar cada artículo por separado en su propia caja grande tan pronto como llegue. Si bien esto puede acelerar el envío de regalos individuales, requiere el esfuerzo adicional de empacar tres cajas separadas y hacer tres viajes a la oficina de correos para enviar tres paquetes diferentes. Como resultado, este método no resulta eficiente en términos de tiempo ni económico.

* **Opción 2:** Empacar y enviar todos los artículos juntos en una sola caja grande. Esto significa que solo manejarán una caja en lugar de tres.

> En este ejemplo, SHARP es la Opción 2, lo que permite el uso eficiente de los recursos y una gestión del tiempo más fluida.

SHARP es un sistema potente que está diseñado para generar pruebas STARK para programas de Cairo agrupados. Cairo, un lenguaje de programación de computación general, permite la acomodación de diversas lógicas de código en una sola prueba. El objetivo principal de SHARP es mejorar la escalabilidad y la eficiencia dentro de la red de Starknet, aquí tenemos algunas de sus propiedades y caractrerísticas:

**Amortización Exponencial y Eficiencia en Costos:** 

Una de las características clave de SHARP es su capacidad para reducir costos y mejorar la eficiencia en la generación de pruebas STARK. Al agrupar múltiples trabajos de Cairo (conjuntos individuales de cálculos), SHARP aprovecha la amortización exponencial que ofrecen las pruebas STARK. Esto significa que a medida que aumenta la carga computacional de las pruebas, el costo de verificarlas aumenta a una tasa logarítmica más lenta que el crecimiento de la computación en sí. Como resultado, el costo de cada transacción dentro del conjunto agregado se reduce significativamente, lo que lo hace más rentable y accesible para los usuarios.

**Procesamiento Paralelo y Pruebas Recursivas:** 

SHARP utiliza el procesamiento paralelo de declaraciones entrantes, lo que permite sortear las barreras de escalabilidad anteriores que requerían que las declaraciones combinadas se demostraran solo después de recibir todas las declaraciones individuales. Con la implementación de pruebas recursivas, SHARP demuestra cada declaración a medida que llega, en lugar de esperar a completar un conjunto de declaraciones para comenzar el proceso de demostración. Esto agiliza el proceso de verificación y mejora la eficiencia en comparación con el cálculo en sí.

Con la implementación de la recursión, SHARP demuestra las declaraciones entrantes de inmediato. A partir de ahí, estas pruebas pueden demostrarse repetidamente y fusionarse en pruebas recursivas. Este proceso de demostración recursiva se implementa hasta que, finalmente, la prueba final se envía a un contrato verificador de Solidity en cadena. 

**Validación y Solidity Verifier:** 

Las pruebas STARK generadas por SHARP se validan mediante un contrato verificador de Solidity en Ethereum. Antes de enviar las pruebas al verificador de Solidity, se envían inicialmente a un programa Verificador STARK escrito en Cairo. Este programa Verificador STARK genera una nueva prueba que confirma la validez de las pruebas iniciales, permitiendo la generación de múltiples pruebas hasta llegar al Verificador de Solidity en Ethereum.

**Acceso a la Escalabilidad de STARK para Todos:** 

SHARP permite que incluso las aplicaciones más pequeñas accedan al enorme poder de escalabilidad que ofrece STARK. Si un programa está escrito en Cairo, SHARP puede demostrarlo, sin importar qué tan diversas sean las aplicaciones (dApps) que lo utilizan.

Con SHARP, los desarrolladores tienen una solución efectiva para mejorar la escalabilidad y reducir los costos de transacción en la red de Starknet. La capacidad de procesar múltiples programas Cairo en una sola prueba STARK es un avance significativo que abre nuevas posibilidades para la adopción masiva de la tecnología de escalabilidad STARK.

**Dynamic Layouts:** 

El equipo detrás de SHARP está desarrollando actualmente Dynamic Layouts como la próxima personalización de sus servicios. Con Dynamic Layouts, el probador calculará los recursos necesarios para cada lógica específica y generará una prueba a medida en consecuencia.

Haciendo un paralelismo con nuestra analogía anterior, Dynamic Layouts se puede asemejar a la idea de cajas de envío personalizadas. Estas cajas personalizadas acomodan perfectamente la forma de cada regalo, asegurándose de que solo pagues por el tamaño exacto necesario, evitando tarifas innecesarias. De manera similar, con Dynamic Layouts, crearán una prueba adaptada para cada lógica y los recursos de computación únicos que requiere, asegurándose de que solo pagues por la computación que uses. Si está en Cairo, SHARP puede demostrarlo con precisión.

Al aprovechar el poder de la generación de pruebas recursivas basadas en STARK, SHARP se convierte en una tecnología que impulsa enormemente la escalabilidad y eficiencia de la red Ethereum. En el próximo capítulo, nos centraremos en analizar más a fondo su arquitectura y componentes, así como su funcionamiento, en especial la recursividad.



