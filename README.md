# Fundamentos de Git
Hola👋 Aqui dejare mis apuntes sobre Git del Curso Profesional Git y Github Platzi.
Tambien subire datos, consejos o tips sobre git y el flujo de trabajo con git.

Para clonarlo puedes seguir estos comandos 👇👇👇
 En Consola GIT BASH: 
- git init (para inicializar una carpeta en git)
- git remote add origin https://github.com/marina-baiardi/Fundamentos-de-Git.git (copiar link https de clone)
- git remote -v (asi puedes checkear si esta vinculado correctamente)

# Consejos para un flujo de trabajo ordenado y profesional
Para poder desarrollar software de manera óptima y ordenada, necesitamos tener un flujo de trabajo profesional, que nos permita trabajar en conjunto sin interrumpir el trabajo de otros desarrolladores. Una buena práctica de flujo de trabajo sería la siguiente:

- Crear ramas
- Asignar una rama a cada programador
- El programador baja el repositorio con git pull origin master
- El programador cambia de rama
- El programador trabaja en esa rama y hace commits
- El programador sube su trabajo con git push origin #nombre_rama
- El encargado de organizar el proyecto baja, revisa y unifica todos los cambios

# Flujo de trabajo profesional con pull request
En un entorno profesional normalmente se bloquea la rama master, y para enviar código a dicha rama pasa por un code review y luego de su aprobación se unen códigos con los llamados merge request.

Para realizar pruebas enviamos el código a servidores que normalmente los llamamos staging develop (servidores de pruebas) luego de que se realizan las pruebas pertinentes tanto de código como de la aplicación estos pasan al servidor de producción con el ya antes mencionado merge request.

Los PR (pull requests) son la base de la colaboración a proyectos Open Source, si tienen pensando colaborar en alguno es muy importante entender esto y ver cómo se hace en las próximas clases. Por lo general es forkear el proyecto, implementar el cambio en una nueva rama, hacer el PR y esperar que los administradores del proyecto hagan el merge o pidan algún cambio en el código o commits que hiciste.

# Proceso de un pull request para trabajo en producción:
- Un pull request es un estado intermedio antes de enviar el merge.
- El pull request permite que otros miembros del equipo revisen el código y así aprobar el merge a la rama.
- Permite a las personas que no forman el equipo, trabajar y colaborar con una rama.
- La persona que tiene la responsabilidad de aceptar los pull request y hacer los merge tienen un perfil especial y son llamados DevOps

NOTA: En Gitlab esto se le llama "Merge request" y en Bitbucket "Push request".

# Cómo se realiza un pull request
- Se trabaja en una rama paralela los cambios que se desean git checkout -b <rama>.
- Se hace un commit a la rama git commit -am '<Comentario>'.
- Se suben al remoto los cambios git push origin <rama>.
- En GitHub se hace el pull request comparando la rama master con la rama del fix.
-Uno, o varios colaboradores revisan que el código sea correcto y dan feedback (en el chat del pull request).
- El colaborador hace los cambios que desea en la rama y lo vuelve a subir al remoto (automáticamente jala la historia de los cambios que se hagan en la rama, en remoto).
- Se aceptan los cambios en GitHub.
- Se hace merge a master desde GitHub.
 
IMPORTANTE: Cuando se modifica una rama, también se modifica el pull request.

# Funcionalidad Fork en Github
Los forks o bifurcaciones son una característica única de GitHub en la que se crea una copia exacta del estado actual de un repositorio directamente en GitHub. Este repositorio podrá servir como otro origen y se podrá clonar (como cualquier otro repositorio). En pocas palabras, lo podremos utilizar como un nuevo repositorio git cualquiera.

Un fork es como una bifurcación del repositorio completo. Comparte una historia en común con el original, pero de repente se bifurca y pueden aparecer varios cambios, ya que ambos proyectos podrán ser modificados en paralelo y para estar al día un colaborador tendrá que estar actualizando su fork con la información del original.

Al hacer un fork de un poryecto en GitHub, te conviertes en dueñ@ del repositorio fork, puedes trabajar en este con todos los permisos, pero es un repositorio completamente diferente que el original, teniendo solamente alguna historia en común (como crédito al creado o creadora original).

Los forks son importantes porque es la manera en la que funciona el open source, ya que, una persona puede no ser colaborador de un proyecto, pero puede contribuír al mismo, haciendo mejor software que pueda ser utilizado por cualquiera.

# Cómo se hace un fork remoto desde consola en GitHub
Al hacer un fork, GitHub sabe que se hizo el fork del proyecto, por lo que se le permite al colaborador hacer pull request desde su repositorio propio.

