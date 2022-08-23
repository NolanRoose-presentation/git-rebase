# Collaborer avec git
### Vive les rebase !

--

### C'est quoi le besoin ?

Collaborer simplement avec git, avec un minimum d'effort.

--

### Sommaire

1. C'est quoi git ?
2. C'est quoi un rebase ? Et pourquoi c'est mieux ?
3. Configurer git
4. Créer un repo et le cloner
5. Faire son premier commit
6. Créer une pull request et merge
7. Récupérer les modifications depuis une branche
8. Faire ça à plusieurs mais bien
9. Quelques outils

---

# C'est quoi git ?

![Git gif](https://media.giphy.com/media/kH6CqYiquZawmU1HI6/giphy.gif)

--

Pour les ancêtres dans la sale, git c'est SVN mais en mieux.  
C'est un système de contrôle de version, le plus utilisé à ce jours,  
open source et développé à l'origine par [Linus Torvalds](https://fr.wikipedia.org/wiki/Linus_Torvalds).  
Il permet de versionner son code ou autres,  
mais aussi le partager de façon simple et efficace (quand on sait l'utiliser).

---

# C'est quoi un rebase ? Et pourquoi c'est mieux ?

![Alt Text](https://media.giphy.com/media/zQOmyYc8TXzSBfrTFb/giphy.gif)

--

## Tout d'abord, c'est quoi le merge ?

Merge est un processus de fusion de deux branches.  
Tout comme le rebase, mais avec un traitement différent :
- Créer un commit de merge
- La branche qu'on merge est prioritaire sur la branche de destination
- Tout les merges sont gardé dans l'historique
- Pas de gestion de conflit étape par étape
- ...

-- 

Les merges ne devraient jamais être utilisés pour récupérer  
des modifications dans une branche de feature.

![merge](/public/img/merge-2.png)

--

Mais pour introduire des modifications dans la branche principale oui.

![merge](/public/img/merge.png)

--

Exemple de merge :

```
git checkout master
git pull
git checkout feature
git merge master
git push
```

--

![mergegif](https://media.giphy.com/media/cFkiFMDg3iFoI/giphy.gif)

-- 

## C'est quoi un rebase ?

Le rebase est comme je l'ai déjà dit, un processus de fusion de deux branches.
Mais en moins violent :
- Mise en tampon des modifications de la branche de destination
- Application des modifications la branche de source
- Application des modifications de la branche de destination commit par commit
- Meilleures gestions des conflits
- Pas de commit de merge superflus



