# Changelog — zmey93/zapret-discord-youtube

Все изменения этого форка относительно оригинала [Flowseal/zapret-discord-youtube](https://github.com/Flowseal/zapret-discord-youtube) задокументированы здесь.

Формат основан на [Keep a Changelog](https://keepachangelog.com/ru/1.0.0/).

---

## [Unreleased] — Fork Customization

### 2026-03-12

#### Changed — `service.bat`

- **[UPDATE URLs]** Все URL обновлений переориентированы с оригинального репозитория на форк `zmey93/zapret-discord-youtube`:
  - `GITHUB_VERSION_URL` → `https://raw.githubusercontent.com/zmey93/zapret-discord-youtube/main/.service/version.txt`
  - `GITHUB_RELEASE_URL` → `https://github.com/zmey93/zapret-discord-youtube/releases/tag/`
  - `GITHUB_DOWNLOAD_URL` → `https://github.com/zmey93/zapret-discord-youtube/releases/latest`
  - **IPSet update URL** (`ipset_update`) → `https://raw.githubusercontent.com/zmey93/zapret-discord-youtube/refs/heads/main/.service/ipset-service.txt`
  - **Hosts update URL** (`hosts_update`) → `https://raw.githubusercontent.com/zmey93/zapret-discord-youtube/refs/heads/main/.service/hosts`

> Это означает, что пункты меню **9 (Check for Updates)**, **7 (Update IPSet List)** и **8 (Update Hosts File)** теперь обращаются к форку, а не к оригинальному репозиторию.

#### Changed — `utils/targets.txt`

- **[TEST TARGETS]** Добавлены дополнительные домены для тестирования из `lists/list-general.txt`:

  | Группа | Добавленные таргеты |
  |--------|--------------------|
  | Discord | `discordapp.com`, `discordstatus.com` |
  | Cloudflare | `cloudflare-ech.com`, `cloudflarestream.com`, `cloudflarestatus.com` |
  | Steam | `steampowered.com`, `steamcommunity.com`, `steamcontent.com`, `steamstatic.com` |
  | Twitch/Stream | `betterttv.net`, `7tv.app` |
  | Games | `escapefromtarkov.com`, `battleye.com` |
  | Tools | `anydesk.com`, `speedtest.net`, `dnsleaktest.com`, `browserleaks.com` |

> Тест (`service.bat` → `Run Tests` → `Standard tests`) теперь охватывает значительно больше сервисов и позволяет точнее оценить качество стратегии обхода.

#### Added — `CHANGELOG.md`

- Создан этот файл для отслеживания всех изменений форка.

---

## Примечания

- Бинарные файлы в `bin/` и логика стратегий (`general*.bat`) не изменялись — они идентичны оригиналу.
- Форк предназначен для личного использования (`> [!CAUTION] Форк для личного использования`).
- Синхронизацию с upstream (`Flowseal/zapret-discord-youtube`) рекомендуется делать вручную через `git merge upstream/main` или PR.
