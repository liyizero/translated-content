---
title: Una reintroducción a JavaScript (Tutorial de JS)
slug: Web/JavaScript/A_re-introduction_to_JavaScript
tags:
  - Aprender
  - Guía
  - Intermedio
  - Intro
  - JavaScript
  - Tutorial
  - introducción
translation_of: Web/JavaScript/A_re-introduction_to_JavaScript
original_slug: Web/JavaScript/Una_re-introducción_a_JavaScript
---
<div>{{jsSidebar}}</div>


<p>¿Por qué una reintroducción? Porque {{Glossary("JavaScript")}} es conocido por ser <a href="http://crockford.com/javascript/javascript.html">el lenguaje de programación más incomprendido</a>. A menudo se le ridiculiza como un juguete, pero debajo de esa capa de engañosa simplicidad, aguardan poderosas características del lenguaje. Ahora un increíble número de aplicaciones de alto perfil utilizan JavaScript, lo cual demuestra que un conocimiento más profundo de esta tecnología es una habilidad importante para cualquier desarrollador web o móvil.</p>

<p>Es útil comenzar con una descripción general de la historia del lenguaje. JavaScript fue creado en 1995 por Brendan Eich mientras era ingeniero en Netscape. JavaScript se lanzó por primera vez con Netscape 2 a principios de 1996. Originalmente se iba a llamar LiveScript, pero se le cambió el nombre en una desafortunada decisión de marketing que intentó capitalizar la popularidad del lenguaje Java de Sun Microsystem, a pesar de que los dos tienen muy poco en común. Esto ha sido una fuente de confusión desde entonces.</p>

<p>Varios meses después, Microsoft lanzó JScript con Internet Explorer 3. Era un JavaScript prácticamente compatible. Varios meses después de eso, Netscape envió JavaScript a <a class="external" href="http://www.ecma-international.org/">Ecma International</a>, una organización europea de estándares, que resultó en la primera edición del estándar {{Glossary("ECMAScript")}} ese año. El estándar recibió una actualización significativa como <a class="external" href="http://www.ecma-international.org/publications/standards/Ecma-262.htm">ECMAScript edición 3</a> en 1999, y se ha mantenido bastante estable desde entonces. La cuarta edición fue abandonada debido a diferencias políticas sobre la complejidad del lenguaje. Muchas partes de la cuarta edición formaron la base para la edición 5 de ECMAScript, publicada en diciembre de 2009, y para la sexta edición principal del estándar, publicada en junio de 2015.</p>

<div class="note">
<p>Debido a que es más familiar, nos referiremos a ECMAScript como "JavaScript" de ahora en adelante.</p>
</div>

<p>A diferencia de la mayoría de los lenguajes de programación, el lenguaje JavaScript no tiene un concepto de entrada o salida. Está diseñado para ejecutarse como un lenguaje de <code>scripting</code> en un entorno hospedado, y depende del entorno para proporcionar los mecanismos para comunicarse con el mundo exterior. El entorno de alojamiento más común es el navegador, pero también se pueden encontrar intérpretes de JavaScript en una gran lista de otros lugares, incluidos Adobe Acrobat, Adobe Photoshop, imágenes SVG, el motor de widgets de Yahoo, entornos de lado del servidor como <a href="http://nodejs.org/">Node.js</a>, bases de datos NoSQL como <a href="http://couchdb.apache.org/">Apache CouchDB</a> de código abierto, computadoras integradas, entornos de escritorio completos como <a href="http://www.gnome.org/">GNOME</a> (una de las IGU —<em>Interfaz Gráfica de Usuario</em>— más populares para sistemas operativos GNU/Linux), y otros.</p>

<h2 id="Información_general">Información general</h2>

