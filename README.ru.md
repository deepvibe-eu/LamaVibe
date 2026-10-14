> Machine-translated from [README.md](README.md) into Русский — corrections welcome.

# LamaVibe

<div align="center">
  <img src="packages/desktop/build/README-images/LamaVibe_ru.png" alt="Скриншот LamaVibe" width="auto" />
</div>

<p align="center">
  <a href="https://deepvibe.eu/lamavibe">lamavibe.eu</a>
</p>

LamaVibe — это **сборка для Ollama** из семейства _Vibe_ — форк ZCode, ориентированный на одного провайдера: **Ollama** (локальные модели). Одна модель, одно рабочее пространство, партнёр — не агент.

Семейство _Vibe_ выпускает по одному специализированному приложению на каждого провайдера (DeepVibe для DeepSeek, KimiVibe для Kimi, LamaVibe для Ollama, MiniVibe для MiniMax, KlausVibe для Claude, …), каждое со своим характером. Оно существует **наряду** с ZCode, а не вместо него: ZCode — для работы с несколькими провайдерами, приложения Vibe — для тех, кому нужна одна модель, одно рабочее пространство, один партнёр. Полный исходный код смотрите в основном репозитории.

## Загрузки

Установщики для macOS, Windows и Linux доступны на [странице релизов](../../releases); самый свежий релиз всегда помечен тегом **latest**:

| Платформа | Файлы |
| --- | --- |
| macOS (Apple Silicon) | `LamaVibe-<version>-mac-arm64.dmg` · `LamaVibe-<version>-mac-arm64.zip` |
| Windows | `LamaVibe-<version>-win-x64.exe` |
| Linux | `LamaVibe-<version>-linux-x86_64.AppImage` · `LamaVibe-<version>-linux-amd64.deb` · `LamaVibe-<version>-linux-x86_64.rpm` · `LamaVibe-<version>-linux-x64.pkg.tar.zst` |

Все приложения семейства *Vibe* выпускаются с **одинаковым номером версии** (сейчас 1.0.3). Встроенное средство обновления проверяет последний релиз этого репозитория.

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

LamaVibe взаимодействует с вашим локальным сервером [Ollama](https://ollama.com) по адресу `http://localhost:11434/v1`. Встроенному провайдеру **Ollama (Local)** **не требуется API-ключ**.

1. Убедитесь, что Ollama запущена и у вас есть хотя бы одна чат-модель, например `ollama pull qwen2.5-coder:7b`.
2. Откройте **Настройки → Провайдеры моделей → Ollama (Local) → Добавить модель**.
3. Нажмите **Загрузить модели**, чтобы увидеть список установленных на вашем компьютере моделей, и выберите одну (или введите ID модели).
4. Оставьте формат API как **OpenAI-совместимый (chat completions)**.

**Вызовы инструментов:** В разделе *Дополнительно → Возможности* вы найдёте переключатель **Вызовы инструментов**. Он **по умолчанию выключен для локальных провайдеров**, поскольку большинство локальных моделей либо не поддерживают вызов функций, либо реализуют его иначе. Включайте его только если ваша модель действительно поддерживает вызовы инструментов Ollama — иначе Ollama отклонит запрос с HTTP 400 `does not support tools`. Для обычного чата оставьте его выключенным.

**Модели эмбеддингов**, такие как `nomic-embed-*`, предназначены для памяти и семантического поиска (эмбеддингов), а не для чата — для беседы выбирайте чат-модель.

## Лицензия и атрибуция

Создано на основе ZCode (Apache-2.0); лицензия и NOTICE сохранены. LamaVibe — независимый проект и не связан с ZCode/Z.ai или Ollama. Ollama является товарным знаком своего владельца; логотип используется с разрешения оператора.
