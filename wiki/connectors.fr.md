# Connecter vos outils

Chaque action de Flow peut atteindre vos outils existants : OBS, webhooks
génériques (Streamer.bot, n8n, Zapier, Make…), Discord et Home Assistant.
Voici les recettes à copier-coller.

## L'enveloppe webhook standard

Quand une règle déclenche une action **Webhook**, Retro Creator envoie ce
POST JSON :

```json
{
  "source": "RetroCreator",
  "event": "resource.gained",
  "timestamp": "2026-07-12T14:03:22.123Z",
  "game": { "name": "Sonic The Hedgehog", "system": "megadrive" },
  "payload": { "actionType": "COIN_GAIN" }
}
```

Garde-fous intégrés : cooldown 1 s par URL, un retry automatique sur erreur
serveur, timeout 5 s. Le bouton **⚡ Tester** à côté de l'action envoie un
événement d'essai instantanément.

## Corps et en-têtes personnalisés

Si votre outil attend **son** format, remplissez le champ « Corps
personnalisé » — il remplace l'enveloppe standard et accepte les
placeholders : `{game}`, `{value}`, `{counter.nom}` et tout champ du
payload. Ajoutez des en-têtes HTTP (une ligne `Nom: valeur` par en-tête)
pour les outils à token.

## Recettes

### Home Assistant
1. Automatisation → Déclencheur → **Webhook**, choisissez un id (ex. `retrocreator`).
2. Dans l'action de Flow, URL : `http://homeassistant.local:8123/api/webhook/retrocreator`.
3. Exploitez les données : `{{ trigger.json.event }}`, `{{ trigger.json.game.name }}`.

### Streamer.bot
1. Activez son **HTTP Server** (Settings → Servers, port 7474 par défaut).
2. Choisissez le preset **Streamer.bot** dans l'action de Flow — il
   pré-remplit `http://127.0.0.1:7474/DoAction` et le gabarit :
   `{"action": {"name": "MonAction"}, "args": {"game": "{game}"}}`.
3. Remplacez `MonAction` par le nom de votre action Streamer.bot. De là,
   pilotez Stream Deck, Touch Portal, sons, messages de chat…

### n8n / Zapier / Make
Créez un déclencheur **Webhook** dans votre scénario et collez son URL dans
l'action de Flow. L'enveloppe standard arrive telle quelle — mappez les
champs utiles.

### Discord
Utilisez l'action dédiée **Discord** avec l'URL d'un webhook de salon
(paramètres du salon → Intégrations → Webhooks). Les messages acceptent les
mêmes placeholders.

## États éphémères (« Pendant… »)

Les popups, bascules de scène OBS et visibilités de source acceptent une
durée **Pendant** (5 s à 10 min, ou sans limite). À la fin, Retro Creator
restaure l'état précédent tout seul : la scène revient, la source se
remasque, la popup se ferme. Idéal pour les alertes temporaires et les
scènes de réaction.
