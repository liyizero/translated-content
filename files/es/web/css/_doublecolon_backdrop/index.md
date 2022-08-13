---
title: '::backdrop'
slug: 'Web/CSS/::backdrop'
tags:
  - CSS
  - Layout
  - NeedsContent
  - Pantalla completa
  - Pseudo Elemento CSS
  - Referencia
  - Web
translation_of: 'Web/CSS/::backdrop'
---
<div>{{CSSRef}} {{SeeCompatTable}}</div>

<p>Cada uno de los elementos en la pila de la  <a href="https://fullscreen.spec.whatwg.org/#top-layer">capa superior</a> posee un  <dfn><code>::backdrop</code></dfn> {{Cssxref("pseudo-elements", "pseudo-element")}}. Este pseudo-elemento es una caja que se muestra inmediatamente debajo del elemento (y sobre el elemento inmediatamente inferior de la pila, si es que hay), dentro de dicha capa superior.</p>

<p class="note">El pseudo-elemento <code>::backdrop</code> se puede usar para crear un fondo que oculte el documento subyacente detrás de la pila de la capa superior, p.ej., para el elemento que es mostrado a pantalla complete tal  y como se describe en esta especificación.</p>

<p>No se hereda ni es heredado de ningún elemento. Tampoco se hacen restricciones sobre qué propiedades se aplican a este pseudo-elemento.</p>

<h2 id="Especificaciones">Especificaciones</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Especificación</th>
   <th scope="col">Estado</th>
   <th scope="col">Comentario</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{SpecName('Fullscreen', '#::backdrop-pseudo-element', '::backdrop')}}</td>
   <td>{{Spec2('Fullscreen')}}</td>
   <td>Definición Inicial</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilidad_con_los_distintos_navegadores">Compatibilidad con los distintos navegadores</h2>

{{Compat("css.selectors.backdrop")}}

<h2 id="Ver_además">Ver además</h2>

<ul>
 <li>{{cssxref(":fullscreen")}}</li>
 <li>{{HTMLElement("dialog")}}</li>
</ul>