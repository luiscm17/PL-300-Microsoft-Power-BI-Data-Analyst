---
lab:
    title: 'Crear cálculos visuales en Power BI Desktop'
    module: 'Crear cálculos visuales en Power BI Desktop'
---

# Crear cálculos visuales en Power BI Desktop

## **Historia del laboratorio**

En este laboratorio, crearás cálculos visuales usando Data Analysis Expressions (DAX).

En este laboratorio aprenderás cómo:

- Crear y editar cálculos visuales
- Usar las funciones PREVIOUS(), RUNNINGSUM() y MOVINGAVERAGE() para crear métricas de comparación entre cada año fiscal
- Usar el parámetro opcional Axis al crear métricas de comparación
- Usar el parámetro opcional Reset para personalizar cálculos acumulativos en un eje multinivel

**Este laboratorio debería tomar aproximadamente 30 minutos.**

## Comenzar

Para completar este ejercicio, primero abre un navegador web e ingresa la siguiente URL para descargar la carpeta comprimida:

`https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst/raw/Main/Allfiles/Labs/05b-create-visual-calculations-in-power-bi-desktop/05b-visual-calculations.zip`

Extrae la carpeta en la ubicación: **C:\Users\Student\Downloads\05b-visual-calculations**.

Abre el archivo **05b-Starter-Sales Analysis.pbix**.

> ***Nota**: Puedes omitir el inicio de sesión seleccionando **Cancelar**. Cierra cualquier otra ventana informativa. Selecciona **Aplicar más tarde** si se te solicita aplicar cambios.*

## Crear un gráfico de barras

En esta tarea, crearás un gráfico de barras que muestra monto de ventas, costo total de producto y ganancia por año fiscal, con métricas de comparación como tooltips.

1. En el panel **Visualizations**, selecciona el tipo de visual gráfico de barras agrupadas.

   ![Picture 01](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image01.png)

1. En el panel **Data**, desde la tabla **Date**, arrastra el campo **Year** al área **Y-axis**.

1. Arrastra los campos **Sales** y **Cost** de la tabla **Sales** al área **X-axis**.

> Nota que cuando agregaste Sales y Cost al visual, la suma de cada campo se calculó automáticamente.

1. Ordena el gráfico de barras por **Year** ascendente usando el menú de tres puntos y seleccionando **Year** seguido de **Sort ascending**:

   ![Picture 02](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image02.png)

> Ahora tienes un gráfico de barras que muestra la Suma de Ventas y Suma de Costos por Año ordenados cronológicamente.

### Agregar cálculos

1. Con el gráfico de barras seleccionado, selecciona **New visual calculation** en la cinta:

   ![Picture 03](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image03.png)

1. Se abre la ventana de edición de cálculos visuales. En la barra de fórmulas sobre la matriz visual ingresa la siguiente expresión y presiona Enter para confirmar:

   ```DAX
   Profit = [Sum of Sales] – [Sum of Cost]
   ```

1. Confirma que ahora ves una columna Profit en la matriz visual en la parte inferior:

   ![Picture 04](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image04.png)

1. Expande el menú bajo **New visual calculation** y selecciona **Versus previous** de las opciones de plantilla:

> **Versus Previous** compara un valor con el valor anterior, así vemos la Ganancia comparada con el valor anterior del Año.

   ![Picture 05](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image05.png)

1. En la barra de fórmulas, reemplaza el marcador `[Field]` con `[Profit]` dos veces y confirma el cálculo.

1. Selecciona **Running sum** del menú de plantillas y reemplaza `[Field]` con `[Profit]` y confirma el cálculo.

> **Running sum** calcula la suma de valores, agregando el valor actual a los anteriores, así vemos el total de años actuales y previos.

1. Selecciona **Moving average** del menú de plantillas y reemplaza `[Field]` con `[Profit]` y `WindowSize` con 2. Deberías tener ahora:

