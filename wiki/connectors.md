# Connect your tools

Every Flow action can reach your existing tools: OBS, generic webhooks
(Streamer.bot, n8n, Zapier, Make…), Discord and Home Assistant. This page
gives you the copy-paste recipes.

## The standard webhook envelope

When a rule fires a **Webhook** action, Retro Creator POSTs this JSON:

```json
{
  "source": "RetroCreator",
  "event": "resource.gained",
  "timestamp": "2026-07-12T14:03:22.123Z",
  "game": { "name": "Sonic The Hedgehog", "system": "megadrive" },
  "payload": { "actionType": "COIN_GAIN" }
}
```

Built-in safeguards: 1 s cooldown per URL, one automatic retry on server
errors, 5 s timeout. Use the **⚡ Test** button next to the action to send a
sample event instantly.

## Custom body & headers

If your tool expects its own format, fill the **Custom body** field — it
replaces the standard envelope and supports placeholders: `{game}`,
`{value}`, `{counter.name}` and any payload field. Add HTTP headers
(one `Name: value` per line) for tools that require a token.

## Recipes

### Home Assistant
1. Automation → Trigger → **Webhook**, pick an id (e.g. `retrocreator`).
2. In the Flow action, URL: `http://homeassistant.local:8123/api/webhook/retrocreator`.
3. Use the data in your automation: `{{ trigger.json.event }}`, `{{ trigger.json.game.name }}`.

### Streamer.bot
1. Enable its **HTTP Server** (Settings → Servers, default port 7474).
2. Pick the **Streamer.bot** preset in the Flow action — it pre-fills
   `http://127.0.0.1:7474/DoAction` and the body template:
   `{"action": {"name": "MyAction"}, "args": {"game": "{game}"}}`.
3. Replace `MyAction` with your Streamer.bot action name. From there you can
   drive Stream Deck, Touch Portal, sounds, chat messages…

### n8n / Zapier / Make
Create a **Webhook trigger** in your scenario and paste its URL in the Flow
action. The standard envelope arrives as-is — map the fields you need.

### Discord
Use the dedicated **Discord** action with a channel webhook URL
(channel settings → Integrations → Webhooks). Messages support the same
placeholders.

## Ephemeral states ("For…")

Popups, OBS scene switches and source visibility accept a **For** duration
(5 s to 10 min, or unlimited). When it ends, Retro Creator restores the
previous state by itself: the scene switches back, the source re-hides, the
popup closes. Great for temporary alerts and reaction scenes.
