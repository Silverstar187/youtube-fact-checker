# YouTube Fact Checker Bot 🤖

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![n8n](https://img.shields.io/badge/n8n-Workflow-blue)](https://n8n.io)
[![Telegram](https://img.shields.io/badge/Telegram-Bot-2CA5E0)](https://telegram.org)

Ein intelligenter Faktenprüfungs-Bot, der YouTube-Videos automatisch analysiert und Behauptungen mit wissenschaftlichen Methoden überprüft.

## ✨ Features

- 🎥 **Automatische YouTube-Analyse** - Extrahiert Transkripte und Metadaten
- 🧠 **KI-gestützte Claim-Extraktion** - Identifiziert überprüfbare Behauptungen
- 🔍 **Multi-Source-Fact-Checking** - Triangulation mit unabhängigen Quellen
- 📊 **Bias-Erkennung** - Bewertet Quellen nach Interessen und Agenda
- 📄 **Professionelle HTML-Reports** - Visuelle Darstellung der Ergebnisse
- 💬 **Telegram-Integration** - Einfache Bedienung via Chat
- 🗄️ **Intelligentes Caching** - Vermeidet doppelte Analysen

## 🚀 Quick Start

1. **Repository klonen**
   ```bash
   git clone https://github.com/Silverstar187/youtube-fact-checker.git
   cd youtube-fact-checker
   ```

2. **n8n Workflow importieren**
   - Öffne deine n8n-Instanz
   - Importiere `White_Rabbit_Fact_Checker Bot.json`
   - Konfiguriere alle API-Keys

3. **Telegram Bot starten**
   - Sende `/start` an den Bot
   - Sende einen YouTube-Link
   - Erhalte detaillierten Fact-Check-Report

## 📖 Dokumentation

- **[Vollständige Anleitung](Anleitung.md)** - Detaillierte Setup- und Konfigurationsanweisungen
- **[API-Dokumentation](docs/api.md)** - Technische Referenz
- **[Troubleshooting](docs/troubleshooting.md)** - Häufige Probleme und Lösungen

## 🛠️ Technologie-Stack

- **n8n** - Workflow-Orchestrierung
- **Telegram Bot API** - Benutzerinterface
- **OpenRouter** - KI-Modelle (GPT-5, Mistral, Gemini)
- **Supadata** - YouTube-Integration
- **Smithery.ai** - MCP Server für Web-Recherche
- **PostgreSQL** - Datenbank und Caching

## 🔒 Sicherheit

- ✅ Alle API-Keys aus Template entfernt
- ✅ Platzhalter für sichere Konfiguration
- ✅ Keine sensiblen Daten im Repository

## 📄 Lizenz

MIT License - siehe [LICENSE](LICENSE) für Details.

## 🤝 Beitragen

Wir freuen uns über Beiträge! Bitte erstelle ein Issue oder Pull Request.

## ⚠️ Disclaimer

Dieser Bot ist ein Tool zur Unterstützung der Faktenprüfung. Die Ergebnisse sind nicht als absolute Wahrheit zu verstehen und sollten immer kritisch hinterfragt werden.
