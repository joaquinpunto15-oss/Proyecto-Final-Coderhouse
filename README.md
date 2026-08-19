# Sistema-Lead-de-automatizacion-con-IA-1-

Descripcion

Sistema autónomo de automatizacion para la gestion y clasificacion de leads comerciales

El sistema recibe leads mediante gmail, procesa la información utilizando un modelo de IA
(google gemini y no chatgpt porque cobra), registra y actualiza la informacion en Notion y utiliza un proceso
human-in-the-loop antes de ejecutar acciones criticas.

- Stack tecnológico

Orquestador: make
Base de datos: notion
Procesamiento IA: google gemini 
Canal de entrada y salida: gmail
Formato estructurado: JSON
Validación humana: gmail y router de make

- Flujo principal
1. Notion recibe un nuevo lead
2. Gemini analiza el lead y genera una respuesta estructurada
3. JSON estructura los datos generados por la IA
4. Notion almacena y actualiza la información del lead en el notion
5. El Router determina la ruta correspondiente
6. Se solicita aprobación humana antes de una acción critica
7. Segun la decisión humana:
   - Approved → continúa el proceso
   - Rejected → registra el rechazo
   - Pending → mantiene el lead pendiente
11. Los errores se registran en notion


-Base de datos
La base de datos principal en el notion contiene información de los leads:
- Lead/Ticket
- Email
- Empresa
- Descripcion
- Fecha
- Score
- Prioridad
- Estado
- Propuesta AI
- Recomendacion AI
- Decisión
- Categoria
- Intencion
- Error


- Human-in-the-Loop
El sistema no ejecuta automáticamente una acción critica ya que antes de continuar, se solicita una decisión humana mediante un correo de gmail al que debe respondder

Las rutas disponibles son:
- Approved
- Rejected
- Pending


- Gestión de errores
El sistema incorpora rutas de error y mecanismos de recuperación para evitar
que un fallo de API detenga todo el proceso

Los errores se registran en Notion para permitir su seguimiento

- Dashboard del la tabla "Lead" en el notion
https://malachite-bolt-bb3.notion.site/Dashboard-de-Leads-3c1b0571c2fb80859f82f44e1c746418?source=copy_link


Aviso: El nodo de "Watch mail" funciona correctamente, solo que por la extensa cantidad de correos que tengo en mi gmail la respuesta del "APPROVED" o el "REJECTED" no la llega a leer (tardaria leyendo los correos), por lo que se debe destinar una cuenta unica de empresa para el proceso. 

El dashboard permite visualizar los principales indicadores del sistema:
- Total de leads
- Leads aprobados
- Leads rechazados
- Leads con error
