# Ruta de aprendizaje 2: laboratorio 2: ejercicio 1: administración del acceso seguro de usuarios 

Las organizaciones deben asegurarse de que el acceso a los datos de su empresa en Microsoft 365 sea siempre seguro. Microsoft 365 (y a su vez, Copilot para Microsoft 365) a menudo muestra datos confidenciales y privados, incluyendo correos electrónicos, documentos, información del cliente y propiedad intelectual. El acceso no autorizado a Microsoft 365 puede provocar infracciones de datos, robo de identidad y otras actividades malintencionadas. Al proteger el acceso de los usuarios, las organizaciones impedirán que personas no autorizadas accedan a los datos de la empresa y hagan mal uso de ellos o los filtren al trabajar en Microsoft 365 y Copilot para Microsoft 365.

En el siguiente ejercicio de laboratorio, continuará en su rol como Holly Dickson, nueva administradora de Microsoft 365 de Adatum. Realizará varias funciones de administración de usuarios para preparar Adatum para la próxima implementación de Copilot para Microsoft 365. Comenzará creando una cuenta de usuario de Microsoft 365 para Holly, a quien se le asignará el rol Administrador global de Microsoft 365. 

**Nota:** El entorno de máquina virtual proporcionado por el proveedor de hospedaje del laboratorio incluye más de 20 cuentas de usuario de Microsoft 365 existentes, así como un gran número de cuentas de usuario locales existentes. En este curso se usarán varias de las cuentas de usuario de Microsoft 365 existentes en todos los laboratorios. Aunque el proveedor de hospedaje del laboratorio haya creado la cuenta Administrador de MOD, seguirá creando la cuenta de usuario de Holly Dickson, ya que tener más de un usuario que tenga asignado el rol Administrador global de Microsoft 365 es un procedimiento recomendado. También se le proporcionará la experiencia de crear una cuenta de usuario de Microsoft 365 en caso de que no esté familiarizado con el proceso.

Entonces, el director de tecnología de Adatum le pide a Holly que implemente la autenticación multifactor (MFA) y Smart Lockout de Microsoft Entra. Estas características ayudarán a reforzar la administración de contraseñas en toda la organización como preparación para Copilot para Microsoft 365. En cuanto a Smart Lockout, lo implementará mediante la administración de directivas de grupo. 

**NOTIFICACIÓN IMPORTANTE DE MFA:** Debido a un cambio reciente de Microsoft a los inquilinos de prueba de Microsoft 365 usados en este curso, tuvimos que realizar un cambio correspondiente en este laboratorio. <br/>

**Diseño de laboratorio original:** Este ejercicio de laboratorio se diseñó originalmente para que, como Holly Dickson, creara una directiva de acceso condicional que habilitara MFA en Adatum en la tarea 3. Este es el método recomendado para habilitar MFA, como aprendió en la parte de la conferencia de este entrenamiento. En la tarea 3, creó una directiva de acceso condicional que habilitó MFA para todos los usuarios, EXCEPTO para aquellos que eran miembros del equipo de trabajo piloto de Microsoft 365 que creó en un ejercicio anterior. Para probar la directiva en la tarea 4, tenía que iniciar sesión como Adele Vance. Como Adele no era miembro del equipo de trabajo piloto, tenía que completar el proceso de MFA para iniciar sesión en Microsoft 365. A continuación, cerró sesión como Adele e inició sesión nuevamente como Holly Dickson. Puesto que Holly es miembro del equipo de trabajo piloto de Microsoft 365, solo tenía que escribir su nombre de usuario y contraseña. No tenía que realizar una segunda forma de autenticación mediante MFA. Estos dos pasos de la tarea 4 comprobaron la directiva de acceso condicional, es decir,  solo los usuarios que no formaban parte del equipo de trabajo piloto tenían que usar MFA. 

La otra ramificación de esta directiva es que no tenía que usar MFA al iniciar sesión en el resto de laboratorios, como los demás usuarios de prueba que también eran miembros del equipo de trabajo piloto de Microsoft 365. Aunque las exclusiones de MFA se pueden establecer por motivos prácticos en función de las necesidades empresariales de una empresa, las empresas deberían evaluar cuidadosamente los riesgos asociados y aplicar exclusiones con prudencia, siempre con el objetivo de alinearse con los procedimientos recomendados de seguridad. En este laboratorio tenía que crear la exclusión del equipo de trabajo piloto por dos motivos: para aprender a crear exclusiones en directivas de acceso condicional y como medio para ahorrar tiempo en los laboratorios de entrenamiento al iniciar sesión como cada usuario de prueba. <br/>

**Cambio de inquilinos de Microsoft:** Dicho esto, Microsoft creó desde entonces una directiva de acceso condicional en el inquilino de prueba de Microsoft 365 que se usa en este laboratorio que requiere MFA para todas las cuentas de usuario. Desafortunadamente, la directiva de acceso condicional de Microsoft tiene prioridad sobre la directiva de acceso condicional que creará en este laboratorio que excluye un grupo específico. Las directivas de acceso condicional de Microsoft Entra se evalúan conjuntamente y se aplica la directiva de prioridad más alta que se aplica a un usuario. Si hubiera varias directivas con la misma prioridad, como es el caso, se aplicará la directiva más restrictiva. En este caso, la directiva de Microsoft es más restrictiva que la que usted crea, ya que la suya incluye excepciones de usuario. <br/>

**Impacto en este ejercicio de laboratorio:** Aunque Microsoft aplica MFA en este inquilino de prueba a través de una directiva de acceso condicional, aún creará su propia directiva de acceso condicional como se diseñó originalmente en la tarea 3. La tarea se modificó ligeramente desde la versión original para que vea la directiva que Microsoft integró en el inquilino de prueba. Pero aparte de eso, la directiva que creará no cambió desde su diseño original: requiere MFA para todos los usuarios, excepto para los miembros del equipo de trabajo piloto de Microsoft 365. Sin embargo, dado que la directiva que Microsoft integró en el inquilino de prueba del laboratorio es la más restrictiva de las dos directivas, esa directiva tiene prioridad durante la aplicación. Este escenario presenta dos implicaciones. En primer lugar, la directiva de Microsoft requiere que use MFA al iniciar sesión como cada usuario de prueba en el resto de estos laboratorios. En segundo lugar, dado que Microsoft Entra omitirá la directiva, no es necesario probarla. Por lo tanto, quitamos la tarea 4 original que probó la directiva de acceso condicional que creó. De todas formas, aunque no pueda probar la directiva, todavía será conveniente que la cree en la tarea 3 para que obtenga esa experiencia para las implementaciones reales. 

### Tarea 1: crear una cuenta de usuario de administrador de Microsoft 365 de Adatum

