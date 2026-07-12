# Retro Creator

**Studio d'overlays live pour le streaming retro-gaming — piloté par les vraies données de jeu.**

Un boss vaincu, des anneaux perdus, un record battu — Retro Creator transforme ce
qui se passe réellement dans vos jeux retro en overlays de stream soignés, en
éclairages de pièce et en automatisations live, sans écrire une ligne de code.

![Le jeu pilote votre stream](assets/flow-game-to-stream.svg)

??? note "Sous le capot"
    Retro Creator s'appuie sur [RetroBat APIExpose](https://github.com/Nelfe80/RetroBat-APIExpose)
    et son [SDK Data/Event](https://github.com/Nelfe80/APIExpose-SDK) ouvert. APIExpose
    observe la mémoire vive du jeu en cours via un wrapper d'émulateur signé et
    normalise chaque moment de gameplay dans un vocabulaire d'événements stable
    (actions et familles comme `scoring.points` ou `flow.lifecycle`). Plus de
    14 000 jeux sur 57 systèmes sont livrés pré-cartographiés, et chaque définition
    d'événement peut être inspectée — ou étendue — en texte clair.

![Vue Live](assets/pulse.png)

## Ce qu'il fait

- **Designer visuel** — composez vos overlays avec des widgets prêts à l'emploi
  (score, timer, now playing, boxart, popups de succès, input viewer…), des thèmes et
  des animations.
- **Compatible avec votre setup de stream** — les overlays sont servis localement en
  sources navigateur standard, compatibles OBS Studio, Streamlabs Desktop, Meld Studio
  et tout logiciel qui affiche des pages web.
- **Automatisations live** — les événements de gameplay déclenchent vos outils
  existants : Streamer.bot, Stream Deck, Touch Portal, webhooks, Discord,
  MQTT / Home Assistant et plus.
- **Local d'abord** — pas de compte, pas de cloud obligatoire. Vos données restent sur
  votre machine.
- Interface **français & anglais**, d'autres langues à venir.


## Documentation

- **[Bien démarrer](getting-started.md)** — de zéro à l'overlay en direct.
- **[Guide du Designer](designer.md)** — vues, popups, composants, calques, styles.
- **[Flows & Event](flows-events.md)** — automatisations et tableau de bord live.
- **[Intégration Twitch](twitch.md)** — branchez votre chat (aucune clé) et lancez des concours.

## Statut

Retro Creator est **disponible** — [téléchargez la dernière version](https://github.com/Nelfe80/RetroCreator-Wiki/releases/latest).
Ce site héberge la documentation officielle et le [suivi des issues](support.md).

!!! tip "Lancez-vous"
    [Téléchargez Retro Creator](https://github.com/Nelfe80/RetroCreator-Wiki/releases/latest), déposez-le dans `RetroBat\plugins\`,
    lancez `RetroCreator.exe` — votre premier overlay live est à cinq minutes.
