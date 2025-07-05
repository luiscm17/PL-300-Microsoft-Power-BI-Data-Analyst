---
lab:
    title: 'Perform analytics in Power BI'
    module: 'Perform analytics in Power BI'
---

# Realizar análisis en Power BI

## Historia del laboratorio

En este laboratorio, crearás el informe **Sales Exploration**.

En este laboratorio, aprenderás a:

- Crear gráficos de dispersión animados.
- Usar un visual para pronosticar valores.

**Este laboratorio debería tomar aproximadamente 30 minutos.**

## Comenzar

Para completar este ejercicio, primero abre un navegador web e ingresa la siguiente URL para descargar la carpeta zip:

`https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst/raw/Main/Allfiles/Labs/10-perform-analytics-power-bi/10-perform-analytics.zip`

Extrae la carpeta en **C:\Users\Student\Downloads\10-perform-analytics**.

1. Abre el archivo **10-Starter-Sales Analysis.pbix**.

> _**Nota**: Puedes cancelar el inicio de sesión seleccionando **Cancelar**. Cierra cualquier otra ventana informativa. Selecciona **Apply Later** si se te solicita aplicar cambios._

## Crear un gráfico de dispersión animado

En esta tarea, crearás un gráfico de dispersión que puede ser animado.

1. Crea una nueva página y nómbrala **Scatter Chart**.

1. Agrega un visual **Scatter Chart** a la página del informe, y luego posiciónalo y redimensiónalo para que ocupe toda la página.

    > _El gráfico puede ser animado cuando se agrega un campo al área **Play Axis**._

    ![Imagen 18](Linked_image_Files/10-perform-analytics-power-bi_image15.png)

    ![Imagen 75](Linked_image_Files/10-perform-analytics-power-bi_image16.png)

1. Agrega los siguientes campos a las áreas del visual:

    > _Los laboratorios usan una notación abreviada para referenciar un campo. Se verá así: **Reseller** **|** **Business Type**. En este ejemplo, **Reseller** es el nombre de la tabla y **Business Type** es el nombre del campo._

    - X Axis: **Sales | Sales**
    - Y Axis: **Sales | Profit Margin**
    - Legend: **Reseller | Business Type**
    - Size: **Sales | Quantity**
    - Play Axis: **Date | Quarter**

1. En el panel **Filters**, agrega el campo **Product | Category** al área **Filters On This Page**.

1. En la tarjeta de filtro, filtra por **Bikes**.

1. Para animar el gráfico, en la esquina inferior izquierda, selecciona **Play**.

    ![Imagen 41](Linked_image_Files/10-perform-analytics-power-bi_image19.png)

1. Observa todo el ciclo de animación desde **FY2018 Q1** hasta **FY2020 Q4**.

    > _El gráfico de dispersión permite entender los valores de las medidas simultáneamente: en este caso, cantidad de pedidos, ingresos por ventas y margen de beneficio._
    > 
    > _Cada burbuja representa un tipo de negocio de revendedor. Los cambios en el tamaño de la burbuja reflejan aumentos o disminuciones en las cantidades de pedidos. Mientras que los movimientos horizontales representan aumentos/disminuciones en los ingresos por ventas, y los movimientos verticales representan aumentos/disminuciones en la rentabilidad._

1. Cuando la animación se detenga, selecciona una de las burbujas para revelar su seguimiento a lo largo del tiempo.

1. Pasa el cursor sobre cualquier burbuja para revelar un tooltip que describe los valores de las medidas para el tipo de revendedor en ese momento.

1. En el panel **Filters**, filtra solo por **Clothing** y observa que produce un resultado muy diferente.

1. Guarda el archivo de Power BI Desktop.

## Crear un pronóstico

En esta tarea, crearás un pronóstico para determinar posibles ingresos futuros por ventas.

1. Agrega una nueva página y luego renómbrala como **Forecast**.

1. Agrega un visual **Line Chart** a la página del informe, y luego posiciónalo y redimensiónalo para que ocupe toda la página.

    ![Imagen 19](Linked_image_Files/10-perform-analytics-power-bi_image21.png)

    ![Imagen 74](Linked_image_Files/10-perform-analytics-power-bi_image22.png)

1. Agrega los siguientes campos a las áreas del visual:

    - X-axis: **Date | Date**
    - Y-axis: **Sales | Sales**

1. En el panel **Filters**, agrega el campo **Date | Year** al área **Filters On This Page**.

1. En la tarjeta de filtro, filtra por dos años: **FY2019** y **FY2020**.

    > _Al pronosticar en una línea de tiempo, necesitarás al menos dos ciclos (años) de datos para producir un pronóstico preciso y estable._

1. Agrega también el campo **Product | Category** al área **Filters On This Page**, y filtra por **Bikes**.

1. Para agregar un pronóstico, debajo del panel **Visualizations**, selecciona el panel **Analytics**.

    ![Imagen 20](Linked_image_Files/10-perform-analytics-power-bi_image26.png)

1. Expande la sección **Forecast**.

    > _Si la sección **Forecast** no está disponible, probablemente se deba a que el visual no se ha configurado correctamente. El pronóstico solo está disponible cuando se cumplen dos condiciones: el eje tiene un solo campo de tipo fecha, y solo hay un campo de valor._

1. Activa la opción **Forecast** a **On**.

1. Configura las siguientes propiedades del pronóstico, luego selecciona **Apply**:

    - Units: **Months**
    - Forecast length: **1 month**
    - Seasonality: **365**
    - Confidence interval: **80%**

    ![Imagen 52](Linked_image_Files/10-perform-analytics-power-bi_image29.png)

1. En el visual de línea, observa que el pronóstico se ha extendido un mes más allá de los datos históricos.

    > _El área gris representa la confianza. Cuanto más amplia sea la confianza, menos estable—y por lo tanto menos preciso—es probable que sea el pronóstico._
    >
    > _Cuando conoces la longitud del ciclo, en este caso anual, debes ingresar los puntos de estacionalidad. A veces podría ser semanal (7) o mensual (30)._

1. En el panel **Filters**, filtra solo por **Clothing** y observa que produce un resultado diferente.

## Laboratorio completado
