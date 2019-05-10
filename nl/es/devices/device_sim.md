---

copyright:
  years: 2017, 2019
lastupdated: "2019-04-05"

keywords: device simulator, devices

subcollection: iot-platform

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# Simulación de datos de dispositivo
{: #sim_device_data}

<p>Esta recopilación de documentación de {{site.data.keyword.cloud}} pertenece al plan de precios Lite de {{site.data.keyword.iot_full}} e incluye información básica de iniciación, referencias de API e información general de resolución de problemas. 
Para obtener la documentación completa de {{site.data.keyword.iot_short_notm}}, consulte la [documentación de producto de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) en IBM Knowledge Center. Encontrará más información acerca de los distintos planes en [Planes del servicio {{site.data.keyword.iot_short_notm}}](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Utilice el simulador de dispositivos {{site.data.keyword.iot_full}} para configurar eventos simulados para dispositivos para conocer, probar y mostrar las características totalmente funcionales de {{site.data.keyword.iot_short_notm}} sin tener que registrar y conectar dispositivos reales.
{: shortdesc}

Utilizando el simulador de dispositivos, puede crear
dispositivos simulados para tipos de dispositivos existentes o crear
nuevos tipos de dispositivos y dispositivos. Cada dispositivo
simulado puede utilizar detalles de suceso exclusivos, pero también
puede crear una configuración predeterminada que se aplique a todos
los dispositivos.

## Antes de empezar
{: #byb-simulation .sectiontitle}
Habilite la simulación de dispositivos para el ID de usuario.
1. Inicie una sesión en {{site.data.keyword.iot_short_notm}}.
2. En el panel de navegación principal, seleccione **Valores**.
3. En la sección **Datos y dispositivos** active el simulador de dispositivo.

Si la simulación de dispositivo está habilitada para el ID de
usuario, todos los dispositivos simulados habilitados se inician
automáticamente cuando inicia sesión en el panel de control de
{{site.data.keyword.iot_short_notm}}.

## Simulación de dispositivos
{: #process-simulation .sectiontitle}
Cuando está activado, el simulador de dispositivos está disponible
en todas las páginas del panel de control. Un mensaje en la esquina
inferior derecha de la pantalla indica el número de simulaciones que
se están ejecutando.

**Importante:** Los dispositivos simulados
y los tipos de dispositivos que define para el ID de usuario están
disponibles para otros usuarios de la organización de {{site.data.keyword.iot_short_notm}}. Sin
embargo, para generar datos simulados para los dispositivos, debe
haber iniciado sesión en el panel de control de
{{site.data.keyword.iot_short_notm}} en una sesión de usuario
activo.

Para simular datos de dispositivo:
1. En el panel de control de
{{site.data.keyword.iot_short_notm}}, pulse el mensaje "Se están ejecutando 0 simulaciones".
3. En la ventana de configuración
**Simulaciones** que se abre, pulse **Crear simulación**.
4. Configure los detalles de la simulación.  
Pulse **Importar/exportar simulación** para
importar una [configuración existente](#reuse) o
configurar manualmente los detalles:
   1. Seleccione un tipo de dispositivo existente para el que desee simular datos o cree un nuevo tipo de dispositivo escribiendo el nombre de tipo de dispositivo.
   2. Modifique el nombre predeterminado para el tipo de
suceso.
   3. En **Planificación**, establezca la frecuencia del suceso.
   4. Edite la carga útil de suceso.  
   Edite la carga útil JSON de muestra añadiendo propiedades y sus
correspondientes valores o utilice las
[funciones](#functions) para añadir
dinámicamente puntos de datos
generados.  
   También puede cargar un [archivo de carga útil de
suceso CSV](#csv) para configurar la carga útil.
   {: tip}
5. Pulse **Nuevo tipo de suceso**
para añadir y configurar más tipos de suceso para el tipo de
dispositivo.
5. Habilite la opción **Guardar sucesos como datos históricos** para que los datos de estado del dispositivo simulado estén disponibles y se pueda acceder a los mismos más tarde.  
Con los datos históricos habilitados, se crean los componentes de {{site.data.keyword.iot_short_notm}} [gestión de datos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/GA_information_management/ga_im_definitions.html){: new_window} y se puede acceder al estado del dispositivo simulado desde la interfaz lógica asociada.  
**Importante:** Después de habilitar el tipo de dispositivo para guardar los datos históricos, no puede añadir o eliminar tipos de suceso, ni puede modificar los campos presentes en las cargas útiles del suceso.
5. Pulse **Guardar** para crear el tipo de dispositivo.  
Ahora ya está preparado para crear uno o más dispositivos simulados.
6. Pulse **Crear dispositivo simulado** para crear un dispositivo y empezar a enviar datos.  
**Sugerencia:** Para crear más de un dispositivo, pulse **1 x** y seleccione el número de dispositivos que se van a crear.  
7. Para crear más simulaciones, pulse **Nueva simulación** y repita los pasos de configuración para cada dispositivo en el que desee aplicar los valores personalizados.   
El mensaje de la esquina inferior derecha de la pantalla muestra el número de simulaciones activas.
8. En la página **Dispositivos**, navegue hasta uno de los dispositivos simulados y seleccione el separador **Sucesos recientes** para verificar que los sucesos simulados están funcionando.

Puede [exportar las configuraciones de suceso simuladas](#reuse) para volverlas a utilizar o compartirlas.

## Funciones de tipo de suceso
{: #functions .sectiontitle}

Puede utilizar varias funciones especiales para crear datos dinámicos para los tipos de suceso.

Función | Uso | Ejemplo  
:--- | :---  | :--  
`random(lower, upper)`  | Genera un número aleatorio en el rango especificado.  | `{"random": random(0, 100)}`  
`$counter` | Muestra el número de dispositivos simulados del tipo actual. | `{"total": $counter}`  
`increment(start, increment)` | Especifica el valor inicial y el incremento por el que se incrementa. |`{"myNumber": increment(10, 1)}` </br> En este ejemplo, `myNumber` empieza en 10 y aumenta 1 cada vez que se envía una carga útil.


## Archivo de carga útil de suceso CSV
{: #csv .sectiontitle}

Si desea crear datos de sucesos controlados para determinados escenarios, puede configurar el flujo de datos en un archivo de entrada CSV.

### Requisitos
El archivo CSV debe cumplir los requisitos siguientes:
- Cada valor es un [primitivo JSON ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://json.org){: new_window} válido, excepto si se indica lo contrario:
  - serie:   
  Ejemplo: "Hello world"
  - número:  
  Ejemplo: 0, 0.1, -22, -2.43
  - booleano:  
  true o false
  - null:  
  null
  - **No recibe soporte:**
    - objetos  
    Ejemplo: {}
    - matrices  
    Ejemplo: []
- Los valores deben estar delimitados por comas.
- Las filas se deben delimitar mediante el carácter de nueva línea (`\n`).
- La fila de cabecera debe constar solo de valores de serie.


### Archivo CSV de ejemplo
```
"temperature", "confidence","status"
1, 0.1, "normal"
2, 0.2, "normal"
3, 0.3, "error"
4, 0.4, "normal"
```

La primera línea o "fila de cabecera" determina las propiedades que se incluyen en el JSON de dispositivo en todos los objetos de suceso JSON del dispositivo generado.
Cada línea posterior o "fila de datos" establece el valor de esas propiedades en cada objeto de suceso JSON del dispositivo generado.

**Sugerencia:** Cuando importa el archivo CSV, puede seleccionar **Bucle de datos simulados del archivo** para desplazarse por las líneas de datos en secuencia para lograr un canal de información continuo. Si no se establece este conmutador, cada fila de datos del archivo CSV se envía una vez a la frecuencia establecida por la planificación.

El archivo CSV de ejemplo da como resultado cargas útiles de suceso del tipo siguiente:
```JSON
{
  "temperature": 1,
  "confidence": 0.1,
  "status": "normal"
}
```

## Uso compartido y reutilización de simulaciones
{: #reuse .sectiontitle}

Puede exportar los detalles de la simulación para reutilizarlos o compartirlos:
1. En la ventana **Simulaciones**, pulse **Importar/exportar**.
2. Seleccione el separador **Exportar**.
3. Copie los detalles de la simulación en el portapapeles o descárguelos en un archivo JSON.
