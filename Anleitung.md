# YouTube Fact Checker Bot 🤖

Ein automatisierter Faktenprüfungs-Bot, der YouTube-Videos analysiert und Behauptungen mit wissenschaftlichen Methoden überprüft.

## 🎯 Was macht dieser Bot?

Der YouTube Fact Checker Bot ist ein intelligenter Faktenprüfer, der:

- **YouTube-Videos automatisch analysiert** (Transkript extrahiert, Claims identifiziert)
- **Behauptungen systematisch überprüft** mit Multi-Source-Triangulation
- **Bias und Propaganda erkennt** in Quellen und Aussagen
- **Professionelle HTML-Reports** generiert
- **Telegram-Integration** für einfache Bedienung

## 🧠 Kernprinzipien des Fact-Checking

### Neutralität & Skepsis
- **Jede Quelle hat eine Agenda** (Propaganda-Grad > 0)
- **Glaubwürdigkeit ≠ Wahrheit** - nur überprüfbare Evidenz zählt
- **Transparenz vor Urteil** - Denkwege und Unsicherheiten werden offengelegt
- **Keine Politik-Empfehlungen** - nur prüfbare Aussagen, Indizien und Logik

### Wissenschaftliche Methoden
- **Claim-first**: Extrahiert überprüfbare, atomare Behauptungen
- **Triangulation**: Mindestens zwei unabhängige Primärquellen
- **Bias-Ledger**: Bewertet Quellen nach Interessen (0-3 Score)
- **Steelman + Red Team**: Stärkste Pro- und Contra-Argumente
- **Bayes-Kalibrierung**: Kalibrierte Konfidenz (0-100%)

## 🛠️ Technische Architektur

### Hauptkomponenten
- **n8n Workflow Engine** - Orchestriert den gesamten Prozess
- **Telegram Bot** - Benutzerinterface
- **Supadata API** - YouTube Video- und Transkript-Extraktion
- **OpenRouter** - KI-Modelle (GPT-5, Mistral, Gemini)
- **MCP Server** - Web-Recherche und Zeitkontext
- **PostgreSQL** - Datenbank für Caching und Sessions

### Workflow-Schritte
1. **Telegram-Trigger** - Empfängt YouTube-Links
2. **URL-Klassifizierung** - Erkennt YouTube-Links
3. **Video-Verarbeitung** - Extrahiert Metadaten und Transkript
4. **Claim-Extraktion** - KI identifiziert überprüfbare Behauptungen
5. **Faktenprüfung** - Multi-Source-Recherche und Analyse
6. **Report-Generierung** - Erstellt HTML-Berichte
7. **Telegram-Delivery** - Sendet Ergebnisse an Nutzer

## 🚀 Installation & Setup

### Voraussetzungen
- n8n (Cloud oder Self-hosted)
- Telegram Bot Token
- Supadata API Key
- OpenRouter API Key
- Smithery.ai Account (für MCP Server)
- PostgreSQL Datenbank

### 1. Repository klonen
```bash
git clone https://github.com/Silverstar187/youtube-fact-checker.git
cd youtube-fact-checker
```

### 2. n8n Workflow importieren
1. Öffne deine n8n-Instanz
2. Importiere `youtube-fact-checker-workflow.json`
3. Konfiguriere alle Credentials

### 3. API-Keys konfigurieren

