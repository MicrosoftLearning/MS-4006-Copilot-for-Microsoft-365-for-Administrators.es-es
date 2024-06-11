# Ruta de aprendizaje 2: laboratorio 2: ejercicio 2: administración de roles y grupos de roles

En este ejercicio, continuará en su rol como Holly Dickson, nueva administradora de Microsoft 365 de Adatum. Como parte del proyecto piloto de Microsoft 365 de Adatum, administrará la delegación de la administración asignando roles de administrador de Microsoft 365 a varias de las cuentas de usuario de Microsoft 365 creadas por el proveedor de hospedaje del laboratorio. Este ejercicio le proporcionará experiencia en el uso de tres métodos diferentes para asignar estos roles: 1) mediante la asignación de un rol directamente a una cuenta de usuario en el Centro de administración de Microsoft 365, 2) mediante la creación de un grupo de roles, la asignación de roles al grupo de roles y, a continuación, la asignación del grupo de roles a un usuario en el Centro de administración de Microsoft 365 y 3) mediante la asignación de un rol a un usuario con Windows PowerShell. Una vez que haya asignado roles de administrador de Microsoft 365 a varias de las cuentas de usuario existentes, deberá probar esas asignaciones comprobando que los usuarios tienen los permisos para actuar de acuerdo con sus roles. 


### ‎Tarea 1: asignación de un rol Administrador en el Centro de administración de Microsoft 365

A Holly Dickson se le ha asignado el rol Administrador global de Microsoft 365. A medida que continúe en su rol como Holly, usará el Centro de administración de Microsoft 365 para asignar derechos de administrador a uno de los usuarios de Adatum. En esta tarea, asignará el rol Administrador de facturación a la cuenta de usuario de Diego Siciliani.

1. Ha finalizado el ejercicio de laboratorio anterior trabajando en LON-DC1. Ahora debería volver a **LON-CL1** para realizar las tareas administrativas de Microsoft 365 en este ejercicio de laboratorio. Como procedimiento recomendado, las tareas administrativas típicas de Microsoft 365 deben realizarse en un equipo cliente en lugar del controlador de dominio de la empresa.  <br/>

    Cambie a **LON-CL1**. 

2. En **LON-CL1**, en el **Centro de administración de Microsoft 365** en el explorador Edge, debe iniciar sesión como Holly Dickson desde un ejercicio de laboratorio anterior. En el panel de navegación izquierdo, seleccione **Usuarios** y, a continuación, seleccione **Usuarios activos**. 

3. En la lista **Usuarios activos**, seleccione **Diego Siciliani**.  <br/>

    **Nota:** Seleccione El nombre de Diego; no active la casilla situada a la izquierda de su nombre. La casilla se usa normalmente para seleccionar varios usuarios cuando desea realizar una de las acciones relacionadas con el usuario en la barra de menús que aparece encima de la lista de usuarios, como **Administrar licencias de productos** y **Administrar roles**. Al seleccionar un nombre de usuario, se abre un panel de propiedades específico para ese usuario.

4. En el panel de **Diego Siciliani** que aparecerá, la pestaña **Cuenta** se mostrará de forma predeterminada. En esta pestaña, desplácese hacia abajo hasta la sección **Roles** y seleccione **Administrar roles**. 

5. En la ventana **Administración de roles de administrador**, la opción **Usuario (sin acceso al Centro de administración)** está seleccionada de forma predeterminada. Ahora que quiere asignar a Diego un rol Administrador, seleccione la opción **Acceso al Centro de administración**. Esto habilita una lista de roles de administrador usados habitualmente para la selección. 

6. Diego ha sido ascendido a Administrador de facturación, pero como este rol no aparece en la lista de roles más usados, desplácese hacia abajo y seleccione **Mostrar todo por categoría**. 

7. En la lista de roles ordenados por categoría, desplácese hacia abajo hasta la categoría **Otros**, active la casilla **Administrador de facturación** y, a continuación, seleccione **Guardar cambios**. <br/>

    **Sugerencia:** Tenga en cuenta el mensaje que aparece en la parte superior del panel una vez guardado el cambio del rol de administrador. Este mensaje proporciona el siguiente procedimiento recomendado que debe tener en cuenta a medida que mantiene roles administrativos en las implementaciones del mundo real: **Proporcione a los usuarios solo el acceso que necesitan asignándoles el rol menos permisivo.**

8. En la ventana **Administrar roles de administrador**, seleccione la **X** en la esquina superior derecha de la pantalla para cerrarla. Esto le devuelve a la lista **Usuarios activos**. 

9. Permanezca conectado a LON-CL1 y al Centro de administración de Microsoft 365 como Holly Dickson.

### ‎Tarea 2: asignación de un rol Administrador mediante un grupo de roles en el Centro de administración de Microsoft 365

En la tarea anterior, asignó un rol Administrador directamente a la cuenta de usuario de Diego Siciliani en el Centro de administración de Microsoft 365. En esta tarea, asignará roles mediante un grupo de roles en su lugar. Creará un grupo de roles de seguridad, le asignará roles de administración de usuarios y, a continuación, asignará el grupo de roles a la cuenta de usuario de Lynne Robbin en el Centro de administración de Microsoft 365.

