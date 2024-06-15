## Inquilinos de WWL: términos de uso

Si se le proporciona un inquilino porque está realizando un curso dirigido por un instructor, tenga en cuenta que ese inquilino está disponible únicamente como apoyo para los laboratorios prácticos del curso. 

Los inquilinos no deben compartirse ni usarse para otros fines que no sean los de los laboratorios prácticos. El inquilino usado en este curso es un inquilino de prueba y no se puede usar ni tener acceso a él después de que la clase haya terminado y no sea apto para la extensión. 

Los inquilinos no se deben convertir a suscripciones de pago. Los inquilinos obtenidos como parte de este curso siguen siendo propiedad de Microsoft Corporation y nos reservamos el derecho de acceso y recuperación en cualquier momento. 

# Ruta de aprendizaje 1 - Laboratorio 1 - Ejercicio 1: Inicialización del inquilino de Microsoft 365 

Adatum Corporation es una subsidiaria de Contoso Electronics. Adatum ejecuta sus aplicaciones heredadas (como Microsoft Exchange Server 2019) en una implementación local. Sin embargo, recientemente se suscribió a Microsoft 365, creando así una implementación híbrida en la que debe sincronizar sus implementaciones locales y en la nube. 

Como administrador de Microsoft 365 de Adatum, se le ha encargado la implementación de Microsoft 365 en la implementación híbrida de Adatum mediante un entorno de laboratorio virtualizado. En este ejercicio, configurará el inquilino de prueba de Microsoft 365 de Adatum. Su instructor(a) le guiará sobre cómo obtener sus credenciales de Microsoft 365 en el entorno hospedado en el laboratorio. Usará estas credenciales en todos los laboratorios restantes de este curso. 

En el entorno de laboratorio, el proveedor de hospedaje de laboratorio ya ha conseguido un inquilino de prueba de Microsoft 365 para usted. El proveedor de laboratorio también ha creado dos cuentas de administrador que usará en el entorno de laboratorio de máquina virtual: 

- Una cuenta de administrador local para el entorno local de Adatum (Adatum\Administrator).
- Una cuenta de administrador de inquilino predeterminada en Microsoft 365 (el nombre para mostrar de esta cuenta de usuario es MOD Administrator). 

Iniciará sesión en el equipo Client 1 (LON-CL1) mediante la cuenta local de Adatum\Administrator. Al acceder a Microsoft 365 por primera vez, iniciará sesión inicialmente con la cuenta de administrador de inquilino de Microsoft 365 (MOD Administrator). A continuación, preparará el inquilino de Microsoft 365 de Adatum para Microsoft Entra ID y para laboratorios posteriores mediante alertas de auditoría y Microsoft Graph PowerShell.


### Tarea 1: Configuración del perfil de organización de Adatum

A lo largo de los laboratorios de este curso, asumirá el rol de Holly Dickson, administradora de Microsoft 365 de Adatum. En su rol como Holly, se le ha encargado configurar el perfil de la empresa para su inquilino de prueba de Microsoft 365. En esta tarea, configurará las opciones necesarias para el inquilino de Adatum. Puesto que Holly todavía tiene que crear una cuenta de usuario personal de Microsoft 365 para ella misma (lo hará en el siguiente ejercicio de laboratorio), Holly iniciará sesión inicialmente en Microsoft 365 con la cuenta de administrador de inquilino de Microsoft 365 predeterminada y la contraseña que ha creado el proveedor de hospedaje de laboratorio. Esta es la cuenta **MOD Administrator**, cuyo alias es "admin". El nombre de usuario de esta cuenta es **admin@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino asignado por el proveedor de hospedaje de laboratorio); el nombre para mostrar de esta cuenta será MOD Administrator.

1. Al abrir el entorno de máquina virtual del proveedor de hospedaje de laboratorio, debe comenzar con la máquina virtual Client 1 (LON-CL1). Si el entorno de máquina virtual se abre con una de las otras máquinas (por ejemplo, LON-DC1), cambie a **LON-CL1** ahora.

2. Inicie sesión en **LON-CL1** con la cuenta de **Administrador** local que ha creado el proveedor de hospedaje de laboratorio con la contraseña **Pa55w.rd**. 

3. En la barra de tareas de la parte inferior de la pantalla, seleccione el icono de **Microsoft Edge**. Si es necesario, maximice la ventana del explorador cuando se abra.

