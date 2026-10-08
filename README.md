<p align="center">
  <img src="./assets/readme/hero.svg" width="100%" alt="Russian Whisper Turbo v2.0: локальная модель русской coding-диктовки с базой Whisper Large V3 Turbo. Студийный тест: WER 14.04%, термины 73.39%. Podlodka: WER 9.71%.">
</p>

<p align="center">
  <a href="https://github.com/kalpakprod/russian-whisper-turbo/releases/download/v2.0.0/handy-whisper-large-v3-turbo-ru-coding-agent-q8_0.bin"><strong>Скачать модель v2.0.0</strong></a> ·
  <a href="./release-v2/INSTALL.md">Установка</a> ·
  <a href="./evaluation.json">Метрики</a> ·
  <a href="https://github.com/kalpakprod/russian-whisper-turbo/releases/tag/v1.0.0">Legacy v1.0.0</a>
</p>

## Модель

- Дообученная `openai/whisper-large-v3-turbo` для русских диктовок coding-агентам: названия инструментов, команды, пути и идентификаторы.
- Формат: `whisper.cpp` GGML, квантование `Q8_0`, размер **833,69 MiB** (874 188 075 байт). Работает локально, без Python и отдельного LoRA-адаптера.
- Дообучение: decoder LoRA rank32, замороженный encoder, 3 эпохи; студийная речь одного диктора и публичная человеческая разметка.

## Качество распознавания

WER: доля ошибок в словах, меньше лучше. Ниже **фиксированные выборки, а не полные публичные тесты**.

| Набор | Записей | WER v2.0 |
|---|---:|---:|
| Coding-фразы, студия | 106 | 14,04% |
| Технический подкаст Podlodka | 20 | 9,71% |
| FLEURS, русский | 192 | 6,60% |
| FLEURS, английский | 164 | 6,27% |
| Common Voice, русский | 200 | 7,01% |
| RuLibriSpeech test | 200 | 12,11% |

- Точность латинских терминов на студийном тесте: **73,39%**.
- На выборке RuLibriSpeech Legacy R48 точнее: **9,83%** против **12,11%**; разница +2,29 п.п., 95% интервал [+1,20; +3,39]. Эта версия ориентирована на coding-диктовку.
- Студийный тест записан тем же диктором, что обучение; Podlodka содержит знакомых ведущих из других выпусков. Протокол и числа: [оценка модели](./evaluation.json), [новый книжный тест](./release-v2/BENCHMARKS-2026-10-08.md).

## Производительность

- RuLibriSpeech: **11,3×** реального времени: 1401,3 секунды аудио обработаны за **123,6 секунды**.
- Замер выполнен на **AMD BC-250**, `whisper.cpp` Vulkan, 12 CPU-потоков, Q8_0. Скорость на другом устройстве может отличаться.

## Загрузка и проверка

- [Скачать `.bin`](https://github.com/kalpakprod/russian-whisper-turbo/releases/download/v2.0.0/handy-whisper-large-v3-turbo-ru-coding-agent-q8_0.bin) и подключить к `whisper.cpp` либо совместимому приложению. [Пошаговая установка](./release-v2/INSTALL.md).
- SHA-256:

  ```text
  eb05b341f8d47a16e554464175529951ba5b94937d6afc8d63e26041ea326ce5
  ```

## Данные и условия

- [Рецепт обучения](./release-v2/TRAINING.md) и [карточка модели](./release-v2/MODEL-CARD.md). Личные аудио и расшифровки не публикуются.
- Базовая модель: [MIT](https://huggingface.co/openai/whisper-large-v3-turbo/blob/main/README.md); условия обучающих данных рассматриваются отдельно. Единой новой лицензии для дообученных весов не заявлено.
- [Legacy v1.0.0](./legacy/v1/README.md): прежняя модель на базе coriollon; её файл и результаты сохранены отдельно.