1. En LON-CL1, debería haber iniciado sesión en el Centro de administración de Microsoft 365 como Holly Dickson. Si no es así, hágalo ahora.

2. En el **Centro de administración de Microsoft 365**, seleccione **Equipos y grupos** en el panel de navegación y, después, seleccione **Equipos y grupos activos**. 

3. En la página **Grupos y equipos activos**, la pestaña **Equipos y grupos de Microsoft 365** se muestra de forma predeterminada. Seleccione la pestaña **Grupos de seguridad**.

4. En la pestaña **Grupos de seguridad**, seleccione **+Agregar un grupo de seguridad** en la barra de menús. Al hacerlo, se inicia el asistente para **agregar un grupo de seguridad**.

5. En el asistente para **agregar un grupo de seguridad**, en la página **Configurar los conceptos básicos**, escriba **Grupo de roles de administración de usuarios** en el campo **Nombre**. Escriba **Este grupo de roles contiene roles de administración de usuarios** en el campo **Descripción**. Seleccione **Siguiente**.

6. En la página **Editar la configuración**, active la casilla **Los roles de Azure AD se puede asignar al grupo** y, a continuación, seleccione **Siguiente**.

7. En la página **Revisar y terminar de agregar grupo**, revise la configuración. Si es necesario cambiar alguna configuración, seleccione la opción **Editar** adecuada y realice el cambio. Cuando todas las opciones de configuración sean correctas, seleccione **Crear grupo**.

8. Una vez creado el **grupo de roles de administración de usuarios**, seleccione **Cerrar**.

9. Ahora que ha creado el grupo de roles, debe asignarle los roles correspondientes. En la página **Grupos y equipos activos**, se muestra la pestaña **Grupos de seguridad**. Seleccione el **grupo de roles de administración de usuarios** para abrir su panel de detalles.

10. En el panel **Grupo de roles de administración de usuarios**, la pestaña **General** se muestra de forma predeterminada. En la sección **Roles**, seleccione **Administrar roles**.

11. En el panel **Administrar roles de administrador** que aparece, seleccione la opción **Acceder al Centro de administración**. En la lista de roles Administrador comunes que aparece directamente debajo de esta opción, active las casillas **Administrador de usuarios** y **Administrador del éxito de la experiencia del usuario**. A continuación, seleccione la opción **Mostrar todo por categoría**. Desplácese hacia abajo hasta la categoría **Identidad**. Observe cómo ya está seleccionado el rol **Administrador de usuarios**, ya que lo seleccionó anteriormente en la lista de roles usados habitualmente. En la categoría **Identidad**, seleccione el rol **Administrador del departamento de soporte técnico** y, a continuación, seleccione **Guardar cambios**. 

12. En el panel **Administrar roles de administrador**, los tres roles seleccionados deben aparecer en la opción **Acceder al Centro de administración**. Seleccione la **X** en la esquina superior derecha del panel para cerrarlo.

13. En la pestaña **Grupos de seguridad**, seleccione **Grupo de roles de administración de usuarios**. En el panel **Grupo de roles de administración de usuarios** que aparece, compruebe que los tres roles aparecen en la sección **Roles**. Cierre este panel.

14. Ahora que ha asignado los roles al grupo de roles, debe asignar el grupo de roles a la cuenta de usuario de Lynne Robbin. En el **Centro de administración de Microsoft 365**, seleccione **Usuarios activos**.

15. En la página **Usuarios activos**, seleccione **Lynne Robbins**. 

16. En el panel de **Lynne Robbins** que aparecerá, la pestaña **Cuenta** se mostrará de forma predeterminada. En la tarea anterior, cuando asignó el rol Administrador de facturación a la cuenta de Diego Siciliani, seleccionó la opción **Administrar roles** en la sección **Roles**. Sin embargo, como asignará las funciones de Lynne a través de un grupo de roles, debe asignar a Lynne como miembro del grupo de roles de seguridad que acaba de crear. A través de la asignación de grupos, Lynne heredará las funciones asignadas al grupo de roles. Por lo tanto, en la sección **Grupos**, seleccione **Administrar grupos**. 

17. En el panel **Administrar grupos**, seleccione **+Asignar pertenencias**.

18. En el panel **Asignar pertenencias**, active la casilla **Grupo de roles de administración de usuarios** y seleccione **Agregar(1)**.

19. Una vez que aparezca una notificación de **Guardado** en la parte superior de la página, cierre este panel. 

20. Para comprobar que Lynne heredó los roles asignados al grupo de roles de administración de usuarios, seleccione **Lynne Robbins** en la lista de usuarios activos. 

21. En el panel **Lynne Robbins** que aparece, en la pestaña **Cuenta** que se muestra de forma predeterminada, debería ver los tres roles de administración de usuarios asignados a Lynne. En la sección **Roles**, seleccione **Administrar roles**.