4. En el explorador Edge, vaya a la página **Inicio de Microsoft 365**; para ello, escriba esta dirección URL en la barra de direcciones: **https://portal.office.com** 

5. En el cuadro de diálogo **Iniciar sesión** que aparece, escriba el **nombre de usuario administrativo** proporcionado por el proveedor de hospedaje de laboratorio (esta es la cuenta del administrador de MOD). El nombre de usuario debe tener el formato **admin@xxxxxZZZZZZ.onmicrosoft.com**, donde xxxxxZZZZZZ es el prefijo de inquilino asignado por el proveedor de hospedaje de laboratorio. Seleccione **Siguiente**. <br/>

    **Nota:** En las instrucciones de laboratorio que aparecen en el entorno de laboratorio de la máquina virtual, el proveedor de hospedaje de laboratorio puede proporcionar la capacidad de seleccionar un botón **Escribir texto** (o equivalente) junto a los datos de recursos, como nombres de usuario, contraseñas, comandos de PowerShell y otros datos que se deben escribir a lo largo del curso de estos laboratorios. Otros proveedores de hospedaje de laboratorio pueden proporcionar un método alternativo, como la capacidad de copiar y pegar esta información. Aproveche esta funcionalidad para no tener que escribir manualmente esta información. 

6. En el cuadro de diálogo **Escribir contraseña**, escriba la **Contraseña administrativa** proporcionada por el proveedor de hospedaje del laboratorio y, después, seleccione **Iniciar sesión**. Si fuera necesario, complete el proceso de inicio de sesión de MFA.

7. En el cuadro de diálogo **¿Mantener la sesión iniciada?**, active la casilla **No volver a mostrar esto** y, a continuación, seleccione **Sí**. En el cuadro de diálogo **Guardar contraseña** que aparece, seleccione **Nunca**.

8. Si aparece un cuadro de diálogo **Le damos la bienvenida a Microsoft 365** en medio de la pantalla, tenga en cuenta que no hay ninguna opción para cerrarlo. En su lugar, a la derecha de la ventana, seleccione el icono de flecha hacia delante (**>**) dos veces y, a continuación, seleccione el icono de marca de verificación para avanzar a través de las diapositivas de esta ventana de mensajes. 

9. Si apareciera una ventana **Buscar más aplicaciones** o **Crear con Microsoft 365**, seleccione la **X** de la esquina superior de la ventana para cerrarla. 

10. La página **Le damos la bienvenida a Microsoft 365** aparece en el explorador Edge en la pestaña **Inicio | Microsoft 365**. Esta es la página principal de Microsoft 365 del MOD Administrator. <br/>

    Observe el icono que aparece en la esquina superior derecha de la pantalla. Este icono representa la cuenta **MOD Administrator**, que es la cuenta de administrador de inquilino creada por el proveedor de hospedaje de laboratorio con la que acaba de iniciar sesión. Las otras cuentas de usuario existentes de Microsoft 365 creadas por el proveedor de hospedaje de laboratorio tienen una imagen asociada a cada una de sus cuentas; Por tanto, al iniciar sesión como cualquiera de esos usuarios en laboratorios posteriores, se mostrará la imagen del usuario en lugar de las iniciales del usuario. Sin embargo, cuando un usuario como el MOD Administrator no tiene ninguna imagen asignada, las iniciales del usuario se muestran en lugar de la imagen o, como en este caso, un icono que se ha asignado a la cuenta. <br/>

    En la página **Le damos la bienvenida a Microsoft 365**, en la lista de iconos de aplicación que aparecen en el panel de navegación, seleccione **Administrador**; se abre el **centro de administración de Microsoft 365** en una nueva pestaña del explorador. 

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

16. En la parte superior del panel **Información de la organización**, tenga en cuenta el mensaje que indica que se han guardado los cambios. Seleccione el **X** en la esquina superior del panel para cerrarlo.

17. Permanezca conectado a **LON-CL1** con Microsoft Edge abierto en el **Centro de administración de Microsoft 365** para la siguiente tarea.

### Tarea 2: Creación de un tema personalizado para el equipo del proyecto piloto de Adatum

