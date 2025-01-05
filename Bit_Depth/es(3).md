<span style="font-size: 3.0em; line-height: 3.0;">Profundidad de
bits</span>

## Introducción

A menudo escucharás o leerás términos como "8-bit", "16-bit", "24-bit",
"32-bit", "64-bit" y "96-bit" haciendo referencia a imágenes digitales.

Este artículo aclarará lo que significan eso.


Las imágenes digitales consisten en millones de píxeles uno al lado del
otro y cada píxel tiene uno o más canales de color.

Las imágenes en escala de grises sólo necesitan un canal (un valor de 0
podría representar el negro puro, 255 podría representar el blanco puro
y los valores intermedios representarían tonos grises entre el blanco y
el negro), mientras que las imágenes en color RGB necesitan tres
canales - uno define el rojo, otro el verde y otro el azul.

Cada canal define sólo la intensidad de un color, por lo que no hay nada
intrínsecamente verde en un número del canal verde de un píxel: los
colores se derivan de la interacción entre los tres canales del [modelo
de color RGB](https://es.wikipedia.org/wiki/RGB).

Un píxel podría constar de más de tres canales: por ejemplo podría
contener información sobre un canal alfa (que describe la transparencia)
o un canal infrarrojo (que algunos escáneres soportan).


Cuanto mayor sea la profundidad de bits, con más precisión se puede
describir un color, a costa de exigir cálculos más largos, más memoria
RAM y más espacio de almacenamiento.

## ¿Bits Por Qué?

La profundidad de bits se expresa como un valor del número de **bits por
píxel** (BPP), o de **bits por canal** (BPC). El más que popular
[JPEG](https://es.wikipedia.org/wiki/Joint_Photographic_Experts_Group%7Cformato)
suele guardar las imágenes con una precisión de 8 bits por canal,
utilizando tres canales, para un total de 24 bits por píxel. El
[TIFF](https://es.wikipedia.org/wiki/TIFF%7Cformato) soporta varias
profundidades de bits, por ejemplo 32 bits por canal para un total de 96
bits por píxel.

Al nombrar la profundidad de bits, indica lo que estás describiendo para
no dejar lugar a dudas. Como ejemplo de ambigüedad: si alguien dice que
tiene una imagen de "32 bits", ¿significa que la imagen tiene 32 bits
por canal, o que tiene 4 canales de 8 bits cada uno?

## Precisión

En la práctica, ¿qué diferencia hay entre una profundidad de bits y
otra? Cuantos más bits se empleen para describir un color, con más
precisión se logrará definirlo.

- Una precisión de 1 bit por canal significa que sólo hay 1 bit para
  establecer un valor. Un bit solo puede ser 0 o 1, por lo que solo se
  pueden establecer dos valores, que normalmente significarán blanco o
  negro.
- Una precisión de 2 bits por canal significa que hay 2 bits disponibles
  para establecer el valor de cada canal. Como hay dos bits y cada uno
  puede ser 0 o 1, hay un total de 4 valores posibles:
      [00] = 0
      [01] = 1
      [10] = 2
      [11] = 3

  Si usamos 0 para representar el negro y 3 para representar el blanco,
  hay dos tonos adicionales de gris que se pueden establecer.
- Una precisión de 8 bits por canal significa que hay 8 bits que pueden
  establecer hasta 256 valores:
      [0000 0000] = 0
      [0000 0001] = 1
      (...)
      [1111 1110] = 254
      [1111 1111] = 255

  Si usamos 0 para representar el negro y 255 para representar el
  blanco, también se pueden establecer 254 tonos de gris. Esto es lo que
  usan los archivos JPEG: 8 bits por canal, con 3 canales de color. En
  general es suficiente si utilizas esta profundidad para guardar tus
  fotografías en el [de color
  sRGB](https://es.wikipedia.org/wiki/Espacio_de_color_sRGB%7Cespacio),
  sin
  [1](https://es.wikipedia.org/wiki/Posterizaci%C3%B3n%7Cposterización)
  visible. Así que, obviamente puedes usarla cuando guardes las
  fotografías que ya estén listas para que las vean a través de
  Internet. No es adecuada para fotografías que no estén acabadas de
  procesar (lo que se suele llamar "formato intermedio"), ni para
  fotografías acabadas (o "formato final") si existe la posibilidad de
  que tengas que modificar la fotografía en un futuro, ya que corres el
  riesgo de introducir artefactos de posterización, dependiendo de la
  intensidad de los ajustes aplicados. Una profundidad de 8 bits no es
  suficiente para reproducir una escena de alto rango dinámico con una
  gama lineal y sin posterización. Es decir, en teoría se podrían
  utilizar 8 bits para describir una escena de alto rango dinámico con
  una gama lineal, pero los tonos asignados a cada valor estarían tan
  separados que se produciría una enorme posterización. Por ejemplo,
  supongamos que en una fotografía capturas un día soleado en el campo,
  con una relación de contraste de 1 000 000:1. Si decidimos que el
  negro debe ser el 0 y el blanco el valor 1 000 000, podríamos asignar
  el valor 0 al 0 y el valor 255 al 1 000 000; sin embargo, entonces
  sólo quedarían 254 valores (de la codificación en 8 bits) a los que
  asignar el resto de 999 999 matices de la escena original.
- Una profundidad de 16 bits por canal (con números enteros) significa
  que tenemos números binarios con 16 ceros y/o unos. Con las
  combinaciones posibles se pueden establecer 65536 valores:
      [0000 0000 0000 0000] = 0
      [0000 0000 0000 0001] = 1
      (...)
      [1111 1111 1111 1110] = 65534
      [1111 1111 1111 1111] = 65535

  Las cámaras digitales suelen capturar la luz con una profundidad de 12
  ó 14 bits, pero debido al ruido y a la imprecisión de la electrónica,
  los valores más bajos son de dudosa calidad. 16 bits por canal son
  suficientes para la mayoría de las necesidades fotográficas,
  incluyendo el uso en formatos intermedios (si deseas pasar una imagen
  de un programa a otro sin pérdida de detalles).
- Los valores de una imagen de 16 bits [coma
  flotante](https://es.wikipedia.org/wiki/Coma_flotante%7Cen), también
  conocida como [flotante de media precisión (sin traducción al
  castellano)](https://en.wikipedia.org/wiki/Half-precision_floating-point_format%7Ccoma),
  se distribuyen de una manera más adecuada para el muestreo de luz que
  en la misma imagen en 16 bits con números enteros. Esto es así por
  varias razones: la visión humana es más sensible a pequeños cambios en
  los tonos oscuros que a pequeños cambios en los tonos brillantes;
  nuestros ojos responden a la luz de una manera logarítmica (la luz
  debe ser 10 veces más intensa para que podamos verla el doble de
  brillante); y los reflejos especulares, que pueden ser los elementos
  más brillantes de una escena (el sol reflejándose en el pomo de una
  puerta), no necesitan ser definidos con la misma precisión que los
  demás tonos. En la notación en coma flotante de 16 bits, los valores
  se distribuyen más apretadamente en los tonos más oscuros (valores más
  bajos) que en los más claros (valores altos), lo que permite una
  definición más precisa de los tonos más relevantes para nosotros.
- Una imagen de 32 bits [coma
  flotante](https://es.wikipedia.org/wiki/Coma_flotante%7Cen) puede
  representar 4.300 millones de valores por canal y requiere
  aproximadamente el doble de espacio en disco que una imagen de 16
  bits. Pocos programas son compatibles con las imágenes de 32 bits.

Una de las razones por las que la profundidad de bits afecta
principalmente a las sombras, se debe a la forma en que se codifican los
colores. Cada color está definido mediante una mezcla de rojo, verde y
azul. Poniendo como ejemplo una imagen de 8 bits y el color naranja,
pueden escogerse muchos valores cuando se codifica el naranja brillante,
pero hay muy pocos valores disponibles para codificar el naranja oscuro;
es decir, sólo los 3-4 valores más bajos de cada canal pueden ser usados
para definir (codificar) el naranja oscuro, lo cual significa que sólo
existen unos 16 valores posibles para codificar todo un rango de tonos
oscuros. Cuanto mayor sea la profundidad de bits, más colores se pueden
definir y se evita la posterización.

## Codificación Gama

La
[gamma](https://es.wikipedia.org/wiki/Correcci%C3%B3n_gamma%7Ccodificación)
puede utilizarse al guardar las imágenes, de manera que al usarla los
valores se modificarán asignando más cantidad en el rango de las sombras
que en el rango de las altas luces, lo cual se ajusta mejor a la
sensibilidad que tiene el ojo humano. Con éllo se consigue que un JPEG
de 8 bits pueda mostrar hasta log2((1/2^8)^2.2) = 17.6 pasos de rango
dinámico, lo cual excede los 14 pasos de las mejores cámaras actuales.
Esto explica por qué a veces se puede ver el ruido de las sombras de una
cámara incluso en un JPEG de 8 bits. Sin embargo, debido a la
distribución no lineal de los valores (mayor densidad de valores en las
sombras, menor densidad en la altas luces), perdemos precisión en
comparación con el archivo raw (con los valores grabados de forma lineal
por la cámara). En la práctica esto no es un problema siempre que el
archivo generado sea el definitivo y que no se vaya procesar más. Sin
embargo, una foto puede mejorarse enormemente cuando se guarda como
datos en bruto (raw) y se procesa utilizando un programa de
procesamiento de datos raw de última generación, como su seguro
servidor, RawTherapee.

## Después de RawTherapee

Una vez que hayas procesado una foto en RawTherapee y te dispongas a
[guardarla](Saving_Images/es "wikilink"), siempre tendrás la misma duda:
qué formato de archivo, qué profundidad de bits por canal, [qué perfil
de color y qué gamma](Color_Management/es#Perfil_de_Salida "wikilink")
usar. Si después de exportarlas en RawTherapee piensas posprocesar tus
fotos en un programa de edición de imágenes de 16 bits, es mejor
guardarlas en un formato de 16 bits sin pérdidas (lossless). RawTherapee
puede guardar imágenes con una precisión de 16 bits con números enteros
(denominada "TIFF (16-bit)" o "PNG (16-bit)" en el cuadro de diálogo
Guardar), así como con una precisión de 16 bits en coma flotante
(denominada "TIFF (16-bit float)"). El formato TIFF sin comprimir de 16
bits con números enteros es el recomendado como formato intermedio, ya
que es el más rápido de guardar en el disco y además es ampliamente
aceptado (soportado) por otros programas. Los archivos de 32 bits tienen
aproximadamente el doble de tamaño y no son bien soportados por otros
programas.