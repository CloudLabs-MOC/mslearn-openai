# Comience a Usar OpenAI y Cree Una Solución de Lenguaje Natural

### Duración Total Estimada: 4 Horas

## Descripción general

El Servicio Azure OpenAI incorpora los modelos de IA Generativa desarrollados por OpenAI a la plataforma Azure, permitiendo el desarrollo de potentes soluciones de IA con la seguridad, la escalabilidad y la integración de los servicios en la nube de Azure. En este laboratorio, aprenderá a aprovisionar Azure OpenAI como un recurso y a usar Azure OpenAI Studio para implementar y explorar los modelos de OpenAI. Con Azure OpenAI, los desarrolladores pueden crear aplicaciones como chatbots y modelos de lenguaje que se destacan por comprender el lenguaje humano natural. El servicio brinda acceso a modelos de IA entrenados previamente y a un conjunto de APIs y herramientas para personalizar y ajustar estos modelos para cumplir con los requisitos específicos de la aplicación. En este escenario, asumirá el rol de un desarrollador de software encargado de implementar una aplicación para proporcionar recomendaciones de senderismo mediante IA generativa, demostrando técnicas aplicables a cualquier aplicación que utilice las API de Azure OpenAI.

## Objetivo

En este laboratorio práctico, aprenderá a usar OpenAI para crear soluciones de lenguaje natural. Comenzará configurando el entorno de OpenAI en Azure y explorando las características básicas de los modelos de OpenAI para el procesamiento del lenguaje. Al finalizar el laboratorio, creará e implementará una aplicación sencilla que pueda procesar y responder a la entrada del usuario, a la vez que aprenderá a mejorar el rendimiento y la calidad de los resultados del modelo.

- **Comenzar a usar el Servicio Azure OpenAI**: Este ejercicio práctico tiene como objetivo aprovisionar un recurso de Azure OpenAI e implementar un modelo. Explore las capacidades del modelo en el área de juegos (Playground) Completions y luego interactúe con él mediante el área de juegos (Playground) Chat. Afine las respuestas mediante el ajuste de los prompts y los parámetros, y aproveche la generación de código para automatizar las tareas.
- **Utilizar los SDKs de Azure OpenAI en su aplicación**: Este ejercicio práctico tiene como objetivo aprovisionar un recurso de Azure OpenAI, implementar un modelo, establecer y configurar una aplicación en Cloud Shell y luego ejecutar la aplicación, demostrando el ciclo de vida completo desde la creación del recurso hasta la implementación y ejecución de la aplicación.

## Requisitos previos

- Familiaridad con el Servicio Azure OpenAI, Azure CLI, y las APIs REST
- Conocimiento básico de los conceptos de IA y machine learning

## Arquitectura

El flujo de arquitectura para esta tarea comienza con el aprovisionamiento de un recurso de Azure OpenAI dentro de su suscripción de Azure y la implementación de un modelo entrenado previamente mediante Azure OpenAI Studio. A continuación, explorará las capacidades del modelo en el área de juegos (Playground) Completions y probará sus capacidades de conversación en el área de juegos (Playground) Chat, experimentando con diferentes prompts y parámetros para personalizar las respuestas. También investigará las capacidades de generación de código del modelo. En la fase de desarrollo de la aplicación, configurará su entorno de aplicación en Azure Cloud Shell, configurará la aplicación para integrarla con el modelo OpenAI implementado y, por último, ejecutará la aplicación para proporcionar recomendaciones de senderismo mediante IA generativa.

## Diagrama de Arquitectura

 ![Acceda a su Máquina Virtual y Guía de Laboratorio](../media/arch20-3.png)

## Explicación de componentes

1. **Azure OpenAI**: El Servicio Azure OpenAI proporciona acceso REST API a los potentes modelos de lenguaje de OpenAI y estos modelos se integran con sus datos, permitiendo interacciones personalizadas y seguras.
1. **Modelos de Azure OpenAI**: Ofrece modelos de lenguaje grande personalizables y pre-entrenados para diversas aplicaciones de IA. Estos modelos permiten crear potentes soluciones impulsadas por IA mediante la generación de contenido personalizado y contextualmente relevante basado en prompts bien diseñados.
1. **Azure CloudShell**: Azure CloudShell ofrece una experiencia shell integrada basada en navegador para administrar los recursos de Azure. Proporciona un entorno listo para usar con herramientas preinstaladas y acceso tanto a Bash como a PowerShell.

