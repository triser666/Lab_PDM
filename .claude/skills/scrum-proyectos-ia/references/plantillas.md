# Plantillas de la bóveda de Obsidian ("cerebro" del proyecto)

El entregable final es una carpeta que se abre en Obsidian con **Abrir carpeta como bóveda**. Cada concepto es una nota; las notas se conectan con `[[enlaces]]` y **propiedades** (frontmatter YAML). Así el gráfico de Obsidian muestra el proyecto como una red: épica → historias → sprint → persona → riesgos.

Marca con `(supuesto)` lo que el usuario no haya confirmado.

## Contenido
1. Estructura de carpetas
2. Reglas de nombres y enlaces
3. Plantillas de cada nota
4. Qué se copia de `assets/boveda/`
5. CLAUDE.md del repositorio
6. Export CSV (opcional)

---

## 1. Estructura de carpetas

```
<Nombre del proyecto>/
├── 00 Inicio.md                      ← nota central (MOC): enlaza todo y muestra tableros
├── 01 Visión/
│   ├── Visión del proyecto.md
│   ├── Roles y stakeholders.md
│   └── Stack tecnológico.md
├── 02 Personas/
│   └── <Nombre> - <rol>.md           (una por persona)
├── 03 Épicas/
│   └── EP-<n> <nombre>.md            (una por épica)
├── 04 Historias/
│   └── HU-<n>.<m> <título>.md        (una por historia)
├── 05 Sprints/
│   ├── Plan de lanzamiento.md
│   ├── Sprint 01.md
│   └── Tablero Sprint 01.md          (formato del plugin Kanban)
├── 06 Calidad/
│   └── Definición de Terminado.md
├── 07 Riesgos/
│   └── R<n> <riesgo>.md              (una por riesgo)
├── 08 Decisiones/
│   └── ADR-<n> <decisión>.md         (decisiones de arquitectura: stack, BD, hosting…)
├── 09 Ceremonias/                    (vacía; aquí se crean dailies, revisiones y retros)
├── Glosario Scrum/                   ← copiado de assets/boveda/Glosario Scrum
└── Plantillas/                       ← copiado de assets/boveda/Plantillas
```

## 2. Reglas de nombres y enlaces

- Los nombres de archivo **no** pueden llevar `: / \ # ^ [ ] | ? * " < >`. Usa `-` en su lugar (p. ej. `HU-1.2 Registrar venta - pago QR.md`).
- En los enlaces se escribe el nombre sin `.md`: `[[EP-1 Gestión de inventario]]`.
- Enlaces dentro de propiedades van **entre comillas**: `epica: "[[EP-1 Gestión de inventario]]"`.
- Enlaza conceptos del glosario la primera vez que aparecen en una nota: `[[Criterios de aceptación]]`, `[[INVEST]]`, `[[MoSCoW]]`.
- Usa siempre los mismos valores en las propiedades (los bloques Dataview dependen de ello):
  - `estado`: `Por hacer` | `En progreso` | `En revisión` | `Terminado`
  - `prioridad`: `Must` | `Should` | `Could` | `Won't`
  - `asignado`: `IA` | `Humano` | `IA + revisión humana`

Los bloques ```` ```dataview ```` requieren el plugin comunitario **Dataview**, y `Tablero Sprint 01.md` requiere el plugin **Kanban**. Sin ellos las notas siguen siendo legibles (los bloques se ven como código).

---

## 3. Plantillas de cada nota

### 00 Inicio.md

````markdown
---
tipo: inicio
proyecto: <Nombre>
creado: <AAAA-MM-DD>
tags: [proyecto]
---
# <Nombre del proyecto>

> <Declaración de visión en una frase>

## Mapa del proyecto
- 🎯 [[Visión del proyecto]] · [[Roles y stakeholders]] · [[Stack tecnológico]]
- 👤 Personas: [[<Persona 1>]], [[<Persona 2>]]
- 🧩 Épicas: [[EP-1 …]], [[EP-2 …]]
- 🗓️ [[Plan de lanzamiento]] · [[Sprint 01]] · [[Tablero Sprint 01]]
- ✅ [[Definición de Terminado]]
- ⚠️ Riesgos: [[R1 …]], [[R2 …]]
- 🏛️ Decisiones: [[ADR-1 …]]
- 📚 [[Scrum]] (glosario)

## Backlog priorizado
<Lista ordenada por el Product Owner; el orden es la prioridad>
1. [[HU-1.1 …]]
2. [[HU-1.2 …]]

## Estado del backlog
```dataview
TABLE WITHOUT ID estado AS "Estado", length(rows) AS "Historias", sum(rows.puntos) AS "Puntos"
FROM "04 Historias"
GROUP BY estado
```

## Historias Must pendientes
```dataview
TABLE id, epica, puntos, sprint
FROM "04 Historias"
WHERE prioridad = "Must" AND estado != "Terminado"
SORT id ASC
```
````

### 01 Visión/Visión del proyecto.md

```markdown
---
tipo: vision
tags: [vision]
---
# Visión del proyecto