22. En el panel **Administrar roles de administrador** que aparece, en la opción **Acceder al Centro de administración**, tenga en cuenta los tres roles seleccionados y el nombre del grupo desde el que se asignaron a Lynne. Tenga en cuenta también cómo se atenúan los tres roles. Esto indica que no se puede anular la selección de los roles de esta ventana. Dado que los roles se asignaron a Lynne desde un grupo de roles que contenía estos roles, solo puede anular la asignación de los roles quitando a Lynne como miembro del grupo de roles. Acaba de comprobar que Lynne tiene asignados estos roles. Cierre el panel **Administrar roles de administrador**.

23. Permanezca conectado a LON-CL1 y al Centro de administración de Microsoft 365 como Holly Dickson.

### Tarea 3: asignación de un rol Administrador mediante Windows PowerShell  

En esta tarea, usará Windows PowerShell para asignar un rol a una cuenta de usuario. Hacerlo le dará experiencia realizando esta función de administración en PowerShell, ya que algunos administradores prefieren realizar un mantenimiento de este tipo mediante PowerShell.  

En esta tarea, Holly quiere asignar a Patti Fernández al rol Administrador de soporte técnico de servicios. Para agregar un usuario a un rol Administrador mediante el módulo de PowerShell de Microsoft Graph, primero debe obtener el identificador de objeto del usuario y el identificador de objeto del rol. Si el rol aún no se ha habilitado (lo que significa que no se ha asignado a un usuario o no se ha habilitado físicamente), debe habilitarlo antes de poder asignárselo a un usuario mediante PowerShell. En esta tarea, habilitará primero el rol Administrador de soporte técnico del servicio antes de asignárselo a Patti Fernández.

PowerShell también le permite mostrar todos los usuarios asignados a un rol específico, lo que puede ser muy importante al auditar la implementación de Microsoft 365. En esta tarea, también aprenderá a usar PowerShell para mostrar todos los usuarios asignados a un rol específico. 

1. En LON-CL1, seleccione el icono de Windows PowerShell en la barra de tareas que dejó abierta desde un laboratorio anterior. Si cerró la ventana de PowerShell, abra una instancia con privilegios elevados con la misma instrucción que antes. 

2. La sesión de PowerShell todavía debe estar conectada a Microsoft Graph PowerShell desde el laboratorio anterior en el que recuperó un grupo eliminado mediante PowerShell. Sin embargo, si anteriormente cerró PowerShell y acaba de volver a abrirlo, importe el submódulo Microsoft.Graph.Identity.DirectoryManagement mediante los pasos del ejercicio de laboratorio anterior. 

3. Para realizar tareas de mantenimiento de usuarios de Microsoft 365 en Microsoft Graph PowerShell, primero debe importar el submódulo Microsoft.Graph.Users y solicitar permisos de lectura y escritura. Para importar este submódulo, escriba el siguiente comando en el símbolo del sistema y presione Entrar:   <br/>

        Import-Module Microsoft.Graph.Users

4. En el ejercicio de laboratorio anterior, se conectó a Microsoft Graph y solicitó permisos "Directory.ReadWrite.All" para ejecutar los cmdlets que restauraron el grupo eliminado. Para actualizar los objetos Usuario y rol de esta tarea, Holly debe solicitar ahora permisos de lectura y escritura para cada objeto. Para solicitar estos permisos, escriba el siguiente comando en el símbolo del sistema y presione Entrar:  <br/>

        Connect-MgGraph -Scopes 'User.ReadWrite.All', 'RoleManagement.ReadWrite.Directory'

5. En la ventana **Seleccionar una cuenta** que aparece, seleccione la cuenta de Holly Dickson. 

6. En el cuadro de diálogo **Permisos solicitados** que aparece, active la casilla **Consentimiento en nombre de la organización** y, a continuación, seleccione **Aceptar**.

7. Holly quiere asignar a **Patti Fernández** al rol **Administrador de soporte técnico del servicio**. Para asignar este rol mediante Microsoft Graph PowerShell, primero debe obtener el identificador de objeto del rol Administrador de soporte técnico del servicio para poder asignárselo a Patti. Sin embargo, en Microsoft Graph PowerShell, solo puede asignar roles que se hayan "habilitado". Los roles habilitados son roles que se habilitaron desde una plantilla de rol o que ya se han asignado a los usuarios a través de PowerShell o el Centro de administración de Microsoft 365. <br/>

    **Importante:** Antes de realizar este paso, compruebe que la ventana de PowerShell está en modo de pantalla completa. El nombre del rol aparece en la columna final del lado derecho de la pantalla. Si no está en modo de pantalla completa, no verá el nombre del rol asociado a cada identificador de objeto. 

    Para ver todos los roles habilitados en Microsoft 365, escriba el siguiente comando en el símbolo del sistema y presione Entrar: <br/>
    
        Get-MgDirectoryRole    <br/>

    **Nota:** Este comando muestra los roles que se han habilitado hasta ahora en Microsoft 365. Si el rol Administrador de soporte técnico de servicio aparece en esta lista, puede continuar directamente con el paso 13 para asignarle el rol a Patti. Sin embargo, dado que Administrador de soporte técnico del servicio no se incluye en esta lista de roles habilitados, debe realizar los pasos del 8 al 12 para habilitar el rol desde la plantilla de rol correspondiente antes de poder asignarle a Patti al rol en el paso 13. 