Holly Dickson es la nueva administradora de Microsoft 365 de Adatum. Debido a que no se configuró una cuenta de usuario de Microsoft 365 para ella, inició sesión inicialmente en Microsoft 365 como la cuenta de administrador de MOD (el administrador global predeterminado) del laboratorio anterior. En esta tarea seguirá iniciando sesión como administrador de MOD, durante la cual creará una cuenta de usuario de Microsoft 365 para Holly. También asignará el rol de administradora global de Microsoft 365 a la cuenta de Holly. Este rol proporcionará a Holly los permisos necesarios para realizar todas las funciones administrativas dentro de Microsoft 365. Después de esta tarea, iniciará sesión con la nueva cuenta de Holly y realizará todos los laboratorios restantes con el rol de Holly. 

**Nota de licencia:** Antes de crear la cuenta de Holly, primero comprobará el número de licencias disponibles. Al hacerlo, observará que, aunque su inquilino de laboratorio proporciona 20 licencias de Microsoft 365 E5 (sin Teams) y 20 licencias de Microsoft Teams Enterprise, todas esas licencias ya se asignaron a las cuentas de usuario existentes creadas por el proveedor de hospedaje del laboratorio. Por lo tanto, primero es necesario anular la asignación de cada una de las licencias de usuario existentes para poder asignarlas a Holly.

**Importante:** Como procedimiento recomendado en la implementación real, siempre debería anotar las credenciales de la primera cuenta de administrador global (en este laboratorio, se trata de la cuenta de administrador de MOD, cuyo nombre de usuario es admin@xxxxxZZZZZZ.onmicrosoft.com, donde xxxxxZZZZZZ es el prefijo de inquilino asignado por el proveedor de hospedaje del laboratorio). Debería almacenar esta información de cuenta por motivos de seguridad. **Esta cuenta debería ser una identidad NO personalizada** que posea los privilegios más altos posibles de un inquilino. **No** se debería activar MFA porque no está personalizado. Dado que el nombre de usuario y la contraseña de esta primera cuenta de administrador global suelen compartirse entre varios usuarios, esta cuenta resulta ser un blanco perfecto para ataques. Por lo tanto, siempre se recomienda que las organizaciones creen cuentas de administrador de servicios personalizadas (por ejemplo: un administrador de Exchange, un administrador de SharePoint, etc.) y tengan los mínimos administradores globales personales posibles. Para aquellos administradores globales personales que se creen en la implementación real, a cada uno de ellos se le debería asignar un único usuario (como Holly Dickson) y a cada uno se le debería aplicar la autenticación multifactor (MFA) de Microsoft Entra.

1. En la máquina virtual **LON-CL1**, el **Centro de administración de Microsoft 365** debe estar abierto en el explorador Microsoft Edge desde el ejercicio de laboratorio anterior. Debería iniciar sesión en Microsoft 365 como **Administrador de MOD**. 

2. Dado que agregará un nuevo usuario, debería comenzar comprobando la disponibilidad de licencias antes de agregar la cuenta de usuario. En el panel de navegación del **Centro de administración de Microsoft 365**, seleccione **Facturación** para expandir el grupo Facturación y, a continuación, seleccione **Licencias**. 

3. En la página **Licencias**, la pestaña **Suscripciones** se muestra de forma predeterminada. En la lista de suscripciones, observe que las suscripciones **Microsoft 365 E5 (sin Teams)** y **Microsoft Teams Enterprise** no tienen licencias disponibles. El inquilino del laboratorio proporciona 20 licencias para cada suscripción, pero se han asignado todas las 40 licencias. Como debe asignar a Holly una licencia de **Microsoft 365 E5 (sin Teams)** y una licencia de **Microsoft Teams Enterprise**, primero deberá anular la asignación de las licencias de una cuenta de usuario existente para que estén disponibles para Holly. 

4. En el panel de navegación del **Centro de administración de Microsoft 365**, seleccione **Usuarios** y, a continuación, seleccione **Usuarios activos**. En la lista **Usuarios activos**, verá la lista de cuentas de usuario existentes creadas por el proveedor de hospedaje del laboratorio. Puesto que Christie Cline pasará a un nuevo rol en la empresa y ya no formará parte del proyecto piloto de Microsoft 365, anulará la asignación de las licencias de **Microsoft 365 E5 (sin Teams)** y **Microsoft Teams Enterprise** de su cuenta para reasignarlas a la nueva cuenta de Holly Dickson.

5. En la página **Usuarios activos**, en la lista de usuarios, seleccione **Christie Cline** (seleccione el nombre con hipervínculo de Christie y no la casilla situada junto a su nombre).

6. En el panel de **Christie Cline** que aparecerá, la pestaña **Cuenta** se mostrará de forma predeterminada. Seleccione la pestaña **Licencias y aplicaciones**. En **Licencias (2)**, active las casillas situadas junto a **Microsoft 365 E5 (sin Teams)** y **Microsoft Teams Enterprise** para desactivarlas y, a continuación, seleccione **Guardar cambios**. Una vez guardados los cambios, cierre el panel **Christie Cline**. 

7. Ya está listo para crear una cuenta de usuario para Holly Dickson, que es la nueva administradora de Microsoft 365 de Adatum. Al hacerlo, asignará a Holly el rol de administradora global de Microsoft 365, que proporcionará a Holly acceso global a la mayoría de las características de administración y los datos en todos los servicios en línea de Microsoft. También asignará a Holly las dos licencias de las que acaba de cancelar la asignación de Christie Cline. <br/>

    En la ventana **Usuarios activos**, seleccione la opción **Agregar un usuario** que aparece en la barra de menús situada encima de la lista de usuarios activos. Esto iniciará el **Asistente para agregar usuarios**.

8. En la página **Configurar los aspectos básicos** del **Asistente para agregar usuarios**, escriba la siguiente información:

    - Nombre: **Holly**

    - Apellido: **Dickson** 

    - Nombre para mostrar: Al hacer una tabulación en este campo, aparecerá **Holly Dickson**.

    - Nombre de usuario: **Holly** <br/>
    
        ‎**IMPORTANTE:** A la derecha del campo **Nombre de usuario** está el campo de dominio. Se rellenará previamente con el dominio en la nube **xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo del inquilino proporcionado por el proveedor de hospedaje del laboratorio).<br/>
    
    - Borre (desactive) la casilla **Crear automáticamente una contraseña**, lo que mostrará un nuevo campo para escribir una contraseña definida por el administrador.

    - Escriba la nueva contraseña administrativa en el nuevo campo **Contraseña** que aparece. 

    - Borre (desactive) la casilla **Requerir a este usuario que cambie la contraseña la primera vez que inicie sesión** 

9. Seleccione **Siguiente**. Si apareciera un cuadro de diálogo **Guardar contraseña** en la parte superior de la pantalla, seleccione **Nunca**.

