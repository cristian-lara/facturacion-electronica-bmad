# BMAD-METHOD Framework - Guía Rápida

## 🚀 ¿Qué es BMAD-METHOD?

BMAD-METHOD es un framework de desarrollo ágil impulsado por IA que utiliza **agentes especializados** para diferentes roles del desarrollo de software. Cada agente tiene conocimientos específicos y sigue metodologías ágiles probadas.

## 🤖 Agentes Disponibles

### **Analyst (Analista)**
- **Propósito:** Análisis de requisitos, investigación de mercado, definición de funcionalidades
- **Comando:** `*analyst`
- **Cuándo usar:** Al inicio del proyecto, para entender necesidades del usuario

### **Architect (Arquitecto)**
- **Propósito:** Diseño de arquitectura, selección de tecnologías, patrones de diseño
- **Comando:** `*architect`
- **Cuándo usar:** Para diseñar la estructura técnica del sistema

### **Dev (Desarrollador)**
- **Propósito:** Implementación de código, debugging, optimización
- **Comando:** `*dev`
- **Cuándo usar:** Para escribir código, refactorizar, implementar funcionalidades

### **QA (Quality Assurance)**
- **Propósito:** Testing, validación, control de calidad
- **Comando:** `*qa`
- **Cuándo usar:** Para crear tests, validar código, asegurar calidad

### **SM (Scrum Master)**
- **Propósito:** Gestión de historias, sprints, coordinación del equipo
- **Comando:** `*sm`
- **Cuándo usar:** Para crear user stories, planificar sprints, gestionar el backlog

### **PM (Project Manager)**
- **Propósito:** Gestión de proyecto, recursos, timeline
- **Comando:** `*pm`
- **Cuándo usar:** Para planificación de proyecto, gestión de recursos

### **PO (Product Owner)**
- **Propósito:** Gestión de producto, priorización, visión del producto
- **Comando:** `*po`
- **Cuándo usar:** Para definir visión del producto, priorizar funcionalidades

### **UX Expert**
- **Propósito:** Experiencia de usuario, diseño de interfaces, usabilidad
- **Comando:** `*ux-expert`
- **Cuándo usar:** Para diseñar interfaces, mejorar experiencia de usuario

## 🔄 Flujo de Trabajo BMAD-METHOD

### **Fase 1: Planning (Planificación)**
```
Analyst → Architect → PM/PO
```
1. **Analyst** analiza requisitos y necesidades
2. **Architect** diseña la solución técnica
3. **PM/PO** prioriza y planifica funcionalidades

### **Fase 2: Development (Desarrollo)**
```
SM → Dev → QA
```
1. **SM** crea historias de usuario detalladas
2. **Dev** implementa el código
3. **QA** valida y testea la implementación

## 🛠️ Comandos Detallados por Agente

### **💻 DEV (Desarrollador) - James**
**Propósito:** Implementación de código, debugging, refactoring

#### **Comandos Principales:**
```bash
*dev
develop-story    # Implementar una story completa paso a paso
explain          # Explicar qué y por qué hizo algo (para aprendizaje)
review-qa        # Aplicar fixes sugeridos por QA
run-tests        # Ejecutar linting y tests
help             # Mostrar lista de comandos
exit             # Salir del modo Dev
```

#### **Cuándo usar DEV:**
- ✅ Implementar código según user stories
- ✅ Refactorizar código existente
- ✅ Debugging y optimización
- ✅ Crear tests unitarios
- ✅ Aplicar fixes de QA

#### **Ejemplo de uso:**
```bash
*dev
develop-story
# Luego especifica: "Implementar Story 1.1: Refactorizar clase Factura.kt"
```

---

### **🧪 QA (Quality Assurance) - Quinn**
**Propósito:** Testing, validación, control de calidad

#### **Comandos Principales:**
```bash
*qa
review {story}      # Revisión completa de una story
gate {story}        # Decisión de quality gate (PASS/CONCERNS/FAIL/WAIVED)
nfr-assess {story}   # Validar requisitos no funcionales
risk-profile {story} # Generar matriz de evaluación de riesgos
test-design {story}  # Crear escenarios de test comprehensivos
trace {story}        # Mapear requisitos a tests (Given-When-Then)
help                # Mostrar lista de comandos
exit                # Salir del modo QA
```

