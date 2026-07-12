# Retro Creator

**Live overlay studio for retro-gaming streams — powered by real gameplay data.**

Beat a boss, lose your rings, break a record — Retro Creator turns what actually
happens in your retro games into polished stream overlays, room lighting and live
automations, without writing a single line of code.

![The game drives your stream](assets/flow-game-to-stream.svg)

??? note "Under the hood"
    Retro Creator is built on top of [RetroBat APIExpose](https://github.com/Nelfe80/RetroBat-APIExpose)
    and its open [Data/Event SDK](https://github.com/Nelfe80/APIExpose-SDK). APIExpose
    watches the live memory of the running game through a signed emulator wrapper and
    normalizes every gameplay moment into a stable event vocabulary (actions and
    families like `scoring.points` or `flow.lifecycle`). More than 14,000 games across
    57 systems ship pre-mapped, and each event definition can be inspected — or
    extended — in plain text.

![Live view](assets/pulse.png)

## What it does

- **Visual designer** — compose overlays with ready-made widgets (score, timer, now
  playing, boxart, achievement popups, input viewer…), themes and animations.
- **Works with your streaming setup** — overlays are served locally as standard
  browser sources, compatible with OBS Studio, Streamlabs Desktop, Meld Studio and
  any software that renders web pages.
- **Live automations** — gameplay events can trigger your existing tools:
  Streamer.bot, Stream Deck, Touch Portal, webhooks, Discord, MQTT / Home Assistant
  and more.
- **Local first** — no account, no cloud required. Your data stays on your machine.
- **English & French** interface, more languages to come.


## Documentation

- **[Getting started](getting-started.md)** — from zero to a live overlay.
- **[Designer guide](designer.md)** — views, popups, components, layers, styles.
- **[Flows & Event](flows-events.md)** — automations and the live dashboard.
- **[Twitch integration](twitch.md)** — plug your chat (no key needed) and run contests.

## Status

Retro Creator is **released** — [download the latest version](https://github.com/Nelfe80/RetroCreator-Wiki/releases/latest).
This site hosts the official documentation and the [issue tracker](support.md).

!!! tip "Get it now"
    [Download Retro Creator](https://github.com/Nelfe80/RetroCreator-Wiki/releases/latest), drop it in `RetroBat\plugins\`, launch
    `RetroCreator.exe` — your first live overlay is five minutes away.