Cuando trabajas en un proyecto que existe en diferentes repositorios remotos (normalmente a causa de un fork), es muy probable que desees poder trabajar con ambos repositorios. Para esto, puedes generar un remoto adicional desde consola:
- git remote add <nombre_del_remoto> <url_del_remoto> 
- git remote upstream https://github.com/marina-baiardi/Fundamentos-de-Git.git

Al crear un remoto adicional, podremos hacer pull desde el nuevo origen. En caso de tener permisos, podremos hacer fetch y push:
- git pull <remoto> <rama>
- git pull upstream master

Este pull nos traerá los cambios del remoto, por lo que se estará al día en el proyecto. El flujo de trabajo cambia, en adelante se estará trabajando haciendo pull desde el upstream y push al origin para pasar a hacer pull request:
- git pull upstream master
- git push origin master

# Haciendo deployment a un servidor
Deploy es el proceso que permite enviar al servidor uno o varios archivos. Este servidor puede ser de prueba, desarrollo o producción.

En el siguiente ejemplo veremos cómo se realiza el deployment de un documento en un servidor web básico.

# Pasos para hacer deployment en un servidor web:
- Entrar a la carpeta de los archivos del servidor.
- Copiar link en clone, elegir entre HTTPS o SSH del repositorio a contribuir.
- En la carpeta deseada se clona el repositorio:
  - git clone url
    Deploy:
- Realizar cambios y commit en GitHub.
- Traer al Repositorio local las actualizacion para el servidor en la capeta de los archivos del servidor:
  - git pull ramaRemota main
  
Nota: Siempre se debe proteger el archivo .git. Dependiendo del software para el servidor web, existen diferentes maneras. La conexión entre GitHub y el servidor se puede realizar mediante: Travis (pago) o Jenkis (Open source).

# Ignorar archivos en el repositorio con .gitignore
No todos los archivos que agregas a un proyecto deberían ir a un repositorio. Por ejemplo, cuando tienes un archivo donde están tus contraseñas que comúnmente tienen la extensión .env o cuando te estás conectando a una base de datos; son archivos que nadie debe ver.

Por diversas razones, no todos los archivos que agregas a un proyecto deberían guardarse en un repositorio. Esto es porque hay archivos que no todo el mundo debería de ver, y hay archivos que al estar en el repositorio ralentizan el proceso de desarrollo (por ejemplo: los binary large objects, blob, que tardan en descargarse).

Para que no se suban estos archivos no deseados se puede crear un archivo con el nombre .gitignore en la raíz del repositorio con las reglas para los archivos que no se deberían subir: Aquí puedes ver la sintaxis de los .gitignore.

Las razones principales para tomar la decisión de no agregar un archivo a un repositorio son:
- Es un archivo con contraseñas (normalmente con la extensión .env)
- Es un blob (binary large object, objeto binario grande), mismos que son difíciles de gestionar en git.
- Son archivos que se generan corriendo comandos, por ejemplo la carpeta node_modules, que genera npm al correr el comando npm install

# Pasos para subir un repositorio a GitHub Pages
- Debemos tomar la llave SSH y hacer un git clone #SSHexample en mi computador local (Home).
- Luego, accederemos a la carpeta nueva que aparece en nuestra máquina local.
- Creamos un nuevo archivo que se llame index.html
- Guardamos los cambios, hacemos un git pull y seguido de esto un git push a master.
- Vamos a las opciones de settings de este repositorio y, en la parte de abajo, en la columna Github Pages, configuramos el source o fuente para que traiga la rama master
- Guardamos los cambios.

Después de esto, podremos ver nuestro trabajo en la web como si tuviéramos nuestro propio servidor.

# A continuación veremos una lista de comandos colaborativos para facilitar el trabajo remoto en GitHub:

- git shortlog -sn: muestra cuantos commit han hecho cada miembro del equipo.
- git shortlog -sn --all: muestra cuantos commit han hecho cada miembro del equipo, hasta los que han sido eliminados.
- git shortlog -sn --all --no-merge: muestra cuantos commit ha hecho cada miembro, quitando los eliminados sin los merges.
- git blame ARCHIVO: muestra quien hizo cada cosa línea por línea.
- git COMANDO --help:muestra como funciona el comando.
- git blame ARCHIVO -Llinea_inicial,linea_final: muestra quien hizo cada cosa línea por línea, indicándole desde qué línea ver. Ejemplo -L35,50.
- git branch -r: se muestran todas las ramas remotas.
- git branch -a: se muestran todas las ramas, tanto locales como remotas.
