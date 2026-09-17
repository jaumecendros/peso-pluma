# Peso Pluma

Compresor de imágenes para campañas de email (Klaviyo). Todo el procesado
ocurre en el navegador: ninguna imagen se sube a ningún servidor.

## Qué hace

1. **Redimensiona** al ancho real de la plantilla — 600 px de columna, 1200 px
   exportados para retina. Reduce por mitades sucesivas en vez de un salto
   directo, que es de donde sale el aliasing.
2. **Busca la calidad justa.** Por cada imagen mide primero su techo y luego
   busca por bisección la calidad más baja que sigue quedándose dentro del
   margen elegido. El listón es relativo a cada imagen: una foto con grano y un
   fondo liso no se miden con la misma vara.
3. **Compara los tres formatos** con el mismo listón y se queda con el más
   ligero. Con pocos colores, el PNG con paleta reducida suele ganar de calle.

## Detalles que importan

- El reenfoque lleva umbral: solo toca bordes reales, así que el grano de un
  fondo plano no se amplifica.
- La fidelidad se mide sobre las imágenes ligeramente desenfocadas. El grano es
  ruido sin correlación; sin ese paso la métrica gasta todo su margen en
  reproducirlo y deja que se rompan los bordes del texto.
- Los GIF animados pasan intactos: reencodearlos dejaría un solo fotograma.
- Al reexportar se pierden los metadatos: EXIF, GPS y perfiles de color.

## Cómo se usa

Un único archivo, sin build ni dependencias. Ábrelo en el navegador o súbelo a
cualquier hosting estático.
