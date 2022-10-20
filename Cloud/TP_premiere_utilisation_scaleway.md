# TP première utilisation de Scaleway

### **Pour chacun des cas, mettre en place l'infrastructure à l’aide de votre compte et des services Scaleway. Vous effectuerez la mise en place à l’aide de la console dans un premier temps puis via le CLI Scaleway dans un second temps.**
<br>

### Important :
* Après avoir fait valider que votre cas est fonctionnel, penser à supprimer toutes les ressources de ce cas !
* Les ressources non éteintes et inutiles coûtent de l’argent et démontreront la non maîtrise de la compétence associée !
* Pour chaque cas, vous ajouterez au compte-rendu les commande Scaleway (scw) associé à la mise en place

***Avant de démarrer vous devez me fournir sur Teams les adresses mail de votre groupe de TP afin que je vous ajoute sur Scaleway***


### Compétences mises en oeuvre dans ce TP

Utiliser les fonctionnalités du Cloud pour mettre en service, dimensionner et distribuer une infrastructure de calcul
<br>
Utiliser les services et les outils permettant d'automatiser la mise en service et le déploiement de l’infrastructure
<br>
Optimiser l’efficacité d’une infrastructure Cloud afin d’améliorer les performances, diminuer les coûts et éviter le gaspillage
<br>

## Cas n°1:
Vous installez une base de données à l’aide du service correspondant sur Scaleway.
A l’aide d’une machine dans le cloud Scaleway (la moins chère possible), vous vous
connectez à cette base de données, vous y créez une base avec une table (user: nom,
prénom, mail).
<br>
Ajoutez 5 ou 6 user dans la table associée. Faire une sauvegarde de la base de données via Scaleway (dans la console puis via la ligne de commande scw). Supprimer les utilisateurs. Restaurer la base de données à l’aide de la sauvegarde faite précédemment (dans la console puis via la ligne de commande scw).
<br>

Le **compte rendu** de l’exercice doit être **déposé sur moodle par chacun des membres du groupe** au format **Markdown le 26 octobre 2022 au plus tard.**

![z link](https://imgur.com/a/NqGyWWY)


type : mysql 
ville : paris
standalone 
DB-DEV-S 
2Go 
1 cpu 
1 noeud 
0,0136 
stockage ssd local 5 Go
sauvegarde dans une région différente automatisé

admin
Ynov31000!
nom db : rdb-antoine-pierre


```
mysql -h 51.159.113.222 --port 8821 -p -u admin
```