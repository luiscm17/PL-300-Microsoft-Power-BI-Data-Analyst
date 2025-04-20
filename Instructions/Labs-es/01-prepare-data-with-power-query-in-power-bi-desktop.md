---
lab:
    title: 'Obtener datos en Power BI Desktop'
    module: 'Obtener datos en Power BI'
---

# Obtener datos en Power BI Desktop

## **Historia del laboratorio**

Este laboratorio está diseñado para introducirle a la aplicación Power BI Desktop, cómo conectarse a los datos y cómo utilizar las técnicas de vista previa de datos para comprender las características y la calidad de los datos de origen. Los objetivos de aprendizaje son:

- Abrir Power BI Desktop
- Conectarse a diferentes fuentes de datos
- Vista previa de datos de origen con Power Query
- Usar funciones de perfilado de datos en Power Query

**Este laboratorio debería tomar aproximadamente 30 minutos.**

## Comenzar con Power BI Desktop

Para completar este ejercicio, primero abra un navegador web e ingrese la siguiente URL para descargar la carpeta zip:

`https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst/raw/Main/Allfiles/Labs/01-prepare-data-with-power-query-in-power-bi-desktop/01-prepare-data.zip`

Extraiga la carpeta en **C:\Users\Student\Downloads\01-prepare-data**.

Abra el archivo **01-Starter-Sales Analysis.pbix**.

- Este archivo de inicio ha sido especialmente configurado para ayudarle a completar el laboratorio. Las siguientes configuraciones a nivel de informe han sido deshabilitadas en el archivo de inicio:

  - Carga de datos > Importar relaciones desde fuentes de datos en la primera carga
  - Carga de datos > Autodetectar nuevas relaciones después de cargar los datos

## Obtener datos desde SQL Server

Esta tarea le enseña cómo conectarse a una base de datos SQL Server e importar tablas, lo que crea consultas en Power Query.

1. En la pestaña de la cinta **Inicio**, dentro del grupo **Datos**, seleccione **SQL Server**.

     ![Icono Obtener datos de SQL Server](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image11.png)

1. En la ventana **Base de datos SQL Server**, en el cuadro **Servidor**, ingrese **localhost** y deje **Base de datos** en blanco, luego seleccione **Aceptar**.

    > ***Nota**: En este laboratorio, se conectará a la base de datos SQL Server usando **localhost** porque las fuentes de datos de gateway no pueden resolver **localhost**. Esta no es una práctica recomendada al crear sus propias soluciones.*

1. Si se le solicitan credenciales, seleccione **Windows > Usar mis credenciales actuales**, y luego **Conectar**.

1. Seleccione **Aceptar** si recibe una advertencia de que no se puede establecer una conexión cifrada.

1. En el panel **Navegador**, expanda la base de datos **AdventureWorksDW2020**.

    > ***Nota**: La base de datos **AdventureWorksDW2020** está basada en la base de datos de ejemplo **AdventureWorksDW2017**. Ha sido modificada para soportar los objetivos de aprendizaje de los laboratorios del curso.*

1. Seleccione la tabla **DimEmployee** y observe la vista previa de los datos de la tabla.

     ![Base de datos AdventureWorksDW2020 con DimEmployee indicado](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image18.png)

    > ***Nota**: La vista previa de datos le permite ver las columnas y una muestra de las filas.*

1. Para importar los datos de la tabla, **marque la casilla** junto a las siguientes tablas:

    - DimEmployee
    - DimEmployeeSalesTerritory
    - DimProduct
    - DimReseller
    - DimSalesTerritory
    - FactResellerSales

1. Complete esta tarea seleccionando **Transformar datos**, lo que abrirá el Editor de Power Query - déjelo abierto para la siguiente tarea.

Ahora se ha conectado a seis tablas desde una base de datos SQL Server.

## **Vista previa de datos en el Editor de Power Query**

Esta tarea introduce el Editor de Power Query y le permite revisar y perfilar los datos. Esto le ayuda a determinar cómo limpiar y transformar los datos más adelante. También revisará las tablas de dimensiones con prefijo "Dim" y las tablas de hechos con prefijo "Fact".

1. En la ventana del **Editor de Power Query**, a la izquierda, observe el panel **Consultas**. El panel **Consultas** contiene una consulta por cada tabla que marcó.

     ![Lista de consultas cargadas](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image20.png)

1. Seleccione la primera consulta—**DimEmployee**.

    > *La tabla **DimEmployee** en la base de datos SQL Server almacena una fila por cada empleado. Un subconjunto de las filas de esta tabla representa a los vendedores, que serán relevantes para el modelo que desarrollará.*

1. En la esquina inferior izquierda de la barra de estado, se proporcionan algunas estadísticas de la tabla—la tabla tiene 33 columnas y 296 filas.

     ![Recuento de 33 columnas, 296 filas](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image22.png)

1. En el panel de vista previa de datos, desplácese horizontalmente para revisar todas las columnas. Observe que las últimas cinco columnas contienen enlaces **Tabla** o **Valor**.

    > *Estas cinco columnas representan relaciones con otras tablas en la base de datos. Se pueden usar para unir tablas. Unirá tablas en el laboratorio **Cargar datos transformados en Power BI Desktop**.*

