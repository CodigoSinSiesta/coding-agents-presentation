# 12-Factor Agents

## Tiempo estimado
3 minutos

## Puntos clave
- **Origen**: Dexter Horthy, fundador de HumanLayer. En el espíritu de los 12 Factor Apps de Heroku.
- **Tesis del repo `humanlayer/12-factor-agents`**: tras hablar con +100 fundadores, todos chocan al **70-80% de calidad** usando frameworks como crewai/langchain/langgraph. Para superar ese muro hay que reverse-engineerar el framework, y normalmente acaba en rewrite desde cero.
- **Punto fundamental**: los buenos agentes son sobre todo **software bien escrito**, no llamadas a un framework mágico. La mayoría de productos que se anuncian como "AI Agents" son código determinista con pasos LLM espolvoreados en el sitio justo.
- **Los 12 factores en 3 grupos**:
  - **Owning** (Factores 2, 3, 8): tus prompts, tu context window, tu control flow son CÓDIGO FUENTE versionado, no caja negra de la librería.
  - **Composición** (Factores 1, 4, 7, 10): NL→tool calls, tools como structured outputs, contactar humanos como tool call, agentes pequeños y enfocados.
  - **Operación** (Factores 5, 6, 9, 11, 12): unificar estado, launch/pause/resume, errores compactos, trigger desde cualquier sitio, reducer stateless.
- **Honorable mention** — Factor 13: "pre-fetch all the context you might need". Si sabes que vas a necesitar algo, no dejes que el agente decida llamar a la tool: pásaselo de entrada.

## Datos relevantes
- Talk de Horthy en AI Engineer World's Fair: youtube.com/watch?v=8kMaTybvDUw
- 12-factor agents está en GitHub bajo `humanlayer/12-factor-agents` (CC BY-SA 4.0).
- Encaja con la idea del Factor 10 ("small focused agents") que sirve de conexión natural con el Slide 5 (Agentes y Sub-agentes) y con Harness Engineering del Slide 12.

## Transición
"Pero, ¿qué necesita el agente para cumplir esos factores? Vamos a hablar del context window..."

## Notas
- Pasar rápido por la grid de 12 (no leer cada uno: que la audiencia los escanee).
- Detenerse en 2 (own your prompts) y 10 (small focused agents) que son los más actionable.
- La cita de Horthy ("código determinista con pasos LLM espolvoreados") suele provocar risas y asentimientos.
- Conectar con el slide siguiente: el factor 3 (own your context) es la introducción a "Gestión de contexto".
