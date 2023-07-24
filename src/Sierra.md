# Sierra - IR
En este apartadao detallaremos más la sintáxis del lenguague que su de finición de IR, que podra revisar en la [sección]()

* **Variables mutables:** En un lenguaje de programación tradicional, cada variable está asociada con una celda de memoria específica, una ubicación en la memoria de la computadora donde se almacenan los datos de la variable. Cuando a una variable se le asigna un valor, el valor se almacena en la celda de memoria asociada con esa variable. La variable puede acceder o modificar el valor almacenado en esa celda de memoria durante la ejecución del programa.

Sin embargo, en Cairo, es imposible modificar el contenido de una celda de memoria a la que ya se ha escrito.

Las variables mutables son el azúcar sintáctico que permite a los desarrolladores de El Cairo modificar y actualizar sin esfuerzo los valores de datos a lo largo de la ejecución de un programa sin tener que seguir manualmente la variable declarada anteriormente. Cuando modificamos nuestra variable mutable x, la variable Sierra correspondiente que almacena su valor se descarta primero ya que ya no se usa, y luego se crea una nueva variable con el valor actualizado

Del mismo modo, para una variable no mutable y, cuyo valor esté sombreado, el procedimiento en Sierra es exactamente el mismo: el valor anterior se cae y uno nuevo se instancia con el valor actualizado asociado con y. Sin embargo, se recomienda usar variables mutables en lugar de sombrear donde sea posible, ya que garantiza la consistencia en los tipos.

* **Referencias:** En los idiomas tradicionales, “pass-by-reference” es un método para pasar variables a funciones donde la función recibe una referencia a la ubicación de memoria de la variable. Esto permite que la función modifique el valor de la variable directamente. En Cairo, el equivalente se logra utilizando el ref modificador al definir el parámetro de función. Sin embargo, como se dijo anteriormente, es esencial tener en cuenta que una vez que los valores variables asignados no se pueden modificar directamente en Cairo, a diferencia de otros idiomas.

* **Snapshot:** En el lenguaje de programación de Cairo, las instantáneas se introducen como un tipo de envoltura que crea una vista inmutable de un objeto en un momento dado. Las instantáneas son útiles cuando necesitamos realizar en tipos no duplicables como matrices. En la implementación del tiempo de ejecución, las instantáneas son abstracción de costo cero debido al modelo de memoria escrita de la Asamblea de Cairo.

En el [crates cairo-lang-sierra](https://github.com/starkware-libs/cairo/blob/main/crates/cairo-lang-sierra/src/extensions/modules/snapshot.rs#L37), aprendemos que una instantánea es solo una envoltura alrededor de un objeto que garantiza que el objeto original no se modifique. los snapshot_take libfunc solo devuelve una instantánea al tipo si el tipo no se puede copiar. Los tipos duplicables son su propia instantánea, ya que la instantánea en sí misma es inútil si podemos duplicar el valor. Este concepto de instantáneas solo existe en el nivel Sierra y hace que el sistema de tipo lineal sea efectivo al garantizar que el objeto envuelto en una instantánea no pueda modificarse.

Pero, ¿cuándo encontramos instantáneas particularmente útiles? Específicamente cuando se trabaja con tipos no duplicables como Arrays. En el siguiente código, una función foo toma como parámetro una matriz a. Una instantánea de esta matriz se pasa a dos funciones, y luego se devuelve la matriz.

Cuando una función lleva una instantánea a un valor usando @, solo puede leer el valor y no modificarlo. Se comporta como un préstamo inmutable usando & en Rust, que permite que varias partes del programa lean el mismo valor simultáneamente y se asegura de que no se modifique. Cuando trabaja con objetos no copiables, el uso de instantáneas le permite retener la propiedad del objeto en el contexto de llamada y garantizar que el objeto permanezca inalterado.

* **Function inlining:** La combinación de funciones es una técnica de optimización del compilador que sustituye una llamada de función con el código real de la función que se llama. Elimina la sobrecarga de una llamada de función integrando el código de la función directamente en la función de llamada.

El compilador de El Cairo reemplazará automáticamente las llamadas a funciones marcadas como en línea directamente con su código Sierra. Esta optimización es especialmente útil para funciones pequeñas frecuentemente llamadas. Inlining puede reducir la sobrecarga de las llamadas a funciones y conducir a ejecuciones más rápidas y optimizadas, ya que los valores no necesitan ser recordados.

Resumen: Hemos explorado algunos conceptos centrales de El Cairo 1, como variables mutables, referencias e instantáneas. Hemos visto cómo las variables mutables en El Cairo son equivalentes a las variables sombreadas en Sierra y cómo las referencias en El Cairo usan el ref prefijo para pasar variables e implícitamente devolverlas. Además, hemos visto cómo las instantáneas en El Cairo son un concepto único que permite a los desarrolladores mantener la propiedad de los objetos al tiempo que garantiza que el valor original permanezca sin modificar. Finalmente, exploramos cómo los desarrolladores pueden usar la función como una técnica de optimización.

Cairo = Mejoras unicas en cairo?