1. Para evaluar la calidad de las columnas, en la pestaña de la cinta **Vista**, dentro del grupo **Vista previa de datos**, marque **Calidad de columna**. La función de calidad de columna le permite determinar fácilmente el porcentaje de valores válidos, errores o vacíos encontrados en las columnas.

     ![Selección de Calidad de columna en la cinta](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image23.png)

1. Observe que la columna **Position** tiene 94% de filas vacías (nulas).

     ![Calidad de columna mostrando 94% de filas vacías](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image24.png)

1. Para evaluar la distribución de columnas, en la pestaña de la cinta **Vista**, dentro del grupo **Vista previa de datos**, marque **Distribución de columna**.

1. Revise la columna **Position** nuevamente y observe que hay cuatro valores distintos y un valor único.

1. Revise la distribución de columnas para la columna **EmployeeKey**—hay 296 valores distintos y 296 valores únicos.

     ![Distribución de columna mostrando 296 distintos, 296 únicos](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image26.png)

    > ***Nota**: Cuando los recuentos distintos y únicos son iguales, significa que la columna contiene valores únicos. Al modelar, es importante que algunas tablas del modelo tengan columnas únicas. Estas columnas únicas se pueden usar para crear relaciones uno a muchos, lo que hará en el laboratorio **Modelar datos en Power BI Desktop**.*

1. En el panel **Consultas**, seleccione la consulta **DimProduct**.

    > *La tabla **DimProduct** contiene una fila por producto vendido por la empresa.*

1. En el panel **Consultas**, seleccione la consulta **DimReseller**.

    > *La tabla **DimReseller** contiene una fila por revendedor. Los revendedores venden, distribuyen o agregan valor a los productos de Adventure Works.*

1. Para ver los valores de las columnas, en la pestaña de la cinta **Vista**, dentro del grupo **Vista previa de datos**, marque **Perfil de columna**.

1. Seleccione el encabezado de la columna **BusinessType** y observe el nuevo panel debajo del panel de vista previa de datos. Revise las estadísticas de columna y la distribución de valores en el panel de vista previa de datos.

    > *Observe el problema de calidad de datos: hay dos etiquetas para almacén (**Warehouse** y **Ware House** mal escrito).*

     ![Distribución de valores para la columna BusinessType](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image31.png)

1. Pase el cursor sobre la barra **Ware House** y observe que hay cinco filas con este valor.

1. En el panel **Consultas**, seleccione la consulta **DimSalesTerritory**.

    > *La tabla **DimSalesTerritory** contiene una fila por región de ventas, incluyendo **Corporate HQ** (sede corporativa). Las regiones están asignadas a un país, y los países están asignados a grupos. En el laboratorio **Modelar datos en Power BI Desktop**, creará una jerarquía para soportar el análisis a nivel de región, país o grupo.*

1. En el panel **Consultas**, seleccione la consulta **FactResellerSales**.

    > *La tabla **FactResellerSales** contiene una fila por línea de orden de venta—una orden de venta contiene uno o más artículos de línea.*

1. Revise la calidad de columna para la columna **TotalProductCost** y observe que el 8% de las filas están vacías.

    > *Los valores faltantes en la columna **TotalProductCost** son un problema de calidad de datos.*

## **Obtener datos desde un archivo CSV**

En esta tarea, creará una nueva consulta basada en archivos CSV.

1. Para agregar una nueva consulta, en la ventana del **Editor de Power Query**, en la pestaña de la cinta **Inicio**, dentro del grupo **Nueva consulta**, seleccione la flecha hacia abajo de **Nueva fuente** y luego seleccione **Texto/CSV**.

1. Navegue hasta el archivo **01-prepare-data > ResellerSalesTargets.csv**. Seleccione **Abrir**.

1. En la ventana **ResellerSalesTargets.csv**, revise la vista previa de datos. Seleccione **Aceptar**.

1. En el panel **Consultas**, observe la adición de la consulta **ResellerSalesTargets**.

    > *El archivo CSV **ResellerSalesTargets** contiene una fila por vendedor, por año. Cada fila registra 12 objetivos de ventas mensuales (expresados en miles). El año fiscal para la empresa Adventure Works comienza el 1 de julio.*

1. Observe que ninguna columna contiene valores vacíos. Cuando no hay un objetivo de ventas mensual, se almacena un carácter de guión en su lugar.

1. Revise los iconos en cada encabezado de columna, a la izquierda del nombre de la columna. Los iconos representan el tipo de datos de la columna. **123** es número entero y **ABC** es texto.

     ![Tipo de datos de columna](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image38.png)

1. Repita los pasos para crear una consulta basada en el archivo **ColorFormats.csv**.

    > *El archivo CSV **ColorFormats** contiene una fila por color de producto. Cada fila registra los códigos HEX para formatear los colores de fondo y fuente.*

Ahora debería tener dos nuevas consultas, **ResellerSalesTargets** y **ColorFormats**.

 ![Lista de consultas](Linked_image_Files/01-all-queries-loaded.png)

## Laboratorio completado