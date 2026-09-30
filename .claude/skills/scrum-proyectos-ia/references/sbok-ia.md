# Resumen del marco SBOK™ (SCRUMstudy) y su adaptación a desarrollo con IA

Resumen propio de los conceptos del *SBOK™ Guide* para usar como referencia. No reemplaza a la guía oficial.

## Contenido
1. Principios
2. Aspectos
3. Roles
4. Fases y procesos
5. Técnicas de priorización y estimación
6. Artefactos principales
7. Adaptaciones para equipos con IA

---

## 1. Los 6 principios de Scrum (SBOK)

| Principio | Idea central | En proyectos con IA |
|---|---|---|
| Control empírico del proceso | Transparencia, inspección y adaptación | Revisar cada PR generado por IA; medir retrabajo |
| Autoorganización | El equipo decide cómo hacer el trabajo | Los humanos deciden qué delegar a la IA y con qué autonomía |
| Colaboración | Conciencia, articulación y apropiación compartidas | El contexto compartido vive en `CLAUDE.md`/`AGENTS.md` y en el backlog |
| Priorización basada en valor | Entregar primero lo de mayor valor de negocio | Igual; la IA abarata construir, no decidir qué construir |
| Time-boxing | Todo tiene un límite de tiempo | Sprints más cortos (1 semana) porque la IA acelera el ciclo |
| Desarrollo iterativo | Entregas incrementales que incorporan feedback | Iteraciones pequeñas y frecuentes; cada historia = un PR revisable |

## 2. Los 5 aspectos

- **Organización**: roles centrales y no centrales, responsabilidades.
- **Justificación de negocio**: el proyecto debe entregar valor; se revisa durante todo el proyecto.
- **Calidad**: cumplir criterios de aceptación y de terminado; en IA, tests automáticos obligatorios.
- **Cambio**: los cambios se gestionan por el backlog priorizado, no a mitad de sprint.
- **Riesgo**: identificar, evaluar, priorizar y mitigar riesgos de forma continua.

## 3. Roles

**Roles centrales** (comprometidos con el proyecto):
- **Product Owner**: maximiza el valor del negocio, es dueño del backlog priorizado, redacta y acepta historias. Representa la voz del cliente.
- **Scrum Master**: facilita, elimina impedimentos, asegura que se sigan los procesos Scrum. Es un líder servidor.
- **Equipo Scrum**: desarrolla los entregables. En proyectos con IA = desarrolladores humanos + agentes de IA; los humanos son responsables finales del código.

**Roles no centrales**: stakeholders (clientes, usuarios, patrocinador), Scrum Guidance Body (define estándares y buenas prácticas de la organización), proveedores. En proyectos grandes: Chief Product Owner y Chief Scrum Master (Scrum of Scrums).

## 4. Las 5 fases y sus 19 procesos

**Inicio**
1. Crear la visión del proyecto
2. Identificar al Scrum Master y a los stakeholders
3. Formar el equipo Scrum
4. Desarrollar épicas
5. Crear el backlog priorizado del producto
6. Realizar la planificación del lanzamiento (release)

**Planificación y estimación**
7. Crear historias de usuario
8. Estimar historias de usuario
9. Comprometer historias de usuario
10. Identificar tareas
11. Estimar tareas
12. Actualizar el sprint backlog

**Implementación**
13. Crear entregables
14. Realizar el daily standup
15. Refinar el backlog priorizado del producto

**Revisión y retrospectiva**
16. Demostrar y validar el sprint
17. Retrospectiva del sprint

**Lanzamiento**
18. Enviar entregables
19. Retrospectiva del proyecto

Duración de sprint en SBOK: de 1 a 6 semanas (4 semanas es habitual en equipos tradicionales; con IA se recomienda 1–2).

## 5. Técnicas

**Priorización**
- **MoSCoW**: Must / Should / Could / Won't (this time).
- **Método de 100 puntos**: cada stakeholder reparte 100 puntos entre las historias.
- **Comparación por pares**: cada historia se compara con cada otra.
- **Modelo Kano**: básicos, de desempeño y de entusiasmo.

**Estimación**
- **Planning Poker** con Fibonacci (1, 2, 3, 5, 8, 13, 21).
- **Puño de cinco** (fist of five) para consenso rápido.
- **Wideband Delphi**: estimaciones anónimas en rondas.
- **Estimación por afinidad / relativa**: agrupar por tamaño comparado con una historia de referencia.

**Calidad de historias**: criterios INVEST (Independiente, Negociable, Valiosa, Estimable, Pequeña, Testeable).

## 6. Artefactos principales

- Declaración de visión del proyecto
- Épicas y personas
- Backlog priorizado del producto (con historias y criterios de aceptación)
- Criterios de terminado (Definition of Done) — generales para todo el proyecto
- Criterios de aceptación — específicos de cada historia
- Calendario de planificación del lanzamiento
- Sprint backlog y lista de tareas
- Burndown / burnup chart
- Registro de riesgos
- Registro de impedimentos

## 7. Adaptaciones para equipos con IA

**Historias**
- Tamaño: implementable y testeable por un agente en una sesión (≈ ≤ 8 puntos).
- Autocontenidas: incluyen el contexto necesario (módulos afectados, modelo de datos, contratos de API).
- "Notas para la IA": archivos a tocar, patrones a seguir, datos de prueba, lo que NO debe cambiar.

**Criterios de aceptación**
- Formato Dado/Cuando/Entonces, cada uno traducible a un test automático.
- Resultados observables (respuesta HTTP, texto en pantalla, registro en BD), nunca "funciona bien".
- Incluir al menos un caso de error o límite por historia.

**Definición de Terminado**
- Tests automáticos que cubren los criterios de aceptación, en verde en CI.
- Revisión humana del PR (la IA no aprueba su propio código).
- Sin secretos en el código; análisis de dependencias/seguridad.
- Documentación y `CLAUDE.md` actualizados si cambió la arquitectura o convenciones.

**Velocidad**
- La IA reduce el tiempo de codificación pero no el de decisión, revisión e integración. Estimar velocidad inicial de forma conservadora y recalibrar tras el Sprint 1.
- Medir también el *retrabajo* (historias rechazadas en la revisión) como indicador de calidad de los criterios.

**Riesgos típicos del desarrollo con IA**
- Requisitos ambiguos → la IA implementa una interpretación distinta.
- Código plausible pero incorrecto (alucinaciones, APIs inexistentes).
- Deuda técnica por generar mucho código sin refactor.
- Fuga de secretos o datos sensibles en prompts o en el repo.
- Dependencias añadidas sin revisión (licencias, vulnerabilidades).
- Dependencia del proveedor de IA (costos, límites, disponibilidad).
- Cuello de botella en la revisión humana.

**Ceremonias**
- Daily: además de qué hice/qué haré/impedimentos, qué historias están en manos de la IA y cuáles esperan revisión.
- Revisión del sprint: validar cada historia contra sus criterios de aceptación, idealmente con los tests como evidencia.
- Retrospectiva: incluir cómo funcionó la colaboración con la IA (prompts útiles, contexto faltante, patrones a documentar en `CLAUDE.md`).
