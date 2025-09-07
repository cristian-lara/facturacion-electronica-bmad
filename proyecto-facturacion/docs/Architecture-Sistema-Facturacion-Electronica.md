# Architecture Document
## Sistema de Facturación Electrónica - Refactoring

**Versión:** 1.0  
**Fecha:** Septiembre 2024  
**Arquitecto:** Equipo de Desarrollo con BMAD-METHOD  
**Estado:** Borrador Inicial  

---

## 1. Resumen Ejecutivo

### 1.1 Propósito del Documento
Este documento define la arquitectura técnica para el refactoring del sistema de facturación electrónica basado en el proyecto existente `fe-mlabs`, utilizando el framework BMAD-METHOD para desarrollo ágil impulsado por IA.

### 1.2 Alcance de la Arquitectura
- **Refactoring del código existente** manteniendo funcionalidad core
- **Mejora de estructura y organización** del código
- **Optimización de dependencias** compatibles con Java 8
- **Implementación de mejores prácticas** de desarrollo

### 1.3 Objetivos Arquitectónicos
- ✅ Mantener compatibilidad con MITyC Libraries
- ✅ Mejorar mantenibilidad del código
- ✅ Facilitar testing y debugging
- ✅ Reducir complejidad ciclomática
- ✅ Implementar logging estructurado

---

## 2. Contexto del Sistema

### 2.1 Sistema Actual (fe-mlabs)
```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Main.kt       │───▶│   Factura.kt    │───▶│   GenerarDocs   │
│   (Entry Point) │    │   (800+ lines)  │    │   (Complex)     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Código        │    │   Validación    │    │   Firma Digital │
│   Comentado     │    │   Datos         │    │   XAdES-BES     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### 2.2 Problemas Identificados
- **Clases monolíticas** (Factura.kt con 800+ líneas)
- **Código comentado extenso** en Main.kt
- **Métodos complejos** en GenerarDocumentos.kt
- **Falta de logging estructurado**
- **Ausencia de tests unitarios**
- **Manejo de errores inconsistente**

---

## 3. Arquitectura Propuesta

### 3.1 Arquitectura de Refactoring

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
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                    CAPA DE MODELOS                              │
├─────────────────────────────────────────────────────────────────┤
│  Domain Models                                                  │
│  ├── Factura.kt (Refactorizado)                                │
│  ├── InformacionTributaria.kt                                  │
│  ├── InformacionFactura.kt                                     │
│  ├── Detalle.kt                                                │
│  └── Impuesto.kt                                               │
│                                                                 │
│  DTOs                                                           │
│  ├── FacturaRequest.kt                                         │
│  ├── FacturaResponse.kt                                        │
│  └── SriResponse.kt                                            │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                    CAPA DE INFRAESTRUCTURA                      │
├─────────────────────────────────────────────────────────────────┤
│  Utils                                                          │
│  ├── Logger.kt (Logging estructurado)                          │
│  ├── FileManager.kt (Gestión archivos)                         │
│  ├── ConfigValidator.kt (Validación configuración)              │
│  └── ExceptionHandler.kt (Manejo excepciones)                  │
│                                                                 │
│  External Libraries                                             │
│  ├── MITyC Libraries (Firma digital)                           │
│  ├── SRI Web Services (Envío documentos)                        │
│  └── Klaxon (JSON parsing)                                     │
└─────────────────────────────────────────────────────────────────┘
```

### 3.2 Patrones de Diseño Aplicados

**1. Service Layer Pattern**
- Separación de responsabilidades por servicio
- FacturaService, FirmaService, SriService

**2. Builder Pattern**
- Para construcción de objetos Factura complejos
- Validación en cada paso de construcción

**3. Strategy Pattern**
- Diferentes estrategias de validación
- Múltiples tipos de documentos

**4. Factory Pattern**
- Creación de diferentes tipos de documentos
- Instanciación de servicios

**5. Observer Pattern**
- Logging de eventos del sistema
- Notificaciones de estado

---

## 4. Componentes Detallados

