# ProyectoC_Astrid_jimenez
proyecto del curso de programacion bajo plataformas abiertas: Modelo del sistema solar de Kepler
UNIVERSIDAD DE COSTA RICA
ESCUELA DE INGENIERÍA ELÉCTRICA 
PROGRAMACIÓN BAJO PLATAFORMAS ABIERTAS




PROYECTO FINAL
MODELO DEL SISTEMA SOLAR




ALUMNA:
ASTRID JIMÉNEZ HERNÁNDEZ
B63623



PROFESOR:
JUAN CARLOS COTO 




FECHA 
LUNES 26 DE JUN. DE 23
 
INTRODUCCIÓN
En este proyecto, aplicaremos lo que hemos aprendido en el curso al desarrollar un programa que modele un sistema solar. Utilizaremos el lenguaje de programación C y crearemos un proyecto para configurar el sistema y hacer consultas sobre las posiciones de los objetos celestes en diferentes momentos.
El programa leerá un archivo de configuración con información sobre los objetos del sistema solar, como planetas y estrellas. A partir de estos datos, calcularemos las posiciones de los objetos en función del tiempo utilizando las leyes de Kepler.
El programa generará un archivo de respuestas donde se registrarán los resultados de las consultas, incluyendo las coordenadas de los objetos en el tiempo especificado.
Con este proyecto, pondremos en práctica nuestros conocimientos sobre el modelo de Kepler y su aplicación en la simulación de órbitas planetarias. También demostraremos nuestras habilidades de programación en C, especialmente en el manejo de archivos y procesamiento de datos.
En el informe final, documentaremos nuestros hallazgos, los pasos seguidos y los desafíos enfrentados durante el desarrollo del programa. Este proyecto nos ayudará a consolidar nuestros conocimientos y demostrar nuestra capacidad para crear aplicaciones prácticas basadas en la teoría aprendida.
 
TRASFONDO
EL programa nos permite explorar y comprender mejor cómo funcionan las órbitas de los planetas y otros cuerpos celestes. Usando el modelo de Kepler, el cual establece tres leyes que describen el movimiento de los planetas y otros objetos en nuestro sistema solar.
Para simular las órbitas en nuestro programa, hemos utilizado el modelo de Kepler como base. Este modelo se basa en las siguientes leyes:
	Primera Ley de Kepler (Ley de las órbitas): Los planetas describen órbitas elípticas alrededor del Sol. El Sol ocupa uno de los focos de la elipse.
	Segunda Ley de Kepler (Ley de las áreas): El radio vector que une al planeta con el Sol barre áreas iguales en tiempos iguales. Esto implica que los planetas se mueven más rápido cuando están más cerca del Sol y más lento cuando están más lejos.
	Tercera Ley de Kepler (Ley de los periodos): El cuadrado del período orbital de un planeta es proporcional al cubo de la longitud del semieje mayor de su órbita. Esta ley establece una relación matemática entre el período orbital y la distancia media del planeta al Sol. (Peralta & Calles, 2003)
Utilizando estas leyes, el programa genera las órbitas de los planetas y otros objetos celestes en el sistema solar. Calculamos las posiciones de los objetos en función del tiempo, teniendo en cuenta sus masas, las posiciones de perihelio y afelio, y las leyes de Kepler. Esto nos permite simular con precisión las trayectorias de los planetas en su movimiento alrededor del Sol.
 
Diseño general
Librerías: 
El programa inicia incluyendo las librerías necesarias para ejecutar el programa:
 

	Stdio.h: Librería de entrada y salida de datos
	Stdlib.h: Realiza operaciones relacionadas con la memoria, la conversión de tipos de datos, además, nos permite usar comando como ‘atof’
	String.h: Para realizar operaciones con cadenas de caracteres y usar comando como ‘strcpy” para copiar cadenas en otras variables.
	Math.h: Para realizar funciones matemáticas.
Estructuras: 
Luego, se definieron las estructuras necesarias para formar el programa, como el objeto, en este caso, el cuerpo celeste, con las especificaciones de los tipos de datos:
 

También se definió la estructura de la consulta, que tiene como elementos el ID del objeto que se va a consultar, el ID de la consulta y el tiempo que se tomará como consulta
Funciones: 
La función ‘procesarLinea’, es la encargada de recopilar la información del modelo, se usa la variable ‘token’ para poder separar los elementos por medio de comas con el comando ‘strtok’, se asignan los elementos tipo char y se les copia la cadena tomada por la variable token. 
 

