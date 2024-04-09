## Inquilinos de WWL: términos de uso

Si se le proporciona un inquilino porque está realizando un curso dirigido por un instructor, tenga en cuenta que ese inquilino está disponible únicamente como apoyo para los laboratorios prácticos del curso. 

Los inquilinos no deben compartirse ni usarse para otros fines que no sean los de los laboratorios prácticos. El inquilino usado en este curso es un inquilino de prueba y no se puede usar ni tener acceso a él después de que la clase haya terminado y no sea apto para la extensión. 

Los inquilinos no se deben convertir a suscripciones de pago. Los inquilinos obtenidos como parte de este curso siguen siendo propiedad de Microsoft Corporation y nos reservamos el derecho de acceso y recuperación en cualquier momento. 

# Ruta de aprendizaje 1 - Laboratorio 1 - Ejercicio 1: Inicialización del inquilino de Microsoft 365 

Adatum Corporation es una subsidiaria de Contoso Electronics. Adatum ejecuta sus aplicaciones heredadas (como Microsoft Exchange Server 2019) en una implementación local. Como nueva administradora de Microsoft 365 de Adatum, se le ha encargado a Holly Dickson preparar la implementación de Microsoft 365 de Adatum para Copilot para Microsoft 365. 

En este ejercicio, configurará el inquilino de prueba de Microsoft 365 de Adatum. Su instructor(a) le guiará sobre cómo obtener sus credenciales de Microsoft 365 en el entorno hospedado en el laboratorio. Usará estas credenciales en todos los laboratorios restantes de este curso. 

En el entorno de laboratorio, el proveedor de hospedaje de laboratorio ya ha conseguido un inquilino de prueba de Microsoft 365 para usted. El proveedor de laboratorio también ha creado dos cuentas de administrador que usará en el entorno de laboratorio de máquina virtual: 

- Una cuenta de administrador local para el entorno local de Adatum (Adatum\Administrator).
- Una cuenta de administrador de inquilino predeterminada en Microsoft 365 (el nombre para mostrar de esta cuenta de usuario es MOD Administrator). 

Iniciará sesión en el equipo Client 1 (LON-CL1) mediante la cuenta local de Adatum\Administrator. Al acceder a Microsoft 365 por primera vez, iniciará sesión inicialmente con la cuenta de administrador de inquilino de Microsoft 365 (MOD Administrator). A continuación, preparará el inquilino de Microsoft 365 de Adatum para Microsoft Entra ID y para laboratorios posteriores mediante alertas de auditoría y Microsoft Graph PowerShell.


### Tarea 1: Obtener sus credenciales de Microsoft 365

Una vez que inicie el laboratorio, podrá acceder al inquilino de prueba gratuito de Microsoft 365 proporcionado por el proveedor de hospedaje de laboratorio en el entorno de Microsoft Virtual Lab. Dentro de este inquilino, el proveedor de hospedaje de laboratorio ha creado una cuenta de usuario de Microsoft 365 para un administrador de inquilino predeterminado denominado MOD Administrator. El proveedor de hospedaje de laboratorio ha asignado a esta cuenta de usuario un nombre de usuario y una contraseña únicos, y a la cuenta se le ha asignado el rol Administrador global de Microsoft 365. Debe recuperar este nombre de usuario y contraseña para que pueda iniciar sesión en Microsoft 365 en el entorno de Microsoft Virtual Lab. También se le asignará un nombre de inquilino y un prefijo de inquilino. También usará esta información en varias tareas de los laboratorios de este curso.

Dado que los asociados de aprendizaje pueden ofrecer este curso con el uso de una variedad de proveedores de hospedaje del laboratorio autorizados, los pasos reales necesarios para recuperar el nombre de UPN y el identificador de inquilino asociados con el inquilino pueden variar según el proveedor de hospedaje de laboratorio. Por lo tanto, tu instructor te dará las instrucciones necesarias sobre cómo recuperar esta información para tu curso. <br/>

Debe anotar la siguiente información (proporcionada por el instructor) para su uso posterior:

