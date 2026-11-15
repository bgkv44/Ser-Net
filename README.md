<div align="center">

<h1>Ser-Net</h1>

<p><b>VPN-клиент для Windows на Xray-core: подписки, умная маршрутизация и управление ссылками <code>sernet://</code>.</b></p>

<p>
  <a href="https://github.com/bgkv44/Ser-Net/releases"><img alt="Release" src="https://img.shields.io/github/v/release/bgkv44/Ser-Net?include_prereleases&amp;label=release&amp;color=7ee0ad"></a>
  <a href="https://github.com/bgkv44/Ser-Net/releases"><img alt="Downloads" src="https://img.shields.io/github/downloads/bgkv44/Ser-Net/total?label=downloads&amp;color=82b8ff"></a>
  <img alt="Platform" src="https://img.shields.io/badge/platform-Windows%2010%20%7C%2011%20x64-0078D6?logo=windows&amp;logoColor=white">
  <img alt="Tauri" src="https://img.shields.io/badge/Tauri-2-24C8DB?logo=tauri&amp;logoColor=white">
  <img alt="Core" src="https://img.shields.io/badge/core-Xray--core-6f42c1">
  <img alt="Status" src="https://img.shields.io/badge/status-beta-ffd27d">
</p>

<p>
  <a href="#русский"><b>Русский</b></a> ·
  <a href="#english"><b>English</b></a> ·
  <a href="https://github.com/bgkv44/Ser-Net/releases">Скачать</a> ·
  <a href="https://bgkv44.github.io/Ser-Net/">Гайд</a> ·
  <a href="https://t.me/secureNet_Support_new">Поддержка</a>
</p>

</div>

---

## Русский

