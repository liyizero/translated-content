---
title: filter
slug: Web/CSS/filter
tags:
  - CSS
  - Filtro
  - Filtro SVG
  - Propiedad CSS
  - Referencia
  - SVG
translation_of: Web/CSS/filter
---
<p>{{SeeCompatTable}}{{CSSRef}}</p>

<h2 id="Resumen">Resumen</h2>

<p>La propiedad CSS <strong><code>filter</code></strong> dota de efectos gráficos como el desenfoque o cambio de color en la representación antes de que se muestre el elemento. Los filtros se utilizan comúnmente para ajustar la representación de imágenes, fondos o bordes.</p>

<p>Hay varias funciones Incluidas en el estándar CSS que logran efectos predefinidos. También puede hacer referencia a un filtro especificado en SVG con una URL  a un <a href="/es/docs/Web/SVG/Element/filter" title="/en/SVG/Element/filter">filtro de un elemento SVG</a>.</p>

<div class="note"><strong>Nota:</strong> Versiones anteriores (4.0 hasta 9.0) del navegador Internet Explorer de Windows admiten una propiedad <a class="external" href="https://msdn.microsoft.com/es-es/library/ms532853(v=vs.85).aspx">"filter"</a> no incluida en el estándar que ha quedado en desuso.</div>

<p>{{cssinfo}}</p>

<h2 id="Sintaxis">Sintaxis</h2>

<pre class="brush:css">filter: url("filters.svg#filter-id");
filter: blur(5px);
filter: brightness(0.4);
filter: contrast(200%);
filter: drop-shadow(16px 16px 20px blue);
filter: grayscale(50%);
filter: hue-rotate(90deg);
filter: invert(75%);
filter: opacity(25%);
filter: saturate(30%);
filter: sepia(60%);

/* Apply multiple filters */
filter: contrast(175%) brightness(3%);

/* Global values */
filter: inherit;
filter: initial;
filter: unset;
</pre>

<p>Con una función, use el siguiente código:</p>

<pre class="syntaxbox">filter: &lt;filter-function&gt; [&lt;filter-function&gt;]* | none
</pre>

<p>Para referenciar a al valor {{SVGElement("filter")}} de un elemento SVG, use el siguiente código:</p>