- **Prefijo de inquilino.** Este prefijo de inquilino es para las cuentas de usuario de Microsoft 365 que usará para iniciar sesión en Microsoft 365 en todos los laboratorios de este curso. El dominio de cada cuenta de usuario de Microsoft 365 tiene el formato de {alias de usuario}@xxxxxZZZZZZ.onmicrosoft.com, donde xxxxxZZZZZZ es el prefijo de inquilino. Consta de dos partes: el prefijo del host de laboratorio (xxxxx; algunos host usan un prefijo genérico como M365x, mientras que otros usan sus iniciales de empresa o alguna otra designación) y el identificador de inquilino (ZZZZZZ; por lo general, un número de 6 dígitos). Registre este valor de prefijo de inquilino xxxxxZZZZ para su uso posterior. Cuando cualquiera de los pasos del laboratorio le dirija a iniciar sesión en Microsoft 365 como una de las cuentas de usuario (como MOD Administrator), debe escribir el valor xxxxxZZZZZZ que obtuvo aquí como la parte del prefijo de inquilino del dominio .onmicrosoft.com.

- **Contraseña de inquilino.** Esta es la contraseña proporcionada por el proveedor de hospedaje de laboratorio para la cuenta de administrador de inquilino. **Nota:** Usará esta contraseña no solo para la cuenta de administrador de inquilino, sino para cada una de las cuentas de usuario predefinidas que se usan en todos los laboratorios.

- **Nombre de dominio personalizado.** El proveedor de hospedaje de laboratorio ha creado un nombre de dominio personalizado para Adatum. Usará este dominio al agregar un dominio personalizado a Microsoft 365 en un ejercicio de laboratorio posterior. El nombre de dominio tiene el formato **xxxUPNxxx.xxxCustomDomainxxx.xxx.** Debe reemplazar **xxxUPNxxx** por el número de UPN proporcionado por el proveedor de hospedaje de laboratorio y debe reemplazar **xxxCustomDomainxxx.xxx** por el nombre de dominio del proveedor de hospedaje de laboratorio. Por ejemplo, supongamos que el proveedor de hospedaje de laboratorio es Fabrikam Inc. Si el número de UPN que asigna al inquilino es AMPVU3a y su nombre de dominio personalizado es fabrikam.us, el nombre de dominio del nuevo dominio personalizado sería AMPVU3a.fabrikam.us. El instructor le proporcionará el número de UPN del proveedor de hospedaje de laboratorio y el nombre de dominio personalizado.  


### Tarea 2: Configurar el perfil de organización de Adatum

A lo largo de los laboratorios de este curso, asumirá el rol de Holly Dickson, administradora de Microsoft 365 de Adatum. En su rol como Holly, se le ha encargado configurar el perfil de la empresa para su inquilino de prueba de Microsoft 365. En esta tarea, configurará las opciones necesarias para el inquilino de Adatum. Puesto que Holly todavía tiene que crear una cuenta de usuario personal de Microsoft 365 para ella misma (lo hará en el siguiente ejercicio de laboratorio), Holly iniciará sesión inicialmente en Microsoft 365 con la cuenta de administrador de inquilino de Microsoft 365 predeterminada y la contraseña que ha creado el proveedor de hospedaje de laboratorio. Esta es la cuenta **MOD Administrator**, cuyo alias es "admin". El nombre de usuario de esta cuenta es **admin@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino asignado por el proveedor de hospedaje de laboratorio); el nombre para mostrar de esta cuenta será MOD Administrator.

1. Al abrir el entorno de máquina virtual del proveedor de hospedaje de laboratorio, debe comenzar con la máquina virtual Client 1 (LON-CL1). Si el entorno de máquina virtual se abre con una de las otras máquinas (por ejemplo, LON-DC1), cambie a **LON-CL1** ahora.

2. Inicie sesión en **LON-CL1** con la cuenta de **Administrador** local que ha creado el proveedor de hospedaje de laboratorio con la contraseña **Pa55w.rd**. 

3. En la barra de tareas de la parte inferior de la pantalla, seleccione el icono de **Microsoft Edge**. Si es necesario, maximice la ventana del explorador cuando se abra.

4. En el explorador Edge, vaya a la página **Inicio de Microsoft 365**; para ello, escriba esta dirección URL en la barra de direcciones: **https://portal.office.com** 

5. En el cuadro de diálogo **Iniciar sesión** que aparece, escriba el **nombre de usuario del inquilino de Microsoft 365** proporcionado por el proveedor de hospedaje de laboratorio (esta es la cuenta MOD Administrator). El nombre de usuario debe tener el formato **admin@xxxxxZZZZZZ.onmicrosoft.com**, donde xxxxxZZZZZZ es el prefijo de inquilino asignado por el proveedor de hospedaje de laboratorio. Seleccione **Siguiente**. <br/>

    **Nota:** El hospedaje de laboratorio puede proporcionar la capacidad de seleccionar un botón **Escribir texto** (o equivalente) junto a los datos de recursos, como nombres de usuario, contraseñas, comandos de PowerShell y otros datos que se deben escribir en todo el curso de estos laboratorios. Otros proveedores de hospedaje de laboratorio pueden proporcionar un método alternativo, como la capacidad de copiar y pegar esta información. Aproveche esta funcionalidad para no tener que escribir manualmente esta información. 

