# Práctica 2. Configuración de Grupos de Seguridad en AWS

## 🎯 Objetivos:
Al finalizar la práctica, serás capaz de:
- Crear y configurar grupos de seguridad (Security Groups) en AWS para controlar el tráfico de red en entornos de análisis y procesamiento de datos, aplicando buenas prácticas de seguridad.

## 📝 Requisitos previos:
- Tener acceso a la consola de AWS con permisos suficientes.
- Contar con conocimientos básicos sobre redes, protocolos y puertos.

## 🕒 Duración aproximada:
- 40 minutos.

## 📍 Región de AWS:
- us-west-2 (Oregón)

---

**[⬅️ Atrás](https://netec-mx.github.io/TPRACT_INGDAT_Priv/Capítulo2/lab1.html)** | **[Lista general](https://netec-mx.github.io/TPRACT_INGDAT_Priv/)** | **[Siguiente ➡️](https://netec-mx.github.io/TPRACT_INGDAT_Priv/Capítulo3/lab3.html)**

---

## Instrucciones: 

### Tarea 1: Iniciar sesión en la consola de AWS.

**Descripción:** Accede como usuario IAM.

- **Paso 1.** Dirígete a [AWS Console](https://aws.amazon.com/console).

- **Paso 2.** Haz clic en **Sign in**.

- **Paso 3.** Inicia sesión con:

  - **Account ID or alias:** `Cuenta asignada en el curso`.
  - **IAM username:** `Asignado en el curso`.
  - **Password:** `Asignada en el curso`.

- **Paso 4.** Verifica que estás en la región `us-west-2`.

  ![awstpract1](../images/lab12/img1.png)  

> **TAREA FINALIZADA**

### Resultado esperado:
Obtendrás el acceso exitoso a la consola.

---

## Tarea 2: Acceder a la sección de grupos de seguridad (Security Groups)

- **Paso 1.** En el buscador superior de la consola de AWS, escribe EC2 y selecciona el servicio correspondiente.

    ![awstpract1](../images/lab2/img1.png)

- **Paso 2.** Verifica que estás en la región **Oregon (`us-west-2`)**.

- **Paso 3.** En el menú lateral izquierdo, buscar la sección **Network & Security** y haz clic en **Security Groups**.

    ![awstpract1](../images/lab2/img2.png)

> **TAREA FINALIZADA**

### Resultado esperado:
Accederás a la lista de grupos de seguridad del VPC en la región de Oregón.

---

## Tarea 3: Crea un grupo de seguridad personalizado  

- **Paso 1.** Haz clic en el botón **Create security group**.

> 💡 ***Nota:** Es posible que veas otros grupos de seguridad (SGs); por ahora, puedes ignorarlos.*

    ![awstpract1](../images/lab2/img3.png)

- **Paso 2.** Escribe el nombre: `SG-Analisis-Datos`.

    ![awstpract1](../images/lab2/img4.png)

- **Paso 3.** Escribe la siguiente descripción: `Grupo para acceso controlado a herramientas de analisis de datos`.

    ![awstpract1](../images/lab2/img5.png)

- **Paso 4.** En el menú, selecciona la VPC llamada: `LabVPC`.

    ![awstpract1](../images/lab2/img6.png)

- **Paso 5.** Haz clic en la opción **Create security Group**.

> **TAREA FINALIZADA**

### Resultado esperado:
El grupo de seguridad se ha creado correctamente, con la información básica y en la región adecuada.

---

## Tarea 4: Configurar reglas de entrada (Inbound Rules)

- **Paso 1.** Dentro de la creación del grupo, ve a la sección **Inbound rules** y haz clic en **Edit inbound rules**.

    ![awstpract1](../images/lab2/img7.png)

- **Paso 2.** Agregar una nueva regla para **SSH**:

    - Type: `SSH`  
    - Protocol: `TCP`  
    - Port: `22`  
    - Source: `Anywhere-IPv4` 
    
    ---
    
    ![awstpract1](../images/lab2/img8.png)
    
    ---
    
    ![awstpract1](../images/lab2/img9.png)

- **Paso 3.** Agrega una nueva regla para permitir el acceso al servicio de análisis, como Jupyter Notebook.

  - Type: `Custom TCP` 
  - Port: `8888`  
  - Source: `Anywhere-IPv4`
  
  ---
  
  ![awstpract1](../images/lab2/img10.png)
  
  ---
  
  ![awstpract1](../images/lab2/img11.png)

- **Paso 4.** Agregar una regla para el protocolo HTTP:

  - Type: `HTTP` 
  - Port: `80`  
  - Source: `Anywhere-IPv4`
  
  ---
  
  ![awstpract1](../images/lab2/img10.png)
  
  ---
  
  ![awstpract1](../images/lab2/img14.png)

- **Paso 5.** Agrega una regla para el protocolo HTTPS:

  - Type: `HTTPS` 
  - Port: `443`  
  - Source: `Anywhere-IPv4`
  
  ---
  
  ![awstpract1](../images/lab2/img10.png)
  
  ---
  
  ![awstpract1](../images/lab2/img15.png)

- **Paso 6.** Haz clic en el botón **Save rules** para guardar las reglas de entrada.  

> **TAREA FINALIZADA**

### Resultado esperado:
 Las reglas de entrada se han configurado correctamente en el grupo de seguridad creado en la región de Oregon.

---

## Tarea 5: Configuración de reglas de salida (Outbound Rules)

- **Paso 1.** Revisa la sección **Outbound rules**.

    ![awstpract1](../images/lab2/img12.png)

- **Paso 2.** Verifica que exista una regla creada por defecto con los siguientes parámetros:

    - Type: `All traffic`  
    - Destination: `0.0.0.0/0`
    
    ---
    
    ![awstpract1](../images/lab2/img13.png)

> **TAREA FINALIZADA**

### Resultado esperado:
Las reglas de salida están correctamente configuradas para permitir conectividad total desde el grupo de seguridad.

---

## Tarea 6: Etiquetado del grupo de seguridad.

- **Paso 1.** Haz clic en la sección de **Tags** y luego en **Manage tags**. Posteriormente, agrega una etiqueta con los siguientes valores:

  - Key: `Name`  
  - Value: `Grupo-Seguridad-Datos` 
    
  ---
    
  ![awstpract1](../images/lab2/img16.png)
   
  ---
    
  ![awstpract1](../images/lab2/img17.png)
    
  ---
    
  ![awstpract1](../images/lab2/img18.png)


- **Paso 2.** Después, agrega las siguientes etiquetas adicionales:

  - Key: `Proyecto`, Value: `DataPipeline`  
  - Key: `Ambiente`, Value: `Desarrollo`  
  - Key: `Equipo`, Value: `IngenieriaDatos`
    
  ---
    
  ![awstpract1](../images/lab2/img19.png)

- **Paso 3.** Finalmente, haz clic en **Save changes**.

> **TAREA FINALIZADA**

### Resultado esperado:
El grupo de seguridad ha sido etiquetado correctamente, lo que facilita su identificación y la trazabilidad de costos.

---

## Tarea 7: Validación final del grupo de seguridad

- **Paso 1.** Ve a la lista de grupos de seguridad en la región de **Oregon (`us-west-2`)**.

- **Paso 2.** Busca el grupo `SG-Analisis-Datos` y revisa su configuración. 

- **Paso 3.** Verifica que las reglas coincidan con lo definido previamente.

- **Paso 4.** Copia el `Security group ID` a un **bloc de notas**; lo necesitarás más adelante. 

> **TAREA FINALIZADA**

### Resultado esperado:

El grupo de seguridad está correctamente configurado y verificado en la región de Oregon.

---

> **¡FELICIDADES, HAS COMPLETADO EL LABORATORIO 2!**

## Resultado final:

Has creado un grupo de seguridad específico para entornos de análisis de datos en la región de Oregón, con:

- Reglas de acceso controladas
- Etiquetas bien definidas
- Verificación completa de la configuración

Todo siguiendo buenas prácticas de seguridad en AWS.

---

## Notas y/o consideraciones

- Usa la opción My IP para evitar exponer servicios a todo internet.
- Aplica etiquetas para facilitar auditorías, trazabilidad y control de costos.
- Ajusta la configuración de puertos según las herramientas que utilice tu equipo de datos.
- Este grupo puede asociarse posteriormente a instancias EC2, EMR o servicios de contenedores.
- Revisa periódicamente las reglas de seguridad y mantenlas al mínimo necesario.

## URLS de referencia:
  
- [AWS Security Groups](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)  
- [Best Practices for Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/security-group-rules.html)

---

**[⬅️ Atrás](https://netec-mx.github.io/TPRACT_INGDAT_Priv/Capítulo2/lab1.html)** | **[Lista general](https://netec-mx.github.io/TPRACT_INGDAT_Priv/)** | **[Siguiente ➡️](https://netec-mx.github.io/TPRACT_INGDAT_Priv/Capítulo3/lab3.html)**