<pre class="syntaxbox">filter: url(file.svg#filter-element-id)
</pre>

<h3 id="Interpolación">Interpolación</h3>

<p>Si ambos filtros tienen una lista de funciones con la misma longitud y sin {{cssxref("&lt;url&gt;")}}, cada una de las funciones de filtro es interpolada, de acuerdo a sus reglas específicas. Si tienen longitudes diferentes, las funciones equivalentes que falten de la lista más larga se añaden al final de la lista más corta, usando sus valores lagunares, y después todas las funciones son interpoladas de acuerdo a sus reglas específicas. Si un filtro es 'none', es reemplazado por la lista de funciones de filtro del otro, usando los valores predeterminados para cada función, y después todos los filtros son interpolados de acuerdo a su regla específica. De otra forma, se usa interpolación discreta.</p>

<h3 id="Sintaxis_formal">Sintaxis formal</h3>

{{csssyntax}}

<h2 id="Ejemplos">Ejemplos</h2>

<p>Ejemplos del uso de las funciones predefinidas se muestran a continuación. Ver cada función. Ver cada función para un ejemplo específico.</p>

<pre class="brush: css">.mydiv { filter: grayscale(50%) }

/* funcion del blanco y negro "grayscale" al 50% y un desenfoque "blur" de 10px */
img {
  filter: grayscale(0.5) blur(10px);
}</pre>

<p>Ejemplos del uso de la función  con el recurso SVG se muestran a continuación.</p>

<pre class="brush: css">.target { filter: url(#c1); }

.mydiv { filter: url(commonfilters.xml#large-blur) }
</pre>

<h2 id="Funciones">Funciones</h2>

<p>Para utilizar la propiedad CSS <code>filter</code>, hay que especificar un valor para una de las siguientes funciones. Si el valor no es válido, la función se ejecutará de la misma manera que si se le aplicara "none". Las funciones que toman un valor en procentaje (como en el 34%) también aceptan el valor expresado como decimal (como en 0.34 ó .34).</p>

<h3 id="url()"><code>url()</code></h3>

<p>La función url() toma la dirección de un archivo XML que especifica un filtro SVG, y puede incluir un ancla para un elemento de filtro especifico.</p>

<pre class="brush: css">filter: url(resources.svg#c1)
</pre>

<h3 id="blur()"><code>blur()</code></h3>

<p>Aplica un desenfoque Gaussiano a la imagen. El valor de 'radio' define el valor de la desviación estándar de la función de desenfoque Gaussiano o el número de píxeles que se mezclan entre sí, por lo que un valor mayor creará un mayor desenfoque. El valor lagunar de interpolación (es decir, si no se proporciona ningún parametro) es <code>0</code>. El parámetro se especifica como una longitud de CSS, pero no acepta porcentajes.</p>

<pre class="brush: css">filter: blur(5px)
</pre>

<div id="blur_example" class="hidden">
<pre class="brush: html">  &lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th align="left" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form.jpg" id="img1" class="internal default" src="/files/3710/Test_Form_2.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form.jpg" id="img2" class="internal default" src="/files/3710/Test_Form_2.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg id="img3" viewbox="0 0 233 176"&gt;
  &lt;filter id="svgBlur" x="-5%" y="-5%" width="110%" height="110%" &gt;
    &lt;feGaussianBlur in="SourceGraphic" stdDeviation="5" /&gt;
  &lt;/filter&gt;
  &lt;image xlink:href="/files/3710/Test_Form_2.jpeg" filter="url(#svgBlur)" x="5%" y="5%" width="212px" height="161px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_s.jpg" id="img4" class="internal default" src="/files/3711/Test_Form_2_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;</pre>

<pre class="brush: css">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter:blur(5px);
  -webkit-filter:blur(5px);
  -o-filter:blur(5px);
  -ms-filter:blur(5px);
  filter:blur(5px); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  height: 100%;
  width: 85%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>
</div>

<pre class="brush: html">&lt;svg height="0" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;filter id="svgBlur" x="-5%" y="-5%" width="110%" height="110%"&gt;
    &lt;feGaussianBlur in="SourceGraphic" stdDeviation="5"/&gt;
  &lt;/filter&gt;
&lt;/svg&gt;</pre>

<p>{{EmbedLiveSample('blur_example','100%','236px','')}}</p>

<h3 id="brightness()"><code>brightness()</code></h3>

<p>Se aplica una multiplicación lineal a la imagen, haciendo que parezca más o menos brillante. Un valor de <code>0%</code> convertirá la imagen completamente a negro. Un valor de <code>100%</code> no producirá ningún cambio en la imagen. Otros valores causarán una multiplicación lineal en el efecto. Los valores de una cantidad superior al <code>100%</code> aumentarán el brillo de la imagen. El valor lagunar (si no se especifica ningún valor) es <code>1</code> (equivalente a <code>100%</code>).</p>

<pre class="brush: css">filter: brightness(0.5)</pre>

<pre class="brush: html">&lt;svg height="0" xmlns="http://www.w3.org/2000/svg"&gt;
 &lt;filter id="brightness"&gt;
    &lt;feComponentTransfer&gt;
        &lt;feFuncR type="linear" slope="[amount]"/&gt;
        &lt;feFuncG type="linear" slope="[amount]"/&gt;
        &lt;feFuncB type="linear" slope="[amount]"/&gt;
    &lt;/feComponentTransfer&gt;
  &lt;/filter&gt;
&lt;/svg&gt;</pre>

<div id="brightness_example" class="hidden">
<pre class="brush: html">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th align="left" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form.jpg" id="img1" class="internal default" src="/files/3708/Test_Form.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form.jpg" id="img2" class="internal default" src="/files/3708/Test_Form.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 286 217"&gt;
 &lt;filter id="brightness"&gt;
    &lt;feComponentTransfer&gt;
        &lt;feFuncR type="linear" slope="2"/&gt;
        &lt;feFuncG type="linear" slope="2"/&gt;
        &lt;feFuncB type="linear" slope="2"/&gt;
    &lt;/feComponentTransfer&gt;
  &lt;/filter&gt;
  &lt;image xlink:href="/files/3708/Test_Form.jpg" filter="url(#brightness)" width="286px" height="217px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_s.jpg" id="img4" class="internal default" src="/files/3709/Test_Form_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter:brightness(2);
  -webkit-filter:brightness(2);
  -o-filter:brightness(2);
  -ms-filter:brightness(2);
  filter:brightness(2); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  height:100%;
  width: 85%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>
</div>

<p>{{EmbedLiveSample('brightness_example','100%','231px','')}}</p>

<h3 id="contrast()"><code>contrast()</code></h3>

<p>Ajusta el contraste del elemento. Un valor superior a <code>0%</code> creará una imagen completamente gris. Un valor de <code>100%</code> deja al elemento sin cambios. Valores superiores a <code>100%</code> son permitidos, dando como resultado mayor contraste. El valor lagunar de interpolación (si no se especifica ningún valor) es <code>1</code> (equivalente a <code>100%</code>).</p>

<pre class="brush: css">filter: contrast(200%)
</pre>

<pre class="brush: html">&lt;svg height="0" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;filter id="contrast"&gt;
    &lt;feComponentTransfer&gt;
      &lt;feFuncR type="linear" slope="[amount]" intercept="-(0.5 * [amount]) + 0.5"/&gt;
      &lt;feFuncG type="linear" slope="[amount]" intercept="-(0.5 * [amount]) + 0.5"/&gt;
      &lt;feFuncB type="linear" slope="[amount]" intercept="-(0.5 * [amount]) + 0.5"/&gt;
    &lt;/feComponentTransfer&gt;
  &lt;/filter&gt;
&lt;/svg&gt;
</pre>

<div id="contrast_example" class="hidden">
<pre class="brush: html">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th align="left" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form_3.jpeg" id="img1" class="internal default" src="/files/3712/Test_Form_3.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_3.jpg" id="img2" class="internal default" src="/files/3712/Test_Form_3.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 240 151"&gt;
 &lt;filter id="contrast"&gt;
    &lt;feComponentTransfer&gt;
      &lt;feFuncR type="linear" slope="2" intercept="-0.5"/&gt;
      &lt;feFuncG type="linear" slope="2" intercept="-0.5"/&gt;
      &lt;feFuncB type="linear" slope="2" intercept="-0.5"/&gt;
    &lt;/feComponentTransfer&gt;
  &lt;/filter&gt;
  &lt;image xlink:href="/files/3712/Test_Form_3.jpeg" filter="url(#contrast)" width="240px" height="151px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_s.jpg" id="img4" class="internal default" src="/files/3713/Test_Form_3_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter:contrast(200%);
  -webkit-filter:contrast(200%);
  -o-filter:contrast(200%);
  -ms-filter:contrast(200%);
  filter:contrast(200%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>
</div>

<p>{{EmbedLiveSample('contrast_example','100%','203px','')}}</p>

<h3 id="drop-shadow()"><code>drop-shadow()</code></h3>

<p>Aplica un efecto de sombra a la imagen. Una  sombra es realmente una versión desenfocada y separada de la máscara alfa de la imagen, dibujada en un color particular, debajo de la misma. La función acepta un parámetro de tipo &lt;shadow&gt; (definido en CSS3 Backgrounds), con la excepción de que la palabra clave ‘inset’ no está permitida. Esta función es similar a la propiedad {{cssxref("box-shadow")}}, más establecida; la diferencia es que con filtros, algunos navegadores proveen aceleración de hardware para mayor rendimiento. Los valores para el parámetro <code>&lt;shadow&gt;</code> son los siguientes:</p>

<dl>
 <dt><code>&lt;offset-x&gt;</code> <code>&lt;offset-y&gt;</code> <small>(requerido)</small></dt>
 <dd>Son dos valores {{cssxref("&lt;length&gt;")}} para establecer la posición de la sobra respecto a la imagen. <code>&lt;offset-x&gt;</code> especifica la distancia horizontal. Valores negativos establecen la sombra a la izquierda del elemento. <code>&lt;offset-y&gt;</code> especifica la distancia vertical. Valores negativos establecen la sombra arriba del elemento. Véase {{cssxref("&lt;length&gt;")}} para unidades posibles.<br>
 Si ambos valores son <code>0</code>, la sombra será colocada detrás del elemento (y puede generar un efecto de desenfoque si se establecen <code>&lt;blur-radius&gt;</code> y/o <code>&lt;spread-radius&gt;</code>).</dd>
 <dt><code>&lt;blur-radius&gt;</code> <small>(opcional)</small></dt>
 <dd>Es un tercer valor {{cssxref("&lt;length&gt;")}}. Mientras mayor sea el valor, mayor será el desenfoque, por lo que la sombra se vuelve más grande y clara. No se permiten valores negativos. Si no es especificado, su valor predeterminado será <code>0</code> (el borde de la sombra es nítido).</dd>
 <dt><code>&lt;spread-radius&gt;</code> <small>(opcional)</small></dt>
 <dd>Es el cuarto valor {{cssxref("&lt;length&gt;")}}. Valores positivos harán que la sombra se expanda, y valores negativos harán que la sombra se contraiga. Si no se especifica, su valor predeterminado será <code>0</code> (la sombra tendrá el mismo tamaño del elemento). <br>
 Nota: Webkit, y tal vez otros navegadores, no soportan este cuarto valor; si se incluye, no se aplicará el filtro.</dd>
 <dt><code>&lt;color&gt;</code> <small>(opcional)</small></dt>
 <dd>Véanse los valores {{cssxref("&lt;color&gt;")}} para las opciones posibles de palabras clave y notaciones. Si no se especifica, el color depende del navegador. En Gecko (Firefox), Presto (Opera) y Trident (Internet Explorer), se usa el valor de la propiedad {{cssxref("color")}}. Por otro lado, la sombra en WebKit es transparente, y por lo tanto, es inútil si se omite <code>&lt;color&gt;</code>.</dd>
</dl>

<pre class="brush: css">filter: drop-shadow(16px 16px 10px black)</pre>

<pre class="brush: html">&lt;svg height="0" xmlns="http://www.w3.org/2000/svg"&gt;
 &lt;filter id="drop-shadow"&gt;
    &lt;feGaussianBlur in="SourceAlpha" stdDeviation="[radius]"/&gt;
    &lt;feOffset dx="[offset-x]" dy="[offset-y]" result="offsetblur"/&gt;
    &lt;feFlood flood-color="[color]"/&gt;
    &lt;feComposite in2="offsetblur" operator="in"/&gt;
    &lt;feMerge&gt;
      &lt;feMergeNode/&gt;
      &lt;feMergeNode in="SourceGraphic"/&gt;
    &lt;/feMerge&gt;
  &lt;/filter&gt;
&lt;/svg&gt;
</pre>

<div id="shadow_example" class="hidden">
<pre class="brush: html">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th align="left" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form_4.jpeg" id="img1" class="internal default" src="/files/3714/Test_Form_4.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_4.jpg" id="img2" class="internal default" src="/files/3714/Test_Form_4.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 239 187"&gt;
 &lt;filter id="drop-shadow"&gt;
    &lt;feGaussianBlur in="SourceAlpha" stdDeviation="5"/&gt;
    &lt;feOffset dx="16" dy="16"/&gt;
    &lt;feMerge&gt;
      &lt;feMergeNode/&gt;
      &lt;feMergeNode in="SourceGraphic"/&gt;
    &lt;/feMerge&gt;
 &lt;/filter&gt;
 &lt;image xlink:href="/files/3714/Test_Form_4.jpeg" filter="url(#drop-shadow)" width="213px" height="161px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_4_s.jpg" id="img4" class="internal default" src="/files/3715/Test_Form_4_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form_4 distorded border - Original image" id="img11" class="internal default" src="/files/8467/Test_Form_4_irregular-shape_opacity-gradient.png" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_4 distorded border - Live example" id="img12" class="internal default" src="/files/8467/Test_Form_4_irregular-shape_opacity-gradient.png" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;
        &lt;div class="svg-container"&gt;
          &lt;svg xmlns="http://www.w3.org/2000/svg" id="img13" viewbox="0 0 239 187"&gt;
            &lt;filter id="drop-shadow2"&gt;
              &lt;feGaussianBlur in="SourceAlpha" stdDeviation="4"/&gt;
              &lt;feOffset dx="8" dy="10"/&gt;
              &lt;feMerge&gt;
                &lt;feMergeNode/&gt;
                &lt;feMergeNode in="SourceGraphic"/&gt;
              &lt;/feMerge&gt;
            &lt;/filter&gt;
            &lt;image xlink:href="/files/8467/Test_Form_4_irregular-shape_opacity-gradient.png<span style="font-size: 1rem;">" filter="url(#drop-shadow2)" width="213px" height="161px" /&gt;</span>
          &lt;/svg&gt;
        &lt;div&gt;
      &lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_4 distorded border drop shadow - Static example" id="img14" class="internal default" src="/files/8469/Test_Form_4_irregular-shape_opacity-gradient_drop-shadow.png" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: drop-shadow(16px 16px 10px black);
  -webkit-filter: drop-shadow(16px 16px 10px black);
  -o-filter: drop-shadow(16px 16px 10px black);
  -ms-filter: drop-shadow(16px 16px 10px black);
  filter: drop-shadow(16px 16px 10px black);
}
#img12 {
  width:100%;
  height:auto;
  -moz-filter: drop-shadow(8px 9px 5px rgba(0,0,0,.8));
  -webkit-filter: drop-shadow(8px 9px 5px rgba(0,0,0,.8));
  -o-filter: drop-shadow(8px 9px 5px rgba(0,0,0,.8));
  -ms-filter: drop-shadow(8px 9px 5px rgba(0,0,0,.8));
  filter: drop-shadow(8px 9px 5px rgba(0,0,0,.8));
}
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
#irregular-shape {
  width: 64%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3, #img13 {
  height:100%;
}
</pre>
</div>

<p>{{EmbedLiveSample('shadow_example','100%','300px','')}}</p>

<h3 id="grayscale()"><code>grayscale()</code></h3>

<p>Convierte la imagen a escala de grises. El valor del parámetro define la proporción de la conversión. Un valor de <code>100%</code> es completamente a escala de grises. Un valor de <code>0%</code> deja la imagen sin cambios. Valores entre <code>0%</code> y <code>100%</code> son múltiplos lineales de este efecto. Si el parámetro no es incluido, se usa el valor de <code>0</code>.</p>

<pre class="brush: css">filter: grayscale(100%)</pre>

<div id="grayscale_example" class="hidden">
<pre class="brush: html">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th align="left" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form_5.jpeg" id="img1" class="internal default" src="/files/3716/Test_Form_5.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_5.jpg" id="img2" class="internal default" src="/files/3716/Test_Form_5.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 276 184"&gt;
 &lt;filter id="grayscale"&gt;
    &lt;feColorMatrix type="matrix"
               values="0.2126 0.7152 0.0722 0 0
                       0.2126 0.7152 0.0722 0 0
                       0.2126 0.7152 0.0722 0 0
                       0 0 0 1 0"/&gt;
  &lt;/filter&gt;
  &lt;image xlink:href="/files/3716/Test_Form_5.jpeg" filter="url(#grayscale)" width="276px" height="184px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_5_s.jpg" id="img4" class="internal default" src="/files/3717/Test_Form_5_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter:grayscale(100%);
  -webkit-filter:grayscale(100%);
  -o-filter:grayscale(100%);
  -ms-filter:grayscale(100%);
  filter:grayscale(100%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>
</div>

<p>{{EmbedLiveSample('grayscale_example','100%','209px','')}}</p>

<h3 id="hue-rotate()"><code>hue-rotate()</code></h3>

<p>Aplica una rotación de tono (matiz) al elemento. El valor del ángulo define el número de grados al rededor del círculo de colores al que se ajustarán los colores de la imagen. Un valor de <code>0deg</code> deja la imagen sin cambios. Si el parámetro del ángulo no es especiicado, se usa valor de <code>0deg</code>. Aunque no hay valor máximo, el efecto de valores encima de <code>360deg</code> da la vuelta al círculo de colores.</p>

<pre class="brush: css">filter: hue-rotate(90deg)</pre>

<div id="huerotate_example" class="hidden">
<pre class="brush: html">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th align="left" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form_6.jpeg" id="img1" class="internal default" src="/files/3718/Test_Form_6.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_6.jpg" id="img2" class="internal default" src="/files/3718/Test_Form_6.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 266 190"&gt;
 &lt;filter id="hue-rotate"&gt;
    &lt;feColorMatrix type="hueRotate"
               values="90"/&gt;
  &lt;/filter&gt;
  &lt;image xlink:href="/files/3718/Test_Form_6.jpeg" filter="url(#hue-rotate)" width="266px" height="190px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_6_s.jpg" id="img4" class="internal default" src="/files/3719/Test_Form_6_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter:hue-rotate(90deg);
  -webkit-filter:hue-rotate(90deg);
  -o-filter:hue-rotate(90deg);
  -ms-filter:hue-rotate(90deg);
  filter:hue-rotate(90deg); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>
</div>

<pre class="brush: html">&lt;svg height="0" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;filter id="svgHueRotate" &gt;
    &lt;feColorMatrix type="hueRotate" values="[angle]" /&gt;
  &lt;filter /&gt;
&lt;/svg&gt;</pre>

<p>{{EmbedLiveSample('huerotate_example','100%','221px','')}}</p>

<h3 id="invert()"><code>invert()</code></h3>

<p>Invierte los colores de la imagen. El parámetro define la proporción de la conversión. Un valor de <code>100%</code> invierte completamente la imagen. Un valor de <code>0%</code> deja a la imagen sin cambios. Valores entre <code>0%</code> y <code>100%</code> son múltiplos lineales del efecto. Si el parámetro no es especificado, se usa un valor de <code>0</code>.</p>

<pre class="brush: css">filter: invert(100%)</pre>

<div id="invert_example" class="hidden">
<pre class="brush: html">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th align="left" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form_7.jpeg" id="img1" class="internal default" src="/files/3720/Test_Form_7.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_7.jpg" id="img2" class="internal default" src="/files/3720/Test_Form_7.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 183 276"&gt;
 &lt;filter id="invert"&gt;
    &lt;feComponentTransfer&gt;
        &lt;feFuncR type="table" tableValues="1 0"/&gt;
        &lt;feFuncG type="table" tableValues="1 0"/&gt;
        &lt;feFuncB type="table" tableValues="1 0"/&gt;
    &lt;/feComponentTransfer&gt;
 &lt;/filter&gt;
 &lt;image xlink:href="/files/3720/Test_Form_7.jpeg" filter="url(#invert)" width="183px" height="276px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_7_s.jpg" id="img4" class="internal default" src="/files/3721/Test_Form_7_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: invert(100%);
  -webkit-filter: invert(100%);
  -o-filter: invert(100%);
  -ms-filter: invert(100%);
  filter: invert(100%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>
</div>

<p>{{EmbedLiveSample('invert_example','100%','407px','')}}</p>

<h3 id="opacity()"><code>opacity()</code></h3>

<p>Aplica transparencia a la imagen. El valor del parámetro define la proporción de la conversión. Un valor de <code>0%</code> es completamente transparente. Un valor de <code>100%</code> deja la imagen sin cambios. Valores entre <code>0%</code> y <code>100%</code> son múltiplos lineales del efecto. Esto es equivalente a multiplicar las muestras de la imagen por el valor indicado. Si el parámetro no es especificado, se usa un valor de <code>1</code>. Esta función es similar a la propiedad {{cssxref("opacity")}}, más establecida; la diferencia es que con filtros, algunos navegadores proveen aceleración de hardware para mayor rendimiento.</p>

<pre class="brush: css">filter: opacity(50%)</pre>

<div id="opacity_example" class="hidden">
<pre class="brush: html">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th align="left" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form_14.jpeg" id="img1" class="internal default" src="/files/3725/Test_Form_14.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_14.jpg" id="img2" class="internal default" src="/files/3725/Test_Form_14.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 276 183"&gt;
 &lt;filter id="opacity"&gt;
    &lt;feComponentTransfer&gt;
        &lt;feFuncA type="table" tableValues="0 0.5"&gt;
    &lt;/feComponentTransfer&gt;
 &lt;/filter&gt;
 &lt;image xlink:href="/files/3725/Test_Form_14.jpeg" filter="url(#opacity)" width="276px" height="183px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_14_s.jpg" id="img4" class="internal default" src="/files/3726/Test_Form_14_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: opacity(50%);
  -webkit-filter: opacity(50%);
  -o-filter: opacity(50%);
  -ms-filter: opacity(50%);
  filter: opacity(50%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>
</div>

<p>{{EmbedLiveSample('opacity_example','100%','210px','')}}</p>

<h3 id="saturate()"><code>saturate()</code></h3>

<p>Aplica saturación a la imagen. El valor del parámetro define la proporción de la conversión. Un valor de <code>0%</code> es completamente sin saturación. Un valor de <code>100%</code> deja la imagen sin cambios. Otros valores son múltiplos lineales del efecto. Valores por encima de <code>100%</code> son permitidos, dando resultados de sobresaturación. Si no se especifica el parámetro, se usa el valor de <code>1</code>.</p>

<pre class="brush: css">filter: saturate(200%)</pre>

<div id="saturate_example" class="hidden">
<pre class="brush: html">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th align="left" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form_9.jpeg" id="img1" class="internal default" src="/files/3722/Test_Form_9.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_9.jpg" id="img2" class="internal default" src="/files/3722/Test_Form_9.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 201 239"&gt;
 &lt;filter id="saturate"&gt;
    &lt;feColorMatrix type="saturate"
               values="2"/&gt;
 &lt;/filter&gt;
 &lt;image xlink:href="/files/3722/Test_Form_9.jpeg" filter="url(#saturate)" width="201px" height="239px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_9_s.jpg" id="img4" class="internal default" src="/files/3724/Test_Form_9_s.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: saturate(200%);
  -webkit-filter: saturate(200%);
  -o-filter: saturate(200%);
  -ms-filter: saturate(200%);
  filter: saturate(200%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>
</div>

<p>{{EmbedLiveSample('saturate_example','100%','332px','')}}</p>

<h3 id="sepia()"><code>sepia()</code></h3>

<p>Convierte la imagen a sepia. El valor del parámetro define la proporción de la conversión. Un valor de <code>100%</code> es completamente sepia. Un valor de <code>0%</code> deja la imagen sin cambios. Valores entre <code>0%</code> y <code>100%</code> son múltiplos lineales del efecto. Si no se especifica el parámetro, se usa el valor de <code>0</code>.</p>

<pre class="brush: css">filter: sepia(100%)</pre>

<div id="sepia_example" class="hidden">
<pre class="brush: html">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th align="left" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;SVG Equivalent&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form_12.jpeg" id="img1" class="internal default" src="/files/3727/Test_Form_12.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_12.jpg" id="img2" class="internal default" src="/files/3727/Test_Form_12.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;div class="svg-container"&gt;&lt;svg xmlns="http://www.w3.org/2000/svg" id="img3" viewbox="0 0 259 194"&gt;
 &lt;filter id="sepia"&gt;
    &lt;feColorMatrix type="matrix"
               values="0.393 0.769 0.189 0 0
                       0.349 0.686 0.168 0 0
                       0.272 0.534 0.131 0 0
                       0 0 0 1 0"/&gt;
 &lt;/filter&gt;
 &lt;image xlink:href="/files/3727/Test_Form_12.jpeg" filter="url(#sepia)" width="259px" height="194px" /&gt;
&lt;/svg&gt;&lt;div&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_12_s.jpg" id="img4" class="internal default" src="/files/3728/Test_Form_12_s.jpg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: sepia(100%);
  -webkit-filter: sepia(100%);
  -o-filter: sepia(100%);
  -ms-filter: sepia(100%);
  filter: sepia(100%); }
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>
</div>

<p>{{EmbedLiveSample('sepia_example','100%','229px','')}}</p>

<h2 id="Combinando_funciones">Combinando funciones</h2>

<p>Se puede combinar cualquier número de funciones para manipular la representación de la imagen. Los siguientes ejemplos aumentan el contraste y brillo de la imagen.</p>

<pre class="brush: css">filter: contrast(175%) brightness(3%)</pre>

<div id="combination_example" class="hidden">
<pre class="brush: html">&lt;table class="standard-table"&gt;
  &lt;thead&gt;
    &lt;tr&gt;
      &lt;th align="left" scope="col"&gt;Original image&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Live example&lt;/th&gt;
      &lt;th align="left" scope="col"&gt;Static example&lt;/th&gt;
    &lt;/tr&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;img alt="Test_Form_8.jpeg" id="img1" class="internal default" src="/files/3729/Test_Form_8.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_8.jpg" id="img2" class="internal default" src="/files/3729/Test_Form_8.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;img alt="Test_Form_8_s.jpg" id="img4" class="internal default" src="/files/3730/Test_Form_8_s.jpeg" style="width: 100%;" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table&gt;
</pre>

<pre class="brush: css">html {
  height:100%;
}
body {
  font: 14px/1.286 "Lucida Grande","Lucida Sans Unicode","DejaVu Sans",Lucida,Arial,Helvetica,sans-serif;
  color: rgb(51, 51, 51);
  height:100%;
  overflow:hidden;
}
#img2 {
  width:100%;
  height:auto;
  -moz-filter: contrast(175%) brightness(103%);
  -webkit-filter: contrast(175%) brightness(103%);
  -o-filter: contrast(175%) brightness(103%);
  -ms-filter: contrast(175%) brightness(103%);
  filter: contrast(175%) brightness(103%);
}
table.standard-table {
  border: 1px solid rgb(187, 187, 187);
  border-collapse: collapse;
  border-spacing: 0px;
  margin: 0px 0px 1.286em;
  width: 85%;
  height: 100%;
}
table.standard-table th {
  border: 1px solid rgb(187, 187, 187);
  padding: 0px 5px;
  background: none repeat scroll 0% 0% rgb(238, 238, 238);
  text-align: left;
  font-weight: bold;
}
table.standard-table td {
  padding: 5px;
  border: 1px solid rgb(204, 204, 204);
  text-align: left;
  vertical-align: top;
  width:25%;
  height:auto;
}
#img3 {
  height:100%;
}
</pre>
</div>

<p>{{EmbedLiveSample('combination_example','100%','209px','')}}</p>

<h2 id="Especificaciones">Especificaciones</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Especificación</th>
   <th scope="col">Estatus</th>
   <th scope="col">Comentarios</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{ SpecName('Filters 1.0', '#FilterProperty', 'filter') }}</td>
   <td>{{ Spec2('Filters 1.0') }}</td>
   <td>Definición inicial</td>
  </tr>
 </tbody>
</table>

<h2 id="Browser_compatibility" name="Browser_compatibility">Compatibilidad de navegadores</h2>

{{Compat("css.properties.filter")}}

<h2 id="Véase_también">Véase también</h2>

<ul>
 <li><a class="internal" href="/es/docs/Applying_SVG_effects_to_HTML_content" title="En/Applying SVG effects to HTML content">Aplicando efectos de SVG a contenido HTML</a></li>
 <li>La propiedad {{ Cssxref("mask") }}</li>
 <li><a class="internal" href="/es/docs/SVG" title="En/SVG">SVG</a></li>
 <li><a class="external" href="http://www.html5rocks.com/en/tutorials/filters/understanding-css/">Entendiendo los filtros CSS</a>, artículo en inglés de HTML5Rocks!</li>
</ul>