# 🍎 Contador de Calorías

<div align="center">

Una aplicación iOS moderna para análisis nutricional con IA

[![Swift](https://img.shields.io/badge/Swift-6.2+-orange.svg)](https://swift.org)
[![iOS](https://img.shields.io/badge/iOS-18.0+-blue.svg)](https://www.apple.com/ios/)
[![SwiftUI](https://img.shields.io/badge/SwiftUI-6.0+-green.svg)](https://developer.apple.com/xcode/swiftui/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-0.8.9-blue.svg)](https://github.com/juliocuesta/ContadorDeCalorias/releases)

</div>

---

## 📖 Descripción

**Contador de Calorías** es una aplicación iOS que utiliza inteligencia artificial para analizar el contenido nutricional de los alimentos a través de múltiples métodos:

- 📷 **Análisis por imagen** con OpenAI GPT-4 Vision o Google Gemini
- 🔍 **Búsqueda por texto** con Perplexity Sonar
- 📊 **Escaneo de códigos de barras** con OpenFoodFacts
- 🌐 **Enriquecimiento con contexto web** de fuentes oficiales

La app está diseñada con las últimas tecnologías de Apple, incluyendo Swift 6, SwiftUI 6, y características modernas como el framework Observation, Swift Concurrency, y TipKit.

## ✨ Características Principales

### 🧠 Inteligencia Artificial Multi-Servicio

- **OpenAI GPT-4 Vision**: Análisis preciso de imágenes de alimentos
- **Google Gemini**: Alternativa rápida para reconocimiento visual
- **Perplexity Sonar**: Análisis contextual de texto con verificación web
- **OpenFoodFacts**: Base de datos colaborativa para productos comerciales
- **Fallback automático**: Cambio inteligente entre servicios si uno falla

### 📱 Métodos de Captura

- **Cámara en tiempo real**: Captura directa con previsualización
- **Galería de fotos**: Selección de imágenes existentes
- **Escáner de códigos de barras**: Lectura rápida de EAN-13/UPC
- **Entrada manual de código**: Teclado numérico para códigos de barras
- **Búsqueda por texto**: Descripción libre del alimento

### 🔒 Seguridad y Privacidad

- **Encriptación AES-256-GCM**: Protección de datos sensibles
- **Modo invitado**: Permite un uso basico sin configurar claves propias
- **Rate limiting**: Control de cuota por servicio en el modo invitado
- **Sin telemetría**: Cero recopilación de datos del usuario
- **Política de Privacidad**: Ver [privacy-policy.html](privacy-policy.html) para más detalles sobre el tratamiento de datos

### 📊 Información Nutricional Completa

- Macronutrientes (calorías, proteína, carbohidratos, grasas)
- Micronutrientes (vitaminas y minerales)
- Alérgenos y advertencias
- Índice Nova (nivel de procesamiento)
- Nutri-Score y etiquetado frontal
- Factores dietéticos (vegano, vegetariano, ecológico)

### 🎨 Interfaz Moderna

- **SwiftUI 6** con Liquid Glass effects (iOS 26+)
- **Modo oscuro** adaptativo
- **Dynamic Type** para accesibilidad
- **VoiceOver** completamente compatible
- **TipKit** para onboarding contextual
- **Toasts** para notificaciones no intrusivas

## 🛠️ Requisitos

- **Xcode**: 26.0+
- **Swift**: 6.2+
- **iOS**: 26.0+
- **macOS**: 26.0+ (para desarrollo)

### API Keys (Opcional)

La app funciona en **modo invitado** sin configuración, pero puedes usar tus propias claves:

- [OpenAI API Key](https://platform.openai.com/api-keys) - GPT-4 Vision
- [Google AI Studio](https://aistudio.google.com/app/apikey) - Gemini
- [Perplexity API](https://www.perplexity.ai/settings/api) - Sonar Pro

## 🚀 Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/juliocuesta/ContadorDeCalorias.git
cd ContadorDeCalorias
```

### 2. Abrir en Xcode

```bash
open ContadorDeCalorias.xcodeproj
```

### 3. Configurar equipo de desarrollo

1. Selecciona el proyecto en el navegador
2. En **Signing & Capabilities**, selecciona tu equipo
3. Cambia el Bundle ID si es necesario

### 4. Compilar y ejecutar

```bash
# Build desde terminal
xcodebuild build \
  -project ContadorDeCalorias.xcodeproj \
  -scheme ContadorDeCalorias \
  -destination 'platform=iOS Simulator,name=iPhone 17'

# O presiona Cmd+R en Xcode
```

## 📐 Arquitectura

### Patrón MVVM + Clean Architecture

```
┌─────────────────────────────────────────────────────┐
│                  Presentation Layer                 │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────┐ │
│  │  SwiftUI     │  │  ViewModels  │  │  Views   │ │
│  │  @Observable │  │  @MainActor  │  │          │ │
│  └──────────────┘  └──────────────┘  └──────────┘ │
└─────────────────────────────────────────────────────┘
                         ▼
┌─────────────────────────────────────────────────────┐
│                   Domain Layer                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────┐ │
│  │  Entities    │  │  Use Cases   │  │ Protocols│ │
│  │  FoodItem    │  │  Business    │  │          │ │
│  └──────────────┘  └──────────────┘  └──────────┘ │
└─────────────────────────────────────────────────────┘
                         ▼
┌─────────────────────────────────────────────────────┐
│                    Data Layer                       │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────┐ │
│  │ Repositories │  │  Services    │  │ SwiftData│ │
│  │              │  │  API Clients │  │          │ │
│  └──────────────┘  └──────────────┘  └──────────┘ │
└─────────────────────────────────────────────────────┘
```

### Componentes Principales

- **AppFactory**: Dependency Injection Container
- **NavigationCoordinator**: Gestión centralizada de navegación
- **ViewModels**: `@Observable` con Swift Concurrency
- **Repositories**: Abstracción de acceso a datos
- **Services**: Integración con APIs externas
- **SwiftData**: Persistencia local moderna

## 🔧 Configuración

### API Keys Propias (Opcional)

1. Abre la app y toca el botón **IA** en el toolbar
2. Toca **"Configurar API Keys"**
3. Selecciona el servicio (OpenAI, Gemini o Perplexity)
4. Introduce tu clave API
5. Autentica con Face ID/Touch ID
6. La clave se guarda encriptada en Keychain

### Ajustes Disponibles

- **Servicio de IA preferido**: OpenAI o Gemini
- **Fallback automático**: Cambiar de servicio si falla
- **Modelo Perplexity**: Fast o Pro
- **Contexto web**: Enriquecimiento con fuentes oficiales
- **Protección biométrica**: Requiere Face ID para cada consulta
- **Tablas nutricionales**: Personaliza qué información mostrar

## 📱 Uso

### Análisis por Imagen

1. Toca el botón **Cámara** en la TabBar
2. Captura la foto del alimento
3. La IA analiza y muestra información nutricional
4. Guarda en historial si lo deseas

### Escaneo de Código de Barras

1. Toca el botón **Código** en la TabBar
2. Usa **"Activar Escáner"** para cámara en tiempo real
3. O introduce el código manualmente
4. Obtén datos de OpenFoodFacts

### Búsqueda por Texto

1. Toca el botón **Buscar** en la TabBar
2. Describe el alimento (ej: "100g de pollo asado")
3. Perplexity analiza y genera la ficha nutricional

## 🧪 Testing

### Ejecutar Tests

```bash
# Todos los tests
xcodebuild test \
  -project ContadorDeCalorias.xcodeproj \
  -scheme ContadorDeCalorias \
  -destination 'platform=iOS Simulator,name=iPhone 17'

# Tests unitarios específicos
xcodebuild test \
  -only-testing:ContadorDeCaloriasTests/SecureEncryptionTests

# Tests de UI
xcodebuild test \
  -only-testing:ContadorDeCaloriasUITests
```

### Framework de Testing

- **Swift Testing**: Tests unitarios y de integración
- **XCUITest**: Tests de interfaz de usuario
- **Cobertura mínima**: 85%

### Estructura de Tests

```
ContadorDeCaloriasTests/
├── Domain/              # Lógica de negocio
├── Data/                # Repositorios y servicios
├── UseCases/            # Casos de uso
├── ViewModels/          # ViewModels
└── Mocks/               # Objetos mock

ContadorDeCaloriasUITests/
├── ServiceSelectorGuestModeUITests.swift
├── SettingsIAUITests.swift
└── ...
```

## 🤝 Contribución

Las contribuciones son bienvenidas. Por favor:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add: Amazing feature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

### Guía de Estilo

- **SwiftLint**: Ejecuta antes de commit
- **Indentación**: 4 espacios
- **Línea máxima**: 120 caracteres
- **Naming**: UpperCamelCase para tipos, lowerCamelCase para variables
- **Commits**: Conventional Commits (feat, fix, refactor, docs, test)

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Ver [LICENSE](LICENSE) para más detalles.

## 🙏 Créditos

### APIs y Servicios

- [OpenAI](https://openai.com) - GPT-4 Vision API
- [Google AI](https://ai.google.dev) - Gemini API
- [Perplexity](https://www.perplexity.ai) - Sonar API
- [OpenFoodFacts](https://world.openfoodfacts.org) - Base de datos colaborativa

### Herramientas

- [Xcode](https://developer.apple.com/xcode/) - IDE oficial de Apple
- [SwiftLint](https://github.com/realm/SwiftLint) - Linter para Swift
- [Claude Code](https://claude.com/code) - Asistencia en desarrollo

## 📞 Contacto

**Julio Cuesta**

- GitHub: [@juliocuesta](https://github.com/juliocuesta)
- Email: [tu-email@example.com](mailto:tu-email@example.com)

---

<div align="center">

**Hecho con ❤️ usando Swift y SwiftUI**

[⬆ Volver arriba](#-contador-de-calorías)

</div>
