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

2. **Verifie le flux AVANT de l'afficher.** Il est valide seulement si TOUTES ces conditions
   sont vraies :

   - la lecture a reussi et le contenu est du JSON ;
   - `schema_version` vaut `1` ;
   - `contract_version` vaut `veille-contract-1` ;
   - `complete` vaut `true` ;
   - `item_count` est **exactement** le nombre d'entrees de `items` ;
   - `items` n'est pas vide ;
   - `generated_at` **et** `data_through` ont moins de **2 heures**.

3. **Si une seule de ces conditions est fausse**, reponds exactement une ligne, et rien d'autre :

```
Flux indisponible ou perime : <la condition qui a echoue>.
```

   Puis arrete-toi. N'affiche aucun item. Ne rejoue rien de memoire. Ne remplace pas par une
   recherche web. Ne propose pas d'alternative.

4. **Filtre.** Si l'utilisateur a ecrit un ou plusieurs mots apres la commande, ne garde que les
   entrees dont `tags` contient un de ces mots (comparaison insensible a la casse et aux accents).
   Sinon, garde tout.

5. **Rends** une ligne d'entete, puis une puce par entree, rien d'autre :

```
Veille du <generated_at en format court : 23 aout, 14h07> — <N> incident(s)<, filtre : tag>
```

Puis, pour chaque entree retenue :

```
- **<title>** — <summary, tel quel> `<tags separes par des espaces>`
  <si victims est non vide : Victimes : les noms separes par des virgules, + "et N autres" si victims_more>
  <une ligne par entree de sources : [<source_id>](<url>)>
```

## Regles

- **Ce que tu affiches vient du JSON, integralement.** N'invente jamais un titre, un resume, un
  lien, un tag ni une victime. Ne resume pas le resume. Ne complete pas un champ vide.
- **N'affiche jamais une URL qui n'est pas dans `sources[].url`.**
- **Court.** Pas d'introduction, pas de conclusion, pas d'analyse, pas de recommandation, pas
  d'evaluation de la situation de l'utilisateur.
- **Si le filtre ne retient rien**, dis-le en une ligne, avec la liste des tags presents dans le
  flux du jour.
- `family_count` est le nombre de familles de sources independantes qui ont couvert l'incident,
  pas un nombre d'articles. Ne l'affiche que si l'utilisateur le demande.
