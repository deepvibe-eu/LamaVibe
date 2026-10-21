> Machine-translated from [README.md](README.md) into Русский — corrections welcome.

# LamaVibe

<div align="center">
  <img src="packages/desktop/build/README-images/LamaVibe_ru.png" alt="Скриншот LamaVibe" width="auto" />
</div>

<p align="center">
  <a href="https://deepvibe.eu/lamavibe">lamavibe.eu</a>
</p>

LamaVibe — это **сборка Ollama** из семейства _Vibe_ — форк ZCode, ориентированный на одного провайдера: **Ollama** (локальные модели). Одна модель, одно рабочее пространство, партнёр — а не агент.

Семейство _Vibe_ выпускает по одному специализированному приложению на каждого провайдера (DeepVibe для DeepSeek, KimiVibe для Kimi, LamaVibe для Ollama, MiniVibe для MiniMax, KlausVibe для Claude, …), каждое со своим характером. Оно существует **наряду** с ZCode, а не вместо него: ZCode — для работы с несколькими провайдерами, приложения Vibe — для тех, кому нужна одна модель, одно рабочее пространство, один партнёр. Полный исходный код см. в основном репозитории.

## Загрузки

Установщики для macOS, Windows и Linux доступны на [странице релизов](../../releases); самый новый релиз всегда помечен тегом **latest**:

| Платформа | Файлы |
| --- | --- |
| macOS (Apple Silicon) | `LamaVibe-<version>-mac-arm64.dmg` · `LamaVibe-<version>-mac-arm64.zip` |
| Windows | `LamaVibe-<version>-win-x64.exe` |
| Linux | `LamaVibe-<version>-linux-x86_64.AppImage` · `LamaVibe-<version>-linux-amd64.deb` · `LamaVibe-<version>-linux-x86_64.rpm` · `LamaVibe-<version>-linux-x64.pkg.tar.zst` |

Все приложения семейства *Vibe* выпускаются с **одинаковым номером версии** (сейчас 1.0.5). Встроенное средство обновления проверяет последний релиз этого репозитория.

> **macOS (Apple Silicon):** сборка **неподписанная** (нет платной программы Apple Developer Program), поэтому Gatekeeper
> предупреждает при первом запуске. Приложение подписано ad-hoc — откройте его один раз через **правый клик → Открыть** или выполните
> `xattr -dr com.apple.quarantine "/Applications/LamaVibe.app"`.

## Сборка из исходного кода

Требуются Git, Node.js **24.14.0** и pnpm **10.33.2** (см. `mise.toml`).

```bash
pnpm bootstrap
# run the LamaVibe flavor in dev
pnpm dev:desktop:lama
# package (LamaVibe flavor)
ZCODE_LAMA_IDENTITY=1 pnpm bundle:desktop -- --os linux --arch x64
```

## Использование локальных моделей

LamaVibe обращается к вашему локальному серверу [Ollama](https://ollama.com) по адресу `http://localhost:11434/v1`. Встроенному провайдеру **Ollama (Local)** **не нужен API-ключ**.

1. Убедитесь, что Ollama запущен и у вас есть хотя бы одна чат-модель, например `ollama pull qwen2.5-coder:7b`.
2. Откройте **Settings → Model providers → Ollama (Local) → Add model**.
3. Нажмите **Load models**, чтобы увидеть список моделей, установленных на вашем компьютере, и выберите одну (или введите ID модели).
4. Оставьте формат API как **OpenAI-compatible (chat completions)**.

**Вызовы инструментов:** В разделе *Advanced → Capabilities* вы найдёте переключатель **Tool calls**. Для локальных провайдеров он **по умолчанию выключен**, поскольку большинство локальных моделей либо не поддерживают вызов функций, либо реализуют его иначе. Включайте его только если ваша модель действительно поддерживает вызовы инструментов Ollama — иначе Ollama отклонит запрос с HTTP 400 `does not support tools`. Для обычного чата оставьте его выключенным.

**Модели эмбеддингов**, такие как `nomic-embed-*`, предназначены для памяти и семантического поиска (эмбеддингов), а не для чата — для беседы выбирайте чат-модель.

## Лицензия и указание авторства

Создано на основе ZCode (Apache-2.0); лицензия и NOTICE сохранены. LamaVibe — независимый проект, не связанный с ZCode/Z.ai или Ollama. Ollama является товарным знаком своего владельца; логотип используется с разрешения оператора.
