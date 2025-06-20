# Liberty: Primeros pasos

## Recopilación de datos, evaluaciones y aceleradores de implementación

![bandera](./images/media/OpenLiberty.png)

**Última actualización:** marzo de 2024

**Duración:** 90 minutos

¿Necesitas ayuda? Contacta con **Lars Besselmann y Kevin Postreich.**

## Tareas de introducción a Liberty

WebSphere Liberty ( **Liberty** ) es un framework ligero y abierto para crear microservicios Java nativos de la nube de forma rápida y eficiente. Cree aplicaciones y microservicios nativos de la nube ejecutando solo lo que necesita. Es el entorno de ejecución de servidor más flexible disponible para desarrolladores Java en este sistema solar.

Liberty se basa en el código fuente de Open Liberty. Open Liberty está diseñado pensando tanto en desarrolladores como en propietarios de aplicaciones.

- Proporciona las últimas API de Java y se integra con las herramientas de desarrollo y compilación más populares.
- Incorpora innovación como la migración cero para reducir los costos de ejecución de las aplicaciones y el esfuerzo de entrega.
- Liberty es una consecuencia de Open Liberty, por lo que todo lo que funciona en Open Liberty funciona en Liberty.
- El mismo ciclo de lanzamiento de entrega continua mensual que Liberty
- No es necesario cambiar a Liberty para obtener soporte comercial

**Liberty Tools** es un conjunto de herramientas intuitivas para desarrolladores para los entornos de desarrollo Eclipse IDE, Visual Studio Code e IntelliJ IDEA. Estas herramientas adoptan un enfoque centrado en Maven/Gradle y permiten el desarrollo rápido e iterativo de aplicaciones Java nativas de la nube mediante el modo de desarrollo de Liberty. Liberty Tools también ofrece funciones útiles que ahorran tiempo, como la finalización de código, descripciones al pasar el cursor sobre el objeto y diagnósticos de configuración para las API de Jakarta EE, las API de MicroProfile y la configuración de Liberty. Para más información, consulte la descripción general de Liberty Tools.

## 1. Introducción

En el laboratorio, habrá diferentes roles involucrados en la realización de distintas tareas con diferentes herramientas. Desempeñarás todos los roles durante el laboratorio.

- Comenzarás como desarrollador de aplicaciones y usarás Liberty Starter y el asistente de código de Liberty Tools para desarrollar una aplicación web sencilla. Pero no te preocupes, no necesitas ser desarrollador para hacerlo.
- Como operador de configuración de Liberty, utilizará el asistente de configuración de Liberty Tools y conceptos como inclusiones y variables para crear una configuración portátil.
- Como administrador de Liberty, instalará Liberty desde una imagen de kernel, agregará funciones faltantes, configurará el registro, la seguridad, etc., utilizará las API REST de Liberty para revisar la configuración y utilizará el Centro de administración de Liberty para la supervisión.

## 2. Objetivo

Estos son los objetivos en el laboratorio:

- Como desarrollador de aplicaciones:

    - Tareas:
        - Desarrolla la aplicación.
        - Crea una configuración básica de Liberty para la aplicación.
    - Herramientas:
        - Apache Maven
            - para construir el proyecto
            - para descargar el entorno de ejecución del servidor Open Liberty desde el repositorio maven
        - Complemento Maven de Liberty para el desarrollo de bucle interno a través del modo Liberty Dev
            - Para construir la aplicación de guerra e implementarla en Liberty
        - Código de Visual Studio
            - como IDE para construir el código de la aplicación
        - Complemento Liberty Tools para Visual Studio Code
            - Proporciona un panel de Liberty con integración del modo de desarrollo en el IDE
            - Proporciona asistencia con el código Jakarta EE y MicroProfile
            - Proporciona asistencia para la configuración de Liberty
        - Proyecto Liberty Starter
            - Para generar un proyecto maven para Liberty
        - Libertad abierta / Libertad de WebSphere
            - como entorno de ejecución para la aplicación Java que se desarrollará
            - para crear un paquete de servidor

- Como operador de configuración de Liberty:

    - Tareas:
        - Extraiga el paquete Liberty desde la línea de comandos e implemente las actualizaciones dinámicas de Liberty
        - Desarrolle fragmentos de configuración portátiles de Liberty utilizando inclusiones, variables y mucho más.
    - Herramientas:
        - Visual Studio Code con el complemento Liberty Tools como editor con asistencia de configuración

- Como administrador de Liberty:

    - Tareas:
        - Instala Liberty
        - Configura Liberty para la aplicación de destino utilizando fragmentos de configuración de Liberty
        - Aplica seguridad para reforzar la configuración de Liberty
        - Configurar el registro mediante configDropins
        - Revisar la configuración usando las API REST de Liberty
        - Monitorea Liberty usando el Centro de administración
    - Herramientas:
        - Comando del servidor Liberty para crear una instancia de Liberty e iniciarla, detenerla o volcarla
        - Utilidad de instalación de Liberty para instalar funciones faltantes
        - Liberty securityUtilidad para crear un almacén de claves o codificar una contraseña
        - API REST de Liberty y Centro de administración

## 3. Requisitos previos

Los siguientes requisitos previos deben completarse antes de comenzar este laboratorio:

- Familiaridad con los comandos básicos de Linux
- Tener acceso a Internet
- Tenga listo un entorno de laboratorio

## 4. Acceso al entorno

Si realiza este laboratorio como parte de un taller impartido por un instructor (virtual o presencial), ya se le ha proporcionado un entorno. El instructor le proporcionará los detalles para acceder al laboratorio.

De lo contrario, deberá reservar un entorno para el laboratorio. Puede obtenerlo aquí. Siga las instrucciones en pantalla para la opción " **Reservar ahora** ".

