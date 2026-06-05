# ⋆⭒˚.⋆ └[∵┌] Web para filtrar cuerpos [┐∵]┘ ⋆.˚⭒⋆

<https://camila-parada.github.io/filtro-cuerpos/>

***

## Qué es
Una app web de filtrado automático de imágenes para tu proyecto "Chile Íntimo". Te ayuda a decidir, de un lote grande de fotos, cuáles muestran un "cuerpo" en condiciones útiles para tu investigación y cuáles descartar, sin tener que revisarlas una por una a mano.

## Qué mide
Sobre cada imagen evalúa tres cosas, todas a partir de la detección de personas:
- **Persona sola**: cuántas personas hay (1 = sola, 2+ = acompañada).
- **Cuerpo protagonista**: si la persona ocupa suficiente espacio para ser el sujeto y no un elemento de fondo.
- **Encuadre**: en qué categoría cae la toma (cuerpo completo, medio cuerpo, primer plano, detalle/zoom, o cuerpo secundario).

Con eso entrega un veredicto INCLUIR o DESCARTAR por foto, según los criterios que marques como obligatorios.

## Cómo lo mide
Usa un modelo de detección de objetos que dibuja una "caja" alrededor de cada persona. De esa caja saca números objetivos:
- **Número de cajas "persona"** → resuelve persona sola.
- **Cobertura** = área de la persona ÷ área de la imagen → resuelve protagonista vs. secundario.
- **Altura relativa** = alto de la caja ÷ alto de la foto → define el encuadre.

Tú fijas los umbrales con deslizadores (cuánta cobertura cuenta como "protagonista", qué altura es "cuerpo completo", etc.) y el veredicto se recalcula al instante. No hay criterio oculto: cada decisión sale de una medida visible.

## Qué recursos usa
- **COCO-SSD sobre TensorFlow.js**: un modelo de detección que corre dentro del navegador, gratis y sin límite de uso.
- Las librerías se descargan de CDN públicos la primera vez (después quedan en caché).
- **No usa ninguna API de pago** (ni Gemini ni similares), no requiere clave, no tiene servidor propio.
- Está alojada en GitHub Pages como un único archivo HTML.

## Lo más importante de destacar
- **Privacidad**: las fotos se procesan localmente en el navegador de cada persona; **nunca se suben a ningún servidor**. Esto es relevante éticamente porque trabajas con imágenes de cuerpos de personas reales.
- **Gratis e ilimitada**: pueden usarla varias personas del equipo desde la URL pública, sin costo.
- **Acelera, no reemplaza**: es un primer pase que ordena y pre-clasifica; el encuadre es orientativo (puede confundir un primer plano de rostro con un zoom de mano), así que conviene una revisión humana rápida de los casos borde.
- **Exporta a CSV** con todas las medidas y el veredicto, para volcarlo directo a tu Excel de filtrado.
- **Límite conocido**: detecta "persona" pero no identifica *quién* es la titular de la cuenta; por eso el criterio de persona sola opera por conteo (si hay 2+, descarta).

## El encaje metodológico
Cubre justo los tres criterios que decidiste automatizar, mientras tú conservas a mano el paso de "¿hay cuerpo humano?" y la decisión de no intervenir/recortar el material original. Es coherente con tu marco: filtra para dejar solo imágenes legibles, que es la antesala del análisis posterior con el espectro de permanencia.

***

## Proyecto hecho con Claude
Análisis automático