### 4.1 FacturaService
```kotlin
class FacturaService {
    private val generator: FacturaGenerator
    private val validator: FacturaValidator
    private val serializer: FacturaSerializer
    
    fun crearFactura(request: FacturaRequest): FacturaResponse
    fun validarFactura(factura: Factura): ValidationResult
    fun generarXML(factura: Factura): String
}
```

### 4.2 FirmaService
```kotlin
class FirmaService {
    private val certificateManager: CertificateManager
    private val xadesSigner: XAdESSigner
    private val signatureValidator: SignatureValidator
    
    fun firmarDocumento(xml: String, certificado: String): String
    fun validarCertificado(certificado: String): Boolean
    fun verificarFirma(xmlFirmado: String): Boolean
}
```

### 4.3 SriService
```kotlin
class SriService {
    private val client: SriClient
    private val responseHandler: ResponseHandler
    private val retryManager: RetryManager
    
    fun enviarDocumento(xmlFirmado: String): SriResponse
    fun consultarEstado(claveAcceso: String): EstadoDocumento
    fun reintentarEnvio(documento: String): SriResponse
}
```

---

## 5. Estructura de Paquetes Refactorizada

```
src/main/kotlin/
├── application/
│   ├── Main.kt
│   ├── Application.kt
│   └── CliInterface.kt
├── services/
│   ├── factura/
│   │   ├── FacturaService.kt
│   │   ├── FacturaGenerator.kt
│   │   ├── FacturaValidator.kt
│   │   └── FacturaSerializer.kt
│   ├── firma/
│   │   ├── FirmaService.kt
│   │   ├── CertificateManager.kt
│   │   ├── XAdESSigner.kt
│   │   └── SignatureValidator.kt
│   └── sri/
│       ├── SriService.kt
│       ├── SriClient.kt
│       ├── ResponseHandler.kt
│       └── RetryManager.kt
├── models/
│   ├── domain/
│   │   ├── Factura.kt
│   │   ├── InformacionTributaria.kt
│   │   ├── InformacionFactura.kt
│   │   ├── Detalle.kt
│   │   └── Impuesto.kt
│   └── dto/
│       ├── FacturaRequest.kt
│       ├── FacturaResponse.kt
│       └── SriResponse.kt
├── utils/
│   ├── Logger.kt
│   ├── FileManager.kt
│   ├── ConfigValidator.kt
│   └── ExceptionHandler.kt
└── config/
    ├── ApplicationConfig.kt
    └── SriConfig.kt
```

---

## 6. Flujo de Datos Refactorizado

### 6.1 Flujo Principal
```
1. CliInterface recibe parámetros
2. ConfigLoader carga configuración
3. FacturaService crea factura
4. FacturaValidator valida datos
5. FacturaGenerator genera XML
6. FirmaService firma documento
7. SriService envía al SRI
8. ResponseHandler procesa respuesta
9. Logger registra resultado
```

### 6.2 Manejo de Errores
```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Error         │───▶│   Exception     │───▶│   Logger        │
│   Detection     │    │   Handler       │    │   Structured    │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Retry Logic   │    │   Error         │    │   Monitoring    │
│   (SriService)  │    │   Recovery      │    │   & Alerting    │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

---

## 7. Configuración y Dependencias

### 7.1 Dependencias Mantenidas
```gradle
dependencies {
    // Core Kotlin
    compile "org.jetbrains.kotlin:kotlin-stdlib-jdk8"
    
    // Firma Digital (Mantener)
    compile fileTree(include: ['*.jar'], dir: 'libs')
    
    // JSON Parsing (Actualizar compatible)
    compile 'com.beust:klaxon:5.0.1'
    
    // Logging (Mejorar)
    compile group: 'org.apache.logging.log4j', name: 'log4j-api', version: '2.11.2'
    compile group: 'org.apache.logging.log4j', name: 'log4j-core', version: '2.11.2'
    
    // Testing (Agregar)
    testCompile group: 'junit', name: 'junit', version: '4.12'
    testCompile group: 'org.jetbrains.kotlin', name: 'kotlin-test-junit', version: '1.3.11'
}
```

### 7.2 Configuración de Aplicación
```kotlin
data class ApplicationConfig(
    val ambiente: String = "1", // 1=Pruebas, 2=Producción
    val directorioXML: String = "./xml",
    val directorioFirmados: String = "./firmados",
    val certificado: String = "",
    val claveCertificado: String = "",
    val debug: Boolean = true,
    val logging: LoggingConfig = LoggingConfig()
)