10. En la página **Asignar licencias de producto**, escriba la siguiente información: <br/>

    - Seleccione la ubicación: **Estados Unidos**

    - Licencias: En la opción **Asignar una licencia de producto a un usuario**, active las casillas **Microsoft 365 E5 (sin Teams)** y **Microsoft Teams Enterprise**.

11. Seleccione **Siguiente**.

12. En la página **Configuración opcional**, seleccione la flecha desplegable situada a la derecha de **Roles**. 

13. En la sección **Roles**, seleccione la opción **Acceso al Centro de administración**. Al seleccionar esta opción, los roles de administrador de Microsoft 365 más usados se habilitarán debajo.  <br/>

    **Nota:** Todos los roles de administrador se mostrarán si selecciona **Mostrar todo por categoría**, que aparecerá después del último rol común. Para Holly, no es necesario ver todos los roles de administrador por categoría, ya que Holly tendrá asignado el rol de administrador global que aparecerá en la lista de roles usados habitualmente.

14. Seleccione la casilla **Administrador global**. <br/>

    **Nota:** Se mostrará un mensaje de advertencia indicando que Adatum ya tiene 7 administradores globales. En un entorno normal, esto sería excesivo y no se recomienda. Para los fines de este laboratorio, el proveedor de hospedaje del laboratorio asignó el rol de administrador global al administrador de MOD y otras seis cuentas de usuario, algo que no se vería normalmente en una implementación real. Sin embargo, para los fines de este laboratorio sobre el entorno de laboratorio ficticio de Adatum, omita este mensaje. **Dicho esto, la guía de procedimientos recomendados que debería seguir consiste en tener de dos a cuatro administradores globales en las implementaciones reales de Microsoft 365.** 

15. Seleccione **Siguiente**.

16. En la ventana **Revisar y finalizar**, revise las selecciones. Si se debiera cambiar algo, seleccione el vínculo **Editar** adecuado y realice los cambios necesarios. De lo contrario, si todo fuera correcto, seleccione **Terminar de agregar**. 

17. En la página **Holly Dickson agregó a los usuarios activos**, en la sección **Detalles del usuario**, seleccione la opción **Mostrar** para comprobar que la contraseña de Holly sea la misma **Contraseña administrativa** proporcionada por el proveedor de hospedaje del laboratorio para la cuenta de administrador del inquilino (es decir, la cuenta de administrador de MOD).  <br/>

    **Nota:** Si escribió accidentalmente una contraseña diferente, una vez que vuelva a la página **Usuarios activos**, deberá seleccionar el icono **Restablecer una contraseña** (el icono de clave que aparecerá al mantener el puntero sobre la cuenta de Holly) para cambiar su contraseña al valor correcto.

18. Seleccione **Close** (Cerrar).

19. Permanezca conectado a la máquina virtual del cliente 1 (LON-CL1) con el Centro de administración de Microsoft 365 abierto en el explorador para la siguiente tarea.


### Tarea 2: agregar a Holly al equipo de trabajo piloto de Microsoft 365

Después de completar la tarea anterior, debería iniciar sesión en el **Centro de administración de Microsoft 365** con la cuenta de **Administrador de MOD**. En esta tarea, comenzará a implementar el proyecto piloto de Microsoft 365 de Adatum como Holly Dickson, nueva administradora de Microsoft 365 de Adatum. Por lo tanto, iniciará esta tarea al cerrar sesión en Microsoft 365 como administrador de MOD y volverá a iniciar sesión como Holly. 

En una tarea anterior, creó un grupo de Microsoft 365 para los miembros del equipo de proyecto piloto de Adatum para poder crear un tema personalizado para ese grupo. En esta tarea, agregará a Holly a este grupo. 

1. En la máquina virtual LON-CL1, el **Centro de administración de Microsoft 365** aún debería estar abierto en el explorador Microsoft Edge desde la tarea anterior. Debería iniciar sesión en Microsoft 365 como **Administrador de MOD**. <br/>

    En la pestaña del **Centro de administración de Microsoft 365**, en la esquina superior derecha de la pantalla, observe que se muestra el nombre del administrador de MOD y el icono de un megáfono. El nombre se muestra debido al tema personalizado que creó en el ejercicio del laboratorio anterior asociado a un grupo de usuarios de proyectos piloto de Microsoft 365 que incluyó el administrador de MOD. Tenga esto en cuenta cuando vuelva a iniciar sesión como Holly Dickson. <br/>

    Seleccione el icono de usuario del **Administrador de MOD** de la esquina superior derecha del explorador. En la ventana **Administrador de MOD** que aparece, seleccione **Cerrar sesión.** <br/>
    
    **Importante:** Al cerrar la sesión de una cuenta de usuario e iniciar sesión en otra, debería cerrar todas las pestañas del explorador, excepto la pestaña **Cerrar sesión**. Este es un procedimiento recomendado que ayuda a evitar cualquier confusión cerrando las ventanas asociadas al usuario anterior. Una vez que haya cerrado la sesión de la cuenta de administrador de MOD, tómese un momento y cierre todas las demás pestañas del explorador, excepto la pestaña **Cerrar sesión**. 
    
2. En el explorador Microsoft Edge, en la pestaña **Cerrar sesión**, escriba la siguiente dirección URL en la barra de direcciones para volver a iniciar sesión en Microsoft 365: **https://portal.office.com**. 

3. En la ventana **Elegir una cuenta**, solo aparecerá la cuenta de administrador de inquilinos del administrador de MOD (la cuenta de admin@xxxxxZZZZZZ.onmicrosoft.com) de la que acaba de cerrar sesión. Seleccione **Usar otra cuenta**. 

4. En la ventana **Iniciar sesión**, escriba **Holly@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino proporcionado por el proveedor de hospedaje del laboratorio). Seleccione **Siguiente**.

5. En la ventana **Escribir contraseña**, escriba la misma **Contraseña administrativa** proporcionada por el proveedor de hospedaje del laboratorio para la cuenta de administrador del inquilino (es decir, la cuenta de administrador de MOD) que también asignó a la cuenta de Holly y, a continuación, seleccione **Iniciar sesión**. Si fuera necesario, complete el proceso de inicio de sesión de MFA.  <br/>

    **Nota:** Desde este momento, Holly y el administrador de MOD serán los únicos usuarios a los que se les asigne la **Contraseña administrativa** proporcionada por el proveedor de hospedaje de laboratorio. A todos los demás usuarios se les asigna la **Contraseña de usuario** proporcionada por el proveedor de hospedaje de laboratorio.

6. Si aparece un cuadro de diálogo **Le damos la bienvenida a Microsoft 365** en medio de la pantalla, tenga en cuenta que no hay ninguna opción para cerrarlo. En su lugar, a la derecha de la ventana, seleccione el icono de flecha hacia delante (**>**) dos veces y, a continuación, seleccione el icono de marca de verificación para avanzar a través de las diapositivas de esta ventana de mensajes. 

