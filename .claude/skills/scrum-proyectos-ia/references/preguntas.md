# Banco de preguntas

Selecciona según el contexto; no hace falta usarlas todas. Agrupa en rondas de 3–5.

## Fase 1 — Scrum Master (inicio)

### Identidad y visión
- ¿Cómo se llama el proyecto?
- ¿Qué problema resuelve? ¿Para quién?
- ¿Qué pasa hoy sin este sistema? (proceso actual, herramientas, dolor)
- ¿Cómo sabremos que el proyecto fue un éxito? (métrica: usuarios, tiempo ahorrado, ingresos, errores reducidos)
- ¿Quién paga o patrocina el proyecto? ¿Quién toma las decisiones finales?

### Tiempo
- ¿Cuánto tiempo hay para desarrollar? ¿Hay una fecha límite dura?
- ¿Hay hitos obligatorios (demo a inversionistas, piloto con un cliente, fecha regulatoria)?
- ¿Qué duración de sprint prefieren? (recomendar 1 semana con IA; 2 si la revisión humana es lenta)
- ¿Cuántas horas por semana dedica cada persona?

### Equipo y roles
- ¿Quién será el Product Owner (decide prioridades y acepta historias)?
- ¿Quién hará de Scrum Master?
- ¿Cuántos desarrolladores humanos hay y qué experiencia tienen con el stack?
- ¿Qué herramientas de IA usarán? (Claude Code, Cursor, Copilot, otras)
- ¿Qué nivel de autonomía tendrá la IA? (sugiere código / implementa y abre PR / implementa y despliega en entorno de pruebas)
- ¿Quién revisa y aprueba el código generado por IA?

### Stack tecnológico
- Frontend: ¿web, móvil, escritorio? ¿framework?
- Backend: ¿lenguaje y framework?
- Base de datos: ¿relacional, documental? ¿cuál?
- Infraestructura: ¿nube (cuál), servidor propio, serverless? ¿contenedores?
- CI/CD y repositorio: ¿GitHub, GitLab, Azure DevOps?
- ¿Hay estándares obligatorios de la empresa (lenguajes, librerías aprobadas, seguridad)?
- ¿Existe código previo o se parte de cero?

### Restricciones y riesgos
- ¿Integraciones externas? (pagos, facturación electrónica, APIs gubernamentales, ERP, correo, SMS)
- ¿Normativa? (protección de datos personales, facturación, salud, financiera)
- ¿Presupuesto mensual para infraestructura y herramientas de IA?
- ¿Idiomas, monedas, zonas horarias que deba soportar?
- ¿Requisitos de rendimiento, disponibilidad o número de usuarios esperado?

## Fase 2 — Product Owner (descubrimiento)

### Personas
- ¿Quiénes usarán el sistema? ¿Qué tipos de usuario hay?
- Para cada tipo: ¿qué necesita lograr?, ¿qué le frustra hoy?, ¿qué tan cómodo está con la tecnología?, ¿desde qué dispositivo trabaja?
- ¿Hay usuarios administradores o de soporte?

### Épicas / capacidades
- ¿Qué debe poder hacer cada persona en el sistema?
- Si solo pudieras lanzar 3 funcionalidades, ¿cuáles serían?
- ¿Qué funcionalidades pueden esperar a una segunda versión?

### Profundización por épica
- Descríbeme el flujo paso a paso: ¿qué hace el usuario primero? ¿y después?
- ¿Qué datos se ingresan? ¿Cuáles son obligatorios? ¿Qué formato/validación tienen?
- ¿Qué reglas de negocio aplican? (cálculos, estados, aprobaciones, límites)
- ¿Quién puede hacer esto y quién no? (permisos)
- ¿Qué pasa si… falla la conexión / el dato es inválido / se hace dos veces / no hay resultados?
- ¿Qué notificaciones o reportes genera?
- ¿Cómo se ve el resultado exitoso? (mensaje, pantalla, documento)
- ¿Hay un ejemplo real (documento, planilla, pantalla de otro sistema) que pueda ver?

### Concreción de requisitos vagos
- "Rápido" → ¿en cuántos segundos? ¿con cuántos registros?
- "Fácil de usar" → ¿en cuántos pasos/clics? ¿sin capacitación?
- "Seguro" → ¿qué datos son sensibles? ¿quién no debe verlos?
- "Reportes" → ¿qué columnas, filtros, formato (PDF/Excel), frecuencia?
- "Integración con X" → ¿qué datos van y vienen? ¿en qué momento? ¿qué pasa si X no responde?

### Priorización
- De estas historias, ¿cuáles son imprescindibles para el primer release (Must)?
- Si tuvieras 100 puntos para repartir entre estas épicas, ¿cómo los repartirías?
- ¿Hay alguna historia que dependa de otra o de un tercero?
