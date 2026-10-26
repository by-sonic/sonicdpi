<!-- SUPPORT-START -->
<p align="center">
  <b>💛 Поддержать проект</b> · <b>USDT</b> (Tether) в сети <b>TRC20</b>:<br/>
  <code>TEHHyPSeZ7t5vfVJmjtEBkqJdpfcrm1wqg</code>
</p>
<!-- SUPPORT-END -->

<!-- ROSEVPN-BANNER-START -->
<p align="center">
  <a href="https://t.me/rosevpnru_bot">
    <img alt="RoseVPN — быстрый VPN" src="https://img.shields.io/badge/%F0%9F%8C%B9%20RoseVPN-%D0%9F%D0%BE%D0%B4%D0%BA%D0%BB%D1%8E%D1%87%D0%B8%D1%82%D1%8C%D1%81%D1%8F%20%D0%B2%20Telegram-E63946?style=for-the-badge&logo=telegram&logoColor=white&labelColor=1a1a1a" height="40"/>
  </a>
</p>
<p align="center">
  <sub><b>Быстрый VPN с обходом YouTube, Discord, Instagram</b> · Бесплатный пробный период · Подключение за 30 секунд через бот <a href="https://t.me/rosevpnru_bot">@rosevpnru_bot</a></sub>
</p>

---

<!-- ROSEVPN-BANNER-END -->

# SonicDPI — обход блокировок YouTube и Discord (Windows / Linux / macOS)

