# Ayuntamiento de Fuente de Cantos · propuesta de web «Puerta abierta»

Maqueta de la web municipal del **Ayuntamiento de Fuente de Cantos** (Badajoz, 4.583 habitantes, INE 2025), hecha con la plantilla «Puerta abierta» y sus datos reales. **No es la web oficial**:
- lleva en todas las páginas la banda «Propuesta de diseño… no es la web oficial»;
- lleva `noindex, nofollow` en todas las páginas.

Publicada en <https://alvarotaiagu.github.io/ayuntamiento-fuente-de-cantos-web/> (con `?revision`, el mando de la reunión).

```bash
npm install                        # Playwright y axe-core (solo para los scripts)
node scripts/aplicar.mjs           # genera la web desde los datos
node scripts/servir.mjs            # http://127.0.0.1:4192/  ·  con ?revision, el mando
node scripts/verificar.mjs         # todas las comprobaciones
```

Las fuentes de cada dato, el inventario de su web actual y los errores comprobados están en la carpeta de trabajo, fuera de esta web: `ayuntamiento-fuente-de-cantos-bocetos/` (`DATOS.md`, `INVENTARIO.md`, `ERRORES.md`).

---

## El concepto

La web es la puerta del Ayuntamiento, abierta todo el día. El panel «Hoy en Fuente de Cantos» dice al entrar si el Ayuntamiento está abierto, qué es lo próximo en la agenda y cuál es el último aviso. Los trámites se buscan con palabras normales y llevan directos a la sede electrónica. Lo vivo se mueve solo: el tablón oficial, las fiestas de fecha fija en la agenda y el «abierto ahora».

Lo propio de Fuente de Cantos:
- **El azul del escudo como marca.** Por área gana el oro (52,9 %), que nunca puede ser marca porque no llega a AA como texto. El siguiente es el **azur** (30,1 %): el de los cuarteles de las torres y el escusón de la fuente, y el azul del logotipo que el Ayuntamiento ya usa. Oscurecido hasta AA. El gules de los leones queda para las alertas, y el oro para los filetes. El motivo está escrito en `marca/marca.json`.
- **La villa de Zurbarán.** La casa natal, el Centro de Interpretación y el Museo del Flamenco están en «El pueblo → Para visitar», con lo que consta y sin horarios inventados.
- **Todo lo que su web tenía colgado**: las 52 ordenanzas y reglamentos, las actas de plenos, los decretos y la guía de residuos, en «El Ayuntamiento → Normativa y documentos». Sus 13 impresos (casi todos en Word) están en «Trámites», con la etiqueta Word o PDF.
- **La recogida puerta a puerta** (qué se saca cada día y a qué hora) y el punto limpio están en el listín.

## Qué se añadió a la plantilla para este pueblo

Su web tenía contenido útil que la plantilla no sabía enseñar. Se añadió **a la plantilla** (`plantilla-ayuntamiento-puerta-abierta-web`), como secciones opcionales y genéricas, probadas con datos de muestra y sin romper Ribera ni el reskin de Segura:
1. `pueblo.visitas`: «Para visitar», con dirección, horario, entrada y teléfono solo si constan.
2. `documentos`: «Normativa y documentos», en desplegables por grupo.
3. Impresos en Word (`tipo: "doc"`).
4. Servicios del listín sin teléfono (la recogida de basura).
5. El filtro del tablón: dos listas de procesos selectivos de su sede («08 ANUNCIO LISTA DEFINITIVA» y «Anuncio lista definitva») pasaban el filtro de datos personales. Ahora una lista dentro de un procedimiento de selección de personal queda fuera siempre.

## El tablón

Su sede es de **Gestiona** (`fuentedecantos.sedelectronica.es`), con el catálogo común: los 111 trámites tienen enlace fijo y se han comprobado uno a uno. El `robots.txt` de la sede prohíbe la lectura automática del tablón, así que:
- **en la maqueta**, el tablón sale de una sola lectura del 3 de octubre de 2026 (10 anuncios: se enseñan 3 y **7 se quedan fuera** por llevar nombres de aspirantes);
- **en producción**, la lectura diaria solo se activa con `"tablon_autorizado": true`, cuando el Ayuntamiento lo autorice por escrito.

Casi todo lo que publica su tablón son procesos de selección con nombres: la web lo enlaza, pero no lo copia.

## Pendientes para el Ayuntamiento