7. Si aparece una ventana **Crear con Microsoft 365**, seleccione la **X** en la esquina superior de la ventana para cerrarla. 

8. La página **Le damos la bienvenida a Microsoft 365** aparecerá en el explorador Edge, en la pestaña **Inicio | Microsoft 365**. Esta es la página principal de Microsoft 365 de Holly. Tenga en cuenta que las iniciales de Holly aparecen en la esquina superior derecha de la pantalla, sin embargo, no se muestra el nombre de Holly. Esto se debe a que la cuenta de Holly no existía cuando se agregó a los usuarios de proyectos piloto de Microsoft 365 al grupo asociado al tema personalizado en el ejercicio del laboratorio anterior. Como Holly desea ver su nombre en la parte superior de cada ventana de Microsoft 365 cuando inicie sesión en el sistema, primero querrá agregar su cuenta al grupo de usuarios de proyectos piloto de Microsoft 365. <br>

    En la columna de iconos de aplicación que aparece en el panel de navegación del lado de la pantalla, seleccione **Administrador**. Esto abrirá el **Centro de administración de Microsoft 365** en una nueva pestaña del explorador. 

9. En el **Centro de administración de Microsoft 365**, seleccione **Equipos y grupos** en el panel de navegación y, después, en él, seleccione **Equipos y grupos activos**. 

10. En la página **Equipos y grupos activos**, hay una pestaña para ver cada uno de los tipos de grupo. La pestaña **Grupos de Teams y Microsoft 365** se muestra de forma predeterminada. En esta pestaña, seleccione **Proyecto piloto de M365**.

11. En el panel **Proyecto piloto de M365** que se muestra, la pestaña **General** se mostrará de forma predeterminada. Seleccione la pestaña **Pertenencia**.

12. En la pestaña **Pertenencia**, la subpestaña **Propietarios** se mostrará de forma predeterminada en el panel de navegación que aparecerá en el lado del panel. Seleccione la subpestaña **Miembros** que hay debajo de ella.

13. En la subpestaña **Miembros**, seleccione **+Agregar miembros**.

14. En el panel **Agregar miembros de grupo al proyecto piloto de M365** que se muestra, seleccione dentro del campo **Buscar por nombre o dirección de correo electrónico**. En la lista de usuarios que aparece, desplácese hacia abajo y seleccione **Holly Dickson**. Seleccione el botón **Agregar (1)** y, a continuación, cierre el panel **Agregar miembros de grupo al proyecto piloto de M365** una vez que Holly se agregue al grupo.

15. En la página **Equipos y grupos activos**, seleccione el icono **Actualizar** que hay en la parte superior de la pantalla, a la izquierda de la barra de direcciones. Observe cómo aparece el nombre de Holly Dickson junto a sus iniciales en la esquina superior derecha de la pantalla (nota: es posible que tenga que actualizar dos veces para ver el nombre de Holly).

16. En el **Centro de administración de Microsoft 365**, seleccione **Usuarios** en el panel de navegación y, después, seleccione **Usuarios activos**.

17. En la ventana **Usuarios activos**, al mantener el mouse sobre el **Nombre para mostrar** de un usuario, aparecerá un **icono de clave** a la derecha del nombre de usuario. Al seleccionar el icono de clave, es posible restablecer la contraseña de un usuario. Es necesario restablecer las contraseñas de Adele Vance, Alex Wilber, Joni Sherman, Lynne Robbins y Patti Fernandez a la misma **Contraseña administrativa** proporcionada por el proveedor de hospedaje del laboratorio para la cuenta de administrador del inquilino (es decir, la cuenta de administrador de MOD) y que anteriormente asignó a Holly Dickson.<br/>

    Mantenga el mouse sobre **Adele Vance** y seleccione el icono de clave que aparezca.

18. En el panel **Restablecer contraseña** que aparece para Adele, borre (desactive) la casilla **Crear contraseña automáticamente**. 

19. En el campo **Contraseña** que aparezca, escriba la misma **Contraseña administrativa** proporcionada por el proveedor de hospedaje del laboratorio para la cuenta de administrador del inquilino (es decir, la cuenta de administrador de MOD). Seleccione el icono de ojo (**Mostrar contraseña**) situado al final del campo **Contraseña** para mostrar el valor especificado. Compruebe que haya escrito correctamente la contraseña del inquilino.

20. Borre (desactive) la casilla **Requerir a este usuario que cambie la contraseña la primera vez que inicie sesión**.

21. Seleccione **Restablecer contraseña**. Si apareciera un cuadro de diálogo **Guardar contraseña** en la parte superior de la pantalla, seleccione **Nunca**. A continuación, seleccione **Cerrar** en el panel **Se restableció la contraseña**.

22. Repita los pasos del 17 al 21 para **Alex Wilber**, **Joni Sherman**, **Lynne Robbins** y **Patti Fernandez**. Restablezca cada una de las contraseñas a la misma **Contraseña administrativa** proporcionada por el proveedor de hospedaje del laboratorio para la cuenta de administrador del inquilino (es decir, la cuenta de administrador de MOD). En el paso 19, no olvide mostrar la contraseña que escribió para comprobar que sea el valor correcto.

23. Permanezca conectado a LON-CL1 con el **Centro de administración de Microsoft 365** abierto en el explorador para la siguiente tarea.


### Tarea 3: Creación de una directiva de acceso condicional para implementar MFA

**IMPORTANTE:** Esta tarea comienza examinando la directiva de acceso condicional que Microsoft creó para implementar MFA para todos los usuarios. Sin embargo, el asociado de aprendizaje podría estar usando inquilinos de prueba anteriores al cambio reciente de la directiva de MFA. Si no se le pidió realizar la MFA después del inicio de sesión de cada usuario, el inquilino de prueba no requiere MFA. En este caso, la directiva de MFA que creó Microsoft no aparecerá en la lista de directivas. Si ese fuera el caso con el inquilino, omitirá los pasos que revisan esta directiva. 

Tal y como se indica en el entrenamiento, hay tres maneras de implementar MFA: con directivas de acceso condicional, con valores predeterminados de seguridad y con MFA por usuario heredado (no se recomienda para organizaciones grandes). En este ejercicio, habilitará MFA mediante una directiva de acceso condicional, que es el método que Microsoft recomienda. Adatum le ha pedido a Holly que habilite MFA para todos los usuarios de Microsoft 365, tanto internos como externos. Sin embargo, para probar la implementación del proyecto piloto de Microsoft 365 de Adatum, Holly desea excluir a los miembros del equipo de trabajo piloto de M365 de tener que usar MFA para iniciar sesión. Una vez completado el proyecto piloto, Holly actualizará la directiva quitando la exclusión de este grupo del requisito de MFA. La directiva también incluirá otros dos requisitos. Se requerirá MFA para todas las aplicaciones en la nube y se requerirá MFA incluso aunque los usuarios inicien sesión desde ubicaciones de confianza. 