#### **Cuándo usar QA:**
- ✅ Crear estrategias de testing
- ✅ Validar calidad del código
- ✅ Evaluar riesgos del proyecto
- ✅ Diseñar casos de prueba
- ✅ Revisar cumplimiento de requisitos

#### **Ejemplo de uso:**
```bash
*qa
review Story 1.1
# Revisará la story y dará recomendaciones de calidad
```

---

### **🏗️ ARCHITECT (Arquitecto) - Winston**
**Propósito:** Diseño de arquitectura, selección de tecnologías

#### **Comandos Principales:**
```bash
*architect
create-backend-architecture     # Crear arquitectura de backend
create-brownfield-architecture  # Crear arquitectura para proyecto existente
create-front-end-architecture   # Crear arquitectura de frontend
create-full-stack-architecture  # Crear arquitectura full-stack
document-project               # Documentar proyecto completo
execute-checklist              # Ejecutar checklist de arquitectura
research {topic}               # Investigar tema específico
shard-prd                      # Dividir PRD en componentes
help                           # Mostrar lista de comandos
exit                           # Salir del modo Architect
```

#### **Cuándo usar ARCHITECT:**
- ✅ Diseñar arquitectura del sistema
- ✅ Seleccionar tecnologías
- ✅ Definir patrones de diseño
- ✅ Planificar infraestructura
- ✅ Revisar arquitectura existente

#### **Ejemplo de uso:**
```bash
*architect
create-brownfield-architecture
# Creará arquitectura para refactoring del proyecto existente
```

---

### **🏃 SM (Scrum Master) - Bob**
**Propósito:** Gestión de historias, sprints, proceso ágil

#### **Comandos Principales:**
```bash
*sm
draft              # Crear próxima story detallada
correct-course     # Corregir curso del proyecto
story-checklist    # Ejecutar checklist de story
help               # Mostrar lista de comandos
exit               # Salir del modo SM
```

#### **Cuándo usar SM:**
- ✅ Crear user stories detalladas
- ✅ Planificar sprints
- ✅ Gestionar backlog
- ✅ Facilitar retrospectivas
- ✅ Coordinar proceso ágil

#### **Ejemplo de uso:**
```bash
*sm
draft
# Creará la próxima story basada en PRD y Architecture
```

---

### **📊 ANALYST (Analista) - Mary**
**Propósito:** Análisis de requisitos, investigación de mercado

#### **Comandos Principales:**
```bash
*analyst
brainstorm {topic}                    # Facilitar sesión de brainstorming
create-competitor-analysis            # Crear análisis de competencia
create-market-research                # Crear investigación de mercado
create-project-brief                  # Crear brief del proyecto
document-existing-project            # Documentar proyecto existente
research {topic}                      # Investigar tema específico
help                                  # Mostrar lista de comandos
exit                                  # Salir del modo Analyst
```

#### **Cuándo usar ANALYST:**
- ✅ Analizar requisitos del negocio
- ✅ Investigar mercado y competencia
- ✅ Crear briefs de proyecto
- ✅ Facilitar brainstorming
- ✅ Documentar proyectos existentes

#### **Ejemplo de uso:**
```bash
*analyst
brainstorm facturacion-electronica
# Facilitará sesión de brainstorming sobre facturación electrónica
```

---

### **Comandos de Utilidad Generales**
```bash
*help                    # Mostrar ayuda completa
*checklist               # Ejecutar checklist de calidad
*research {topic}        # Investigar un tema específico
*doc-out                 # Exportar documento completo
*exit                    # Salir del modo agente
```

## 🎯 Recomendaciones para Empezar

### **Opción 1: Comenzar con Desarrollo (Recomendado)**
```bash
*dev
develop-story
# Especifica: "Implementar Story 1.1: Refactorizar clase Factura.kt"
```

### **Opción 2: Crear Tests Primero**
```bash
*qa
test-design Story 1.1
# Creará escenarios de test para la refactorización
```