6. En el cuadro de diálogo **Escribir contraseña**, escriba la **contraseña de inquilino única de Microsoft 365** proporcionada por el proveedor de hospedaje de laboratorio y, a continuación, seleccione **Iniciar sesión**.

7. En el cuadro de diálogo **¿Mantener la sesión iniciada?**, active la casilla **No volver a mostrar esto** y, a continuación, seleccione **Sí**. En el cuadro de diálogo **Guardar contraseña** que aparece, seleccione **Nunca**.

8. Si aparece un cuadro de diálogo **Le damos la bienvenida a Microsoft 365** en medio de la pantalla, tenga en cuenta que no hay ninguna opción para cerrarlo. En su lugar, a la derecha de la ventana, seleccione el icono de flecha hacia delante (**>**) dos veces y, a continuación, seleccione el icono de marca de verificación para avanzar a través de las diapositivas de esta ventana de mensajes. 

9. Si aparece una ventana **Buscar más aplicaciones** o una ventana **Crear con Microsoft 365**, seleccione la **X** en la esquina superior derecha de las ventanas para cerrarlas. 

10. La página **Le damos la bienvenida a Microsoft 365** aparece en el explorador Edge en la pestaña **Inicio | Microsoft 365**. Esta es la página principal de Microsoft 365 del MOD Administrator. <br/>

    Observe el icono que aparece en la esquina superior derecha de la pantalla. Este icono representa la cuenta **MOD Administrator**, que es la cuenta de administrador de inquilino creada por el proveedor de hospedaje de laboratorio con la que acaba de iniciar sesión. Las otras cuentas de usuario existentes de Microsoft 365 creadas por el proveedor de hospedaje de laboratorio tienen una imagen asociada a cada una de sus cuentas; Por tanto, al iniciar sesión como cualquiera de esos usuarios en laboratorios posteriores, se mostrará la imagen del usuario en lugar de las iniciales del usuario. Sin embargo, cuando un usuario como el MOD Administrator no tiene ninguna imagen asignada, las iniciales del usuario se muestran en lugar de la imagen o, como en este caso, un icono que se ha asignado a la cuenta. <br/>

    En la página **Le damos la bienvenida a Microsoft 365**, en la lista de iconos de aplicación que aparecen en el panel izquierdo, seleccione **Administrador**; se abrirá el **Centro** de administración de Microsoft 365 en una nueva pestaña del explorador. 

11. En el **Centro de administración de Microsoft 365**, seleccione **Mostrar todo** en el panel de navegación y, a continuación, seleccione **Configuración**. En el grupo **Configuración**, seleccione**Configuración de la organización**. 

12. En la pagina **Configuración de la organización**, la pestaña **Servicios** se mostrará de forma predeterminada. Seleccione la pestaña **Perfil de organización**.

13. En la pestaña **Perfil de organización**, seleccione **Información de la organización** en la lista de datos de perfil.