Dentro de esta función, se le asignan los miembros a la estructura ‘objeto’ y se usa el comando ‘atof’ para convertir el tipo de ‘char’ a ‘double’.
 

Luego se usan punteros para poder modificarlo directamente en la función, tanto para los objetos y para las consultas.
En la función ‘calcularPosicion’ se usa la fórmula: 
√(〖(objeto*afelioX-objeto*perihelioX)〗^2+〖(objeto*afelioY-objeto*perihelioY)〗^2 )

Para la posición X se usó la fórmula: 
Objeto.InicioX+{(Objeto.afelioX-Objeto.inicioX)*Tiempo/Periodo}
Para la posición Y se usó la fórmula: 
Objeto.InicioY+{(Objeto.afelioY-Objeto.inicioY)*Tiempo/Periodo}
La siguiente función corresponde a la ‘LiberarMemoria’ para eliminar los datos tanto de las descripciones de los objetos como de las consultas
 

Función principal 
La función principal inicia con la creación de los archivos de entrada y salida de los datos del modelo
 

Luego se agregan dos punteros más, que corresponde a las opciones que pueden estar en la enumeración, ‘descripción o consulta’, estas variables se utilizan para llevar el seguimiento del estado actual del programa mientras se leen y procesan las líneas del archivo, y para almacenar los objetos y consultas que se extraen de dicho archivo.
Una vez listo, se inicia un ciclo While que permite verificar qué parte del archivo se está trabajando, si la línea es igual a ‘Descripción’, la variable ‘tipoActual” toma el valor de descripción, del mismo modo cuando la línea corresponde a ‘consulta’:
 

Luego se utiliza un ciclo For para recorrer todas las consultas almacenadas en el arreglo ‘consultas’, Para cada consulta, se imprime la información en el archivo de salida con el comando ‘fprintf’, y se calcula la posición del objeto consultado en el tiempo indicado.
 

El programa finaliza llamando a la función ‘liberarMemoria’ tanto para las descripciones de los objetos como para las consultas, además de cerrar los archivos. 
 

 
Principales retos
Los principales retos fueron la implementación de los punteros en la parte de la estructura de ‘objeto objeto’ pues no permitía que el archivo funcionara, se recurrió a ‘chatGPT’ con el prompt “Crea un código que permita crear punteros para utilizar de manera fácil los objetos”.
Otro reto importante fue el de crear la instrucción ‘procesarLinea’, pues debía contener muchos elementos, al principio no se incluían todos y generaban error, luego era difícil manipularlos, por lo que también se le pidió a ChatGPT que ordenara la función y añadiera los archivos necesarios por medio del prompt “modifica la función ‘procesarLinea’ para que cada línea pueda leer el tipo de objeto, si es una descripción  o si es una consulta y dividirlo en los archivos desde la función”.
Además, se tuvo que investigar con detalle la funciones strcpy, strtok, atof, para poder cambiar los tipos y los valores de los datos que se requerían para añadir la información sobre los cuerpos celestes u objetos. También se recurrió a chatGPT, donde le pedí usos y ejemplos de estos comando, pues en un primer prompt, los había utilizado. 
 
Conclusiones
Al finalizar este programa en C se puede concluir lo siguiente:
	Al no contar con objetos como tales, en el lenguaje C, el uso de estructuras, resultó determinante para organizar y almacenar la información relevante, pues estas estructuras nos permiten agrupar datos relacionados y facilitan su manipulación.
	El proyecto utiliza archivos de entrada y salida para leer y escribir datos. Se emplean las funciones como ‘fprintf’ que es diferente al ‘’printf’ que imprime en la consola. 
	El proyecto hace uso de punteros para almacenar y manipular dinámicamente los arreglos de objetos y consultas. Los punteros permiten la asignación y realocación de memoria durante la ejecución del programa, lo que facilita la gestión de la memoria y permite trabajar con estructuras de datos de tamaño variable.
	Además, el proyecto muestra cómo realizar operaciones con los datos almacenados en las estructuras y cómo aplicar cálculos y funciones para obtener resultados deseados.
 
Bibliografía
Peralta, J. A., & Calles, A. &. (2003). El análisis de Fourier de las trayectorias planetarias y el modelo copernicano del sistema solar. Revista mexicana de física, 49(3), 283-289.

