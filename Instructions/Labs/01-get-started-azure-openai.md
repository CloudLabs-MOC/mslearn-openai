# Laboratorio 01: Comenzar a usar el Servicio Azure OpenAI

### Duración Estimada: 40 minutos

## Escenario del Laboratorio
El Servicio Azure OpenAI incorpora los modelos de IA generativa desarrollados por OpenAI a la plataforma Azure, lo que le permite desarrollar potentes soluciones de IA que se benefician de la seguridad, la escalabilidad y la integración de los servicios que ofrece la plataforma de nube de Azure. En este ejercicio, aprenderá cómo comenzar con Azure OpenAI mediante el aprovisionamiento del servicio como un recurso de Azure y el uso de Azure AI Foundry portal para implementar y explorar los modelos de OpenAI. 

## Objetivos del laboratorio
En este laboratorio, completará las siguientes tareas:

- Tarea 1: Aprovisionar un recurso de Azure OpenAI
- Tarea 2: Implementar un modelo
- Tarea 3: Explorar un modelo en el Área de juegos (Playground) Completions
- Tarea 4: Utilizar el Área de juegos Chat
- Tarea 5: Explorar prompts y parámetros 
- Tarea 6: Explorar la generación de código

### Tarea 1: Aprovisionar un recurso de Azure OpenAI

Antes de poder usar modelos de Azure OpenAI, debe aprovisionar un recurso de Azure OpenAI en su suscripción de Azure.

1. En el **Portal de Azure**, busque **OpenAI (1)** y seleccione **Azure OpenAI (2)**.

   ![](../media/nlp1.png)

2. En la hoja **Servicios de IA de Azure | Azure OpenAI**, haga clic en **+ Crear**.

   ![](../media/nls301.png)

3. Cree un recurso **Azure OpenAI** con la siguiente configuración. Haga clic en **Siguiente (6)** tres veces
   
    - **Suscripción**: Predeterminada - Suscripción preasignada **(1)**
    - **Grupo de recursos**: **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
    - **Región**: Seleccione **<inject key="Region" enableCopy="false" /> (3)**
    - **Nombre**: **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject> (4)**
    - **Plan de tarifa**: **Standard S0 (5)**
  
      ![](../media/nls302-1.png)

4. Clic en **Crear**.

5. Espere a que se complete la implementación. Luego, vaya al recurso de Azure OpenAI implementado en el Portal de Azure.

#### Validación

> ¡**Felicitaciones** por completar la tarea! Ahora es momento de validarla. Estos son los pasos:
> - Presione el botón Validar para la tarea correspondiente. Si recibe un mensaje de éxito, puede continuar con la siguiente tarea. 
> - De lo contrario, lea atentamente el mensaje de error y vuelva a intentar el paso, siguiendo las instrucciones de la guía de laboratorio.
> - Si necesita ayuda, comuníquese con nosotros a cloudlabs-support@spektrasystems.com. Estamos disponibles las 24 horas del día, los 7 días de la semana para ayudarlo.

   <validation step="1fa0e87b-eb46-463d-b63b-edf6e2282e16" />

### Tarea 2: Implementar un modelo

Azure OpenAI ofrece un portal basado en la web llamado **Azure AI Foundry portal**, que puede usar para implementar, administrar y explorar modelos. Comenzará su exploración de Azure OpenAI usando Azure AI Foundry portal para implementar un modelo.

1. En el **Portal de Azure**, busque **OpenAI (1)** y seleccione **Azure OpenAI (2)**.

   ![](../media/nlp1.png)

1. En la hoja **Azure AI Services | Azure OpenAI**, seleccione **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject>**

   ![](../media/nls303.png)

1. En el panel de recursos de Azure OpenAI, haga clic en **Go to Azure AI Foundry portal** para navegar a **Azure AI Foundry portal**.

    ![](../media/nls304.png)

1. Haga clic en **Implementaciones (1)** en el panel de navegación izquierdo, haga clic en **+ Implementar modelo (2)** y seleccione **Implementación del modelo base (3)**.

    ![](../media/1.png)

1. En la ventana **Seleccionar un modelo**, busque **gpt-4o-mini (1)**, luego seleccione **gpt-4o-mini (2)** y haga clic en **Confirmar (3)**.

   ![](../media/nlp2.png)

