# Intégration Twitch

Retro Creator lit votre chat Twitch **sans clé, sans token, sans mot de
passe** : il rejoint votre chaîne anonymement, en lecture seule. Il ne peut
rien écrire — zéro risque pour votre chaîne.

## 1. Brancher sa chaîne

1. Ouvrez **Fichier → Paramètres…**
2. Dans la carte **Twitch**, tapez le nom de votre chaîne (ex. `ma_chaine`)
   et enregistrez.
3. L'entête de l'onglet Event confirme l'état :
   `🟣 chat Twitch connecté · #ma_chaine`.

Dès lors, chaque message du chat devient un événement du pipeline :

| Événement | Quand |
|---|---|
| **Message du chat Twitch** | un viewer écrit n'importe quoi |
| **!commande du chat Twitch** | un viewer tape une `!commande` (ex. `!ring 3`) |

Ils apparaissent dans la vue Live, dans le Moniteur, et déclenchent des
**Flows** comme n'importe quel événement de jeu. Le Designer gagne aussi des
données liées : *dernier viewer*, *dernier message*.

## 2. Lancer un concours de chat (zéro configuration)

![Tableau de bord Event](assets/event.png)

Ouvrez **Mode → Event** → **Concours express** :

1. Choisissez la **!commande** que les viewers doivent taper (le *slug*,
   ex. `!go`), la **durée**, et le message du gagnant.
2. Appuyez sur **▶ Démarrer la participation** — le décompte tourne, la liste
   des participants grossit en direct (une entrée par viewer, même s'il
   spamme), avec un compteur.
3. À zéro, un gagnant est tiré au sort : grande annonce à l'écran **et** popup
   sur votre overlay OBS.

## 3. Automatiser les concours avec les Flows (ex. Ring Lottery)

Pour les mécaniques récurrentes, tout se conditionne dans **Flows** et se
pilote depuis **Event** :

1. **Widgets → Ring Lottery Pop → Éditer** crée le scénario prêt à l'emploi :
      - chaque anneau ramassé en jeu incrémente un compteur ;
      - chaque viewer qui tape `!ring` entre dans le pool du tirage ;
      - à 100 anneaux, un gagnant est tiré et annoncé.
2. Changez le *slug* en éditant la condition **Si** de la règle
   (`commande du chat = ring` → mettez ce que vous voulez).
3. Dans **Event → Jeux automatisés**, sélectionnez le flow, appuyez sur
   **▶ Activer**, et suivez le tableau de bord : compteur d'anneaux,
   participants qui s'inscrivent en direct, dernier gagnant.

!!! note "Et écrire dans le chat ?"
    Annoncer les gagnants *dans le chat* (et pas seulement sur l'overlay)
    demande une autorisation Twitch (OAuth). C'est sur la feuille de route ;
    aujourd'hui toutes les annonces se font à l'écran — là où les viewers
    regardent, de toute façon.
