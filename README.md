# Sistema de Facturación Electrónica - BMAD-METHOD

## 📋 Descripción del Proyecto

Este proyecto implementa un sistema de facturación electrónica moderno utilizando el framework **BMAD-METHOD** para desarrollo ágil impulsado por IA. El proyecto se basa en el refactoring del sistema existente `fe-mlabs` para mejorar la calidad del código manteniendo la compatibilidad con las librerías MITyC.

## 🎯 Objetivos

- **Crear facturas electrónicas** con estructura XML válida según normativa SRI
- **Firmar documentos digitalmente** usando certificados XAdES-BES
- **Enviar al SRI** de manera automática y confiable
- **Refactorizar el código existente** mejorando calidad y mantenibilidad

## 🏗️ Arquitectura

El proyecto utiliza una arquitectura de refactoring con 4 capas principales:

```
┌─────────────────────────────────────────────────────────────────┐
│                    CAPA DE PRESENTACIÓN                         │
├─────────────────────────────────────────────────────────────────┤
│  Main.kt (Refactorizado)                                        │
│  ├── Application.kt (Configuración)                            │
│  ├── CliInterface.kt (Interfaz línea comandos)                 │
│  └── ConfigLoader.kt (Carga configuración)                     │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                    CAPA DE SERVICIOS                            │
├─────────────────────────────────────────────────────────────────┤
│  FacturaService.kt                                             │
│  ├── FacturaGenerator.kt (Generación XML)                      │
│  ├── FacturaValidator.kt (Validación datos)                     │
│  └── FacturaSerializer.kt (Serialización)                      │
│                                                                 │
│  FirmaService.kt                                               │
│  ├── CertificateManager.kt (Gestión certificados)               │
│  ├── XAdESSigner.kt (Firma XAdES-BES)                          │
│  └── SignatureValidator.kt (Validación firma)                  │
│                                                                 │
│  SriService.kt                                                  │
│  ├── SriClient.kt (Cliente web services)                       │
│  ├── ResponseHandler.kt (Manejo respuestas)                    │
│  └── RetryManager.kt (Reintentos)                               │
└─────────────────────────────────────────────────────────────────┘
```

## 🛠️ Stack Tecnológico

### Tecnologías Actuales (Mantenidas)
- **Java:** JDK 8 (compatibilidad MITyC)
- **Kotlin:** 1.3.11
- **Build Tool:** Gradle
- **Firma Digital:** MITyC Libraries (XAdES-BES)
- **SRI Integration:** Web Services SOAP
- **JSON Parsing:** Klaxon 5.0.1

### Mejoras de Refactoring
- **Arquitectura:** Mejorar estructura de clases y paquetes
- **Código:** Refactoring de métodos largos y complejos
- **Testing:** Implementar tests unitarios e integración
- **Logging:** Implementar logging estructurado
- **Manejo de Errores:** Mejorar gestión de excepciones

## 📁 Estructura del Proyecto

```
fe-bmad/
├── .bmad-core/                    # BMAD-METHOD Core System
├── .bmad-infrastructure-devops/   # DevOps Pack
├── web-bundles/                   # AI Agent Bundles
├── proyecto-facturacion/          # Proyecto Principal
│   ├── docs/                      # Documentación
│   │   ├── PRD-Sistema-Facturacion-Electronica.md
│   │   └── Architecture-Sistema-Facturacion-Electronica.md
│   ├── src/                       # Código fuente (futuro)
│   └── tests/                     # Tests (futuro)
└── README.md
```

## 📚 Documentación

### **Proyecto**
- **[PRD (Product Requirements Document)](proyecto-facturacion/docs/PRD-Sistema-Facturacion-Electronica.md)** - Requisitos funcionales y no funcionales
- **[Architecture Document](proyecto-facturacion/docs/Architecture-Sistema-Facturacion-Electronica.md)** - Arquitectura técnica detallada
- **[User Stories](proyecto-facturacion/docs/User-Stories-Facturacion-Electronica.md)** - Historias de usuario y planificación de sprints

