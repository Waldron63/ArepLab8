# Taller del Diseño de Aplicaciones Seguras

## Introducción

En este laboratorio, se quiere demostrar el uso del desarrollo de una aplicacion, subiendola a servicios LAMBDA, que son apuntados desde un API Gateway.
En este informe se quiere mostrar el desarrollo del laboratorio al montar los servicios y generar las pruebas dadas en cada uno.

### Prerrequisitos

Para el correcto uso del servidor, es necesario tener las siguientes aplicaciones instaladas:
- JAVA
     ```sh
   java -version
   ```
- MAVEN
     ```sh
   mvn -v
   ```
- GIT
   ```sh
   git --version
   ```
(NOTA: si alguna de estas aplicaciones no fue instalada, ir a la página oficial de cada una e instalar la versión recomendada).

### Instalación
1. clonar el repositorio con el siguiente comando y ingresar a la carpeta en donde esta incluido el *pom.xml*:

   ```sh
   git clone https://github.com/Waldron63/ArepLab8.git
   cd ArepLab8
   ```

2. Construir el proyecto:

   ```sh
   mvn clean install
   mvn clean package
   ```
   
  La consola mostrará información parecida a:

<img width="1167" height="205" alt="image" src="https://github.com/user-attachments/assets/7e717e61-00c1-4d54-a120-957dc5765240" />

## Desarrollo:
### Despliegue del servicio MathService.square:
```sh
  public class MathServices {
      public static Integer square(Integer i){
          return i*i;
      }
  }
```
Primero, se implementan las herramientas a trabajar en este laboratorio:
- API Gateway
- Lambda
  
<img width="590" height="211" alt="image" src="https://github.com/user-attachments/assets/3a91b5eb-3df8-4d6d-ba61-716d805cc4a9" />

Dentro del Lambda, se crea una nueva lambda llamada square, por dentro, se cambia el controlador para que tenga la estructura: "edu.eci.com.areplab8.MathServices::square"

<img width="1364" height="732" alt="image" src="https://github.com/user-attachments/assets/bce2bc6c-56f9-4787-92ae-4b36ab45b6ca" />

Ahora, se compila el proyecto y se carga con el archivo .jar del proyecto al Lambda; de esta forma revisamos que funcione con una prueba:

<img width="1447" height="737" alt="image" src="https://github.com/user-attachments/assets/06f2edd8-8da6-4f97-afad-9acb03b1692d" />

Ya viendo que funciona, entramos a API Gateway para crear un nuevo api llamado "/mathservices" y dentro de este colocamos la ruta "/square" que tendrá el GET 

<img width="1577" height="758" alt="image" src="https://github.com/user-attachments/assets/0797ad71-66e0-4b5a-a710-0656248c1e71" />

<img width="1482" height="531" alt="image" src="https://github.com/user-attachments/assets/29af3174-0cfa-401f-ae49-c067943b54c7" />

Para la integracion de las solicitudes, se arman los parametros que se pueden agregar en el path de la URI, para poder enviar la informacion de manera variada y no estatica.

<img width="1580" height="764" alt="image" src="https://github.com/user-attachments/assets/00b4ffa0-07bf-43de-9fcb-f6637448240b" />

<img width="1582" height="580" alt="image" src="https://github.com/user-attachments/assets/f71bf9c4-3867-4531-8eeb-fff76e032d31" />

#### Prueba de aceptacion para square
Se hade la prueba test desde AWS y desde el path dado por el API Gateway

<img width="1592" height="371" alt="image" src="https://github.com/user-attachments/assets/4c80a8f9-0e97-450e-bf86-d4620b48989e" />

<img width="1588" height="728" alt="image" src="https://github.com/user-attachments/assets/3a725f7e-003e-4c57-b8de-19bea1fc2b62" />

<img width="911" height="78" alt="image" src="https://github.com/user-attachments/assets/043f2680-65d9-4594-bc9f-e224401ffd48" />

### Despliegue del servicio MathService.square:
```sh
public class SecurityUtils {
    
    public static User login(User u){
        System.out.println("Username: " + u.getUsername());
        System.out.println("password: " + u.getPassword());
        u.setPassword("");
        return u;
    }
}
```

Dentro del Lambda, se crea una nueva lambda llamada square, por dentro, se cambia el controlador para que tenga la estructura: "edu.eci.com.areplab8.SecurityUtils::login"

<img width="1582" height="770" alt="image" src="https://github.com/user-attachments/assets/99bcb2c7-f4f4-43a1-b501-248674c3cf88" />

Ahora, se compila el proyecto y se carga con el archivo .jar del proyecto al Lambda; de esta forma revisamos que funcione con una prueba:

+<img width="1571" height="549" alt="image" src="https://github.com/user-attachments/assets/8abe6b12-13c5-4eab-9718-e4eddb0cc9fd" />

<img width="1582" height="758" alt="image" src="https://github.com/user-attachments/assets/a5f5f258-2bfe-4f35-9c81-99e61209e3ff" />

Ya viendo que funciona, entramos a API Gateway para crear un nuevo api llamado "/mathservices" y dentro de este colocamos la ruta "/login" que tendrá el GET 

<img width="1578" height="763" alt="image" src="https://github.com/user-attachments/assets/d5226d58-5542-480a-a982-47ad1e8a38fc" />

Para la integracion de las solicitudes, se arman los parametros que se pueden agregar en el path de la URI, para poder enviar la informacion de manera variada y no estatica.

<img width="1580" height="792" alt="image" src="https://github.com/user-attachments/assets/48546aff-7030-4d8a-ad33-8feef455f804" />

#### Prueba de aceptacion para square
Se hade la prueba test desde AWS y desde el path dado por el API Gateway

<img width="1588" height="761" alt="image" src="https://github.com/user-attachments/assets/00c8b4f5-5560-42af-9813-d40929a699db" />

<img width="973" height="79" alt="image" src="https://github.com/user-attachments/assets/267a44ee-2697-440e-becf-fab58cce2d4b" />

## Video de desarrollo
Video de muestra del funcionamiento completo de AWS, despliegue y peticiones:

[Deployment Video](./areplab08.mp4)

## Construido con

[Maven](https://maven.apache.org/index.html) - Dependency Management

[Git](https://git-scm.com) - Version Control System

[AWS academy](https://www.awsacademy.com/vforcesite/LMS_Login) - Instances EC2

## Autor

Santiago Gualdron Rincon - [Waldron63](https://github.com/Waldron63)

