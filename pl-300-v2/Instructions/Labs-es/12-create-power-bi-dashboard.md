---
lab:
    title: 'Create dashboards in Power BI'
    module: 'Create dashboards in Power BI'
---

# Crear dashboards en Power BI

## Historia del laboratorio

En este laboratorio, crearás el dashboard **Sales Monitoring** en el servicio Power BI utilizando un informe existente.

En este laboratorio, aprenderás a:

- Fijar visuales en un dashboard.
- Usar Q&A para crear tiles en el dashboard.

**Este laboratorio debería tomar aproximadamente 30 minutos.**

## Comenzar

Para completar este ejercicio, primero abre un navegador web e ingresa la siguiente URL para descargar la carpeta zip:

`https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst/raw/Main/Allfiles/Labs/12-create-power-bi-dashboard/12-create-dashboard.zip`

Extrae la carpeta en **C:\Users\Student\Downloads\12-create-dashboard**.

## **Publicar el informe**

En esta tarea, configurarás el entorno para el laboratorio creando un modelo semántico.

1. En la ventana del navegador Microsoft Edge, en el servicio Power BI, navega a **My Workspace**.

1. Selecciona **Import > Report or Paginated Report > From this computer**.

1. Navega a la carpeta **C:\Users\Student\Downloads\12-create-dashboard**.

1. Selecciona el archivo **12-Starter-Sales Analysis.pbix**, y luego selecciona **Open**.

    > _Si se te solicita reemplazar el modelo semántico, selecciona **Replace it**._

## **Crear un dashboard**

En esta tarea, crearás el dashboard **Sales Monitoring**. Fijarás un visual del informe, agregarás un tile basado en una URI de datos de imagen y usarás Q&A para crear un tile.

1. En el servicio Power BI, abre el informe **12-Starter-Sales Analysis**.

1. En la página **Overview**, configura el slicer **Year** a **FY2020**.

    ![Imagen 4](Linked_image_Files/12-create-power-bi-dashboard_image17.png)

1. Configura el slicer **Region** a **Select All**.

    > _Los visuales fijados se configuran con el contexto de filtro al momento de fijarlos. Si el visual subyacente cambia, necesitarás actualizar el tile del dashboard también. Para filtros basados en tiempo, es mejor usar un slicer de fecha relativa (o Q&A con una pregunta basada en tiempo relativo)._

1. Para crear un dashboard y fijar un visual, pasa el cursor sobre el visual **Sales and Profit Margin by Month** (columna/línea) y selecciona el icono de pushpin.

    ![Imagen 43](Linked_image_Files/12-create-power-bi-dashboard_image18.png)

1. En la ventana **Pin to Dashboard**, en el cuadro **Dashboard Name**, ingresa **Sales Monitoring**, luego selecciona **Pin**.

    ![Imagen 3](Linked_image_Files/12-create-power-bi-dashboard_image19.png)

1. Abre **My Workspace** y abre el dashboard **Sales Monitoring**.

1. Observa que el dashboard tiene un solo tile.

    ![Imagen 45](Linked_image_Files/12-create-power-bi-dashboard_image22.png)

1. Para agregar un tile basado en una pregunta, en la parte superior izquierda del dashboard, selecciona **Ask a Question About Your Data**.

    *Puedes usar la función Q&A para hacer una pregunta, y Power BI responderá con un visual.*

    ![Imagen 7](Linked_image_Files/12-create-power-bi-dashboard_image23.png)

1. Selecciona cualquiera de las preguntas sugeridas debajo del cuadro Q&A y revisa la respuesta.

1. Elimina todo el texto del cuadro Q&A e ingresa lo siguiente: **Sales YTD**

1. Observa la respuesta **(Blank)**.

    > _Puedes recordar que agregaste la medida **Sales YTD** en el laboratorio **Create Advanced DAX Calculations in Power BI Desktop**. Esta medida es una expresión de Time Intelligence y por lo tanto requiere un filtro en la tabla **Date** para producir un resultado._

    ![Imagen 14](Linked_image_Files/12-create-power-bi-dashboard_image25.png)

1. Extiende la pregunta con: **in year FY2020**.

1. Observa que la respuesta ahora es **$33M**.

    ![Imagen 13](Linked_image_Files/12-create-power-bi-dashboard_image27.png)

1. Para fijar la respuesta al dashboard, en la esquina superior derecha, selecciona **Pin Visual**.

    ![Imagen 15](Linked_image_Files/12-create-power-bi-dashboard_image28.png)

1. Cuando se te solicite fijar el tile al dashboard **Sales Monitoring**, selecciona **Pin**.

1. Para regresar al dashboard, en la esquina superior izquierda, selecciona **Exit Q&A**.

1. Para agregar el logo de la compañía, en la barra de menú, selecciona **Edit**, y luego selecciona **Add a Tile**.

    > _Usar esta técnica para agregar un tile al dashboard te permite mejorar tu dashboard con medios, incluyendo contenido web, imágenes, cuadros de texto con formato enriquecido y video (usando enlaces de YouTube o Vimeo)._

1. En el panel **Add a Tile** (ubicado a la derecha), selecciona el tile **Image**, luego **Next**.

1. Navega a la carpeta **C:\Users\Student\Downloads\12-create-dashboard** y abre el archivo **AdventureWorksLogo_DataURL.txt**.

