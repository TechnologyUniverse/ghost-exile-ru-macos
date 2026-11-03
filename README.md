# Ghost Exile Russian Fix for macOS

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

## Зачем нужен фикс

В Wine-контейнерах язык Ghost Exile может расходиться сразу в нескольких местах: Steam хранит `english`, игра использует собственное значение в реестре, а часть локализации ищет файлы в папках с неправильными кодами языка.

В результате в настройках может быть выбран `Russian`, но интерфейс или отдельные игровые материалы останутся на английском. Скрипты исправляют всю цепочку:

- устанавливают `russian` в Steam-манифесте игры;
- обновляют пользовательскую настройку Steam в `localconfig.vdf`;
- в Ghost Exile 2.x выставляют русский язык интерфейса и распознавания речи в `ge_settings.gs`;
- используют прежнюю настройку Wine-реестра для старых сборок;
- создают недостающие fallback-папки из русской локализации;
- сохраняют резервные копии изменяемых файлов.

## Выбери свою платформу

| Платформа | Скрипт | Автопоиск контейнера |
| --- | --- | :---: |
| CrossOver | `ghost_exile_ru_crossover.sh` | Bottle `Steam` |
| GameHub | `ghost_exile_ru_gamehub.sh` | ✅ |

Оба скрипта рассчитаны на macOS и Steam-версию Ghost Exile с AppID `1807080`.

## Установка

```bash
git clone https://github.com/TechnologyUniverse/ghost-exile-ru-macos.git
cd ghost-exile-ru-macos
chmod +x ghost_exile_ru_crossover.sh ghost_exile_ru_gamehub.sh
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

## После запуска

Для Ghost Exile 2.x сначала запусти игру один раз, чтобы она создала файл настроек. Закрой игру и Steam перед применением исправления. После запуска игры проверь язык главного меню, меню контракта и вкладок настроек. На контракте выбери ритуал изгнания, проверь текст на экране и произнеси русскую реплику, чтобы проверить распознавание.

Игра использует отдельную настройку языка распознавания речи для выбора реплик ритуала. Скрипты переключают обе настройки на русский и используют штатные переводы из игры. Если скрипт сообщает о неизвестном формате файла, выбери оба языка вручную и примени настройки в игре.

Скрипты не работают в фоне. Обычно достаточно одного запуска; повторный запуск безопасен и пропустит уже выполненные изменения.

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

## Примечание

Скриншоты взяты из официальных материалов Ghost Exile в Steam и используются только для оформления README. Проект не связан с разработчиками Ghost Exile, Valve, CodeWeavers или GameHub.
