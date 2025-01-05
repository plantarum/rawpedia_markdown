## Revelado por lotes

El procedimiento general es seleccionar una imagen clave o
representativa del grupo a modificar y revelarla completamente según se
desee. A continuación, tras volver al *Explorador de archivos*, haz
sobre la imagen y dentro de ***Operaciones con el [perfil de
procesamiento](Sidecar_Files_-_Processing_Profiles/es "wikilink")***,
haz en **Copiar**. Después, tras seleccionar las imágenes necesarias,
sobre una de éllas haz y dentro de *Operaciones con el perfil de
procesamiento*, haz en **Pegar** o en **Pegar - parcialmente**.

Copiar y pegar un perfil de procesamiento a una selección de imágenes es
una tarea muy común. Supongamos que has tomado una serie de fotos, por
ejemplo tomas de estudio, retratos de boda o fotos macro con apilado de
enfoque. Todas las imágenes van a ser muy similares: probablemente
usarán el mismo objetivo, la misma ISO, el mismo equilibrio de blancos,
y acabarán destinándose al mismo propósito. Esto significa que
probablemente todas necesitarán los mismos parámetros de procesamiento:
la misma reducción de ruido, la misma nitidez, corrección de la
distorsión del objetivo y así sucesivamente.

Además, RawTherapee te permite aplicar solamente una parte del perfil de
procesamiento copiado, por ejemplo solamente la herramienta
"Exposición". Para hacer ésto, usa la opción *Pegar - parcialmente*,
mientras que si quieres aplicar todos los ajustes en todas las fotos
seleccionadas, usa la opción *Pegar*.

## Sincronizar

También es posible seleccionar un número cualquiera de imágenes, y
ajustar cualquier herramienta en todas ellas a la vez.

RawTherapee permite aplicar instantáneamente los ajustes realizados en
las herramientas a una selección de imágenes. Esta funcionalidad es
similar a la de otros programas y en general se llama ***sincronizar***.

Este método es útil cuando **no necesitas** ver una previsualización
precisa de tus cambios, como por ejemplo cuando sólo quieres activar la
herramienta *Cambiar tamaño* en una selección de fotos. Y ésto es así
porque trabajando en la pestaña *Explorador de archivos*, la única
previsualización disponible son las miniaturas, pequeñas e imprecisas.

La sincronización sólo puede usarse desde la pestaña *Explorador de
archivos* porque necesitas acceder a las *herramientas de
sincronización* del panel *Revelar*, a la derecha. Estas herramientas
son las mismas que encontrarás en la pestaña del *Editor*, pero sólo se
usan para la *sincronización*.

Tus retoques pueden o bien reemplazar los existentes (modo
***Establecer***), o sumarlos (modo ***Añadir***). Por ejemplo,
supongamos que seleccionas dos fotos, una de las cuales ha sido retocada
con **+1EV** de *Compensación de exposición* y la otra sin retocar. Si
en la herramienta de sincronización *Exposición* ajustas la
*Compensación de exposición* a **+0.6EV**, entonces la foto que ya
estaba editada tendría una *Compensación de exposición* de **+1.6EV** en
modo *Añadir* y sólo **+0.6EV** en modo *Establecer*. La foto que no
había sido previamente retocada tendría **+0.6EV** en ambos modos.

Para decidir en qué modo debe funcionar cada herramienta de
sincronización, debes establecerlo en la [**pestaña Procesamiento por
lotes**, de las
*Preferencias*](Preferences/es#Batch_Processing_Tab "wikilink").