14. En el panel **Información de la organización** que aparece, escriba la siguiente información: <br/>

    - Nombre: **Adatum Corporation** (Nota: Adatum Corporation es una subsidiaria de Contoso Inc. Es posible que el inquilino de prueba de Microsoft que el proveedor de hospedaje de laboratorio haya obtenido para este laboratorio se haya asignado originalmente a Contoso. Si **Contoso** (o cualquier otro valor) aparece como el nombre de la organización, cámbielo a **Adatum Corporation**.

    - Dirección postal: **555 Main Street**

    - Ciudad: **Redmond**

    - Estado o provincia: **Washington**

    - Código postal: **98052**

    - Teléfono: no cambiar

    - Contacto técnico: no cambiar

    - Lenguaje preferido: **Inglés**

15. Seleccione **Guardar**.

16. En la parte superior del panel **Información de la organización**, tenga en cuenta el mensaje que indica que se han guardado los cambios. Seleccione la **X** en la esquina superior derecha para cerrar el panel.

17. Permanezca conectado a **LON-CL1** con Microsoft Edge abierto en el **Centro de administración de Microsoft 365** para la siguiente tarea.

### Tarea 3: Crear un tema personalizado para el equipo del proyecto piloto de Adatum

En la tarea anterior, ha aprendido que cuando alguien ha iniciado sesión en Microsoft 365, el sistema mostrará su fotografía (si se proporciona una) o sus iniciales si no se proporciona ninguna fotografía. Holly Dickson, administradora de Microsoft 365 de Adatum, no está satisfecha con ver una imagen o las iniciales del usuario que ha iniciado sesión. Quiere crear un tema personalizado para los miembros de su equipo de proyecto piloto para que también muestre el nombre del usuario que ha iniciado sesión. Al final del proyecto piloto, si los miembros del equipo del proyecto piloto prefieren este diseño, configurará esta misma opción en el tema predeterminado para que se aplique a todos los usuarios. 

Los temas personalizados deben estar asociados a uno o varios grupos de Microsoft 365. Por tanto, para implementar este cambio, Holly primero debe crear un grupo de Microsoft 365 para los miembros del equipo del proyecto piloto. A continuación, podría crear un tema personalizado asociado a este grupo que permita que la configuración muestre el nombre del usuario que ha iniciado sesión. En esta tarea, creará un grupo de Microsoft 365 para los miembros del equipo piloto de Microsoft 365 de Adatum. Después, creará un tema personalizado que muestre el nombre del usuario que ha iniciado sesión y asignará el equipo del proyecto piloto a este tema. También revisará otras opciones que se pueden configurar con temas personalizados y podrá realizar cualquier cambio de color que desee.

**Nota:** El registro de equipo que cree para el equipo de proyectos piloto de Microsoft 365 también se usará en un ejercicio de laboratorio posterior en el que se crea una directiva de acceso condicional para habilitar la autenticación multifactor. Habilitará MFA para todos los usuarios, excepto para los miembros del equipo de proyecto piloto.

1. Todavía debe iniciar sesión en LON-CL1 como la cuenta local **adatum\administrator** y, en el explorador Edge, todavía debe iniciar sesión en Microsoft 365 como **MOD Administrator**. 

2. En el **Centro de administración de Microsoft 365**, seleccione **Equipos y grupos** en el panel de navegación y, después, en él, seleccione **Equipos y grupos activos**. 

3. En la página **Equipos y grupos activos**, hay una pestaña para ver cada uno de los tipos de grupo. La pestaña **Grupos de Teams y Microsoft 365** se muestra de forma predeterminada. En esta pestaña, se muestran los grupos de Microsoft 365 existentes.  <br/>

    Seleccione la opción **+Agregar un grupo de Microsoft 365** que aparece en la barra de menús situada encima de la lista de grupos de Microsoft 365 y Teams. Esto inicia el asistente para **Agregar un grupo de Microsoft 365**. 

4. En el asistente para **Agregar un grupo de Microsoft 365**, en la página **Configurar la información básica**, escriba **proyecto piloto de M365** en el campo **Nombre** y, después, escriba **Miembros del equipo del proyecto piloto de Microsoft 365** en el campo **Descripción** (Nota: Aunque no escriba una descripción, todavía debe seleccionar en este campo para habilitar el botón **Siguiente**). Seleccione **Siguiente**.

5. Ahora asignará al MOD Administrator como propietario del grupo de **proyecto piloto de M365**. En la ventana **Asignar propietarios**, seleccione **+Asignar propietarios **.
    
6. En el panel **Asignar propietarios** que aparece, active la casilla situada junto a **MOD Administrator** y, a continuación, seleccione el botón **Agregar (1)** situado en la parte inferior del panel.

7. En la página **Asignar propietarios**, el MOD Administrator debe aparecer como propietario del grupo. Seleccione **Siguiente**.

8. Ahora asignará miembros al grupo de proyecto piloto de M365. En la página **Agregar miembros**, seleccione **+Agregar miembros**.

9. En el panel **Agregar miembros** que aparece, active las casillas situadas junto a los siguientes usuarios (en orden alfabético): **Alex Wilber**, **Allan Deyoung**, **Diego Siciliani**, **Isaiah Langer**, **Joni Sherman**, **Lynne Robbins**, **Megan Bowen**, **MOD Administrator**, **Nestor Wilke** y **Patti Fernandez**. A continuación, seleccione el botón **Agregar (10)** en la parte inferior del panel.

10. En la página **Agregar miembros**, compruebe que estos 10 usuarios aparezcan como miembros del grupo. Si le ha faltado algún usuario, seleccione **+Agregar miembros** y agregue cualquiera de los 10 usuarios que no haya agregado. Cuando aparezcan los 10 usuarios en esta página, seleccione **Siguiente**.

11. En la página **Editar configuración**, escriba la siguiente información: <br/>

    - Escriba **m365pilotproject** en el campo **Dirección de correo electrónico del grupo**.
    - En el campo **Privacidad**, seleccione **Privado**.
    - En la sección **Agregar Microsoft Teams al grupo**, compruebe que la casilla **Crear un equipo para este grupo** esté activada (selecciónela si está en blanco) y, a continuación, seleccione **Siguiente**.

12. En la página **Revisar y terminar de agregar grupo**, revise el contenido que ha escrito. Si es necesario corregir algo, seleccione **Editar** en el área específica que necesita ajuste, realice las correcciones necesarias y, después seleccione **Siguiente** para volver a esta página. Cuando vea que todo es correcto, seleccione **Crear grupo**.

13. Una vez que aparezca la ventana **grupo de proyecto piloto de M365 creado**, observe el comentario en la parte superior de la página, que puede tardar 5 minutos en aparecer en la lista de Grupos activos.  </br>

    Seleccione **Close** (Cerrar). Esto le regresa a la página **Equipos y grupos activos**, que debe mostrar la pestaña **Grupos de Teams y Microsoft 365**. Dado que el grupo de proyecto piloto de M365 era un grupo de Microsoft 365, debería mostrarse en esta pestaña en algún momento. Si es necesario, seleccione la opción **Actualizar** en la barra de menús hasta que vea el grupo de proyecto piloto de M365 en la lista de grupos de Teams y Microsoft 365.

14. En el **Centro de administración de Microsoft 365**, en el grupo **Configuración** del panel de navegación, seleccione **Configuración de la organización**. 

15. En la página **Configuración de la organización**, seleccione la pestaña **Perfil de organización**.

16. En la lista de datos de perfil de la organización, seleccione **Temas personalizados**.

17. En el panel **Personalizar Microsoft 365 para su organización** que aparece, puede personalizar el tema predeterminado que ven los usuarios al iniciar sesión en Microsoft 365 y puede agregar más temas personalizados. Seleccione la opción **+Agregar tema**.

18. En el panel **Nuevo tema de grupo que aparece**, la pestaña **General** se muestra de forma predeterminada. Escriba el **tema del proyecto piloto M365** en el campo **Nombre**.

19. Seleccione dentro del campo **Grupos**. En la lista de grupos que aparece, seleccione **proyecto piloto de M365** si aparece en la lista de grupos. <br/>

    **Nota:** Si el **proyecto piloto de M365** no aparece en la lista de grupos, escriba **M365** en el campo **Grupos**. Debería aparecer un cuadro de resultados de la búsqueda que muestre el grupo de **proyecto piloto de M365**. Seleccione **proyecto piloto de M365**. 

20. Active la casilla **Mostrar el nombre para mostrar del usuario**. Esta es la configuración que Holly quiere personalizar para los miembros del equipo del proyecto piloto de M365. Esta opción muestra el nombre de los usuarios junto a sus iniciales en cada encabezado de ventana.
 
21. Seleccione **Guardar**. Cierre el **panel de temas del proyecto piloto de M365** una vez guardados los cambios. 

22. Seleccione el icono **Actualizar** situado en la parte superior de la pantalla, a la izquierda de la barra de direcciones. Una vez que se actualice la pantalla, observe cómo aparece el nombre **MOD Administrator** a la izquierda del círculo con el icono de megáfono. Cuando los miembros del equipo del proyecto piloto de Microsoft 365 inician sesión en Microsoft 365, su nombre de usuario aparece ahora a la izquierda de su imagen de perfil (o, en este caso, un icono de un megáfono) o sus iniciales debido al tema personalizado que acaba de crear.

23. En la lista de datos de perfil de la organización, seleccione **Temas personalizados**.

24. En el panel **Personalizar Microsoft 365 para su organización** que aparece, observe cómo se muestra el **tema Predeterminado** y el **tema del proyecto piloto de M365**. Seleccione el **Tema predeterminado**. 

25. En el panel **Tema predeterminado**, observe cómo la opción **Mostrar el nombre para mostrar del usuario** no está seleccionada para el tema predeterminado. Si Holly más adelante decide convertir la opción **Mostrar el nombre para mostrar del usuario** en una característica permanente, seleccionará esta opción en el panel **Tema predeterminado** para que se aplique a todos los usuarios de Adatum y eliminará el **tema del proyecto piloto de M365**. <br/>

    Cierre el panel **Tema personalizado**.

26. Permanezca conectado a **LON-CL1** con Microsoft Edge abierto en el **Centro de administración de Microsoft 365** para la siguiente tarea.

### Tarea 4: Instalar Microsoft Graph PowerShell 

Microsoft Graph PowerShell es necesario para realizar varias tareas de configuración al instalar Microsoft 365. Dado que los ejercicios de laboratorio futuros realizarán varias de estas tareas con Windows PowerShell, debe comenzar instalando el módulo de PowerShell de Microsoft Graph. Este módulo le permite realizar muchas de las tareas de administración de usuarios y organizaciones de Microsoft 365 a través de PowerShell. Es excelente para tareas masivas, como restablecimientos de contraseña, directivas de contraseña, administración de licencias e informes, etc.  

1. En LON-CL1, todavía debería tener la sesión iniciada con la cuenta local **adatum\administrator**. Para instalar Microsoft Graph PowerShell, debe abrir una instancia con privilegios elevados de **Windows PowerShell**. Escriba **power** en el cuadro Buscar que aparece en la esquina inferior izquierda de la barra de tareas. En la lista de resultados de la búsqueda, haga clic con el botón derecho en **Windows PowerShell** (no seleccione Windows PowerShell ISE) y seleccione **Ejecutar como administrador** en el menú desplegable que aparece. 

2. Maximice la ventana de PowerShell. En **Windows PowerShell**, escriba el siguiente comando en el símbolo del sistema para instalar el módulo de PowerShell de Microsoft Graph desde la Galería de PowerShell y presione Entrar: <br/>

        Install-Module Microsoft.Graph -Scope CurrentUser

3. Se le pedirá que confirme si desea instalar el módulo desde un repositorio que no es de confianza (PSGallery). Escriba **A** para seleccionar **[A] Sí a todo** y presione Entrar.  <br/>

    **Nota:** La respuesta iniciará la instalación de todos los submódulos de Microsoft Graph. Una vez que todos los mensajes de instalación de cada submódulo hayan terminado de mostrarse, seguirá tardando aproximadamente entre 5 y 10 minutos adicionales en completar la instalación de PowerShell de Microsoft Graph. Durante este tiempo, el cursor seguirá parpadeando debajo del mensaje del repositorio que no es de confianza. <br/>

    **Esto puede ser un buen momento para tomar un breve descanso.**

4. Aparecerá un símbolo del sistema una vez instalado Microsoft Graph PowerShell. Ahora se mostrará la lista de submódulos que se han instalado. Para ello, ejecute el comando siguiente:

        Get-InstalledModule Microsoft.Graph.* | select *name*

5. Compruebe que la lista de submódulos instalados incluya estos tres submódulos, que se usarán en ejercicios de laboratorio posteriores: 

    - Microsoft.Graph.Groups
    - Microsoft.Graph.Identity.DirectoryManagement
    - Microsoft.Graph.Users
    
    Si los tres submódulos aparecen en la lista de submódulos instalados, continúe con el paso siguiente. Sin embargo, si alguno de estos tres submódulos no aparece en la lista, ejecute el siguiente comando de PowerShell para instalar manualmente el submódulo que falta:

        Install-Module -Name <module name> -Scope CurrentUser

    Por ejemplo, si el módulo Microsoft.Graph.Identity.DirectoryManagement no se ha instalado, ejecutaría el siguiente comando:

        Install-Module -Name Microsoft.Graph.Identity.DirectoryManagement

6. La configuración de la directiva de ejecución de PowerShell determina qué scripts de PowerShell se pueden ejecutar en un sistema Windows. Establecer esta directiva en **Unrestricted** permite a Holly cargar todos los archivos de configuración y ejecutar todos los scripts. En el símbolo del sistema, escriba el siguiente comando y presione ENTRAR:   <br/>

        Set-ExecutionPolicy unrestricted

    ‎Si se le pide que compruebe que desea cambiar la directiva de ejecución, escriba **A** para seleccionar **[A] Sí a todo.** 

7. Deje abierta la ventana de PowerShell, pero minimícela. La usará en un ejercicio de laboratorio posterior.


**Enhorabuena. Ha completado todos los pasos para inicializar el inquilino del laboratorio. Ya está listo para realizar los ejercicios de laboratorio restantes.**

# Fin del Laboratorio 1