En la tarea anterior, ha aprendido que cuando alguien ha iniciado sesión en Microsoft 365, el sistema mostrará su fotografía (si se proporciona una) o sus iniciales si no se proporciona ninguna fotografía. Holly Dickson, administradora de Microsoft 365 de Adatum, no está satisfecha con ver una imagen o las iniciales del usuario que ha iniciado sesión. Quiere crear un tema personalizado para los miembros de su equipo de proyecto piloto para que también muestre el nombre del usuario que ha iniciado sesión. Al final del proyecto piloto, si los miembros del equipo del proyecto piloto prefieren este diseño, configurará esta misma opción en el tema predeterminado para que se aplique a todos los usuarios. 

Los temas personalizados deben estar asociados a uno o varios grupos de Microsoft 365. Por tanto, para implementar este cambio, Holly primero debe crear un grupo de Microsoft 365 para los miembros del equipo del proyecto piloto. A continuación, podría crear un tema personalizado asociado a este grupo que permita que la configuración muestre el nombre del usuario que ha iniciado sesión. En esta tarea, creará un grupo de Microsoft 365 para los miembros del equipo piloto de Microsoft 365 de Adatum. Después, creará un tema personalizado que muestre el nombre del usuario que ha iniciado sesión y asignará el equipo del proyecto piloto a este tema. También revisará otras opciones que se pueden configurar con temas personalizados y podrá realizar cualquier cambio de color que desee.

**Importante:** Al final de esta tarea, intentará guardar el tema personalizado que creó. Hay un problema conocido en la plataforma en el Centro de administración de Microsoft 365 en el que a veces guarda el tema personalizado sin problemas y otras veces devuelve un mensaje que dice: "Lo sentimos, no se ha podido guardar el tema". Inténtelo de nuevo más tarde." Si recibe este mensaje, lo único que puede hacer es continuar. Si se intenta guardar el tema más tarde, suele aparecer el mismo error. Este problema no afectará a ningún laboratorio futuro, aparte de que no mostrará el nombre del usuario junto a su icono de usuario o sus iniciales en la línea de encabezado. A pesar de este problema conocido, queremos que realice esta tarea para que adquiera experiencia en la creación de un tema, aunque puede que no se guarde en el inquilino de prueba.

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

14. En el **Centro de administración de Microsoft 365**, seleccione **Configuración** en el panel de navegación y, a continuación, seleccione **Configuración de la organización**. 

15. En la pagina **Configuración de la organización**, la pestaña **Servicios** se mostrará de forma predeterminada. Seleccione la pestaña **Perfil de organización**.

16. La pestaña **Perfil de la organización** muestra la lista de datos del perfil de la organización. En la lista de datos, seleccione **Temas personalizados**.

17. En el panel **Personalizar Microsoft 365 para su organización** que aparece, puede personalizar el tema predeterminado que ven los usuarios al iniciar sesión en Microsoft 365 y puede agregar más temas personalizados. Si quiere crear un nuevo tema personalizado que solo se aplique a los miembros del grupo del **proyecto piloto de M365** que creó anteriormente, seleccione la opción **+Agregar tema**.

18. En el panel **Nuevo tema de grupo que aparece**, la pestaña **General** se muestra de forma predeterminada. Escriba el **tema del proyecto piloto M365** en el campo **Nombre**.

19. Seleccione dentro del campo **Grupos**. En la lista de grupos que aparece, seleccione **proyecto piloto de M365** si aparece en la lista de grupos. <br/>

    **Nota:** Si el **proyecto piloto de M365** no aparece en la lista de grupos, escriba **M365** en el campo **Grupos**. Debería aparecer un cuadro de resultados de la búsqueda que muestre el grupo de **proyecto piloto de M365**. Seleccione **proyecto piloto de M365**. 

20. Active la casilla **Mostrar el nombre para mostrar del usuario**. Esta es la configuración que Holly quiere personalizar para los miembros del equipo del proyecto piloto de M365. Esta opción muestra el nombre del usuario que ha iniciado sesión junto a sus iniciales en cada encabezado de ventana.
 