8. Para habilitar un rol en Microsoft Graph PowerShell, primero debe buscar su plantilla para obtener el identificador de objeto de la plantilla. Debe conocer el identificador de objeto de la plantilla para habilitar el rol desde la plantilla. Hay dos maneras en las que puede ver las plantillas de rol: puede mostrar toda la lista de plantillas de rol o puede mostrar la plantilla para un rol específico. Como experiencia de aprendizaje, realizará ambos métodos para que pueda ver la diferencia. <br/>

    Comencemos mostrando la lista completa de plantillas de rol junto con su identificador de objeto y el nombre para mostrar. Para ello, escriba el siguiente comando y presione Entrar: <br/>

        Get-MgDirectoryRoleTemplate | Format-List Id, DisplayName   <br/>

    Como puede ver después de ejecutar este comando, debe desplazarse por la lista de plantillas de rol que buscan el rol Administrador de soporte técnico del servicio. Puede ver fácilmente cómo esto puede ser tedioso. Como alternativa, ejecute el siguiente comando para consultar una plantilla de rol específica; en este caso, la plantilla de rol "Administrador de soporte técnico de servicio": <br/>

        Get-MgDirectoryRoleTemplate | ? DisplayName -eq "Service Support Administrator"   <br/>

    Después de ejecutar este comando, puede ver que solo muestra la plantilla de rol solicitada. Obviamente, puede haber ocasiones en las que se muestre toda la lista de plantillas de rol. Pero cuando necesite buscar una sola plantilla de rol, ejecutar el segundo comando de PowerShell será mucho más eficaz que tener que desplazarse por toda la lista de plantillas.
    
9. Ahora que ha consultado la plantilla de rol Administrador de soporte técnico de servicio en el paso anterior, resalte su **id.** (por ejemplo, fe930be7-5e62-47db-91af-98c3a49a38b1) y presione **Ctrl+C** para copiarlo en el Portapapeles (al copiarlo, desaparece el resaltado).

10. Ahora creará una variable que capture los atributos de la plantilla Administrador de soporte técnico del servicio. Al escribir el siguiente comando, presione **Ctrl+V** para pegar el id. de plantilla de Administrador de soporte técnico de servicio que copió en el Portapapeles en el paso anterior. <br/>

    En el símbolo del sistema, escriba el siguiente comando y presione Entrar: <br/>

        $ServiceSupportRoleTemplate = @{ RoleTemplateID = "paste in template ID here" }  <br/>

    Por ejemplo: $ServiceSupportRoleTemplate = @{ RoleTemplateID = "fe930be7-5e62-47db-91af-98c3a49a38b1" }

11. Ya está listo para habilitar el rol Administrador de soporte técnico del servicio en función de los atributos de la plantilla que capturó en la variable $ServiceSupportRoleTemplate. Escriba el siguiente comando y presione Entrar:  <br/>

        New-MgDirectoryRole -BodyParameter $ServiceSupportRoleTemplate

12. Para comprobar que el rol Administrador de soporte técnico de servicio se ha habilitado, escriba el siguiente comando y presione Entrar. Este comando mostrará la lista de roles habilitados:  <br/>
            
        Get-MgDirectoryRole <br/>

    **Nota:** Este comando muestra el id. de objeto de todos los roles habilitados, incluido el rol Administrador de soporte técnico de servicio que acaba de habilitar desde su plantilla. Más adelante, copiará y pegará el id. de objeto del rol Administrador de soporte técnico de servicio en el paso 15 al asignar a Patti a este rol.

13. Para asignar a Patti Fernández el rol Administrador de soporte técnico del servicio recién habilitado, primero debe obtener el id. de objeto de la cuenta de usuario de Patti. Para ello, escriba el siguiente comando y presione Entrar: <br/>

        Get-MgUser | Format-List ID, DisplayName

14. Ahora que conoce el id. de objeto del rol Administrador de soporte técnico del servicio habilitado recientemente y el id. de objeto de la cuenta de usuario de Patti, puede asignar el rol a Patti. Siga estos pasos para completar el proceso: <br/>

    a. En el comando anterior, ha mostrado la lista de usuarios activos. Resalte el **Id.** para la cuenta de Patti y cópielo (**Ctrl+C**) en el Portapapeles. El resaltado desaparece una vez que se copia en el Portapapeles.  <br/>

    b. Ejecute el siguiente comando que crea una variable que contiene el objeto de directorio para la cuenta de usuario de Patti. Al escribir este comando, pegue (**Ctrl+V**) el id. que acaba de copiar para la cuenta de usuario de Patti. <br/>

        $UserObject = @{ "@odata.id" = "https://graph.microsoft.com/v1.0/directoryObjects/paste in Patti's user account ID here" }  <br/>

    Por ejemplo: $UserObject = @{ "@odata.id" = "https://graph.microsoft.com/v1.0/directoryObjects/22fddbf7-42d2-4698-be65-ebc972a023e3" }

    c. En el paso 12, ha mostrado la lista de roles habilitados. Resalte el id del rol Administrador de soporte técnico del servicio y cópielo (**Ctrl+C**) en el Portapapeles. <br/>

    d. Ejecute el siguiente comando que asigna la variable que contiene la cuenta de usuario de Patti ($UserObject) al rol de directorio. Al escribir este comando, pegue (**Ctrl+V**) el id. que acaba de copiar para el rol Administrador de soporte técnico del servicio. <br/> 

        New-MgDirectoryRoleMemberByRef -DirectoryRoleId 'paste in the ID of the role here' -BodyParameter $UserObject
                