1. Haga clic en **Personalizar**.   

   ![](../media/nlp23.png)

1. Dentro de la interfaz emergente **Implementar modelo**, ingrese los siguientes detalles:
    
    - Nombre de implementación: **my-gpt-model (1)** 
    - Tipo de implementación: **Estendar (2)**
    - Habilitar actualizaciones automáticas de versiones: **Habilitado(3)**
    - Versión de modelo: **2024-07-18 (Predetermindado) (4)**
    - ubicación de recursos: **Sweden Central(5)**
    - Tokens por límite de velocidad por minuto (miles): **8K (6)**
    - Habilitar cuota dinámica: **Habilitado (7)**
    - Haga clic en **crear recurso e implementar (8)**
  
      ![](../media/2.png)

         > **Note**: gpt-4o-mini solo se admite para la finalización del chat y no para la API de finalización.

1.  Haga clic en **Implementaciones (1)** en el panel de navegación izquierdo, haga clic en **+ Implementar modelo (2)** y seleccione **Implementación del modelo base (3)**.

    ![](../media/spansih_model.png)

1. En la ventana **Seleccionar un modelo**, busque **gpt-35-turbo-instruct (1)**, luego seleccione **gpt-35-turbo-instruct (2)** y haga clic en **Confirmar (3)**.

    ![](../media/nlp4.png)

1. Haga clic en **Personalizar**.   

   ![](../media/nlp5.png)    

1. Dentro de la interfaz emergente **Implementar modelo**, ingrese los siguientes detalles:
    
    - Nombre de implementación: **gpt-35-turbo-instruct (1)** 
    - Tipo de implementación: **Estendar (2)**
    - Habilitar actualizaciones automáticas de versiones: **Habilitado(3)**
    - Versión de modelo: **0914(Predetermindado) (4)**
    - ubicación de recursos: **Sweden Central(5)**
    - Tokens por límite de velocidad por minuto (miles): **20K (6)**
    - Habilitar cuota dinámica: **Habilitado (7)**
    - Haga clic en **crear recurso e implementar (8)**

       ![](../media/3.png)


11. Estos implementarán modelos con los que puede experimentar tanto para el chat como para completar tareas a medida que avanza.

      > **Note**: Puede ignorar cualquier error relacionado con la asignación de roles para ver los límites de cuota.


#### Validación

   <validation step="3b4a472e-f956-45d8-b828-3e2cc01c2e88" />

> ¡**Felicitaciones** por completar la tarea! Ahora es momento de validarla. Estos son los pasos:
> - Presione el botón Validar para la tarea correspondiente. Si recibe un mensaje de éxito, puede continuar con la siguiente tarea. 
> - De lo contrario, lea atentamente el mensaje de error y vuelva a intentar el paso, siguiendo las instrucciones de la guía de laboratorio.
> - Si necesita ayuda, comuníquese con nosotros a cloudlabs-support@spektrasystems.com. Estamos disponibles las 24 horas del día, los 7 días de la semana para ayudarlo.


### Tarea 3: Explorar un modelo en el Área de juegos (Playground) Completions

Los *Playgrounds* (Patios de juego) son interfaces útiles en Azure AI Foundry portal que puede usar para experimentar con sus modelos implementados sin necesidad de desarrollar su propia aplicación cliente.

1. En Azure OpenAI Foundry, en el panel izquierdo, debajo de **Patios de juego**, seleccione **Finalizaciones**.

   ![](../media/nlp7.png) 

2. En la página Finalizaciones, asegúrese de que su implementación **gpt-35-turbo-instruct (1)** esté seleccionada, escriba `Generar un cuestionario de 5 preguntas. Para cada pregunta, proporcione las opciones de respuesta y la respuesta correcta (2)` en el mensaje y haga clic en **Generar (3)**.

    ![](../media/nlp8.png)

     > **Note**: La muestra de texto resumido consta de un mensaje que proporciona texto para indicarle al modelo qué tipo de respuesta se requiere e incluye información contextual.

