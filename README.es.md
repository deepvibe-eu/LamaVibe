> Machine-translated from [README.md](README.md) into Español — corrections welcome.

# LamaVibe

<div align="center">
  <img src="packages/desktop/build/README-images/LamaVibe_ru.png" alt="Captura de pantalla de LamaVibe" width="auto" />
</div>

<p align="center">
  <a href="https://deepvibe.eu/lamavibe">lamavibe.eu</a>
</p>

LamaVibe es la **build de Ollama** de la familia _Vibe_ — un fork de ZCode enfocado en un único proveedor: **Ollama** (modelos locales). Un modelo, un espacio de trabajo, un compañero — no un agente.

La familia _Vibe_ distribuye una aplicación enfocada por proveedor (DeepVibe para DeepSeek, KimiVibe para Kimi, LamaVibe para Ollama, MiniVibe para MiniMax, KlausVibe para Claude, …), cada una con su propio carácter. Existe **junto a** ZCode, no en su lugar: ZCode para el flujo de trabajo multiproveedor, las aplicaciones Vibe para quienes quieren un modelo, un espacio de trabajo, un compañero. Consulta el repositorio principal del código fuente para ver la base de código completa.

## Descargas

Los instaladores para macOS, Windows y Linux están en la [página de releases](../../releases); la versión más reciente siempre está etiquetada como **latest**:

| Plataforma | Archivos |
| --- | --- |
| macOS (Apple Silicon) | `LamaVibe-<version>-mac-arm64.dmg` · `LamaVibe-<version>-mac-arm64.zip` |
| Windows | `LamaVibe-<version>-win-x64.exe` |
| Linux | `LamaVibe-<version>-linux-x86_64.AppImage` · `LamaVibe-<version>-linux-amd64.deb` · `LamaVibe-<version>-linux-x86_64.rpm` · `LamaVibe-<version>-linux-x64.pkg.tar.zst` |

Cada aplicación de la familia *Vibe* se publica con el **mismo número de versión** (actualmente 1.0.3). El actualizador integrado comprueba la última release de este repositorio.

> **macOS (Apple Silicon):** la build **no está firmada** (sin Apple Developer Program de pago), por lo que Gatekeeper
> avisa en el primer inicio. La aplicación está firmada ad-hoc — ábrela una vez con **clic derecho → Abrir**, o ejecuta
> `xattr -dr com.apple.quarantine "/Applications/LamaVibe.app"`.

## Compilar desde el código fuente

Requiere Git, Node.js **24.14.0** y pnpm **10.33.2** (ver `mise.toml`).

```bash
pnpm bootstrap
# run the LamaVibe flavor in dev
pnpm dev:desktop:lama
# package (LamaVibe flavor)
ZCODE_LAMA_IDENTITY=1 pnpm bundle:desktop -- --os linux --arch x64
```

## Uso de modelos locales

LamaVibe se comunica con tu servidor local de [Ollama](https://ollama.com) en `http://localhost:11434/v1`. El proveedor integrado **Ollama (Local)** **no necesita clave de API**.

1. Asegúrate de que Ollama esté en ejecución y de que tengas al menos un modelo de chat, por ejemplo `ollama pull qwen2.5-coder:7b`.
2. Abre **Ajustes → Proveedores de modelos → Ollama (Local) → Añadir modelo**.
3. Haz clic en **Cargar modelos** para listar los modelos instalados en tu máquina y elige uno (o escribe el ID del modelo).
4. Mantén el formato de API en **Compatible con OpenAI (chat completions)**.

**Llamadas a herramientas:** En *Avanzado → Capacidades* encontrarás un interruptor de **Llamadas a herramientas**. Está **desactivado por defecto para proveedores locales**, porque la mayoría de los modelos locales o no admiten el llamamiento a funciones o lo exponen de forma diferente. Actívalo solo si tu modelo realmente admite las llamadas a herramientas de Ollama — de lo contrario Ollama rechazará la solicitud con HTTP 400 `does not support tools`. Para chat simple, déjalo desactivado.

**Modelos de embeddings** como `nomic-embed-*` están pensados para memoria y búsqueda semántica (embeddings), no para chatear — elige un modelo de chat para un hilo.

## Licencia y atribución

Basado en ZCode (Apache-2.0); la licencia y el NOTICE se conservan. LamaVibe es un proyecto independiente y no está afiliado a ZCode/Z.ai ni a Ollama. Ollama es una marca registrada de su propietario; el logotipo se usa con permiso del operador.