**Nota:** Aunque creará una directiva de acceso condicional en esta tarea que habilita la MFA, NO la habilitará. Algunos alumnos podrían tener un inquilino que requiera MFA, en cuyo caso no se aplicará esta directiva. Y aunque todos los alumnos de la clase tengan un inquilino que no requiera MFA, aún no habilitará la directiva. El punto de este ejercicio es proporcionarle experiencia en la creación de directivas para habilitar la autenticación multifactor y no autenticarse realmente con MFA, algo que se supone que sabe hacer. Por lo tanto, elegimos no permitir que los alumnos habiliten su directiva, lo que proporciona el mayor equilibrio, dada la posible situación de los inquilinos en la clase. 

1. En la máquina virtual LON-CL1, el **Centro de administración de Microsoft 365** aún debería estar abierto en el explorador Microsoft Edge desde la tarea anterior. Debería iniciar sesión en Microsoft 365 como **Holly Dickson**.
   
2. En el **Centro de administración de Microsoft 365**, en la sección **Centros de administración** del panel de navegación, seleccione **Identidad**. Al hacerlo, se abrirá el Centro de administración de Microsoft Entra en una nueva pestaña del explorador. Si apareciera una ventana indicando **Seleccionar una cuenta**, seleccione la **cuenta de Holly Dickson**.

3. En el **Centro de administración de Microsoft Entra**, seleccione **Protección** en el panel de navegación y, a continuación, seleccione **Acceso condicional**.

4. En la página **Acceso condicional | Información general**, seleccione **Directivas** en el panel de navegación central.

5. En la página **Acceso condicional | Directivas**, revise las directivas predeterminadas disponibles con la suscripción de Microsoft 365. Observe la directiva titulada **Autenticación multifactor para asociados y proveedores de Microsoft**. Esta es la directiva de acceso condicional que Microsoft creó que requiere MFA para todos los usuarios de todas las aplicaciones en la nube. Seleccione esta directiva para poder ver cómo Microsoft está aplicando MFA para todos los usuarios de este inquilino de prueba.   <br/>

    **IMPORTANTE:** El asociado de aprendizaje podría estar usando inquilinos de prueba anteriores a este cambio reciente de MFA. Si no se le pidió realizar la MFA después del inicio de sesión de cada usuario, el inquilino de prueba no requiere MFA. En este caso, la directiva titulada **Autenticación multifactor para asociados y proveedores de Microsoft** no aparecerá en la lista de directivas, en cuyo caso deberá ir al paso 11 para empezar a crear su propia directiva de acceso condicional. 

6. En la página **Autenticación multifactor para asociados y proveedores de Microsoft**, en el grupo **Usuarios**, seleccione **Todos los usuarios incluidos y los usuarios específicos excluidos**. Al hacerlo, se mostrarán dos pestañas: **Incluir** y **Excluir**.

7. En la pestaña **Incluir**, observe que **Todos los usuarios** está seleccionado. Solo para satisfacer su curiosidad, intentemos cambiar esta directiva desactivando MFA. Seleccione **Ninguno** y, a continuación, seleccione el botón **Guardar**. <br/>

    **Observe lo que ocurrió:** Aparecerá brevemente un cuadro de mensaje en la parte superior de la página indicando **No se pudo actualizar la autenticación multifactor para asociados y proveedores de Microsoft**. A continuación, el sistema le devolvió a la página **Acceso condicional | Directivas**. Si no encontró este mensaje, repita este paso de nuevo.  <br/>

    Lo mismo sucede si, en la pestaña **Incluir**, se selecciona **Usuarios y grupos** y se seleccionan usuarios o grupos específicos en lugar de todos los usuarios. De hecho, Microsoft ha integrado un firewall de seguridad para que, si se intenta realizar algún cambio en esta directiva, se producirá un error al intentar guardarla. 

8. Microsoft compiló una exclusión en esta directiva. Echémosle un vistazo. En la página **Directivas**, seleccione de nuevo la directiva **Autenticación multifactor para asociados y proveedores de Microsoft** y, a continuación, seleccione **Todos los usuarios incluidos y los usuarios específicos excluidos**. Esta vez, seleccione la pestaña **Excluir**. 

9. Tenga en cuenta que Microsoft seleccionó la casilla **Roles de directorio**. Seleccione el campo que hay debajo de esta opción. En el menú de roles que se pueden elegir para excluir de MFA, el único rol seleccionado por Microsoft es **Cuentas de sincronización de directorios**. Este rol se asigna automáticamente a la cuenta de servicio de Microsoft Entra Connect Sync y no está pensado para usarse de forma contraria. Es un rol especial que solo tiene permisos para realizar tareas de sincronización de directorios. Este rol resulta fundamental para sincronizar una instancia local de Active Directory Domain Services (AD DS) con Microsoft Entra ID, lo que proporciona coexistencia de identidades. Microsoft no requiere MFA para este rol porque el servicio de sincronización debe ejecutarse continuamente sin interrupciones que pudieran deberse a solicitudes de MFA. Además, esta cuenta de servicio está configurada con permisos muy limitados y no se usa para inicios de sesión interactivos, reduciendo riesgos de seguridad.   <br/>

    Al igual que con el paso anterior, en el que intentó cambiar la configuración de MFA para que no incluyera a usuarios o a usuarios seleccionados, si se intentan seleccionar otros roles para moverse por la configuración de MFA, experimentará el mismo error que indica **No se pudo actualizar la autenticación multifactor para asociados y proveedores de Microsoft** al intentar guardar la directiva. El firewall de seguridad de Microsoft no permite ningún cambio en esta directiva de acceso condicional que afecte a aquellos que deban usar MFA.

10. Si sigue teniendo abierta la página **Autenticación multifactor para asociados y proveedores de Microsoft**, seleccione la **X** de la esquina superior para cerrarla y volver a la página **Acceso condicional | Directivas**. O bien, si intentó guardar un cambio en la directiva, se producirá un error en el intento y ya debería estar de regreso en la página **Acceso condicional | Directivas**.

11. En la página **Acceso condicional | Directivas**, en la barra de menús de la parte superior de la página, seleccione **+Nueva directiva**.

12. En la ventana **Nueva directiva de acceso condicional**, escriba **MFA para todos los usuarios de Microsoft 365** en el campo **Nombre**.

13. Comenzará definiendo los requisitos de MFA para los usuarios. En el grupo **Usuarios**, seleccione **0 usuarios y grupos seleccionados**. Al hacerlo, se mostrarán dos pestañas: **Incluir** y **Excluir**.

14. En la pestaña **Incluir**, seleccione **Todos los usuarios**. Observe el mensaje de advertencia que aparece. Se abordará esto en los dos pasos siguientes.