## Declaración de visión
Para <usuarios objetivo> que <necesidad>, **<producto>** es un <tipo de producto> que <beneficio clave>. A diferencia de <alternativa actual>, <diferenciador>.

## Objetivos y métricas de éxito
| Objetivo | Métrica | Meta | Plazo |
|---|---|---|---|

## Alcance
- **MVP:** …
- **Fuera de alcance por ahora:** …

## Restricciones
- Plazo: … · Presupuesto: … · Normativa: … · Integraciones: …

Relacionado: [[Roles y stakeholders]] · [[Stack tecnológico]] · [[Plan de lanzamiento]]
```

### 01 Visión/Roles y stakeholders.md

```markdown
---
tipo: roles
tags: [equipo]
---
# Roles y stakeholders

| Rol | Persona / herramienta | Responsabilidad |
|---|---|---|
| [[Product Owner]] | | Prioriza y acepta historias |
| [[Scrum Master]] | | Facilita y elimina impedimentos |
| [[Equipo Scrum]] (humanos) | | Diseñan, revisan y aprueban código |
| [[Equipo Scrum]] (IA) | <Claude Code…> | Implementa historias · autonomía: <nivel> |
| [[Stakeholders]] | | |
```

### 01 Visión/Stack tecnológico.md

```markdown
---
tipo: stack
tags: [tecnico]
---
# Stack tecnológico

| Capa | Tecnología | Motivo | Decisión |
|---|---|---|---|
| Frontend | | | [[ADR-1 …]] |
| Backend | | | |
| Base de datos | | | |
| Infraestructura | | | |
| CI/CD | | | |
| IA | | | |
```

### 02 Personas/<Nombre> - <rol>.md

```markdown
---
tipo: persona
rol: <rol>
tags: [persona]
---
# <Nombre> — <rol>
- **Contexto:** …
- **Objetivo principal:** …
- **Frustración actual:** …
- **Nivel técnico / dispositivo:** …

## Historias de esta persona
```dataview
LIST FROM "04 Historias" WHERE persona = this.file.link
```
```

### 03 Épicas/EP-<n> <nombre>.md

```markdown
---
tipo: epica
id: EP-<n>
prioridad: Must
tags: [epica]
---
# EP-<n> <nombre>

<Descripción y valor de negocio>

**Personas:** [[<Persona>]]

## Flujo principal
1. …

## Reglas de negocio
- …

## Historias
```dataview
TABLE id, prioridad, puntos, estado, sprint
FROM "04 Historias"
WHERE epica = this.file.link
SORT id ASC
```
```

### 04 Historias/HU-<n>.<m> <título>.md

```markdown
---
tipo: historia
id: HU-<n>.<m>
epica: "[[EP-<n> <nombre>]]"
persona: "[[<Nombre> - <rol>]]"
prioridad: Must
puntos: 3
sprint: "[[Sprint 01]]"
estado: Por hacer
asignado: IA + revisión humana
depende_de: []
tags: [historia]
---
# HU-<n>.<m> <título>

**Como** [[<Nombre> - <rol>]], **quiero** <acción>, **para** <beneficio>.

## Criterios de aceptación
- [ ] **Dado** <contexto>, **cuando** <acción>, **entonces** <resultado observable>.
- [ ] **Dado** <contexto de error>, **cuando** <acción>, **entonces** <mensaje/comportamiento>.

## Notas para la IA
- Módulos / archivos afectados: …
- Modelo de datos / contrato de API: …
- Datos de prueba: …
- No modificar: …
- Prompt sugerido: `Implementa HU-<n>.<m> según esta nota. Escribe un test por cada criterio de aceptación y cumple [[Definición de Terminado]].`

## Tareas
- [ ] …

## Registro
<!-- decisiones, dudas, enlace al PR -->
```

Los criterios son casillas (`- [ ]`) para marcarlos durante la [[Revisión del sprint]].

### 05 Sprints/Plan de lanzamiento.md

```markdown
---
tipo: plan-lanzamiento
duracion_sprint: 1 semana
velocidad_estimada: <N>
tags: [planificacion]
---
# Plan de lanzamiento

- Duración del sprint: … · Velocidad inicial: <N> pts (conservadora; se recalibra tras [[Sprint 01]])
- Total MVP: <N> pts → <N> sprints

| Sprint | Fechas | Objetivo | Pts |
|---|---|---|---|
| [[Sprint 01]] | | | |

