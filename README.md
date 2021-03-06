# OBFAU3 (Autoit-Obfuscator)
## Características del proceso de ofuscado

* Número de iteraciones del proceso de ofuscado.
* Enlazar includes desde otros ficheros del proyecto.
* Eliminar comentarios especificados por tags (comment-start/comment-end y cs/ce)
* Eliminar comentarios especificados por ;
* Eliminar comentarios especificados por #
* Eliminar regiones (#Region)
* Añadir nuevas regiones
* Ocultar nombres de variables
* Ocultar nombres de funciones
* Añadir funciones hardcodeadas especificadas en Hardcoded/HardcodedPrograms.py
* Añadir variables
* Añadir comentarios
* Añadir bloques de código generado al inicio
* Añadir bloques de código generado al final
* Añadir bloques de código generado entre lineas del código original.
* Añadir funciones
* Añadir llamadas a funciones
* Ocultar strings con método replace.
* Ocultar strings con método shuffle (genera codigo autoit para desordenar y ordenar las strings).
* Ocultar strings con método cipher  (medio implementado por problemas con la salida de los algoritmos de PyCrypto).
* Ocultar strings con método reverse.
* Ofuscar enteros.
* Añadir directivas, incluido #pragma compile con datos generados.
* Añadir espacios y tabuladores en el código.
* Añadir símbolos en el EOF.

## Características de los bloques de código generados 

* Generación de código y bloques If, For, Switch, Func y Simple (definiciones de nuevas variables haciendo uso de macros,constantes ofuscadas, funciones del lenguaje de aridades 0,1 y 2 y valores de tipos básicos)
* Definición del número mínimo y máximo de bloques a añadir.
* Definición del número mínimo y máximo de sentencias a añadir dentro del bloque (estas sentencias pueden ser a su vez nuevos bloques).
* Definición del número mínimo y máximo de condiciones lógicas a añadir en la guarda de los bloques generados.
* Definición del número mínimo y máximo de ElseIf dentro de un bloque If.
* Definición de la profundidad máxima de anidamiento de bloques generados.
* Definición de los valores mínimo y máximo de los enteros a usar en las definiciones (tiene sentido cuando se combina con la ofuscación de números).
* Posibilidad de añadir bloques al inicio, al final y entre medias del código original.
* Definición de la probabilidad de generación de nuevos bloques entre medias del código original.
* Definición del número mínimo y máximo de funciones a añadir.
* Definición de la aridad mínima y máxima de las funciones a añadir (define el número de parámetros de una función).
* Es necesario especificar todos estos valores en las tres posibilidades de adición de bloques (inicio,final,medio).

## Otras características

* Definición de la profundidad máxima en el ofuscado de enteros.
* Definición del tamaño en KB de la secuencia de símbolos a añadir tras el EOF.
* Variables declaradas con Local,  Dim y Global.
* Considerado Call en las llamadas a funciones. (Considerar que el usuario pueda desactivarlo)
* Considerado Assign en las definiciones de variables. (Considerar que el usuario pueda desactivarlo)
* Considerado Eval. (Considerar que el usuario pueda desactivarlo)
* Alterar nombres de las funciones y palabras clave de AutoIt (Considerar que el usuario pueda desactivarlo)
* Posibilidad de combinar los métodos de ofuscado de strings disponibles.
* Implementado operador ternario (parece funcionar solo con algunas versiones de AutoIt, dar posibilidad de activarlo)
* Todos los parámetros de los procesos son elegidos de forma aleatoria entre los valores límite especificados por el usuario (incrementa la dispersión y permite incrementar la exploración del espacio de soluciones si se emplean algoritmos genéticos para optimizar los parámetros).

 

## Futuras versiones

* Algoritmo genético para optimizar los parámetros del proceso.
* GUI (Sadfud y Blau)
* Compilar automáticamente con Aut2Exe y variar sus parámetros (compresión,  iconos,  ...)
* Considerar arrays.
* Considerar constantes y enumeraciones (const y enum). (Reparando bugs)
* Añadir más funciones hardcodeadas.
* Añadir más métodos de ofuscado de strings.
* Parametrizar el script principal.
* Reordenación de código (tengo planteado algo usando grafos para tener en cuenta las dependencias).
* Dar la posibilidad de especificar más parámetros como el tamaño de los identificadores generados (esto se considera en las funciones implementadas pero no se deja al usuario especificarlo,   puede reducir considerablemente el tamaño del código).
* Hardcodear instancias simples de problemas NP.

## Errores conocidos

* Duplicate name (function) -> 
    * Problema: Repetición del nombre de alguna función (al parecer ocurre cuando se añaden directivas include repetidas).
    * Solución: Volver a ejecutar el ofuscador (desactivar la función de añadir directivas).
    
* Error in expresion        -> 
    * Problema: Error en algún Switch generado
    * Solución: Volver a ejecutar el ofuscador.
    
* Error subscripted array   -> 
    * Problema: Error general, fuente desconocida.
    * Solución: Volver a ejecutar el ofuscador, error general, fuente desconocida.

* Undefined variable        ->
    * Problema: Se hace uso de una variable no definida en alguna evaluación. 
		Generalmente ocurre cuando se intentan ocultar variables y se hace uso en el código de constantes AutoIt.
    * Solución: Desactivar la función de ocultar variables. (Intentad volviendo a ejecutar el ofuscador)

* Only Object-type variables allowed in a "With" statement ->
    * Problema: La variable especificada en la guarda del bloque With no es un objeto.
		Ocurre por una inicialización incorrecta de es tipo de bloques.
    * Solución: Volver a ejecutar el ofuscador.

* Variable must be of type "Object" ->
    * Problema: Alguna variable no es del tipo esperado (Object) en alguna expresión. Fuente desconocida.
    * Solución: Volver a ejeutar el ofuscador.

## Changelog 1

* Añadidos bloques For ... In, With, While y Do ... Until.
* Creación y uso de objetos COM.
* Operador ternario.
* Enums y consts (bug).
* Reparado el bug al ocultar variables no definidas por el usuario.
* Considerado Step en bucles For ... To.
* Añadidas cuatro funciones hardcodeadas.
* Añadido método para split para ofuscar strings.
* Actualizada la lista de errores y soluciones.

## Changelog 2

* Añadidas condiciones siempre ciertas en el código inicial.
* Expresiones regulares precompiladas.
* Añadidas más funciones hardcodeadas.
* Añadido método rotate para ofuscado de strings.
* Arreglado bug en hide var names.
* Arreglado bug en hide func names.
* Arreglado bug en true guard statements.
* Arreglado Error in expresion.
* Arreglado Only Object-type variables allowed in a "With" statement.
* Arreglado Variable must be of type "Object".
* Detectada la fuente de subscripted array (alguna de las funciones hardcodeadas).
* Mejorada la estabilidad.

##Changelog 3

* Arreglados bugs con los ofuscados de strings (replace,reverse,flip_two,split,rotate), shuffle sigue dando problemas.
* Mejorado el ofuscado de strings.
* Arreglados bugs con los ofuscados de nombres de variables.
* Arreglado bug al eliminar comentarios que empiezan por # (hash).
* Arreglado bug al eliminar comentarios que empiezan por ;
* Añadidos snippets de https://www.autoitscript.com/wiki/AutoIt_Snippets como funciones hardcodeadas.
* Añadida función para llamar a las funciones hardcodeadas.
* Añadido nuevo método de ofuscado de strings, hexify (BinaryToString , StringToBinary). 
  La longitud de las strings, con este método, se duplica, si supera el tamaño máximo de linea (Unterminated string) usar junto método split.
* Arreglados bugs al añadir funciones hardcodeadas.
* Extraídos mensajes para permitir traducciones.
* Mejorado el aspecto de la salida por consola.

##Changelog 4

* Añadido fichero de configuración del proceso. Todos los parámetros se gestionan ahora desde config.ini. 
* Traducción al Español y Portugués (Spanish,English,Portuguese disponibles). 
* Posibilidad de cambiar de idioma. 
* Ocultados parámetros de funciones. 
* Soporte a ByRef y valores por defecto en parámetros de funciones. 
* Mejorada la estabilidad en la ofuscación de nombres de variables, funciones y parámetros. 
* Generado ejecutable. 
* Añadidos todos los snippets AutoIt (https://www.autoitscript.com/wiki/AutoIt_Snippets) sin dependencias ni efectos visibles (+30). 
* Arreglado método shuffle para ocultar strings. Cuidado con las combinaciones, duplica el tamaño de las strings. 
* Detectados problemas en algunas funciones hardcodeadas (se depurará en la siguiente versión). 


##Changelog 5

* Arregladas las funciones hardcodeadas (junto con la adición de bloques aleatorios pueden darse situaciones que corrompan el script, volver a ofuscar o reducir el número de funciones hardcodeadas).
* Error Unable to parse line, se soluciona volviendo a ejecutar el script ofuscado. 
* Arreglado bug al ocultar parámetros de funciones hardcodeadas (ahora no se ocultan en estas funciones). 
* Algunos problemas se solucionan por la profundidad de ofuscado de números (recomendado entre 1 y 2 o entre 1 y 1).
* Realizadas pruebas con más scripts (los resultados han sido muuy buenos).  
* Compilación automática de los scripts con Aut2Exe y posibilidad de cambiar parámetros de compilación en config.ini.
* Mejorado el procesamiento de parámetros.