[![CI](https://github.com/by-sonic/sonicdpi/actions/workflows/ci.yml/badge.svg)](https://github.com/by-sonic/sonicdpi/actions/workflows/ci.yml)
[![Release](https://github.com/by-sonic/sonicdpi/actions/workflows/release.yml/badge.svg)](https://github.com/by-sonic/sonicdpi/actions/workflows/release.yml)
[![License: MIT OR Apache-2.0](https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-blue.svg)](#лицензия)
[![Rust](https://img.shields.io/badge/rust-stable-orange.svg)](https://www.rust-lang.org/)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey)](#поддерживаемые-платформы)

> [!CAUTION]
> ## 🔴 Помоги проекту — пришли результаты sweep со своего провайдера
>
> Рабочий профиль зависит от того, **какой DPI стоит у вашего ISP**. Один-единственный конфиг, который пробивает у меня в Москве, может не пробивать в Перми. Мне нужны полевые данные с разных провайдеров и регионов, чтобы добавить новые `youtube-discord-*` профили в дефолтную поставку.
>
> **Что сделать (3 минуты):**
>
> 1. Скачайте [последний релиз](https://github.com/by-sonic/sonicdpi/releases/latest), распакуйте.
> 2. **Windows** (admin PowerShell): `Start-Process powershell -Verb RunAs -ArgumentList '-NoExit','-ExecutionPolicy','Bypass','-File','.\sweep.ps1','-Quick'`
>    **Linux/macOS**: `sudo ./sweep.sh --quick` *(в работе, см. issue #4)*
> 3. Дождитесь завершения (~3-10 минут, прогон 30 конфигов).
> 4. **Откройте новый issue** через [готовый шаблон Field report](https://github.com/by-sonic/sonicdpi/issues/new?template=field-report.yml) и приложите:
>    - **Провайдер и регион** (например: «Ростелеком, Москва» или «ER-Telecom, Пермь»)
>    - **Полный stdout sweep-а** (от `=== ENV ===` до `=== DONE ===`)
>    - Сторонне: какой `winws.exe` / `zapret` / `goodbyedpi`-конфиг у вас работает сейчас (если есть)
>
> Чем больше отчётов, тем быстрее у `sonicdpi run` появится опция «попробовать всё подряд» с кешем рабочих рецептов по ISP. Спасибо.

**Открытый кросс-платформенный обход DPI для YouTube и Discord (включая голосовые каналы).** Альтернатива zapret / GoodbyeDPI / byedpi на Rust — один движок, три ОС, готовые сборки. Снимает замедление YouTube, чинит «Checking for updates» и «Update failed» в Discord, возвращает голосовые каналы.

**VPN-сервис автора:** 🌹 [@rosevpnru_bot](https://t.me/rosevpnru_bot) — RoseVPN, быстрый VPN с обходом блокировок (VLESS + Reality + Xray + Hysteria 2). Используйте если SonicDPI на вашем провайдере не пробивает.

## ⬇ Скачать готовые сборки

Берите архив с последнего релиза на странице [**Releases**](https://github.com/by-sonic/sonicdpi/releases/latest) или сразу прямой ссылкой:

| Платформа | Архив |
|---|---|
| **Windows x64** (Win 10 / 11) | [SonicDPI-windows-x64.zip](https://github.com/by-sonic/sonicdpi/releases/latest/download/SonicDPI-windows-x64.zip) |
| **Linux x64** (Ubuntu / Debian / Arch / etc.) | [SonicDPI-linux-x64.tar.gz](https://github.com/by-sonic/sonicdpi/releases/latest/download/SonicDPI-linux-x64.tar.gz) |
| **Linux ARM64** (Raspberry Pi, роутеры, серверы Ampere) | [SonicDPI-linux-arm64.tar.gz](https://github.com/by-sonic/sonicdpi/releases/latest/download/SonicDPI-linux-arm64.tar.gz) |
| **macOS Apple Silicon** (M1/M2/M3/M4) | [SonicDPI-macos-arm64.tar.gz](https://github.com/by-sonic/sonicdpi/releases/latest/download/SonicDPI-macos-arm64.tar.gz) |
| **macOS Intel** | [SonicDPI-macos-x64.tar.gz](https://github.com/by-sonic/sonicdpi/releases/latest/download/SonicDPI-macos-x64.tar.gz) |
| Контрольные суммы | [SHA256SUMS.txt](https://github.com/by-sonic/sonicdpi/releases/latest/download/SHA256SUMS.txt) |

**Ключевые слова:** обход блокировок, обход ТСПУ, антиблок, замедление YouTube, ютуб не работает, дискорд не работает, проверка обновлений Discord, Discord checking for updates fix, обход Роскомнадзора, zapret аналог, GoodbyeDPI на Rust, byedpi альтернатива, WinDivert, NFQUEUE, ClientHello desync, TLS fragmentation, fake-multidisorder, hostfakesplit, обход блокировки YouTube Windows, обход блокировки Discord Mac.

---

## Зачем ещё один?

- **GoodbyeDPI** — только Windows.
- **zapret** — мощный, но это C с матрицей сборки, неудобной для не-Linux разработчиков, без официальной macOS-сборки.
- **byedpi** — userspace SOCKS-прокси, не умеет голос Discord (UDP/RTP).

**SonicDPI** — единый Rust-проект, один движок на три ОС, готовые подписанные релизы, поддержка голосового UDP, декларативные TOML-профили.

## Возможности

- **Кроссплатформенно:** Windows (WinDivert 2.2.2), Linux (NFQUEUE через чистый Rust, без GPL `libnetfilter_queue`), macOS (pf `rdr-to`).
- **Голос Discord:** перехват UDP к `*.discord.media` на портах 19294–19344 и 50000–50100, прайминг STUN-/Discord-фейками.
- **Профили в TOML:** declarative, можно роутировать ALT-вариантами когда провайдер пропатчил один.
- **Встраиваемость:** крейт `sonicdpi-engine` без OS-зависимостей — линкуется в GUI, Electron, кастомный прокси.
- **Анти-фингерпринт:** фейковые ClientHello / QUIC Initial / STUN генерируются с per-run рандомизацией — нельзя задетектить по статичному байтовому шаблону.

## Стратегии обхода

| Стратегия | Что делает |
|---|---|
| `tls-multisplit` | Дробит TLS ClientHello на сегменты с seqovl-перекрытием и подменой паттерна на безопасный SNI. |
| `fake-multidisorder` | Эмитит N фейковых ClientHello (с нужным fooling — TS / MD5SIG / badseq) до настоящего, классификатор DPI «коммитится» на фейк. |
| `hostfakesplit` | Переименовывает SNI в первом сегменте на безобидный (`www.google.com`, `ozon.ru`), сервер в итоге собирает оригинал. |
| `quic-fake-initial` | Прайм-бёрст фейковых QUIC Initial с SNI=google перед настоящим — обходит классификатор YouTube QUIC. |
| `discord-voice-prime` | UDP-фейки в STUN/Discord-форме перед настоящим RTP, чтобы DPI не успел навесить ярлык на голосовой поток. |

## Встроенные профили

| Имя | Когда использовать |
|---|---|
| `youtube-discord` | По умолчанию. Текущий рабочий рецепт на 2026-05: `fake-multidisorder + badseq + ozon.ru × 4`, QUIC-prime × 6, voice-prime × 6. |
| `youtube-discord-aggressive` | Если default не пробивает Discord-direct (Gateway). Добавляет `fake+multisplit` ALT11. |
| `youtube-discord-multidisorder` | Если default ловит mid-stream classifier. Out-of-order TLS-сегменты. |
| `youtube-discord-seqovl` | Совместимость со старым именем профиля. Сейчас алиас default. |
| `youtube-discord-hostfakesplit` | Когда DPI ловит SNI до пересборки. Переписывает SNI на `www.google.com` / `ozon.ru`. |

```bash
sonicdpi profiles                          # список
sonicdpi show youtube-discord -o my.toml   # дамп TOML для редактирования
sonicdpi run --profile my.toml -v          # запуск с кастомным TOML
```

## Быстрый старт

### Windows

Скачать архив `SonicDPI-windows-x64.zip` со страницы [Releases](https://github.com/by-sonic/sonicdpi/releases), распаковать, запустить `sonicdpi-tray.exe` — UAC → значок в трее → правый клик → «Включить».

Ручной запуск из админ-PowerShell:
```powershell
.\sonicdpi.exe run --profile youtube-discord -vv
```
Установить как службу (автозапуск при логине):
```powershell
.\sonicdpi.exe install --profile youtube-discord
```

### Linux

```bash
sudo apt install nftables
tar -xzf SonicDPI-linux-x64.tar.gz
sudo setcap cap_net_admin=eip ./sonicdpi
./sonicdpi run --profile youtube-discord -vv
```
Или через systemd:
```bash
sudo ./sonicdpi install --profile youtube-discord
sudo systemctl enable --now sonicdpi
journalctl -u sonicdpi -f
```

### macOS

```bash
tar -xzf SonicDPI-macos-arm64.tar.gz   # или -x64 на Intel
sudo ./sonicdpi run --profile youtube-discord -vv
```
> ⚠️ В v0.2 голос Discord на macOS не поддерживается (нужен NetworkExtension System Extension — это v0.3+). YouTube/TLS-Discord работают.

## Сборка из исходников

```bash
# stable rust toolchain
rustup default stable

# Linux: системные зависимости
sudo apt install libnetfilter-queue-dev nftables

cargo build --workspace --release
# готовые бинари в target/release/
```

Smoke-тесты движка (без сети):
```bash
cargo test --workspace --lib
```

Отладка:
```bash
sonicdpi run --profile youtube-discord -vv
# Лог:
#   Windows: %LOCALAPPDATA%\SonicDPI\sonicdpi.log
#   Linux:   journalctl -u sonicdpi
#   macOS:   /var/log/sonicdpi.log
```

## Архитектура

```
                           ┌──────────────────────────┐
                           │      sonicdpi-cli        │   sonicdpi.exe
                           │  (clap, profiles, svc)   │
                           └────────────┬─────────────┘
                                        │
                ┌───────────────────────┴──────────────────────┐
                │                                              │
   ┌────────────▼────────────┐                  ┌──────────────▼─────────────┐
   │   sonicdpi-platform     │                  │      sonicdpi-engine       │
   │ ┌────────────────────┐  │  Action ◄─────┐  │  Flow table                │
   │ │ Windows: WinDivert │  │               │  │  TLS / QUIC / RTP detect   │
   │ │ Linux:   NFQUEUE   │──┼──► Engine ────┘  │  Strategy pipeline         │
   │ │ macOS:   pf rdr-to │  │   (handle pkt)   │   • multisplit + seqovl    │
   │ └────────────────────┘  │                  │   • fake-multidisorder     │
   └─────────────────────────┘                  │   • hostfakesplit          │
                                                │   • quic-fake-initial      │
                                                │   • discord-voice-prime    │
                                                └────────────────────────────┘
```

## UI

Полноценного desktop-GUI **нет** — только `sonicdpi-tray.exe`, минимальный системный трей: правый клик → вкл/выкл, выбор профиля, открыть логи, ссылки на VPN-боты автора и GitHub. Для headless-сценария используйте CLI (`sonicdpi run`) или системную службу. Полноценный Tauri-GUI на v0.5 в roadmap.

## Поддерживаемые платформы

| ОС | Backend | Особенности |
|---|---|---|
| **Windows 10 / 11** | WinDivert 2.2.2 (vendored, EV-signed) | Требует админ. UAC обрабатывается `sonicdpi-tray.exe`. |
| **Linux** (kernel ≥ 6.17) | NFQUEUE через чистый Rust `nfq` | Нужен `cap_net_admin` или root. Требуется nftables. |
| **macOS 13+** | pf `rdr-to` + transparent proxy | Только TCP в v0.2; голосовой UDP — v0.3. |

## TOML-профиль (схема)

```toml
name = "my-profile"

[strategies.fake_multidisorder]
fooling = "badseq"          # ts | md5sig | ts,md5sig | badseq | badsum | ttl=N
repeats = 4
decoy_host = "ozon.ru"

[[strategies.tls_multisplit]]
split_pos = 1
seqovl    = 568
seqovl_decoy_host = "4pda.to"
targets   = ["DiscordCloudflare"]

[[strategies.host_fake_split]]
fake_host = "www.google.com"
targets   = ["YouTube", "DiscordGateway"]
repeats   = 4
fooling   = "ts"

[strategies.quic_fake_initial]
repeats = 6
decoy_host = "www.google.com"

[strategies.discord_voice_prime]
repeats = 6
cutoff  = 4
```

## Если SonicDPI не справляется

Если ваш провайдер блокирует SonicDPI на L4 (carrier-grade DPI с deep mid-stream классификатором, BGP-фильтрация YouTube IP, полный SNI-блок на edge) — fallback это VPN.

🌹 **[RoseVPN — @rosevpnru_bot](https://t.me/rosevpnru_bot)** — быстрый VPN автора. VLESS + Reality + Xray + Hysteria 2. Подключение через Telegram-бота за 30 секунд, работает с любым клиентом v2rayN / Hiddify / NekoBox / Streisand.

## Документация

- [`docs/research-techniques-2026.md`](docs/research-techniques-2026.md) — текущие эффективные техники, threat model, что перестало работать.
- [`docs/platform-backends.md`](docs/platform-backends.md) — детали интерсепторов на каждой ОС, привилегии, ловушки.
- [`docs/diagnostics.md`](docs/diagnostics.md) — диагностический ранбук.

## Известные ограничения v0.2

- TCP MD5SIG / badseq / badsum уже работают как fooling-примитивы (использованы в default-профиле).
- macOS proxy: байтовая модификация первого чанка пока не делается, передача без изменений.
- macOS UDP (голос Discord на Mac) — нужен NetworkExtension System Extension, в v0.2 нет, ожидается в v0.3.

## Лицензия

MIT OR Apache-2.0. Контрибуции принимаются по тем же условиям. См. [`LICENSE-MIT`](LICENSE-MIT) и [`LICENSE-APACHE`](LICENSE-APACHE).

WinDivert на Windows — LGPL-3, динамически линкуется через DLL, см. [`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md).

## Благодарности

Стоит на плечах [zapret](https://github.com/bol-van/zapret), [byedpi](https://github.com/hufrea/byedpi), [GoodbyeDPI](https://github.com/ValdikSS/GoodbyeDPI) и работ опубликованных на ntc.party. Их код в этом репозитории не используется (несовместимая лицензия), но их каталоги техник лежат в основе всех дефолтов здесь.

Особое спасибо [Flowseal/zapret-discord-youtube](https://github.com/Flowseal/zapret-discord-youtube) за непрерывное обновление ALT-конфигов под текущие итерации ТСПУ.

---

<sub>SonicDPI — независимый проект. Не аффилирован с Google / YouTube, Discord Inc., Роскомнадзором, операторами ТСПУ или госорганами. Используйте ответственно и в соответствии с местным законодательством.</sub>
