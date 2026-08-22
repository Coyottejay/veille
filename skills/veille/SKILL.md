---
name: veille
description: Rend un condense court de la veille securite de Jay - fuites de donnees, leaks, incidents cyber, vulnerabilites. A utiliser quand l'utilisateur tape /veille, demande "la veille", "les dernieres fuites", "quoi de neuf en securite", ou donne un tag a filtrer apres la commande.
---

# Veille securite

## Ce qu'il faut faire

1. Lis cette URL avec l'outil de lecture web (web fetch) :

```
https://coyottejay.github.io/veille/feed/latest.json
```

2. C'est un JSON : `generated_at` (date de publication du flux) et `items[]`, chaque item ayant
   `title`, `summary`, `url`, `tags`.

3. **Filtre.** Si l'utilisateur a ecrit un ou plusieurs mots apres la commande, ne garde que les
   items dont `tags` contient un de ces mots (comparaison insensible a la casse et aux accents).
   Sinon, garde tout.

4. **Rends.** Une ligne d'entete, puis une puce par item, rien d'autre :

```
Veille du <generated_at en format court : 22 aout, 15h36> — <N> item(s)<, filtre : tag si filtre>
```

Puis, pour chaque item retenu :

```
- **<title>** — <summary, une phrase, tel quel> [lien](<url>) `<tags>`
```

## Regles

- **Court.** Pas d'introduction, pas de conclusion, pas d'analyse, pas de recommandation, pas
  d'evaluation de la situation de l'utilisateur. Le contenu du flux, rien de plus.
- **N'invente jamais un item.** Tout ce que tu affiches vient du JSON. Si tu n'as pas lu le JSON,
  tu n'as rien a afficher.
- **Si la lecture de l'URL echoue**, reponds exactement une ligne :
  `Flux injoignable : <la raison>.` Ne remplace pas par une recherche web, ne rejoue pas de
  memoire, ne propose pas d'alternative.
- **Si le filtre ne retient rien**, dis-le en une ligne avec la liste des tags qui existent dans
  le flux du jour.
- Si `generated_at` a plus de 48 h, ajoute a la fin une seule ligne : `(flux pas rafraichi depuis
  <duree>)`.
