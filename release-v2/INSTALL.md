# Установка Russian Whisper Turbo v2.0.0

## Файл модели

- Скачать: [модель Q8_0](https://github.com/kalpakprod/russian-whisper-turbo/releases/download/v2.0.0/handy-whisper-large-v3-turbo-ru-coding-agent-q8_0.bin).
- Сохрани под именем `handy-whisper-large-v3-turbo-v6-q8_0.bin`, чтобы не перезаписать прежнюю Legacy-модель.
- Размер: 874 188 075 байт. SHA-256:

  ```text
  eb05b341f8d47a16e554464175529951ba5b94937d6afc8d63e26041ea326ce5
  ```

## Linux

```bash
curl -L -o handy-whisper-large-v3-turbo-v6-q8_0.bin \
  "https://github.com/kalpakprod/russian-whisper-turbo/releases/download/v2.0.0/handy-whisper-large-v3-turbo-ru-coding-agent-q8_0.bin"
sha256sum handy-whisper-large-v3-turbo-v6-q8_0.bin
```

- Сравни хеш с указанным выше, затем подключи файл к `whisper.cpp` или совместимому приложению.

## Handy, Windows

```powershell
$modelDir = Join-Path $env:APPDATA "com.pais.handy\models"
$modelPath = Join-Path $modelDir "handy-whisper-large-v3-turbo-v6-q8_0.bin"
$url = "https://github.com/kalpakprod/russian-whisper-turbo/releases/download/v2.0.0/handy-whisper-large-v3-turbo-ru-coding-agent-q8_0.bin"
New-Item -ItemType Directory -Force -Path $modelDir | Out-Null
Invoke-WebRequest -Uri $url -OutFile $modelPath
(Get-FileHash -Algorithm SHA256 $modelPath).Hash
```

- После проверки хеша перезапусти Handy и выбери модель по имени нового файла.
- Файл загружался сервером OpenWhispr Vulkan; полный тест диктовки через интерфейс Handy для этой версии не выполнялся.
- Настройки приложения автоматически не меняются. [Прежняя модель](https://github.com/kalpakprod/russian-whisper-turbo/releases/tag/v1.0.0) остаётся доступной для отката.
