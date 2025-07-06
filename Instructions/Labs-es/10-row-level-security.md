---
lab:
    title: 'Enforce Row-Level Security'
    module: 'Enforce Row-Level Security'
---

# Aplicar Seguridad a Nivel de Fila (Row-Level Security)

## Historia del laboratorio

En este laboratorio, aplicarás seguridad a nivel de fila para garantizar que un vendedor solo pueda analizar datos de ventas de su(s) región(es) asignada(s).

En este laboratorio aprenderás a:

- Implementar seguridad a nivel de fila
- Elegir entre métodos dinámicos y estáticos

**Este laboratorio debería tomar aproximadamente 20 minutos.**

## Comenzar

Para completar este ejercicio, primero abre un navegador web e ingresa la siguiente URL para descargar la carpeta zip:

`https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst/raw/Main/Allfiles/Labs/10-row-level-security/10-row-level-security.zip`

Extrae la carpeta en la ubicación: **C:\Users\Student\Downloads\10-row-level-security**.

Abre el archivo **10-Starter-Sales Analysis.pbix**.

> ***Nota**: Puedes descartar el inicio de sesión seleccionando **Cancel**. Cierra cualquier otra ventana informativa. Selecciona **Apply Later**, si se te solicita aplicar cambios.*

## Aplicar seguridad a nivel de fila

En esta tarea, implementarás seguridad a nivel de fila para garantizar que un vendedor solo vea ventas realizadas en su(s) región(es) asignada(s).

1. Cambia a la vista de Tabla.

   ![Picture 5701](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image20.png)

1. En el panel **Data**, selecciona la tabla **Salesperson (Performance)**.

1. Revisa los datos, observando que Michael Blythe (EmployeeKey 281) tiene un valor UPN de: **`michael-blythe@adventureworks.com`**
    
	> *Recordarás que Michael Blythe está asignado a tres regiones de ventas: US Northeast, US Central y US Southeast.*

1. En la pestaña **Home**, dentro del grupo **Security**, selecciona **Manage Roles**.

    ![Picture 5700](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image21.png)

1. En la ventana **Manage security roles**, en la sección **Roles**, selecciona **New**.

1. En el cuadro, reemplaza el texto seleccionado con el nombre del rol: **Salespeople**, y luego presiona **Enter**.

   ![Picture 5703](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image23.png)

1. Para asignar un filtro, selecciona la tabla **Salesperson (Performance)**, y luego selecciona **Switch to DAX editor** en la sección **Filter data**.

   ![Screenshot 2024-04-18 144345](https://github.com/afelix-95/PL-300-Microsoft-Power-BI-Data-Analyst/assets/148110824/1308d47f-2cca-4f88-9237-b02b66b4cf1e)

1. En el cuadro del editor DAX, ingresa la siguiente expresión:

    ```DAX
    [UPN] = USERPRINCIPALNAME()
    ```

   ![Picture 11](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image25.png)

    > *USERPRINCIPALNAME() es una función de Data Analysis Expressions (DAX) que devuelve el nombre del usuario autenticado. Significa que la tabla **Salesperson (Performance)** se filtrará por el User Principal Name (UPN) del usuario que consulta el modelo.*

1. Selecciona **Save** y **Close**.

1. Para probar el rol de seguridad, en la pestaña **Home**, dentro del grupo **Security**, selecciona **View As**.

   ![Picture 5708](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image27.png)

1. En la ventana **View as Roles**, marca el ítem **Other User**, y luego en el cuadro correspondiente, ingresa: **`michael-blythe@adventureworks.com`**

1. Marca el rol **Salespeople**, y luego **OK**.
    
	> *Esta configuración resulta en usar el rol **Salespeople** e impersonar al usuario con el nombre de Michael Blythe.*

   ![Picture 5709](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image28.png)

1. Observa el banner amarillo sobre la página del reporte, que describe el contexto de seguridad de prueba.

   ![Picture 13](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image30.png)

1. En el visual de tabla, observa que solo se lista el vendedor **Michael Blythe**.

   ![Picture 5713](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image31.png)

1. Para detener la prueba, en el lado derecho del banner amarillo, selecciona **Stop Viewing**.

   ![Picture 5712](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image32.png)

1. Para eliminar el rol **Salespeople**, en la pestaña **Home**, dentro del grupo **Security**, selecciona **Manage Roles**.

   ![Picture 16](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image33.png)

1. En la ventana **Manage security roles**, selecciona los puntos suspensivos (...) en el rol **Salespeople**, y selecciona **Delete**. Cuando se te solicite confirmar la eliminación, selecciona **Yes, Delete**.

   ![Screenshot 2024-04-18 145556](https://github.com/afelix-95/PL-300-Microsoft-Power-BI-Data-Analyst/assets/148110824/deeb4eac-b639-433d-a9d4-29c8e127008e)

*Nota: Cuando el archivo de Power BI Desktop se publique en el servicio Power BI, deberás completar una tarea posterior a la publicación para mapear entidades de seguridad al rol **Salespeople**. No harás eso en este laboratorio.*

## Laboratorio completado