15. Ahora quiere comprobar que se le ha asignado a Patti el rol Administrador de soporte técnico del servicio. Anteriormente copió el id. de objeto de este rol en el Portapapeles y lo pegó en el comando anterior. También debe pegarlo en este comando. Escriba el siguiente comando y presione Entrar:
    
        Get-MgDirectoryRoleMember -DirectoryRoleId 'paste in the ID of the role here' 
                
16. El comando anterior solo muestra los id. de los usuarios asignados al rol seleccionado. Sin embargo, puede coincidir con el id. que se muestra con el id. de Patti para comprobar que a su cuenta se le ha asignado al rol **Administrador de soporte técnico del servicio**. Como puede ver, Patti es el único usuario asignado al rol. 

17. Ahora repitamos este proceso para ver todos los usuarios asignados al rol Administrador global. Repita el paso 15 para comprobar cuántos usuarios de Adatum se han asignado al rol **Administrador global**. Para completar este comando, primero debe copiar (**Ctrl+C**) el id. del rol Administrador global en el Portapapeles. Puede encontrar este id. en la lista de roles habilitados cuando ejecutó el paso 12. <br/>

    **Advertencia:** Copie el id. del rol Administrador global y NO el id. de la plantilla de rol Administrador global.

18. Compruebe que hay varios usuarios de Adatum a los que se les ha asignado el rol Administrador global. En un escenario real, el administrador de Microsoft 365 usaría este comando de PowerShell para supervisar cuántos administradores globales existen en su implementación de Microsoft 365. A continuación, quitarían el rol Administrador global de los usuarios que realmente no deberían tenerlo (recuerde que la guía de procedimientos recomendados es tener entre 2 y 4 administradores globales en una implementación de Microsoft 365, en función del tamaño de la organización).  <br/>

    En el caso de este laboratorio, aunque su proveedor de hospedaje de laboratorio asignó el rol Administrador global a usuarios distintos del Administrador de MOD (y se lo asignó a Holly Dickson), dejará a estos usuarios tal como están. En esta implementación ficticia de Adatum, no tiene sentido perder el tiempo eliminando este rol de sus cuentas. Además, algunas de las tareas futuras del laboratorio se basan en que a estos usuarios se les asigna el rol Administrador global. <br/>

    **IMPORTANTE:** Recuerde que, en la implementación real, el administrador de Microsoft 365 debe supervisar el rol Administrador global de forma periódica para mantener el número de usuarios asignados entre 2 y 4.
    
19. Deje abierta la sesión de Windows PowerShell para futuros ejercicios de laboratorio, pero minimícela antes de continuar con la siguiente tarea.


### Tarea 4: validación de asignaciones de roles 

En esta tarea, comenzará examinando las propiedades administrativas de dos usuarios, Joni Sherman y Lynne Robbins. Después, iniciará sesión en la página principal de Microsoft 365 en la máquina virtual cliente 2 (LON-CL2) como cada usuario para confirmar varios de los cambios realizados al administrar su delegación administrativa en las tareas anteriores. Por último, como Lynne Robbins, realizará dos tareas importantes de mantenimiento de cuentas de usuario: restablecer contraseñas y bloquear cuentas de usuario.

1. En LON-CL1, debería haber iniciado sesión en el Centro de administración de Microsoft 365 como Holly Dickson. Si no es así, hágalo ahora.

2. En el **Centro de administración de Microsoft 365**, si no muestra los **Usuarios activos**, vaya a esa página.  

3. En la lista **Usuarios activos**, seleccione **Joni Sherman**. 

4. En la ventana de propiedades de **Joni Sherman**, la pestaña **Cuenta** se muestra de manera predeterminada. En la sección **Roles**, debe indicar que Joni **no tiene acceso de administrador**. Seleccione la **X** en la esquina superior derecha para cerrar la ventana de propiedades de Joni.

5. En la lista **Usuarios activos**, seleccione **Lynne Robbins**. 

6. En la ventana de propiedades de **Lynne Robbins**, debe indicar que Lynne tiene asignado el rol **Administrador de usuarios**. Cierre la ventana de propiedades de Lynne.

7. Cambie a la máquina virtual cliente 2 (**LON-CL2**).

8. En **LON-CL2**, en la pantalla de inicio de sesión, iniciará sesión como la cuenta **Administrador** local con la contraseña **Pa55w.rd**.

9. Si aparece la ventana **Redes**, seleccione **Sí**.

10. En la barra de tareas, seleccione el icono de **Microsoft Edge**. Maximice la ventana del explorador Edge si es necesario.

11. En el explorador **Edge**, vaya a **https://portal.office.com**. 

