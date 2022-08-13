---
title: WindowOrWorkerGlobalScope.isSecureContext
slug: Web/API/isSecureContext
translation_of: Web/API/WindowOrWorkerGlobalScope/isSecureContext
original_slug: Web/API/WindowOrWorkerGlobalScope/isSecureContext
---
<p>{{APIRef()}}{{SeeCompatTable}}</p>

<p>La propiedad de sólo-lectura <code><strong>isSecureContext</strong></code>, de la interface  {{domxref("WindowOrWorkerGlobalScope")}} Devuelve un booleano indicando si el contexto actual es seguro (<code>true</code>) or not (<code>false</code>).</p>

<h2 id="Sintaxis">Sintaxis</h2>

<pre class="syntaxbox">var <em>isItSecure</em> = self.isSecureContext; // or just isSecureContext
</pre>

<h3 id="Valor">Valor</h3>

<p>Un {{domxref("Boolean")}}.</p>

<h2 id="Especificaciones">Especificaciones</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Especificación</th>
   <th scope="col">Estado</th>
   <th scope="col">Comentario</th>
  </tr>
  <tr>
   <td>{{SpecName('Secure Contexts', 'webappapis.html#dom-origin', 'WindowOrWorkerGlobalScope.isSecureContext')}}</td>
   <td>{{Spec2('Secure Contexts')}}</td>
   <td>Definición inicial.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilidad_de_Navegadores">Compatibilidad de Navegadores</h2>

{{Compat("api.isSecureContext")}}