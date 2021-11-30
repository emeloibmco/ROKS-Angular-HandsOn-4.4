# ROKS Angular - HandsOn 4.4 ☁

Para el desarrollo de este proyecto se tiene como base el desarrollo de una aplicación basada en el lenguaje de programación angular y su posterior despliegue en un **Cluster de OpenShift** que se encuentra alojado en **IBM Cloud**.

<br />

### Indice
1. [Despliegue en OpenShift desde IBM Cloud shell](#Despliegue-en-OpenShift-desde-IBM-Cloud-shell-)
2. [Despliegue Aplicación Hello World en Angular](#despliegue-aplicación-hello-world-en-angular-🅰️)
3. [Despliegue Aplicación Listas en Angular](#despliegue-aplicación-listas-en-angular-🅰️)
4. [Despliegue Aplicación Hello World en Nodejs Desde la consola web de OpenShift ](#Despliegue-Aplicación-Hello-World-en-Nodejs-Desde-la-consola-web-de-OpenShift-)
5. [Despliegue de una imagen Docker en un contenedor de Opeshift](#Despliegue-de-una-imagen-Docker-en-un-contenedor-de-Opeshift-)
6. [Despliegue Aplicación CRUD en Angular](#Despliegue-Aplicación-CRUD-en-Angular-)
7. [Instalación y despliegue de Eclipce Che con un operador](#Instalación-y-despliegue-de-Eclipce-Che-con-un-operador-)
8. [Anexos](#ANEXOS)
9. [Pre-requisitos](#Pre-requisitos-)
10. [Referencias](#Referencias)
<br />

## Despliegue en OpenShift desde IBM Cloud shell: 🚀

### Haga 'login' a IBM Cloud desde la línea de comando

Inicialmente debe acceder al shell de IBM Cloud desde el siguiente link:

```
https://cloud.ibm.com/shell
```
<br />

### Acceda al cluster de Open Shift (ROKS) desplegado en IBM Cloud 📦

1.	Inicie sesión e ingrese desde la CLI de OpenShift al clúster en el que se va a trabajar. Para ingresar al clúster que tengamos aprovisionado en nuestra cuenta de IBM Cloud se deben realizar los siguientes pasos:

    * Ingresar a la plataforma de IBM cloud con sus credenciales de inicio de sesión, lo puede hacer desde el siguiente link:

     ```
     https://cloud.ibm.com/
     ```
     <br />
     
    * Diríjase al resource list. Primero debe dar clic en el navigation menu y luego donde dice Resource list, como se puede ver en la siguiente imagen:

      <p align="center">
      <img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">
      </p>
      <br />

    * Diríjase a la sección de clústers y dar clic en el que se desea acceder.
      <br />

    * Se da clic en el botón OpenShift web console.
    
      <br />

### Haga 'login' en el cluster de Open Shift (ROKS) desde la linea de comando 📦

Ahora en la parte superior derecha se da clic sobre el ID del correo con el que ingresamos y luego en la sección que dice Copy Login Command.
<br />

<p align="center">
<img width="144" alt="1" src="https://user-images.githubusercontent.com/60987042/76917049-53479180-6890-11ea-91a1-b2c2c9213729.PNG">
</p>
<br />

Y por último volvemos a la terminal que se estaba utilizando pegamos y damos enter.

<br />

### Cree un nuevo proyecto en Open Shift para desplegar las aplicaciones 📦
1.	Cree un nuevo proyecto en el cluster de la siguiente manera:

   ```
   oc new-project <projectname>
   ```
   
   **Nota:** Para el **projectname** coloque **openshift + las iniciales de su nombre y apellido.**
   <br />
   
2.	Acceda al proyecto que acabo de crear de la siguiente manera:

   ```
   oc project <projectname>
   ```   
   <br />

## Despliegue Aplicación Hello World en Angular 🅰️
1.	Clone el repositorio de la aplicación que se desea desplegar.

   **App de hello Word en angular:** https://github.com/emeloibmco/AngularHelloWorld
   
   <br />

2.	Desde el Shell de IBM cloud digite el comando:

   ```
   git clone <url_repositorio>
   ```
   
   <br />
   
3.	Dirigirse desde a esta carpeta con el comando:

   ```
   cd AngularHelloWorld
   ```
   
   <br />
   
4.	Para desplegar la aplicación en OpenShift es necesario escribir el siguiente comando:

   ```
   npx nodeshift --strictSSL=false --dockerImage=nodeshift/ubi8-s2i-web-app --imageTag=10.x --build.env OUTPUT_DIR=dist/angular-web-app --expose
   ```
   <br />
   
   El resultado de este comando va a ser una respuesta de este tipo, que nos indica que la aplicación se desplego correctamente.
   <br />
   
   <p align="center">
   <img width="865" alt="2" src="https://user-images.githubusercontent.com/60987042/76918560-9441a500-6894-11ea-954f-62c8076b8903.PNG">
   </p>
   
   <br />

5.	Para poder acceder al la URL de la aplicación y realizar la verificación de la misma debemos:

      * Acceder a IBM cloud.

      * Dirigirse al resource list.

      * Dirigirse a la sección de clusters.

      * Ingresar al cluster que lleva por nombre openshift-4.2

      * Ingrese a la sección de openshift web console.

      * Buscar el proyecto que creo con sus iniciales y buscar la aplicación que se desplego.

      <br />

   ![image](https://user-images.githubusercontent.com/44415995/83429276-6bdc3800-a3f9-11ea-8b92-51d6032ce830.png)
   
   <br />

   Y por último solo faltaría dar clic en el link que lo llevara a la aplicación desplegada.

   <br />
   
   ![12](https://user-images.githubusercontent.com/60987042/77018166-89494c00-694a-11ea-9f7e-f05d109631d0.png)

   <br />
   
   De esta forma se daría por terminado el despliegue de la aplicación angular en openshift.

   <br />
   

## Despliegue Aplicación Listas en Angular 🅰️ 
1.	Clone el repositorio de la aplicación que se desea desplegar.

   **App de listas en angular:** https://github.com/emeloibmco/AngularWebList

   Desde el Shell de IBM cloud digitar el comando:

   ```
   Git clone <url_repositorio>
   ```
   
   <br />
   
2.	Dirigirse desde a esta carpeta con el comando:

   ```
   cd AngularWebList
   ```
   
   <br />
   
3.	Para desplegar la aplicación en OpenShift es necesario escribir el siguiente comando:

   ```
   npx nodeshift --strictSSL=false --dockerImage=nodeshift/ubi8-s2i-web-app --imageTag=10.x --build.env OUTPUT_DIR=dist/angular-web-app --expose
   ```
   
   <br />
   
4. Para confirmar que la aplicación ha sido desplegada busque la aplicación en el proyecto creado en la consola Web de OpenShift, y seleccione el link con el enlace a la aplicación.

   <p align="center">
   <img width="515" alt="listas" src="https://user-images.githubusercontent.com/60987042/83415347-91ab1200-a3e4-11ea-9df1-90a6ef1e608a.PNG">
    </p>

   Y por último solo faltaría dar clic en el link que lo llevara a la aplicación desplegada.

   <p align="center">
   <img width="681" alt="lis" src="https://user-images.githubusercontent.com/60987042/83415439-adaeb380-a3e4-11ea-8d5c-bf189f652fc1.PNG">
   </p>
   
   <br />
   
## Despliegue Aplicación Hello World en Nodejs Desde la consola web de OpenShift 📦 

Para realizar el despliegue desde la consola web de OpenShif de una  manera mas intuitiva se deben seguir los siguientes pasos:

1. Ingrese a IBM cloud desde el siguiente link:

   ```
   https://cloud.ibm.com/login
   ```
   
   <br />
   
2. Realice el login con sus credenciales de ingreso.

   ---
   ![Captura de pantalla de 2020-03-26 17-25-55](https://user-images.githubusercontent.com/60987042/77702638-f8482580-6f86-11ea-9a83-9714df69ec38.png)

   ---
   
   <br />

3. Dirijase al resource list.

   ---
   <p align="center">
   <img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">
   </p>


   **NOTA:** En la parte superior derecha al lado de "Manage", aparece las diferentes cuantas que tiene disponibles para trabajar. Para este caso debe asegurase que se encuentre en la cuenta:**1699257_......**
   
   <br />

4. Dirigirse a la sección de clusters.

   <p align="center">
   <img width="749" alt="ope-4" src="https://user-images.githubusercontent.com/60987042/93896282-5ba4dd00-fcb6-11ea-83de-dd6fabe43333.PNG">
   </p>
   
   <br />

5. Ingresar al cluster que lleva por nombre **openshift-4.4.20**
<br />

6. Ingrese a la sección de openshift web console.

<p align="center">
<img width="960" alt="op" src="https://user-images.githubusercontent.com/60987042/93896373-76775180-fcb6-11ea-8974-059b54190f55.PNG">
</p>

<br />

7. Cree un nuevo proyecto con la siguiente syntaxis **handson-nombreapellido**.

<p align="center">
<img width="749" alt="new-project" src="https://user-images.githubusercontent.com/60987042/93888733-0369dd00-fcae-11ea-9918-80bcfd8bb35c.PNG">
</p>

<br />

8. Ingrese a la sección add y luego debe elegir From Catolog.

<p align="center">
<img width="668" alt="add" src="https://user-images.githubusercontent.com/60987042/83418062-97a2f200-a3e8-11ea-8d9d-300204c15e2f.PNG">
</p>

<br />

9. En este momento estamos en el catalogo de OpenShift, ahora se debe seleccionar la opcion Node.js.

<p align="center">
<img width="668" alt="node" src="https://user-images.githubusercontent.com/60987042/83418103-a9849500-a3e8-11ea-8e26-d2d9b549d600.PNG">
</p>

<br />

10. Una vez seleccionada, presione "Next" y proporcione el nombre de la aplicación, la URL del git donde se encuentra el proyecto a desplegar.

<p align="center">
<img width="960" alt="add-repo" src="https://user-images.githubusercontent.com/60987042/93888847-209eab80-fcae-11ea-8916-6ce5ffa4cfa2.PNG">
</p>

<br />

   Si desea desplegar desplegar un HelloWord de nodejs puede utilizar el siguiente repositorio de github:
   ```
   https://github.com/Smith2008S/HelloWorld-NodeJs.git
   ```
   
   <br />
   
   
11. Al final de esta pagina encontrara una sección de opciones avanzadas en la cual encontrara un link de **Scaling**.

<p align="center">
<img width="747" alt="Scaling" src="https://user-images.githubusercontent.com/60987042/93889169-7ecb8e80-fcae-11ea-8c39-c30e2ac90465.PNG">
</p>

<br />

12. La sección de **Scaling**, nos permitirá configurar el número de replicas si deseamos un auto escalamiento para nuestra aplicación.

<p align="center">
<img width="960" alt="replicas" src="https://user-images.githubusercontent.com/60987042/93889521-e71a7000-fcae-11ea-80ca-515528219c9e.PNG">
</p>

<br />

13. Al dar clic en crear se iniciara un proceso de build el cual nos entregara el link de despliegue de nuestra aplicación".

<p align="center">
<img width="959" alt="build" src="https://user-images.githubusercontent.com/60987042/93889687-2052e000-fcaf-11ea-8115-a33397862c1d.PNG">
</p>


**Nota:** Espere unos cuantos segunodos mientras el proceso de construcción y despliegue de la aplicación se termina.

<br />

14. Una vez terminado el proceso de despliegue puede dirigirse a Routes, donde podra ver la URL mediante la cual podra acceder a la aplicacion ya desplegada.

<p align="center">
<img width="960" alt="hwl" src="https://user-images.githubusercontent.com/60987042/93890404-ecc48580-fcaf-11ea-8dfa-742a6aad9e92.PNG">
</p>

<br />

### Monitoreo de la aplicación

Para realizar un monitoreo de nuestra aplicación desplegada debemos seguir los siguientes pasos:

1. En la sección izquierda de nuestra panatalla debemos acceder al modo de **Administrador**.

<p align="center">
<img width="746" alt="admin" src="https://user-images.githubusercontent.com/60987042/93892976-bccab180-fcb2-11ea-8864-0cf86a18b380.PNG">
</p>
<br />

2. En el menú lateral izquierdo, debemos dirigirnos a la sección de **Monitoring** y luego dar clic en **Dashboards**.

<p align="center">
<img width="746" alt="moni" src="https://user-images.githubusercontent.com/60987042/93893022-c81ddd00-fcb2-11ea-97bd-b9a532c350af.PNG">
</p>
<br />

3. Ahora debemos dar clic donde dice **Grafana UI**.

<p align="center">
<img width="752" alt="grafana-ui" src="https://user-images.githubusercontent.com/60987042/93896636-c524eb80-fcb6-11ea-8986-d689e99eac8b.PNG">
</p>
<br />

4. Esta acción nos va a redirigir a una nueva ventana de nuestro navegador en la cual debemos seleccionar nuesro metodo de acceso al cual debemos dar clic en **Log in with Openshift**.

<p align="center">
<img width="960" alt="log in grafana" src="https://user-images.githubusercontent.com/60987042/93893051-d1a74500-fcb2-11ea-8982-24db221aec48.PNG">
</p>
<br />

5. En esta nueva ventana inicialmente nos aparecera un mensaje de autorización en cual debemos dar clic en **Allow Selected Permissions**.

<p align="center">
<img width="960" alt="acces" src="https://user-images.githubusercontent.com/60987042/93896923-1fbe4780-fcb7-11ea-9a69-dc23dd35f814.PNG">
</p>
<br />

6. Al completar el paso anterior nos aparecera el Dashboard inicial de Grafana, la cual es la herramineta de monitoreo que viene integrada con openshift.

<p align="center">
<img width="959" alt="grafa" src="https://user-images.githubusercontent.com/60987042/93893080-dbc94380-fcb2-11ea-9733-5e8a37e31d84.PNG">
</p>
<br />

7. Para poder monitorear nuestra aplicacion debemos dar clic en **Home** y aca se nos mostrara un menu desplegable en el cual debemos seleccionar el siguienete:

<p align="center">
<img width="752" alt="menu-grafa" src="https://user-images.githubusercontent.com/60987042/93893179-f69bb800-fcb2-11ea-8263-5f1e8fef79ea.PNG">
</p>
<br />

8. El paso final es en el apartado de **namespace**, buscar nuestro proyecto el cual tenia la syntaxis de **handson-nobreapellido**.

<p align="center">
<img width="960" alt="cpu" src="https://user-images.githubusercontent.com/60987042/93893355-2945b080-fcb3-11ea-99ca-fa8d27a58a97.PNG">
</p>

De esta manera podemos analizar el consumo que se a tenido en nuestra aplicación tanto en CPU como en Memoria.

<br />

## Despliegue de una imagen Docker en un contenedor de Opeshift 📦

Para realizar el despliegue de una aplicación que se encuentra alojada en un una imagen de DockerHub se deben realizar los siguintes pasos:


1. Ingrese a IBM cloud desde el siguiente link:
   ```
   https://cloud.ibm.com/login
   ```
   
   <br />
   
2. Realice el login con sus credenciales de ingreso.

---
![Captura de pantalla de 2020-03-26 17-25-55](https://user-images.githubusercontent.com/60987042/77702638-f8482580-6f86-11ea-9a83-9714df69ec38.png)
---

<br />

3. Dirijase al resource list.
---
<img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">
---

**NOTA:** En la parte superior derecha al lado de "Manage", aparece las diferentes cuantas que tiene disponibles para trabajar. 

<br />

4. Dirigirse a la sección de clusters.

---
<p align="center">
<img width="668" alt="clus" src="https://user-images.githubusercontent.com/60987042/83417688-13506f00-a3e8-11ea-8d06-69558164a8a0.PNG">
</p>

<br />

5. Ingresar al cluster que lleva por nombre openshift-4.3
<br />

6. Ingrese a la sección de openshift web console.

<p align="center">
<img width="949" alt="4 3" src="https://user-images.githubusercontent.com/60987042/83417830-40048680-a3e8-11ea-968b-2cda9035accf.PNG">
</p>

<br />

7. Dar clic en la sección **Add** y luego en la sección ***Container Image*.

<p align="center">
<img width="668" alt="contai" src="https://user-images.githubusercontent.com/60987042/83419932-7e4f7500-a3eb-11ea-8a3a-1a1e2a652adc.PNG">
</p>

<br />

8. Al dar clic en Container Image se abre una ventana en la cual debemos seleccionar el campo **Image Name** y llenar el campo con la ruta fuente de la imagen docker.

<img width="960" alt="librty1" src="https://user-images.githubusercontent.com/45157348/83713481-cd64f800-a5ed-11ea-87b0-420f6f37231f.PNG">
<br />

9. Si reconoce la imagen docker, automaticamente aparece la imagen docker y se llena la información necesaria para el despligue y se  habilita la opción para dar clic en **CREAR**, y al dar clic acá se inicia el despliegue de la aplicación por lo que se debe esperar un momento mientras se realiza el mismo.

<p align="center">
<img width="501" alt="ibm-sphere" src="https://user-images.githubusercontent.com/45157348/83713491-d35ad900-a5ed-11ea-9f2e-b37163277a29.PNG">
</p>
<br />

10. Una vez terminado el proceso de despliegue puede dirigirse a Overview dando clic sobre el circulo de despliegue, donde podra ver la URL mediante la cual podra acceder a la aplicacion ya desplegada.

<p align="center">
<img width="508" alt="we" src="https://user-images.githubusercontent.com/60987042/83420340-1e0d0300-a3ec-11ea-8d0f-c36e60ff15e7.PNG">
</p>
<br />

11. al dar clic en la URL podra acceder a la aplicacion ya desplegada.

![image](https://user-images.githubusercontent.com/45157348/83714177-ae676580-a5ef-11ea-8477-841da501564a.png)

<br />

## Despliegue Aplicación CRUD en Angular 📦

Como ejercicio OPCIONAL se puede realizar el despligue de una aplicación en una arquitectura multi-capa.  Esta aplicación de ejemplo es una aplicación que permite crear transacciones (giros), que son almacenados en una base de datos.   
<br />

La aplicación esta compuesta por 3 contenedores: 

- Front, front desarrollado en Angular, para la interfaz de usuario Web
- CRUD,  backend desarrollado en express, que expone API's para la operaciones hacia la base de datos
- MongoDB, un contenedor con el motor de la base de datos MongoDB
<br />

Para realizar este ejercicio, se pueden seguir las siguientes guias, en donde se encuentra el código de la aplicación de ejemplo: 
<br />

Despliegue de base de datos y back-end de la aplicación:
https://github.com/emeloibmco/AngularWebCRUDMongo
<br />

Despliegue de front de aplicación:
https://github.com/emeloibmco/AngularWebFrontCRUD
<br />

Es recomendable realizar el despliegue del back-end, y luego el despliegue del front.  Se requiere modificar las credenciales y las URL's especificas cuando para completar el ejercicio. 

Como ejercicio adicional, se recomienda configurar ConfigMap para utlizar parametros en variables de ambiente  para las URL's, y Secrets para almacenar credenciales y contraseñas en Open Shift.

La siguiente es la URL de el despliegue de esta aplicación demo:
http://efecty-app-default.openshift311-ea9753cca330b7f05a99ad5b2c8b5da1-0001.us-east.containers.appdomain.cloud/inicio

<br />

## Instalación y despliegue de Eclipce Che con un operador 🚀

**PASOS:**

### Acceda al cluster de Open Shift (ROKS) desplegado en IBM Cloud 📦


1. Ingrese a IBM cloud desde el siguiente link:
   ```
   https://cloud.ibm.com/login
   ```
   <br />
   
2. Realice el login con sus credenciales de ingreso.

---
![Captura de pantalla de 2020-03-26 17-25-55](https://user-images.githubusercontent.com/60987042/77702638-f8482580-6f86-11ea-9a83-9714df69ec38.png)
---
<br />

3. Dirijase al resource list.

<img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">
<br />

4. Dirigirse a la sección de clusters.

<p align="center">
<img width="749" alt="ope-4" src="https://user-images.githubusercontent.com/60987042/93896282-5ba4dd00-fcb6-11ea-83de-dd6fabe43333.PNG">
</p>
<br />

5. Ingresar al cluster que lleva por nombre **openshift-4.4.20**
<br />

6. Ingrese a la sección de openshift web console.

<p align="center">
<img width="960" alt="op" src="https://user-images.githubusercontent.com/60987042/93896373-76775180-fcb6-11ea-8974-059b54190f55.PNG">
</p>
<br />

7. Dar clic en el menú desplegable de la parte superior izquierda y seleccionar **Administrator**.

<p align="center">
<img width="699" alt="administrator-oc" src="https://user-images.githubusercontent.com/60987042/89837634-fd210680-db2e-11ea-9674-1a6b96bba17b.PNG">
</p>
<br />

8. Al dar clic en Administrator se abre una nueva interfaz en la cual debemos seleccionar el campo **Operators** y luego dar clic en **OperatorHub**.

<p align="center">
<img width="706" alt="OperatorHub" src="https://user-images.githubusercontent.com/60987042/89837669-1033d680-db2f-11ea-981f-d8c5ec89dd5f.PNG">
</p>
<br />

9. Una vez estemos en OpratorHub debemos buscar mediante el **Filter by keyword...** el operador correspondiente a **Eclipse-che**.

<p align="center">
<img width="960" alt="Eclipse-che" src="https://user-images.githubusercontent.com/60987042/89837709-2477d380-db2f-11ea-975b-b2b30c2ec04a.PNG">
</p>
<br />

10. Al dar clic sobre Eclipse-che se nos va desplegar una nueva ventana en la cual debemos instalar el operador sin modificar ningun campo.
<br />

11. Una vez instalado el operador, ingresamos y le damos clic en **Create CheCluster**.

<p align="center">
<img width="700" alt="create" src="https://user-images.githubusercontent.com/60987042/89837718-280b5a80-db2f-11ea-8201-867f97450fe3.PNG">
</p>
<br />

12. Al dar clic en **Create CheCluster**, se nos va a mostrar un **.YAMl** el cual describe nuestro despliegue y en el, debemos cambiar las siguientes variables:

    * ```selfSignedCert```: **true**
    * ```openShiftoAuth```: **false**
<br />

13. Al modificar las variables anteriores o al asegurarse de que estas tengan el valor dado en el paso anterior, prosedemos a dar clic en **Create**

<p align="center">
<img width="702" alt="Create yaml" src="https://user-images.githubusercontent.com/60987042/89837728-2b9ee180-db2f-11ea-8437-c98727482f7f.PNG">
</p>
<br />

14. Al Pasar unos 10 min, debemos dar clic en el menú desplegable de la parte superior izquierda y seleccionar **Developer**.

<p align="center">
<img width="702" alt="Developer-oc" src="https://user-images.githubusercontent.com/60987042/89837738-2fcaff00-db2f-11ea-9036-409932e55747.PNG">
</p>
<br />

15. Al ingresar como developer vamos a ver todos los Pods que se generarón para el despliegue de Eclipse-che. Para acceder a la interfaz grafica de Eclipse debemos dar clic en **Open-URL**

<p align="center">
<img width="702" alt="Open-URL" src="https://user-images.githubusercontent.com/60987042/89837745-335e8600-db2f-11ea-81e7-c423ec7ff40e.PNG">
</p>
<br />

16. Al acceder a la url de eclipse-che vemos la pagina de login del mismo.

<p align="center">
<img width="702" alt="Che-login" src="https://user-images.githubusercontent.com/60987042/89838149-1d04fa00-db30-11ea-8c7c-cb12acce3312.png">
</p>

**Nota:** El usuario y el password se configuran en el .Yaml, pero en este caso se dejaron por default por ende se tiene que el User y el Password son admin
<br />

17. Al ingresar las credenciales de acceso vamos a ingresar a eclipse-che.

<p align="center">
<img width="656" alt="Che-home" src="https://user-images.githubusercontent.com/60987042/89838151-1f675400-db30-11ea-85a4-54b013cebc3b.png">
</p>
<br />

# ANEXOS

Si se desea realizar el mismo despliegue desde la cli, pero desde la maquina local se deberían seguir los siguientes pasos:
<br />

## Pre-requisitos 📋

Paso 1: Instale IBM Cloud CLI.

Instale la interfaz de la línea de comandos de IBM Cloud así:
<br />

**Para Mac y Linux ™**
Ejecute el siguiente comando en la terminal:
```
curl -sL https://ibm.biz/idt-installer | bash
```
<br />

**Para Windows™ 10 Pro**_
Pulse con el botón derecho del ratón el icono de Windows™ PowerShell y seleccione **Ejecutar como administrador**, efectué el siguiente comando:

```
[Net.ServicePointManager]::SecurityProtocol="Tls12";iex(New-Object Net.WebClient).DownloadString('https://ibm.biz/idt-win-installer')
```
<br />

Paso 2: Verificar la instalación.
Para verificar que las herramientas de desarrollador y la CLI se han instalado correctamente, ejecute el comando **help**:

```
ibmcloud dev help
```
<br />

Paso 3:	Instalar CLI de OpenShift.
<br />

Desde el siguiente link podremos descargar el respectivo instalador.

```
https://www.okd.io/download.html
```
<br />

Para instalarlo debemos descomprimir la carpeta, encontraremos los siguientes archivos:

<img width="513" alt="5" src="https://user-images.githubusercontent.com/60987042/76979004-60529800-6905-11ea-9830-5d28e2d5c4af.PNG">
<br />

De estos archivos debemos copiar el que tiene por nombre oc y pegarlo en la carpeta bin que encontramos en la siguiente dirección:

```
C:\Program Files\IBM\Cloud\bin
```
<br />

## Referencias

La documentación en linea de IBM Cloud Red Hat OpenShift Managed, se encuentra en el siguiente enlace:

https://cloud.ibm.com/docs/openshift?topic=openshift-getting-started

En la siguiente página se encuentra la información de administración y configuración de Open Shift 3.11.

https://access.redhat.com/documentation/en-us/openshift_container_platform/3.11/
<br />

## Autores ✒️

Equipo *IBM Cloud Tech Sales Colombia*.

