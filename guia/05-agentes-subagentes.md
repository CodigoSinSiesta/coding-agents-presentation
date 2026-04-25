# Agentes vs Subagentes

> **Pie del slide (abril 2026)**: la taxonomía canónica de IBM cita 7 roles que cualquier agente complejo termina necesitando: **doer · planner · tool operator · learner · critic · supervisor · presenter**. Sirve de checklist: si tu agente entrega outputs incoherentes te falta `critic`; si pierde el hilo te falta `supervisor`; si fabrica datos te falta `learner`.

## Tiempo estimado
3 minutos

## Puntos clave
- **Agente principal**: Coordina el trabajo general
  - Recibe la instrucción del usuario
  - Descompone tareas complejas
  - Delega a subagentes especializados
- **Subagentes**: Especialistas en tareas específicas
  - Reciben instrucciones específicas del  - Tienen su propio contexto acotado
  - Devuelven resultados al agente principal
- Ejemplos de subagentes:
  - Subagente de testing: genera y ejecuta tests
  - Subagente de documentación: escribe docs
  - Subagente de refactorización: reestructura código
  - Subagente de revisión: revisa código en busca de bugs
- Beneficios de la arquitectura multi-agente:
  - Mayor especialización
  - Contextos más enfocados
  - Mejores resultados en tareas específicas
- Anatomía de la comunicación:
  - Agente → subagente: instrucción específica
  - Subagente → agente: resultado + contexto

## Datos relevantes
- Claude Code puede invocar subagentes automáticamente
- El contexto del subagente es más pequeño y enfocado
- La coordinación entre agentes es clave para tareas complejas

## Transición
"Pero, ¿qué pasa cuando el agente se equivoca? Vamos a hablar de alucinaciones..."

## Notas
- Usar la analogía de un equipo de trabajo: manager + especialistas
- Mencionar que no siempre necesitas subagentes para tareas simples
- Enfatizar que la comunicación entre agentes consume tokens
- Mostrar ejemplo visual del flujo de comunicación
