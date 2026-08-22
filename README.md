# Veille

Tape `/veille` dans Claude, reçois un condensé court des dernières fuites de données, leaks et
incidents sécurité. C'est tout.

Rien à installer sur ton ordinateur. Pas de serveur, pas de clé, pas de compte à créer.

## Avant de commencer

Il te faut Claude avec un compte **Pro** (ou plus), sur le site ou l'application bureau.

Un réglage à activer une seule fois : **Paramètres → Capacités →
« Exécution de code cloud et création de fichiers »**. Sans lui, les plugins ne se chargent pas.

## Installer — 1 minute

1. **Paramètres → Plugins** (colonne de gauche, tout en bas, sous « Personnaliser »).
2. En haut à droite, bouton **Ajouter** → **Ajouter une place de marché**.
3. Dans la fenêtre qui s'ouvre, choisis **Ajouter depuis un dépôt**
   (« Synchroniser une marketplace de plugins depuis un dépôt GitHub ou une URL git »).
4. Un avertissement rouge s'affiche : il dit qu'Anthropic ne contrôle pas les plugins des
   marketplaces. C'est normal, il apparaît pour tout le monde.
5. Sous **URL**, clique **Sélectionner un dépôt**, puis colle cette adresse dans le champ de
   recherche :

   ```
   https://github.com/Coyottejay/veille
   ```

   > La liste déroulante ne montre que **tes** dépôts GitHub. Le mien n'y sera pas :
   > colle l'adresse, ne la cherche pas dans la liste.

6. Valide. La marketplace **veille** apparaît, avec une carte **Veille** par Jay.
7. Clique dessus pour l'installer. Un message confirme :
   « Veille est installé et prêt à être utilisé. »

## Utiliser

Dans une conversation :

```
/veille
```

Pour ne voir qu'un sujet :

```
/veille phishing
```

Les tags changent avec l'actualité. Si ton filtre ne trouve rien, Claude te dit lesquels
existent aujourd'hui.

## Se mettre à jour

Rien à faire. Le contenu est lu à chaque appel — tu as toujours la dernière version.

Très rarement, si l'outil lui-même change, il faut deux clics :

1. **Paramètres → Plugins**, onglet **Personnel**, sur la pastille **veille** → **⋯** →
   **Rechercher des mises à jour**.
2. Puis, sur la fiche du plugin **Veille**, le bouton **Mettre à jour**.

L'ordre compte : le premier clic ne suffit pas, il prévient seulement Claude qu'une version
existe. Le second l'installe.

## Ce que c'est, ce que ce n'est pas

Un partage entre potes. Pas un produit, pas un service, aucune garantie. Les liens mènent aux
sources : va voir par toi-même.