data class LoggingConfig(
    val level: String = "INFO",
    val file: String = "./logs/facturacion.log",
    val maxSize: String = "10MB",
    val maxFiles: Int = 5
)
```

---

## 8. Testing Strategy

### 8.1 Unit Tests
- **FacturaService:** Testing de generación y validación
- **FirmaService:** Testing de firma y validación
- **SriService:** Testing de envío y manejo de respuestas
- **Utils:** Testing de utilidades

### 8.2 Integration Tests
- **Flujo completo:** Crear → Firmar → Enviar
- **Manejo de errores:** Testing de escenarios de fallo
- **Configuración:** Testing con diferentes configuraciones

### 8.3 Test Structure
```
src/test/kotlin/
├── services/
│   ├── factura/FacturaServiceTest.kt
│   ├── firma/FirmaServiceTest.kt
│   └── sri/SriServiceTest.kt
├── models/
│   └── FacturaTest.kt
├── utils/
│   └── LoggerTest.kt
└── integration/
    └── FacturacionFlowTest.kt
```

---

## 9. Logging y Monitoreo

### 9.1 Logging Estructurado
```kotlin
class Logger {
    fun infoFacturaCreada(facturaId: String, cliente: String)
    fun infoDocumentoFirmado(documentoId: String, certificado: String)
    fun infoEnvioSri(documentoId: String, respuesta: String)
    fun errorFirmaFallida(documentoId: String, error: Exception)
    fun errorEnvioSri(documentoId: String, error: Exception)
}
```

### 9.2 Métricas de Monitoreo
- **Tiempo de generación** de facturas
- **Tasa de éxito** de firma digital
- **Tiempo de respuesta** del SRI
- **Errores por tipo** y frecuencia

---

## 10. Plan de Migración

### 10.1 Fase 1: Preparación (Semana 1)
- ✅ Análisis del código existente
- ✅ Definición de estructura de paquetes
- ✅ Creación de interfaces base

### 10.2 Fase 2: Refactoring Core (Semana 2)
- 🔄 Refactoring de FacturaService
- 🔄 Separación de responsabilidades
- 🔄 Implementación de logging

### 10.3 Fase 3: Servicios Especializados (Semana 3)
- 🔄 Refactoring de FirmaService
- 🔄 Refactoring de SriService
- 🔄 Implementación de manejo de errores

### 10.4 Fase 4: Testing y Documentación (Semana 1)
- 🔄 Implementación de tests unitarios
- 🔄 Testing de integración
- 🔄 Documentación técnica

---

## 11. Criterios de Éxito

### 11.1 Métricas de Calidad
- **Complejidad ciclomática:** < 10 por método
- **Líneas de código:** < 200 por clase
- **Cobertura de tests:** > 80%
- **Tiempo de build:** < 2 minutos

### 11.2 Métricas Funcionales
- **Tiempo de generación:** < 5 segundos
- **Tasa de éxito firma:** > 95%
- **Tiempo de envío SRI:** < 30 segundos
- **Disponibilidad:** > 99%

---

## 12. Riesgos y Mitigaciones

### 12.1 Riesgos Técnicos
- **Riesgo:** Incompatibilidad con MITyC
- **Mitigación:** Testing exhaustivo con certificados reales

- **Riesgo:** Pérdida de funcionalidad durante refactoring
- **Mitigación:** Tests de regresión y validación continua

### 12.2 Riesgos de Negocio
- **Riesgo:** Interrupción del servicio
- **Mitigación:** Implementación gradual y rollback plan

---

*Este documento será actualizado conforme avance el refactoring y se obtenga más información técnica.*
