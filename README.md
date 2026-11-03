# Ghost Exile на русском · macOS

<p align="center">
  <img src="assets/header.jpg" alt="Ghost Exile" width="100%">
</p>

<p align="center">
  Включает и удерживает русский язык в <b>Ghost Exile</b>, запущенной через Steam в <b>CrossOver</b> или <b>GameHub</b> на macOS.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/macOS-CrossOver-black?style=for-the-badge&logo=apple" alt="macOS CrossOver">
  <img src="https://img.shields.io/badge/macOS-GameHub-6c5ce7?style=for-the-badge&logo=apple" alt="macOS GameHub">
  <img src="https://img.shields.io/badge/Steam-Ghost%20Exile-1b2838?style=for-the-badge&logo=steam" alt="Steam Ghost Exile">
  <img src="https://img.shields.io/badge/Language-Russian-1f6feb?style=for-the-badge" alt="Russian language">
</p>

**[Скачать Ghost Exile RU для macOS v1.2.0](https://github.com/TechnologyUniverse/ghost-exile-ru-macos/releases/download/v1.2.0/ghost-exile-ru-macos-v1.2.0.tar.gz)** · [Описание релиза](https://github.com/TechnologyUniverse/ghost-exile-ru-macos/releases/tag/v1.2.0)

> В игровом прогоне подтверждены русский интерфейс и русские реплики. Ритуал изгнания успешно завершён.

[Установка](#установка) · [GameHub](#gamehub) · [CrossOver](#crossover) · [Проверка в игре](#проверка-в-игре) · [История версий](#история-версий) · [Авторские права](#авторские-права)

## Совместимость

Оба скрипта рассчитаны на Steam-версию Ghost Exile для Windows (AppID `1807080`), запущенную на macOS.

| Лаунчер | Скрипт | Где ищет игру |
| --- | --- | --- |
| GameHub | [ghost_exile_ru_gamehub.sh](ghost_exile_ru_gamehub.sh) | Автоматически ищет контейнер с установленной игрой |
| CrossOver | [ghost_exile_ru_crossover.sh](ghost_exile_ru_crossover.sh) | По умолчанию использует бутылку `Steam` |

В Ghost Exile 2.x скрипты переключают язык интерфейса и распознавания речи на русский. Это позволяет игре использовать штатные русские реплики при изгнании. Скрипты также обновляют настройки языка Steam и создают недостающие папки с русскими материалами для записок и доски Уиджи.

## Установка

1. Скачай архив релиза и распакуй его. Оба скрипта и два общих файла настроек должны лежать в одной папке.
2. Запусти Ghost Exile 2.x один раз, чтобы игра создала файл настроек, затем закрой её.
3. Открой Терминал в распакованной папке и выполни команды для своего лаунчера.

Если пользуешься Git, можно получить ту же версию командой:

```bash
git clone --branch v1.2.0 https://github.com/TechnologyUniverse/ghost-exile-ru-macos.git
cd ghost-exile-ru-macos
```

## GameHub

Сначала можно безопасно посмотреть предполагаемые изменения:

```bash
./ghost_exile_ru_gamehub.sh --dry-run
```

Применить исправление, закрыть Steam и снова открыть GameHub:

```bash
./ghost_exile_ru_gamehub.sh --kill-steam --start-gamehub
```

Контейнер с установленной Ghost Exile определяется автоматически. Если найдено несколько контейнеров, укажи нужный вручную:

```bash
./ghost_exile_ru_gamehub.sh --container "/путь/к/virtual_container" --kill-steam
```

### Параметры GameHub

| Параметр | Назначение |
| --- | --- |
| `--dry-run` | Показать изменения без записи |
| `--kill-steam` | Закрыть Steam перед изменениями |
| `--start-gamehub` | Открыть GameHub после завершения |
| `--container PATH` | Указать Wine-контейнер вручную |
| `--help` | Показать справку |

## CrossOver

Проверить изменения без записи:

```bash
./ghost_exile_ru_crossover.sh --dry-run --kill-steam
```

Применить исправление и перезапустить Steam:

```bash
./ghost_exile_ru_crossover.sh --kill-steam --start-steam
```

### Параметры CrossOver

| Параметр | Назначение |
| --- | --- |
| `--dry-run` | Показать изменения без записи |
| `--kill-steam` | Закрыть Steam/CrossOver bottle |
| `--start-steam` | Запустить Steam после завершения |
| `--bottle PATH` | Указать нестандартный bottle |
| `--help` | Показать справку |

## Проверка в игре

1. Запусти Ghost Exile через свой лаунчер.
2. Проверь главное меню, меню контракта и вкладки настроек.
3. Начни контракт, выбери ритуал изгнания и проверь русскую реплику на экране. Произнеси её в микрофон, чтобы проверить распознавание.

Если скрипт сообщает о неизвестном формате `ge_settings.gs`, выбери русский язык интерфейса и распознавания речи в игре и примени настройки.

## История версий

Версии относятся к скриптам. **v1.2.0** — первый опубликованный релиз на GitHub. Версии **1.0** и **1.1** обозначают предыдущие этапы проекта.

| Версия скриптов | Дата | Изменения |
| --- | --- | --- |
| [**1.2.0**](https://github.com/TechnologyUniverse/ghost-exile-ru-macos/releases/tag/v1.2.0) | 3 ноября 2026 | Поддержка настроек Ghost Exile 2.x в обоих лаунчерах. Русский язык интерфейса и распознавания речи через `ge_settings.gs`, резервная копия перед записью и проверка формата файла. [PR №2](https://github.com/TechnologyUniverse/ghost-exile-ru-macos/pull/2) |
| **1.1** | 7 июля 2026 | Поддержка GameHub с автоматическим поиском контейнера и ручным выбором через `--container`. [PR №1](https://github.com/TechnologyUniverse/ghost-exile-ru-macos/pull/1) |
| **1.0** | 18 апреля 2026 | Первый скрипт для CrossOver. Настройка языка Steam и игры, резервные копии и пробный запуск. [Первый коммит](https://github.com/TechnologyUniverse/ghost-exile-ru-macos/commit/bf77d64) |

Оба скрипта проверены на macOS во временных контейнерах с копиями настроек Steam-сборки `26403410`. В отдельном игровом прогоне подтверждены русские меню и реплики, ритуал изгнания завершён. Лаунчер и номер сборки для игрового прогона не указаны.

## Какие файлы затрагиваются

- `steamapps/appmanifest_1807080.acf`;
- `userdata/*/config/localconfig.vdf`;
- `drive_c/users/*/AppData/LocalLow/LostOneTeam/GhostExile/ge_settings.gs`;
- `user.reg` внутри CrossOver bottle или GameHub container для старых сборок;
- `GhostExile_Data/StreamingAssets/LoreNote/*`;
- `GhostExile_Data/StreamingAssets/Ouija/*`.

Перед изменением файлов создаются копии с именем вида `.bak.YYYYMMDD-HHMMSS`.

## Скриншоты

<p align="center">
  <img src="assets/screenshot-1.jpg" alt="Ghost Exile Screenshot 1" width="49%">
  <img src="assets/screenshot-2.jpg" alt="Ghost Exile Screenshot 2" width="49%">
</p>

<p align="center">
  <img src="assets/screenshot-3.jpg" alt="Ghost Exile Screenshot 3" width="49%">
  <img src="assets/screenshot-4.jpg" alt="Ghost Exile Screenshot 4" width="49%">
</p>

## Авторские права

**© 2026 Technology Universe. Все права на оригинальный код скриптов сохранены.**

Скрипты можно скачивать и запускать для личного использования по инструкции. Для перепубликации, распространения изменённых версий и включения кода в сторонние проекты требуется предварительное письменное разрешение правообладателя, за исключением случаев, предусмотренных законом или условиями GitHub. При упоминании проекта указывайте Technology Universe и ссылку на оригинальный репозиторий.

### Материалы игры

Скриншоты взяты из официальных материалов Ghost Exile в Steam и используются только для оформления README. Проект не связан с разработчиками Ghost Exile, Valve, CodeWeavers или GameHub.
