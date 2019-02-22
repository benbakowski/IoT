---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# Gestión de acceso de usuario
{: #managing-user-access}

<p>Esta recopilación de documentación de {{site.data.keyword.Bluemix}} pertenece al plan de precios Lite de {{site.data.keyword.iot_full}} e incluye información básica de iniciación, referencias de API e información general de resolución de problemas. 
Para obtener la documentación completa de {{site.data.keyword.iot_short_notm}}, consulte la [documentación de producto de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) en IBM Knowledge Center. Encontrará más información acerca de los distintos planes en [planes de servicios de {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Desde la página Miembros del panel de control, puede controlar y gestionar el acceso a la organización de {{site.data.keyword.iot_full}}. Puede añadir usuarios añadiéndolos, invitándolos o importándolos. También puede dar distintos niveles de acceso a los usuarios asignando roles.
{:shortdesc}

## Adición de usuarios
{: #adding-new-users}

En la página **Miembros** del panel de control, puede añadir miembros mediante la función Añadir. También puede añadir miembros simultáneamente mediante la función Importar.

De forma predeterminada, las cuentas de los miembros no caducan. Al añadir usuarios a la organización de {{site.data.keyword.iot_short_notm}}, puede, si lo desea, establecer una fecha de caducidad para su cuenta.

### Adición de miembros a la organización de {{site.data.keyword.iot_short_notm}}

Para añadir un miembro a su organización, necesitará el IBMid del miembro. Para añadir un miembro, no necesita que este se lo confirme.

Para añadir un solo miembro a la organización de {{site.data.keyword.iot_short_notm}}:
1. En el panel de control de {{site.data.keyword.iot_short_notm}}, pulse **Miembros** en la barra de navegación.
2. Pulse **Añadir miembros** y seleccione el separador **Añadir**.
3. Especifique el IBMid del miembro.
4. Seleccione un rol para el miembro.
5. Opcional: establezca una fecha de caducidad.
6. Pulse **Añadir**.

Para añadir varios miembros simultáneamente, debe cargar un archivo `.csv` que contiene el IBMid, el rol y la fecha de caducidad opcional para cada miembro. Para obtener información, consulte [Construir el archivo CSV](#constructing-your-csv).
1. En el panel de control de {{site.data.keyword.iot_short_notm}}, pulse **Miembros** en la barra de navegación.
2. Pulse **Añadir miembros** y seleccione el separador **Importar**.
3. Examine los archivos o arrastre el archivo `.csv` a la ventana **Cargar CSV**.
4. Seleccione un rol predeterminado para utilizar si no se reconoce un rol especificado en el archivo CSV.
5. Correlacione los números de columna del archivo CSV con las entradas correspondientes de IBMid, rol y fecha de caducidad opcional.
6. Seleccione el separador de columna de coma o punto y coma adecuado para que coincida con el separador utilizado en el archivo `.csv`.
7. Pulse **Importar** para importar los IBMid y crear los miembros.


### Construir el archivo CSV
{: #constructing-your-csv}

Cuando se construye un archivo CSV para importar miembros a su organización, asegúrese de incluir la información necesaria para el método que está utilizando. Utilice comas o puntos y comas para separar las columnas.  
**Importante:** al cargar el archivo CSV, en **Valores CSV**, asegúrese de que selecciona el separador de columna correcto.

Archivo CSV de ejemplo con delimitación por comas:  
```
user1@sample.com,PD_DEVELOPER_USER,2018-03-13
user2@sample.com,PD_OPERATOR_USER,2018-03-13
user3@sample.com,PD_ADMIN_USER,2018-03-13
```
Donde se utilizan las siguientes entradas de columna:  
- Columna 1: la dirección de correo electrónico del usuario.  
Si está añadiendo miembros, asegúrese de utilizar la dirección de correo electrónico correspondiente a un IBMid válido. Si está invitando a miembros, puede utilizar cualquier dirección de correo electrónico válida.
- Columna 2: el rol que se asignará al usuario.  
Especifique uno de los roles siguientes:
 - PD_ADMIN_USER
 - PD_OPERATOR_USER
 - PD_DEVELOPER_USER
 - PD_ANALYST_USER
 - PD_READER_USER  
 Para obtener más información sobre los roles de usuario, consulte [Roles de usuario, aplicación y pasarela ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/roles_index.html#user_roles){: new_window}.
- Columna 3: la fecha ISO 6801 (por ejemplo, `2018-03-13`) correspondiente a la fecha de caducidad del usuario.

## Edición de usuarios
{: #editing-users}

Los usuarios se pueden editar para modificar su rol, añadir, eliminar o cambiar una fecha de caducidad de acceso o añadir o eliminar el acceso a la organización.

1. En el panel de control de {{site.data.keyword.iot_short_notm}}, pulse **Miembros** en la barra de navegación.
2. Pulse el icono **Editar**, situado junto al usuario que desea editar.
3. Realice los cambios que desee en el usuario.
4. Pulse **Guardar**.

## Bloqueo del de acceso de usuarios
{: #blocking-users}

Se puede bloquear el acceso de los usuarios a la organización {{site.data.keyword.iot_short_notm}} mientras siguen manteniendo la pertenencia a la organización.

1. En el panel de control de {{site.data.keyword.iot_short_notm}}, pulse **Miembros** en la barra de navegación.
2. Pulse el conmutar situado junto al usuario cuyo acceso a la organización {{site.data.keyword.iot_short_notm}} desea bloquear.

## Limitación del acceso de usuarios
{: #limiting-users}

El control de acceso a nivel de recurso le permite limitar el acceso a dispositivos en una organización. Puede utilizar grupos de recursos para especificar los dispositivos que puede gestionar cada usuario o clave de API. Para obtener información acerca de cómo configurar el control de acceso a nivel de recurso, consulte [Configuración del control de acceso a nivel de recurso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/rlac.html#configure_RLAC){: new_window}.

## Eliminación de usuarios
{: #removing-users}

Los usuarios se pueden eliminar por completo de la organización {{site.data.keyword.iot_short_notm}}. La eliminación de usuarios no se puede deshacer y los usuarios se deben [añadir a la plataforma](#adding-new-users) para restaurar el acceso.

1. En el panel de control de {{site.data.keyword.iot_short_notm}}, pulse **Miembros** en la barra de navegación.
2. Pulse el icono **Suprimir**, situado junto al usuario que se va a eliminar.
3. Pulse **Suprimir** en el recuadro de diálogo de confirmación.