- [ ] **Horario de atención** al público. Ahora sale «Lunes a viernes, de 9:00 a 14:00» con la etiqueta «Ejemplo»: no está publicado en ningún sitio.
- [ ] **El saluda** de la alcaldía: el texto actual es de ejemplo.
- [ ] **Horario de la casa natal de Zurbarán, del Centro de Interpretación y de la Oficina de Turismo.** Su web tiene cuatro horarios distintos (2015-2024); en la propuesta se dice que se pregunte en el 924 580 380.
- [ ] Dirección y teléfono del **Museo del Flamenco**, y qué es el **«Museo del Campo»** (Plaza del Sol), que solo aparece nombrado.
- [ ] **Fotos propias** de calidad (casa natal, la Hermosa, los conventos, la Chanfaina) y **autorización** para usar las de su web, que en la propuesta llevan la nota «solo para la propuesta».
- [ ] **El escudo**: se usa el cuartelado que el Ayuntamiento enseña en su web (SVG de Commons, Erlenmeyer, CC BY-SA 4.0). Heraldry of the World da otro blasón, concedido en 2006, y no se ha encontrado la orden en el DOE. No se publica blasón hasta aclararlo.
- [ ] **El texto de la placa de la casa natal**. En una foto de 2015 se lee «En esta casa nació Francisco de Zurbarán, pincel de sombras y luces que supo ganar las cumbres de la fama universal», pero las fechas y alguna palabra no se distinguen. Con el texto confirmado, la placa tiene su sitio en «El pueblo».
- [ ] **La oposición en 2026**: el BOP no recoge cambios desde 2023, pero no se ha podido abrir el acta del Pleno del 30-06-2026 para confirmarlo.
- [ ] Si los **plenos** se graban o se emiten, para enlazarlos (en su canal de YouTube no hay ninguno).
- [ ] **Autorización para leer su tablón** de forma automática.
- [ ] Trámites propios que no estén en el catálogo común de Gestiona.
- [ ] El **teléfono de averías del agua** (su web da dos números sin decir cuál es cuál) y la **dirección de la residencia de mayores**.
- [ ] La **fecha del Otoño Flamenco 2026** y la hora de las puertas abiertas de la Guardia Civil.
- [ ] La lista actual de **asociaciones** (la de su web es de 2015).
- [ ] Revisar las **listas de procesos selectivos antiguas** que siguen publicadas con nombres en su web (Policía Local 2020, piano 2023).

## Erratas de su web, corregidas al usar sus textos

- «Fuente**s** de Cantos» en el pie de todas las páginas → **Fuente de Cantos**.
- «Luisa Durán Pagadoer» y «D. Inmaculada González Muñoz» → **Luisa María Durán Pagador** y **D.ª Inmaculada** (BOP 3770/2023).
- «Nicolás Megías» (calle) → **Nicolás Megía**.
- Dos teléfonos pegados: «924 500 031647 701 575» (Policía Local) → **924 500 031** y **647 701 575**; «924 500 211647 702 065» (Universidad Popular) → **647 702 065** (el primero es el del Ayuntamiento).
- Títulos de ordenanzas: «Precio públcio», «usso», «funcionamientodel», «barracas,casetas», «radiodifución», «guarderias», «analoga», «caracter», «policia» → corregidos. La ordenanza n.º 12, titulada «12TASA~1» en su web, lleva su título real (leído del PDF): **Tasa por el servicio de matadero, lonjas y mercados**.
- El impreso de comunicación previa estaba dos veces (una copia idéntica con «-1»): sale una vez.

## Datos que se contradicen (y cuál se usa)

| Dato | Versiones | Se usa |
|---|---|---|
| Número del Ayuntamiento | n.º 1 (sede, BOP 2026, su web) · s/n (oficina de registro, Diputación, «El Municipio» 2015) | n.º 1 |
| Biblioteca | 924 580 380 (Directorio de Bibliotecas) · 924 500 017 (su web, 2020) | el del directorio |
| CEIP Francisco de Zurbarán | 924 023 363, C/ San Julián, 12 (web del colegio) · 924 023 634, C/ Carniceros (su web, 2020) | la del colegio |
| Centro de Salud | C/ San Julián (SES, nuevo desde 2025) · Pza. de la Aurora y «924 924 924» (su web) | el SES |
| Farmacias | C/ Llerena, 1 y C/ Martínez, 9 (Colegio de Farmacéuticos) · Pza. de la Constitución, 3 y C/ Martínez, 15 (su web, 2020) | el Colegio |
| Oficina de Turismo | Pza. del Carmen (2020) · Pza. de la Constitución, 1 (Mancomunidad) · antigua Casa de Correos, Pza. de la Constitución (su web, 2025) | la de 2025 |
| Teléfono de la casa natal | 924 500 211 (Turismo de Extremadura, Diputación) · 924 580 380 (Turismo de la Diputación, Mancomunidad) | 924 580 380, el de la Oficina de Turismo |
| Declaración de Interés Turístico de la Chanfaina | 1993 · 1987 | no se enseña el año |
| Distancia a Badajoz | 101, 100 o 98 km | no se enseña |
| Autor del retablo mayor | Manuel García de Santiago · «atribuido a González del Castillo» | no se nombra |

## Créditos de las fotos

| Foto | Autor | Licencia |
|---|---|---|
| Plaza y torre de la parroquia (portada) | Sergueibubu (Wikimedia Commons) | CC0 |
| Parroquia, Casa Consistorial | stavros1 (Wikimedia Commons) | CC BY 3.0 |
| Ermita de San Isidro | Rene112233, foto de Jorge Armestar (Wikimedia Commons) | CC BY-SA 4.0 |
| Estatua de Zurbarán | Gonzalo 11789 (Wikimedia Commons) | CC0 |
| Casa natal, la Hermosa, San Juan de Letrán, San Diego, Los Castillejos, chanfaina | web del Ayuntamiento | **Solo para la propuesta**: hace falta su autorización |
| Escudo | Erlenmeyer (Wikimedia Commons) | CC BY-SA 4.0 |