15. Seleccione la pestaña **Excluir**. Para evitar el bloqueo del sistema, tal y como se indicaba en el mensaje de advertencia anterior, tendrá que excluir a los administradores globales (en este caso, Holly). Holly también desea excluir a los demás miembros del equipo de trabajo piloto de Microsoft 365 para realizar pruebas. Una vez que la instancia de Microsoft 365 esté activa, Holly quitará el equipo de trabajo piloto de la lista Excluir de esta directiva de acceso condicional y, simplemente, se excluirá a sí misma y a algunos otros administradores globales. Pero por ahora, Holly quiere excluir a todo el grupo. <br/>

    Para ello, seleccione **Usuarios y grupos**. 

16. En la ventana **Seleccionar usuarios y grupos excluidos** que aparece, seleccione el equipo de trabajo piloto de Microsoft 365. La pestaña **Todos** se muestra de forma predeterminada. Para encontrar rápidamente el equipo de trabajo piloto, seleccione la pestaña **Grupos**. En la lista de grupos activos, active la casilla situada junto al equipo de **trabajo piloto de M365** y, a continuación, seleccione el botón **Seleccionar** de la parte inferior de la ventana. De nuevo en la ventana **Nueva directiva de acceso condicional**, observe el mensaje que aparece en la sección **Usuarios**. 

17. Ahora definirá el requisito de MFA para todas las aplicaciones en la nube. En la sección **Recursos de destino**, seleccione **No hay recursos de destino seleccionados**. Al hacerlo, se mostrarán dos pestañas: **Incluir** y **Excluir**.

18. Seleccione el campo desplegable **Seleccionar a qué se aplica esta directiva** para ver las distintas opciones en el menú desplegable. Seleccione **Aplicaciones en la nube**. 

19. En la pestaña **Incluir**, observe que la configuración predeterminada sea **Ninguno**. Si no cambió esta configuración, ninguna aplicación en la nube requeriría MFA (y eso incluye a Microsoft 365). Por lo tanto, incluso si creó esta directiva y seleccionó la opción para requerir MFA para todos los usuarios, pero dejó esta configuración de **Recursos de destino** en **Ninguno**, cualquier usuario que inicie sesión en Microsoft 365 no tendría que usar MFA. <br/>

    En la pestaña **Incluir**, seleccione la opción **Seleccionar aplicaciones**. Al hacerlo, se muestran dos secciones: **Editar filtro** y **Seleccionar**. En la sección **Seleccionar**, seleccione **Ninguna**. En el panel **Seleccionar aplicaciones en la nube** que aparece, desplácese hacia abajo por la lista de aplicaciones para ver todas las distintas aplicaciones para las que se podría requerir MFA. **NO seleccione ninguna de las aplicaciones.** Estamos haciendo que se desplace por esta lista solo para que vea lo granular que se puede ser al requerir MFA si se decidiera limitar MFA a determinadas aplicaciones.  <br/>

    Para Adatum, Holly desea requerir MFA para todas las aplicaciones en la nube, lo que normalmente es un escenario empresarial más común que seleccionar aplicaciones específicas. En la pestaña **Incluir**, seleccione la opción **Todas las aplicaciones en la nube**. Adatum no excluirá ninguna aplicación en la nube de la autenticación MFA. Es posible seleccionar la pestaña **Excluir** si se desean ver las opciones que proporciona. Funciona básicamente de la misma forma que la pestaña **Incluir**. Es posible ver esta pestaña, pero NO seleccione ninguna aplicación en la nube para su exclusión. 

20. Por último, definirá el requisito de MFA para todas las ubicaciones de inicio de sesión de usuario. En algunos escenarios, las organizaciones podrían requerir MFA solamente si un usuario iniciase sesión desde una ubicación que no fuera de confianza. Sin embargo, Adatum desea requerir MFA para todos los usuarios incluidos, independientemente de dónde inicien sesión. <br/>

    En **Condiciones**, seleccione **0 condiciones seleccionadas**. Al hacerlo, se mostrará una lista de posibles condiciones en las que se comprobará la directiva. Para este ejercicio de laboratorio, en la condición **Ubicaciones**, seleccione **Sin configurar**. Al hacerlo, se mostrará un botón de alternancia **Configurar** y dos pestañas: **Incluir** y **Excluir**. Ambas pestañas están deshabilitadas actualmente.

21. Establezca el botón de alternancia **Configurar** en **Sí**, lo que habilitará las dos pestañas. 

22. En la pestaña **Incluir**, compruebe que la opción **Cualquier ubicación** esté seleccionada (selecciónela si fuera necesario). Seleccione la pestaña **Excluir**. Si la organización reconociera direcciones IP específicas o intervalos de direcciones como "de confianza", será posible excluir el requisito de MFA cuando un usuario inicie sesión desde una de esas ubicaciones. Sin embargo, Adatum desea requerir MFA para todos los intentos de inicio de sesión del usuario, independientemente de su ubicación. Esto incluirá inicios de sesión de usuario internos y externos. Compruebe que esté seleccionada la opción **Ubicaciones seleccionadas** y, en la sección **Seleccionar**, compruebe que se indique **Ninguna**. Al no especificar ninguna ubicación seleccionada, esta configuración garantizará que ninguna ubicación se excluya de MFA. 

23. En la sección **Controles de acceso**, en el grupo **Conceder**, seleccione **0 controles seleccionados**. Al hacerlo, se mostrará un panel **Conceder**.

24. En el panel **Conceder** que aparecerá, compruebe que la opción **Conceder acceso** esté seleccionada (selecciónela si fuera necesario). Entonces, seleccione la casilla **Requerir autenticación multifactor**. Observe todos los demás controles de acceso disponibles que se pueden habilitar con esta directiva. Para esta directiva, solo se necesitará MFA. Seleccione el botón **Seleccionar** situado en la parte inferior del panel **Conceder**, el cual que cierra el panel. 

25. **IMPORTANTE:** En este punto, normalmente establecería el campo **Habilitar directiva** en **Activado**. Sin embargo, dado que algunos alumnos podrían tener inquilinos de prueba más antiguos que no requieran MFA, mientras que otros podrían tener los nuevos inquilinos que la requieran, NO habilitará la directiva que acaba de crear. Por lo tanto, establezca el campo **Habilitar directiva** en **Desactivado**.

27. Haga clic en el botón **Crear** para crear la directiva.

28. En la ventana **Acceso condicional | Directivas** que aparece, compruebe que la directiva **MFA para todos los usuarios de Microsoft 365** aparezca y que su **Estado** esté establecido en **Desactivado**.

29. Permanezca conectado a LON-CL1 con todas las pestañas del explorador de Microsoft Edge abiertas para la siguiente tarea.

