# Twitch integration

Retro Creator reads your Twitch chat **without any key, token or password**:
it joins your channel anonymously, in read-only mode. It cannot write anything,
so there is zero risk for your channel.

## 1. Plug your channel

1. Open **File → Settings…**
2. In the **Twitch** card, type your channel name (e.g. `my_channel`) and save.
3. The Event tab header confirms the state: `🟣 Twitch chat connected · #my_channel`.

From that moment, every chat message becomes an event in the pipeline:

| Event | When |
|---|---|
| **Twitch chat message** | a viewer writes anything |
| **Twitch chat !command** | a viewer types a `!command` (e.g. `!ring 3`) |

They appear in the Live view, in the Monitor, and can trigger **Flows** like
any game event. The Designer also gets bindings: *last viewer*, *last message*.

## 2. Run a chat contest (no configuration)

![Event dashboard](assets/event.png)

Open **Mode → Event** → **Quick contest**:

1. Choose the **!command** viewers must type (the *slug*, e.g. `!go`),
   the **duration**, and the winner message.
2. Press **▶ Start participation** — the countdown runs, the participant list
   grows in real time (one entry per viewer, even if they spam), with a live
   counter.
3. At zero, a winner is drawn: big announcement on screen **and** a popup on
   your OBS overlay.

## 3. Automate contests with Flows (e.g. Ring Lottery)

For recurring mechanics, condition everything in **Flows** and pilot it from
**Event**:

1. **Widgets → Ring Lottery Pop → Edit** creates the ready-made flow:
      - every ring collected in-game increments a counter;
      - every viewer typing `!ring` joins the draw pool;
      - at 100 rings, a winner is drawn and announced.
2. Change the *slug* by editing the rule's **If** condition
   (`chat command equals ring` → put whatever you want).
3. In **Event → Automated games**, select the flow, press **▶ Activate**, and
   watch the dashboard: ring counter, participants joining live, last winner.

!!! note "What about writing to the chat?"
    Announcing winners *in the chat* (not just on the overlay) requires a
    Twitch authorization (OAuth). This is on the roadmap; today all
    announcements happen on-screen, which is what viewers watch anyway.