## Comenzando con el Laboratorio

¡Bienvenido al taller **Comience a Usar OpenAI y Cree Una Solución de Lenguaje Natural**! En este laboratorio, aprenderá a usar los modelos de OpenAI para crear soluciones de lenguaje natural. Explorará los conceptos básicos y trabajará en la creación e implementación de aplicaciones que comprenden y procesan el lenguaje. Comencemos con el laboratorio y exploremos las posibilidades de la IA.
 
## Accediendo a Su Ambiente de Laboratorio
 
Una vez que esté listo para comenzar, su máquina virtual y la guía de laboratorio estarán al alcance de su mano dentro de su navegador web.
 
![Acceda a su Máquina Virtual y Guía de Laboratorio](../media/upd-0.png)

### Máquina Virtual & Guía de Laboratorio
 
Su máquina virtual es su caballo de batalla durante todo el taller. La guía de laboratorio es su hoja de ruta hacia el éxito.
 
## Explorando Los Recursos de Su Laboratorio
 
Para obtener una mejor comprensión de sus recursos de laboratorio y credenciales, navegue a la pestaña **Ambiente**.
 
![Explore los Recursos de Laboratorio](../media/upd-1.png)
 
## Utilizando la Función de Ventana Dividida
 
Para mayor comodidad, puede abrir la guía de laboratorio en una ventana separada seleccionando el botón **Ventana Dividida** de la esquina superior derecha.
 
![Utilice la Función de Ventana Dividida](../media/upd-2.png)
 
## Administrando Su Máquina Virtual
 
Siéntase libre de **Iniciar, Detener o Reiniciar (2)** su máquina virtual cuando lo necesite desde la pestaña **Recursos (1)**. ¡Su experiencia está en sus manos!
 
![Administre Su Máquina Virtual](../media/GS3.png)

### Acercar/Alejar Guía de laboratorio

Para ajustar el nivel de zoom de la página del entorno, haga clic en el icono **A↕: 100%** ubicado junto al temporizador en el entorno del laboratorio.

   ![Manage Your Virtual Machine](../media/GS4.png)

## Validación de Laboratorio

Tras completar la tarea, pulse el botón **Validar** en la pestaña Validación integrada en la guía de laboratorio. Si recibe un mensaje de éxito, puede continuar con la siguiente tarea; de lo contrario, lea atentamente el mensaje de error y vuelva a intentar el paso siguiendo las instrucciones de la guía de laboratorio.

   ![Validación en línea](../media/upd-4.png)

## Comenzando con el Portal de Azure
 
1. En LabVM, haga clic en el acceso directo **Azure Portal** del navegador Microsoft Edge, que se crea en el escritorio.
 
   ![Inicie el Portal de Azure](../media/sc900-image(1).png)
 
2. Verá la pestaña **Iniciar sesión en Microsoft Azure**. Aquí, ingrese sus credenciales:
 
   - **Correo electrónico/Nombre de usuario:** <inject key="AzureAdUserEmail"></inject>
 
       ![Ingrese Su Nombre de usuario](../media/upd-5.png)
 
3. A continuación, proporcione su contraseña:
 
   - **Contraseña:** <inject key="AzureAdUserPassword"></inject>
 
       ![Ingrese Su Contraseña](../media/upd-6.png)
 
4. Si se le solicita que permanezca conectado, puede hacer clic en "No".
 
5. Si aparece una ventana emergente de **Bienvenido a Microsoft Azure**, simplemente haga clic en **Cancelar** para omitir la visita guiada.
 
## Contacto de Soporte

El equipo de soporte de CloudLabs está disponible las 24 horas del día, los 7 días de la semana, los 365 días del año, por correo electrónico y chat en vivo para garantizar una asistencia perfecta en cualquier momento. Ofrecemos canales de soporte dedicados y diseñados específicamente para estudiantes e instructores, garantizando que todas sus necesidades se aborden de manera rápida y eficiente.

Contactos de Soporte para Estudiantes:

- Soporte por Correo Electrónico: cloudlabs-support@spektrasystems.com
- Soporte por Chat en Vivo: https://cloudlabs.ai/labs-support

Ahora, haga clic en Siguiente en la esquina inferior derecha para pasar a la página siguiente.

![Comience Su Recorrido Hacia Azure](../media/nlsg6.png)

## ¡¡Feliz aprendizaje!!
