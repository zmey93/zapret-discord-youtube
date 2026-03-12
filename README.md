> [!CAUTION]
> **Это личный форк репозитория [Flowseal/zapret-discord-youtube](https://github.com/Flowseal/zapret-discord-youtube), настроенный под себя.**  
> Обновления, тесты и релизы берутся из этого репозитория, а не из оригинала.

<div align="center">

# 🛡️ zapret-discord-youtube
### Обход блокировок Discord, YouTube и других сервисов на Windows

**Форк:** [zmey93/zapret-discord-youtube](https://github.com/zmey93/zapret-discord-youtube)  
**Оригинал:** [Flowseal/zapret-discord-youtube](https://github.com/Flowseal/zapret-discord-youtube)  
**Ядро:** [bol-van/zapret](https://github.com/bol-van/zapret)

</div>

---

## 📥 Установка

### Шаг 1 — Скачать

Скачайте самораспаковывающийся архив (`.exe`) со страницы последнего релиза:

👉 **[Скачать последний релиз](https://github.com/zmey93/zapret-discord-youtube/releases/latest)**

> [!WARNING]
> **Антивирусы** могут реагировать на файлы WinDivert — это нормально. WinDivert не является вирусом, это драйвер для перехвата трафика с цифровой подписью. Добавьте папку в исключения антивируса.

### Шаг 2 — Распаковать

1. Запустите скачанный `.exe` от имени администратора
2. Укажите путь распаковки: `C:\DPI\` (архив сам создаст подпапку с версией, например `C:\DPI\1.9.7b-z1`)
3. Дождитесь завершения распаковки

> [!IMPORTANT]
> Путь **не должен** содержать кириллицу, пробелы или спецсимволы. Рекомендуется использовать корень диска: `C:\DPI\`

### Шаг 3 — Запустить service.bat

Перейдите в папку с распакованными файлами, например `C:\DPI\1.9.7b-z1\`, и запустите **`service.bat` от имени администратора**.

---

## 🚀 Быстрый старт (первая установка)

```
service.bat → 11. Run Tests
  → 1. Standard tests (HTTP/ping)
  → 1. All configs
  → дождаться результатов → запомнить лучшую стратегию

service.bat → 1. Install Service
  → выбрать лучшую стратегию из результатов теста
```

После установки обход запустится автоматически и будет стартовать вместе с Windows.

---

## 🔄 Обновление

> [!IMPORTANT]
> При обновлении **сначала** удалите старую службу, и только потом устанавливайте новую.

```
1. service.bat → 2. Remove Services       ← удалить старую службу
2. Распаковать новый архив в C:\DPI\новая_версия\
3. service.bat → 11. Run Tests            ← запустить тесты
      → 1. Standard tests (HTTP/ping)
      → 1. All configs
      → дождаться результатов
4. service.bat → 1. Install Service       ← установить лучшую стратегию
```

---

## ⚙️ Функции service.bat

| Пункт | Действие |
|-------|----------|
| **1. Install Service** | Установить выбранную стратегию в автозапуск Windows |
| **2. Remove Services** | Удалить службу zapret и WinDivert из системы |
| **3. Check Status** | Проверить, запущен ли обход и какая стратегия установлена |
| **4. Game Filter** | Вкл/Выкл фильтрацию UDP/TCP портов для игр (1024–65535) |
| **5. IPSet Filter** | Переключить режим фильтрации по IP-спискам (`none` / `loaded` / `any`) |
| **6. Auto-Update Check** | Вкл/Выкл автопроверку новых версий при запуске |
| **7. Update IPSet List** | Обновить список IP-адресов `ipset-all.txt` из репозитория |
| **8. Update Hosts File** | Обновить `hosts` — нужно для веб-версии Telegram и голосового чата Discord |
| **9. Check for Updates** | Проверить наличие новой версии |
| **10. Run Diagnostics** | Диагностика конфликтов (Adguard, VPN, Killer и др.) + очистка кэша Discord |
| **11. Run Tests** | Тестирование стратегий — см. ниже |

### Про Run Tests

- **Standard tests (HTTP/ping)** — проверяет доступность Discord, YouTube, Steam, Cloudflare и других сервисов через HTTP/TLS и ping для каждой стратегии. В конце показывает лучшую конфигурацию.
- **DPI checkers** — проверяет блокировку по паттерну TCP 16–20 KB на различных провайдерах.

### Про IPSet Filter

- `none` — ни один IP не фильтруется
- `loaded` — фильтруются только IP из `ipset-all.txt`
- `any` — фильтруется любой IP

> При тестировании рекомендуется переключить IPSet в `any`, чтобы обход применялся ко всем адресам.

---

## 🗒️ Добавление своих доменов

Добавьте нужные домены или IP в следующие файлы в папке `lists\`:

- **`list-general-user.txt`** — домены для обхода (поддомены учитываются автоматически)
- **`list-exclude-user.txt`** — домены для исключения из обхода
- **`ipset-all.txt`** — IP-адреса и подсети для фильтрации
- **`ipset-exclude-user.txt`** — IP-адреса и подсети для исключения

> Файлы `*-user.txt` создаются автоматически при первом запуске.

---

## ❓ Частые проблемы

### Не работает Discord
1. Запустите `Run Diagnostics` — проверьте конфликты
2. Попробуйте другие стратегии (`ALT`, `FAKE` и их варианты)
3. Обновите `hosts`: `service.bat` → `8. Update Hosts File`
4. Убедитесь, что настроен Secure DNS в браузере

### Не работает YouTube
1. Убедитесь, что настроен Secure DNS
2. Отключите блокировщик рекламы
3. Попробуйте другие стратегии

### Не работает веб-версия Telegram / голосовой чат Discord
```
service.bat → 8. Update Hosts File
```
Если hosts устарел — будет предложено обновить его вручную. Откройте файл `hosts` (`C:\Windows\System32\drivers\etc\hosts`) от имени администратора и добавьте содержимое из открывшегося блокнота в конец файла.

### Античит ругается на WinDivert
См. инструкцию: https://github.com/bol-van/zapret-win-bundle/tree/master/windivert-hide

### После запуска general*.bat ничего не происходит
Должно открыться окно `winws.exe` в панели задач. Если нет — запустите `Run Diagnostics`.

### WinDivert остаётся в службах после удаления
```cmd
driverquery | find "Divert"
sc stop НАЗВАНИЕ
sc delete НАЗВАНИЕ
```

---

## ⚖️ Лицензия

Проект распространяется на условиях лицензии [MIT](./LICENSE.txt).  
Бинарные файлы в папке `bin/` взяты из [bol-van/zapret-win-bundle](https://github.com/bol-van/zapret-win-bundle/tree/master/zapret-winws).