1. En el panel **Add Image Tile**, en el cuadro **URL**, pega la URL del archivo de texto, y luego selecciona **Apply**.

    > _Puedes incrustar una imagen usando su URL, o puedes usar una data URL, que incrusta el contenido en línea._

1. Para redimensionar el tile del logo, arrastra la esquina inferior derecha y redimensiona el tile para que tenga una unidad de ancho y una unidad de alto.

    > _Los tamaños de los tiles están limitados a una forma rectangular._

1. Organiza los tiles para que el logo aparezca en la parte superior izquierda, con el tile **Sales YTD** debajo y el tile **Sales, Profit Margin** a la derecha.

    ![Imagen 52](Linked_image_Files/12-create-power-bi-dashboard_image35.png)

## **Editar detalles del tile**

En esta tarea, editarás los detalles de dos tiles.

1. Pasa el cursor sobre el tile **Sales YTD**, y luego en la parte superior derecha del tile, selecciona los puntos suspensivos, y luego selecciona **Edit Details**.

    ![Imagen 50](Linked_image_Files/12-create-power-bi-dashboard_image36.png)

1. En el panel **Tile Details** (ubicado a la derecha), en el cuadro **Subtitle**, ingresa **FY2020**, y luego selecciona **Apply**.

1. Observa que el tile **Sales YTD** muestra un subtítulo.

    ![Imagen 21](Linked_image_Files/12-create-power-bi-dashboard_image39.png)

1. Edita los detalles del tile para **Sales, Profit Margin**.

1. En el panel **Tile Details**, en la sección **Functionality**, marca **Display Last Refresh Time**, y luego selecciona **Apply**.

    ![Imagen 22](Linked_image_Files/12-create-power-bi-dashboard_image40.png)

1. Observa que el tile muestra la última hora de actualización (que se realizó al cargar el modelo de datos en Power BI Desktop).

*Actualizarás el modelo semántico en el siguiente ejercicio. Dependiendo de tus datos e informe, puedes hacer una actualización de datos adhoc en cualquier momento o programarla. Sin embargo, las actualizaciones programadas requieren gateways que no podremos configurar para este laboratorio. Así que desde Power BI Desktop, realizarás una actualización manual de datos y luego cargarás el archivo a tu workspace.*

## **Actualizar el modelo semántico**

En este ejercicio, primero cargarás datos de órdenes de venta para junio de 2020 en la base de datos **AdventureWorksDW2020**. Luego abrirás tu archivo de Power BI Desktop, realizarás una actualización de datos y luego cargarás el archivo a tu workspace.

> _**Nota**: Si no puedes conectarte a la base de datos, puedes usar el archivo **12-Solution-Sales-Analysis.pbix**. En lugar de actualizar la base de datos y refrescar el modelo semántico, carga el archivo de solución a **My workspace** y observa los cambios mencionados en las siguientes tareas._

## **Actualizar la base de datos del laboratorio**

En esta tarea, ejecutarás un script de PowerShell para actualizar datos en la base de datos **AdventureWorksDW2020**.

1. En el Explorador de archivos, dentro de la carpeta **C:\Users\Student\Downloads\12-create-dashboard**, haz clic derecho en el archivo **UpdateDatabase-2-AddSales.ps1**, y luego selecciona **Run with PowerShell**.

    ![Imagen 28](Linked_image_Files/12-create-power-bi-dashboard_image46.png)

1. Si se te solicita cambiar la política de ejecución, presiona **A**.

1. Cuando se te solicite presionar cualquier tecla para cerrar, presiona **Enter** nuevamente.

*La base de datos **AdventureWorksDW2020** ahora incluye órdenes de venta realizadas en junio de 2020.*

## **Actualizar el archivo de Power BI Desktop**

En esta tarea, abrirás el archivo de Power BI Desktop **12-Starter-Sales Analysis**, realizarás una actualización de datos y luego cargarás el archivo a tu workspace **Sales Analysis**.

1. En el archivo de Power BI Desktop, en el panel **Data**, haz clic derecho en la tabla **Sales**, y luego selecciona **Refresh Data**.

    ![Imagen 55](Linked_image_Files/12-create-power-bi-dashboard_image47.png)

1. Cuando la actualización se complete, guarda el archivo de Power BI Desktop.

1. Para publicar el archivo en tu workspace, en la pestaña **Home**, dentro del grupo **Share**, selecciona **Publish** y luego selecciona **Select** para publicar.

    ![Imagen 59](Linked_image_Files/12-create-power-bi-dashboard_image48.png)

1. Cuando se te solicite reemplazar el modelo semántico, selecciona **Replace**.

1. Cierra Power BI Desktop.

*El modelo semántico en el servicio Power BI ahora tiene datos de ventas de junio de 2020.*

### **Revisar el dashboard**

En esta tarea, revisarás el dashboard para observar las ventas actualizadas.

1. En la ventana del navegador Microsoft Edge, abre el servicio Power BI, y luego revisa el dashboard **Sales Monitoring** en **My Workspace**.

2. En el tile **Sales, Profit Margin**, junto al subtítulo, observa que los datos fueron **Refreshed: NOW**.

3. Observa también que ahora hay una columna para **2020 Jun**.

    > _Si no ves los datos de junio de 2020, es posible que necesites presionar **F5** para recargar el navegador web._

    ![Imagen 33](Linked_image_Files/12-create-power-bi-dashboard_image50.png)

## Laboratorio completado
