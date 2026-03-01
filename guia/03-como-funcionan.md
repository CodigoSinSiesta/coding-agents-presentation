# ¿Cómo funcionan por dentro?

## Tiempo estimado
4 minutos

## Puntos clave
- El ciclo de trabajo de un agente sigue 4 pasos fundamentales:
  1. **Recibe instrucción**: Lees el System Prompt y tu prompt del usuario
  2. **Razona**: El LLM analiza qué necesita hacer
  3. **Ejecuta**: Usa herramientas (leer archivos, hacer tool calls)
  4. **Itera**: Repite hasta completar la tarea
- Los componentes clave del agente:
  - **LLM**: El cerebro que razona y genera texto
  - **Tools**: Funciones para interactuar con el mundo exterior
  - **Memory**: Contexto conversacional y conocimiento
  - **Planning**: Capacidad de descomponer tareas complejas
- El agente tiene acceso a:
  - Archivos del proyecto
  - Terminal / comandos shell
  - APIs y servicios externos
  - Git y control de versiones
- La diferencia con un chatbot: el agente PUEDE actuar, no solo hablar

## Datos relevantes
- El contexto se acumula con cada interacción
- Las tool calls consumen tokens y tiempo
- El agente puede cometer errores y necesita iterar
- La calidad del output depende de la calidad del input (contexto)

## Transición
"Todo este comportamiento depende de instrucciones claras. Vamos a ver qué es el System Prompt..."

## Notas
- Usar la analogía del ciclo para explicar el flujo
- Recorrer los 4 pasos visualmente
- Mencionar que esto pasa MILES de veces en una sesión de coding
- Hacer énfasis en que el agente no es mágico: sigue un proceso lógico
- Conectar con la siguiente slide: el System Prompt es la base de todo