### **Opción 3: Revisar Arquitectura**
```bash
*architect
create-brownfield-architecture
# Creará arquitectura específica para refactoring
```

### **Opción 4: Crear Más Stories**
```bash
*sm
draft
# Creará la próxima story detallada
```

## 🔄 Flujo Recomendado para Tu Proyecto

1. **SM** → Crear stories detalladas
2. **DEV** → Implementar código
3. **QA** → Crear tests y validar
4. **ARCHITECT** → Revisar arquitectura si es necesario

## 💡 Tips Importantes

- **Sé específico:** Describe exactamente lo que necesitas
- **Usa el contexto:** Los agentes leen PRD y Architecture automáticamente
- **Itera:** Puedes volver a cualquier agente para refinar
- **Sigue el flujo:** Planning → Development → QA

## 📚 Templates Disponibles

BMAD-METHOD incluye templates para crear documentos estructurados:

- **PRD** (Product Requirements Document)
- **Architecture** (Documentos de arquitectura)
- **User Stories** (Historias de usuario)
- **Testing Plans** (Planes de testing)
- **Project Briefs** (Resúmenes de proyecto)

## 🎯 Ejemplos de Uso

### **Ejemplo 1: Análisis de Requisitos**
```bash
*analyst
Necesito analizar los requisitos para un módulo de facturación electrónica que debe integrarse con el SRI de Ecuador
```

### **Ejemplo 2: Diseño de Arquitectura**
```bash
*architect
Quiero diseñar la arquitectura de un sistema de facturación que use Java 8, Kotlin y librerías MITyC para firma digital
```

### **Ejemplo 3: Desarrollo de Código**
```bash
*dev
Necesito refactorizar una clase Factura.kt de 800 líneas en componentes más pequeños siguiendo principios SOLID
```

### **Ejemplo 4: Creación de Tests**
```bash
*qa
Quiero crear tests unitarios para un servicio de firma digital que use certificados XAdES-BES
```

### **Ejemplo 5: Gestión de Historias**
```bash
*sm
Necesito crear user stories detalladas para el refactoring de un sistema de facturación electrónica
```

## 📁 Estructura de Archivos BMAD-METHOD

```
fe-bmad/
├── .bmad-core/                    # Sistema core de BMAD-METHOD
│   ├── agents/                    # Definiciones de agentes
│   ├── templates/                 # Templates para documentos
│   ├── tasks/                     # Tareas específicas
│   ├── checklists/                # Listas de verificación
│   └── workflows/                  # Flujos de trabajo
├── .bmad-infrastructure-devops/   # Pack de DevOps
├── web-bundles/                   # Bundles web para agentes
│   ├── agents/                    # Agentes para web/chat
│   ├── teams/                     # Equipos predefinidos
│   └── expansion-packs/           # Packs de expansión
└── .cursor/                       # Reglas para Cursor IDE
    └── rules/bmad/                # Reglas específicas de BMAD
```

## 🔧 Configuración para Cursor IDE

BMAD-METHOD incluye reglas específicas para Cursor IDE en `.cursor/rules/bmad/`:

- `analyst.mdc` - Reglas para agente Analyst
- `architect.mdc` - Reglas para agente Architect
- `dev.mdc` - Reglas para agente Dev
- `qa.mdc` - Reglas para agente QA
- `sm.mdc` - Reglas para agente SM
- Y más...

## 📖 Documentación Oficial

