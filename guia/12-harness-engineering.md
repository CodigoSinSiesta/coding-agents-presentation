# Harness Engineering

## Tiempo estimado
4 minutos

## Puntos clave
- **Origen**: Ryan Lopopolo, member of technical staff en OpenAI. Talk en AI Engineer London (abril 2026) + artículo `openai.com/index/harness-engineering`. Token billionaire (>$1.000/día en tokens). Lleva 9 meses prohibiendo a su equipo abrir el editor.
- **Tesis "code is free"**:
  - La implementación deja de ser el recurso escaso. El código es libre: gratis de producir, refactorizar y borrar.
  - Cada engineer tiene 5-50-5.000 colaboradores 24/7 limitados solo por GPU y presupuesto de tokens.
  - Migraciones que llevaban 6 meses se cierran lanzando 15 agentes en paralelo.
  - Los P3 dejan de morir en la cola.
- **Recursos escasos en el nuevo régimen**: tiempo humano, atención (humana y del modelo), context window. NO el tiempo de teclear.
- **El repo es prompt persistente**: cada lint, cada test, cada error message, cada reviewer agent en CI es prompt que se reactiva cuando toca. Escríbelo una vez, durabilidad infinita.
- **3 patrones operativos**:
  - **Reviewer agents por persona**: cada engineer documenta su rol técnico (front-end, reliability, scalability). Un agent por persona se ejecuta en CI bloqueando merges con esa lente.
  - **Garbage Collection Friday**: una vez a la semana, todo el equipo convierte feedback humano en lints/tests/docs. Comentarios repetidos en code review → guardrail automático.
  - **Skills para escribir prompts**: cuando escribir prompts a mano se repite, shellea al agente con una skill que los genere a partir de cookbooks.
- **Convergencia destacada**: el mismo patrón emerge en OpenAI (Lopopolo), Y Combinator (Garry Tan / gstack) y HumanLayer (Horthy / 12-factor). Persona-based review se ha vuelto pieza estable, no moda.

## Datos relevantes
- Cita memorable: *"Cada vez que tienes que decirle 'continúa' al agente es un fallo del harness."*
- Anécdota: Lopopolo ata el laptop al asiento trasero del coche y deja al agente cocinando el trayecto a casa.
- Implicación: el código deja de ser el documento autoritativo. La spec implícita (lints, tests, docs, reviewer agents) sí lo es. Cambiar de modelo equivale a cambiar de backend de codegen (LLVM → Cranelift).

## Transición
"Y si tu rol es operacionalizar, no teclear... ¿estás preparado para el cambio?"

## Notas
- Énfasis en la cita de "continúa = fallo del harness" — hace que la audiencia se cuestione su práctica.
- Conectar con el slide 8 (Buenas prácticas, especialmente el DO 7: "lee el código del PR, no solo el plan") y con el slide 9 (12-factor, Factor 8: own your control flow).
- Si la audiencia es senior, profundizar en "Garbage Collection Friday" como ritual de equipo. Si es junior, quedarse en "code is free" y por qué cambia el rol.
- No vender gstack/Codex/Claude Code como tools concretas — el patrón es lo que importa, las tools cambian.
