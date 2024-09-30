# 1.- Creación de diccionarios con PYDICTOR Y DYMERGE

Vamos a trabajar con la herramienta **Pydictor**, que permite la creación de diccionarios para fuerza bruta. Sus principales características son las siguientes:

## Instalación de Pydictor y Dymerge 
### Instalación de Pydictor:
1. Entrando en root procedemos a descargarnos los repositorios de Pydictor con el siguiente comando:
   ```bash
   wget https://raw.githubusercontnet.com/landgrey/pydictor/master/pydictor.py
---
   # ![image](https://github.com/user-attachments/assets/bb13987d-9762-4071-9a08-b67359b5557d)
   # ![image](https://github.com/user-attachments/assets/ef8c9d76-917b-4b98-90e9-84762be6af9a)

2. Procedemos a la creación de los dos diccionarios mediante Pydictor:
   - Diccionario de números de 1 cifra hasta máximo 6 cifras.
     ```bash
     python3 pydictor.py -base d --len 1 6 -o diccionario_numeros.txt
---
   # ![image](https://github.com/user-attachments/assets/aa254a0c-59b4-4114-adfb-180a37fb76ed)
   # ![image](https://github.com/user-attachments/assets/c46b12a4-3844-45c7-b983-9a9abfd95bfe)

  - Diccionario de letras de 1 crifa hasta máximo 6 cifras.
     ```bash
     python3 pydictor.py -base L --len 1 6 -o diccionario_letras.txt
---
   # ![image](https://github.com/user-attachments/assets/7f3ff5c7-9cb3-49ce-8874-781e6d46c75e)


   - Entrando dentro de la carpeta de /pydictor/results podemos observar como ser han creado los dos diccionarios requeridos.
   # ![image](https://github.com/user-attachments/assets/09e11f1a-e918-4abb-bc1c-4c590cc2f4c6)

3. Continuamos instalando Dymerge para la fusión de los dos diccionarios creados anteriormente:
   - Primero procedemos a actualizar la lista de paquetes:
     ```bash
     apt update --fix-missing
---
   # ![image](https://github.com/user-attachments/assets/b2b2f311-bc88-4d51-9acb-3a59ced33cf3)

   - Segundo si no teníamos instalado python3 lo hacemos, pero también nos sirve con python2.
   # ![image](https://github.com/user-attachments/assets/72c206cf-3745-477d-957c-dff94be49bd6)

   - En tercer lugar clonaremos el archivo para poder usar dymerge.git
     ```bash
     git clone https://github.com/ikerlur/dymerge.git
---
   # ![image](https://github.com/user-attachments/assets/bedbb5a9-9fbc-4ccd-8429-66dcf9b654b2)
 
   - Con el siguiente comando procedemos a fusionar los dos diccionarios y después comprobamos, en la ruta que hayamos puesto, que se ha creado correctamente:
     ```bash
     python2 dymerge.p /home/alumno/pydictor/results/diccionario_numeros.txt /home/alumno/pydictor/results/diccionario_letras.txt -o /home/alumno/Dowloads/Diccionario.txt
---
   # ![image](https://github.com/user-attachments/assets/28f373ea-455e-4271-ab8a-0adecf5a7fc5)
   # ![image](https://github.com/user-attachments/assets/e8db4df1-6fb1-4938-b9fe-05a6725364bb)

# 2. Uilizar diccionarion con Hydra para simular un ataque de fuerza bruta en SSH
1. Instalar OpenSSH:
   - Procedemos a actualizar los repositorios del sistema:
   #  ![image](https://github.com/user-attachments/assets/5726b28d-1f21-4506-94ec-4f1236027e0f)
     
   - Con el siguiente comando procedemos a instalar OpenSSH
      ```bash
      sudo apt install openssh-server
---
   # ![image](https://github.com/user-attachments/assets/e9ba9ab0-1890-4aa9-8fb8-fa8a66504f2a)

2. Iniciar y configurar el servidor SSH:
   - Iniciamos el servidor SSh
   # ![image](https://github.com/user-attachments/assets/35ed6e31-d5be-476c-89b5-df03653993ea)
   - Comprobamos el estado
   # ![image](https://github.com/user-attachments/assets/961398d9-a324-42c3-b6a1-97169e13f357)
   - Habilitamos el servicio y volvemos a comprobar el estado.
   # ![image](https://github.com/user-attachments/assets/d924e8c1-9344-4c5c-ad62-29258a6f53bb)

3. CREAR UN USUARIO
   - Creamos un usuario y le asignamos una contraseña, la cual descifraremos más adelante
   # ![image](https://github.com/user-attachments/assets/110d0b85-c5ec-4107-8126-cd7d9c3bd7ca)

4. Conectar al servidor SSH
   - Conectamos el usuario creado al servidor SSH con el siguiente comando sencillo:
   #  ![image](https://github.com/user-attachments/assets/e4622575-26db-4a51-93c4-291dca896d75)

5. Simular un ataque de fuerza bruta
   - Procedemos a la instalación de hydra con el siguiente comando:
     ```bash
        sudo apt install hydra -y
