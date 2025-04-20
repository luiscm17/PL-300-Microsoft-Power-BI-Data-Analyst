---
lab:
    title: 'Configurar su propio entorno'
    module: 'Configurar su propio entorno'
---

# Configuración del entorno local de laboratorio

Idealmente, debería completar estos laboratorios en un entorno de laboratorio alojado. Si desea completarlos en su propia computadora, puede hacerlo instalando el siguiente software.

- Todos los archivos de configuración y recursos se pueden [descargar desde GitHub](https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst/raw/Main/AllfilesDownload.zip).
  - Extraiga la carpeta 'AllFiles' en D:/ y renómbrela a 'D:\Allfiles\'.

***Puede experimentar diálogos y comportamientos inesperados al usar su propio entorno. Debido a la amplia gama de posibles configuraciones locales, el equipo del curso no puede dar soporte a los problemas que pueda encontrar en su propio entorno.***

## Instrucciones para Windows 11

> &#128221; Las instrucciones siguientes son para una computadora con Windows 11. La conexión desde un sistema operativo diferente puede no resultar en la misma experiencia.

### Power BI Desktop

1. Descargue e instale desde la Microsoft Store. Si no tiene acceso a la Microsoft Store, descargue desde la [web](https://www.microsoft.com/download/details.aspx?id=58494). Power BI Desktop es la aplicación principal para estos laboratorios.

    - Use las opciones predeterminadas en el instalador.

### Cuenta de Desarrollador M365

Para algunos de los ejercicios, necesitará iniciar sesión en Power BI con una cuenta organizacional. Puede usar la suya propia, pero si no tiene acceso, puede crear una [cuenta de desarrollador M365](https://developer.microsoft.com/en-us/microsoft-365/dev-program) gratuita.

### Motor de Base de Datos SQL Server

1. El laboratorio se conecta a una instancia local de SQL Server. Las siguientes instrucciones le ayudarán a instalar SQL Server y configurar las opciones predeterminadas. Solo necesita instalar la característica Motor de Base de Datos.

    - Descargue la [copia gratuita del medio de instalación para Desarrolladores](https://www.microsoft.com/sql-server/sql-server-downloads?SilentAuth=1&f=255&MSPPError=-2147217396&rtc=1)
    - [Instale SQL Server desde el Asistente de Instalación (Setup)](https://learn.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup)

> &#128221; Puede usar una instancia existente de SQL Server si tiene acceso, en lugar de instalar una versión local. Sin embargo, necesitará modificar la cadena de conexión de "localhost" al nombre de su instancia.

### Microsoft Edge

1. Instale la última versión de [Microsoft Edge](https://microsoft.com/edge) para acceder al servicio Power BI en línea.