12. Comenzará iniciando sesión en Microsoft 365 como **Joni Sherman**. En la ventana **Iniciar sesión**, escriba **JoniS@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino proporcionado por el proveedor de hospedaje del laboratorio). <br/>

    **Importante:** El proveedor de hospedaje de laboratorio ha asignado una **contraseña administrativa** a la cuenta de administrador de MOD y ha asignado esta misma **contraseña administrativa** a la cuenta de Holly Dickson al crearla. Sin embargo, el proveedor de hospedaje de laboratorio ha asignado otra **contraseña de usuario** a todas las demás cuentas de usuario predefinidas. En el futuro, al iniciar sesión como cualquier usuario que no sea el administrador de MOD o Holly Dickson, debe escribir esta **contraseña de usuario** y NO la **contraseña administrativa**. <br/>

    Puesto que inicia sesión como Joni Sherman, escriba esta **contraseña de usuario** en la ventana **Escribir contraseña**. Si fuera necesario, complete el proceso de inicio de sesión de MFA.

13. En la ventana **¿Mantener la sesión iniciada?**, active la casilla **No volver a mostrar** y, a continuación, seleccione **Sí**. Si aparece la ventana **Guardar contraseña**, seleccione **Nunca**.

14. Si aparece el cuadro de diálogo **Bienvenido a Microsoft 365** en medio de la página, seleccione la flecha hacia delante (>) dos veces y, a continuación, la marca de verificación para cerrarla.

15. Si aparece la ventana **Buscar más aplicaciones**, seleccione la **X** en la esquina superior derecha de la ventana para cerrarla.

16. En la ventana **Bienvenido a Microsoft 365**, que es la página principal de Microsoft 365 de Joni, aparece un panel de navegación en el lado izquierdo de la pantalla que indica las aplicaciones a las que el usuario tiene permiso para acceder. En este panel **Aplicaciones**, tenga en cuenta cómo no se muestra la opción **Administrador**. Esto se debe a que Joni nunca tuvo un rol de administrador de Microsoft 365. 

17. Ahora cerrará la sesión de Microsoft 365 como Joni. En **Microsoft Edge**, en la parte superior derecha de la página **Bienvenido a Microsoft 365**, seleccione el icono de usuario para **Joni Sherman** (el círculo en la esquina superior derecha con la imagen de Joni) y, en la ventana **Joni Sherman** que aparece, seleccione **Cerrar sesión.** 

18. Ahora volverá a iniciar sesión en Microsoft 365 como **Lynne Robbins**. En la pestaña actual del explorador **Edge**, debe mostrar un mensaje que indica **Joni, se ha cerrado la sesión**. En esta ventana, se le ofrece la opción de volver a iniciar sesión como Joni o iniciar sesión como un usuario diferente. <br/>

    Seleccione **Cambiar a otra cuenta** y, en el campo **Dirección de correo electrónico** que aparece, escriba **LynneR@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino proporcionado por el proveedor de hospedaje de laboratorio) y, a continuación, seleccione **Iniciar sesión**. En la ventana **Escribir contraseña**, escriba la **contraseña de usuario** proporcionada por el proveedor de hospedaje del laboratorio y seleccione **Iniciar sesión**. Si fuera necesario, complete el proceso de inicio de sesión de MFA. 

19. Si aparece el cuadro de diálogo **Bienvenido a Microsoft 365**, seleccione la flecha hacia delante (>) dos veces y, a continuación, seleccione la marca de verificación para cerrar la ventana.

20. Si aparece la ventana **Buscar más aplicaciones**, seleccione la **X** en la esquina superior derecha de la ventana para cerrarla.

21. En la ventana **Bienvenido a Microsoft 365**, que es la página principal de Microsoft 365 de Lynne, tenga en cuenta cómo se muestra el icono **Administrador** en el panel de navegación del lado izquierdo de la pantalla. Este icono aparece porque a Lynne se le asignó a un rol Administrador de Microsoft 365. Seleccione el icono **Administrador** para abrir el Centro de administración de Microsoft 365.

22. En el **Centro de administración de Microsoft 365**, seleccione **Usuarios** en el panel de navegación y, después, seleccione **Usuarios activos**. 

23. Como **Administrador de usuarios**, Lynne tiene permiso para cambiar las contraseñas de usuario. Recientemente, **Diego Siciliani** y **Pradeep Gupta** se pusieron en contacto con Lynne e informaron de que sus contraseñas podrían haber sido puestas en peligro. Según la directiva de empresa de Adatum, Lynne debe restablecer sus contraseñas a un valor temporal y, a continuación, obligarles a restablecer su contraseña en su siguiente inicio de sesión.   <br/>

    ‎En la lista **Usuarios activos**, a medida que mueve el mouse de una cuenta de usuario a otra, observe el icono de **llave (Restablecer una contraseña)** que aparece a la derecha del nombre de cada usuario. Seleccione el icono de llave que aparece a la derecha del nombre de **Diego Siciliani**.

24. En la ventana **Restablecer contraseña** de Diego, si la casilla **Crear automáticamente una contraseña** muestra una marca de verificación, marque esta casilla para desactivarla. Esto permitirá a Lynne asignarle manualmente a Diego una contraseña temporal.  