#### Telegram Bot
1. Erstelle einen Bot via [@BotFather](https://t.me/botfather)
2. Kopiere den Bot Token
3. Konfiguriere in n8n Credentials

#### Supadata
1. Registriere dich bei [Supadata](https://supadata.ai)
2. Erstelle einen API Key
3. Konfiguriere in n8n

#### OpenRouter
1. Erstelle Account bei [OpenRouter](https://openrouter.ai)
2. Füge Credits hinzu
3. Erstelle API Key
4. Konfiguriere in n8n

#### Smithery.ai (MCP Server)
1. Gehe zu [Smithery.ai](https://smithery.ai)
2. Erstelle Account
3. Gehe zu [API Keys](https://smithery.ai/dashboard/api-keys)
4. Erstelle neuen API Key
5. Ersetze in den MCP Client Tool Nodes:
   - `YOUR_SMITHERY_API_KEY` → dein API Key
   - `YOUR_PROFILE_ID` → deine Profile ID

### 4. Datenbank einrichten
1. Erstelle PostgreSQL Datenbank
2. Konfiguriere Connection in n8n
3. Erstelle Tabellen für Sessions und Transcripts

## 📊 Verwendung

### Telegram Bot starten
1. Sende `/start` an den Bot
2. Sende einen YouTube-Link
3. Warte auf Analyse (2-15 Minuten)
4. Erhalte HTML-Report als Download

### Beispiel-Interaktion
```
Du: https://youtube.com/watch?v=example
Bot: 🤖 Analysiere Video... das dauert ein paar Minuten
Bot: [HTML-Report als Datei]
```

## 🔍 Fact-Checking Methodologie

### 1. Claim-Extraktion
- **Atomare Behauptungen** werden identifiziert
- **Kategorisierung**: empirisch, historisch, rechtlich, kausal, prognose
- **Propaganda-Signale** werden markiert

### 2. Evidenz-Sammlung
- **Primärquellen**: Originaldokumente, amtliche Daten, Protokolle
- **Sekundärquellen**: Verschiedene Lager und Perspektiven
- **Bias-Bewertung**: Jede Quelle wird nach Interessen bewertet

### 3. Triangulation
- **Multi-Source-Verifikation** mit unabhängigen Quellen
- **Timeline-Analyse** für zeitliche Kohärenz
- **Zitat-Treue-Prüfung** mit Originalkontext

### 4. Bewertung
- **Steelman/Red Team**: Stärkste Gegenargumente
- **Bayes-Update**: Konfidenz-Kalibrierung
- **Verdict**: wahr, überwiegend_wahr, gemischt, überwiegend_falsch, falsch, unprüfbar

## 📈 Ausgabeformate

### Telegram-Kurzbericht
```
[Fact-Check] Video-Titel
• Claim C001: Behauptung → Urteil: wahr (Konfidenz 85%)
• Wichtigste Evidenz: 2-3 Stichpunkte
• Stärkstes Gegenargument: 1 Satz
• Was fehlt: max 2 Punkte
```

### HTML-Report
- **Gesamtbewertung** mit visuellen Scores
- **Zusammenfassung** (Was stimmt/Was nicht)
- **Detaillierte Analyse** aller Claims
- **Quellenangaben** mit Bias-Bewertung
- **Methodik-Erklärung**

### JSON-Output
Strukturierte Daten für weitere Verarbeitung:
```json
{
  "source": {...},
  "claims": [...],
  "evidence": [...],
  "meta": {...}
}
```

## ⚙️ Konfiguration

### Umgebungsvariablen
```bash
TELEGRAM_BOT_TOKEN=your_bot_token
SUPADATA_API_KEY=your_supadata_key
OPENROUTER_API_KEY=your_openrouter_key
SMITHERY_API_KEY=your_smithery_key
POSTGRES_CONNECTION_STRING=your_db_connection
```

### n8n Credentials
- **Telegram API**: Bot Token
- **Supadata API**: API Key
- **OpenRouter API**: API Key
- **PostgreSQL**: Connection String

## 🔒 Sicherheit & Datenschutz

### API-Key Management
- **Niemals echte Keys** in Templates teilen
- **Umgebungsvariablen** für sensible Daten
- **Regelmäßige Rotation** der API-Keys

### Datenverarbeitung
- **Lokale Verarbeitung** wo möglich
- **Minimale Datensammlung** nur für Fact-Checking
- **Keine dauerhafte Speicherung** persönlicher Daten

## 🐛 Troubleshooting

### Häufige Probleme
1. **API-Limits erreicht** → Credits auffüllen
2. **Transkript nicht verfügbar** → Video hat keine Untertitel
3. **MCP Server Fehler** → API-Keys prüfen
4. **Datenbank-Verbindung** → Connection String prüfen

### Logs prüfen
- n8n Execution Logs
- Telegram Bot Logs
- Datenbank-Queries

## 🤝 Beitragen

### Bug Reports
- Erstelle Issue mit detaillierter Beschreibung
- Füge Logs und Screenshots hinzu

### Feature Requests
- Beschreibe gewünschte Funktionalität
- Erkläre Use Case und Nutzen

### Pull Requests
1. Fork das Repository
2. Erstelle Feature Branch
3. Committe Änderungen
4. Erstelle Pull Request

## 📄 Lizenz

MIT License - siehe [LICENSE](LICENSE) für Details.

## 🙏 Danksagungen

- **n8n** für die Workflow-Engine
- **OpenRouter** für KI-Modelle
- **Supadata** für YouTube-Integration
- **Smithery.ai** für MCP Server
- **Telegram** für Bot-Platform

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/Silverstar187/youtube-fact-checker/issues)
- **Discussions**: [GitHub Discussions](https://github.com/Silverstar187/youtube-fact-checker/discussions)
- **Email**: [Deine Email]

---

**⚠️ Disclaimer**: Dieser Bot ist ein Tool zur Unterstützung der Faktenprüfung. Die Ergebnisse sind nicht als absolute Wahrheit zu verstehen und sollten immer kritisch hinterfragt werden. Keine Politikempfehlung - nur überprüfbare Fakten und Logik.