21. Seleccione la pestaña **Logotipos** y tómese un tiempo para revisar sus opciones. Haga lo mismo para la pestaña **Colores**. Observe las distintas opciones de temas y marcas que puede actualizar. <br/>

    Para este laboratorio, puede cambiar cualquiera de las opciones o dejar los valores predeterminados tal como están. Por ejemplo, en el entorno real, puede agregar el logotipo de su empresa y establecer la imagen de fondo como valor predeterminado para todos los usuarios. En este laboratorio, puede cambiar los colores del panel de navegación, el color del texto, el color de los iconos y el color de énfasis. <br/>

    **Continúe y explore las diferentes opciones de este tema que usarán los miembros del equipo del proyecto piloto de Microsoft 365. Realice los cambios que desee.** <br/>

    **Sugerencia:** Algunos patrones de color distraen estéticamente a los usuarios. Si cambia alguno de los colores, se recomienda que evite usar colores muy contrastados juntos, como los colores neón y los colores de alta resolución, como el rosa fuerte y el blanco.

22. Seleccione **Guardar**. 

    **Nota:** Como se mencionó anteriormente al principio de esta tarea, hay un problema conocido en la plataforma en el Centro de administración de Microsoft 365, donde a veces se guarda un nuevo tema personalizado y otras veces devuelve un mensaje que dice: "Lo sentimos, no se ha podido guardar el tema". Inténtelo de nuevo más tarde." Si recibe este mensaje, no afectará a ningún laboratorio futuro. Como su tema personalizado no se guardó, el sistema simplemente no mostrará el nombre de usuario junto a su icono o sus iniciales en la línea de en (además, no aparecerán los cambios de color que haya realizado). Aún así le pedimos que realice esta tarea aunque reciba este mensaje para que adquiera la experiencia de crear un tema como este. Por lo tanto, si recibe este error, omita el paso siguiente, que prueba el tema personalizado. Sin embargo, aún puede realizar los pasos restantes siguiendo el siguiente paso para obtener información sobre el tema Predeterminado. Tanto si se ha guardado el tema personalizado como si no, cierre el panel de **temas del proyecto piloto de M365**.

23. Si el tema personalizado no se guardó, vaya al paso siguiente. Sin embargo, si se guardó el tema personalizado, seleccione el icono **Actualizar** situado en la parte superior de la pantalla, a la izquierda de la barra de direcciones. Una vez que se actualice la pantalla, observe cómo el **nombre del administrador de MOD** aparece a la izquierda del círculo con las iniciales de MA o del icono seleccionado para esta cuenta por el proveedor de hospedaje de laboratorio. Cuando los miembros del equipo del proyecto piloto de Microsoft 365 inician sesión en Microsoft 365, este tema personalizado mostrará su nombre de usuario, tal como aparece aquí el nombre del administrador de MOD. 

24. En la lista de datos de perfil de la organización, seleccione **Temas personalizados**.

25. En el panel **Personalizar Microsoft 365 para su organización** que aparece, observe cómo se muestra el **tema Predeterminado** y el **tema del proyecto piloto de M365** (si el tema se guardó en el paso anterior). Seleccione el **Tema predeterminado**. 

26. En el panel **Tema predeterminado**, observe cómo la opción **Mostrar el nombre para mostrar del usuario** no está seleccionada para el tema predeterminado. Si Holly más adelante decide convertir la opción **Mostrar el nombre para mostrar del usuario** en una característica permanente, seleccionará esta opción en el panel **Tema predeterminado** para que se aplique a todos los usuarios de Adatum y eliminará el **tema del proyecto piloto de M365**. <br/>

    **Nota:** Si recibió el mensaje de error "Lo sentimos, no se ha podido guardar el tema" Inténtelo de nuevo más tarde." cuando intentó guardar el tema personalizado, seleccione esta opción **Mostrar el nombre para mostrar del usuario** en el tema Predeterminado y, a continuación, seleccione **Guardar**. Queremos que vea lo que ocurre cuando se selecciona esta opción, aunque no haya podido guardar su tema personalizado. Si establece esta opción en el tema Predeterminado, seleccione el icono **Actualizar** situado en la parte superior de la pantalla, a la izquierda de la barra de direcciones. Una vez que se actualice la pantalla, observe cómo el **nombre del administrador de MOD** aparece a la izquierda del círculo con las iniciales de MA o del icono seleccionado para esta cuenta por el proveedor de hospedaje de laboratorio.
 
27. Cierre el panel **Tema predeterminado**.

28. Permanezca conectado a **LON-CL1** con Microsoft Edge abierto en el **Centro de administración de Microsoft 365** para la siguiente tarea.

### Tarea 3: Instalación de PowerShell de Microsoft Graph 

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
