# Gestión de Contexto

## Tiempo estimado
4 minutos

## Puntos clave
- **¿Qué hay en el contexto?** (capas de información):
  - **System Prompt**: ~2k tokens, define comportamiento base
  - **Historial de conversación**: Variable, acumula con cada interacción
  - **Archivos leídos (tool calls)**: Grandes, contenido del proyecto
  - **Resultados de herramientas**: Variable, outputs de comandos
  - **Límite de contexto**: ~200k tokens (peligro de "olvido")
- **Archivos de contexto por herramienta**:
  - `CLAUDE.md`: Arquitectura, reglas, comandos
  - `AGENTS.md`: Formato estándar multi-agente, instrucciones de proyecto
  - `copilot-instructions.md`: Personalización de Copilot Chat
- **Pro tip crítico**: Empieza siempre con un CLAUDE.md o AGENTS.md básico
- El agente lee estos archivos en CADA conversación
- **Problema del contexto largo**: Más caro, más probabilidad de que el modelo "olvide" información temprana

## Datos relevantes
- Claude Code lee CLAUDE.md automáticamente al inicio
- Varios agentes soportan AGENTS.md como formato estándar
- El límite de 200k tokens es real, no teórico
- El contexto se degrada con conversaciones largas

## Transición
"Vamos a ver todo esto en acción con una demo real..."

## Notas
- Mostrar visualmente las capas de contexto
- Enfatizar que el System Prompt es la base, todo lo demás se construye sobre él
- Mencionar el problema de "olvido" en conversaciones largas
- Recomendar mantener el foco y evitar digresiones largas
- Conectar con la demo: veremos estos archivos en acción
