> Machine-translated from [README.md](README.md) into Deutsch — corrections welcome.

# LamaVibe

<div align="center">
  <img src="packages/desktop/build/README-images/LamaVibe_ru.png" alt="LamaVibe screenshot" width="auto" />
</div>

<p align="center">
  <a href="https://deepvibe.eu/lamavibe">lamavibe.eu</a>
</p>

LamaVibe ist der **Ollama-Build** der _Vibe_-Familie — ein Fork von ZCode, der sich auf einen einzigen Anbieter konzentriert: **Ollama** (lokale Modelle). Ein Modell, ein Arbeitsbereich, ein Partner — kein Agent.

Die _Vibe_-Familie liefert eine fokussierte App pro Anbieter (DeepVibe für DeepSeek, KimiVibe für Kimi, LamaVibe für Ollama, MiniVibe für MiniMax, KlausVibe für Claude, …), jede mit ihrem eigenen Charakter. Sie existiert **neben** ZCode, nicht an dessen Stelle: ZCode für den Multi-Provider-Workflow, die Vibe-Apps für alle, die ein Modell, einen Arbeitsbereich, einen Partner wollen. Den vollständigen Codebestand findest du im Hauptquellcode-Repository.

## Downloads

Installer für macOS, Windows und Linux werden unter [Releases](../../releases) veröffentlicht. Der integrierte Updater prüft dieses Repository.

## Aus dem Quellcode bauen

Erfordert Git, Node.js **24.14.0** und pnpm **10.33.2** (siehe `mise.toml`).

```bash
pnpm bootstrap
# run the LamaVibe flavor in dev
pnpm dev:desktop:lama
# package (LamaVibe flavor)
ZCODE_LAMA_IDENTITY=1 pnpm bundle:desktop -- --os linux --arch x64
```

## Lokale Modelle verwenden

LamaVibe kommuniziert mit deinem lokalen [Ollama](https://ollama.com)-Server unter `http://localhost:11434/v1`. Der integrierte Anbieter **Ollama (Local)** benötigt **keinen API-Schlüssel**.

1. Stelle sicher, dass Ollama läuft und du mindestens ein Chat-Modell hast, z. B. `ollama pull qwen2.5-coder:7b`.
2. Öffne **Einstellungen → Modellanbieter → Ollama (Local) → Modell hinzufügen**.
3. Klicke auf **Modelle laden**, um die auf deinem Rechner installierten Modelle aufzulisten und eines auszuwählen (oder gib die Modell-ID ein).
4. Lass das API-Format auf **OpenAI-kompatibel (Chat Completions)**.

**Tool-Aufrufe:** Unter *Erweitert → Fähigkeiten* findest du einen Schalter **Tool-Aufrufe**. Er ist **standardmäßig für lokale Anbieter deaktiviert**, weil die meisten lokalen Modelle entweder keine Funktionsaufrufe unterstützen oder sie anders bereitstellen. Aktiviere ihn nur, wenn dein Modell wirklich Ollama-Tool-Aufrufe unterstützt — andernfalls lehnt Ollama die Anfrage mit HTTP 400 `does not support tools` ab. Für reines Chatten lass ihn aus.

**Embedding-Modelle** wie `nomic-embed-*` sind für Memory und semantische Suche (Embeddings) gedacht, nicht fürs Chatten — wähle für einen Thread ein Chat-Modell.

## Lizenz & Namensnennung

Basiert auf ZCode (Apache-2.0); die Lizenz und der NOTICE-Hinweis bleiben erhalten. LamaVibe ist ein unabhängiges Projekt und steht in keiner Verbindung zu ZCode/Z.ai oder Ollama. Ollama ist eine Marke ihres Inhabers; das Logo wird mit Erlaubnis des Betreibers verwendet.