3. La respuesta consiste en una prueba basada en el ejemplo del mensaje.

    ![](../media/nls310.png)

      > **Nota**: El resultado del chat puede variar. La captura de pantalla se proporciona solo como referencia y es posible que no refleje exactamente el mismo resultado.

      > **Nota**: Puede utilizar el botón Regenerar para volver a enviar el mensaje (se han realizado nuevos cambios) y tenga en cuenta que la respuesta puede variar de la original. Un modelo de IA generativa puede producir un nuevo lenguaje cada vez que se llama.

4. En la parte inferior de la página, anote la cantidad de tokens detectados en el texto. Los tokens son las unidades básicas de una indicación: esencialmente palabras o partes de palabras en el texto.

5. Utilice el botón **Ver código** para ver el código que una aplicación cliente usaría para enviar el mensaje. Puede seleccionar su lenguaje de programación preferido. El mensaje contiene el texto que envió al modelo. La solicitud se envía a la API de finalización de su servicio Azure OpenAI.

    ![](../media/nls311.png)

    ![](../media/nls312-1.png)

6. Cierre el código de muestra.

### Tarea 4: Utilizar el Área de juegos Chat

El patio de juegos de *Chat* proporciona una interfaz de chatbot para los modelos GPT 3.5 y superiores. Utiliza la API *ChatCompletions* en lugar de la API *Completions* anterior.

1. En la sección **Patios de juego**, seleccione la página **Chat (1)** y asegúrese de que el modelo **my-gpt-model (2)** esté seleccionado en el panel de configuración.

   ![](../media/nlp10.png) 

1. En la sección **Configuración**, en el cuadro **Mensaje del sistema**, reemplace el texto actual con la siguiente oración: `
El sistema es un profesor de IA que ayuda a las personas a aprender sobre la IA.`. **(1)** y luego haga clic en **Aplicar cambios (2)**.

    ![](../media/nlp11.png)

1. Debajo del cuadro Mensaje del sistema, haga clic en **+ Agregar sección (1)**, seleccione **ejemplos (2)** e ingrese el siguiente mensaje y respuesta en los cuadros designados:

    ![](../media/nlp13.png)

    - **Usuario**: `¿Cuáles son los diferentes tipos de inteligencia artificial?`
    
    - **Asistente**: `Hay tres tipos principales de inteligencia artificial: IA estrecha o débil (como asistentes virtuales como Siri o Alexa, software de reconocimiento de imágenes y filtros de spam), IA general o fuerte (IA diseñada para ser tan inteligente como un ser humano. Este tipo de IA no existe actualmente y es puramente teórica), y la Superinteligencia Artificial (IA que es más inteligente que cualquier ser humano y puede realizar tareas que están más allá de la comprensión humana. Este tipo de IA también es puramente teórica y aún no se ha desarrollado) .`

       ![](../media/nls315.png)
  
    > **Nota**: Se utilizan algunos ejemplos para proporcionar al modelo ejemplos de los tipos de respuestas que se esperan. El modelo intentará reflejar el tono y el estilo de los ejemplos en sus propias respuestas.
  
1. Guarde los cambios haciendo clic en **Aplicar cambios**. 

   ![](../media/nls316.png)

1. posteriormente haga clic en **Continuar** para iniciar una nueva sesión y establecer el contexto de comportamiento del sistema de chat.   

    ![](../media/nlp12.png)

1. En el cuadro de consulta en la parte inferior de la página, ingrese el texto `¿Qué es la inteligencia artificial? (1)`. Utilice el botón **Enviar (2)** para enviar el mensaje y ver la respuesta.

    ![](../media/nlp14.png)

      > **Nota**: Es posible que reciba una respuesta indicando que la implementación de API aún no está lista. Si es así, espera unos minutos y vuelve a intentarlo.

1. Revise la respuesta.

    ![](../media/nlp15.png)

1. luego envíe el siguiente mensaje para continuar la conversación: `¿Cómo se relaciona con el aprendizaje automático?`

1. Revise la respuesta y observe que se conserva el contexto de la interacción anterior (para que el modelo entienda que "eso" se refiere a inteligencia artificial).

1. Utilice el botón **Ver código** para ver el código de la interacción. El mensaje consta del mensaje del *sistema*, los ejemplos breves de mensajes de *usuario* y *asistente*, y la secuencia de mensajes de *usuario* y *asistente* en la sesión de chat hasta el momento.

      ![](../media/nls317.png)