<p>JavaScript es un lenguaje dinámico múltiparadigma con tipos y operadores, objetos estándar integrados y métodos. Su sintaxis se basa en los lenguajes Java y C — muchas estructuras de esos lenguajes también se aplican a JavaScript. JavaScript admite la programación orientada a objetos con prototipos de objetos, en lugar de clases (consulta más información sobre {{jsxref("Inheritance_and_the_prototype_chain", "herencia prototípica")}} y ES2015 {{jsxref("Reference/Classes", "clases")}}. JavaScript también admite la programación funcional — debido a que son objetos, las funciones se pueden almacenar en variables y pasarse como cualquier otro objeto.</p>

<p>Comencemos observando los componentes básicos de cualquier lenguaje: los tipos. Los programas JavaScript manipulan valores, y todos esos valores pertenecen a un tipo. Los tipos de JavaScript son:</p>

<ul>
 <li>{{jsxref("Number", "Números")}}</li>
 <li>{{jsxref("String", "Cadenas de texto (Strings)")}}</li>
 <li>{{jsxref("Boolean", "Booleanos")}}</li>
 <li>{{jsxref("Function", "Funciones")}}</li>
 <li>{{jsxref("Object", "Objetos")}}</li>
 <li>{{jsxref("Symbol", "Símbolos")}} (nuevo en ES2015)</li>
</ul>

<p>... oh, y {{jsxref("undefined")}} y {{jsxref("null")}}, que son ... ligeramente extraños. Y {{jsxref("Array")}}, que es un tipo de objeto especial. Y {{jsxref("Date", "Fechas (Date)")}} y {{jsxref("RegExp", "Expresiones regulares (RegExp)")}}, que son objetos que obtienes de forma gratuita. Y para ser técnicamente precisos, las funciones son solo un tipo especial de objeto. Por lo tanto, el diagrama de tipos se parece más a este:</p>

<ul>
 <li>{{jsxref("Number", "Números")}}</li>
 <li>{{jsxref("String", "Cadenas de texto (Strings)")}}</li>
 <li>{{jsxref("Boolean", "Booleanos")}}</li>
 <li>{{jsxref("Symbol", "Símbolos")}} (nuevo en ES2015)</li>
 <li>{{jsxref("Object", "Objetos")}}
  <ul>
   <li>{{jsxref("Function", "Funciones")}}</li>
   <li>{{jsxref("Array")}}</li>
   <li>{{jsxref("Date")}}</li>
   <li>{{jsxref("RegExp")}}</li>
  </ul>
 </li>
 <li>{{jsxref("null")}}</li>
 <li>{{jsxref("undefined")}}</li>
</ul>

<p>Y también hay algunos tipos {{jsxref("Error")}} integrados. Sin embargo, las cosas son mucho más fáciles si nos atenemos al primer diagrama, por lo que discutiremos los tipos enumerados allí por ahora.</p>

<h2 id="Números">Números</h2>

<p>Los números en JavaScript son "valores IEEE 754 de formato de 64 bits de doble precisión", de acuerdo con las especificaciones. <strong><em>No existen números enteros</em></strong> en JavaScript (excepto {{jsxref("BigInt")}}), por lo que debes tener un poco de cuidado. Ve este ejemplo:</p>

<pre class="syntaxbox notranslate">console.log(3 / 2);             // 1.5, <em>not</em> 1
console.log(Math.floor(3 / 2)); // 1</pre>

<p>Entonces, un <em>entero aparente</em> de hecho <em>implícitamente es un <code>float</code></em>.</p>

<p>Además, ten cuidado con cosas como:</p>

<pre class="brush: js notranslate">0.1 + 0.2 == 0.30000000000000004;
</pre>

<p>En la práctica, los valores enteros se tratan como enteros de 32 bits, y algunas implementaciones incluso los almacenan de esa manera hasta que se les pide que realicen una instrucción que sea válida en un Número pero no en un entero de 32 bits. Esto puede ser importante para operaciones bit a bit.</p>

<p>Se admiten los {{jsxref("Operators", "operadores", "#Operadores_aritméticos")}} estándar, incluidas la aritmética de suma, resta, módulo (o resto), etc. También hay un objeto incorporado que no mencionamos anteriormente llamado {{jsxref("Math")}} que proporciona funciones matemáticas avanzadas y constantes:</p>

<pre class="brush: js notranslate">Math.sin(3.5);
var circumference = 2 * Math.PI * r;
</pre>

<p>Puedes convertir una cadena en un número entero usando la función {{jsxref("Objetos_Globales/parseInt", "parseInt()")}} incorporada. Esta toma la base para la conversión como un segundo argumento opcional, que siempre debes proporcionar:</p>

<pre class="brush: js notranslate">parseInt('123', 10); // 123
parseInt('010', 10); // 10
</pre>

<p>En los navegadores más antiguos, se supone que las cadenas que comienzan con un "0" están en octal (raíz 8), pero este no ha sido el caso desde 2013 más o menos. A menos que estés seguro de tu formato de cadena, puedes obtener resultados sorprendentes en esos navegadores más antiguos:</p>

<pre class="brush: js notranslate">parseInt('010');  //  8
parseInt('0x10'); // 16
</pre>

<p>Aquí, vemos que la función {{jsxref("Objetos_Globales/parseInt", "parseInt()")}} trata la primera cadena como octal debido al 0 inicial, y la segunda cadena como hexadecimal debido al "0x" inicial. La <em>notación hexadecimal todavía está en su lugar</em>; solo se ha eliminado el octal.</p>

<p>Si deseas convertir un número binario en un entero, simplemente cambia la base:</p>

<pre class="brush: js notranslate">parseInt('11', 2); // 3
</pre>

<p>De manera similar, puedes analizar números de coma flotante utilizando la función incorporada {{jsxref("Objetos_Globales/parseFloat", "parseFloat()")}}. A diferencia de su primo {{jsxref("Objetos_Globales/parseInt", "parseInt()")}}, <code>parseFloat()</code> siempre usa base 10.</p>

<p>También puedes utilizar el operador <code>+</code> unario para convertir valores en números:</p>

<pre class="brush: js notranslate">+ '42';   // 42
+ '010';  // 10
+ '0x10'; // 16
</pre>

<p>Se devuelve un valor especial llamado {{jsxref("NaN")}} (abreviatura de "Not a Number" o "No es un número") si la cadena no es numérica:</p>

<pre class="brush: js notranslate">parseInt('hello', 10); // NaN
</pre>

<p><code>NaN</code> es tóxico: si lo proporcionas como operando para cualquier operación matemática, el resultado también será <code>NaN</code>:</p>

<pre class="brush: js notranslate">NaN + 5; // NaN
</pre>

<p>Puedes probar si un valor es <code>NaN</code> utilizando la función incorporada {{jsxref("Objetos_Globales/isNaN", "isNaN()")}}:</p>

<pre class="brush: js notranslate">isNaN(NaN); // true
</pre>

<p>JavaScript también tiene los valores especiales {{jsxref("Infinity")}} e <code>-Infinity</code>:</p>

<pre class="brush: js notranslate"> 1 / 0; //  Infinity
-1 / 0; // -Infinity
</pre>

<p>Puedes probar los valores <code>Infinity</code>, <code>-Infinity</code> y <code>NaN</code> utilizando la función integrada {{jsxref("Objetos_Globales/isFinite", "isFinite()")}}:</p>

<pre class="brush: js notranslate">isFinite(1 / 0); // false
isFinite(-Infinity); // false
isFinite(NaN); // false
</pre>

<div class="note">Las funciones {{jsxref("Objetos_Globales/parseInt", "parseInt()")}} y {{jsxref("Objetos_Globales/parseFloat", "parseFloat()")}} analizan una cadena hasta que alcancen un caracter que no es válido para el formato de número especificado, luego devuelve el número analizado hasta ese punto. Sin embargo, el operador "+" simplemente convierte la cadena a <code>NaN</code> si contiene un caracter no válido. Intenta analizar la cadena "10.2abc" con cada método tú mismo en la consola y comprenderás mejor las diferencias.</div>

<h2 id="Strings">Strings</h2>

<p>Las cadenas en JavaScript son secuencias de <a href="/es/docs/Web/JavaScript/Guide/Values,_variables,_and_literals#Unicode">caracteres Unicode</a>. Esta debería ser una buena noticia para cualquiera que haya tenido que lidiar con la internacionalización. Exactamente, son secuencias de unidades de código UTF-16; cada unidad de código está representada por un número de 16 bits. Cada caracter Unicode está representado por 1 o 2 unidades de código.</p>

<p>Si deseas representar un solo caracter, simplemente usa una cadena que consta de ese único caracter.</p>

<p>Para encontrar la longitud de una cadena (en unidades de código), accede a su propiedad {{jsxref("Objetos_Globales/String/length", "lenght")}}:</p>

<pre class="brush: js notranslate">'hello'.length; // 5
</pre>

<p>¡Aquí está nuestra primer pincelada con objetos JavaScript! ¿Mencionamos que también puedes usar cadenas como {{jsxref("Object", "objectos", "", 1)}}? También tienen {{jsxref("String", "métodos", "#Métodos", 1)}} que te permiten manipular la cadena y acceder a información sobre la cadena:</p>

<pre class="brush: js notranslate">'hello'.charAt(0); // "h"
'hello, world'.replace('world', 'mars'); // "hello, mars"
'hello'.toUpperCase(); // "HELLO"
</pre>

<h2 id="Otros_tipos">Otros tipos</h2>

<p>JavaScript distingue entre {{jsxref("null")}}, que es un valor que indica un no valor deliberado (y solo se puede acceder a él mediante la palabra clave <code>null</code>), y {{jsxref("undefined")}}, que es un valor de tipo <code>undefined</code> que indica una variable no iniciada es decir, que aún no se le ha asignado un valor. Hablaremos de variables más adelante, pero en JavaScript es posible declarar una variable sin asignarle un valor. Si hace esto, el tipo de la variable es <code>undefined</code>. <code>undefined</code> en realidad es una constante.</p>

<p>JavaScript tiene un tipo booleano, con valores posibles <code>true</code> y <code>false</code> (ambos son palabras clave). Cualquier valor se puede convertir a booleano de acuerdo con las siguientes reglas:</p>

<ol>
 <li><code>false</code>, <code>0</code>, cadenas vacías (<code>""</code>), <code>NaN</code>, <code>null</code>, y <code>undefined</code> todos se vuelven <code>false.</code></li>
 <li>Todos los demás valores se vuelven <code>true.</code></li>
</ol>

<p>Puedes realizar esta conversión explícitamente utilizando la función <code>Boolean()</code>:</p>

<pre class="brush: js notranslate">Boolean('');  // false
Boolean(234); // true
</pre>

<p>Sin embargo, esto rara vez es necesario, ya que JavaScript realizará silenciosamente esta conversión cuando espera un booleano, como en una declaración <code>if</code> (ve más adelante). Por esta razón, a veces hablamos simplemente de "valores verdaderos" y "valores falsos", es decir, valores que se convierten en <code>true</code> y <code>false</code>, respectivamente, cuando se convierten en booleanos. Alternativamente, estos valores se pueden llamar "veracidad" y "falsedad", respectivamente.</p>

<p>Operaciones booleanas como <code>&amp;&amp;</code> (<em>and</em> lógico), <code>||</code> (<em>or</em> lógico) y <code>!</code> (<em>not</em> lógico) son compatibles; ve más adelante.</p>

<h2 id="Variables">Variables</h2>

<p>Las nuevas variables en JavaScript se declaran utilizando una de tres palabras clave: {{jsxref("Sentencias/let", "let")}}, {{jsxref("Sentencias/const", "const")}} o {{jsxref("Sentencias/var", "var")}}.<br>
 <br>
 <strong><code>let</code></strong> te permite declarar variables a nivel de bloque. La variable declarada está disponible en el <em>bloque</em> en el que está incluida.</p>

<pre class="brush: js notranslate">let a;
let name = 'Simon';
</pre>

<p>El siguiente es un ejemplo de alcance con una variable declarada con <code><strong>let</strong></code>:</p>

<pre class="brush: js notranslate">// myLetVariable *no* es visible aquí

for (let myLetVariable = 0; myLetVariable &lt; 5; myLetVariable++) {
  // myLetVariable solo es visible aquí
}

// myLetVariable *no* es visible aquí

</pre>

<p><code><strong>const</strong></code> te permite declarar variables cuyos valores pretendes nunca cambiar. La variable está disponible en el <em>bloque</em> en el que se declara.</p>

<pre class="brush: js notranslate">const Pi = 3.14; // establece la variable Pi
Pi = 1; // arrojará un error porque no puede cambiar una variable constante.</pre>

<p><br>
 <code><strong>var</strong></code> es la palabra clave declarativa más común. No tiene las restricciones que tienen las otras dos palabras clave. Esto se debe a que tradicionalmente era la única forma de declarar una variable en JavaScript. Una variable declarada con la palabra clave <strong><code>var</code></strong> está disponible en la <em>función</em> en la que se declara.</p>

<pre class="brush: js notranslate">var a;
var name = 'Simon';</pre>

<p>Un ejemplo de ámbito con una variable declarada con <strong><code>var</code>:</strong></p>

<pre class="brush: js notranslate">// myVarVariable *es* visible aquí

for (var myVarVariable = 0; myVarVariable &lt; 5; myVarVariable++) {
  // myVarVariable es visible para toda la función
}

// myVarVariable *es* visible aquí
</pre>

<p>Si declaras una variable sin asignarle ningún valor, su tipo es <code>undefined</code>.</p>

<p>Una diferencia importante entre JavaScript y otros lenguajes como Java es que en JavaScript, los bloques no tienen alcance; solo las funciones tienen alcance. Entonces, si una variable se define usando <code>var</code> en una declaración compuesta (por ejemplo, dentro de una estructura de control <code>if</code>), será visible para toda la función. Sin embargo, a partir de ECMAScript 2015, las declaraciones {{jsxref("Sentencias/let", "let")}} y {{jsxref("Sentencias/const", "const")}} te permiten crear variables con alcance de bloque.</p>

<h2 id="Operadores">Operadores</h2>

<p>Los operadores numéricos de JavaScript son <code>+</code>, <code>-</code>, <code>*</code>, <code>/</code> y <code>%</code> que es el operador de residuo o resto (<a href="/es/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#Remainder_%28%29">que es lo mismo que módulo</a>). Los valores se asignan usando <code>=</code>, y también hay declaraciones de asignación compuestas como <code>+=</code> y <code>-=</code>. Estas se extienden hasta <code>x = x <em>operador</em> y</code>.</p>

<pre class="brush: js notranslate">x += 5;
x = x + 5;
</pre>

<p>Puedes usar <code>++</code> y <code>--</code> para incrementar y disminuir respectivamente. Estos se pueden utilizar como operadores prefijos o sufijos.</p>

<p>El <a href="/es/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#Addition" title="/es/JavaScript/Reference/Operators/String_Operators">operador <code>+</code></a> también hace concatenación de cadenas:</p>

<pre class="brush: js notranslate">'hello' + ' world'; // "hello world"
</pre>

<p>Si agregas una cadena a un número (u otro valor), todo se convierte primero en cadena. Esto podría hacerte tropezar:</p>

<pre class="brush: js notranslate">'3' + 4 + 5;  // "345"
 3 + 4 + '5'; // "75"
</pre>

<p>Agregar una cadena vacía a algo es una forma útil de convertirla en cadena.</p>

<p><a href="/es/docs/Web/JavaScript/Reference/Operators/Comparison_Operators" title="/es/JavaScript/Reference/Operators/Comparison_Operators">Se pueden realizar comparaciones</a> en JavaScript utilizando <code>&lt;</code>, <code>&gt;</code>, <code>&lt;=</code> y <code>&gt;=</code>. Estas funcionan tanto para cadenas como para números. La igualdad es un poco menos sencilla. El operador doble-igual realiza la coerción de tipos si le das diferentes tipos, con resultados a veces interesantes:</p>

<pre class="brush: js notranslate">123 == '123'; // true
1 == true; // true
</pre>

<p>Para evitar la coerción de tipos, usa el operador triple-igual:</p>

<pre class="brush: js notranslate">123 === '123'; // false
1 === true;    // false
</pre>

<p>También hay operadores <code>!=</code> y <code>!==</code>.</p>

<p>JavaScript también tiene <a href="/es/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators" title="/es/JavaScript/Reference/Operators/Bitwise_Operators">operaciones bit a bit</a>. Si quieres usarlas, ahí están.</p>

<h2 id="Estructuras_de_control">Estructuras de control</h2>

<p>JavaScript tiene un conjunto de estructuras de control similar a otros lenguajes de la familia C. Las declaraciones condicionales son compatibles con <code>if</code> y <code>else</code>; las puedes encadenarlas si lo deseas:</p>

<pre class="brush: js notranslate">var name = 'kittens';
if (name == 'puppies') {
  name += ' woof';
} else if (name == 'kittens') {
  name += ' meow';
} else {
  name += '!';
}
name == 'kittens meow';
</pre>

<p>JavaScript tiene bucles <code>while</code> y bucles <code>do-while</code>. El primero es bueno para bucles básicos; el segundo bucle para donde deseas asegurarte de que el cuerpo del bucle se ejecute por lo menos una vez:</p>

<pre class="brush: js notranslate">while (true) {
  // ¡un bucle infinito!
}

var input;
do {
  input = get_input();
} while (inputIsNotValid(input));
</pre>

<p>El <a href="/es/docs/Web/JavaScript/Reference/Statements/for">bucle <code>for</code></a> de JavaScript es igual que el de C y Java: te permite proporcione la información de control para tu bucle en una sola línea.</p>

<pre class="brush: js notranslate">for (var i = 0; i &lt; 5; i++) {
  // Se ejecutará 5 veces
}
</pre>

<p>JavaScript también contiene otros dos bucles <code>for</code> destacados: <a href="/en-US/docs/Web/JavaScript/Reference/Statements/for...of"><code>for</code>...<code>of</code></a></p>

<pre class="brush: js notranslate">for (let value of array) {
  // haz algo con valor
}
</pre>

<p>y <a href="/es/docs/Web/JavaScript/Reference/Statements/for...in"><code>for</code>...<code>in</code></a>:</p>

<pre class="brush: js notranslate">for (let property in object) {
  // hacer algo con la propiedad del objeto
}
</pre>

<p>Los operadores <code>&amp;&amp;</code> y <code>||</code> utilizan evaluación de cortocircuito, lo cual significa que la evaluación del segundo operando depende del valor del primero. Esto es útil para verificar objetos nulos antes de acceder a sus atributos:</p>

<pre class="brush: js notranslate">var name = o &amp;&amp; o.getName();
</pre>

<p>O para almacenar en caché los valores (cuando los valores falsos no son válidos):</p>

<pre class="brush: js notranslate">var name = cachedName || (cachedName = getName());
</pre>

<p>JavaScript tiene un operador ternario para expresiones condicionales:</p>

<pre class="brush: js notranslate">var allowed = (age &gt; 18) ? 'yes' : 'no';
</pre>

<p>La instrucción <code>switch</code> se puede usar para múltiples ramas según un número o cadena:</p>

<pre class="brush: js notranslate">switch (action) {
  case 'draw':
    drawIt();
    break;
  case 'eat':
    eatIt();
    break;
  default:
    doNothing();
}
</pre>

<p>Si no agregas una instrucción <code>break</code>, la ejecución "caerá" al siguiente nivel. Esto muy rara vez es lo que deseas; de hecho, vale la pena etiquetar específicamente la caída deliberada con un comentario si realmente lo pretendías para ayudar a la depuración:</p>

<pre class="brush: js notranslate">switch (a) {
  case 1: // caída deliberada
  case 2:
    eatIt();
    break;
  default:
    doNothing();
}
</pre>

<p>La cláusula <code>default</code> es opcional. Puedes tener expresiones tanto en la parte del switch como en los casos si lo deseas; las comparaciones tienen lugar entre los dos utilizando el operador <code>===</code>:</p>

<pre class="brush: js notranslate">switch (1 + 3) {
  case 2 + 2:
    yay();
    break;
  default:
    neverhappens();
}
</pre>

<h2 id="Objetos">Objetos</h2>

<p>Los objetos de JavaScript se pueden considerar como simples colecciones de pares nombre-valor. Como tal, son similares a:</p>

<ul>
 <li>Diccionarios en Python.</li>
 <li>Hashes en Perl y Ruby.</li>
 <li>Tablas hash en C y C++.</li>
 <li>HashMaps en Java.</li>
 <li>Arreglos asociativas en PHP.</li>
</ul>

<p>El hecho de que esta estructura de datos se utilice tan ampliamente es un testimonio de su versatilidad. Dado que todo (el núcleo, tipos bar) en JavaScript es un objeto, cualquier programa de JavaScript implica naturalmente una gran cantidad de búsquedas en tablas hash. ¡Qué bueno que sean tan rápidas!</p>

<p>La parte "name" es una cadena JavaScript, mientras que el valor puede ser cualquier valor de JavaScript, incluidos más objetos. Esto te permite construir estructuras de datos de complejidad arbitraria.</p>

<p>Hay dos formas básicas de crear un objeto vacío:</p>

<pre class="brush: js notranslate">var obj = new Object();
</pre>

<p>Y:</p>

<pre class="brush: js notranslate">var obj = {};
</pre>

<p>Estas son semánticamente equivalentes; la segunda se llama sintaxis literal de objeto y es más conveniente. Esta sintaxis también es el núcleo del formato JSON y se debe preferir en todo momento.</p>

<p>La sintaxis de objeto literal se puede utilizar para iniciar un objeto en su totalidad:</p>

<pre class="brush: js notranslate">var obj = {
  name: 'Carrot',
  for: 'Max', // 'for' es una palabra reservada, use '_for' en su lugar.
  details: {
    color: 'orange',
    size: 12
  }
};
</pre>

<p>El acceso a los atributos se puede encadenar:</p>

<pre class="brush: js notranslate">obj.details.color; // orange
obj['details']['size']; // 12
</pre>

<p>El siguiente ejemplo crea un prototipo de objeto (<code>Person</code>) y una instancia de ese prototipo (<code>you</code>).</p>

<pre class="brush: js notranslate">function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Define un objeto
var you = new Person('You', 24);
// Estamos creando una nueva persona llamada "You" de 24 años.

</pre>

<p><strong>Una vez creado</strong>, se puede volver a acceder a las propiedades de un objeto de dos formas:</p>

<pre class="brush: js notranslate">// notación de puntos
obj.name = 'Simon';
var name = obj.name;
</pre>

<p>Y...</p>

<pre class="brush: js notranslate">// notación de corchetes
obj['name'] = 'Simon';
var name = obj['name'];
// puedes usar una variable para definir una clave
var user = prompt('¿cuál es su clave?')
obj[user] = prompt('¿cuál es su valor?')
</pre>

<p>Estas también son semánticamente equivalentes. El segundo método tiene la ventaja de que el nombre de la propiedad se proporciona como una cadena, lo cual significa que se puede calcular en tiempo de ejecución. Sin embargo, el uso de este método evita que se apliquen algunas optimizaciones de minificación y del motor de JavaScript. También se puede utilizar para establecer y obtener propiedades con nombres <a href="/es/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords" title="/es/JavaScript/Reference/Reserved_Words">palabras reservadas</a>:</p>

<pre class="brush: js notranslate">obj.for = 'Simon'; // Error de sintaxis, porque 'for' es una palabra reservada
obj['for'] = 'Simon'; // trabaja bien
</pre>

<div class="note">
<p>A partir de ECMAScript 5, las palabras reservadas se pueden utilizar como nombres de propiedad de objeto "en bruto". Esto significa que no necesitan "vestirse" entre comillas al definir objeto literales. Consulta la <a href="http://es5.github.io/#x7.6.1"> especificación</a> de ES5.</p>
</div>

<p>Para obtener más información sobre objetos y prototipos, consulta {{jsxref("Objetos_Globales/Object/prototype", "Object.prototype")}}. Para obtener una explicación de los prototipos de objetos y las cadenas de prototipos de objetos, consulta <a href="/es/docs/Web/JavaScript/Inheritance_and_the_prototype_chain">Herencia y la cadena de prototipos</a>.</p>

<div class="note">
<p>A partir de ECMAScript 2015, las claves de objeto se pueden definir mediante la variable en notación de corchetes al crearlas. <code>{[phoneType]: 12345}</code> es posible en lugar de solo <code>var userPhone = {}; userPhone[phoneType] = 12345</code>.</p>
</div>

<h2 id="Arreglos">Arreglos</h2>

<p>Los arreglos en JavaScript en son realidad un tipo especial de objeto. Funcionan de manera muy parecida a los objetos normales (las propiedades numéricas se pueden acceder naturalmente solo usando la sintaxis <code>[]</code>) pero tienen una propiedad mágica llamada '<code>length</code>'. Este siempre es uno más que el índice más alto de el arreglo.</p>

<p>Una forma de crear arreglos es la siguiente:</p>

<pre class="brush: js notranslate">var a = new Array();
a[0] = 'dog';
a[1] = 'cat';
a[2] = 'hen';
a.length; // 3
</pre>

<p>Una notación más conveniente es usar un arreglo literal:</p>

<pre class="brush: js notranslate">var a = ['dog', 'cat', 'hen'];
a.length; // 3
</pre>

<p>Ten en cuenta que <code>array.length</code> no necesariamente es el número de elementos del arreglo. Considera lo siguiente:</p>

<pre class="brush: js notranslate">var a = ['dog', 'cat', 'hen'];
a[100] = 'fox';
a.length; // 101
</pre>

<p>Recuerda — la longitud de el arreglo es uno más que el índice más alto.</p>

<p>Si consultas un índice de arreglo que no existe, obtendrás un valor de <code>undefined</code>:</p>

<pre class="brush: js notranslate">typeof a[90]; // undefined
</pre>

<p>Si tienes en cuenta lo anterior sobre <code>[]</code> y <code>length</code>, puedes iterar sobre un arreglo utilizando el siguiente bucle <code>for</code>:</p>

<pre class="brush: js notranslate">for (var i = 0; i &lt; a.length; i++) {
  // Haz algo con a[i]
}
</pre>

<p>ES2015 introdujo el bucle más conciso <a href="/es/docs/Web/JavaScript/Reference/Statements/for...of"><code>for</code>...<code>of</code></a> para objetos iterables como arreglos:</p>

<pre class="brush:js notranslate">for (const currentValue of a) {
  // Haz algo con currentValue
}</pre>

<p>También puedes iterar sobre un arreglo utilizando el bucle <a href="/es/docs/Web/JavaScript/Reference/Statements/for...in" title="/es/JavaScript/Reference/Statements/for...in"><code>for</code>...<code>in</code></a>, sin embargo, este no itera sobre los elementos del arreglo, sino los índices del arreglo. Además, si alguien agrega nuevas propiedades a <code>Array.prototype</code>, también serán iteradas por dicho bucle. Por lo tanto, este tipo de bucle no se recomienda para arreglos.</p>

<p>Otra forma de iterar sobre un arreglo que se agregó con ECMAScript 5 es {{jsxref("Objetos_Globales/Array/forEach", "arr.forEach()")}}:</p>

<pre class="brush: js notranslate">['dog', 'cat', 'hen'].forEach(function(currentValue, index, array) {
  // Hacer algo con currentValue o array[index]
});
</pre>

<p>Si deseas agregar un elemento a un arreglo, simplemente hazlo así:</p>

<pre class="brush: js notranslate">a.push(item);</pre>

<p>Los arreglos vienen con varios métodos. Consulta también la {{jsxref("Objetos_Globales/Array", "documentación completa para métodos de arreglo")}}.</p>

<table>
 <thead>
  <tr>
   <th scope="col">Nombre del método</th>
   <th scope="col">Descripción</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>a.toString()</code></td>
   <td>Devuelve una cadena con el <code>toString()</code> de cada elemento separado por comas.</td>
  </tr>
  <tr>
   <td><code>a.toLocaleString()</code></td>
   <td>Devuelve una cadena con el <code>toLocaleString()</code> de cada elemento separado por comas.</td>
  </tr>
  <tr>
   <td><code>a.concat(item1[, item2[, ...[, itemN]]])</code></td>
   <td>Devuelve un nuevo arreglo con los elementos agregados.</td>
  </tr>
  <tr>
   <td><code>a.join(sep)</code></td>
   <td>Convierte el arreglo en una cadena, con valores delimitados por el parámetro <code>sep</code></td>
  </tr>
  <tr>
   <td><code>a.pop()</code></td>
   <td>Elimina y devuelve el último elemento.</td>
  </tr>
  <tr>
   <td><code>a.push(item1, ..., itemN)</code></td>
   <td>Agrega elementos al final del arreglo.</td>
  </tr>
  <tr>
   <td><code>a.shift()</code></td>
   <td>Elimina y devuelve el primer elemento.</td>
  </tr>
  <tr>
   <td><code>a.unshift(item1[, item2[, ...[, itemN]]])</code></td>
   <td>Añade elementos al inicio del arreglo.</td>
  </tr>
  <tr>
   <td><code>a.slice(start[, end])</code></td>
   <td>Devuelve un subarreglo.</td>
  </tr>
  <tr>
   <td><code>a.sort([cmpfn])</code></td>
   <td>Toma una función de comparación opcional.</td>
  </tr>
  <tr>
   <td><code>a.splice(start, delcount[, item1[, ...[, itemN]]])</code></td>
   <td>Te permite modificar un arreglo eliminando una sección y reemplazándola con más elementos.</td>
  </tr>
  <tr>
   <td><code>a.reverse()</code></td>
   <td>Invierte el arreglo.</td>
  </tr>
 </tbody>
</table>

<h2 id="Funciones">Funciones</h2>

<p>Junto con los objetos, las funciones son el componente principal para comprender JavaScript. La función más básica no podría ser mucho más sencilla:</p>

<pre class="brush: js notranslate">function add(x, y) {
  var total = x + y;
  return total;
}
</pre>

<p>Esto demuestra una función básica. Una función de JavaScript puede tomar 0 o más parámetros con nombre. El cuerpo de la función puede contener tantas declaraciones como desees y puedes declarar tus propias variables que son locales para esa función. La declaración <code>return</code> se puede usar para devolver un valor en cualquier momento, terminando la función. Si no se utiliza una declaración <code>return</code> (o <code>return</code> vacía sin valor), JavaScript devuelve <code>undefined</code>.</p>

<p>Los parámetros nombrados resultan ser más intuitivos que cualquier otra cosa. Puedes llamar a una función sin pasar los parámetros que espera, en cuyo caso se establecerán en <code>undefined</code>.</p>

<pre class="brush: js notranslate">add(); // NaN
// No puedes realizar sumas en undefined
</pre>

<p>También puedes pasar más argumentos de los que espera la función:</p>

<pre class="brush: js notranslate">add(2, 3, 4); // 5
// sumó los dos primeros; el 4 fue ignorado
</pre>

<p>Eso puede parecer un poco tonto, pero las funciones tienen acceso a una variable adicional dentro de su cuerpo llamada <a href="/es/docs/Web/JavaScript/Reference/Functions/argument" title="/es/JavaScript/Reference/Functions_and_function_scope/arguments"><code>argumentos</code></a>, que es un objeto tipo arreglo que contiene todos los valores pasados a la función. Reescribamos la función de suma para tomar tantos valores como queramos:</p>

<pre class="brush: js notranslate">function add() {
  var sum = 0;
  for (var i = 0, j = arguments.length; i &lt; j; i++) {
    sum += arguments[i];
  }
  return sum;
}

add(2, 3, 4, 5); // 14
</pre>

<p>Sin embargo, eso no es más útil que escribir <code>2 + 3 + 4 + 5</code>. Creemos una función de promedio:</p>

<pre class="brush: js notranslate">function avg() {
  var sum = 0;
  for (var i = 0, j = arguments.length; i &lt; j; i++) {
    sum += arguments[i];
  }
  return sum / arguments.length;
}

avg(2, 3, 4, 5); // 3.5
</pre>

<p>Esta es bastante útil, pero parece un poco detallada. Para reducir un poco más este código, podemos considerar la sustitución del uso del arreglo de argumentos a través de la <a href="/es/docs/Web/JavaScript/Reference/Functions/rest_parameters">sintaxis del parámetro <code>Rest</code></a>. De esta manera, podemos pasar cualquier número de argumentos a la función manteniendo nuestro código mínimo. El <strong>operador de parámetro <code>rest</code></strong> se usa en listas de parámetros de función con el formato: <strong>...variable</strong> e incluirá dentro de esa variable la lista completa de argumentos no capturados a los que se llamó la función. <code>with</code>. También reemplazaremos el bucle <strong>for</strong> con un bucle <strong>for...of</strong> para devolver los valores dentro de nuestra variable.</p>

<pre class="brush: js notranslate">function avg(...args) {
  var sum = 0;
  for (let value of args) {
    sum += value;
  }
  return sum / args.length;
}

avg(2, 3, 4, 5); // 3.5
</pre>

<div class="note">En el código anterior, la variable <strong>args</strong> contiene todos los valores que se pasaron a la función.<br>
<br>
Es importante tener en cuenta que dondequiera que se coloque el operador de parámetro <code>rest</code> en una declaración de función, almacenará todos los argumentos <em>después</em> de su declaración, pero no antes. <em>es decir, function</em> <em>avg(</em><strong>firstValue, </strong><em>...args)</em> almacenará el primer valor pasado a la función en la variable <strong>firstValue</strong> y los argumentos restantes en <strong>args</strong>. Esa es otra característica útil del lenguaje, pero nos lleva a un nuevo problema. La función <code>avg() </code> toma una lista de argumentos separados por comas, pero ¿qué sucede si deseas encontrar el promedio de un arreglo? Simplemente, podrías reescribir la función de la siguiente manera:</div>

<pre class="brush: js notranslate">function avgArray(arr) {
  var sum = 0;
  for (var i = 0, j = arr.length; i &lt; j; i++) {
    sum += arr[i];
  }
  return sum / arr.length;
}

avgArray([2, 3, 4, 5]); // 3.5
</pre>

<p>Pero sería bueno poder reutilizar la función que ya hemos creado. Afortunadamente, JavaScript te permite llamar a una función con un arreglo arbitrario de argumentos, usando el método {{jsxref("Function.apply", "apply()")}} de cualquier objeto función.</p>

<pre class="brush: js notranslate">avg.apply(null, [2, 3, 4, 5]); // 3.5
</pre>

<p>El segundo argumento de <code>apply()</code> es el arreglo que se utilizará como <code>arguments</code>; el primero se explicará más adelante. Esto enfatiza el hecho de que las funciones también son objetos.</p>

<div class="note">
<p>Puedes lograr el mismo resultado utilizando el <a href="/es/docs/Web/JavaScript/Reference/Operators/Spread_operator">operador de propagación</a> en la llamada de función.</p>

<p>Por ejemplo: <code>avg(...numbers) </code></p>
</div>

<p>JavaScript te permite crear funciones anónimas.</p>

<pre class="brush: js notranslate">var avg = function() {
  var sum = 0;
  for (var i = 0, j = arguments.length; i &lt; j; i++) {
    sum += arguments[i];
  }
  return sum / arguments.length;
};
</pre>

<p>Esto semánticamente es equivalente a la forma <code>function avg()</code>. Es extremadamente poderosa, ya que te permite colocar una definición de función completa en cualquier lugar donde normalmente colocarías una expresión. Esto permite todo tipo de ingeniosos trucos. Aquí hay una forma de "ocultar" algunas variables locales — como alcance de bloque en C:</p>

<pre class="brush: js notranslate">var a = 1;
var b = 2;

(function() {
  var b = 3;
  a += b;
})();

a; // 4
b; // 2
</pre>

<p>JavaScript te permite llamar a funciones de forma recursiva. Esto es particularmente útil para tratar con estructuras de árbol, como las que se encuentran en el DOM del navegador.</p>

<pre class="brush: js notranslate">function countChars(elm) {
  if (elm.nodeType == 3) { // TEXT_NODE
    return elm.nodeValue.length;
  }
  var count = 0;
  for (var i = 0, child; child = elm.childNodes[i]; i++) {
    count += countChars(child);
  }
  return count;
}
</pre>

<p>Esto resalta un problema potencial con las funciones anónimas: ¿cómo las llama de forma recursiva si no tienen un nombre? JavaScript te permite nombrar expresiones de función para esto. Puedes utilizar {{Glossary("IIFE", "IIFE (expresiones de función invocadas inmediatamente)")}} con nombre como se muestra a continuación:</p>

<pre class="brush: js notranslate">var charsInBody = (function counter(elm) {
  if (elm.nodeType == 3) { // TEXT_NODE
    return elm.nodeValue.length;
  }
  var count = 0;
  for (var i = 0, child; child = elm.childNodes[i]; i++) {
    count += counter(child);
  }
  return count;
})(document.body);
</pre>

<p>El nombre proporcionado a una expresión de función como arriba solo está disponible para el alcance de la función. Esto permite que el motor realice más optimizaciones y da como resultado un código más legible. El nombre también aparece en el depurador y en algunos seguimientos de la pila, lo cual puede ahorrarte tiempo al depurar.</p>

<p>Ten en cuenta que las funciones de JavaScript en sí mismas son objetos, como todo lo demás en JavaScript, y puedes agregar o cambiar propiedades en ellas tal como hemos visto anteriormente en la sección Objetos.</p>

<h2 id="Objetos_personalizados">Objetos personalizados</h2>

<div class="note">Para obtener una descripción más detallada de la programación orientada a objetos en JavaScript, consulta <a href="/es/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript">Introducción a JavaScript orientado a objetos</a>.</div>

<p>En la programación clásica orientada a objetos, los objetos son colecciones de datos y métodos que operan sobre esos datos. JavaScript es un lenguaje basado en prototipos que no contiene una declaración de clase, como la encontrarías en C++ o Java (esto, a veces es confuso para los programadores acostumbrados a lenguajes con una declaración de clase). En cambio, JavaScript usa funciones como clases. Consideremos un objeto <code>person</code> con campos <code>first</code> y <code>last name</code>. Hay dos formas de mostrar el nombre: como "primero último" o como "último, primero". Usando las funciones y objetos que hemos explicado anteriormente, podríamos mostrar los datos de esta manera:</p>

<pre class="brush: js notranslate">function makePerson(first, last) {
  return {
    first: first,
    last: last
  };
}
function personFullName(person) {
  return person.first + ' ' + person.last;
}
function personFullNameReversed(person) {
  return person.last + ', ' + person.first;
}

var s = makePerson('Simon', 'Willison');
personFullName(s); // "Simon Willison"
personFullNameReversed(s); // "Willison, Simon"
</pre>

<p>Esto funciona, pero es bastante feo. Terminas con docenas de funciones en tu espacio de nombres global. Lo que realmente necesitamos es una forma de enlazar una función a un objeto. Dado que las funciones son objetos, esto es fácil:</p>

<pre class="brush: js notranslate">function makePerson(first, last) {
  return {
    first: first,
    last: last,
    fullName: function() {
      return this.first + ' ' + this.last;
    },
    fullNameReversed: function() {
      return this.last + ', ' + this.first;
    }
  };
}

var s = makePerson('Simon', 'Willison');
s.fullName(); // "Simon Willison"
s.fullNameReversed(); // "Willison, Simon"
</pre>

<p>Nota sobre la palabra clave <code><a href="/es/docs/Web/JavaScript/Reference/Operators/this" title="/es/JavaScript/Reference/Operators/this">this</a></code>. Usada dentro de una función, <code>this</code> se refiere al objeto actual. Lo que realmente significa está especificado por la forma en que llamaste a esa función. Si lo llamaste usando <a href="/es/docs/Web/JavaScript/Reference/Operators/Object_initializer#Accessing_properties" title="/es/JavaScript/Reference/Operators/Member_Operators">notación de puntos o notación de corchetes</a> en un objeto, ese objeto se convierte en <code>this</code>. Si la notación de puntos no se usó para la llamada, <code>this</code> se refiere al objeto global.</p>

<p>Ten en cuenta que <code>this</code> es una frecuente causa de errores. Por ejemplo:</p>

<pre class="brush: js notranslate">var s = makePerson('Simon', 'Willison');
var fullName = s.fullName;
fullName(); // undefined undefined
</pre>

<p>Cuando llamamos a <code>fullName()</code> solo, sin usar <code>s.fullName()</code>, <code>this</code> está vinculado al objeto global. Debido a que no hay variables globales llamadas <code>first</code> o <code>last</code> obtenemos <code>undefined</code> para cada una.</p>

<p>Podemos aprovechar la palabra clave <code>this</code> para mejorar nuestra función <code>makePerson</code>:</p>

<pre class="brush: js notranslate">function Person(first, last) {
  this.first = first;
  this.last = last;
  this.fullName = function() {
    return this.first + ' ' + this.last;
  };
  this.fullNameReversed = function() {
    return this.last + ', ' + this.first;
  };
}
var s = new Person('Simon', 'Willison');
</pre>

<p>Hemos introducido otra palabra clave: <code><a href="/es/docs/Web/JavaScript/Reference/Operators/new" title="/es/JavaScript/Reference/Operators/new">new</a></code>. <code>new</code> está fuertemente relacionado con <code>this</code>. Crea un nuevo objeto vacío y luego llama a la función especificada, con <code>this</code> configurado para ese nuevo objeto. Sin embargo, ten en cuenta que la función especificada con <code>this</code> no devuelve un valor, sino que simplemente modifica el objeto <code>this</code>. Es <code>new</code> que devuelve el objeto <code>this</code> al sitio que realiza la llamada. Las funciones que están diseñadas para ser llamadas por <code>new</code> se denominan funciones constructoras. La práctica común es poner en mayúscula estas funciones como recordatorio para llamarlas con <code>new</code>.</p>

<p>La función mejorada todavía tiene el mismo error al llamar a <code>fullName()</code> sola.</p>

<p>Nuestros objetos <code>person</code> están mejorando, pero todavía tienen algunos bordes desagradables. Cada vez que creamos un objeto <code>person</code>, estamos creando dos nuevos objetos de función dentro de él, ¿no sería mejor si este código fuera compartido?</p>

<pre class="brush: js notranslate">function personFullName() {
  return this.first + ' ' + this.last;
}
function personFullNameReversed() {
  return this.last + ', ' + this.first;
}
function Person(first, last) {
  this.first = first;
  this.last = last;
  this.fullName = personFullName;
  this.fullNameReversed = personFullNameReversed;
}
</pre>

<p>Eso es mejor: estamos creando las funciones como métodos solo una vez y asignándoles referencias dentro del constructor. ¿Podemos hacer algo mejor que eso? La respuesta es sí:</p>

<pre class="brush: js notranslate">function Person(first, last) {
  this.first = first;
  this.last = last;
}
Person.prototype.fullName = function() {
  return this.first + ' ' + this.last;
};
Person.prototype.fullNameReversed = function() {
  return this.last + ', ' + this.first;
};
</pre>

<p><code>Person.prototype</code> es un objeto compartido por todas las instancias de <code>Person</code>. Forma parte de una cadena de búsqueda (que tiene un nombre especial, "cadena de prototipos"): cada vez que intentes acceder a una propiedad de <code>Person</code> que no esté configurada, JavaScript revisará <code>Person.prototype</code> para ver si esa propiedad existe allí. Como resultado, todo lo asignado a <code>Person.prototype</code> pasa a estar disponible para todas las instancias de ese constructor a través del objeto <code>this</code>.</p>

<p>Esta es una herramienta increíblemente poderosa. JavaScript te permite modificar el prototipo de algo en cualquier momento en tu programa, lo cual significa que —en tiempo de ejecución— puedes agregar métodos adicionales a los objetos existentes:</p>

<pre class="brush: js notranslate">var s = new Person('Simon', 'Willison');
s.firstNameCaps(); // TypeError en la línea 1: s.firstNameCaps no es una función

Person.prototype.firstNameCaps = function() {
  return this.first.toUpperCase();
};
s.firstNameCaps(); // "SIMON"
</pre>

<p>Curiosamente, también puedes agregar cosas al prototipo de objetos JavaScript integrados. Agreguemos un método a <code>String</code> que devuelva esa cadena a la inversa:</p>

<pre class="brush: js notranslate">var s = 'Simon';
s.reversed(); // TypeError en la línea 1: s.reversed no es una función

String.prototype.reversed = function() {
  var r = '';
  for (var i = this.length - 1; i &gt;= 0; i--) {
    r += this[i];
  }
  return r;
};

s.reversed(); // nomiS
</pre>

<p>¡Nuestro método <code>new</code> funciona incluso con cadenas literales!</p>

<pre class="brush: js notranslate">'Esto ahora se puede revertir'.reversed(); // ritrever edeup es aroha otsE
</pre>

<p>Como se mencionó anteriormente, el prototipo forma parte de una cadena. La raíz de esa cadena es <code>Object.prototype</code>, cuyos métodos incluyen <code>toString()</code>; es este método el que se llama cuando intentas representar un objeto como una cadena. Esto es útil para depurar nuestros objetos <code>Person</code>:</p>

<pre class="brush: js notranslate">var s = new Person('Simon', 'Willison');
s.toString(); // [object Object]

Person.prototype.toString = function() {
  return '&lt;Person: ' + this.fullName() + '&gt;';
}

s.toString(); // "&lt;Person: Simon Willison&gt;"
</pre>

<p>¿Recuerda cómo <code>avg.apply()</code> tenía un primer argumento <code>null</code>? Ahora lo podemos revisar. El primer argumento de <code>apply()</code> es el objeto que se debe tratar como '<code>this</code>'. Por ejemplo, aquí hay una implementación trivial de <code>new</code>:</p>

<pre class="brush: js notranslate">function trivialNew(constructor, ...args) {
  var o = {}; // Crea un objeto
  constructor.apply(o, args);
  return o;
}
</pre>

<p>Esta no es una réplica exacta de <code>new</code> ya que no configura la cadena de prototipos (sería difícil de ilustrar). Esto no es algo que use con mucha frecuencia, pero es útil conocerlo. En este fragmento, <code>...args</code> (incluidos los puntos suspensivos) se denomina "<a href="/es/docs/Web/JavaScript/Reference/Functions/rest_parameters">argumentos rest</a>" — como su nombre indica, contiene el resto de los argumentos.</p>

<p>Llamar a...</p>

<pre class="brush: js notranslate">var bill = trivialNew(Person, 'William', 'Orange');</pre>

<p>...por tanto, casi es equivalente a</p>

<pre class="brush: js notranslate">var bill = new Person('William', 'Orange');</pre>

<p><code>apply()</code> tiene una función hermana llamada {{jsxref("Objetos_Globales/Function/call", "call()")}}, que nuevamente te permite establecer <code>this</code> pero toma una lista de argumentos expandida en lugar de un arreglo.</p>

<pre class="brush: js notranslate">function lastNameCaps() {
  return this.last.toUpperCase();
}
var s = new Person('Simon', 'Willison');
lastNameCaps.call(s);
// Es lo mismo que:
s.lastNameCaps = lastNameCaps;
s.lastNameCaps(); // WILLISON
</pre>

<h3 id="Funciones_internas">Funciones internas</h3>

<p>Las declaraciones de función de JavaScript están permitidas dentro de otras funciones. Hemos visto esto una vez antes, con la función <code>makePerson()</code> anterior. Un detalle importante de las funciones anidadas en JavaScript es que pueden acceder a las variables en el alcance de su función padre:</p>

<pre class="brush: js notranslate">function parentFunc() {
  var a = 1;

  function nestedFunc() {
    var b = 4; // parentFunc no puede usar esto
    return a + b;
  }
  return nestedFunc(); // 5
}
</pre>

<p>Esto proporciona una gran utilidad para escribir un código más fácil de mantener. Si una función llamada se basa en una o dos funciones que no son útiles para ninguna otra parte de tu código, puedes anidar esas funciones de utilidad dentro de ella. Esto mantiene baja la cantidad de funciones que están en el alcance global, lo cual siempre es bueno.</p>

<p>Esto también contrarresta el atractivo de las variables globales. Al escribir código complejo, a menudo es tentador utilizar variables globales para compartir valores entre múltiples funciones, lo que conduce a un código difícil de mantener. Las funciones anidadas pueden compartir variables en su padre, por lo que puedes usar ese mecanismo para unir funciones cuando tenga sentido sin contaminar tu espacio de nombres global — "globales locales" si lo deseas. Esta técnica se debe usar con precaución, pero es una útil habilidad.</p>

<h2 id="Cierres">Cierres</h2>

<p>Esto nos lleva a una de las abstracciones más poderosas que JavaScript tiene para ofrecer — pero potencialmente, también la más confusa. ¿Qué hace esta?</p>

<pre class="brush: js notranslate">function makeAdder(a) {
  return function(b) {
    return a + b;
  };
}
var add5 = makeAdder(5);
var add20 = makeAdder(20);
add5(6); // ?
add20(7); // ?
</pre>

<p>El nombre de la función <code>makeAdder()</code> lo debería revelar: crea nuevas funciones '<code>adder</code>', cada una de las cuales, cuando se llama con un argumento, lo suma al argumento con el que fue creada.</p>

<p>Lo que está sucediendo aquí es más o menos lo mismo que sucedía anteriormente con las funciones internas: una función definida dentro de otra función tiene acceso a las variables de la función externa. La única diferencia aquí es que la función externa ha regresado y, por lo tanto, el sentido común parece dictar que sus variables locales ya no existen. Pero <em>sí</em> existen todavía — de lo contrario, las funciones de suma no podrían funcionar. Además, hay dos diferentes "copias" de las variables locales de <code>makeAdder()</code>: una en la que <code>a</code> es 5 y la otra en la que <code>a</code> es 20. Entonces, el resultado de las llamadas a esa función es el siguiente:</p>

<pre class="brush: js notranslate">add5(6); // returns 11
add20(7); // devuelve 27
</pre>

<p>Esto es lo que está sucediendo realmente. Siempre que JavaScript ejecuta una función, se crea un objeto '<code>scope</code>' para contener las variables locales creadas dentro de esa función. Se inicia con cualquier variable pasada como parámetros de función. Esto es similar al objeto global en el que viven todas las variables y funciones globales, pero con un par de importantes diferencias: en primer lugar, se crea un objeto de alcance completamente nuevo cada vez que una función se comienza a ejecutar y, en segundo lugar, a diferencia del objeto global (que es accesible como <code>this</code> y en los navegadores como <code>window</code>) no se puede acceder directamente a estos objetos <code>scope</code> desde tu código JavaScript. No hay ningún mecanismo para iterar sobre las propiedades del objeto <code>scope</code> actual, por ejemplo.</p>

<p>Entonces, cuando se llama a <code>makeAdder()</code>, se crea un objeto <code>scope</code> con una propiedad: <code>a</code>, que es el argumento que se pasa a la función <code>makeAdder()</code>. <code>makeAdder()</code> luego devuelve una función recién creada. Normalmente, el recolector de basura de JavaScript limpiaría el objeto <code>scope</code> creado para <code>makeAdder()</code> en este punto, pero la función devuelta mantiene una referencia a ese objeto de ámbito. Como resultado, el objeto <code>scope</code> no será recolectado como basura hasta que no haya más referencias al objeto función que <code>makeAdder()</code> devolvió.</p>

<p>Los objetos <code>scope</code> forman una cadena llamada cadena de ámbito, similar a la cadena de prototipos utilizada por el sistema de objetos de JavaScript.</p>

<p>Un <strong>cierre</strong> es la combinación de una función y el objeto <code>scope</code> en el que se creó. Los cierres te permiten guardar el estado — como tal, a menudo se pueden usar en lugar de objetos. Puedes encontrar <a href="http://stackoverflow.com/questions/111102/how-do-javascript-closures-work">varias presentaciones excelentes de los cierres</a>.</p></code></code>