<div align="center">

<!-- Баннер: assets/banner.svg (1200x300). Замените файл, чтобы поменять фон/цвета,
     или удалите весь блок <div align="center"> ... </div> ниже, если баннер не нужен.
     ВАЖНО: при смене картинки меняйте и ?v=N — иначе GitHub отдаёт старую версию из кэша. -->
<img src="./assets/banner.svg?v=2" width="100%" alt="Mextrim — Rust server admin &amp; stream overlay engineering" />

<br/>

<a href="https://github.com/Mextrim?tab=followers">
  <img src="https://img.shields.io/github/followers/Mextrim?label=Followers&color=7FD3FF&style=flat-square" alt="Followers" />
</a>
<!-- Бейдж Repos-3 статичный: у shields.io нет счётчика репозиториев на уровне
     пользователя. Обновляйте цифру вручную, когда появится новый репозиторий. -->
<a href="https://github.com/Mextrim?tab=repositories">
  <img src="https://img.shields.io/badge/Repos-3-7CE7C4?style=flat-square" alt="Repositories" />
</a>
<a href="https://github.com/Mextrim/RUST_SERVER/commits/main">
  <img src="https://img.shields.io/github/last-commit/Mextrim/RUST_SERVER?label=Last%20commit&color=FFD479&style=flat-square" alt="Last commit" />
</a>
<!-- Счётчик просмотров (komarev.com) убран: GitHub'овский camo-прокси не отдаёт его картинку,
     и на профиле вместо бейджа показывается текст «Profile views». -->

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=3821798934">
  <img src="https://img.shields.io/badge/Steam%20Workshop-Minimal%20Chat-1b2838?style=flat-square&logo=steam&logoColor=66c0f4" alt="Minimal Chat on Steam Workshop" />
</a>
<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=3821773297">
  <img src="https://img.shields.io/badge/Steam%20Workshop-W.TV%20Bridge-1b2838?style=flat-square&logo=steam&logoColor=66c0f4" alt="W.TV bridge on Steam Workshop" />
</a>

<br/>

<!-- Высота 120px обязательна: сервис игнорирует multiline=true и по умолчанию
     отдаёт бокс 50px, в котором три строки обрезаются. -->
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=23&pause=1300&color=7FD3FF&center=true&vCenter=true&height=120&width=640&lines=Rust+dedicated+server+admin;Chat+overlays+for+streamers;Automation+that+just+keeps+working" alt="Typing animation" />

</div>

---

## 👋 Hey, I'm Mextrim

📍 Парабель

---

## 🛠 What I build

| 🎮 **Rust server ops** | 💬 **Stream chat tooling** |
|:---|:---|
| **Dedicated server setup** — launch scripts, `watchdog.ps1` auto-restart, one-command validate<br>**Carbon config suite** — 15 tuned configs (Admins, Backpacks, Kits, NTeleportation, FancyDrop, FurnaceSplitter, RemoverTool, …)<br>**Permissions & kits** — group-based permissions, kit data, no secrets in the repo<br>**`RLXMenu` plugin** — C# source for the server menu, documented in `docs/PLUGINS.md` | **Chat themes** — CSS/HTML templates with live-editable parameters (14 knobs: colors, fonts, row count, fade time, shadows)<br>**Chat-bot scripts** — C# autonomous scripts, hot-reloadable, no restart required<br>**Platform bridges** — pull chats from places RutonyChat doesn't support natively, without ever joining or posting<br>**OBS-ready output** — every theme exposes a browser-source link straight from the app |

---

## 📦 Repositories

