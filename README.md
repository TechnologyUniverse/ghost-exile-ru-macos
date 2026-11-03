# Ghost Exile на русском на Mac

![Ghost Exile](assets/ghost-exile.png)

Этот проект помогает включить русский язык в Steam-версии Ghost Exile 2.x на macOS. Скрипты работают с **GameHub** и **CrossOver** и переключают язык меню, настроек и реплик ритуала изгнания.

## Как установить

1. [Скачай архив v1.2.0](https://github.com/TechnologyUniverse/ghost-exile-ru-macos/releases/download/v1.2.0/ghost-exile-ru-macos-v1.2.0.tar.gz) и распакуй его. Оставь все файлы из архива в одной папке.
2. Запусти Ghost Exile через свой лаунчер хотя бы один раз, чтобы игра создала настройки. Затем закрой игру.
3. Открой Терминал. Напечатай `cd`, поставь пробел, перетащи распакованную папку в окно Терминала и нажми Enter.
4. Выполни команду для своего лаунчера.

### GameHub

```bash
bash ghost_exile_ru_gamehub.sh --kill-steam --start-gamehub
```

### CrossOver

```bash
bash ghost_exile_ru_crossover.sh --kill-steam --start-steam
```

Скрипт закроет Steam, если он запущен, и сохранит резервные копии изменяемых настроек. Когда появится сообщение «Готово», запусти Ghost Exile и проверь меню и реплики ритуала. Те же шаги есть в файле `ИНСТРУКЦИЯ.txt` внутри архива.

Если хочешь сначала посмотреть, что изменится, запусти свой скрипт с параметром `--dry-run` вместо параметров из примера. Если скрипт сообщает о неизвестном формате настроек, выбери русский язык интерфейса и распознавания речи в самой игре.

## История версий

- **[1.2.0](https://github.com/TechnologyUniverse/ghost-exile-ru-macos/releases/tag/v1.2.0)** — поддержка Ghost Exile 2.x. В игровом прогоне меню и реплики были на русском, ритуал изгнания завершён.
- **1.1** — добавлена поддержка GameHub.
- **1.0** — первый скрипт для CrossOver.

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

Скрипты можно скачивать и запускать для личного использования. Для перепубликации, распространения изменённых версий и включения кода в сторонние проекты требуется предварительное письменное разрешение правообладателя, за исключением случаев, предусмотренных законом или условиями GitHub. При упоминании проекта указывай Technology Universe и ссылку на оригинальный репозиторий.

Права на Ghost Exile и изображения игры принадлежат их правообладателям.