**Содержание:** [Возможности](#возможности) · [Установка](#установка) · [Первое подключение](#первое-подключение) · [Режимы маршрутизации](#режимы-маршрутизации) · [Команды](#команды-sernet) · [Настройки](#настройки-и-обновления) · [Сборка](#сборка-из-исходников) · [Документация](#документация) · [English](#english)

### Что это

Ser-Net — настольный VPN-клиент для Windows, который работает поверх [Xray-core](https://github.com/XTLS/Xray-core). Он берёт серверы из обычной ссылки подписки вашего провайдера и даёт три понятных режима: пускать Россию напрямую, гнать всё через VPN или завернуть только выбранные сайты и приложения.

> [!NOTE]
> Ser-Net не продаёт подписки. Для работы нужен адрес подписки от вашего VPN-провайдера.

### Возможности

| Возможность | Описание |
|---|---|
| **Подписки** | Несколько ссылок одновременно, серверы активной подписки на главном экране, обновление одной карточки без переключения остальных. |
| **Мониторинг подписки** | Использованный трафик, срок действия, HWID-статус и кнопка личного кабинета — если провайдер передаёт эти данные. |
| **Выбор сервера** | Поиск по названию или стране, TCP-проверка задержки, фильтр доступных узлов и автоматический подбор быстрого сервера с подтверждением. |
| **Маршрутизация** | Три режима, готовые наборы правил для сервисов, свои домены/IP, импорт и экспорт списков. |
| **Два режима туннеля** | Системный прокси без прав администратора или TUN со службой Ser-Net для трафика всей системы. |
| **Обход DPI** | Фрагментация TLS для профилей TLS/REALITY, когда соединение режут по SNI. |
| **Автоматизация** | Автозапуск при входе в Windows, подключение к быстрому серверу при старте и команды `sernet://` для ярлыков. |
| **Диагностика** | Логи ядра и службы, версия ядра, состояние службы и проверка обновлений в самом приложении. |

### Установка

1. Откройте [страницу релизов](https://github.com/bgkv44/Ser-Net/releases).
2. Выберите один из файлов:
   - **Установщик** `Ser-Net_..._x64-setup.exe` — обычная установка в систему;
   - **Портативная версия** `SerNet-...-windows-x64-portable.zip` — распакуйте в любую папку и запустите без установки.
3. Запустите Ser-Net.

Требования: Windows 10 или 11, 64-битная система. Текущие сборки помечены как **бета** — это тестовые версии, которые могут меняться между релизами.

### Первое подключение

1. Откройте раздел **«Подписки»** в нижней навигации.
2. Нажмите **«Добавить подписку»**, вставьте ссылку и нажмите **«Загрузить»**. Ссылку можно вставить из буфера обмена.
3. Если подписок несколько, нажмите **«Выбрать»** на нужной — её серверы появятся на главном экране.
4. На экране **«Подключение»** выберите сервер и нажмите круглую кнопку питания. Либо нажмите **«Подключиться к быстрому серверу»**: Ser-Net проверит узлы и предложит подтвердить подключение.

> [!IMPORTANT]
> Для режима TUN нужна служба Ser-Net. При её установке Windows покажет запрос UAC. Системному прокси эта служба не требуется.

### Режимы маршрутизации

| Режим | Что делает |
|---|---|
| **Умный режим** | Сайты России и локальная сеть идут напрямую, остальное — через VPN. Подходит для повседневной работы. |
| **Весь трафик через VPN** | Весь трафик идёт в туннель, кроме локальных сетей и заданных исключений. В режиме системного прокси называется «Трафик через прокси». |
| **Только выбранное** | Через VPN идут только правила из списка «Через VPN», остальное — напрямую. Здесь же работает блокировка рекламных доменов. |

Дополнительно:

- **Ручные правила** — домены, IP-адреса и приложения Windows (в TUN). Списки зависят от режима: «Напрямую»/«Блокировать» или «Через VPN»/«Блок».
- **Применение на лету** — при активном подключении изменения сначала помечаются как «Есть изменения», затем применяются кнопкой **«Применить»**.
- **Готовая конфигурация панели** — если подписка отдаёт полный JSON, маршрутизацию задаёт провайдер, а режимы Ser-Net для неё не применяются.

### Команды `sernet://`

Команды управляют приложением из ярлыка, скрипта или другого приложения. Шаблоны в фигурных скобках нужно заменить своими данными.

| Команда | Действие |
|---|---|
| `sernet://connect` | Подключиться к выбранному серверу; если сервер не выбран — запустить подбор быстрого сервера. |
| `sernet://open` | Показать окно и подключиться, если VPN ещё не подключён. |
| `sernet://disconnect` | Отключить VPN. |
| `sernet://toggle` | Включить VPN, если он выключен, и наоборот. |
| `sernet://best` | Проверить серверы и выбрать самый быстрый. |
| `sernet://refresh` | Обновить серверы активной подписки. |
| `sernet://add/{ссылка}` | Добавить подписку по ссылке в URL-кодировании. |
| `sernet://server/{имя-или-код-страны}` | Выбрать сервер по коду страны или части названия. |
| `sernet://routing/off` | Вернуть «Умный режим»; ручные правила сохраняются. |
| `sernet://routing/mode/smart` | Включить «Умный режим». |
| `sernet://routing/mode/global` | Включить режим «Весь трафик через VPN». |
| `sernet://routing/mode/selective` | Включить режим «Только выбранное». |
| `sernet://routing/add/{base64}` | Импортировать правила из base64url: JSON с массивами `proxy`/`direct`/`block` или список строк. |

Полный справочник с копированием доступен в приложении: **Настройки → «Команды Ser-Net»**.

### Настройки и обновления

- **Режим подключения** — системный прокси или TUN; выбранный вариант применяется при следующем подключении.
- **Служба Ser-Net** — состояние, установка, обновление и переустановка.
- **Автозапуск** — запуск при входе в Windows без запроса UAC.
- **Защита трафика при запуске** — при следующем старте приложение проверяет серверы и подключается к самому быстрому.
- **Оформление** — светлая, тёмная или системная тема.
- **Логи** — журналы ядра и службы для диагностики.
- **Обновления** — встроенная проверка новых версий и ручная проверка в разделе «О приложении».

> [!WARNING]
> Ссылка подписки — это доступ к вашему аккаунту. Не публикуйте её в чатах и не прикладывайте к issues. Для диагностики достаточно логов без ссылки.

### Сборка из исходников

Нужны **Node.js 20+**, **Rust (stable)** с инструментами MSVC, **WebView2** (в Windows 11 уже установлен) и `cargo`.

```bash
git clone https://github.com/bgkv44/Ser-Net.git
cd Ser-Net
npm install
npm run tauri:dev
```

Сборка службы TUN и установщика:

```bash
cargo build --release --manifest-path service/Cargo.toml
npm run tauri:build
```

Проверки маршрутизации:

```bash
npm run test:routing
npm run test:routing:xray
```

Релиз собирается GitHub Actions по тегу `v*`; workflow проверяет совпадение тега, версии в `package.json` и `src-tauri/tauri.conf.json`.

### Документация

| Документ | О чём |
|---|---|
| [Руководство пользователя](https://bgkv44.github.io/Ser-Net/) | Подробный гайд по всем экранам и командам; исходник — [SITE-github/index.html](SITE-github/index.html). |
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | Архитектура: изоляция платформ, мост UI ↔ ядро, структура проекта. |
| [docs/01_BUILD_LIBXRAY.md](docs/01_BUILD_LIBXRAY.md) | Сборка ядра XTLS/LibXray. |
| [docs/02_ANDROID_GUIDE.md](docs/02_ANDROID_GUIDE.md) | Модуль Android: `VpnService` и `libXray.aar`. |
| [docs/03_IOS_MACOS_GUIDE.md](docs/03_IOS_MACOS_GUIDE.md) | Модули iOS/macOS: Network Extension и лимит памяти. |
| [docs/04_WINDOWS_GUIDE.md](docs/04_WINDOWS_GUIDE.md) | Модуль Windows: системный прокси, WinTun и маршруты. |
| [release](release) | Заметки к последним бета-сборкам. |

Текущие публичные сборки — **Windows x64**. Модули macOS, Android и iOS находятся в репозитории как изолированные платформенные части и документация к ним.

### Поддержка

- Telegram: [@secureNet_Support_new](https://t.me/secureNet_Support_new)
- Ошибки и предложения: [GitHub Issues](https://github.com/bgkv44/Ser-Net/issues)

Перед обращением приложите логи из **Настройки → «Логи»** и версию из **«О приложении»**. Ссылку подписки и пароли не отправляйте.

---

## English

**Contents:** [Features](#features) · [Install](#install) · [First connection](#first-connection) · [Routing modes](#routing-modes) · [Commands](#sernet-commands) · [Settings](#settings-and-updates) · [Build](#build-from-source) · [Documentation](#documentation) · [Русский](#русский)

### What is Ser-Net

Ser-Net is a Windows desktop VPN client built on [Xray-core](https://github.com/XTLS/Xray-core). It reads servers from a standard provider subscription link and offers three straightforward modes: keep Russian sites direct, route everything through the VPN, or tunnel only the sites and apps you choose.

> [!NOTE]
> Ser-Net does not sell subscriptions. You need a subscription URL from your VPN provider.

### Features

- **Multiple subscriptions** with per-card refresh, traffic usage, expiry date and provider dashboard link when the subscription exposes them.
- **Smart server selection**: search, TCP latency checks, an available-only filter, and one-click fastest-server picking with confirmation.
- **Three routing modes** with service presets, custom domain/IP rules, and list import/export.
- **Two tunnel modes**: system proxy without administrator rights, or TUN through the Ser-Net service for system-wide traffic.
- **DPI evasion** via TLS fragmentation for TLS/REALITY profiles.
- **Automation**: launch at Windows sign-in, auto-connect to the fastest server at startup, and `sernet://` links for shortcuts and scripts.
- **Diagnostics**: core and service logs, core version, service state and update checks inside the app.

### Install

1. Open the [releases page](https://github.com/bgkv44/Ser-Net/releases).
2. Pick a file:
   - **Installer** `Ser-Net_..._x64-setup.exe` — regular system installation;
   - **Portable** `SerNet-...-windows-x64-portable.zip` — unpack anywhere and run without installing.
3. Launch Ser-Net.

Requirements: Windows 10 or 11, 64-bit. Current builds are marked **beta**: test versions that may change between releases.

### First connection

1. Open **Subscriptions** in the bottom navigation.
2. Click **Add subscription**, paste the link and press **Load**. Pasting straight from the clipboard works too.
3. With several subscriptions, press **Select** on the one you need; its servers appear on the main screen.
4. On the **Connection** screen pick a server and press the round power button. Or press **Connect to fastest server**: Ser-Net checks the nodes and asks you to confirm.

> [!IMPORTANT]
> TUN mode requires the Ser-Net service. Windows shows a UAC prompt during installation. System proxy mode does not need the service.

### Routing modes

| Mode | Behaviour |
|---|---|
| **Smart** | Russian sites and the local network stay direct; everything else goes through the VPN. |
| **All traffic through VPN** | Everything is tunnelled except local networks and your exceptions. In system proxy mode it is labelled “Traffic through proxy”. |
| **Selected only** | Only rules in the “Through VPN” list are tunnelled; everything else stays direct. Ad-domain blocking works in this mode. |

Notes:

- **Custom rules** cover domains, IP addresses and Windows applications (TUN). Available lists depend on the mode.
- **Live changes** are marked as pending on an active connection and applied with the **Apply** button.
- **Provider JSON** subscriptions control their own routing; Ser-Net modes and manual lists do not apply to them.

### `sernet://` commands

Commands control the app from a shortcut, script or another application. Replace placeholders in braces with your own values.

| Command | Action |
|---|---|
| `sernet://connect` | Connect to the selected server, or start fastest-server picking when none is selected. |
| `sernet://open` | Show the window and connect if the VPN is not running. |
| `sernet://disconnect` | Disconnect the VPN. |
| `sernet://toggle` | Turn the VPN on if it is off, and vice versa. |
| `sernet://best` | Check servers and pick the fastest one. |
| `sernet://refresh` | Refresh the active subscription. |
| `sernet://add/{url}` | Add a subscription from a URL-encoded link. |
| `sernet://server/{name-or-country-code}` | Select a server by country code or part of its name. |
| `sernet://routing/off` | Return to Smart mode; manual rules are kept. |
| `sernet://routing/mode/smart` | Enable Smart mode. |
| `sernet://routing/mode/global` | Enable All traffic through VPN. |
| `sernet://routing/mode/selective` | Enable Selected only. |
| `sernet://routing/add/{base64}` | Import rules from base64url: JSON arrays `proxy`/`direct`/`block`, or a plain list. |

The in-app reference with copy buttons lives under **Settings → Ser-Net commands**.

### Settings and updates

- **Tunnel mode** — system proxy or TUN; applied on the next connection.
- **Ser-Net service** — state, install, update and reinstall.
- **Autostart** — launch at Windows sign-in without a UAC prompt.
- **Protect traffic at startup** — on the next launch the app checks servers and connects to the fastest one.
- **Appearance** — light, dark or system theme.
- **Logs** — core and service journals for diagnostics.
- **Updates** — built-in version checks plus a manual check under About.

> [!WARNING]
> A subscription URL is access to your account. Do not post it in chats or attach it to issues. Logs without the link are enough for diagnostics.

### Build from source

You need **Node.js 20+**, **Rust (stable)** with MSVC tooling, **WebView2** (already present on Windows 11) and `cargo`.

```bash
git clone https://github.com/bgkv44/Ser-Net.git
cd Ser-Net
npm install
npm run tauri:dev
```

Build the TUN service and the installer:

```bash
cargo build --release --manifest-path service/Cargo.toml
npm run tauri:build
```

Routing checks:

```bash
npm run test:routing
npm run test:routing:xray
```

Releases are built by GitHub Actions on `v*` tags; the workflow verifies that the tag matches the versions in `package.json` and `src-tauri/tauri.conf.json`.

### Documentation

| Document | Content |
|---|---|
| [User guide](https://bgkv44.github.io/Ser-Net/) | Full guide covering every screen and command; source — [SITE-github/index.html](SITE-github/index.html). |
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | Architecture: platform isolation, UI ↔ core bridge, project layout. |
| [docs/01_BUILD_LIBXRAY.md](docs/01_BUILD_LIBXRAY.md) | Building the XTLS/LibXray core. |
| [docs/02_ANDROID_GUIDE.md](docs/02_ANDROID_GUIDE.md) | Android module: `VpnService` and `libXray.aar`. |
| [docs/03_IOS_MACOS_GUIDE.md](docs/03_IOS_MACOS_GUIDE.md) | iOS/macOS modules: Network Extension and memory limits. |
| [docs/04_WINDOWS_GUIDE.md](docs/04_WINDOWS_GUIDE.md) | Windows module: system proxy, WinTun and routes. |
| [release](release) | Notes for the latest beta builds. |

Public builds currently target **Windows x64**. The macOS, Android and iOS modules live in the repository as isolated platform parts with their own documentation.

### Support

- Telegram: [@secureNet_Support_new](https://t.me/secureNet_Support_new)
- Bugs and ideas: [GitHub Issues](https://github.com/bgkv44/Ser-Net/issues)

Include logs from **Settings → Logs** and the version from **About**. Never send your subscription link or passwords.

---

<div align="center">
  <sub>Ser-Net · <a href="#русский">Русский</a> · <a href="#english">English</a> · <a href="#">Наверх / Back to top</a></sub>
</div>