### **BMAD-METHOD Framework**
- **[BMAD-METHOD Quick Guide](BMAD-METHOD-Quick-Guide.md)** - Guía rápida de uso del framework
- **[Documentación Oficial](https://github.com/bmad-code-org/BMAD-METHOD)** - Repositorio oficial de BMAD-METHOD

## 🚀 Quick Start con BMAD-METHOD

### **1. Activar un Agente**
```bash
# En el chat, escribe el comando del agente:
*dev        # Para desarrollo
*analyst    # Para análisis de requisitos
*architect  # Para diseño de arquitectura
*qa         # Para testing
*sm         # Para gestión de historias
```

### **2. Describir tu Necesidad**
```bash
*dev
Necesito refactorizar la clase FacturaService.kt dividiendo la lógica en componentes más pequeños
```

### **3. Seguir las Recomendaciones**
- El agente te proporcionará código, documentación o guías específicas
- Puedes iterar con el mismo agente o cambiar a otro según necesites
- Consulta la [BMAD-METHOD Quick Guide](BMAD-METHOD-Quick-Guide.md) para más detalles

## 🚀 Funcionalidades Core (MVP)

- ✅ Crear facturas XML válidas según normativa SRI
- ✅ Firmar documentos con certificados XAdES-BES
- ✅ Enviar documentos firmados al SRI exitosamente
- ✅ Manejar respuestas del SRI (autorizado/rechazado)
- ✅ Validación básica de datos tributarios

## 🔄 Plan de Desarrollo

### Fase 1: Análisis y Evaluación (1 semana)
- ✅ Análisis del proyecto existente fe-mlabs
- ✅ Identificación de áreas de mejora
- ✅ Evaluación de dependencias compatibles
- ✅ Definición de estrategia de refactoring

### Fase 2: Refactoring Base (2 semanas)
- 🔄 Refactoring de estructura de clases y paquetes
- 🔄 Mejora de métodos largos y complejos
- 🔄 Actualización de dependencias compatibles
- 🔄 Implementación de logging estructurado

### Fase 3: Desarrollo MVP (3 semanas)
- 🔄 Refactoring de creación de facturas
- 🔄 Mejora de firma digital
- 🔄 Optimización de envío al SRI
- 🔄 Implementación de tests unitarios

### Fase 4: Testing y Documentación (1 semana)
- 🔄 Testing integral del flujo completo
- 🔄 Documentación técnica del código
- 🔄 Preparación para producción
- 🔄 Validación con SRI

## 🤖 BMAD-METHOD Framework

Este proyecto utiliza el framework **BMAD-METHOD** para desarrollo ágil impulsado por IA:

- **Agentes Especializados:** Analyst, Architect, Dev, QA, SM
- **Metodología Ágil:** Planning y Development phases
- **Documentación Automatizada:** PRD y Architecture documents
- **Desarrollo Colaborativo:** Equipos de IA especializados

## 📊 Métricas de Éxito

### Métricas de Calidad
- **Complejidad ciclomática:** < 10 por método
- **Líneas de código:** < 200 por clase
- **Cobertura de tests:** > 80%
- **Tiempo de build:** < 2 minutos

### Métricas Funcionales
- **Tiempo de generación:** < 5 segundos
- **Tasa de éxito firma:** > 95%
- **Tiempo de envío SRI:** < 30 segundos
- **Disponibilidad:** > 99%

## 🔧 Instalación y Configuración

### Prerrequisitos
- Java JDK 8
- Gradle
- Certificado digital .p12 del Registro Civil
- Acceso a servicios web del SRI

### Setup Rápido
```bash
# Clonar el repositorio
git clone https://github.com/cristian-lara/facturacion-electronica-bmad.git

# Navegar al directorio
cd facturacion-electronica-bmad

# ¡Listo! BMAD-METHOD ya está incluido
# No necesitas ejecutar npx bmad-method install
```

### Configuración del Proyecto
```bash
# Configurar certificados y parámetros
# (Documentación detallada en Architecture Document)

# Estructura de directorios
mkdir -p xml firmados certificados logs

# Configurar certificado .p12
# Copiar tu certificado a la carpeta certificados/
```

## 📝 Contribución

Este proyecto sigue la metodología BMAD-METHOD para desarrollo ágil impulsado por IA. Para contribuir:

1. Revisar la documentación (PRD y Architecture)
2. Seguir las mejores prácticas de refactoring
3. Implementar tests unitarios
4. Mantener compatibilidad con MITyC

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Ver [LICENSE](LICENSE) para más detalles.

## 👥 Equipo

Desarrollado utilizando **BMAD-METHOD** framework con agentes de IA especializados:
- **Analyst:** Análisis de requisitos y PRD
- **Architect:** Diseño de arquitectura técnica
- **Dev:** Desarrollo e implementación
- **QA:** Testing y calidad
- **SM:** Gestión de proyecto ágil

## 🔗 Enlaces Útiles

- [BMAD-METHOD Framework](https://github.com/bmad-code-org/BMAD-METHOD)
- [SRI Ecuador - Facturación Electrónica](https://www.sri.gob.ec/)
- [MITyC Libraries](https://www.mityc.es/)

---

*Proyecto desarrollado con ❤️ usando BMAD-METHOD para desarrollo ágil impulsado por IA*
