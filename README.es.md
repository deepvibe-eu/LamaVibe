> Machine-translated from [README.md](README.md) into Español — corrections welcome.

# LamaVibe

<div align="center">
  <img src="packages/desktop/build/README-images/LamaVibe_ru.png" alt="LamaVibe screenshot" width="auto" />
</div>

<p align="center">
  <a href="https://deepvibe.eu/lamavibe">lamavibe.eu</a>
</p>

LamaVibe es la **versión de Ollama** de la familia _Vibe_ — un fork de ZCode enfocado en un único proveedor: **Ollama** (modelos locales). Un modelo, un espacio de trabajo, un compañero — no un agente.

La familia _Vibe_ ofrece una aplicación enfocada por proveedor (DeepVibe para DeepSeek, KimiVibe para Kimi, LamaVibe para Ollama, MiniVibe para MiniMax, KlausVibe para Claude, …), cada una con su propio carácter. Existe **junto a** ZCode, no en su lugar: ZCode para el flujo de trabajo multiproveedor, las aplicaciones Vibe para quienes quieren un modelo, un espacio de trabajo, un compañero. Consulta el repositorio principal del código fuente para ver la base de código completa.

## Descargas

Los instaladores para macOS, Windows y Linux se publican en [Releases](../../releases). El actualizador integrado comprueba este repositorio.

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

1. Asegúrate de que Ollama esté en ejecución y de que tengas al menos un modelo de chat, por ejemplo `ollama pull qwen2.5-coder:7b`.
2. Abre **Settings → Model providers → Ollama (Local) → Add model**.
3. Haz clic en **Load models** para listar los modelos instalados en tu máquina y elegir uno (o escribe el ID del modelo).
4. Mantén el formato de API en **OpenAI-compatible (chat completions)**.

**Llamadas a herramientas:** En *Advanced → Capabilities* encontrarás un interruptor de **Tool calls**. Está **desactivado de forma predeterminada para los proveedores locales**, porque la mayoría de los modelos locales o no admiten el llamamiento a funciones o lo exponen de forma diferente. Actívalo solo si tu modelo realmente admite las llamadas a herramientas de Ollama — de lo contrario, Ollama rechazará la solicitud con HTTP 400 `does not support tools`. Para chat simple, déjalo desactivado.

**Modelos de embeddings** como `nomic-embed-*` están pensados para memoria y búsqueda semántica (embeddings), no para chatear — elige un modelo de chat para un hilo.

## Licencia y atribución

Construido sobre ZCode (Apache-2.0); la licencia y el NOTICE se conservan. LamaVibe es un proyecto independiente y no está afiliado a ZCode/Z.ai ni a Ollama. Ollama es una marca registrada de su propietario; el logotipo se utiliza con el permiso del operador.
