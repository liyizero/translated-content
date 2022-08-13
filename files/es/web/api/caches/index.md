---
title: WindowOrWorkerGlobalScope.caches
slug: Web/API/caches
translation_of: Web/API/WindowOrWorkerGlobalScope/caches
original_slug: Web/API/WindowOrWorkerGlobalScope/caches
---
<p>{{APIRef()}}{{SeeCompatTable}}</p>

<p>La propiedad de sólo-lectura <code><strong>caches</strong></code>, de la interfaz {{domxref("WindowOrWorkerGlobalScope")}}, devuelve el objeto {{domxref("CacheStorage")}} asociado al contexto actual. Este objeto habilita funcionalidades como guardar assets para su utilización <em>offline</em>, y generar respuestas personalizadas a las peticiones.</p>

<h2 id="Sintaxis">Sintaxis</h2>

<pre class="syntaxbox">var <em>myCacheStorage</em> = self.caches; // or just caches
</pre>

<h3 id="Valor">Valor</h3>

<p>Un objeto {{domxref("CacheStorage")}}.</p>

<h2 id="Ejemplo">Ejemplo</h2>

<p>El siguiente ejemplo muestra la forma en la que utilizarías una cache en un contexto de <a href="/en-US/docs/Web/API/Service_Worker_API">service worker</a> para guardar assets <em>offline</em>.</p>

<pre class="brush: js">this.addEventListener('install', function(event) {
  event.waitUntil(
    caches.open('v1').then(function(cache) {
      return cache.addAll(
        '/sw-test/',
        '/sw-test/index.html',
        '/sw-test/style.css',
        '/sw-test/app.js',
        '/sw-test/image-list.js',
        '/sw-test/star-wars-logo.jpg',
        '/sw-test/gallery/',
        '/sw-test/gallery/bountyHunters.jpg',
        '/sw-test/gallery/myLittleVader.jpg',
        '/sw-test/gallery/snowTroopers.jpg'
      );
    })
  );
});</pre>

<h2 id="Especificaciones">Especificaciones</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Especificación</th>
   <th scope="col">Estado</th>
   <th scope="col">Comentario</th>
  </tr>
  <tr>
   <td>{{SpecName('Service Workers', '#self-caches', 'caches')}}</td>
   <td>{{Spec2('Service Workers')}}</td>
   <td>Definido en un <code>WindowOrWorkerGlobalScope</code> parcial en la última especificación.</td>
  </tr>
  <tr>
   <td>{{SpecName('Service Workers')}}</td>
   <td>{{Spec2('Service Workers')}}</td>
   <td>Definición inicial.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilidad_de_Navegadores">Compatibilidad de Navegadores</h2>

{{Compat("api.caches")}}

<h2 id="Ver_también">Ver también</h2>

<ul>
 <li><a href="/en-US/docs/Web/API/ServiceWorker_API">Service Workers</a></li>
 <li><a href="/en-US/docs/Web/API/Web_Workers_API">Web Workers</a></li>
 <li>{{domxref("CacheStorage")}}</li>
 <li>{{domxref("Cache")}}</li>
</ul>