Las de Commons llevan recorte y gradación de color propios, y así se dice en «El pueblo → Créditos de las fotos». Las de la romería de Commons no se usan: tienen personas reconocibles en primer plano.

## Antes de entregarla

La receta completa está en [RESKIN.md](RESKIN.md) §9: fijar en la reunión la versión y el color, quitar el mando con `python scripts/quitar_mandos.py`, y poner `"propuesta": false` e `"indexar": true` solo cuando sea la web oficial en su dominio.


---

## v3 (2026-10-05)

La web pasó a la v3 de la plantilla (v3 + v3b + v3c). Método: se superpuso el código de la plantilla (`scripts/`, `js/`, `css/`, `fuente/`, `.github/`, `plantillas-hoja/`, `pruebas/`…) y se conservaron `municipio.json`, `marca/`, `media/` y `contenido/`.
- Los campos nuevos de `municipio.json` los añadió `../ayuntamiento-fuente-de-cantos-bocetos/_scripts/v3-datos.py` y las traducciones, `v3-idiomas.py`.
- Datos añadidos: `ine` (**06052**, comprobado con la tabla del padrón del INE y con el DIR3 `L01060520`), `cifras` (padrón de 2025, 251,8 km² y 582 m, que coinciden en la Diputación, Wikidata y su web, y 1293, el año del primer documento del archivo; **sin distancia a Badajoz**: 101, 100 o 98 km según la fuente), `incidencias` (al correo del Ayuntamiento, por confirmar), `canal_avisos` (el canal de WhatsApp «Ayuntamiento De Fuente De Cantos», con sus pasos; ya no se repite entre las redes), `farmacias` (solo el buscador del Colegio: sin calendario de guardias), `transparencia` (con los huecos «Pendiente»; solo enlaza las dos páginas de ordenanzas de su web, con 200 el 5/10/2026), `propuesta_web` (cinco problemas de ERRORES.md, vueltos a comprobar el 5/10/2026, y captura real de fuentedecantos.eu), cuatro fotos para el arco de la portada y la cabecera de «El pueblo».
- Arreglo de datos: `montar-municipio.mjs` había dejado repetido cinco veces «Pagar en línea una tasa o un recibo» (en «Tengo que pagar algo» y en el tema «Pagos e impuestos») y varias veces «Reservar una pista o el pabellón»; `v3-datos.py` quita los pasos repetidos.
- Sin plazos: ningún aviso dice una fecha de cierre.
- Nuevos: `contenido/facil.json` (lectura fácil: padrón, licencia de obra, pagar una tasa, reservar una pista y avisar de un problema; el pago y la reserva, según lo que dicen su portal de pagos y su web de reservas), `contenido/pueblo.en.json` y `pueblo.pt.json`, plano del pie (`way/223998587`, `amenity=townhall` «Ayuntamiento de Fuente de Cantos»), mapa del término desde OpenStreetMap (`relation/341690`; 5 de 17 lugares) y fotos igualadas (originales en `media/originales/`).
- Los 5 lugares del mapa se comprobaron uno a uno con sus etiquetas de OSM, con Nominatim (la calle) y con las coordenadas del Turismo de la Diputación: la parroquia (`way/220879930`), la Casa de Zurbarán (`node/906071528`, museo en la calle Águilas), la ermita de San Juan (`node/8883639013`, junto a la fuente de la calle Almena), el santuario de la Hermosa (`node/911479118`, a 7 m de la coordenada de la Diputación) y la Casa Consistorial (`way/223998587`). Se descartó «Los Castillejos»: el nodo de OSM es una localidad a 1,3 km del yacimiento que sitúa la Diputación. Las copias de Overpass están en `../ayuntamiento-fuente-de-cantos-bocetos/_osm/`.
- Cambios por los datos del pueblo: `scripts/verificar.mjs` (la prueba de precio ignora los `<script>`; V16 renombra la muestra a lugares de Fuente de Cantos; F25 comprueba los ids de OSM de arriba) y `css/imprimir.css` (la hoja de teléfonos de la nevera lleva 45 números: en papel, las notas de los grupos salen solo en la web, no salen las filas sin número y el alto de fila y los tamaños se compactan para que quepa en **una** A4).
- `pruebas/segura-de-leon/` es el de la plantilla; este repo no tenía ninguna carpeta de otro municipio con datos de Ribera que actualizar.
- **Pendiente**: perfil del pie real (ahora genérico), correo de incidencias y «Escríbanos» por confirmar, horario real de atención (sigue «Ejemplo»), `hoja.id` vacío, tablón sin autorización, el cierre real de la preinscripción de inglés de AUPEX (el aviso no da fecha) y revisar con una persona de habla inglesa y portuguesa las glosas de `pueblo.en/pt.json` y con personas usuarias el texto de lectura fácil.

## Verificación (v3)

`node scripts/verificar.mjs --capturas` el 5 de octubre de 2026: **174 de 174 comprobaciones** (`_verificar-v3.log`).
