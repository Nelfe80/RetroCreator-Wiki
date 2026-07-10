# Bien démarrer

Retro Creator fonctionne aux côtés de [RetroBat](https://www.retrobat.org/) et
transforme les données réelles de vos parties en overlays et automatisations de
stream. Voici le chemin complet, de zéro à l'overlay en direct.

## 1. Lancer et connecter

1. Démarrez **RetroBat** (EmulationStation), avec le plugin APIExpose actif.
2. Lancez **Retro Creator**. L'application s'ouvre sur la vue **Live** avec un
   seul bouton : **Connecter**.
3. Cliquez **Connecter** — l'état en bas de fenêtre passe au vert
   (`Connecté`). Dès lors, chaque jeu parcouru ou lancé alimente l'application.

!!! tip "Pas de RetroBat sous la main ?"
    Cliquez **Essayer le mode démo** sous le bouton Connecter : une session de
    jeu simulée traverse tout le pipeline pour explorer chaque vue.

L'interface s'organise autour du menu **Mode** :

| Mode | À quoi il sert |
|---|---|
| **Live** | Le pouls de votre stream — chaque événement de jeu orbite autour du logo du jeu en cours. |
| **Designer** | Composer vos vues d'overlay, popups et composants. |
| **Flows** | Conditionner vos automatisations : *Quand… Si… Alors…* |
| **Event** | Le tableau de bord : activer vos jeux, lancer des concours de chat. |
| **Widgets** | Le catalogue de mécaniques de stream prêtes à l'emploi et de templates de vues. |

Le bouton **Moniteur** de la barre d'état déplie un terminal avec le journal
brut des événements (6 lignes) — pratique pour vérifier ce que les jeux
émettent réellement.

## 2. Composer une vue dans le Designer

![Designer](assets/designer.png)

1. Ouvrez **Mode → Designer**.
2. Piochez des éléments dans la palette de gauche — groupés par usage
   (**Média**, **Données du jeu**, **Variables**, **Popups**, **Formes**) et
   déjà pré-réglés : *Titre du jeu*, *Année*, *Note ★*, *Marquee*, *Boxart*,
   *Logo système*…
3. Tout suit une logique de calques : réordonnez par **glisser-déposer**,
   groupez en dossiers, masquez (👁) ou verrouillez (🔒), renommez.
4. Les propriétés sont en trois groupes repliables : **Calque** (position,
   taille, fond, transition de mise à jour), **Contenu** (donnée liée, texte
   composé), **Style** (police — système ou vos fichiers —, taille, couleur,
   alignement, ombre portée, contour).
5. L'**aperçu live** est actif par défaut : le canvas affiche les vraies
   données et les vrais visuels du jeu en cours.

## 3. Envoyer vers votre logiciel de stream

Cliquez **Ajouter à OBS** dans l'entête du Designer : la vue est enregistrée
puis poussée comme source navigateur nommée `RC - <nom de la vue>` dans la
scène courante (mot de passe obs-websocket requis, voir
[Paramètres](#5-parametres)). Après le premier envoi, le bouton devient
**Mettre à jour dans OBS**.

Tout logiciel de stream sachant afficher une page web convient : la vue est une
simple URL locale (`http://127.0.0.1:19780/overlay/<vue>`), à coller
manuellement dans Streamlabs, Meld Studio, etc.

## 4. Automatiser avec les Flows

Ouvrez **Mode → Flows** et décrivez vos réactions en phrases simples :

> **Quand** *vie perdue* → **Alors** *afficher une popup* « 💥 {game} frappe encore ! »

Les conditions acceptent des nombres (*compteur au moins 100*) et du texte
(*commande du chat = `ring`*). Les actions couvrent les popups (simple ou une
popup dessinée par vous), les compteurs, le pilotage OBS
(scène/source/média), les webhooks, Discord — et les sélecteurs de scènes et
de sources listent **votre vrai contenu OBS**.

## 5. Paramètres

**Fichier → Paramètres…** ouvre une fenêtre pour :

- **Twitch** — le nom de votre chaîne. C'est *tout* ce qu'il faut pour lire
  votre chat (anonyme, lecture seule, aucune clé) : voir
  [Intégration Twitch](twitch.md).
- **OBS Studio** — le mot de passe obs-websocket (Outils → Paramètres du
  serveur WebSocket dans OBS). Stocké chiffré, jamais affiché.
- **Mes médias** — un dossier à vous (images/vidéos), exposé au Designer comme
  sources `user:`.
- **Discord** — un webhook par défaut pour les annonces.

Le **thème clair/sombre** se bascule via **Fichier → Thème clair/sombre**.

## 6. Sauvegarder son travail

**Fichier → Sauvegarder** écrit toute votre configuration (vues + flows) dans
un fichier projet `.rct` unique ; **Fichier → Ouvrir…** la restaure — idéal
pour les sauvegardes ou pour transporter un setup complet de stream d'une
machine à l'autre.