---
   # ![image](https://github.com/user-attachments/assets/cab64b2e-d5ae-4497-81d6-0b8b7d381b6a)
   - Con el siguiente comando realizaremos el ataque a objetivo_victima3 para descubrir su contraseña, no olvides remplazar la ruta por la que este en tu máquina:
     ```bash
        hydra -l objetivo_victima3 -P /home/alumno/Dowloads/Diccionario.txt -t 4 -V ssh://localhost
   # ![image](https://github.com/user-attachments/assets/a32fda47-b24d-46ab-b985-e31c23fbf21b)

6. Revisar los logs del sistema
   - En mi caso no tenía los logs instalados por lo que procedí a instalarmelos y a volver  a realizar el ataque para que se me guarden. En las siguientes capturas lo podemos observar.
   # ![image](https://github.com/user-attachments/assets/57cc5dfd-bbb2-45d1-b1f7-a0732dde5b78)
   - Con el siguiente comando lo instalaremos:
     ```bash
        sudo apt install --fix-missing rsyslog -y
---
   # ![image](https://github.com/user-attachments/assets/98b0b52c-1c2c-40d7-9727-fa42f3446565)

   - Iniciamos el ryslog y comprobamos su estado
   # ![image](https://github.com/user-attachments/assets/d98da4c4-7ac8-4837-aaa6-274bc105eb60)

   - Entramos en el fichero sshd_config para modificar un parametro que es el que nos va a dar los logs de haber hecho el ataque mediante SSH. Dentro del fichero procedemos a quitar # de la linea señalada.
   # ![image](https://github.com/user-attachments/assets/e4792d27-19ee-41f9-a726-b65d2daf1ea7)
   # ![image](https://github.com/user-attachments/assets/e58d9e30-9165-4b9e-8f94-1579da9c7323)

   - Hacemos un ls y comprobamos que tenemos ya instalado correctamente "auth.log"
   # ![image](https://github.com/user-attachments/assets/b36f36a2-6c6b-43ff-8589-3d196d186738)
   
   - Al hacer un cat auth.log podemos observar todos los parametros que se han utilizado para realizar el ataque.
   # ![image](https://github.com/user-attachments/assets/7533eeed-32ce-47f4-a24a-aec0d5196106)


# 3.- Utilizar diccionarion con Hydra para simular un ataque de fuerza bruta con HTTP
1. Instalar y configurar DVWA(https://github.com/digininja/DVWA) como una aplicación web vulnerable en tu servidor Apache local.
   
   # ![image](https://github.com/user-attachments/assets/d4dd2aa2-dcaa-496c-bffd-dff7b4c8ce14)

   # ![image](https://github.com/user-attachments/assets/dfb3ca15-63aa-44c8-850a-9ac6e6c364f9)

   # ![image](https://github.com/user-attachments/assets/8e2fb5f9-c8ea-49a1-9f52-6e6b0179da43)

   # ![image](https://github.com/user-attachments/assets/d19628cd-68e8-4a4a-ab29-722ea4d40fa9)

   # ![image](https://github.com/user-attachments/assets/c83c060a-400f-4e4a-918f-5bd9c837234c)

   # ![image](https://github.com/user-attachments/assets/de840c55-9e5f-4d4e-9213-97c5555b4553)

   - c. Configurar la base de datos
Configura MySQL y crea una base de datos para DVWA:
   # ![image](https://github.com/user-attachments/assets/8ac2daef-5b0c-4708-9173-445181cd812d)
   # ![image](https://github.com/user-attachments/assets/44b22e1e-f9cb-4b70-b983-5668cf931a0c)
      
   ![image](https://github.com/user-attachments/assets/e1f78e08-611d-4093-ae78-e300413c84bd)


   - d. Configuración de DVWA
      Edita el archivo de configuración de DVWA:
   # ![image](https://github.com/user-attachments/assets/38573be2-2c02-4098-9bf3-e985e1f06cc6)
   # ![image](https://github.com/user-attachments/assets/d04e41c9-1a61-4074-b43e-28bf7d162ec8)
   # ![image](https://github.com/user-attachments/assets/0be32810-d91b-4598-b444-68391ee730f5)

   - e. Configurar permisos
   # ![image](https://github.com/user-attachments/assets/ff9f6680-4ccc-4275-8e22-a90717093d81)

   # ![image](https://github.com/user-attachments/assets/f44c3848-6931-42ab-9628-e1735b70bee7)

   # ![image](https://github.com/user-attachments/assets/1e68ab4c-67c4-4986-892f-84a9855c22ce)

   - http://localhost/DVWA
   # ![image](https://github.com/user-attachments/assets/53aec449-a907-401e-ac9e-ff87ee82880e)

2. Identificar los detalles del formulario de login para poder construir el ataque.

   # ![image](https://github.com/user-attachments/assets/a67cbb94-5509-4470-873e-1f8cbeb19571)
   # ![image](https://github.com/user-attachments/assets/2dcb4aca-1d4a-44d3-b6f5-07f3b44c98ef)

3. Usar Hydra para realizar un ataque de fuerza bruta, utilizando diccionarion
   - Si no tenemos instalado hydra, lo hacemos con el siguiente comando.
     ```bash
     apt install hydra
---
   # ![image](https://github.com/user-attachments/assets/4cff40f7-d8c3-4e80-8aea-7849e1b613ea)




   