25. Escriba **diego** en el campo **Contraseña**. Observe que a la derecha de la contraseña, el sistema muestra un mensaje indicando que se trata de una contraseña **Débil**. Observe también el mensaje que aparece debajo del campo que indica los requisitos de una contraseña segura. Por último, observe que el botón **Restablecer contraseña**, situado en la parte inferior del panel, no está habilitado. **Este botón solo se habilitará una vez que escriba una contraseña segura**.  

26. Compruebe que la casilla **Requerir que este usuario cambie su contraseña cuando inicie sesión por primera vez** está activada (si no es así, selecciónela para que aparezca una marca de verificación). Escriba **Pa55w.rd** en el campo **Contraseña**. Observe que el campo **Contraseña** indica que se trata de una contraseña segura. <br/>

    Sin embargo, ahora seleccione la casilla **Requerir a este usuario que cambie la contraseña la primera vez que inicie sesión** para desactivarla. Tenga en cuenta el mensaje de error que aparece que indica la contraseña (Pa55w.rd) contiene una palabra, frase o serie de números que hace que sea fácil de adivinar. En este caso, escribió una variación de la palabra **password**, que desencadenará este error. El sistema le permite escribir esta contraseña si obliga al usuario a cambiarla en su primer inicio de sesión. Pero si no obliga al usuario a escribir una contraseña diferente en su primer inicio de sesión, no se permitirá esta contraseña.

27. Después de estos dos intentos de contraseña erróneos, Lynne ha decidido permitir que Microsoft 365 genere automáticamente una contraseña. Active la casilla **Crear automáticamente una contraseña** para que muestre una marca de verificación. <br/>
    
28. La contraseña que se genera automáticamente será una contraseña temporal porque Lynne quiere forzar a Diego a cambiarla la próxima vez que inicie sesión. Por lo tanto, compruebe que la casilla **Requerir que este usuario cambie su contraseña cuando inicie sesión por primera vez** muestra una marca de verificación; si la casilla está desactivada, selecciónela para que muestre una marca de verificación.

29. Seleccione **Restablecer contraseña**.

30. Si se le pide que guarde la contraseña, seleccione **nunca** para cerrar la ventana.

31. Debería recibir un mensaje de error que indica que no se puede restablecer la contraseña de Diego porque se le ha asignado un rol Administrador. En el caso de Diego, le asignó el rol Administrador de facturación anteriormente en este ejercicio de laboratorio. Dado que solo los Administradores de empresa pueden cambiar la contraseña de otro administrador y, dado que Lynne no es Administrador de empresa, tendrá que pedir a Holly Dickson que realice este cambio. Seleccione **Cerrar** en el panel **Restablecer contraseña**. 

32. Si aparece una ventana de solicitud de encuesta, seleccione **Cancelar**.

33. En la lista **Usuarios activos**, seleccione el icono de **llave (Restablecer una contraseña)** para **Pradeep Gupta**. 

34. En la ventana **Restablecer contraseña** para Pradeep, compruebe que la casilla **Crear automáticamente una contraseña** muestra una marca de verificación; si no lo hace, seleccione este cuadro para que el sistema genere automáticamente una contraseña para Pradeep.  <br/>

    Esta es una contraseña temporal porque Lynne quiere obligar a Pradeep a cambiarla la próxima vez que inicie sesión. Por lo tanto, compruebe que la casilla **Requerir que este usuario cambie su contraseña cuando inicie sesión por primera vez** muestra una marca de verificación; si la casilla está desactivada, selecciónela para que muestre una marca de verificación.
    
35. Seleccione el botón **Restablecer contraseña**.

36. En la ventana **La contraseña se ha restablecido**, debería recibir un mensaje que indica que restableció correctamente la contraseña de Pradeep. Seleccione **Close** (Cerrar).

37. La administración ha descubierto recientemente que el nombre de usuario de Alex Wilber puede haber estado en peligro. En consecuencia, se le ha pedido a Lynne que bloquee la cuenta de Alex para que nadie pueda iniciar sesión con su nombre de usuario hasta que la administración pueda determinar la magnitud del problema. En la lista **Usuarios activos**, active la casilla situada a la izquierda del nombre de **Alex Wilber** (NO seleccione el nombre de Alex).  <br/>

    **Importante:** Puesto que va a ejecutar un comando global en lugar de un comando asociado a la cuenta de Alex, solo quiere que la cuenta esté seleccionada en la lista de usuarios activos. Si se selecciona cualquier otra cuenta de usuario, debe anular la selección de esa cuenta de usuario antes de continuar. Desplácese por la lista de usuarios activos y compruebe que no hay ninguna otra cuenta de usuario seleccionada. Si se selecciona una cuenta distinta de Alex, seleccione la casilla de verificación de la cuenta para desactivarla. **Solo debe seleccionarse la cuenta de Alex Wilber.**

38. En la barra de menús de la parte superior de la página, seleccione el icono de puntos suspensivos **(...)** para mostrar un menú desplegable de acciones adicionales. En el menú que aparece, seleccione **Editar estado de inicio de sesión**.

39. En el panel **Bloquear inicio de sesión** que aparece, compruebe que la dirección de correo electrónico de Alex aparece debajo del encabezado **Bloquear inicio de sesión**. Active la casilla **Impedir que este usuario inicie sesión** y, a continuación, seleccione **Guardar cambios.** 