| 🎮 <a href="https://github.com/Mextrim/RUST_SERVER">RUST_SERVER</a> | 💬 <a href="https://github.com/Mextrim/rutonychat-minimal-chat">rutonychat-minimal-chat</a> | 🌉 <a href="https://github.com/Mextrim/rutonychat-wtv-script">rutonychat-wtv-script</a> |
|:---|:---|:---|
| <img src="https://img.shields.io/badge/C%23-512BD4?style=flat-square&logo=csharp&logoColor=white" alt="C#" /> <img src="https://img.shields.io/badge/PowerShell-5391FE?style=flat-square&logo=powershell&logoColor=white" alt="PowerShell" /> | <img src="https://img.shields.io/badge/HTML-E34F26?style=flat-square&logo=html5&logoColor=white" alt="HTML" /> <img src="https://img.shields.io/badge/CSS-1572B6?style=flat-square&logo=css3&logoColor=white" alt="CSS" /> <img src="https://img.shields.io/badge/license-MIT-7CE7C4?style=flat-square" alt="MIT" /> | <img src="https://img.shields.io/badge/C%23-512BD4?style=flat-square&logo=csharp&logoColor=white" alt="C#" /> <img src="https://img.shields.io/badge/license-MIT-7CE7C4?style=flat-square" alt="MIT" /> |
| Rust dedicated server setup — launch scripts, Carbon configs, and menu plugin source. | Minimal chat theme for RutonyChat — **no cards, no backgrounds, just text.** | Read-only W.TV chat bridge for RutonyChat, as an autonomous script. |
| `watchdog.ps1`<br>`configs/carbon/`<br>`configs/permissions/`<br>`RLXMenu.cs` | ~25px per row instead of ~44px, fully transparent, so the game stays visible on stream.<br>14 tunable parameters · 36 recognised platforms | RutonyChat has no native W.TV support, so this pulls the public message list and injects every line into the chat window. |
| **[Repo →](https://github.com/Mextrim/RUST_SERVER)** | **[Repo →](https://github.com/Mextrim/rutonychat-minimal-chat)** · [Workshop →](https://steamcommunity.com/sharedfiles/filedetails/?id=3821798934) | **[Repo →](https://github.com/Mextrim/rutonychat-wtv-script)** · [Workshop →](https://steamcommunity.com/sharedfiles/filedetails/?id=3821773297) |

---

## 🔬 Notes from the field

<details>
<summary><b>Why the W.TV bridge doesn't use a WebSocket</b></summary>

<br/>

W.TV's realtime endpoint (`wss://ws.w.tv/connection/websocket`, Centrifugo) rejects .NET's `ClientWebSocket` with **HTTP 403**. The headers are fine — Cloudflare bot management rejects the **TLS fingerprint**, not the payload. There is no header you can set to fix this.

So the script polls the REST history instead of holding a socket:

1. `GET profiles-service.w.tv/api/v1/profiles/by-nickname/{nick}` → resolve `userId` (which *is* the `chatId`)
2. `GET chats-service.w.tv/api/v1/chats/{chatId}/messages?limit=30` → pull the public message list

Both requests are anonymous, every response is wrapped so a bad payload can never take the chat client down, and a bounded dedupe buffer keeps re-rendered messages from repeating. Lines are tagged with an invisible `U+200D wtv U+200D` marker so chat themes can recognise the source and render the right logo.

**Strictly read-only.** It never joins a chat, never opens a realtime socket, never posts.

</details>

<details>
<summary><b>Why the chat theme has no cards</b></summary>

<br/>

A chat card with a background and a border costs roughly **44px per line**. On stream that is the difference between "chat at the edge of the frame" and "chat covering the HUD".

Minimal Chat is **fully transparent, ~25px per line**, with readability carried by **text shadow** instead of a plate. That makes shadow size the primary parameter, not decoration — 4–5px over a light game, 2–3px over a dark one.

Replies are styled inline in italics rather than getting their own row, and site icons are detected from the icon file and glow in the platform colour.

</details>

---

## 🧰 Stack

<div align="center">

<img height="42" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" alt="C#" />
<img height="42" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" alt="HTML5" />
<img height="42" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" alt="CSS3" />
<img height="42" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/powershell/powershell-original.svg" alt="PowerShell" />
<img height="42" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/visualstudio/visualstudio-original.svg" alt="Visual Studio" />
<img height="42" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/json/json-original.svg" alt="JSON" />
<img height="42" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/sqlite/sqlite-original.svg" alt="SQLite" />
<img height="42" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nuget/nuget-original.svg" alt="NuGet" />
<img height="42" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt="Git" />

<br/><br/>

**Carbon** · **Rust** · **RutonyChat** · **OBS Studio** · **Steam Workshop** · **WebView2**

</div>

---

## 📊 Stats

<!-- Карточки приходят с публичных сервисов и могут не отрисоваться при их недоступности
     или rate-limit. Чтобы убрать блок целиком — удалите отсюда до конца секции "Elsewhere".
     Если картинки не грузятся, удалите <details> со змейкой: она требует Actions
     (.github/workflows/snake.yml) и появляется через сутки после первого запуска. -->
<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=Mextrim&show_icons=true&theme=tokyonight&hide_border=true&include_all_commits=true&count_private=true&rank_icon=github" alt="GitHub stats" width="410" />
<img src="https://github-readme-stats.vercel.app/api/top-langs?username=Mextrim&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" alt="Top languages" width="300" />

</div>

<br/>

<details>
<summary>Contribution activity</summary>

<br/>

<img src="https://raw.githubusercontent.com/Platane/snk/output/github-contribution-grid-snake-dark.svg" alt="Contribution snake animation" />

</details>

---

## 🔗 Elsewhere

<div align="center">

[![Steam](https://img.shields.io/badge/Steam-1b2838?style=flat-square&logo=steam&logoColor=66c0f4&label=Workshop)](https://steamcommunity.com/app/524660/workshop/)
[![Twitch](https://img.shields.io/badge/Twitch-9146FF?style=flat-square&logo=twitch&logoColor=white)](https://twitch.tv)
[![W.TV](https://img.shields.io/badge/W.TV-0F1620?style=flat-square&logoColor=7CE7C4&label=chat%20bridge)](https://w.tv/mextrim)
[![RutonyChat](https://img.shields.io/badge/RutonyChat-1b2838?style=flat-square&logoColor=FFD479&label=theme+author)](https://store.steampowered.com/app/524660/RutonyChat/)

</div>

<br/>

<div align="center">

*Built with too much stubbornness and not enough sleep.*

</div>