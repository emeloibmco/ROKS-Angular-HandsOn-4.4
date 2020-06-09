# ROKS-Angular-HandsOn-4.3


# GUIA DE INSTALACIÓN Y DESPLIEGUE DE APP ANGULAR EN OPENSHIFT

_Para el desarrollo de este proyecto se tiene como base el desarrollo de una aplicación basada en el lenguaje de programación angular y su posterior despliegue en un **Cluster de OpenShift** que se encuentra alojado en **IBM Cloud**._

### Indice
1. [Despliegue en OpenShift desde IBM Cloud shell](#Despliegue-en-OpenShift-desde-IBM-Cloud-shell-)
2. [Despliegue Aplicación Hello World en Angular](#Despliegue-Aplicación-Hello-World-en-Angular-)
3. [Despliegue Aplicación Listas en Angular](#Despliegue-Aplicación-Listas-en-Angular-)
4. [Despliegue Aplicación Hello World en Nodejs Desde la consola web de OpenShift ](#Despliegue-Aplicación-Hello-World-en-Nodejs-Desde-la-consola-web-de-OpenShift-)
5. [Despliegue de una imagen Docker en un contenedor de Opeshift](#Despliegue-de-una-imagen-Docker-en-un-contenedor-de-Opeshift-)
6. [Despliegue Aplicación CRUD en Angular](#Despliegue-Aplicación-CRUD-en-Angular-)
7. [Anexos](#ANEXOS)
8. [Pre-requisitos](#Pre-requisitos-)
9. [Referencias](#Referencias)

## Despliegue en OpenShift desde IBM Cloud shell: 🚀

### Haga 'login' a IBM Cloud desde la línea de comando

_Inicialmente debe acceder al shell de IBM Cloud desde el siguiente link:_
```
https://cloud.ibm.com/shell
```

### Acceda al cluster de Open Shift (ROKS) desplegado en IBM Cloud 📦


_1.	Inicie sesión e ingrese desde la CLI de OpenShift al clúster en el que se va a trabajar._

_Para ingresar al clúster que tengamos aprovisionado en nuestra cuenta de IBM Cloud se deben realizar los siguientes pasos:_

_•	Ingresar a la plataforma de IBM cloud con sus credenciales de inicio de sesión, lo puede hacer desde el siguiente link:_

```
https://cloud.ibm.com/
```

_•	Diríjase al resource list._
_Primero debe dar clic en el navigation menu y luego donde dice Resource list, como se puede ver en la siguiente imagen:_

<p align="center">
<img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">
</p>

_•	Diríjase a la sección de clústers y dar clic en el que se desea acceder._

_•	Se da clic en el botón OpenShift web console._

### Haga 'login' en el cluster de Open Shift (ROKS) desde la linea de comando 📦

_•	Ahora en la parte superior derecha se da clic sobre el ID del correo con el que ingresamos y luego en la sección que dice Copy Login Command._

<p align="center">
<img width="144" alt="1" src="https://user-images.githubusercontent.com/60987042/76917049-53479180-6890-11ea-91a1-b2c2c9213729.PNG">
</p>
_•	Y por último volvemos a la terminal que se estaba utilizando pegamos y damos enter._

### Cree un nuevo proyecto en Open Shift para desplegar las aplicaciones 📦

_2.	Cree un nuevo proyecto en el cluster de la siguiente manera:_
```
oc new-project <projectname>
```
_**Nota:** Para el **projectname** coloque **openshift + las iniciales de su nombre y apellido.**_

_3.	Acceda al proyecto que acabo de crear de la siguiente manera:_

```
oc project <projectname>
```

## Despliegue Aplicación Hello World en Angular 🅰️

_4.	Clone el repositorio de la aplicación que se desea desplegar._

_**App de hello Word en angular:** https://github.com/emeloibmco/AngularHelloWorld_


_5.	Desde el Shell de IBM cloud digite el comando:_

```
git clone <url_repositorio>
```
_6.	Dirigirse desde a esta carpeta con el comando:_

_•	Para la carpeta del proyecto Hello word:_
```
cd AngularHelloWorld
```
_7.	Para desplegar la aplicación en OpenShift es necesario escribir el siguiente comando:_
```
npx nodeshift --strictSSL=false --dockerImage=nodeshift/ubi8-s2i-web-app --imageTag=10.x --build.env OUTPUT_DIR=dist/angular-web-app --expose
```
_El resultado de este comando va a ser una respuesta de este tipo, que nos indica que 
la aplicación se desplego correctamente.

<p align="center">
<img width="865" alt="2" src="https://user-images.githubusercontent.com/60987042/76918560-9441a500-6894-11ea-954f-62c8076b8903.PNG">
</p>

_8.	Para poder acceder al la URL de la aplicación y realizar la verificación de la misma debemos:_

_•Acceder a IBM cloud._

_•Dirigirse al resource list._

_•Dirigirse a la sección de clusters._

_•Ingresar al cluster que lleva por nombre openshift-4.2_

_•Ingrese a la sección de openshift web console._

_•Buscar el proyecto que creo con sus iniciales y buscar la aplicación que se desplego._

![image](https://user-images.githubusercontent.com/44415995/83429276-6bdc3800-a3f9-11ea-8b92-51d6032ce830.png)

_Y por último solo faltaría dar clic en el link que lo llevara a la aplicación desplegada._


![12](https://user-images.githubusercontent.com/60987042/77018166-89494c00-694a-11ea-9f7e-f05d109631d0.png)


_De esta forma se daría por terminado el despliegue de la aplicación angular en openshift._

## Despliegue Aplicación Listas en Angular 🅰️ 

 

_9.	Clone el repositorio de la aplicación que se desea desplegar._

_**App de listas en angular:** https://github.com/emeloibmco/AngularWebList_

_10.	Desde el Shell de IBM cloud digitar el comando:_

```
Git clone <url_repositorio>
```
_11.	Dirigirse desde a esta carpeta con el comando:_

•	Para la carpeta del proyecto listas.
```
cd AngularWebList
```
_12.	Para desplegar la aplicación en OpenShift es necesario escribir el siguiente comando:_
```
npx nodeshift --strictSSL=false --dockerImage=nodeshift/ubi8-s2i-web-app --imageTag=10.x --build.env OUTPUT_DIR=dist/angular-web-app --expose
```
_13. Para confirmar que la aplicación ha sido desplegada busque la aplicación en el proyecto creado en la consola Web de OpenShift, y seleccione el link con el enlace a la aplicación.

<p align="center">
<img width="515" alt="listas" src="https://user-images.githubusercontent.com/60987042/83415347-91ab1200-a3e4-11ea-9df1-90a6ef1e608a.PNG">
 </p>

_Y por último solo faltaría dar clic en el link que lo llevara a la aplicación desplegada._

<p align="center">
<img width="681" alt="lis" src="https://user-images.githubusercontent.com/60987042/83415439-adaeb380-a3e4-11ea-8d5c-bf189f652fc1.PNG">
</p>

## Despliegue Aplicación Hello World en Nodejs Desde la consola web de OpenShift 📦 

_Para realizar el despliegue desde la consola web de OpenShif de una  manera mas intuitiva se deben seguir los siguientes pasos:_

_1. Ingrese a IBM cloud desde el siguiente link:_
```
https://cloud.ibm.com/login
```
_2. Realice el login con sus credenciales de ingreso._

---
![Captura de pantalla de 2020-03-26 17-25-55](https://user-images.githubusercontent.com/60987042/77702638-f8482580-6f86-11ea-9a83-9714df69ec38.png)
  
---

_3. Dirijase al resource list._

---
<p align="center">
<img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">
</p>


_**NOTA:** En la parte superior derecha al lado de "Manage", aparece las diferentes cuantas que tiene disponibles para trabajar. Para este caso debe asegurase que se encuentre en la cuenta:**1699257_......**_

_4. Dirigirse a la sección de clusters._

---
<p align="center">
<img width="668" alt="clus" src="https://user-images.githubusercontent.com/60987042/83417688-13506f00-a3e8-11ea-8d06-69558164a8a0.PNG">
</p>


_5. Ingresar al cluster que lleva por nombre openshift-4.3_

_6. Ingrese a la sección de openshift web console._

<p align="center">
<img width="949" alt="4 3" src="https://user-images.githubusercontent.com/60987042/83417830-40048680-a3e8-11ea-968b-2cda9035accf.PNG">
</p>

_7. Ingrese a la sección add y luego debe elegir From Catolog._

<p align="center">
<img width="668" alt="add" src="https://user-images.githubusercontent.com/60987042/83418062-97a2f200-a3e8-11ea-8d9d-300204c15e2f.PNG">
</p>

_8. En este momento estamos en el catalogo de OpenShift, ahora se debe seleccionar la opcion Node.js._

---
<p align="center">
<img width="668" alt="node" src="https://user-images.githubusercontent.com/60987042/83418103-a9849500-a3e8-11ea-8e26-d2d9b549d600.PNG">
</p>

_9. Una vez seleccionada, presione "Next" y proporcione el nombre de la aplicación, la URL del git donde se encuentra el proyecto a desplegar y presione "Create"._

<p align="center">
<img width="668" alt="img7" src="https://user-images.githubusercontent.com/40369712/77024355-527c3180-695c-11ea-8f74-d58c9d5c8999.png">
</p>

_si desea desplegar desplegar un HelloWord de nodejs puede utilizar el siguiente repositorio de github:_
```
https://github.com/openshift/nodejs-ex.git
```

_10. Para ver el link de despliegue se debe dar clic en "Continue to the project overview"._

<p align="center">
<img width="580" alt="nodej" src="https://user-images.githubusercontent.com/60987042/83418284-f7010200-a3e8-11ea-9c1c-86efc9b25aef.PNG">
</p>


**Nota:** Espere unos mintos mientras el proceso de construcción y despliegue de la aplicación se termina.

---

_11. Una vez terminado el proceso de despliegue puede dirigirse a Routes, donde podra ver la URL mediante la cual podra acceder a la aplicacion ya desplegada._


<img width="894" alt="nod" src="https://user-images.githubusercontent.com/60987042/83419230-5d3a5480-a3ea-11ea-86fd-7cdf9bf92fe4.PNG">


## Despliegue de una imagen Docker en un contenedor de Opeshift 📦

_Para realizar el despliegue de una aplicación que se encuentra alojada en un una imagen de DockerHub se deben realizar los siguintes pasos:_


_1. Ingrese a IBM cloud desde el siguiente link:_
```
https://cloud.ibm.com/login
```
_2. Realice el login con sus credenciales de ingreso._

---
![Captura de pantalla de 2020-03-26 17-25-55](https://user-images.githubusercontent.com/60987042/77702638-f8482580-6f86-11ea-9a83-9714df69ec38.png)
---

_3. Dirijase al resource list._
---
<img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">
---

_**NOTA:** En la parte superior derecha al lado de "Manage", aparece las diferentes cuantas que tiene disponibles para trabajar. Para este caso debe asegurase que se encuentre en la cuenta:**1699257**._

_4. Dirigirse a la sección de clusters._

---
<p align="center">
<img width="668" alt="clus" src="https://user-images.githubusercontent.com/60987042/83417688-13506f00-a3e8-11ea-8d06-69558164a8a0.PNG">
</p>

_5. Ingresar al cluster que lleva por nombre openshift-4.3_

_6. Ingrese a la sección de openshift web console._

<p align="center">
<img width="949" alt="4 3" src="https://user-images.githubusercontent.com/60987042/83417830-40048680-a3e8-11ea-968b-2cda9035accf.PNG">
</p>

_8. Dar clic en la sección **Add** y luego en la sección ***Container Image*._

<p align="center">
<img width="668" alt="contai" src="https://user-images.githubusercontent.com/60987042/83419932-7e4f7500-a3eb-11ea-8a3a-1a1e2a652adc.PNG">
</p>

_9. Al dar clic en Container Image se abre una ventana en la cual debemos seleccionar el campo **Image Name** y llenar el campo con la ruta fuente de la imagen docker._

<img width="960" alt="librty1" src="https://user-images.githubusercontent.com/45157348/83713481-cd64f800-a5ed-11ea-87b0-420f6f37231f.PNG">


_10. Si reconoce la imagen docker, automaticamente aparece la imagen docker y se llena la información necesaria para el despligue y se  habilita la opción para dar clic en **CREAR**_, y al dar clic acá se inicia el despliegue de la aplicación por lo que se debe esperar un momento mientras se realiza el mismo.

<p align="center">
<img width="501" alt="ibm-sphere" src="https://user-images.githubusercontent.com/45157348/83713491-d35ad900-a5ed-11ea-9f2e-b37163277a29.PNG">
</p>

_11. Una vez terminado el proceso de despliegue puede dirigirse a Overview dando clic sobre el circulo de despliegue, donde podra ver la URL mediante la cual podra acceder a la aplicacion ya desplegada._

<p align="center">
<img width="508" alt="we" src="https://user-images.githubusercontent.com/60987042/83420340-1e0d0300-a3ec-11ea-8d0f-c36e60ff15e7.PNG">
</p>

_12. al dar clic en la URL podra acceder a la aplicacion ya desplegada._

![image](https://user-images.githubusercontent.com/45157348/83714177-ae676580-a5ef-11ea-8477-841da501564a.png)


## Despliegue Aplicación CRUD en Angular 📦

Como ejercicio OPCIONAL se puede realizar el despligue de una aplicación en una arquitectura multi-capa.  Esta aplicación de ejemplo es una aplicación que permite crear transacciones (giros), que son almacenados en una base de datos.   

La aplicación esta compuesta por 3 contenedores: 

- Front, front desarrollado en Angular, para la interfaz de usuario Web
- CRUD,  backend desarrollado en express, que expone API's para la operaciones hacia la base de datos
- MongoDB, un contenedor con el motor de la base de datos MongoDB

Para realizar este ejercicio, se pueden seguir las siguientes guias, en donde se encuentra el código de la aplicación de ejemplo: 

Despliegue de base de datos y back-end de la aplicación:
https://github.com/emeloibmco/AngularWebCRUDMongo

Despliegue de front de aplicación:
https://github.com/emeloibmco/AngularWebFrontCRUD

Es recomendable realizar el despliegue del back-end, y luego el despliegue del front.  Se requiere modificar las credenciales y las URL's especificas cuando para completar el ejercicio. 

Como ejercicio adicional, se recomienda configurar ConfigMap para utlizar parametros en variables de ambiente  para las URL's, y Secrets para almacenar credenciales y contraseñas en Open Shift.

La siguiente es la URL de el despliegue de esta aplicación demo:
http://efecty-app-default.openshift311-ea9753cca330b7f05a99ad5b2c8b5da1-0001.us-east.containers.appdomain.cloud/inicio


# ANEXOS

_Si se desea realizar el mismo despliegue desde la cli, pero desde la maquina local se deberían seguir los siguientes pasos:_

## Pre-requisitos 📋

_Paso 1: Instale IBM Cloud CLI._

_Instale la interfaz de la línea de comandos de IBM Cloud así:_

_**Para Mac y Linux ™**_
_Ejecute el siguiente comando en la terminal:_
```
curl -sL https://ibm.biz/idt-installer | bash
```
_**Para Windows™ 10 Pro**_
_Pulse con el botón derecho del ratón el icono de Windows™ PowerShell y seleccione **Ejecutar como administrador**, efectué el siguiente comando:_

```
[Net.ServicePointManager]::SecurityProtocol="Tls12";iex(New-Object Net.WebClient).DownloadString('https://ibm.biz/idt-win-installer')
```

_Paso 2: Verificar la instalación._
_Para verificar que las herramientas de desarrollador y la CLI se han instalado correctamente, ejecute el comando **help**:_

```
ibmcloud dev help
```
_Paso 3:	Instalar CLI de OpenShift._

_Desde el siguiente link podremos descargar el respectivo instalador._

```
https://www.okd.io/download.html
```

_Para instalarlo debemos descomprimir la carpeta, encontraremos los siguientes archivos:_

<img width="513" alt="5" src="https://user-images.githubusercontent.com/60987042/76979004-60529800-6905-11ea-9830-5d28e2d5c4af.PNG">

_De estos archivos debemos copiar el que tiene por nombre oc y pegarlo en la carpeta bin que encontramos en la siguiente dirección:_

```
C:\Program Files\IBM\Cloud\bin
```
## Referencias

La documentación en linea de IBM Cloud Red Hat OpenShift Managed, se encuentra en el siguiente enlace:

https://cloud.ibm.com/docs/openshift?topic=openshift-getting-started

En la siguiente página se encuentra la información de administración y configuración de Open Shift 3.11.

https://access.redhat.com/documentation/en-us/openshift_container_platform/3.11/

## Autores ✒️

_Equipo IBM Cloud Tech sales Colombia._

