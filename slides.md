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

![merge](img/merge-3.png)

--

Sinon on va se retrouver avec ça et bon courage pour s'y retrouver.

![merge](img/merge-2.png)

--

Mais pour introduire des modifications dans la branche principale oui.  
Seulement si vous êtes à jours avec la branche de destination.

![merge](img/merge-4.png)

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

En conclusion, on ne peut pas se passer de merges.  
Mais seulement dans un seul sens, de la branche feature vers la develop.

--

## C'est quoi un rebase ?

Le rebase est comme je l'ai déjà dit, un processus de fusion de deux branches.  
Mais en moins violent :  
- Mise en tampon des modifications de la branche de destination
- Application des modifications la branche de source
- Application des modifications de la branche de destination commit par commit
- Meilleures gestions des conflits
- Pas de commit de merge superflus

--

Une illustration de ce que fait un rebase

![rebase](img/rebase.png)

--

Voici comment récupérer correctement les modifications de la branche mère de votre feature.

![rebase](img/rebase-2.png)

--

Exemple de rebase sans conflits :

```
git checkout master
git pull --rebase
git checkout feature
git rebase master
git push -f
```

--

### Les conflits

Avec le merge la question ne se pose pas, la branche source écrase tout ce quelle peut.  
Pour le reste, vous devez tout résoudre en même temps.  
  
Pour le rebase, c'est différent, cela ce fait par N étapes.  
N étant le nombre de commits de la branche de destination.  
Ce qui permet d'avoir le control sur les conflits de chaques commits.  
Cependant, attention vous devez résoudre que les conflits et rien de plus.  
Au risque de multiplier les conflits.  

--

Pour chaque commit en conflit, il faut résoudre le conflit, et ensuite appliquer les modifications.

```
git add .
git rebase --continue
```

--

## En cas de problème lors d'un rebase  
# Arrêtez tout ! Et recommencez !

```
git rebase --abort
```

--

### Qui suit réellement ?  

Avez-vous remarqué une différence dans les examples de merge/rebase ?  
Si oui laquel ?

--

## Git pull / git pull --rebase

- `git pull` => fait un merge  
- `git pull --rebase` => fait un rebase

--

![pull](img/pull.png)