## Ajuste de alcance
<Qué pasó a Won't y por qué>
```

### 05 Sprints/Sprint 01.md

````markdown
---
tipo: sprint
numero: 1
inicio: <AAAA-MM-DD>
fin: <AAAA-MM-DD>
objetivo: <una frase>
tags: [sprint]
---
# Sprint 01

**Objetivo:** <valor que se entrega>

## Historias comprometidas
```dataview
TABLE id, puntos, estado, asignado
FROM "04 Historias"
WHERE sprint = this.file.link
SORT id ASC
```

## Avance
```dataview
TABLE WITHOUT ID sum(rows.puntos) AS "Puntos", estado AS "Estado"
FROM "04 Historias"
WHERE sprint = this.file.link
GROUP BY estado
```

## Ceremonias
- Planificación: <fecha> · Daily: <hora> · Revisión: <fecha> · Retrospectiva: <fecha>
- Tablero: [[Tablero Sprint 01]]
````

### 05 Sprints/Tablero Sprint 01.md (plugin Kanban)

```markdown
---
kanban-plugin: basic
---

## Por hacer

- [ ] [[HU-1.1 …]]
- [ ] [[HU-1.2 …]]

## En progreso


## En revisión


## Terminado

```

### 06 Calidad/Definición de Terminado.md

```markdown
---
tipo: dod
tags: [calidad]
---
# Definición de Terminado

Una historia está terminada cuando:
- [ ] Cumple todos sus [[Criterios de aceptación]].
- [ ] Cada criterio tiene al menos un test automático y los tests pasan en CI.
- [ ] Un humano revisó y aprobó el PR (la IA no aprueba su propio código).
- [ ] Sin secretos ni datos sensibles en código o commits.
- [ ] Dependencias nuevas revisadas (licencia y vulnerabilidades).
- [ ] Linter/formateador sin errores.
- [ ] Documentación y `CLAUDE.md` actualizados si cambió la arquitectura.
- [ ] Desplegado en pruebas y validado por el [[Product Owner]].

<Criterios específicos del stack>
```

### 07 Riesgos/R<n> <riesgo>.md

```markdown
---
tipo: riesgo
id: R<n>
probabilidad: 3
impacto: 4
exposicion: 12
estado: Abierto
responsable: <rol>
tags: [riesgo]
---
# R<n> <riesgo>

- **Causa:** …
- **Efecto:** …
- **Respuesta:** Mitigar | Evitar | Transferir | Aceptar — …
- **Historias afectadas:** [[HU-…]]
```

Riesgos base de proyectos con IA (ajústalos): requisitos ambiguos, código generado incorrecto o inseguro, cuello de botella en revisión de PRs, fuga de secretos, dependencias no revisadas, dependencia del proveedor de IA.

### 08 Decisiones/ADR-<n> <decisión>.md

```markdown
---
tipo: decision
id: ADR-<n>
estado: Aceptada
fecha: <AAAA-MM-DD>
tags: [decision]
---
# ADR-<n> <decisión>

- **Contexto:** …
- **Decisión:** …
- **Alternativas consideradas:** …
- **Consecuencias:** …
```

Crea un ADR por cada elección importante del stack (lenguaje/framework, base de datos, hosting, herramienta de IA).

---

## 4. Qué se copia de `assets/boveda/`

Copia **tal cual** a la bóveda del proyecto (no hace falta leerlos antes):
- `assets/boveda/Glosario Scrum/`: 26 notas de conceptos del SBOK enlazadas entre sí (la nota central es `Scrum.md`).
- `assets/boveda/Plantillas/`: plantillas `Plantilla - …` para el plugin central *Plantillas* de Obsidian (historia, daily, revisión, retrospectiva, ADR).

Los nombres ya están pensados para no chocar con las notas del proyecto. Por ejemplo, el concepto se llama `Definición de Terminado (DoD)` y la nota del proyecto se llama `Definición de Terminado`. No crees notas del proyecto con el mismo nombre que una del glosario, porque Obsidian enlaza por nombre de archivo.

Indica al usuario que en *Ajustes → Plantillas* configure la carpeta `Plantillas`.

---

## 5. CLAUDE.md del repositorio

Si hay repositorio de código, crea o amplía `CLAUDE.md` (o `AGENTS.md`) en su raíz:

```markdown
# <Nombre del proyecto>

<Visión en 2-3 líneas>

## Cerebro del proyecto (Obsidian)
La bóveda Scrum está en `<ruta>/`. Antes de implementar, lee:
- La historia en `<ruta>/04 Historias/HU-x.y ….md` (criterios de aceptación y "Notas para la IA").
- `<ruta>/06 Calidad/Definición de Terminado.md`.
Al terminar una historia, cambia su propiedad `estado` a `En revisión` y añade el enlace del PR en "Registro".

## Stack
- …

## Comandos
- Instalar: `…` · Tests: `…` · Ejecutar: `…`

## Convenciones
- Una historia por rama/PR: `feature/HU-x.y-descripcion`.
- Si un criterio es ambiguo, pregunta en vez de suponer.
```

## 6. Export CSV (opcional)

```
ID,Epica,Titulo,Historia,CriteriosAceptacion,Prioridad,Puntos,Sprint
```
Separa criterios con ` | ` y encierra los textos entre comillas dobles.
