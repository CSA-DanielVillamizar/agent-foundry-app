# 🏭 Agent Foundry App

> Una aplicación nativa para descubrir, instalar y gestionar agentes de IA especializados

[![Licencia: MIT](https://img.shields.io/badge/Licencia-MIT-blue.svg)](LICENSE)
[![Construido con Tauri 2](https://img.shields.io/badge/Construido%20con-Tauri%202-orange.svg)](https://tauri.app)
[![macOS 13+](https://img.shields.io/badge/macOS-13%2B-black.svg)](https://www.apple.com/macos)
[![Svelte 5](https://img.shields.io/badge/Frontend-Svelte%205-red.svg)](https://svelte.dev)

---

## 📖 ¿Qué es Agent Foundry App?

**Agent Foundry** es una aplicación nativa, de código abierto y con licencia MIT que te permite:

- 🔍 **Explorar** un catálogo completo de agentes IA especializados
- 📦 **Instalar** agentes en tus herramientas de código favoritas
- 📊 **Rastrear** todas tus instalaciones localmente
- 🔄 **Mantener sincronizado** tu ecosistema de agentes
- 🛡️ **Controlar** todo localmente sin telemetría

La aplicación es **100% local-first**, **sin rastreo**, y pone todo el control en tus manos.

---

## 🎯 ¿Por Qué Existe?

El ecosistema de herramientas de codificación con IA es fragmentado. Cada una tiene su propio formato de agentes y ruta de instalación:

- Claude Code
- GitHub Copilot
- Cursor
- Codex
- Gemini CLI
- Qwen Code
- opencode
- Osaurus

**Agent Foundry** unifica esto ofreciendo:

✨ Una interfaz nativa para explorar agentes por división y rol  
✨ Inspección de agentes antes de instalarlos  
✨ Instalaciones determinísticas y verificables  
✨ Seguimiento local de todas las instalaciones  
✨ Detección automática de cambios fuera de la app  
✨ Actualizaciones, eliminación y respaldo sin complicaciones  

---

## ✨ Características Principales

### 🤖 Espacio de Trabajo de Agentes
- Catálogo explorable con tres paneles
- Filtros por división y categoría
- Vista de estado de instalación
- Panel de detalles y controles de despliegue por agente

### 🛠️ Panel de Herramientas
- Visualiza todas las herramientas reconocidas
- Detecta instalaciones automáticamente
- Contadores y versiones disponibles
- Operaciones en lote
- Estado de las herramientas (instaladas/reconocidas)

### 👥 Equipos
- Equipos preestablecidos incluidos
- Crea tus propios equipos personalizados
- Despliegue rápido integrado
- Gestión simplificada de configuraciones

### 📂 Proyectos
- Instalaciones específicas por proyecto
- Navega con master/detail
- Exactamente los agentes y herramientas que necesitas
- Aislamiento por proyecto

### 📋 Seguimiento de Instalaciones
- Registro de cada instalación administrada
- Hashes de origen y renderizado
- Herramienta, destino y alcance guardados
- Referencia de rutas de proyecto

### 🔄 Reconciliación Automática
- Detecta archivos como: actuales, desactualizados, modificados, eliminados o externos
- El Dashboard muestra qué necesita atención
- Filtros inteligentes en el panel de Agentes

### 🚀 Auto-Actualización
- Verificación de manifiesto firmado
- Instalación en lugar con verificación de clave
- Actualización y reinicio con un clic
- Disponible en macOS (Apple Silicon + Intel) desde v0.2.0

### 📚 Registro de Herramientas
- Base única de conocimiento compartida
- Agregar herramientas es editar una entrada JSON
- Instalabilidad derivada automáticamente

### 📊 Dashboard
- Estado de instalaciones
- Gráfico de cobertura global vs por proyecto
- Cobertura cruzada de herramientas
- Enlaces profundos al área de trabajo

### 🔐 Integración de GitHub
- OAuth Device Flow opcional
- Tokens guardados en el keychain del sistema
- Nunca se devuelven al frontend

### 📡 Catálogo Offline-First
- Línea base incluida en la aplicación
- Soporte para clones locales o gestionados
- Funciona sin conexión a internet

### 🖥️ Multiplataforma
- Tauri 2 + Svelte 5
- Interfaz nativa macOS
- Ventanas nativas opacas en Windows/Linux

---

## 🎯 Objetivos de Instalación Compatibles

| Herramienta | Alcance | Destino |
|---|---|---|
| **Claude Code** | usuario | `~/.claude/agents/*.md` |
| **Codex** | usuario | `~/.codex/agents/*.toml` |
| **Gemini CLI** | usuario | `~/.gemini/agents/*.md` |
| **GitHub Copilot** | usuario | `~/.github/agents/*.md` y `~/.copilot/agents/*.md` |
| **Qwen Code** | usuario | `~/.qwen/agents/*.md` |
| **Cursor** | proyecto | `.cursor/rules/*.mdc` |
| **opencode** | proyecto | `.opencode/agents/*.md` |
| **Osaurus** | usuario | `~/.osaurus/skills/agency-<slug>/SKILL.md` |

> 📌 Antigravity, Aider, Windsurf, OpenClaw y Kimi están reconocidos pero requieren trabajo adicional antes de ser instalaciones de primera clase.

---

## ❌ Lo Que NO Es

- ❌ No es un runtime de agentes (instala en otras herramientas, no ejecuta)
- ❌ No reemplaza el repositorio original de agent-foundry
- ❌ No es un producto de telemetría (sin analytics, tracking ni cuentas requeridas)
- ❌ No es un puente de comandos shell

---

## 📦 Instalación

### Descargas Oficiales
Obtén la compilación para tu plataforma desde la [última versión](https://github.com/CSA-DanielVillamizar/agent-foundry-app/releases):

- **macOS** (Apple Silicon & Intel) — .dmg firmado y notarizado, macOS 13+
- **Linux** (x86_64) — .deb, .rpm o .AppImage portable
- **Windows** (x64 & ARM64) — Instalador .exe

### macOS con Homebrew
```bash
brew tap CSA-DanielVillamizar/agent-foundry
brew install --cask agent-foundry-app
