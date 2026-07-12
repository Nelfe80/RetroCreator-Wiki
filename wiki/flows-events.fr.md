# Flows & tableau de bord Event

Deux onglets, un seul process : **Flows** pour *conditionner* une mécanique,
**Event** pour l'*activer et la suivre*.

## Flows — conditionner le process

![Flow Builder](assets/flows.png)

Un flow est un ensemble de règles lisibles :

> **Quand** `anneau gagné` → **Alors** `ajouter 1 au compteur rings`
>
> **Quand** `compteur atteint` **Si** `compteur rings au moins 100` →
> **Alors** `afficher popup 🎉`, `remettre le compteur rings à zéro`

- **Quand** — n'importe quel événement du catalogue : événements de jeu (vie
  perdue, game over, anneaux/pièces, record, niveau…), messages et !commandes
  du chat Twitch, compteurs, état de l'API.

    ??? note "Sous le capot — d'où viennent les événements de jeu"
        Les événements de jeu sont de vrais signaux de gameplay normalisés, publiés
        par APIExpose sur `/ws/ingame`. Chacun porte une **action** (`LOSE_LIFE`,
        `BOSS_DEFEATED`, `COIN_GAIN`…), une **famille** (`resources.lives`,
        `combat.enemies`, `scoring.collectibles`…) et, quand le jeu les fournit, une
        **couleur** et un index **joueur**. Les sélecteurs ne proposent que les
        moments qui existent vraiment dans le jeu en cours — les définitions
        dormantes sont filtrées, donc ce que vous choisissez se déclenchera.
- **Si** — une condition fermée sur un champ du payload ou un compteur. Les
  valeurs peuvent être **numériques** (`au moins 100`) ou **textuelles**
  (`commande = ring`).
- **Alors** — des actions : afficher une popup (simple, ou une de *vos*
  popups dessinées), incrémenter/remettre à zéro des compteurs, changer de
  scène OBS, afficher/masquer une source, lancer un média (les sélecteurs
  listent **vos vraies scènes et sources OBS**), appeler un webhook, annoncer
  sur Discord, inscrire un viewer au tirage, tirer un viewer au sort.

Les 20 widgets du catalogue (onglet Widgets) embarquent chacun un **flow prêt
à l'emploi** : le bouton *Éditer* le crée au premier clic, puis vous y ramène
toujours.

## Event — le tableau de bord

![Tableau de bord Event](assets/event.png)

**Jeux automatisés** — choisissez un de vos flows :

- **▶ Activer / ⏸ Désactiver** (un flow désactivé ne fait rien) ;
- **Éditer dans Flows** renvoie au builder ;
- des tuiles live montrent les **compteurs** du flow, les **participants du
  tirage** qui s'inscrivent en direct, le **dernier gagnant** et la
  **dernière popup**.

**Concours express** — un tirage ponctuel sans flow : tapez la !commande, la
durée, démarrez. Décompte, pseudos en direct, compteur, gagnant tiré au sort
annoncé à l'écran et sur l'overlay.