**Nota:** Según la explicación anterior, no hay ninguna forma de probar la directiva de acceso condicional en caso de tener un inquilino de prueba de Microsoft 365 que requiera MFA. La directiva de acceso condicional de Microsoft requiere MFA para todos los usuarios. Cuando hay varias directivas que requieren MFA, se aplica la directiva más restrictiva. En este caso, la directiva de Microsoft es más restrictiva que la que acaba de crear que incluía excepciones para los miembros del equipo de trabajo piloto, por lo que no habría ninguna manera de probar la directiva. Si el inquilino fuera uno anterior que no requiriese MFA, no lo probará, ya que otros alumnos de la clase podrían tener ya inquilinos que se requieran para el uso de MFA. En lugar de tener que probar su directiva mientras que otros no, se eligió no probarla. Aunque no es posible probar la directiva con este inquilino de prueba, le recomendamos que use esta experiencia de creación de directivas de acceso condicional para requerir MFA en las implementaciones reales de Microsoft 365.


### Tarea 4: Implementación de Smart Lockout de Microsoft Entra

El director de tecnología de Adatum le pidió que implemente Smart Lockout de Microsoft Entra, que ayuda a bloquear a los actores malintencionados que intenten adivinar las contraseñas de los usuarios o usar métodos de fuerza bruta para ser admitidos en la red. Smart Lockout puede reconocer los inicios de sesión que procedan de usuarios válidos y tratarlos de forma distinta a los que provengan de atacantes y otros orígenes desconocidos. 

El director de tecnología está ansioso por implementar Smart Lockout porque bloqueará a los atacantes y permitirá al mismo tiempo que los usuarios de Adatum sigan accediendo a sus cuentas y sean productivos. El director de tecnología pidió a Holly que configure Smart Lockout para que los usuarios no puedan usar la misma contraseña más de una vez y no puedan usar contraseñas que se consideren demasiado sencillas o comunes. 

**Nota:** Es posible mantener la configuración de la directiva de bloqueo de cuenta en el Editor de administración de directivas de grupo y en Microsoft Entra a través de su característica Smart Lockout. Esta tarea de laboratorio muestra cómo acceder a cada método, aunque solo actualizará la configuración de Smart Lockout en Microsoft Entra. Es necesario usar el controlador de dominio de la empresa (LON-DC1) para acceder al Editor de administración de directivas de grupo. 

1. En las tareas anteriores, trabajó con LON-CL1. En esta tarea, trabajará desde el controlador de dominio de Adatum, LON-DC1. <br/>

    Cambiar a **LON-DC1**.

2. En **LON-DC1**, es necesario seleccionar **Ctrl+Alt+Eliminar** para iniciar sesión (el instructor le guiará sobre cómo encontrar esta opción en el entorno de la máquina virtual). Inicie sesión en LON-DC1 como la cuenta de administrador de Adatum local que creó el proveedor de hospedaje del laboratorio (**Administrador**) con la contraseña **Pa55w.rd**.

3. En LON-DC1, el **Administrador del servidor** se iniciará automáticamente en el arranque. En **Administrador del servidor**, seleccione **Herramientas** en la barra de menús superior derecha y, en el menú desplegable, seleccione **Administración de directivas de grupo.** Maximice la ventana **Administración de directivas de grupo** que aparece.

4. Desea editar la directiva de grupo que incluye la directiva de bloqueo de cuentas de la organización. Si fuera necesario, en el árbol de consola raíz del panel lateral, expanda **Forest:Adatum.com**, expanda **Dominios** y, a continuación, expanda **Adatum.com**.  <br/>

    ‎En **Adatum.com**, haga clic con el botón derecho en **Directiva de dominio predeterminada** y, a continuación, seleccione **Editar** en el menú.

5. Maximice la ventana **Editor de administración de directivas de grupo** que aparece.

6. En el árbol **Directiva de dominio predeterminada** del panel lateral, en **Configuración del equipo**, expanda **Directivas**, expanda **Configuración de Windows**, expanda **Configuración de seguridad** y, a continuación, expanda **Directivas de cuenta.**

7. En la carpeta **Directivas de cuenta**, seleccione **Directiva de bloqueo de cuenta**.

8. Como puede ver en el panel que aparece, no se ha definido ninguno de los parámetros de bloqueo inteligente. En lugar de mantener estos parámetros de bloqueo en el Editor de administración de directivas de grupo, en su lugar usará el Centro de administración de Microsoft Entra. Aunque es posible usar el Editor de administración de directivas de grupo, este método se usa normalmente en entornos de Active Directory local. Le mostramos este editor para que pudiera ver esta alternativa. Sin embargo, para las organizaciones que usen estrictamente servicios basados en la nube, como Microsoft 365, o que encuentren el uso del Centro de administración de Microsoft Entra mucho más sencillo que acceder al Editor de administración de directivas de grupo, es preferible usar el **Centro de administración de Microsoft Entra** para asignar los valores correspondientes en el contexto de Entra ID. <br/>  

    Tenga en cuenta también que el comportamiento de bloqueo y las opciones de personalización difieren entre los dos métodos. Con el Editor de administración de directivas de grupo, se tiene un control más granular sobre la configuración de directivas, incluyendo el umbral de bloqueo de cuentas, la duración del bloqueo y el restablecimiento del contador de bloqueo de cuentas después. Sin embargo, el uso de este método requiere conocimientos sobre directivas de grupo y la administración de Active Directory. Por el contrario, la directiva de bloqueo de cuentas de Microsoft Entra no se puede personalizar tan extensamente. Sin embargo, es más fácil de usar, aunque carece de algunas de las opciones de ajuste disponibles en la directiva de grupo. <br/>

    Para Adatum, Holly eligió usar el Centro de administración de Microsoft Entra para configurar la directiva de bloqueo de cuentas de la empresa. En la barra de tareas de la parte inferior de la pantalla, seleccione el icono de **Microsoft Edge**. Si fuera necesario, maximice la ventana del explorador cuando se abra.

9. En el explorador Edge, vaya a la página **Inicio de Microsoft 365**. Para ello, escriba esta dirección URL en la barra de direcciones: **https://portal.office.com** 

10. En el cuadro de diálogo **Iniciar sesión**, inicie sesión como Holly Dickson. Escriba **Holly@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino asignado por el proveedor de hospedaje del laboratorio). Seleccione **Siguiente**. <br/>

11. En el cuadro de diálogo **Escribir contraseña**, escriba la **Contraseña administrativa** única proporcionada por el proveedor de hospedaje del laboratorio y, a continuación, seleccione **Iniciar sesión**. Si fuera necesario, complete el proceso de inicio de sesión de MFA.

12. En el cuadro de diálogo **¿Mantener la sesión iniciada?**, active la casilla **No volver a mostrar esto** y, a continuación, seleccione **Sí**. En el cuadro de diálogo **Guardar contraseña** que aparece, seleccione **Nunca**.

