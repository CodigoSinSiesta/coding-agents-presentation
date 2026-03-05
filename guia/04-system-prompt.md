# El System Prompt

## Tiempo estimado
4 minutos

## Puntos clave
- El System Prompt es el conjunto de instrucciones que define el comportamiento del agente
- Es como el "contrato" entre tú y el agente
- Componentes típicos de un System Prompt:
  - **Identidad**: Quién es el agente y qué rol desempeña
  - **Reglas**: Qué debe y qué NO debe hacer
  - **Contexto**: Información sobre el proyecto, arquitectura, tecnologías
  - **Formato**: Cómo debe estructurar sus respuestas
- El System Prompt se configura en archivos específicos:
  - `CLAUDE.md` para Claude Code
  - `AGENTS.md` como formato genérico multi-agente
  - `COPILOT_INSTRUCTIONS.md` para GitHub Copilot
- Sin un buen System Prompt, el agente:
  - No conoce tu arquitectura
  - No sigue tus convenciones
  - Puede sugerir soluciones que rompen patrones
  - Genera código inconsistente

## Datos relevantes
- Un System Prompt puede ser desde 500 hasta 5000+ tokens
- Claude Code lee CLAUDE.md en CADA interacción
- Varios agentes soportan AGENTS.md como formato estándar
- El System Prompt consume contexto pero mejora drásticamente la calidad

## Transición
"Pero, ¿qué pasa si tienes un agente y un subagente? Vamos a ver la diferencia..."

## Notas
- Mostrar ejemplos de System Prompts reales si es posible
- Enfatizar que el System Prompt es INVERTIR tiempo, no desperdiciarlo
- Mencionar que un mal System Prompt = malos resultados
- Conectar con buenas prácticas: el System Prompt es la base
