# ¿Qué son las Alucinaciones?

## Tiempo estimado
3 minutos

## Puntos clave
- **Definición**: El LLM genera texto estadísticamente probable que puede ser incorrecto
- El agente NO sabe si lo que genera es verdad o o mentira
- **Tipos de alucinaciones**:
  - **Paquetes inexistentes**: "import { superTool } from 'nonexistent-lib'"
  - **APIs incorrectas**: Métodos que no existen o parámetros inventados
  - **Archivos inexistentes**: Rutas que suenan plausible pero no existen
- **Analogía del arquitecto**:
  - Un arquitecto que no conoce una normativa concreta
  - Inventa una normativa plausible que suena bien "el edificio parece bien diseñado así"
  - El inspector (tú) debe verificar
- **Estadística impactante**: ~30% del código generado puede contener alucinaciones
- El problema NO es que el agente mienta, es que no tiene forma de verificar

## Datos relevantes
- Los LLMs no tienen acceso a verdad, solo a probabilidades
- Las alucinaciones son más comunes en dominios específicos o poco documentados
- Un modelo puede "sonar confiado" incluso cuando está equivocado

## Transición
"Vale, esto es preocupante. ¿Cómo podemos evitar que pase? Vamos a ver las técnicas..."

## Notas
- Usar la analogía del arquitecto para hacer el concepto memorable
- Mostrar los ejemplos reales de alucinaciones (paquetes npm inventados son comunes)
- No asustar a la audiencia, es normal y esperado
- Enfatizar que la verificación es RESPONSABILIDAD DEL DESARROLLADOR