### Tarea 5: Explorar prompts y parámetros 

Puede utilizar el mensaje y los parámetros para maximizar la probabilidad de generar la respuesta que necesita.

1. En el panel **Configuración**, seleccione **Parámetro (1)** y configure los siguientes valores de parámetro:
   
    - **Respuesta máxima (tokens)**: 500 **(2)**
    - **Temperatura**: 0 **(3)**

      ![](../media/nlp16.png)
   
3. Envíe **(2)** el siguiente mensaje en la sesión de chat **(1)**

    ```
   Escribe tres preguntas de opción múltiple basadas en el siguiente texto.

   La mayoría de las soluciones de visión por computadora se basan en modelos de aprendizaje automático que se pueden aplicar a la información visual de cámaras, videos o imágenes.*
   
   - La clasificación de imágenes implica entrenar un modelo de aprendizaje automático para clasificar imágenes en función de su contenido. Por ejemplo, en una solución de monitoreo de tráfico, podría usar un modelo de clasificación de imágenes para clasificar imágenes según el tipo de vehículo que contienen, como taxis, autobuses, ciclistas, etc.*
   
   - Los modelos de aprendizaje automático de detección de objetos están entrenados para clasificar objetos individuales dentro de una imagen e identificar su ubicación con un cuadro delimitador. Por ejemplo, una solución de monitoreo de tráfico podría utilizar la detección de objetos para identificar la ubicación de diferentes clases de vehículos.*
   
   - La segmentación semántica es una técnica avanzada de aprendizaje automático en la que los píxeles individuales de la imagen se clasifican según el objeto al que pertenecen. Por ejemplo, una solución de monitoreo de tráfico podría superponer imágenes de tráfico con capas de "máscara" para resaltar diferentes vehículos usando colores específicos.
    ```

     ![](../media/nlp17.png)    

4. Revise los resultados, que deben consistir en preguntas de opción múltiple que un maestro podría usar para evaluar a los estudiantes sobre los temas de visión por computadora en el mensaje. La respuesta total debe ser menor que la longitud máxima especificada como parámetro.

      ![](../media/nls319.png)

5. Revise los resultados, los cuales deben consistir de preguntas de opción múltiple que un maestro podría usar para evaluar a los estudiantes sobre los temas de visión artificial en el prompt. La respuesta total debe ser menor que la longitud máxima que especificó como parámetro.

    Observe lo siguiente sobre el prompt y los parámetros que utilizó:

    - El prompt indica específicamente que el resultado deseado debe ser tres preguntas de opción múltiple.
    
    - Los parámetros incluyen *Temperatura*, que controla el grado en el que la generación de respuestas incluye un elemento de aleatoriedad. El valor **0** utilizado en su envío minimiza la aleatoriedad, lo que da como resultado respuestas estables y predecibles.

### Tarea 6: Explorar la generación de código

Además de generar respuestas en lenguaje natural, puede utilizar modelos GPT para generar código.

1. En el **panel de configuración**, bajo **Mensaje del sistema**, ingrese el mensaje del sistema: `Usted es un desarrollador de Python (1)`. Luego guarde los cambios haciendo clic en **Aplicar cambios (2)** y haga clic en **Continuar** cuando se le solicite.

      ![](../media/nlp18.png)

2. En el panel **Sesión de chat**, seleccione **Borrar chat** para borrar el historial de chat e iniciar una nueva sesión.

      ![](../media/nls321.png)  

3. Envíe el siguiente mensaje de usuario:

    ```
    Write a Python function named Multiply that multiplies two numeric parameters.
    ```

4. Revise la respuesta, que debe incluir un código de Python de ejemplo que cumple con el requisito en el prompt.

   ![](../media/task-6-last.jpg)

## Resumen

En este laboratorio, ha logrado lo siguiente:
-   Aprovisionar un recurso de Azure OpenAI
-   Implementar un modelo de Azure OpenAI dentro de Azure AI Foundry portal
-   Usar el área de juegos de chat para utilizar las funcionalidades de prompts, parámetros y generación de código

### Ha completado con éxito el laboratorio