13. Si aparece un cuadro de diálogo **Le damos la bienvenida a Microsoft 365** en medio de la pantalla, tenga en cuenta que no hay ninguna opción para cerrarlo. En su lugar, a la derecha de la ventana, seleccione el icono de flecha hacia delante (**>**) dos veces y, a continuación, seleccione el icono de marca de verificación para avanzar a través de las diapositivas de esta ventana de mensajes. 

14. Si apareciera una ventana **Buscar más aplicaciones** o **Crear con Microsoft 365**, seleccione la **X** de la esquina superior de la ventana para cerrarla. 

15. En la página **Le damos la bienvenida a Microsoft 365**, en la lista de iconos de aplicación que aparecen en el panel de la ventana lateral, seleccione **Administrador**. Esto abrirá el **Centro de administración de Microsoft 365** en una nueva pestaña del explorador. 

16. En el **Centro de administración de Microsoft 365**, seleccione **...Mostrar todo** en el panel de navegación. En **Centros de administración**, seleccione **Identidad**, que mostrará el **Centro de administración de Microsoft Entra** en una nueva pestaña.

17. En el **Centro de administración de Microsoft Entra**, seleccione **Protección** en el panel de navegación y, a continuación, seleccione **Métodos de autenticación**.

18. En la página **Métodos de autenticación | Directivas**, en el panel central, en la sección **Administrar**, seleccione **Protección de contraseñas.**

19. En la ventana **Métodos de autenticación | Protección de contraseñas**, en el panel de detalles de la derecha, escriba la siguiente información:

    - En la sección **Smart Lockout personalizado**:

        - **Umbral de bloqueo:** este campo indica el número de inicios de sesión con error permitidos en una cuenta antes de su primer bloqueo. El valor predeterminado es 10. Con fines de prueba, Adatum ha solicitado que establezca esto en **3**.

        - **Duración del bloqueo en segundos:** Esta es la duración en segundos de cada bloqueo. El valor predeterminado es 60 segundos (un minuto). Adatum ha solicitado que cambie esto a **90** segundos.

    - En la sección **Contraseñas prohibidas personalizadas**:

        - **Exigir lista personalizada**: seleccione **Sí**

        - **Lista de contraseñas prohibidas personalizadas:** Escriba los valores siguientes (presione Entrar después de escribir cada valor para que cada valor esté en una línea independiente):

            - **Password01**

            - **F00tball01**

            - **Se@Hawks1**

            - **Never4get!!**

    - En la sección **Modo**, seleccione **Aplicado**

20. En la barra de menús de la parte superior de la página, seleccione **Guardar**.

21. Ahora debería probar la funcionalidad de contraseña prohibida. Seleccione el icono de usuario de Holly Dickson de la esquina superior derecha de la pantalla y, en el menú que aparece, seleccione **Ver cuenta**. 

22. En la ventana **Mi cuenta** que aparece, en el icono **Contraseña**, seleccione **CAMBIAR CONTRASEÑA**.

23. Se abrirá una nueva pestaña en la que se mostrará la ventana **Cambiar contraseña**. En el campo **Contraseña antigua**, escriba la contraseña existente de Holly, que será la misma **Contraseña administrativa** proporcionada por el proveedor de hospedaje del laboratorio para la cuenta de administrador del inquilino (es decir, la cuenta de administrador de MOD). <br/>

    Escriba **Never4get!!** en los campos **Crear nueva contraseña** y **Confirmar nueva contraseña** y, a continuación, seleccione **Enviar**. Observe el mensaje de error que reciba.

24. En el explorador, cierre la pestaña **Cambiar contraseña**. 

25. Ahora debería probar la funcionalidad de umbral de bloqueo. Seleccione el icono de usuario de Holly Dickson de la esquina superior derecha de la pantalla y, en el menú que aparece, seleccione **Cerrar sesión**.  

26. Una vez que haya cerrado la sesión como Holly, aparecerá la ventana **Seleccionar una cuenta** en la pestaña **Inicio de sesión en Microsoft Entra**. Como procedimiento recomendado al cerrar sesión desde un servicio en línea de Microsoft como un usuario y volver a iniciar sesión como otro, cierre todas las pestañas del explorador, excepto **Cerrar sesión** o **Iniciar sesión**. En este caso, cierre las demás pestañas ahora y deje abierta la pestaña **Iniciar sesión**.  <br/>

    En la ventana **Elegir una cuenta**, seleccione **Usar otra cuenta**. 

27. En la ventana **Iniciar sesión**, iniciará sesión como Patti Fernandez. Escriba **pattif@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo del inquilino asignado a usted por el proveedor de hospedaje del laboratorio) y, a continuación, seleccione **Siguiente**. 

28. En la ventana **Escribir contraseña**, escriba cualquier combinación aleatoria de letras y números y, a continuación, seleccione **Iniciar sesión**. Observe el mensaje de error de contraseña no válida que aparece. 

    Repita este paso 2 veces más. 
    
    Como estableció el **Umbral de bloqueo** en **3**, debería recibir un mensaje de error indicando que esta cuenta está bloqueada después del tercer intento erróneo de inicio de sesión. <br/>

    **Nota:** Si no recibiera este mensaje de bloqueo después del tercer intento, el sistema aún no habrá terminado de propagar este cambio de umbral de bloqueo a lo largo del servicio. Es posible que el cambio tarde varios minutos en aplicarse. Espere unos minutos y vuelva a iniciar sesión con una contraseña ficticia. Las pruebas de este laboratorio mostraron resultados variables. El cambio a veces se propaga casi inmediatamente para que se produzca el bloqueo después del tercer intento de inicio de sesión. Otras veces pasaron entre 5 y 10 minutos antes de mostrar el mensaje de bloqueo. Continúe este proceso hasta recibir el mensaje de bloqueo, momento en el que la cuenta de Patti se bloqueará temporalmente para evitar el acceso no autorizado.

29. Se le impedirá iniciar sesión de nuevo como Patti hasta que pase la **duración del bloqueo de 90 segundos** que estableció anteriormente. <br/>

    Una vez que se produzca el bloqueo, espere 90 segundos y vuelva a iniciar sesión como **pattif@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino asignado a usted por el proveedor de hospedaje del laboratorio). En el campo **Contraseña**, escriba la contraseña de Patti, que es la **Contraseña de usuario** proporcionada por el proveedor de hospedaje del laboratorio. Si fuera necesario, complete el proceso de inicio de sesión de MFA. Compruebe que pueda iniciar sesión correctamente como Patti.

30. Una vez que el inicio de sesión se haya realizado correctamente, cierre todas las aplicaciones abiertas. Este será el último ejercicio del laboratorio con el controlador de dominio LON-DC1.
 
# Continuar con el laboratorio 2: ejercicio 2
