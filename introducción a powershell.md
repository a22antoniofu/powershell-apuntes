# Sintaxis
Se intenta que se siga una estructura típica en MarkDown.
Los comentarios (# en scripts) se tratarán aquí como // para evitar conflictos con los encabezados.

# Introducción a PowerShell 
Windows PowerShell es una interfaz de consola (Command-Line Interface, CLI) con posibilidad
de escritura y unión de comandos por medio de instrucciones (scripts). Es un CLI mucho más
rico que DOS. Esta interfaz de consola está diseñada para su uso por parte de administradores
de sistemas, con el propósito de automatizar tareas o realizarlas de forma más controlada.
Originalmente denominada como MONAD en 2003, su nombre oficial cambió al actual cuando
fue lanzada al público el 25 de abril de 2006. 

## Versiones de Powershell 
• PowerShell 1.0 : PowerShell 1.0 fue liberado en 2006 para el Windows XP SP2,
Windows Server 2003 y Windows Vista. Es un componente opcional para Windows
Server 2008. 
• PowerShell 2.0 : PowerShell 2.0 está integrado con Windows 7 y Windows Server
2008 R2 y es liberado para Windows XP con Service Pack 3, Windows Server 2003 con
Service Pack 2 y Windows Vista con Service Pack 1. 
◦ PowerShell V2 incluye cambios del lenguaje de scripting y la API del equipo,
añadiendo unos 240 cmdlets. 
◦ Windows PowerShell ISE v2.0, es un entorno de desarrollo para scripts
PowerShell, está integrado en el Windows 7 y en el Windows Server 2008 R2 y es
liberado para Windows XP con Service Pack 3, Windows Server 2003 con Service
Pack 2 y Windows Vista con Service Pack 1. 
• PowerShell 3.0 : PowerShell 3.0 está integrado en el Windows 8 y en el Windows
Server 2012. Microsoft también hizo PowerShell 3.0 posible para Windows 7 con Service
Pack 1, para Windows Server 2008 con Service Pack 1 y para Windows Server 2008 R2
con Service Pack 1. 
◦ PowerShell 3.0 es una parte de un paquete mucho más grande, Windows
Management Framework 3.0 (WMF3), que también contiene el servicio WinRM. 
• PowerShell 4.0 : PowerShell 4.0 está integrado con Windows 8.1 y con Windows
Server 2012 R2. Microsoft también hizo posible PowerShell 4.0 para Windows 7 SP1,
Windows Server 2008 R2 SP1 y Windows Server 2012. 
• PowerShell 5.0 : La revisión previa del PowerShell 5.0 estuvo disponible con Windows
Management Framework 5.0 (WMF5) en Abril de 2014. 
◦ Una de las novedades que introduce es OneGet PowerShell cmdlets para soportar el
manejo de paquetes del repositorio Chocolatey. 
◦ En Agosto de 2015 Microsoft se libera la última actualización de PowerShell 5.0. 
◦ Windows 10 ya lo trae integrado. 
• PowerShell 5.1 : Aparece con la Versión 1607 de Windows 10 (Anniversary Update) y
en Windows 2016. 
◦ Windows 11 y Windows Server 2022 ya lo traen integrado. 
• PowerShell Core 6.0, 6.1 y 6.2 : Anunciada en Agosto de 2016. 
◦ PowerShell Core es un PowerShell más pequeño que el PowerShell convencional y
puede instalarse en sistemas operativos: MacOS y Linux, también en Windows. 
◦ Con PowerShell Core, podremos administrar y ejecutar los mismos scripts sobre los
tres tipos de sistemas operativos: Windows MacOS y Linux como si fueran uno solo.
 
• PowerShell 7 : Será la próxima versión de PowerShell. 
◦ Reemplazará al PowerShell Core 6.x y a Windows PowerShell 5.1. 

Ya lanzado, ver [https://learn.microsoft.com/es-es/shows/it-ops-talk/how-to-install-powershell-7](Microsoft Learn)

## La sintaxis de Windows Powershell
El lenguaje PowerShell está formado por comandos que se denominan cmdlets. Se trata de
comandos descritos con la forma de un verbo y, a continuación, un sustantivo, separados por
un guión. Para hacerse una idea, algunos cmdlets pueden ser los siguientes:
• New-Item : Crear (New) un nuevo objeto (Item).
• Get-Service : Obtener (Get) información vinculada a los servicios (Service) de
Windows.
• Set-ExecutionPolicy : Definir (Set) la política de ejecución (ExecutionPolicy) de los
scripts en PowerShell.

## Ejecutar Windows PowerShell 
Un modo rápido de ejecutar PowerShell es pulsar la Tecla de Windows + R para que se
ejecute "Ejecutar", escribir PowerShell y pulsar Enter. 
Al ejecutarlo así, en un sistema Windows Cliente, lo haremos sin privilegios, por lo que NO será
posible realizar tareas de administración, como crear particiones, formatearlas, instalar
software, etc. 
Para ejecutar Windows PowerShell como Administrador, lo podemos realizar de varios
modos:
• Crear un Acceso directo especial: Se crea un acceso directo en el escritorio. Donde
pone "Escriba la localización del elemento" escribimos simplemente "PowerShell" y
pulsamos en "Siguiente". Luego le damos un nombre para este acceso directo como,
por ejemplo: "PowerShell como Administrador". Luego, una vez creado el acceso
directo, hacemos click con el botón derecho sobre él y, en la ficha "Acceso directo"
pulsamos en el botón "Opciones avanzadas…", nos aparece una ventana en la que
tendremos que seleccionar
la casilla de verificación
"Ejecutar como
administrador". Luego
pulsamos en aceptar y ya
tendremos preparado el
acceso directo para
ejecutar en cualquier
momento PowerShell con
privilegios de
Administrador, siempre
que nuestro usuario pueda
realizarlo o tengamos
acceso a un
usuario/contraseña que
tenga esos privilegios.

### Ejecutar Powershell como administrador desde línea de comandos: 

Para realizar esta tarea se utiliza el cmdlet Start-Process. 
→ Para Abrir PowerShell como Administrador utilizamos el comando:
PS> Start-Process Powershell -Verb RunAs
 Para ejecutar un → script de PowerShell como Administrador: 
PS> Start-Process Powershell -Verb RunAs -ArgumentList "-file c:\scripts\cambionome.ps1" 
Para conocer la versión de PowerShell instalada en nuestro equipo utilizamos el cmdlet
Get-Host. 

### Otros modos de conocer la versión de PowerShell
instalada en nuestra versión de Windows es accediendo
a las variables globales:
PS> $PSVersionTable
PS> $Host

## Descubrir los cmdlets existentes
Existen muchísimos cmdlets y, en cada versión de Windows
PowerShell se incorporan nuevos, igual que se incorporan
nuevos al instalar aplicaciones y servicios a nuestro equipo. 
Para hacerse una idea de los cmdlets existentes en nuestro
puesto de trabajo, utilizaremos el comando:
PS> Get-Command
Y, para conocer, exactamente el número exacto:
PS> (Get-Command).Count
Los comandos NO son sensibles a mayúsculas/minúsculas.

### Algo más de info
Como vemos, en powershell todo es un objeto que tiene sus propiedades y sus métodos. Así, si usamos (Get-Command).count, nos cuenta la cantidad de CMDLets que tenemos instalados.
Ojo con los paréntesis. Se utilizan para decirle que ejecute get-command, lo tome como un objeto para posteriormente hacer la cuenta de elementos en la lista.

## Configurar la ejecución de scripts de PowerShell
Para configurar en Windows la ejecución de scripts PowerShell, antes de nada debemos saber
que:
• Los scripts de PowerShell son archivos de texto guardados con extensión .PS1 .
• Para crearlos podemos emplear el propio Notepad u otro editor de texto cualquiera o,
mejor, el software PowerShell ISE que se encuentra ya instalado en los sistemas
operativos Windows actuales. También existen herramientas de terceros como
PowerGUI y, como no, podemos utilizar Visual Studio Code con la extensión adecuada.
• Por defecto, para mejorar la seguridad, estos archivos los abre el Notepad por lo que,
si hacemos doble click en uno, o hacemos que se ejecute automáticamente al iniciar el
equipo, lo único que ocurre es que se "abren" sin más (se ve su contenido). Si nos
interesa, podemos configurar el Sistema Operativo Windows para que los archivos con
extensión .ps1 se ejecuten todos por defecto con el programa Powershell.exe.
• Además, muchos de los scripts que vamos a programar, para que hagan la tarea para lo
que están programados, tendremos que ejecutarlos con permisos de Administrador.
Para que esta tarea no pida confirmación, hay que bajar el nivel de “Notificación acerca
de cambios en el equipo”, o UAC (Control de Cuentas de Usuario). 
• Por último, hay que cambiar la preferencia del usuario para la Directiva de Ejecución de
Windows PowerShell, ejecutando el comando Set-ExecutionPolicy.
→ Para ver la Preferencia actual para la directiva de ejecución de Windows PowerShell
(Fijarse lo que implica la preferencia configurada) :
PS> Get-ExecutionPolicy
→ Para cambiar la Preferencia a RemoteSigned:
PS> Set-ExecutionPolicy RemoteSigned
• También se puede ajustar cómo el PowerShell se comporta cuando se produce un error
cuando se ejecuta código o scripts. Para ver el modo actual emplearemos la variable
ErrorActionPreference:
PS> $ErrorActionPreference
Continue
• El modo por defecto vemos que es Continue que muestra los errores y continúa con la
ejecución. Si queremos que no muestre los errores y que siga con la ejecución
tendríamos que configurarlo en SilentlyContinue.
PS> $ErrorActionPreference = "SilentlyContinue"

### Información útil
Ise no es accesible, se prefiere usar VSCode con la extensión Powershell, creada por la propia Microsoft.

## Mini-Introducción a la consola de PowerShell
Realizar las siguientes tareas para una primera aproximación al manejo de la consola
PowerShell (a partir de ahora PS === PowerShell):
• Ejecutar PS como un usuario normal
• Ejecutar PS como administrador:
PS> Start-Process Powershell -Verb RunAs

### Información útil
Windows + x es tu amigo, permite ejecutar powershell con privilegios normales (tecla rápida i) y administrativos (tecla rápida a).

• Comprobar la versión de PS que estamos utilizando
PS> Get-Host
• Configurar el equipo para ejecutar scripts de PS realizados por nosotros y bajados 
firmados:
PS> Get-ExecutionPolicy
- Restricted - AllSigned
- RemoteSigned - Unrestricted
PS> Set-ExecutionPolicy RemoteSigned
• Recordar el formato que tienen los nuevos cmdlets de PS.
• Ejemplo típico con un cmdlet como G et-D ate:
#Actualizar la ayuda
PS> Update-Help
#Pedir Fecha y hora actual
PS> Get-Date
#Pedir Ayuda del comando Get-Date → Analizar parámetros ‘-full’ y ‘-online’
PS> Get-Help Get-Date

// Pedir en formato lista todos los datos devueltos por el comando Get-Date
PS> Get-Date | fl *
// Pedir en formato tabla solo los datos day,hour,minute,second
PS> Get-Date | ft day,hour,minute,second
// Guardar en la variable $fecha la salida del comando Get-Date
PS> $fecha = Get-Date
// Ver el tipo de variable que es $fecha.
PS> $fecha.GetType()
// Centrarse en el valor de ‘Name’
PS> $fecha.GetType().Name
// Ver los datos guardados en la variable $fecha
PS> $fecha
// Verlos en formato lista
PS> $fecha | fl
// Descubrir todas las Propiedades y Métodos de ese ‘objeto’ $fecha
PS> $fecha | Get-Member
// Centrarnos sólo en las Propiedades
PS> $fecha | Get-Member -MemberType Property
// Descubrir de todas las propiedades el valor de la propiedad ‘Date’
PS> $fecha.Date
// Centrarnos sólo en los Métodos
PS> $fecha | Get-Member -MemberType Method
// Crear una fecha nueva que sean 10 días después de la variable $fecha
PS> $fechaNueva = $fecha.AddDays(10)
// Ver que, efectivamente, es la misma pero 10 días después
PS> $fechaNueva.Date
// Ver que volvemos a recuperar esos 10 días...
PS> ($fechaNueva - $fecha).TotalDays
• Ver de qué comandos disponemos para trabajar:
// Ver todos los cmdlets instalados en nuestro equipo
PS> Get-Command
// Para ver todos esos comandos página a página
PS> Get-Command | Out-Host -Paging
// Aunque también funciona
PS> Get-Command | more
// Número de cmdlets existentes
PS> (Get-Commad).Count
// Cmdlets en cuyo nombre aparece la palabra ‘date’
PS> Get-Command -Noun “*date*”
// Todos los cmdlets que tienen de acción ‘get’
PS> Get-Command -Verb ‘get’ | more
// Todos los Alias de cmdlets configurados hasta este momento
PS> Get-Alias | more
//Alias del comando ‘rm’
PS> Get-alias -Name rm
// Todos los alias en cuyo nombre existe una ‘m’
PS> get-alias | where {$_.Name -Like "*m*"}
// El alias del comando utilizado antes ‘where’
PS> Get-Alias -Name where
• Instalar nuevos módulos de PowerShell :
#Instalar módulo PSWindowsUpdate (como Administrador)
PS> Install-Module -Name PSWindowsUpdate
// Cargar un módulo ya instalado
PS> Import-Module PSWindowsUpdate
// Descubrir los comandos instalados con ese nuevo módulo
PS> Get-Command -Module PSWindowsUpdate
// Listar la lista de todas las actualizaciones de Windows
PS> Get-WindowsUpdate
// Ver si alguna de estas actualizaciones necesita reinicio del sistema
PS> Get-WURebootStatus
// Descargar e instalar todas las actualizaciones de Windows Update
PS> Install-WindowsUpdate -AcceptAll -AutoReboot
// Ver el historial de actualizaciones de Windows
PS> Get-WUHistory
// Desinstalar una actualización de Windows
PS> Remove-WindowsUpdate -KBArticleID KB2267602

// Instalar software en Windows
→ Acceder a la web de Chocolatey e instalarlo 
// Ayuda
$ choco /?
// Buscar el paquete a instalar en la web y de ahí el comando
$ choco install firefox
• Información del sistema :
// Ver contenido unidad env: (Environment)
PS> Get-ChildItem env:
// Descubrir el nombre del equipo
PS> $env:computername
// Descubrir nombre del usuario que ejecuta el terminal
PS> $env:username
// Path por defecto de la carpeta de usuario, home en linux, vaya
PS> $env:userprofile
// Descubrir todas las clases WMI
PS> Get-WmiObject -List
// Sólo las que tienen en su nombre la palabra “computer”
PS> Get-WmiObject -List | where { $_.Name -like "*computer*" }
// Ver la información devuelta por la API WMI “Win32_ComputerSystem
PS> Get-WmiObject -Class Win32_ComputerSystem
// Otros comandos:
// Apagar el equipo
PS> Stop-Computer
// Reiniciar el equipo
PS> Restart-computer
• Historial de comandos:
// Ver el historial de comandos
PS> Get-History
// → Ctrl+R y buscar coincidencia de comando 
// → Ctrl+R y Ctrl+S para moverse
// Borrar el Historial de comandos
PS> Clear-History
