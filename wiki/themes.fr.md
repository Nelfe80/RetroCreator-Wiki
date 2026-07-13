# Thèmes

Un thème change tout le look d'un overlay — police, couleurs, fond des
panneaux, halo — **sans toucher à votre mise en page ni aux données**.
Changez de thème quand vous voulez : vos widgets continuent de fonctionner
exactement pareil.

## Choisir un thème

Dans le **Designer**, utilisez le sélecteur 🎨 de la barre d'outils. Le choix
est enregistré avec le document, et chaque source navigateur qui affiche cet
overlay suit au rechargement.

Cinq thèmes sont livrés avec Retro Creator :

| Thème | Ambiance |
|---|---|
| `arcade-neon` | défaut — panneaux sombres, accent doré, halo violet |
| `crt-classic` | terminal au phosphore vert, monospace ère cathodique |
| `neogeo-red` | borne d'arcade assumée, blanc chaud sur rouge profond |
| `minimal-broadcast` | épuré, faible contraste, plateau esport |
| `pixel-challenge` | pixel-party joueur, magenta sur violet |

L'édition Lite reste sur le thème par défaut ; le sélecteur se débloque avec
Pro.

## Comment un thème est conçu

Un thème, ce sont juste **cinq tokens de design** — aucune image, aucun
téléchargement, rien à licencier. Les polices sont des polices système, les
couleurs de simples valeurs CSS :

| Token | Ce qu'il pilote | Exemple |
|---|---|---|
| `font` | tous les textes | `"'Courier New',monospace"` |
| `text` | couleur du texte principal | `"#c8ffc8"` |
| `accent` | scores, valeurs, surlignages | `"#7CFC00"` |
| `panel` | fond des widgets | `"rgba(0,20,0,.88)"` |
| `shadow` | halo / ombre portée | `"0 0 6px rgba(124,252,0,.7)"` |

Comme un thème n'embarque **aucun média**, il pèse quelques centaines
d'octets et ne peut jamais casser un overlay : si un thème manque, le défaut
s'applique simplement.

## Créer votre propre thème

1. Ouvrez votre dossier de travail : `%APPDATA%\RetroCreator\workspace`.
2. Créez un dossier `themes` s'il n'existe pas.
3. Déposez un fichier JSON par thème, par exemple `themes\sunset-drive.json` :

```json
{
  "id": "sunset-drive",
  "name": "Sunset Drive",
  "tokens": {
    "font": "'Segoe UI',system-ui,sans-serif",
    "text": "#ffe9d6",
    "accent": "#ff7a45",
    "panel": "rgba(30,12,24,.88)",
    "shadow": "0 2px 12px rgba(255,122,69,.55)"
  }
}
```

4. Rechargez le Designer — **Sunset Drive** apparaît dans le sélecteur 🎨.

Bonnes pratiques :

- `id` est le nom technique (minuscules, tirets), unique ; `name` est ce que
  le sélecteur affiche.
- Gardez `panel` semi-transparent (`rgba(..., .7–.9)`) pour que le gameplay
  reste visible derrière l'overlay.
- Testez sur un fond chargé : c'est le token `shadow` qui garde le texte
  lisible.
- Un fichier invalide est ignoré en silence — impossible de casser vos
  overlays.

Les thèmes sont aussi la première brique des **packs de contenu** : un pack
peut livrer plusieurs thèmes (plus des vues et des widgets) qui s'installent
dans les mêmes dossiers du workspace.
