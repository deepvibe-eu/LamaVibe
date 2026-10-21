> Machine-translated from [README.md](README.md) into Español — corrections welcome.

# LamaVibe

<div align="center">
  <img src="packages/desktop/build/README-images/LamaVibe_ru.png" alt="Captura de pantalla de LamaVibe" width="auto" />
</div>

<p align="center">
  <a href="https://deepvibe.eu/lamavibe">lamavibe.eu</a>
</p>

LamaVibe es la **compilación para Ollama** de la familia _Vibe_ — un fork de ZCode centrado en un único proveedor: **Ollama** (modelos locales). Un modelo, un espacio de trabajo, un compañero — no un agente.

La familia _Vibe_ distribuye una aplicación enfocada por proveedor (DeepVibe para DeepSeek, KimiVibe para Kimi, LamaVibe para Ollama, MiniVibe para MiniMax, KlausVibe para Claude, …), cada una con su propio carácter. Existe **junto a** ZCode, no en su lugar: ZCode para el flujo de trabajo multiproveedor, las aplicaciones Vibe para quienes quieren un modelo, un espacio de trabajo, un compañero. Consulta el repositorio principal del código fuente para ver el código completo.

## Descargas

Los instaladores para macOS, Windows y Linux están en la [página de versiones](../../releases); la versión más reciente siempre lleva la etiqueta **latest**:

| Plataforma | Archivos |
| --- | --- |
| macOS (Apple Silicon) | `LamaVibe-<version>-mac-arm64.dmg` · `LamaVibe-<version>-mac-arm64.zip` |
| Windows | `LamaVibe-<version>-win-x64.exe` |
| Linux | `LamaVibe-<version>-linux-x86_64.AppImage` · `LamaVibe-<version>-linux-amd64.deb` · `LamaVibe-<version>-linux-x86_64.rpm` · `LamaVibe-<version>-linux-x64.pkg.tar.zst` |

Todas las aplicaciones de la familia *Vibe* se publican con el **mismo número de versión** (actualmente 1.0.5). El actualizador integrado comprueba la última versión de este repositorio.

> **macOS (Apple Silicon):** la compilación **no está firmada** (sin el Apple Developer Program de pago), por lo que Gatekeeper
> muestra una advertencia en el primer inicio. La aplicación está firmada de forma ad-hoc — ábrela una vez mediante **clic derecho → Abrir**, o ejecuta
> `xattr -dr com.apple.quarantine "/Applications/LamaVibe.app"`.

## Compilar desde el código fuente

Requiere Git, Node.js **24.14.0** y pnpm **10.33.2** (consulta `mise.toml`).

```bash
pnpm bootstrap
# run the LamaVibe flavor in dev
pnpm dev:desktop:lama
# package (LamaVibe flavor)
ZCODE_LAMA_IDENTITY=1 pnpm bundle:desktop -- --os linux --arch x64
```

## Uso de modelos locales

LamaVibe se comunica con tu servidor local de [Ollama](https://ollama.com) en `http://localhost:11434/v1`. El proveedor integrado **Ollama (Local)** **no necesita clave de API**.

1. Asegúrate de que Ollama esté en ejecución y de tener al menos un modelo de chat, por ejemplo `ollama pull qwen2.5-coder:7b`.
2. Abre **Ajustes → Proveedores de modelos → Ollama (Local) → Añadir modelo**.
3. Haz clic en **Cargar modelos** para listar los modelos instalados en tu máquina y elige uno (o escribe el ID del modelo).
4. Mantén el formato de API en **Compatible con OpenAI (chat completions)**.

**Llamadas a herramientas:** En *Avanzado → Capacidades* encontrarás un interruptor de **Llamadas a herramientas**. Está **desactivado por defecto para los proveedores locales**, porque la mayoría de los modelos locales no admiten el llamado a funciones o lo exponen de forma distinta. Actívalo solo si tu modelo realmente admite las llamadas a herramientas de Ollama — de lo contrario, Ollama rechazará la solicitud con HTTP 400 `does not support tools`. Para chat simple, déjalo desactivado.

**Los modelos de embeddings** como `nomic-embed-*` están pensados para la memoria y la búsqueda semántica (embeddings), no para chatear — elige un modelo de chat para un hilo.

## Licencia y atribución

Basado en ZCode (Apache-2.0); la licencia y el NOTICE se conservan. LamaVibe es un proyecto independiente y no está afiliado a ZCode/Z.ai ni a Ollama. Ollama es una marca registrada de su propietario; el logotipo se utiliza con el permiso del operador.
