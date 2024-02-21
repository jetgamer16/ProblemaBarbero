# ProblemaBarbero - JOSE ENRIQUE PARDO


## 1-Contenidos Principales del problema:

En el sistema del "Barbero Dormido," hay tres componentes clave.

 **Barbero:**
  - El barbero debe atender a los clientes en la barbería.
  - Puede tener los siguientes estados: trabajando o durmiendo en la silla de barbero
  - Cuando está trabajando, atiende a los clientes en la silla de barbero
  - Si no hay trabajo se pone a dormir en la silla de barbero hasta que llegue un cliente

 **Silla de Barbero:**
  - La silla de barbero se utiliza para interactuar con el estado del barbero.
  - Puede estar ocupada si el barbero está trabajando o disponible si el barbero está libre y dispuesto a atender a otro cliente
  - Este componente es esencial para la sincronizacion y para que los clientes comprueben si pueden ser atendidos

 **Sillas de Espera:**
  - Las sillas de espera es donde los clientes esperan mientras el barbero trabaja
  - Este espacio es limitado, lo que significa que solo un número específico de clientes puede esperar
  - Las sillas de espera forman parte crucial de la gestión de la cola de espera:
    - si la cola se encuentra llena los clientes no podran ponerse en la cola de espera

## 2-Interacciones Principales entre los componentes:

**El problema del barbero tiene bastantes interacciones ya que todo esta conectado con todo,
es un triangulo entre Barbero-Cliente y de por medio la silla del Barbero**

 **Llegada de Clientes:**
  - Si el barbero está durmiendo: **El cliente lo despierta y le atiende**
  - Si el barbero está ocupado: **Revisa las sillas de espera**
    - Si hay sillas libres: **Siéntate y espera tu turno en la cola**
    - Si no hay sillas: **Ciao Ciao...** (A.K.A se va)

 **Cola de Espera:**
  - Se usa una cola tipo fila. Llegas al final cuando llegas y sales cuando te atienden o decides irte
  - Utilizando semaforos o bloqueos para que todo sea "ordenado".
  
 **Atención del Barbero:**
  - El barbero atiende al que ha estado esperando más tiempo cuando está libre.
  - Después de atender, mira si hay más en la cola:
    - Si hay mas clientes atiende al siguiente.
    - Si no pues... Vuelve a dormirse! 

 **Concurrencia y Sincronización:**
  - Para evitar atascos, usamos semáforos o bloqueos. Así, cada uno espera su turno y todo marcha sin problemas.
 
 **Justicia y Eficiencia:**
  - Cada vez que entre un cliente aumenta la prioridad a los que han esperado más tiempo.
  - Nos aseguramos de que siempre haya alguien para ser atendido, así no perdemos tiempo esperando y el barbero no se aburre.

## 3-Flujo de Eventos en la Barbería

**Llegada de un Cliente:**
- Un Cliente llega a la barbería.
- El Cliente comprueba si el barbero está despierto o dormido.

**Decisiones del Cliente:**
 Si el barbero está dormido:
  - Cliente despierta al barbero.
  - Cliente se sienta en la silla de barbero para ser atendido.
 Si el barbero está despierto:
  - Cliente comprueba las sillas de espera.
    - Si hay sillas disponibles:
      - Cliente se sienta en una silla de espera.
    - Si no hay sillas disponibles:
      - Cliente se va.

**Manejo de la Cola de Espera:**
- Si el cliente se sienta en la silla de espera, se añade a la cola.
- Utilizar semáforos o bloqueos para garantizar acceso seguro a la cola de espera.
- Notificación al barbero cuando un cliente se añade a la cola.

**Atención del Barbero:**
- Cuando el barbero está despierto:
  - Barbero atiende al cliente que ha estado esperando más tiempo en la cola.
  - Utilizar semáforos o bloqueos para evitar acceso concurrente a la cola.

**Resolución de Condiciones de Carrera:**
- Utilizar mecanismos de sincronización para evitar que múltiples clientes accedan a la silla de barbero al mismo tiempo.
- Evitar despertar innecesario del barbero si no hay clientes en espera.
- Garantizar que la cola de espera se maneje de manera segura y en orden de llegada.

**Finalización de la Atención:**
  - Después de atender a un cliente, el barbero verifica si hay otros clientes en espera.
    - Si hay clientes en la cola $\rightarrow$ el barbero atiende al siguiente cliente.
    - Si la cola está vacía $\rightarrow$ el barbero vuelve a dormirse.

**Cliente Atendido o Se Va:**
- Cliente es atendido y se retira de la cola.
- Cliente se va si decide abandonar la espera.


##Conclusión:##
- El problema del barbero dormilón destaca un sistema complejo de la programación concurrente al organizar varios porcesos al mismo tiempo
- Segun las decisiones que se toman a la hora de programar solo para evitar conflictos y lograr una ejecucion eficiente y "ordenada". 