> **Moving average** calcula un promedio de un conjunto de valores en una ventana dada dividiendo la suma por el tamaño de la ventana. Al establecer el tamaño en 2, calculamos el promedio de dos valores consecutivos. En este ejemplo, los valores son ganancias anuales, así el promedio móvil para FY2019 es el promedio de ganancias para FY2018 y FY2019.

   ![Picture 06](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image06.png)

1. Bajo el área **X-axis**, selecciona el icono de visibilidad de estos campos para ocultarlos del visual:

   - Sum of Sales
   - Sum of Cost
   - Profit

   ![Picture 07](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image07.png)

> Nota cómo los campos y cálculos ocultos ya no se muestran en el visual.

1. En el panel **Visualizations**, arrastra **Running sum** y **Moving average** al área **Tooltips**.  

1. Confirma que el visual cumple los objetivos. Sal de la pantalla de edición de cálculos visuales:

   ![Picture 08](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image08.png)

> Ahora tienes un gráfico de barras con: Suma de Ventas, Suma de Costos, Ganancia, y Ganancia *versus previous* con tooltips para *running sum* y *moving average* de Ganancia.

## Crear un visual de matriz

En esta tarea, crearás una matriz que compare el monto de ventas por categoría contra el primer año fiscal para cada año siguiente.

1. En **Vista de informe**, crea una nueva página.

1. En **Page 2**, agrega un visual de matriz.

1. Agrega estos campos a las áreas del visual:

     - Rows: **Product \| Category**
     - Columns: **Date \| Year**
     - Values: **Sales \| Sales**

 > *Los laboratorios usan notación abreviada para campos: **Date \| Year**. **Date** es la tabla y **Year** el campo.*

### Agregar cálculos

1. Con la matriz seleccionada, selecciona **New visual calculation** en la cinta.

1. En la ventana de edición, ingresa y guarda este cálculo:

   ```DAX
    Versus first = [Sum of Sales] - FIRST([Sum of Sales])
   ```

> Nota cómo la matriz muestra la diferencia en ventas por categoría contra la primera categoría.

1. Selecciona el campo **Versus first** en **Values** y actualiza el cálculo agregando ROWS como parámetro Axis a FIRST:

   ```DAX
    Versus first = [Sum of Sales] - FIRST([Sum of Sales], ROWS)
   ```

> Nada cambia ya que ROWS es el valor predeterminado para Axis.

1. Reemplaza ROWS con COLUMNS y observa que ahora compara ventas por categoría contra el primer año fiscal:

   ![Picture 11](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image11.png)

> Nota que **Total Sales** devuelve cero en lugar de la diferencia contra el primer año fiscal. **Total Sales** está en un nivel jerárquico diferente.

1. Sal de la pantalla de edición.

## Crear un gráfico de líneas

En esta tarea, crearás un gráfico de líneas que muestre la suma acumulativa de ventas, reiniciando cada año fiscal.

1. En **Vista de informe**, crea una nueva página.

1. En **Page 3**, agrega un gráfico de líneas.

1. Agrega estos campos:

     - X-axis: **Date \| Year** y **Date \| Quarter**
     - Y-axis: **Sales \| Sales**

### Agregar suma acumulativa

1. Con el gráfico seleccionado, expande **New visual calculation** y selecciona **Running sum**.

1. Reemplaza `[Field]` con `[Sum of Sales]` y confirma. El visual debería verse así:

   ![Picture 09](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image09.png)

### Actualizar para reiniciar cada año fiscal

1. En la ventana de edición, selecciona **Running sum** en **Y-axis** y actualiza la expresión agregando HIGHESTPARENT como parámetro Reset:

   ```DAX
    Running sum = RUNNINGSUM([Sum of Sales], HIGHESTPARENT)
   ```

Verifica que la suma se reinicia cada año fiscal:

   ![Picture 10](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image10.png)

## Laboratorio completado
