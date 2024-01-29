# Proyecto ASP.NET Angular

---

[//]: # "version: 1.0"
[//]: # "author: Juan Sebastián López Ruiz"
[//]: # "date: 29-01-2024"

# Tabla de contenidos

- [Proyecto ASP.NET Angular](#Proyecto-ASP.NET-Angular)
- [Tabla de contenidos](#tabla-de-contenidos)

  - [Introducción](#introducción)
  - [Instalación](#instalación)

    - [Instalar NODE.JS](#instalar-node-js)
    - [Instalar MYSQL](#instalar-mysql)
    - [Instalar .NET](#instalar-.net)
    - [Instalar Angular](#instalar-angular)
    - [Instalar Visual Studio Code](#instalar-visual-studio-code)

  - [MySQL](#instalar-mysql)

  - [Angular](#angular)
  - [.NET](#net)

<div style="page-break-after: always;"></div>

---

## Introducción

[Tabla de contenidos](#tabla-de-contenidos)

Este proyecto es una aplicación web desarrollada utilizando ASP.NET y Angular. Combina la potencia del backend de ASP.NET con la flexibilidad y la capacidad de respuesta del framework de frontend Angular.

1. El objetivo de este proyecto:

- Crear una aplicación web donde realizar un CRUD normal y general permitiendo leer, eliminar, añadir, y actualizar directamente en la base de datos
- Ha sido montado en SLQ SERVER.

2. Las caracteristicas de usar estas tecnologías son:

- Integración de ASP.NET y Angular para aprovechar las fortalezas de ambos frameworks.
- Diseño modular y componentizado para facilitar el desarrollo y el mantenimiento.
- Uso de servicios RESTful para la comunicación entre el frontend y el backend.
- Pruebas unitarias y de integración para asegurar la calidad del código.

3. Por ultimo, pero no menos importante, para describir estas tecnologías:

- ASP.NET: Framework de desarrollo web de Microsoft.
- Angular: Framework de desarrollo de aplicaciones web de Google.
- C#: Lenguaje de programación utilizado en el backend.
- TypeScript: Lenguaje de programación utilizado en el frontend.
- HTML/CSS: Lenguajes de marcado utilizados para la estructura y el estilo de la interfaz de usuario.

- ## URL
  -

<div style="page-break-after: always;"></div>

## Instalación

###

[Tabla de contenidos](#tabla-de-contenidos)

```console
# ...
```

## Decidir que Sistema Operativo usaremos

Esto es una decisión muy importante porque como se comprobará en este MarkDown utilizar Linux facilita muchisimo las cosas.

- Utilizar la consola de comandos para todo es extremadamente sencillo.

<div style="page-break-after: always;"></div>

### Instalar MySQL

[Tabla de contenidos](#tabla-de-contenidos)

```console
sudo apt update
sudo apt install mysql-server mysql-client
```

- Ahora toca acceder, pero en primer lugar debemos definir el acceso sin sudo:

```console
sudo mysql -u root -p
```

```sql
use mysql;
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
FLUSH PRIVILEGES;
exit

# NOTA: En caso de ser MariaDB usar:
# ALTER USER 'root'@'localhost' IDENTIFIED BY 'root';
```

- Solo queda reinicirar MySQL y entrar con root/root

```console
sudo service mysql restart
mysql -u root -p
# Y ahora ponemos la conraseña: root
```

<div style="page-break-after: always;"></div>

### Instalación .NET

[Tabla de contenidos](#tabla-de-contenidos)

- Recurso:
  - https://learn.microsoft.com/es-es/dotnet/core/install/linux-ubuntu-2204
- Componentes:
  - 1. SDK (Entorno Desarrollo + Ejecución)
  - 2. CLR (Entorno Ejecución) -> ASP.NET Core

1. Instalamos el SDK

```console
sudo apt-get update
sudo apt-get install -y dotnet-sdk-7.0

# Visualizar las versiones instaladas
dotnet --list-sdks
dotnet --list-runtimes

# Para ver la ayuda del comando:
dotnet --help
```

2. Si luego queremos instalar paquetes adicionales de .NET, lo haremos por consola.

- Por ejemplo Newtonsoft.Json, que es una biblioteca muy popular para trabajar con JSON en .NET

```console
dotnet add package Newtonsoft.Json
```

3. Instalamos Visual Studio Code como IDE

- Dentro, instalamos la extensión C# (el que viene con ese nombre de Microsoft, no el que pone C# Dev Kit)

<div style="page-break-after: always;"></div>

## Intstalar Angular

[Tabla de contenidos](#tabla-de-contenidos)

- Podemos instalar esta capa de Front-end tanto en Linux como en Windows.
- Me he tomado la libertad de tomar este magnifico apartado de nuestro querido profesor ya que la explicación en Linux son estos pasos tal cuales se explican a continuación.

> NOTA: para instalar Angular en Windows se hace a partir del instalador de NodeJS
> El repositorio para todo del 18 es este: https://nodejs.org/download/release/latest-v18.x/
> Windows: https://nodejs.org/download/release/latest-v18.x/node-v18.18.2-x64.msi
> En windows NO hace falta yarn. Una vez instalado NODE, saltar a la sección 3. Instalar cliente Angular

1. Instalar Yarn

```console
curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install yarn
yarn --version
```

2. Instalar NodeJS y NPM

- Recursos:
  - https://github.com/nodesource/distributions#installation-instructions

```console
sudo apt-get update
sudo apt-get install -y ca-certificates curl gnupg
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg

NODE_MAJOR=18
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list

sudo apt-get update
sudo dpkg --remove --force-remove-reinstreq libnode72:amd64
sudo apt-get install nodejs -y
```

> IMPORTANTE: Si hemos instalado una versión incorrecta o queremos otra mas superior, procedemos a desinstalar con lo siguiente:

```console
sudo apt-get purge nodejs
sudo rm -r /etc/apt/sources.list.d/nodesource.list
sudo rm -r /etc/apt/keyrings/nodesource.gpg
```

> IMPORTANTE: EN windows una vez acabada la instalación debemos hacer lo siguiente:
>
> 1. Reiniciar Powershell en modo administrador
> 2. Ejecutar este comando: Set-ExecutionPolicy Unrestricted
> 3. Decir [S] Si
> 4. Volver a reiniciar el powershell

3. Instalar el Cliente de Angular

```console
sudo npm install -g @angular/cli
# Para ver la versión de NPM (la actual es la 7.5.4)
npm -v
# Instalamos el Cliente...
sudo yarn -npm install -g @angular/cli
# Vemos la versión actual
ng version

# Saldrá algo similar a esto...
Global setting: enabled
Local setting: No local workspace configuration file.
Effective status: enabled

     _                      _                 ____ _     ___
    / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
   / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
  / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
 /_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
                |___/


Angular CLI: 16.2.0
Node: 18.17.1
Package Manager: npm 9.8.1
OS: linux x64

```

<div style="page-break-after: always;"></div>

### Instalar Visual Studio Code

[Tabla de contenidos](#tabla-de-contenidos)

Recursos:

- https://ubunlog.com/visual-studio-code-editor-codigo-abierto-ubuntu-20-04/

- Instalación por consola:

```console
sudo apt update
sudo apt update
sudo apt install software-properties-common apt-transport-https wget
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt install code
```

- Extensiones:
  - Sería bueno que tuviesemos la opción de Formatear al guardar para mejorar la visualización del código.
  1. Le damos a CTRL + MAY + X (Extensiones)
  2. Escribimos Spanish Lenguage Pack y le damos a [install]. Pulsamos abajo a la derecha en [Restart].
  3. Escribimos PHP Intelephense y le damos a [Instalar]
  4. Escribimos Markdown All in One y le damos a [Instalar]
  5. Abrimos la configuración de Visual Studio Code: [CTRL + ","]
  6. Buscamos: settings.json. Le damos a Editar en JSON. Y ponemos esto:
     (para los archivo php y json formateamos al guardar)

```json
{
  "[php]": {
    "editor.formatOnSave": true
  },
  "[json]": {
    "editor.quickSuggestions": {
      "strings": true
    },
    "editor.suggest.insertMode": "replace",
    "editor.formatOnSave": true
  }
}
```

<div style="page-break-after: always;"></div>

## MYSQL

[Tabla de contenidos](#tabla-de-contenidos)

- Para este proyecto he montado la base de datos de Mascotas en MYSQL SERVER.

- Instalación:

  1. Primero tendremos que descargarnos el sistema de administración de datos donde los anidaremos:

  - https://www.microsoft.com/es-es/download/details.aspx?id=101064

  2. Segundo tendremos que instalar el SQL Management Studio donde gestionaremos nuestra base de datos: -https://learn.microsoft.com/es-es/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16

- He creado una base de datos muy sencilla para hacer nuestro CRUD sobre Mascotas:

```console
# SELECT TOP (1000) [id_mascota]
      ,[nombre]
      ,[edad]
      ,[descripcion]
  FROM [DB_MASCOTAS].[dbo].[Mascota]

```

En esta parte del codigo podemos traernos las 1000 primeras filas y observar los datos de prueba que hemos creado. Podemos observar las columnas que hemos creado.

- También para facilitar el manejo de datos en nuestro CRUD, MYSQL nos facilita una herramienta de crear procedimientos almacenados. Hemos aprovechado esta función:
  1. Añadir:
  ```console
  # USE [DB_MASCOTAS]
  GO
  /****** Object:  StoredProcedure [dbo].[Mascota_Add]    Script Date: 29/01/2024 19:00:48 ******/
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  ALTER PROC [dbo].[Mascota_Add]
  @nombre varchar(50),
  @edad int,
  @desc varchar(MAX)
  AS
  INSERT INTO Mascota (nombre, edad, descripcion)
  VALUES (@nombre, @edad, @desc)
  ```
  2. Eliminar:
  ```console
  USE [DB_MASCOTAS]
  GO
  /****** Object:  StoredProcedure [dbo].[Mascota_All]    Script Date: 29/01/2024 19:05:52 ******/
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  ALTER PROC [dbo].[Mascota_All]
  AS
  SELECT id_mascota, nombre, edad, descripcion FROM Mascota
  ORDER BY id_mascota ASC
  ```
  3. Todos:
  ```console
  USE [DB_MASCOTAS]
  GO
  /****** Object:  StoredProcedure [dbo].[Mascota_All]    Script Date: 29/01/2024 19:06:27 ******/
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  ALTER PROC [dbo].[Mascota_All]
  AS
  SELECT id_mascota, nombre, edad, descripcion FROM Mascota
  ORDER BY id_mascota ASC
  ```
  4. Actualizar:
  ```console
  # USE [DB_MASCOTAS]
  GO
  /****** Object:  StoredProcedure [dbo].[Mascota_All]    Script Date: 29/01/2024 19:06:27 ******/
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  ALTER PROC [dbo].[Mascota_All]
  AS
  SELECT id_mascota, nombre, edad, descripcion FROM Mascota
  ORDER BY id_mascota ASC
  ```
- Con esto terminamos con la parte de MySQL

<div style="page-break-after: always;"></div>

## Angular (Frontend)

[Tabla de contenidos](#tabla-de-contenidos)

- .NET es un conjunto de tecnologías desarrolladas por Microsoft que proporciona un entorno para construir y ejecutar una variedad de aplicaciones en diferentes plataformas.

- Las principales características de .NET incluyen:
  - Common Language Runtime (CLR): El CLR es el entorno de ejecución de .NET. Proporciona servicios como la gestión de memoria, la seguridad, el manejo de excepciones y la ejecución de código. Permite a los lenguajes de programación de .NET compilar el código a un lenguaje intermedio común (CIL o MSIL) que se ejecuta en el CLR.
  - Framework Class Library (FCL): La FCL es una colección de clases reutilizables y bibliotecas que proporcionan funcionalidades comunes para el desarrollo de aplicaciones. Contiene clases para manejar la entrada/salida, manipular archivos, realizar operaciones de red, trabajar con bases de datos, entre otras tareas.
  - Lenguajes de programación: .NET admite varios lenguajes de programación, incluyendo C#, F#, VB.NET y otros.
  - Herramientas de desarrollo: Microsoft ofrece herramientas como Visual Studio y Visual Studio Code para desarrollar aplicaciones en .NET.

<div style="page-break-after: always;"></div>

## .NET

[Tabla de contenidos](#tabla-de-contenidos)

- .NET es un conjunto de tecnologías desarrolladas por Microsoft que proporciona un entorno para construir y ejecutar una variedad de aplicaciones en diferentes plataformas.

- Las principales características de .NET incluyen:
  - Common Language Runtime (CLR): El CLR es el entorno de ejecución de .NET. Proporciona servicios como la gestión de memoria, la seguridad, el manejo de excepciones y la ejecución de código. Permite a los lenguajes de programación de .NET compilar el código a un lenguaje intermedio común (CIL o MSIL) que se ejecuta en el CLR.
  - Framework Class Library (FCL): La FCL es una colección de clases reutilizables y bibliotecas que proporcionan funcionalidades comunes para el desarrollo de aplicaciones. Contiene clases para manejar la entrada/salida, manipular archivos, realizar operaciones de red, trabajar con bases de datos, entre otras tareas.
  - Lenguajes de programación: .NET admite varios lenguajes de programación, incluyendo C#, F#, VB.NET y otros.
  - Herramientas de desarrollo: Microsoft ofrece herramientas como Visual Studio y Visual Studio Code para desarrollar aplicaciones en .NET.

<div style="page-break-after: always;"></div>

### Sección

[Tabla de contenidos](#tabla-de-contenidos)

```console
# ...
```