40. La ventana **Bloquear inicio de sesión** debe mostrar un mensaje que indica que Alex está bloqueado para iniciar sesión (y nadie puede iniciar sesión con el nombre de usuario de Alex en caso de que su nombre de usuario esté realmente en peligro). Además, Alex se desconectará automáticamente de los servicios de Microsoft en 60 minutos. Seleccione la **X** en la esquina superior derecha del panel para cerrarlo. 

41. Acaban de informar a Lynne de que el nombre de usuario de **Nestor Wilke** también ha sido puesto en peligro. Repita los pasos del 33 al 36 para impedir que Nestor inicie sesión (y para impedir que cualquier otra persona use su nombre de usuario para iniciar sesión). <br/>

    Cuando intentó bloquear el inicio de sesión de Nestor, debería haber recibido un mensaje de error que indica que **no se pudieron guardar los cambios**. La razón por la que recibió este error es que Nestor es un Administrador global y Lynne no. Solo un Administrador global puede impedir que otro Administrador global pueda iniciar sesión. Lynne tendrá que pedirle a Holly Dickson que haga este cambio. <br/>

    Cierre el panel **Bloquear inicio de sesión**.

42. Anteriormente, bloqueó a Alex Wilber para que no pudiera iniciar sesión. Para comprobar si está bloqueado, intentará iniciar sesión como Alex. Cierre sesión en Microsoft 365 seleccionando el icono de usuario de **Lynne Robbins** (el círculo con la imagen de Lynne en la esquina superior derecha) y en la ventana **Lynne Robbins** que aparece, seleccione **Cerrar sesión.** 

43. Como procedimiento recomendado, cierre todas las pestañas del explorador, excepto la pestaña **Cerrar sesión** una vez que se haya cerrado la sesión. En la pestaña **Cerrar sesión**, vaya a **https://portal.office.com**. 

44. En la ventana **Elegir una cuenta**, seleccione **Usar otra cuenta**. En la ventana **Iniciar sesión**, escriba **AlexW@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino proporcionado por el proveedor de hospedaje del laboratorio). En la ventana **Escribir contraseña**, escriba la **contraseña de usuario** proporcionada por el proveedor de hospedaje del laboratorio.  <br/>

    Debería aparecer la ventana **Seleccionar una cuenta** y debería mostrar el siguiente mensaje de error: **Se ha bloqueado la cuenta. Contacte con la persona responsable de soporte técnico para desbloquearla y vuelva a intentarlo.** Acaba de comprobar que Alex (o alguien que ha obtenido el nombre de usuario y la contraseña de Alex) no puede iniciar sesión. <br/>

    **Nota:** El bloqueo de cuenta puede tardar unos minutos en implementarse por completo. Hasta que el bloqueo se haya implementado en el sistema, es posible que Alex pueda iniciar sesión, pero ninguno de los servicios de Microsoft 365 estará disponible y no aparecerá en el portal de Microsoft 365. Una vez desbloqueada la cuenta, los servicios volverán a estar disponibles. <br/>

    Si puede iniciar sesión como Alex, cierre la sesión y espere unos minutos. Esto puede ser un buen momento para tomar un breve descanso. A continuación, intente volver a iniciar sesión como Alex. En este momento, debería recibir el mensaje de error que indica que la cuenta de Alex se ha bloqueado para iniciar sesión. 
    
45. Vuelva a **LON-CL1**. 

46. En **LON-CL1**, debería seguir conectado a **Microsoft 365** como Holly Dickson en su explorador Edge. La lista **Usuarios activos** debe mostrarse en el **Centro de administración de Microsoft 365** desde el inicio de esta tarea. 

47. Tras una investigación adicional, el director de tecnología de Adatum ha determinado que la cuenta de Alex Wilber no se ha puesto en peligro; por lo tanto, le ha pedido a Holly que quite el bloqueo de la cuenta de usuario de Alex. Repita los pasos del 33 al 36 para desbloquear su cuenta. Observe cómo la ventana **Bloquear inicio de sesión** del paso 35 muestra ahora la ventana **Desbloquear inicio de sesión**.  <br/>

    En la ventana **Desbloquear el inicio de sesión**, la casilla **Bloquear el inicio de sesión de este usuario** está seleccionada. Seleccione la casilla para desactivarla y, a continuación, seleccione **Guardar cambios**. <br/>
    
    **IMPORTANTE:** Aparecerá un mensaje de advertencia indicando que pueden pasar hasta 15 minutos antes de que Alex pueda iniciar sesión de nuevo. Dadas las limitaciones de tiempo con la formación, **NO** intentará comprobar si Alex puede volver a iniciar sesión. Si lo desea, puede intentar iniciar sesión como Alex en un momento posterior si está en un descanso o tiene tiempo libre y desea probarlo. Por ahora, permanezca en LON-CL1 y simplemente cierre la ventana **Desbloquear inicio de sesión**.
    
48. En LON-CL1, deje abierto el explorador y todas las pestañas y continúe con el siguiente ejercicio. 


# Fin del laboratorio 2