[https://TBD-al-enlace-de-reserva](https://TBD-to-the-reservation-link)

El entorno de laboratorio contiene una (1) máquina virtual Linux, denominada Workstation.

<kbd><img src="./images/media/workstation.png" alt=""></kbd>

<br>

1. Acceda al entorno de laboratorio desde su navegador web.

    Se configura un `Published Service` para proporcionar acceso a la máquina virtual **`Workstation`** a través de la interfaz noVNC para el entorno de laboratorio.

    a. Cuando se aprovisione el entorno de demostración, haga clic en el **`environment tile`** para abrir su vista de detalles.

    b. Haga clic en el enlace **`Published Service`** que mostrará una **lista del directorio.**

    c. Haga clic en el enlace **`vnc.html`** para abrir el entorno de laboratorio a través de la interfaz **noVNC** .

    <kbd><img src="./images/media/vnc-link.png" alt=""></kbd>

    d. Haga clic en el botón **`Connect`**

    <kbd><img src="./images/media/vnc-connect.png" alt=""></kbd>

    e. Ingrese la contraseña: **IBMDem0s!.** Luego, haga clic en el botón **`Send Credentials`** para acceder al entorno de laboratorio.

    <kbd><img src="./images/media/vnc-password.png" alt=""></kbd>

     <br>
    

2. Si se le solicita iniciar sesión en la máquina virtual de la "estación de trabajo", utilice las credenciales a continuación:

    Las credenciales de inicio de sesión para la **estación de trabajo "** VM" son:

    - ID de usuario: **techzone**

    - Contraseña: **IBMDem0s!**

    > Nota: Ese es un cero numérico en la contraseña.

     <br>


    <kbd><img src="./images/media/techzone-user-pw.png" alt="pantalla de vm del estudiante"></kbd>

     <br>
    

## 5. Consejos para trabajar en el entorno de laboratorio

1. Puede cambiar el tamaño del área visible utilizando las opciones **de configuración de noVNC** para cambiar el tamaño del escritorio virtual para que se ajuste a su pantalla.

    a. Desde la máquina virtual del entorno, haga clic en el **icono de giro** en el panel de control noNC para abrir el menú.

    <kbd><img src="./images/media/vnc-twisty.png" alt="ajustar a la ventana"></kbd>

    b. Para aumentar el área visible, haga clic en `Settings > Scaling Mode` y configure el valor en `Remote Resizing`

    <kbd><img src="./images/media/vnc-remote-resize.png" alt="ajustar a la ventana"></kbd>

2. Puede copiar/pegar texto de la guía de laboratorio en el entorno de laboratorio utilizando el portapapeles en el visor noVNC.

    a. Copie el texto de la guía de laboratorio que desea pegar en el entorno de laboratorio.

    b. Haga clic en el icono **`Clipboard`** y **`paste`** el texto en el portapapeles de noVNC.

    <kbd><img src="./images/media/vnc-paste.png" alt="ajustar a la ventana"></kbd>

    c. Pegue el texto en la máquina virtual, como en una ventana de terminal, una ventana del navegador, etc.

    d. Haga clic en el icono **`clipboard`** nuevamente para cerrarlo.

3. Como alternativa a la opción "Copiar y pegar" de noVNC, puede considerar abrir la guía de laboratorio en un navegador web dentro de la máquina virtual. Con este método, puede copiar y pegar fácilmente texto de la guía de laboratorio sin tener que usar el portapapeles de noVNC.

4. Para cambiar entre diferentes ventanas u obtener acceso a la barra de herramientas, haga clic en el ícono **`Activities`** dentro de la VM.

    <kbd><img src="./images/media/Activities.png" alt="ajustar a la ventana"></kbd>

    Luego, seleccione la aplicación que desea abrir en la barra de herramientas. En el laboratorio, usará Firefox y la terminal.

    <kbd><img src="./images/media/Toolbar.png" alt="Barra de herramientas"></kbd>

5. Cómo cambiar el color de fondo. En el entorno, el fondo predeterminado para las ventanas de terminal y Visual Studio Code es oscuro. Para la documentación del laboratorio, cambiamos el color a claro. Puedes mantener el fondo claro, pero si quieres cambiarlo a oscuro, aquí tienes la explicación de cómo hacerlo.

    1. Cómo cambiar el fondo de la terminal a blanco Haga clic derecho en el fondo de la terminal, luego seleccione Preferencias.

        <kbd><img src="./images/media/Terminal-change-background1.png" alt="Cambio de terminal de fondo1"></kbd>

        Se abrirá una ventana de Preferencias. Haz clic en Colores y desmarca la casilla "Usar colores del tema del sistema". (Si quieres volver al modo oscuro, vuelve a marcar la casilla).

        <kbd><img src="./images/media/Terminal-change-background2.png" alt="Terminal-cambiar-fondo2"></kbd>

        El fondo de la terminal debería cambiar a blanco.

        <kbd><img src="./images/media/Terminal-change-background3.png" alt="Terminal-cambiar-fondo3"></kbd>

        Cerrar la ventana de Preferencias.

    2. Cómo cambiar el fondo de Visual Studio Code de oscuro a claro

        En una ventana de terminal, ejecute el siguiente comando para iniciar Visual Studio Code

        ```
         mkdir ~/temp
         code ~/temp
        ```

        <kbd><img src="./images/media/start-VSCode.png" alt="inicio-VSCode"></kbd>

        Visual Studio Code se abre con un fondo oscuro. Haga clic en "Sí, confío en los autores".

        <kbd><img src="./images/media/VSCode-trust.png" alt="Confianza en VSCode"></kbd>

        Luego seleccione Preferencias &gt; Tema &gt; Tema de color

        <kbd><img src="./images/media/VSCode-Theme.png" alt="Tema de VSCode"></kbd>

        Seleccionar luz

        <kbd><img src="./images/media/VSCode-Theme-light.png" alt="Tema claro de VSCode"></kbd>

        La herramienta cambiará a un fondo claro, vea a continuación.

        <kbd><img src="./images/media/VSCode-light.png" alt="VSCode-light"></kbd>

        Cierre Visual Studio Code.


<br>


## 6. Ejecutar tareas de laboratorio

### 6.1 Verificar el software instalado

1. Abra una terminal haciendo clic en Actividades y seleccionando terminal.

    <kbd><img src="./images/media/Toolbar_terminal.png" alt="Terminal de la barra de herramientas"></kbd>

    Se abre la ventana del terminal.

    <kbd><img src="./images/media/Terminal.png" alt="Terminal"></kbd>

2. Compruebe la versión de Maven mediante el siguiente comando:

    ```
     mvn -version
    ```

    <kbd><img src="./images/media/mvn-v.png" alt="mvn-v"></kbd>

3. Compruebe la versión de Docker mediante el siguiente comando:

    ```
     docker -v
    ```

    <kbd><img src="./images/media/docker-v.png" alt="docker-v"></kbd>

4. Compruebe la versión de Git mediante el siguiente comando:

    ```
     git -v
    ```

    <kbd><img src="./images/media/git-v.png" alt="git-v"></kbd>

### 6.2 Crear los directorios de trabajo necesarios

1. Cree los directorios de estudiantes y algunos subdirectorios utilizados en el laboratorio con los comandos:

    ```
     mkdir ~/Student
     mkdir ~/Student/dev
     mkdir ~/Student/ops
     mkdir ~/Student/assets
    ```

### 6.3 Desarrollar una aplicación web Liberty

El objetivo de esta sección es desarrollar una aplicación web sencilla para Liberty. Utilizarás una **aplicación de inicio de Liberty** para empezar desde cero y usarás Visual Studio Code y las herramientas de Liberty para compilarla.

### 6.3.1 Crear un proyecto de aplicación de inicio.

En este escenario, se desea crear una aplicación web Jakarta EE 10 llamada **simpleweb** y se usará Maven para compilarla. La forma más rápida de comenzar es usar una aplicación de inicio Open Liberty que genere un proyecto con la configuración de Maven y una configuración básica de Liberty.

<kbd><img src="./images/media/LibertyStarter.png" alt="LibertyStarter"></kbd>

El **programa de inicio de Open Liberty** te ofrece una forma sencilla y rápida de obtener los archivos necesarios para empezar a crear una aplicación en Open Liberty. No necesitas buscar qué añadir a tus archivos de compilación de Maven o Gradle. Se genera un archivo **RestApplication.java** sencillo para que puedas empezar a crear una aplicación basada en REST. Se proporciona un archivo de configuración **server.xml** con las características necesarias para las versiones de MicroProfile y Jakarta EE que seleccionaste previamente.

1. Abra una ventana del navegador haciendo clic en **Actividades** y luego seleccione el ícono del navegador **Firefox** .

    <kbd><img src="./images/media/Toolbar_firefox.png" alt="Barra de herramientas de Firefox"></kbd>

    Si aparece una ventana emergente que indica que se requiere autenticación, ingrese **IBMDem0s!.**

    <kbd><img src="./images/media/Authentication-required.png" alt="Se requiere autenticación"></kbd>

2. Ingresa la URL **https://openliberty.io/start/**

<table>
<tbody>
<tr class="odd">
<td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
<td>
<p>Si la página no se abre, cierre el navegador y ábralo nuevamente. </p>
</td>
</tr>
</tbody>
</table>

1. Cambie el nombre del artefacto a **simpleweb** , cambie el nivel de Java a **17** y la versión de MicroProfile a **6.1** , luego haga clic en **Generar proyecto.**

    <kbd><img src="./images/media/LibertyStarter-simpleweb.png" alt="LibertyStarter-simpleweb"></kbd>

2. Haga clic en **Guardar** para guardar el proyecto en Descargas.

    <kbd><img src="./images/media/LibertyStarter-simpleweb-save.png" alt="LibertyStarter-simpleweb-save"></kbd>

    Verás una ventana emergente como la de abajo. Haz clic en **«Entendido»** para cerrarla.

    <kbd><img src="./images/media/LibertyStarter-simpleweb-save2.png" alt="LibertyStarter-simpleweb-save2"></kbd>

3. Extraiga el archivo.

    a. Haga clic en **Actividades** y cambie a la ventana de terminal.

    b. Mueva el proyecto de inicio al directorio del desarrollador y extráigalo con los comandos:

    ```
     mv ~/Downloads/simpleweb.zip ~/Student/dev
     unzip ~/Student/dev/simpleweb.zip -d ~/Student/dev/simpleweb
    ```

    <kbd><img src="./images/media/image020.png" alt="imagen020"></kbd>

    El proyecto se ha creado en el directorio **~/Student/dev/simpleweb** .

    c. Enumere el contenido mediante el siguiente comando:

    ```
     ls -lrt ~/Student/dev/simpleweb
    ```

    <kbd><img src="./images/media/image021.png" alt="imagen021"></kbd>

### 6.3.2. Inspeccionar el proyecto de inicio con Open Visual Studio Code

Ahora utilizará Visual Studio Code para ver lo que se ha generado como parte del proyecto de inicio.

1. Desde la ventana de terminal, inicie Visual Studio Code

    ```
     cd ~/Student/dev/simpleweb/
     code .
    ```

    <kbd><img src="./images/media/image022.png" alt="imagen022"></kbd>

    Se abrirá la interfaz de usuario de Visual Studio Code.

2. Haga clic en **Sí, confío en los autores** para continuar.

    <kbd><img src="./images/media/image023.png" alt="imagen023"></kbd>

    Si durante el laboratorio ve una de las ventanas emergentes a continuación o cualquier otra ventana emergente que le pide instalar algo, cierre la ventana emergente sin instalación haciendo clic en la X. <kbd></kbd>![imagen024](./images/media/image024.png)<kbd><img src="./images/media/image025.png" alt="imagen025"></kbd>

3. Investigar el proyecto generado:

    En Visual Studio Code, consulta la sección **Explorador** para ver el contenido del proyecto. Encontrarás una carpeta de origen y una de destino, un Dockerfile y un archivo de compilación de Maven (pom.xml).

    <kbd><img src="./images/media/image026.png" alt="imagen026"></kbd>

4. Eche un vistazo a la configuración de Maven generada

    a. Haga clic en **pom.xml** para ver el pom maven.

    En la sección de compilación, puede encontrar la configuración del complemento liberty-maven-plugin. <kbd></kbd>![imagen027](./images/media/image027.png)

<table>
<tbody>
<tr class="odd">
<td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
<td>
<p>No te preocupes si la versión del complemento ha cambiado a 3.10.2 o posterior. </p>
</td>
</tr>
</tbody>
</table>

```
b. Finally close the pom.xml.
```

1. Revisar la configuración de Liberty generada

    a. Abra **src &gt; main &gt; liberty &gt; config &gt; server.xml** para ver la configuración de Liberty.

    <kbd><img src="./images/media/image028.png" alt="imagen028"></kbd>

    Como puede ver, se han configurado las funciones para **jakartaee-10** y **MicroProfile-6.1** .

    <kbd><img src="./images/media/image029.png" alt="imagen029"></kbd>

    b. Desplácese hacia abajo y podrá ver que el punto final http y la aplicación web se han configurado.

    <kbd><img src="./images/media/image030.png" alt="imagen030"></kbd>

### 6.3.3 Ajustar la configuración de Liberty

La aplicación **simpleweb** no requerirá el estándar **Jakarta EE 10** completo, sino solo la especificación del servlet.

Como práctica recomendada para optimizar el uso de memoria y espacio en disco durante la ejecución de la aplicación y limitar las posibles vulnerabilidades, se recomienda definir únicamente las funciones que requiere la aplicación. En este caso, se reemplazará la función **jakartaee-10** por una función de servlet adecuada.

1. En el editor de Visual Studio Code para **server.xml** , desplácese hacia arriba hasta la sección de características.

2. Elimine las líneas **&lt;feature&gt;jakartaee-10.0&lt;/feature&gt;** y **&lt;feature&gt;MicroProfile-6.1&lt;/feature&gt;** . La sección **featureManager** debería verse así:

    <kbd><img src="./images/media/image031.png" alt="imagen031"></kbd>

3. Ahora usará el **asistente de configuración de Liberty Tools** para definir la función del servlet. Coloque el cursor al principio de una línea vacía en la sección featureManager. A continuación, pulse la **tecla Ctrl** y la barra **espaciadora** para activar el asistente de configuración de Liberty Tools. Debería ver algo similar a esto:

    <kbd><img src="./images/media/image032.png" alt="imagen032"></kbd>

<table>
<tbody>
<tr class="odd">
<td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
<td>
<p>Es posible que tengas que hacer clic en la flecha hacia la derecha para obtener la descripción. </p>
</td>
</tr>
</tbody>
</table>

1. Seleccione **la característica** y se agregará el elemento de característica.

    <kbd><img src="./images/media/image033.png" alt="imagen033"></kbd>

2. Utilice nuevamente **CTRL+ESPACIO** para obtener la lista de funciones disponibles.

    <kbd><img src="./images/media/image034.png" alt="imagen034"></kbd>

3. Escriba la palabra **servlet** para ver las funciones de servlet disponibles.

    <kbd><img src="./images/media/image035.png" alt="imagen035"></kbd>

4. Utilice la tecla de flecha hacia abajo para obtener la descripción de **servlet-6.0** .

    <kbd><img src="./images/media/image036.png" alt="imagen036"></kbd>

5. Seleccione la función **servlet-6.0** y su configuración ahora debería verse así:

    <kbd><img src="./images/media/image037.png" alt="imagen037"></kbd>

6. Para esta parte del laboratorio, no es necesario definir un almacén de claves ni el registro básico, por lo que deberá eliminar las entradas generadas. Su configuración debería verse así:

    <kbd><img src="./images/media/image038.png" alt="imagen038"></kbd>

7. Guarde la configuración utilizando **CTRL+S** .

8. Cierre el archivo **server.xml** .

### 6.3.4 Uso del modo Liberty Dev

El modo de desarrollo Liberty, o modo dev, permite desarrollar aplicaciones con cualquier editor de texto o IDE, ofreciendo recarga e implementación en caliente, pruebas bajo demanda y compatibilidad con depuradores. El modo de desarrollo Liberty se habilita a través de proyectos Maven y Gradle.

Su código se compila y se implementa automáticamente en su servidor en ejecución, lo que facilita la iteración de sus cambios.

Puedes ejecutar pruebas a demanda o incluso automáticamente para obtener información inmediata sobre tus cambios. También puedes conectar un depurador en cualquier momento para depurar tu aplicación en ejecución.

<kbd><img src="./images/media/LibertyDevMode.png" alt="Modo LibertyDev"></kbd>

<table>
<tbody>
<tr class="odd">
<td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
<td>
<p>Puedes usar las capacidades del modo de desarrollo de Liberty dentro y fuera de un IDE. Esto te brinda flexibilidad para que puedas decidir qué IDE usar.<br> En una ventana de terminal, usarías Liberty en modo de desarrollo con maven usando el comando <strong>mvn liberty:dev</strong> (o <strong>mvn liberty:devc</strong> si quieres desarrollar en un contenedor).<br> Para gradle, los comandos relacionados son <strong>gradle libertyDev</strong> y <strong>gradle libertyDevc</strong> . </p>
</td>
</tr>
</tbody>
</table>

En el entorno de laboratorio, el complemento Liberty Tools se ha instalado en Visual Studio Code. Por lo tanto, utilizará el panel de control integrado de Liberty, que ejecutará los comandos Maven relacionados de forma oculta.

1. En Visual Studio Code, expanda el Panel de Liberty.

    <kbd><img src="./images/media/image040.png" alt="imagen040"></kbd>

2. Haga clic derecho en **simpleweb** y luego **en Iniciar** para iniciar el servidor en modo de desarrollo.

    <kbd><img src="./images/media/image041.png" alt="imagen041"></kbd>

3. Se abre una terminal dentro de Visual Studio Code y puedes ver que se activa el inicio del proceso de compilación.

    <kbd><img src="./images/media/image042.png" alt="imagen042"></kbd>

4. Se descargan el complemento Maven de Liberty y los artefactos del servidor Liberty, luego el servidor está listo para la prueba.

    <kbd><img src="./images/media/image043.png" alt="imagen043"></kbd>

5. Abra la ventana del navegador e introduzca la URL **localhost:9080** . Debería ver algo como esto:

    <kbd><img src="./images/media/image044.png" alt="imagen044"></kbd>

<table>
<tbody>
<tr class="odd">
<td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
<td>
<p>Si aparece una ventana emergente que dice <strong>Autenticación requerida</strong> , ingrese la contraseña <strong>IBMDem0s!</strong> y haga clic en <strong>Desbloquear</strong> . </p>
</td>
</tr>
</tbody>
</table>

```
Now, let’s create a simple web application.
```

### 6.3.5 Editar la aplicación simpleweb

Ahora editarás la aplicación **web simple** , que solo consta de un servlet. Gracias al asistente de código de Liberty Tools, no tendrás que escribir el código tú mismo.

1. Cambiar a Visual Studio Code.

2. En Visual Studio Code, expanda la ruta a **src/main/java/com/demo/rest** , luego **haga clic derecho** en **demo** y seleccione **Nuevo archivo** .

    <kbd><img src="./images/media/image045.png" alt="imagen045"></kbd>

3. Ingrese el nombre **helloWorldServlet.java** y presione **ENTER** .

    <kbd><img src="./images/media/image046.png" alt="imagen046"></kbd>

4. El archivo **src/main/java/com/demo/helloWorldServlet.java** se genera y se abre en un editor.

    <kbd><img src="./images/media/image047.png" alt="imagen047"></kbd>

5. Elimine todo el código del archivo. Luego, introduzca **el servlet** y presione **Ctrl+Espacio** .

    <kbd><img src="./images/media/image048.png" alt="imagen048"></kbd>

6. El asistente de código ofrece algunos métodos de servlet para Jakarta EE. Seleccione **servlet_doget** y se generará el código de inicio necesario. Como puede ver, los campos que deben modificarse están resaltados.

    <kbd><img src="./images/media/image049.png" alt="imagen049"></kbd>

7. Cambia el **nombre del servlet** a **helloWorldServlet** y los **patrones de URL** a **/helloWorld** . El código debería verse así:

    <kbd><img src="./images/media/image050.png" alt="imagen050"></kbd>

8. Presione **CTRL+S** para guardar el cambio de código. Observe la salida de la terminal. Como Liberty se ha iniciado en modo de desarrollo, los cambios de código se aplican automáticamente, el código fuente se compila y Liberty se actualiza.

    <kbd><img src="./images/media/image051.png" alt="imagen051"></kbd>

9. Abra el navegador y la URL **localhost:9080/simpleweb/helloWorld** . Debería ver la salida del servlet creado.

    <kbd><img src="./images/media/image052.png" alt="imagen052"></kbd>

10. Regrese a Visual Studio Code y cambie el código fuente del texto de respuesta del servlet a algo como esto: **helloWorld - Ejemplo de solicitud HTTP GET para HTTPServlet**

    <kbd><img src="./images/media/image053.png" alt="imagen053"></kbd>

11. Guarde los cambios y vuelva a cargar la página en el navegador. El resultado debería actualizarse.

    <kbd><img src="./images/media/image054.png" alt="imagen054"></kbd>

12. Regrese a Visual Studio Code y cierre el editor del archivo **helloWorldServlet.java** .

El paso final como desarrollador es exportar la aplicación desarrollada como archivo WAR para que pueda usarse en la siguiente parte del laboratorio.

### 6.3.6 Exportar la aplicación desarrollada como archivo WAR

Exportar la aplicación desarrollada para que el equipo de operaciones pueda implementarla en Liberty.

El pom de Maven generado no genera un archivo WAR por defecto, ya que utiliza un enfoque "looseApplication" para optimizar el desarrollo del bucle interno. (Para más detalles, consulte https://github.com/OpenLiberty/ci.maven). Para cambiar el comportamiento de compilación predeterminado, debe ajustar el archivo pom.xml y configurar el plugin de Maven de Liberty para que genere un WAR mediante la propiedad **&lt;looseApplication&gt;false&lt;/looseApplication&gt;** .

1. Regrese a Visual Studio Code.

2. En el panel de Liberty, **haga clic derecho** en la aplicación **simpleweb** y seleccione **Detener** (o use **CTRL+C** en la ventana del terminal en su lugar).

    <kbd><img src="./images/media/image055.png" alt="imagen055"></kbd>

3. Verificar en la terminal que Liberty haya sido detenido.

    <kbd><img src="./images/media/image056.png" alt="imagen056"></kbd>

4. En Visual Studio Code, abra el archivo **pom.xml** y agregue a la configuración del complemento Maven de Liberty las líneas:

    ```
     <configuration>
     <looseApplication>false</looseApplication>
     </configuration>
    ```

    <kbd><img src="./images/media/image057.png" alt="imagen057"></kbd>

5. Si iniciara Liberty ahora nuevamente en modo de desarrollo, la propiedad looseApplication se ignoraría y vería una advertencia como esta:

    <kbd><img src="./images/media/image058.png" alt="imagen058"></kbd>

    Por lo tanto, debe iniciar Liberty en modo de ejecución para generar el archivo WAR. Esto se puede hacer introduciendo el comando en la ventana de terminal:

    ```
     mvn liberty:run
    ```

    <kbd><img src="./images/media/image059.png" alt="imagen059"></kbd>

    Como puede ver en la captura de pantalla anterior, maven ha creado el archivo **simpleweb.war** y lo ha almacenado en el directorio **~/Student/dev/simpleweb/target/** .

6. Desplácese hacia abajo y podrá ver que se ha instalado en el directorio ~/Student/dev/simpleweb/target/liberty/wlp/usr/servers/defaultServer/apps.

    <kbd><img src="./images/media/image060.png" alt="imagen060"></kbd>

7. Siéntase libre de probar la aplicación en el navegador, luego detenga la instancia de Liberty usando **CTRL+C** .

8. Cierre Visual Studio Code.

### 6.3.7 Crear un paquete de servidor

Para el próximo laboratorio, necesitará el archivo WAR así como el **server.xml** que se puede encontrar en la instancia de Liberty creada en: **~/Student/dev/simpleweb/target/liberty/wlp/usr/servers/defaultServer** .

Las aplicaciones más complejas también dependen de otros archivos como archivos jar de utilidades, archivos de configuración adicionales de Liberty y controladores JDBC, por ejemplo.

Entonces, en lugar de copiar los archivos uno por uno, podría crear un paquete de servidor que contenga todos los archivos.

¿Qué es un **paquete de servidor** ? Un paquete de servidor puede contener solo el directorio de usuario o el servidor de aplicaciones completo.

La sintaxis del comando del paquete del servidor es:

```
server package server_name --archive=package_file_name.jar --include=all
```

Con la opción **--include=all** , se empaquetan los binarios de Liberty así como el directorio usr.

Para obtener más detalles y opciones, consulte https://www.ibm.com/docs/en/was-liberty/base?topic=line-packaging-liberty-server-from-command.

1. Para crear el paquete del servidor, ejecute el siguiente comando:

    ```
     ~/Student/dev/simpleweb/target/liberty/wlp/bin/server package defaultServer --archive=simpleweb-serverpackage.jar --include=all
    ```

    <kbd><img src="./images/media/image061.png" alt="imagen061"></kbd>

2. Para entregar el paquete del servidor al equipo de operaciones, utilice los siguientes comandos:

    ```
     cp ~/Student/dev/simpleweb/target/liberty/wlp/usr/servers/defaultServer/simpleweb-serverpackage.jar ~/Student/assets
    ```

### 6.3.8 Resumen

Felicitaciones, has terminado la parte de desarrollo de la aplicación.

**Resumamos lo que has hecho hasta ahora.**

Actuó como desarrollador y utilizó Visual Studio Code y Liberty Tools para estas tareas:

- generó un proyecto de inicio de Liberty que incluye la configuración requerida de maven y Liberty.
- Utilicé el asistente de configuración de Liberty Tools para ajustar la configuración de Liberty.
- Se utilizó el modo Liberty Dev para el desarrollo de bucle interno.
- actualizó la aplicación simpleweb utilizando el asistente de código Jakarta EE.
- exportó la aplicación web como archivo WAR.
- creó un paquete de servidor que incluye la aplicación y los binarios de Liberty.

Enlaces útiles: https://github.com/OpenLiberty/liberty-tools-vscode/blob/HEAD/docs/user-guide.md

### 6.4 Operaciones de Liberty

Ahora trabajará con Liberty desde una perspectiva operativa. El equipo de desarrollo le ha proporcionado un paquete de servidor de Liberty. Este paquete contiene toda la configuración necesaria para ejecutar la aplicación **simpleweb** . Normalmente, este paquete no está listo para producción, ya que probablemente no sea portable entre etapas y no cumpla con los requisitos de seguridad, entre otros.

En esta parte del laboratorio, explorará cómo crear fragmentos de configuración y cómo administrar Liberty desde la línea de comandos. Pero primero, explorará el paquete del servidor y comprenderá las actualizaciones dinámicas.

### 6.4.1 Explorar el paquete del servidor

Ahora explorará el paquete del servidor Liberty para comprender mejor cómo usarlo, además lo utilizará para aprender más sobre **la administración de Liberty desde la línea de comandos** y **las actualizaciones dinámicas de Liberty** .

<table>
<tbody>
<tr class="odd">
<td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
<td>
<p>En esta sección, usará el comando <strong>server run</strong> en lugar del comando <strong>server start</strong> . Esto le permitirá ver los registros inmediatamente en lugar de tener que usar el comando tail. También le permitirá detener el servidor Liberty con <strong>Ctrl+C.</strong> </p>
</td>
</tr>
</tbody>
</table>

### 6.4.1.1 Extraer el paquete Liberty desde la línea de comandos

1. Extraiga el paquete del servidor Liberty e intente ejecutarlo. Cuando se le solicite, introduzca **"test"** como directorio de destino.

    ```
     cd ~/Student/ops/
     java -jar ~/Student/assets/simpleweb-serverpackage.jar
    ```

    <kbd><img src="./images/media/image062.png" alt="imagen062"></kbd>

    Se creó el directorio test/wlp y contiene la instancia de Liberty configurada, incluida la aplicación.

2. Ejecute el siguiente comando para **obtener la versión de Liberty** :

    ```
     test/wlp/bin/productInfo version
    ```

    <kbd><img src="./images/media/image063.png" alt="imagen063"></kbd>

3. Ejecute el siguiente comando para **enumerar las características de Liberty** que se han instalado:

    ```
     test/wlp/bin/productInfo featureInfo
    ```

    <kbd><img src="./images/media/image064.png" alt="imagen064"></kbd>

    Como puede ver, el paquete de servidor proporcionado por el desarrollador solo contiene las características de **servlet-6.0** , que es la única característica requerida por la aplicación.

4. Ejecute el siguiente comando para obtener la **lista de servidores de aplicaciones Liberty definidos** :

    ```
     test/wlp/bin/server list
    ```

    <kbd><img src="./images/media/image065.png" alt="imagen065"></kbd>

5. **Inicie la instancia del servidor Liberty** ejecutando el comando:

    ```
     test/wlp/bin/server start defaultServer
    ```

    <kbd><img src="./images/media/image066.png" alt="imagen066"></kbd>

    Esto ejecuta el servidor en segundo plano y la salida se escribe en archivos en el directorio **test/wlp/bin/servers/defaultServer/logs** .

    Para iniciar el servidor en primer plano (para que los mensajes de la consola se muestren en la ventana de comandos), debe usar el comando

    ```
     test/wlp/bin/server run defaultServer.
    ```

    Lo usarás más tarde en el laboratorio.

6. Vea el archivo messages.log del servidor Liberty para ver los mensajes de inicio del servidor mediante el comando:

    ```
     cat test/wlp/usr/servers/defaultServer/logs/messages.log
    ```

    <kbd><img src="./images/media/image067.png" alt="imagen067"></kbd>

    Al principio del registro, se puede ver la versión de Open Liberty utilizada (versión 24.0.0.2 o posterior). El servidor se inicia cuando se muestra el mensaje **"El servidor defaultServer está listo para ejecutar un planeta más inteligente"** en el archivo messages.log.

7. Pruebe que la aplicación sea accesible a través de la URL **http://localhost:9080/simpleweb/helloWorld**

    <kbd><img src="./images/media/image068.png" alt="imagen068"></kbd>

### 6.4.1.2 Actualizaciones dinámicas de Liberty

Hagamos un breve recorrido por las actualizaciones dinámicas de Liberty. Usarás Visual Studio Code para realizar algunos cambios menores de configuración. Para esta parte del laboratorio, también podrías usar un editor de texto sencillo como vi o gedit.

1. Abra Visual Studio Code.

    ```
     cd ~/Student/ops/test
     code .
    ```

    <kbd><img src="./images/media/image069.png" alt="imagen069"></kbd>

2. Se abre Visual Studio Code. Haga clic en **Sí** si se le solicita que confíe en el autor.

    <kbd><img src="./images/media/image070.png" alt="imagen070"></kbd>

3. En Visual Studio Code, abra una ventana de terminal

    <kbd><img src="./images/media/image071.png" alt="imagen071"></kbd>

4. En la terminal, use el comando tail para mostrar el registro de mensajes de Liberty.

    ```
     tail -f wlp/usr/servers/defaultServer/logs/messages.log
    ```

    <kbd><img src="./images/media/image072.png" alt="imagen072"></kbd>

5. Espere hasta que se haya inicializado la aplicación web

    <kbd><img src="./images/media/image073.png" alt="imagen073"></kbd>

6. En Visual Studio Code, navegue a **wlp &gt; usr &gt; servers &gt; defaultServer** y abra el archivo **server.xml** .

    <kbd><img src="./images/media/image074.png" alt="imagen074"></kbd>

7. En el archivo **server.xml** , cambie la configuración httpPort del puerto **9080** al puerto **9081** .

    <kbd><img src="./images/media/image075.png" alt="imagen075"></kbd>

    Puedes ver en la terminal que el cambio se ha recogido y Liberty ahora escucha en el puerto **9081** .

    <kbd><img src="./images/media/image076.png" alt="imagen076"></kbd>

8. Cambie la configuración contextRoot de webApplication de **“/simpleweb”** a **“/mysimpleweb”** .

    <kbd><img src="./images/media/image077.png" alt="imagen077"></kbd>

    En el registro se puede observar que se ha recogido el cambio.

    <kbd><img src="./images/media/image078.png" alt="imagen078"></kbd>

9. Cambie al navegador y acceda a la aplicación a través de la URL **localhost:9081/mysimpleweb/helloWorld** .

    <kbd><img src="./images/media/image079.png" alt="imagen079"></kbd>

    Como has visto, puedes cambiar la configuración de Liberty sin tener que reiniciar el servidor. Analizarás esto con más detalle más adelante en el laboratorio, por ejemplo, cuando actualices dinámicamente el registro. Ahora, detengamos el servidor.

10. En la terminal, presione **CTRL+C** para detener el comando tail.

11. Detenga la instancia de Liberty ejecutando en la terminal el comando:

    ```
    wlp/bin/server stop defaultServer
    ```

    <kbd><img src="./images/media/image080.png" alt="imagen080"></kbd>

### 6.4.2 Crear fragmentos de configuración de Liberty

Existen diferentes maneras de crear una configuración de servidor Liberty y, a menudo, intervienen diferentes roles para obtener la configuración final para producción. Por ejemplo, la configuración específica de la aplicación suele ser creada por el desarrollador, mientras que la configuración de seguridad suele ser realizada por el departamento de operaciones. El departamento de operaciones también suele ser responsable de la portabilidad de la configuración entre etapas, la configuración del registro, etc.

Puede crear fragmentos de configuración de Liberty copiando los fragmentos relacionados de la documentación del producto y ajustándolos en un editor de texto normal. En esta parte del laboratorio, verá que el complemento Liberty Tools de Visual Studio Code puede ayudarle a agilizar la creación de fragmentos de configuración, ya que proporciona asistencia para la configuración, incluida la documentación. Comencemos.

Ahora modificará el archivo **server.xml** que se ha proporcionado como parte del paquete del servidor para hacerlo más portátil y reutilizable.

1. En Visual Studio Code, abra el archivo **server.xml** si lo cerró anteriormente.

    <kbd><img src="./images/media/image081.png" alt="imagen081"></kbd>

2. Eche un vistazo al elemento httpEndpoint.

    <kbd><img src="./images/media/image082.png" alt="imagen082"></kbd>

    Como se menciona en el comentario, el httpEndpoint no es accesible por defecto desde un cliente remoto. Esto es positivo desde el punto de vista de la seguridad y funciona correctamente si el cliente es local respecto al servidor. Sin embargo, si, por ejemplo, utiliza un balanceador de carga remoto o un servidor HTTP remoto, esto no funcionará. Por lo tanto, es probable que en situaciones en las que desee permitir el acceso a la aplicación desde un cliente remoto, deba agregar un atributo de host. Para ello, utilice el asistente de configuración de Liberty Tools.

3. Coloque el cursor al final de la línea **&lt;httpEndpoint id="defaultHttpEndpoint"** y presione **ENTER** para agregar otra línea.

    En la nueva línea, presione **CTRL+ESPACIO** para ver los atributos disponibles.

    Utilice la tecla de flecha hacia abajo y navegue hasta el atributo **del host** para ver la descripción del atributo.

    <kbd><img src="./images/media/image083.png" alt="imagen083"></kbd>

4. Seleccione el host y su configuración debería verse así:

    <kbd><img src="./images/media/image084.png" alt="imagen084"></kbd>

    Como puede ver, el atributo host tiene como valor predeterminado **localhost** .

### 6.4.2.1 Utilizar variables para la portabilidad

Para que la configuración sea portátil, reemplazará los valores fijos de puertos y host con variables de Liberty. Estas variables pueden definirse con un valor predeterminado y sobrescribirse desde dentro o fuera de Liberty. Para ilustrar el concepto, ajustará la configuración de httpEndpoint.

Puede utilizar el fragmento de configuración a continuación para reemplazar la configuración httpEndpoint existente con una configuración portátil.

```
<httpEndpoint id="defaultHttpEndpoint"
              host="${httpEndpoint_host}"
              httpPort="${httpEndpoint_port}"
              httpsPort="${httpEndpoint_secure_port}" />
<variable name="httpEndpoint_host" defaultValue="*"/>
<variable name="httpEndpoint_port" defaultValue="9080"/>
<variable name="httpEndpoint_secure_port" defaultValue="9443"/>
```

En su lugar, utilizará el asistente de configuración de Liberty Tools para comprender cómo podría crear dicho fragmento de configuración.

1. Coloque el cursor en una línea vacía debajo de la sección httpEndpoint, luego ingrese **var** y presione **CTRL+ESPACIO** .

    <kbd><img src="./images/media/image085.png" alt="imagen085"></kbd>

2. Seleccione **la variable** y luego ingrese el nombre **"httpEndpoint_port"** .

    <kbd><img src="./images/media/image086.png" alt="imagen086"></kbd>

3. Coloque el cursor después de **name="httpEndpoint_port"** , ingrese un **ESPACIO** y presione **CTRL+ESPACIO** .

    <kbd><img src="./images/media/image087.png" alt="imagen087"></kbd>

4. Seleccione **defaultValue** e ingrese el valor **9080** .

    <kbd><img src="./images/media/image088.png" alt="imagen088"></kbd>

5. Utilice copiar y pegar para crear dos variables adicionales:

    - uno con el nombre **"httpEndpoint_secure_port"** y el valor predeterminado **"9443"**
    - el otro con el nombre **"httpEndpoint_host"** y el valor **"*"** .

    Su configuración ahora debería verse así:

    <kbd><img src="./images/media/image089.png" alt="imagen089"></kbd>

6. Cambie a la sección **httpEndpoint** , elimine del atributo **host** el valor **"localhost"** , ingrese **${ht** y presione **CTRL+ESPACIO** .

    <kbd><img src="./images/media/image090.png" alt="imagen090"></kbd>

    Como puede ver, se ofrecen los nombres de las variables.

    <p> SUGERENCIA: Si la finalización del código no muestra <strong>ninguna sugerencia</strong> , elimine el corchete <strong>{</strong> para que solo quede <strong>$ht</strong> y realice la finalización del código.</p>

7. Seleccione **"httpEndpoint_host"** y luego introduzca **"}"** . Su configuración debería verse así:

    <kbd><img src="./images/media/image090b.png" alt="imagen090b"></kbd>

8. Realice el mismo tipo de cambio para los atributos **httpPort** y **httpsPort** .

    La configuración final de httpEndpoint ahora debería verse así:

    <kbd><img src="./images/media/image091.png" alt="imagen091"></kbd>

9. Guarde sus cambios.

    Su archivo **server.xml** ahora debería verse así:

    ```
     <?xml version="1.0" encoding="UTF-8"?>
     <server description="new server">

     <!-- Enable features -->
     <featureManager>
         <feature>servlet-6.0</feature>
     </featureManager>


     <!-- To access this server from a remote client add a host attribute to the following element, e.g. host="*" -->
     <httpEndpoint id="defaultHttpEndpoint"
                   host="${httpEndpoint_host}"
                   httpPort="${httpEndpoint_port}"
                   httpsPort="${httpEndpoint_secure_port}" />
     <variable name="httpEndpoint_host" defaultValue="*"/>
     <variable name="httpEndpoint_port" defaultValue="9080"/>
     <variable name="httpEndpoint_secure_port" defaultValue="9443"/>

     <!-- Automatically expand WAR files and EAR files -->
     <applicationManager autoExpand="true"/>

     <!-- Configures the application on a specified context root -->
     <webApplication contextRoot="/mysimpleweb" location="simpleweb.war" />

     <!-- Default SSL configuration enables trust for default certificates from the Java runtime -->
     <ssl id="defaultSSLConfig" trustDefaultCerts="true" />
     </server>
    ```

    Ahora probemos si la configuración de Liberty es realmente portable.

10. Desde la terminal de Visual Studio Code, inicie la instancia del servidor Liberty mediante el siguiente comando:

    ```
    wlp/bin/server run defaultServer
    ```

    <kbd><img src="./images/media/image092.png" alt="imagen092"></kbd>

    Como puede ver, el servidor Liberty se inicia y escucha en el puerto **9080** .

11. Presione **CTRL+C** para detener el servidor.

12. Establezca el valor httpEnpoint_port en la variable de entorno del sistema operativo e inicie nuevamente el servidor Liberty.

    ```
    export httpEndpoint_port=9081
    wlp/bin/server run defaultServer
    ```

    <kbd><img src="./images/media/image093.png" alt="imagen093"></kbd>

    Como puede ver, el servidor Liberty ahora escucha en el puerto **9081** , lo que indica que puede anular desde fuera de Liberty la configuración predeterminada definida en el archivo server.xml de Liberty. En un entorno de Kubernetes, podría usar, por ejemplo, un mapa de configuración para cambiar la configuración.

13. Presione **Ctrl+C** para detener el servidor. Luego, desactive la variable del sistema operativo con el siguiente comando:

    ```
    unset httpEndpoint_port
    ```

    Esto restaurará el valor httpEnpoint_port en la variable de entorno del sistema operativo a **9080** .

### 6.4.2.2 Utilice inclusiones para una mejor reutilización y visibilidad

Si configura un servidor Liberty con recursos como fuentes de datos, colas JMS, registro de usuarios, etc., su archivo de configuración puede resultar bastante extenso y difícil de leer y mantener. Liberty permite especificar recursos de configuración para incluirlos en la configuración del servidor. Esto ayuda a mantener el control sobre la configuración, facilita la reutilización de las diferentes configuraciones y permite dividir la responsabilidad de la configuración entre diferentes equipos. El desarrollador, por ejemplo, podría crear la configuración específica de la aplicación y gestionar la configuración de seguridad.

Ahora utilizará **inclusiones** para estructurar la configuración del servidor.

1. En la terminal de Visual Studio Code, copie el archivo server.xml existente en un nuevo archivo llamado application-config.xml.

    ```
     cp wlp/usr/servers/defaultServer/server.xml wlp/usr/servers/defaultServer/application-config.xml
    ```

    <kbd><img src="./images/media/image094.png" alt="imagen094"></kbd>

2. Abra el archivo recién creado **application-config.xml** en Visual Studio Code.

    <kbd><img src="./images/media/image095.png" alt="imagen095"></kbd>

3. Elimine toda la configuración de la sección del servidor, excepto la definición del elemento **webApplication** . Su **archivo application-config.xml** debería tener este aspecto:

    <kbd><img src="./images/media/image096.png" alt="imagen096"></kbd>

4. Guarde los cambios y luego cierre el archivo **application-config.xml** .

5. Vaya al archivo server.xml. Elimine el elemento **webApplication** , escriba " **include"** y presione **Ctrl+Espacio** .

    El asistente de configuración de Liberty Tools le muestra los elementos disponibles.

    <kbd><img src="./images/media/image097.png" alt="imagen097"></kbd>

6. Seleccione **"Incluir"** y se generará el elemento. Como valor para **la ubicación** , introduzca **"application-config.xml"** .

    <kbd><img src="./images/media/image098.png" alt="imagen098"></kbd>

7. Como propietario del archivo server.xml, es posible que desee decidir qué sucede si el archivo que se incluirá no existe o contiene configuraciones conflictivas.

    Vaya al final de la instrucción include y presione **CTRL+ESPACIO** . Se mostrarán los atributos disponibles para el elemento include.

    <kbd><img src="./images/media/image099.png" alt="imagen099"></kbd>

    Como puede ver, puede definir el archivo de inclusión como opcional, por lo que Liberty no generará un error si falta el archivo de inclusión.

8. Haga clic en **Conflicto** para ver los atributos disponibles para esas opciones.

    <kbd><img src="./images/media/image100.png" alt="imagen100"></kbd>

    Si desea asegurarse de que las configuraciones en server.xml no puedan ser anuladas por los archivos incluidos, seleccione **IGNORAR** ; de lo contrario, utilice **FUSIONAR** o **REEMPLAZAR** .

9. Haga clic en **FUSIONAR** y su declaración de inclusión debería verse así:

    ```
     <include location="application-config.xml" onConflict="MERGE"/>
    ```

    <kbd><img src="./images/media/image101.png" alt="imagen101"></kbd>

    Puedes configurar varios archivos de inclusión; por ejemplo, uno para security-config.xml y otro para la configuración de recursos específicos, como bases de datos o JMS. Ahora, probemos si la **inclusión** funciona.

10. Guarde el archivo **server.xml** .

11. Desde la terminal de Visual Studio Code, inicie la instancia del servidor Liberty mediante el siguiente comando:

    ```
    wlp/bin/server run defaultServer
    ```

    Como puedes ver, la **inclusión** se ha encontrado y procesado, por lo que se inicia la aplicación.

    <kbd><img src="./images/media/image102.png" alt="imagen102"></kbd>

    Mantenga el servidor funcionando como lo necesitamos en la siguiente sección.

### 6.4.2.3 Habilitar la seguridad del transporte

En este momento, no puede acceder a Liberty mediante HTTPS. Si bien el puerto HTTPS 9443 está definido, SSL no está habilitado en Liberty. SSL se puede habilitar mediante la función de seguridad de transporte. Por lo tanto, el siguiente paso es habilitar la seguridad de transporte y revisar otros temas relacionados, como los almacenes de claves.

1. En el archivo **server.xml** , navegue hasta la sección featureManager.

2. Agregue la función **transportSecurity-1.0** a la sección **featureManager** agregando la línea:

    ```
     <feature>transportSecurity-1.0</feature>
    ```

    Alternativamente, puede utilizar el asistente de configuración para habilitarlo.

    <kbd><img src="./images/media/image103.png" alt="imagen103"></kbd>

3. Eche un vistazo a los registros y podrá ver que la función aún no está disponible.

    <kbd><img src="./images/media/image104.png" alt="imagen104"></kbd>

    Esto se debe a que el paquete del servidor Liberty generado por el desarrollador solo incluye las características requeridas (características definidas en el archivo de configuración del servidor). Utilizará la **herramienta Liberty featureUtility** para instalar la característica faltante. Esta característica podría descargarse desde un repositorio local si está configurada; en este caso, la descargará desde un repositorio central de Maven.

4. En la ventana de terminal, detenga la instancia de Liberty presionando **CTRL+C** .

    Luego, ejecute el siguiente comando para instalar la función faltante del repositorio maven:

    ```
     wlp/bin/featureUtility installFeature transportSecurity-1.0
    ```

    <kbd><img src="./images/media/image105.png" alt="imagen105"></kbd>

5. Luego, inicie nuevamente la instancia de Liberty ejecutando el siguiente comando:

    ```
     wlp/bin/server run defaultServer
    ```

    <kbd><img src="./images/media/image106.png" alt="imagen106"></kbd>

    Como puede ver, Liberty creó un certificado y lo colocó en el archivo de clave SSL **"wlp/usr/servers/defaultServer/resources/security/key.p12"** .

6. Liberty usó la variable **keystore_password** para proteger el almacén de claves. Como no se definió un valor para la variable keystore_password, Liberty generó una contraseña y la almacenó en el archivo **server.env** . En Visual Studio, abra el archivo **server.env** para ver la contraseña del almacén de claves. Es probable que su contraseña sea diferente, ya que se generó aleatoriamente.

    <kbd><img src="./images/media/image107.png" alt="imagen107"></kbd>

    Cierre el archivo **server.env** .

7. Para que sea más visible de dónde proviene la contraseña del almacén de claves, agregue la siguiente definición al archivo **server.xml** :

    ```
     <keyStore id="defaultKeyStore" password="${keystore_password}" />
    ```

    El elemento keyStore también le permite especificar una ubicación de almacén de claves diferente y mucho más.

    <kbd><img src="./images/media/image108.png" alt="imagen108"></kbd>

8. Revise su configuración en **server.xml** . Debería verse así:

    ```
     <?xml version="1.0" encoding="UTF-8"?>
     <server description="new server">

         <!-- Enable features -->
         <featureManager>
             <feature>servlet-6.0</feature>
             <feature>transportSecurity-1.0</feature>
         </featureManager>


         <!-- To access this server from a remote client add a host attribute to the following element, e.g. host="*" -->
         <httpEndpoint id="defaultHttpEndpoint"
                     host="${httpEndpoint_host}"
                     httpPort="${httpEndpoint_port}"
                     httpsPort="${httpEndpoint_secure_port}" />
         <variable name="httpEndpoint_host" defaultValue="*"/>
         <variable name="httpEndpoint_port" defaultValue="9080"/>
         <variable name="httpEndpoint_secure_port" defaultValue="9443"/>

         <!-- Automatically expand WAR files and EAR files -->
         <applicationManager autoExpand="true"/>

         <!-- Configures the application on a specified context root -->
         <include location="application-config.xml" onConflict="MERGE"/>

         <!-- Default SSL configuration enables trust for default certificates from the Java runtime -->
         <ssl id="defaultSSLConfig" trustDefaultCerts="true" />
         <keyStore id="defaultKeyStore" password="${keystore_password}" />
     </server>
    ```

9. Ahora veamos si la aplicación es accesible a través de HTTPS.

    Cambie al navegador y acceda a Liberty a través de **https://localhost:9443/mysimpleweb/helloWorld** .

    Debería recibir una advertencia de seguridad como ésta:

    <kbd><img src="./images/media/image109.png" alt="imagen109"></kbd>

10. Haga clic en **Avanzado** , luego desplácese hacia abajo y haga clic en **"Aceptar el riesgo y continuar"** .

    <kbd><img src="./images/media/image110.png" alt="imagen110"></kbd>

11. Debería ver la salida de la aplicación web.

    <kbd><img src="./images/media/image111.png" alt="imagen111"></kbd>

12. Regrese a Visual Studio Code y detenga la instancia de Liberty en ejecución ingresando **CTRL+C** en la ventana de terminal.

13. Cierre Visual Studio Code.

### 6.4.2.4 Copia de seguridad de los archivos generados

En la siguiente sección del laboratorio, reutilizarás los fragmentos de configuración generados y otros recursos. Por lo tanto, es recomendable crear un repositorio de fragmentos. Estos suelen alojarse en un repositorio Git, donde usarás la carpeta **~/Student/assets** . También usarás el directorio de recursos para almacenar el archivo WAR de la aplicación.

1. Copie los archivos de configuración generados así como el archivo war de la aplicación en el directorio de activos.

    ```
     cp ~/Student/ops/test/wlp/usr/servers/defaultServer/server.* ~/Student/assets

     cp ~/Student/ops/test/wlp/usr/servers/defaultServer/application-config.xml ~/Student/assets

     cp ~/Student/ops/test/wlp/usr/servers/defaultServer/apps/simpleweb.war ~/Student/assets
    ```

    <kbd><img src="./images/media/image112a.png" alt="imagen112"></kbd>

2. Verifique que el directorio de recursos contenga el archivo WAR de la aplicación y los archivos de configuración. También contiene el paquete del servidor, pero ya no es necesario.

    ```
     ls ~/Student/assets
    ```

    <kbd><img src="./images/media/image112b.png" alt="imagen112"></kbd>

3. Si aún no lo ha hecho, salga de **Visual Studio Code** y detenga cualquier instancia de Liberty que esté en ejecución.

### 6.4.2.5 Resumen

En esta sección del laboratorio, obtendrá una idea de cómo crear y usar fragmentos de configuración:

- Usé el **asistente de configuración de Liberty Tools** para crear fragmentos de configuración y configurar Liberty.
- Usé la **herramienta Liberty featureUtility** para instalar las funciones faltantes.
- Aprendí a usar **variables** para hacer la configuración más portable.
- Aprendí a usar **inclusiones** para dividir la configuración en múltiples archivos reutilizables.
- creó una configuración de seguridad.

Comentarios:

- En lugar de utilizar el asistente de configuración de Liberty Tools en Visual Studio Code, también puede utilizar la documentación del producto y copiar y pegar para crear fragmentos de configuración de Liberty.
- También puede utilizar las herramientas de migración de IBM para transformar una configuración existente de WebSphere Traditional y otros entornos de ejecución en una configuración Liberty.

### 6.5 Administración de la Libertad

Ahora cambiemos al rol de administrador de Liberty y exploremos cómo instalar y configurar Liberty desde un punto de vista de administrador.

Un administrador tradicional suele descargar los binarios del servidor de aplicaciones desde las páginas de IBM y utiliza un editor estándar en lugar de un entorno de desarrollo integrado (IDE) como Visual Studio para configurar Liberty. Para descargar la última versión de WebSphere Liberty, el administrador puede consultar la página de soporte de IBM: https://www.ibm.com/support/pages/recommended-updates-websphere-application-server

### 6.5.1 Instalar Liberty desde cero

La mejor práctica para instalar Liberty es crear una instalación mínima usando la imagen del kernel de Liberty e instalar solo las características necesarias sobre ella. La imagen del kernel de WebSphere Liberty más reciente se puede descargar desde la página de soporte de IBM. Para simplificar, utilizaremos el paquete del Acuerdo de Licencia Internacional para Programas Sin Garantía (ILAN), disponible como archivo zip en: https://public.dhe.ibm.com/ibmdl/export/pub/software/websphere/wasdev/downloads/wlp/24.0.0.1/wlp-kernel-24.0.0.1.zip

1. Abra una ventana de terminal.

2. Crea un directorio para almacenar el paquete Liberty.

    ```
     mkdir ~/Student/ops/software
    ```

    <kbd><img src="./images/media/image113.png" alt="imagen113"></kbd>

3. Descargue y almacene la imagen del kernel de Liberty.

    ```
     wget https://public.dhe.ibm.com/ibmdl/export/pub/software/websphere/wasdev/downloads/wlp/24.0.0.1/wlp-kernel-24.0.0.1.zip -P ~/Student/ops/software
    ```

    <kbd><img src="./images/media/image114.png" alt="imagen114"></kbd>

4. Use el comando **ls** para comprobar que la imagen del kernel tiene un tamaño inferior a 17 MB. El espacio total en disco será mayor según las características requeridas de Liberty.

    ```
     ls -lrt ~/Student/ops/software/
    ```

    <kbd><img src="./images/media/image115.png" alt="imagen115"></kbd>

5. Cree un directorio para el entorno de integración. Este se usará para la instalación de Liberty.

    ```
     mkdir ~/Student/ops/int
     cd ~/Student/ops/int
    ```

    <kbd><img src="./images/media/image116.png" alt="imagen116"></kbd>

6. Utilice el comando descomprimir para extraer la imagen.

    ```
     unzip ../software/wlp-kernel-24.0.0.1.zip
    ```

    <kbd><img src="./images/media/image117.png" alt="imagen117"></kbd>

<table>
<tbody>
<tr class="odd">
<td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
<td>
<p>En la página de soporte de IBM, además de los paquetes de conveniencia, como el paquete del kernel de Liberty, también encontrará archivos de Liberty para Liberty Core, Liberty Base o Liberty ND. Para instalar un archivo de este tipo, utilice un comando como: <strong>"java -jar ../wlp-base-all-24.0.0.1.jar --acceptLicense".</strong>  </p>
</td>
</tr>
</tbody>
</table>

1. Obtenga la versión Liberty ejecutando el siguiente comando:

    ```
     wlp/bin/productInfo version
    ```

    <kbd><img src="./images/media/image118.png" alt="imagen118"></kbd>

    Como puede ver, este es un paquete ILAN que se puede utilizar tanto para evaluación como para producción.

2. Obtenga la lista de características de Liberty que forman parte de la instalación:

    ```
     wlp/bin/productInfo featureInfo
    ```

    <kbd><img src="./images/media/image119.png" alt="imagen119"></kbd>

    Como puedes ver, no se incluye ninguna característica en la imagen del kernel.

    Ahora que se ha instalado Liberty, el siguiente paso es crear una instancia de servidor Liberty.

<table>
<tbody>
<tr class="odd">
<td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
<td>
<p>Como has visto, la instalación de Liberty es básicamente una descompresión.<br> Si desea actualizar Liberty más adelante, puede aplicar un archivo jar o simplemente reemplazar los binarios.</p>
</td>
</tr>
</tbody>
</table>

### 6.5.2 Introducción a la configuración de variables de entorno de Liberty

Puede personalizar el entorno de Liberty mediante variables específicas para facilitar la ubicación de los binarios del producto y los recursos compartidos. Estas variables se especifican mediante el archivo server.env. Puede usar este archivo en la instalación y en el servidor para especificar variables de entorno como **JAVA_HOME** , **WLP_USER_DIR** y **WLP_OUTPUT_DIR** . Aquí puede usar algunas variables específicas de Liberty para personalizar el entorno: (consulte también https://www.ibm.com/docs/en/was-liberty/nd?topic=liberty-customizing-environment)

- **${wlp.install.dir}** : Esta variable de configuración tiene una ubicación inferida. El directorio de instalación siempre se establece en el directorio principal del directorio que contiene el script de inicio o en el directorio principal del directorio /lib que contiene los archivos jar de destino.
- **JVM_ARGS** : Esta variable de entorno permite especificar una lista de opciones de línea de comandos, como propiedades del sistema o parámetros -X, que se pasan a la JVM al iniciar el servidor. Los valores que contengan espacios deben ir entre comillas.
- **WLP_USER_DIR** : Esta variable de entorno permite especificar una ubicación alternativa para **wlp.user.dir** . Debe ser una ruta absoluta. Si se especifica, el entorno de ejecución busca recursos compartidos y definiciones de servidor en el directorio especificado. **WLP_USER_DIR** solo se puede especificar en el archivo **${wlp.install.dir}/etc/server.env** , ya que su propósito es especificar la ubicación de la configuración restante. Una vez encontrada y fusionada la configuración restante, no se espera ni se admite ninguna otra configuración en una ubicación diferente.
- **WLP_OUTPUT_DIR** : Esta variable de entorno permite especificar una ubicación alternativa para la salida generada por el servidor, como los registros, el directorio del área de trabajo y los archivos generados. Los archivos del directorio de registros pueden incluir console.log, messages.log y cualquier archivo FFDC generado. Los archivos generados pueden incluir volcados de servidor creados con los comandos server dump o server javadump. Esta variable debe ser una ruta absoluta.

### 6.5.3 Crear una instancia de servidor Liberty

El comando **"server" de Liberty** permite iniciar, detener, crear, empaquetar y volcar un servidor Liberty. El comando **"server create** " crea un nuevo servidor Liberty con el nombre especificado. Puede encontrar más información sobre el comando "server" aquí: https://www.ibm.com/docs/en/was-liberty/base?topic=line-server-command-options

El comando **de creación del servidor** crea, por defecto, el directorio de usuario en un subdirectorio del directorio **${wlp.install.dir}** . En producción, se recomienda almacenar la configuración de Liberty en un directorio aparte. Esto se puede hacer configurando la variable de entorno **WLP_USER_DIR** .

1. El directorio etc así como el archivo server.env no se crean como parte de la instalación.<br> Utilice los siguientes comandos para establecer la variable **WLP_USER_DIR** en **/home/techzone/Student/ops/int/wlp_usr** en server.env en el nivel de tiempo de ejecución.<br> (Tenga en cuenta que la ruta en server.env debe ser absoluta, ~/Student por ejemplo no es compatible):

    ```
     mkdir ~/Student/ops/int/wlp/etc
     echo "WLP_USER_DIR=/home/techzone/Student/ops/int/wlp_usr" > ~/Student/ops/int/wlp/etc/server.env
     cat ~/Student/ops/int/wlp/etc/server.env
    ```

    <kbd><img src="./images/media/image120.png" alt="imagen120"></kbd>

2. Ejecute los siguientes comandos para crear un nuevo servidor llamado **"myServer"** :

    ```
     wlp/bin/server create myServer
    ```

    <kbd><img src="./images/media/image121.png" alt="imagen121"></kbd>

    El nuevo servidor se crea en el siguiente directorio: **wlp_usr/servers/myServer** .

3. Ejecute el siguiente comando para verificar el nombre y la ruta de la instancia del servidor:

    ```
     wlp/bin/server list
    ```

    <kbd><img src="./images/media/image122.png" alt="imagen122"></kbd>

4. Ejecute el siguiente comando para enumerar los archivos y directorios que se han creado para myServer:

    ```
     ls -lrt wlp_usr/servers/myServer
    ```

    <kbd><img src="./images/media/image123.png" alt="imagen123"></kbd>

5. Reemplace la configuración de Liberty generada con la configuración que almacenó en el directorio de activos.

    ```
     cp ~/Student/assets/server.* wlp_usr/servers/myServer
     ls -lrt wlp_usr/servers/myServer
    ```

    <kbd><img src="./images/media/image124.png" alt="imagen124"></kbd>

<table>
    <tbody>
    <tr class="odd">
    <td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
    <td>
    <p>En la configuración de Liberty, ahora tiene un archivo <strong>server.env</strong> en dos niveles:<br> - en <strong>el nivel de ejecución</strong> en <strong>${wlp.install.dir}/etc/server.env</strong> y<br> - en <strong>el nivel del servidor</strong> en <strong>${server.config.dir}/server.env</strong> .<br> Si ambos archivos están presentes, el contenido de los dos archivos se fusiona; los valores en el archivo de nivel de servidor tienen prioridad sobre los valores en el archivo de nivel de ejecución.     </p>
</td>
    </tr>
    </tbody>
</table>

1. Verifique que la configuración HTTP predefinida se ajuste a su entorno:

    ```
     cat wlp_usr/servers/myServer/server.xml | grep http
    ```

    <kbd><img src="./images/media/image125.png" alt="imagen125"></kbd>

<table>
    <tbody>
    <tr class="odd">
    <td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
    <td>
    <p>Si desea cambiar esos valores de puerto, puede definirlos en el archivo <strong>server.env</strong> o en el archivo <strong>bootstrap.properties,</strong> por ejemplo.<br> Alternativamente, puede definir la variable relacionada en el nivel del sistema operativo.      </p>
</td>
    </tr>
    </tbody>
</table>

### 6.5.4 Instalar las funciones necesarias

Ha instalado el paquete del kernel de Liberty, que no contiene ninguna característica. El siguiente paso es instalar las características necesarias. En lugar de revisar la configuración de Liberty para determinar qué características son necesarias, puede dejar que Liberty inspeccione las que faltan. Esto se puede hacer usando featureUtility y especificando el servidor que busca. El comando, por defecto, descargará las características necesarias del repositorio en línea. En un entorno aislado, puede descargar el repositorio de características desde la página de soporte de IBM y luego especificar en el comando featureUtility que se utilice un repositorio local.

1. Para descargar e instalar las funciones necesarias, utilice el siguiente comando:

    ```
     wlp/bin/featureUtility installServerFeatures myServer
    ```

    <kbd><img src="./images/media/image126.png" alt="imagen126"></kbd>

    Como puede ver, el comando detectó que faltaban las funciones **servlet-6.0** y **transportSecurity-1.0** . También descarga la función **ssl-1.0,** ya que **transportSecurity-1.0** depende de ella.

2. Verifique que las características de Liberty se hayan instalado mediante el siguiente comando:

    ```
     wlp/bin/productInfo featureInfo
    ```

    <kbd><img src="./images/media/image127.png" alt="imagen127"></kbd>

### 6.5.5 Utilice su propio almacén de claves

Si no crea un almacén de claves, pero habilita SSL, Liberty creará uno con una contraseña aleatoria. Ahora, creará su propio almacén de claves con la contraseña que elija.

1. Ejecute el siguiente comando para crear un almacén de claves

    ```
     wlp/bin/securityUtility createSSLCertificate --server=myServer --password=mySecret
    ```

    <kbd><img src="./images/media/image128.png" alt="imagen128"></kbd>

    Como puede ver, el comando utiliza el nombre de host y el nombre del servidor como subjectDN y codifica la contraseña mediante xor. El comando también permite usar codificación o cifrado AES (consulte https://www.ibm.com/docs/en/was-liberty/base?topic=applications-securityutility-command).

2. Nuestra plantilla de servidor ya tiene SSL configurado y utiliza una variable para especificar la contraseña del almacén de claves. Utilice los siguientes comandos para revisar la configuración en el archivo server.xml:

    ```
     cat wlp_usr/servers/myServer/server.xml | grep trans
     cat wlp_usr/servers/myServer/server.xml | grep keystore
    ```

    <kbd><img src="./images/media/image129.png" alt="imagen129"></kbd>

3. La contraseña del almacén de claves se ha configurado en el archivo server.env. Utilice el siguiente comando para revisar la configuración:

    ```
     cat wlp_usr/servers/myServer/server.env;echo
    ```

    <kbd><img src="./images/media/image130.png" alt="imagen130"></kbd>

    Como se esperaba, la contraseña utilizada para el almacén de claves no coincide con la de **server.env** y debe actualizarse.

4. La mejor práctica es almacenar la contraseña codificada o cifrada. En este caso, se utilizará la codificación AES y se guardará la contraseña en el archivo server.env. Para generar la contraseña codificada, se puede usar el comando "encode" de securityUtility. Utilice el siguiente comando para actualizar el archivo server.env con la contraseña codificada del almacén de claves "mySecret" y, a continuación, revise el resultado:

    ```
     echo "keystore_password=$(wlp/bin/securityUtility encode --encoding=aes mySecret)" > wlp_usr/servers/myServer/server.env
     cat wlp_usr/servers/myServer/server.env
    ```

    <kbd><img src="./images/media/image131.png" alt="imagen131"></kbd>

<table>
    <tbody>
    <tr class="odd">
    <td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
    <td>
    <p>La contraseña del almacén de claves codificada no es única, por lo que es posible que tenga una contraseña diferente a la de la captura de pantalla anterior.<br> Pero siempre que utilice la misma contraseña para codificar, todas las diferentes cadenas resultantes serán válidas.      </p>
</td>
    </tr>
    </tbody>
</table>

### 6.5.6 Verificar que la configuración del servidor funciona:

1. Inicie el servidor mediante el siguiente comando:

    ```
     wlp/bin/server start myServer
     tail -f wlp_usr/servers/myServer/logs/messages.log
    ```

    <kbd><img src="./images/media/image132.png" alt="imagen132"></kbd>

    Como puede ver, el servidor Liberty está en ejecución y escucha en los puertos **9080** y **9443.** También puede ver que se queja de la **falta del archivo de inclusión application-config.xml** . Lo solucionará más adelante.

2. Verifique que el servidor sea accesible mediante HTTPS. Abra el navegador y acceda a la aplicación web mediante la URL **https://localhost:9443** . Como antes, recibirá una advertencia indicando que su conexión no es segura. Haga clic en **"Avanzado"** , desplácese hacia abajo y haga clic en **"Aceptar el riesgo y continuar"** . Debería poder acceder a la aplicación.

    <kbd><img src="./images/media/image133.png" alt="imagen133"></kbd>

3. Regrese a la ventana de terminal y presione **CTRL+C** en la ventana de terminal para detener el comando tail.

4. Detenga el servidor mediante el siguiente comando:

    ```
     wlp/bin/server stop myServer
    ```

### 6.5.7 Implementación de una aplicación de muestra en Liberty

En la primera parte de este laboratorio, utilizó las herramientas de Liberty para desarrollar y configurar una aplicación. La aplicación se implementó mediante Maven de forma oculta. Posteriormente, utilizó el paquete de servidor de Liberty, que ya incluía la aplicación implementada. En esta sección del laboratorio, implementará una aplicación en Liberty utilizando dos técnicas diferentes.

Primero, simplemente copie el módulo WAR de la aplicación en el directorio **"dropins"** de Liberty. Liberty supervisa este directorio. A medida que se añaden unidades implementables (WAR, EAR, JAR) al directorio, Liberty implementa e inicia automáticamente la aplicación en el servidor Liberty. El directorio **dropins** se puede usar para aplicaciones que no requieren configuración adicional, como la asignación de roles de seguridad. Al eliminar las unidades implementables de la carpeta dropins, las aplicaciones se detienen y se eliminan del servidor Liberty en ejecución.

1. En la ventana del terminal, inicie el servidor y use el comando tail -f para ver el archivo messages.log.

    ```
     wlp/bin/server start myServer
     tail -f wlp_usr/servers/myServer/logs/messages.log
    ```

2. **Haga clic derecho** en **Terminal** y seleccione **Nueva ventana** para abrir una segunda ventana de terminal.

    <kbd><img src="./images/media/image134.png" alt="imagen134"></kbd>

3. En la nueva ventana de Terminal, navegue hasta el directorio int:

    ```
     cd ~/Student/ops/int/
    ```

4. Copie la aplicación web en el directorio dropins.

    ```
     cp ~/Student/assets/simpleweb.war wlp_usr/servers/myServer/dropins
    ```

    <kbd><img src="./images/media/image135.png" alt="imagen135"></kbd>

5. Acceda a la ventana de terminal donde se ejecuta el comando tail. Podrá ver mensajes que indican que la aplicación se ha implementado, que la aplicación simpleweb se ha iniciado y que está disponible en **http://rhel9-base.gym..lan:9080/simpleweb/** .

    Tenga en cuenta que Liberty definió la raíz del contexto en función del nombre del archivo WAR como **"/simpleweb"** .

    <kbd><img src="./images/media/image136.png" alt="imagen136"></kbd>

6. Verifique que la aplicación sea accesible abriendo un navegador en: **http://localhost:9080/simpleweb/helloWorld**

    <kbd><img src="./images/media/image137.png" alt="imagen137"></kbd>

7. En la ventana de terminal donde se ejecuta tail, puedes ver que se ha accedido a la aplicación.

    <kbd><img src="./images/media/image138.png" alt="imagen138"></kbd>

8. Regrese a la terminal donde ingresó el comando de copia y elimine la aplicación implementada del directorio dropins usando el siguiente comando:

    ```
     rm wlp_usr/servers/myServer/dropins/simpleweb.war
    ```

9. Regresa a la ventana de terminal donde se ejecuta tail. Puedes ver que la aplicación se ha eliminado.

    <kbd><img src="./images/media/image139.png" alt="imagen139"></kbd>

    Si bien el directorio dropins se puede usar para aplicaciones que no requieren configuración adicional, implementar la aplicación añadiéndola a la configuración del servidor Liberty ofrece la libertad de configurar el servidor Liberty según los requisitos de configuración de la aplicación. Ahora implementará la aplicación simpleweb añadiéndola a la configuración del servidor Liberty.

    El lugar predeterminado para las aplicaciones es: **${server.config.dir}/apps** .

10. Regrese a la ventana de terminal sin ejecutar tail. Copie el archivo WAR de la aplicación en el directorio de aplicaciones con el siguiente comando:

    ```
    cp ~/Student/assets/simpleweb.war wlp_usr/servers/myServer/apps
    ls -lrt wlp_usr/servers/myServer/apps/*.war
    ```

    <kbd><img src="./images/media/image140.png" alt="imagen140"></kbd>

11. Para definir la aplicación en el archivo de configuración de Liberty, eche un vistazo a la configuración de la aplicación que se ha proporcionado como fragmento.

    ```
    cat ~/Student/assets/application-config.xml
    ```

    <kbd><img src="./images/media/image141.png" alt="imagen141"></kbd>

    Como puede ver, se ha definido una raíz de contexto diferente.

12. Agregará el elemento webApplication a la configuración de Liberty mediante el concepto **de inclusión** . Revise el elemento de inclusión y las propiedades definidas en el archivo server.xml.

    ```
    cat wlp_usr/servers/myServer/server.xml | grep include
    ```

    <kbd><img src="./images/media/image142.png" alt="imagen142"></kbd>

13. Copie el archivo application-config.xml en el directorio del servidor.

    ```
    cp ~/Student/assets/application-config.xml wlp_usr/servers/myServer
    ls -lrt wlp_usr/servers/myServer
    ```

    <kbd><img src="./images/media/image143.png" alt="imagen143"></kbd>

14. Regresa a la ventana de terminal que ejecuta tail. Puedes ver que la aplicación **simpleweb** se implementa, esta vez con el contexto raíz **mysimpleweb** .

    <kbd><img src="./images/media/image144.png" alt="imagen144"></kbd>

15. Finalmente prueba la aplicación en el navegador a través de la URL **http://localhost:9080/mysimpleweb/helloWorld** .

    <kbd><img src="./images/media/image145.png" alt="imagen145"></kbd>

**Ha implementado exitosamente la aplicación web en Liberty, primero a través del directorio dropins, y luego agregándola al archivo server.xml a través de include.**

### 6.5.8 Registro y seguimiento de cambios mediante ConfigDropins

Hasta ahora, ha utilizado el concepto **de inclusión** para ampliar el archivo server.xml con archivos de configuración adicionales. Como alternativa, puede especificar archivos de configuración adicionales en el directorio **configDropins** sin especificar elementos de inclusión en el archivo **server.xml** . Si desea agregar archivos de configuración para anular cualquier elemento del archivo **erver.xml** del servidor, cree el directorio **configDropins/overrides** . En este caso, desea agregar o modificar el nivel de registro del servidor de aplicaciones.

1. Desde la segunda ventana de terminal, emita el siguiente comando para crear un directorio configDropins en el directorio del servidor.

    ```
     mkdir -p wlp_usr/servers/myServer/configDropins/overrides
    ```

    <kbd><img src="./images/media/image146.png" alt="imagen146"></kbd>

    **Agregar salida de registro INFO a la consola**

    Liberty proporciona la capacidad de establecer el nivel de registro en cualquiera de los niveles de registro admitidos definidos en la documentación: https://www.ibm.com/docs/en/was-liberty/base?topic=liberty-logging-trace

    - El registro de AUDITORÍA permite registrar “Eventos significativos que afectan el estado o los recursos del servidor”.
    - El registro INFO habilita la "Información general que describe el progreso general de la tarea". De forma predeterminada, el servidor Liberty tiene el nivel de registro de la consola configurado en AUDITORÍA. En esta sección, cambiará el nivel de los mensajes de registro escritos en la consola de AUDITORÍA a INFO, lo que generará mensajes de registro adicionales. Esta actividad no se realizará directamente en el archivo server.xml, sino mediante el concepto configDropins. El objetivo es que pueda cambiar el nivel de registro fácilmente sobre la marcha y volver al nivel anterior sin tener que editar manualmente un archivo.

<table>
    <tbody>
    <tr class="odd">
    <td><kbd><img src="./images/media/info.png" alt="información de inicio de sesión"></kbd></td>
    <td>
    <p>Nota:<br> También es posible configurar las opciones de registro predeterminadas en el archivo bootstrap.properties.<br> Si las opciones de registro se configuran en el archivo bootstrap.properties, las opciones de registro tendrán efecto muy temprano en el inicio del servidor.<br> Por lo tanto, puede ser útil para depurar problemas de inicialización del servidor.     </p>
</td>
    </tr>
    </tbody>
</table>

1. Cambie a la terminal que actualmente está ejecutando la cola en el archivo messages.log y presione CTRL+C para detenerlo.

2. Revise el registro de la consola actual y podrá ver que solo contiene mensajes de tipo AUDIT.

    ```
     tail -f wlp_usr/servers/myServer/logs/console.log
    ```

    <kbd><img src="./images/media/image147.png" alt="imagen147"></kbd>

3. Acceda a la segunda ventana de terminal. Cree un archivo de configuración del servidor para cambiar el nivel de registro de la consola a INFO mediante el siguiente comando:

    ```
     echo '
     <server>
         <logging consoleLogLevel="INFO"> </logging>
     </server>
     ' > wlp_usr/servers/myServer/configDropins/overrides/loglevel-config.xml
    ```

    <kbd><img src="./images/media/image148.png" alt="imagen148"></kbd>

4. Cambie a la ventana de terminal que ejecuta tail para verificar que se haya detectado el nuevo archivo.

    <kbd><img src="./images/media/image149.png" alt="imagen149"></kbd>

    Verificará que los mensajes de nivel de registro **INFO** ahora se registrarán durante la configuración del seguimiento.

    **Actualizar la especificación del seguimiento**

    De forma predeterminada, la especificación de seguimiento de Liberty Server está establecida en **"*=info=enabled"** .

    Para actualizar la especificación de seguimiento, utilizará nuevamente el concepto configDropins.

5. Vaya a la segunda ventana de terminal. Actualice el archivo **configDropins/overrides/loglevel-config.xml** para incluir una especificación de seguimiento mediante el siguiente comando:

    ```
     echo '
     <server>
         <logging consoleLogLevel="INFO" traceSpecification="webcontainer=all=enabled">
         </logging>
     </server>
     ' > wlp_usr/servers/myServer/configDropins/overrides/loglevel-config.xml
    ```

    <kbd><img src="./images/media/image150.png" alt="imagen150"></kbd>

6. Cambie a la ventana de terminal que ejecuta tail para verificar que se haya detectado el nuevo archivo.

    <kbd><img src="./images/media/image151.png" alt="imagen151"></kbd>

    Como puede ver, ahora se muestran mensajes de nivel de registro **INFO,** lo que significa que se ha detectado el cambio de consoleLogLevel.<br> El mensaje indica, como se esperaba, que el nivel de seguimiento se ha establecido en “webcontainer=all”.

7. Cambie a la segunda ventana de terminal para verificar que se haya creado el seguimiento.

    ```
     ls -lrt wlp_usr/servers/myServer/logs
    ```

    <kbd><img src="./images/media/image152.png" alt="imagen152"></kbd>

8. Elimine el archivo para restablecer el nivel de seguimiento al valor predeterminado.

    ```
     rm wlp_usr/servers/myServer/configDropins/overrides/loglevel-config.xml
    ```

9. Cambie a la ventana de terminal que ejecuta tail para verificar que se haya detectado el nuevo archivo.

    <kbd><img src="./images/media/image153.png" alt="imagen153"></kbd>

    Como puede ver, la especificación de seguimiento se ha cambiado nuevamente a **"*=info"** .

10. Presione CTRL+C en la ventana del terminal para detener el comando tail.

11. Detenga la instancia de Liberty usando el siguiente comando:

    ```
    wlp/bin/server stop myServer
    ```

12. Elimine los archivos de seguimiento generados utilizando el siguiente comando:

    ```
    rm wlp_usr/servers/myServer/logs/trace*.log
    ```

    Como has visto, el componente de registro se puede controlar a través de la configuración del servidor y es bastante conveniente habilitar y deshabilitar el seguimiento usando configDropins.

    **Configurar el registro en el archivo bootstrap.properties**

    En ocasiones, podría ser necesario configurar el seguimiento para diagnosticar un problema que ocurre antes de procesar el archivo server.xml. O bien, podría querer cambiar el formato del registro a uno distinto del básico. En este caso, las propiedades de configuración equivalentes se pueden especificar en el archivo **bootstrap.properties** .

    Si se especifica una propiedad de configuración tanto en el archivo bootstrap.properties como en el archivo server.xml, se utiliza el valor de bootstrap.properties hasta que se procese el archivo server.xml. A continuación, se utiliza el valor del archivo server.xml. Evite especificar valores diferentes para la misma propiedad de configuración en ambos archivos.

    Ahora cambiará el formato del registro a JSON. Como el archivo bootstrap.properties no existe, simplemente lo creará.

13. Cree un archivo de propiedades de arranque que defina la propiedad **com.ibm.ws.logging.console.format** ejecutando el siguiente comando:

    ```
    echo 'com.ibm.ws.logging.console.format=json' > wlp_usr/servers/myServer/bootstrap.properties
    cat wlp_usr/servers/myServer/bootstrap.properties
    ```

    <kbd><img src="./images/media/image154.png" alt="imagen154"></kbd>

14. Inicie el servidor a través de **la ejecución del servidor** y podrá ver que el formato de registro se ha establecido en JSON.

    ```
    wlp/bin/server run myServer
    ```

    <kbd><img src="./images/media/image155.png" alt="imagen155"></kbd>

15. En la ventana del terminal, presione **CTRL+C** para detener el servidor.

16. Cambie el formato de registro al predeterminado eliminando bootstrap.properties y luego ejecute el servidor nuevamente.

    ```
    rm wlp_usr/servers/myServer/bootstrap.properties
    wlp/bin/server run myServer
    ```

    <kbd><img src="./images/media/image156.png" alt="imagen156"></kbd>

17. En la terminal, presione **CTRL+C** para detener el servidor.

    Si está interesado en atributos de registro adicionales, consulte: https://www.ibm.com/docs/en/was-liberty/base?topic=liberty-logging-trace

### 6.5.9 Revisar la configuración de Liberty a través de las API REST de Liberty

Si utiliza varias inclusiones o dropins de configuración, podría necesitar revisar la configuración final. Esto se puede hacer mediante las API **de restConnector** .

**Configurar el acceso de administrador a la instancia de Liberty** .

1. En primer lugar, necesitas una contraseña segura, ya que las API proporcionan acceso a datos confidenciales que podrían permitir a un hacker manipular el sistema. Usa **securityUtility** para crear una contraseña segura como **LibertyIsGreat** .

    ```
     wlp/bin/securityUtility encode --encoding=aes LibertyIsGreat
    ```

    <kbd><img src="./images/media/image157.png" alt="imagen157"></kbd>

    Como antes, la contraseña codificada no es única, por lo que el resultado probablemente será diferente al anterior. Sin embargo, ambos son válidos.

2. Utilice los siguientes comandos para configurar restConnector.

    a. Actualice la contraseña del usuario en el siguiente fragmento de código o mantenga la contraseña como está.

    ```
     echo '
     <server>
         <featureManager>
             <feature>restConnector-2.0</feature>
         </featureManager>
     <quickStartSecurity userName="admin" userPassword="{aes}ALCpb79MrIuO8aVUdyXKVDWNssXfX3OmL+xD2J3jWcOgLwrIq1f7/qO8tCR7JwNmcQ==" />
     </server>
     ' > wlp_usr/servers/myServer/configDropins/overrides/rest-config.xml
    ```

    <kbd><img src="./images/media/image158.png" alt="imagen158"></kbd>

    b. Como la función restConnector aún no está instalada, abra una ventana de terminal para instalar las funciones faltantes mediante el comando:

    ```
     wlp/bin/featureUtility installServerFeatures myServer
    ```

    <kbd><img src="./images/media/image159.png" alt="imagen159"></kbd>

3. Inicie la instancia de Liberty usando el comando:

    ```
     wlp/bin/server start myServer
    ```

4. Desde una ventana del navegador, acceda a las API REST de Liberty a través de la URL **https://localhost:9443/ibm/api/config** .<br> Introduzca nombre de usuario/contraseña como: **admin** / **LibertyIsGreat** .

    <kbd><img src="./images/media/image160.png" alt="imagen160"></kbd>

5. Si se te solicita, no guardes la contraseña en el navegador. Tu navegador debería mostrar algo como esto:

    <kbd><img src="./images/media/image161.png" alt="imagen161"></kbd>

6. En la ventana del navegador, presione **Ctrl+F** e introduzca **"webapp"** para buscar "webapp". Debería encontrar la configuración correspondiente.

    <kbd><img src="./images/media/image162.png" alt="imagen162"></kbd>

7. Busque **registro** y obtendrá todos los atributos utilizados actualmente para el registro.

    <kbd><img src="./images/media/image163.png" alt="imagen163"></kbd>

8. Finalmente, detenga el servidor y elimine la configuración de restConnector.

    ```
     wlp/bin/server stop myServer
     rm wlp_usr/servers/myServer/configDropins/overrides/rest-config.xml
    ```

    Para obtener más detalles sobre restConnector para administración, consulte: **https://www.ibm.com/docs/en/was-liberty/base?topic=features-admin-rest-connector-20**

### 6.5.10 Uso del Centro de administración de Liberty

El **Centro de Administración** de Liberty permite supervisar el estado del servidor Liberty. Definirá dos usuarios: un usuario administrativo con el rol **"admin"** y un segundo usuario con el rol " **reader"** . Utilice de nuevo la utilidad de seguridad para crear dos contraseñas seguras.

1. Cree una contraseña como **Liberty4Admins** para el usuario administrador.

    ```
         wlp/bin/securityUtility encode --encoding=xor Liberty4Admins
    ```

    <kbd><img src="./images/media/image164.png" alt="imagen164"></kbd>

2. Crea una contraseña como **Liberty4Readers** para el segundo usuario.

    ```
         wlp/bin/securityUtility encode --encoding=xor Liberty4Readers
    ```

    <kbd><img src="./images/media/image165.png" alt="imagen165"></kbd>

3. Ejecute el siguiente comando para configurar el AdminCenter con los dos usuarios utilizando las contraseñas generadas anteriormente.

    ```
     echo '
     <server>
         <featureManager>
             <feature>adminCenter-1.0</feature>
             <feature>websocket-2.1</feature>
         </featureManager>
         <!-- Configure administrative roles. -->
         <basicRegistry realm="basicRealm">
             <user name="admin" password="{xor}EzY9Oi0rJmseOzI2MSw=" />
             <user name="reader" password="{xor}EzY9Oi0rJmsNOj47Oi0s" />
         </basicRegistry>
         <!-- Assign 'admin' to Administrator -->
         <administrator-role>
             <user>admin</user>
         </administrator-role>
         <reader-role>
             <user>reader</user>
         </reader-role>
     </server>
     ' > wlp_usr/servers/myServer/configDropins/overrides/adminCenter-config.xml
    ```

    <kbd><img src="./images/media/image166.png" alt="imagen166"></kbd>

4. Como la función AdminCenter no está instalada todavía, cambie a una ventana de terminal para instalar la función mediante el comando:

    ```
     wlp/bin/featureUtility installServerFeatures myServer
    ```

    <kbd><img src="./images/media/image167.png" alt="imagen167"></kbd>

5. Inicie el servidor y eche un vistazo al registro:

    ```
     wlp/bin/server start myServer
     tail -f wlp_usr/servers/myServer/logs/messages.log
    ```

    <kbd><img src="./images/media/image168.png" alt="imagen168"></kbd>

    Como puedes ver, se ha habilitado la función AdminCenter **adminCenter-1.0** .

6. Acceda al Centro de administración de Liberty a través de la URL **https://localhost:9443/adminCenter** , luego ingrese las credenciales para el usuario administrador ( **admin** / **Liberty4Admins** ) y presione **Enviar** .

    <kbd></kbd>![imagen169](./images/media/image169.png) Se muestra la caja de herramientas del Centro de administración.

7. Haga clic en **Explorar** para explorar el estado de Liberty, las aplicaciones, así como los datos de monitoreo y la configuración.

    <kbd><img src="./images/media/image170.png" alt="imagen170"></kbd>

8. En la pestaña **Descripción general** eche un vistazo a los servidores y aplicaciones que se están ejecutando.

    <kbd><img src="./images/media/image171.png" alt="imagen171"></kbd>

    Verías más de un servidor si se hubiera definido un colectivo.

9. En la pestaña **Aplicaciones,** puedes ver las aplicaciones en ejecución. Como usuario con permisos de administrador, puedes usar el menú para iniciar, detener o reiniciar una aplicación.

    <kbd><img src="./images/media/image172.png" alt="imagen172"></kbd>

10. En la pestaña **Montor** , puedes ver datos básicos de rendimiento.

    <kbd><img src="./images/media/image173.png" alt="imagen173"></kbd>

    Como puede ver aquí, el valor máximo de memoria de montón usada es superior a 1,9 MB, lo que indica que no se ha definido el montón máximo. Esto se modificará en la siguiente sección del laboratorio.

11. En la pestaña **Configurar** , puedes ver la configuración actual.

    <kbd><img src="./images/media/image174.png" alt="imagen174"></kbd>

    Verá una advertencia que indica que el acceso remoto a archivos no está configurado. Puede ignorarla, ya que no configurará Liberty a través de AdminCenter.<br> Pero puedes hacer clic en el enlace para ver la configuración en la vista de diseño y fuente.

12. Seleccione para cerrar sesión como administrador.

    <kbd><img src="./images/media/image175.png" alt="imagen175"></kbd>

13. Inicie sesión como usuario **lector** con contraseña **Liberty4Readers** .

    <kbd><img src="./images/media/image176.png" alt="imagen176"></kbd>

14. Haz clic en **Explorar** y luego selecciona la pestaña **Aplicaciones** . Intenta hacer clic en el icono junto a la aplicación **simpleweb** y verás que no tienes autorización para iniciar ni detener ninguna aplicación.

    <kbd><img src="./images/media/image177.png" alt="imagen177"></kbd>

15. Seleccione para cerrar sesión como lector.

    <kbd><img src="./images/media/image178.png" alt="imagen178"></kbd>

16. En la ventana del terminal, presione **CRTL+C** para detener el comando tail.

17. Detener el servidor Liberty.

    ```
    wlp/bin/server stop myServer
    ```

### 6.5.11 Personalización de las opciones de Liberty JVM

Como ha visto en el Centro de administración, el valor de Liberty para el montón máximo es bastante alto, lo que indica que aún no se ha definido un límite. Esto se hará en esta sección, definiendo las opciones de Liberty JVM.

Los argumentos genéricos de la JVM se utilizan para configurar y ajustar su ejecución. Liberty viene preconfigurado con una configuración mínima. Los argumentos genéricos personalizados de la JVM, como la configuración del montón para un servidor Liberty, se pueden definir en el archivo **jvm.options** .

1. Cree un archivo **jvm.options** con definiciones para el montón mínimo y máximo ejecutando el siguiente comando:

    ```
     echo '-Xms25m' > wlp_usr/servers/myServer/jvm.options
     echo '-Xmx500m' >> wlp_usr/servers/myServer/jvm.options
     cat wlp_usr/servers/myServer/jvm.options
    ```

    <kbd><img src="./images/media/image179.png" alt="imagen179"></kbd>

2. Inicie el servidor con las opciones JVM actualizadas.

    ```
     wlp/bin/server start myServer
    ```

3. Acceda de nuevo al Centro de Administración de Liberty a través de la URL **https://localhost:9443/adminCenter** . Inicie sesión como usuario reader y con la contraseña Liberty4Readers.

    <kbd><img src="./images/media/image176.png" alt="imagen176"></kbd>

4. Haga clic en **Explorar** y luego seleccione **Monitor** . Observe el panel de control y verá que la memoria máxima del montón usado ahora es de 500 MB, según lo definido en jvm.options.

    <kbd><img src="./images/media/image180.png" alt="imagen180"></kbd>

5. Cerrar sesión en el centro de administración.

6. Detenga el servidor Liberty usando el siguiente comando:

    ```
     wlp/bin/server stop myServer
    ```

    Para obtener información adicional sobre el Centro de administración de Liberty, consulte: **https://www.ibm.com/docs/en/was-liberty/base?topic=center-setting-up-admin**

### 6.5.12 Resumen

Resumamos lo que hiciste en esta parte del laboratorio:

- Instaló un servidor Liberty usando la imagen del kernel de Liberty.
- Se utilizaron variables de entorno de Liberty para separar la configuración de Liberty de los binarios.
- Creé una instancia de servidor Liberty e instalé las funciones faltantes.
- Implementé una aplicación web simple a través de dropins y server.xml.
- Registro configurado a través de server.xml y server.env.
- cambió el tamaño del montón de Liberty a través de jvm.options.
- Usé la API REST para ver la configuración de Liberty.
- Usé Liberty Admin Center para ver datos de monitoreo y administrar aplicaciones de Liberty.

### 7 Limpieza del laboratorio

1. Una vez que haya terminado, asegúrese de que Liberty y Visual Studio Code no estén ejecutándose.

2. Eliminar la carpeta Estudiante mediante el comando:

    ```
     rm -rf ~/Student
    ```

3. Cierre el navegador y todas las ventanas de terminal.

## Resumen

En este laboratorio, aprendió a desarrollar una aplicación simple como desarrollador, a implementar y configurar la aplicación como operador de configuración, y a instalar y configurar Liberty como administrador.

**¡Felicidades!**

**Has completado con éxito el laboratorio "Introducción a Liberty"**

# Solución de problemas

## Asistente de código de Liberty Tools

Si la asistencia de código a través de Liberty Tools no funciona, asegúrese de que la variable de entorno JAVA_HOME se haya establecido en un valor válido.