### **Repositorio Principal**
- **GitHub:** [https://github.com/bmad-code-org/BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD)
- **Estrellas:** 13.6k+ ⭐
- **Forks:** 2.1k+ 🍴

### **Documentación Completa**
- **User Guide:** [https://github.com/bmad-code-org/BMAD-METHOD/blob/main/docs/user-guide.md](https://github.com/bmad-code-org/BMAD-METHOD/blob/main/docs/user-guide.md)
- **Core Architecture:** [https://github.com/bmad-code-org/BMAD-METHOD/blob/main/docs/core-architecture.md](https://github.com/bmad-code-org/BMAD-METHOD/blob/main/docs/core-architecture.md)
- **Expansion Packs:** [https://github.com/bmad-code-org/BMAD-METHOD/blob/main/docs/expansion-packs.md](https://github.com/bmad-code-org/BMAD-METHOD/blob/main/docs/expansion-packs.md)

### **Recursos Adicionales**
- **YouTube Channel:** [BMadCode](https://www.youtube.com/@BMadCode)
- **Discord Community:** [https://discord.gg/bmad](https://discord.gg/bmad)
- **Buy Me a Coffee:** [https://buymeacoffee.com/bmad](https://buymeacoffee.com/bmad)

## 🎮 Expansion Packs Disponibles

BMAD-METHOD incluye expansion packs para diferentes dominios:

### **Game Development**
- **Phaser 2D Games** - Desarrollo de juegos 2D con Phaser
- **Unity 2D Games** - Desarrollo de juegos 2D con Unity
- **Godot Games** - Desarrollo de juegos con Godot

### **Creative Writing**
- **Novel Writing** - Escritura de novelas
- **Character Development** - Desarrollo de personajes
- **World Building** - Construcción de mundos

### **Infrastructure & DevOps**
- **Platform Engineering** - Ingeniería de plataformas
- **Infrastructure as Code** - Infraestructura como código
- **DevOps Automation** - Automatización DevOps

## 🚀 Quick Start

### **1. Clonar el Proyecto**
```bash
git clone https://github.com/cristian-lara/facturacion-electronica-bmad.git
cd facturacion-electronica-bmad
```

### **2. Activar un Agente**
```bash
# En el chat, escribe:
*dev
# Luego describe lo que necesitas
```

### **3. Seguir el Flujo**
```bash
# Planning Phase
*analyst    # Analizar requisitos
*architect  # Diseñar arquitectura
*pm         # Planificar proyecto

# Development Phase  
*sm         # Crear historias
*dev        # Implementar código
*qa         # Crear tests
```

## 💡 Tips y Mejores Prácticas

### **1. Usar Agentes Específicos**
- No mezcles responsabilidades de agentes
- Cada agente tiene su expertise específico
- Sigue el flujo Planning → Development

### **2. Ser Específico en las Solicitudes**
```bash
# ❌ Malo
*dev
Ayúdame con el código

# ✅ Bueno  
*dev
Necesito refactorizar la clase FacturaService.kt dividiendo la lógica de generación XML en un componente separado siguiendo el patrón Builder
```

### **3. Usar Templates**
- Los templates te ayudan a crear documentos estructurados
- Siguen mejores prácticas de la industria
- Son consistentes con metodologías ágiles

### **4. Iterar y Refinar**
- BMAD-METHOD es iterativo
- Puedes volver a cualquier agente para refinar
- Los agentes aprenden del contexto del proyecto

## 🆘 Troubleshooting

### **Problema: El agente no responde correctamente**
**Solución:** Asegúrate de usar el comando correcto (`*agente`) y ser específico en tu solicitud

### **Problema: No encuentro el template que necesito**
**Solución:** Revisa `.bmad-core/templates/` o usa `*help` para ver opciones disponibles

### **Problema: El agente no entiende el contexto**
**Solución:** Proporciona más contexto sobre tu proyecto y objetivos

## 📞 Soporte y Comunidad

- **Discord:** [https://discord.gg/bmad](https://discord.gg/bmad) - Comunidad activa de desarrolladores
- **GitHub Issues:** [https://github.com/bmad-code-org/BMAD-METHOD/issues](https://github.com/bmad-code-org/BMAD-METHOD/issues)
- **YouTube:** [BMadCode](https://www.youtube.com/@BMadCode) - Tutoriales y demos

## 📄 Licencia

BMAD-METHOD está bajo licencia MIT. Ver [LICENSE](https://github.com/bmad-code-org/BMAD-METHOD/blob/main/LICENSE) para más detalles.

---

*Esta guía rápida te ayudará a comenzar con BMAD-METHOD. Para información más detallada, consulta la documentación oficial en los enlaces proporcionados.*

**¡Happy Coding con BMAD-METHOD! 🚀**
