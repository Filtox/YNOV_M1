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

<br><br>

## Configuration machine virtuelle :

<br>

| Moteur de base de données | Mysql |
| ------------- |:-------------:|
| Région | Paris |
|Configuration| Standalone (1 nœud) |
| Type de noeud | Développement : DB-DEV-S ( 2vCPU, 2 Go de mémoire, 1 noeud ) |
| Type de stockage et capacité | Stockage SSD local à 5 Go |
| Configuration de sauvegarde | Sauvegarde automatisé dans une région différente |
| Nom de l'instance | rdb-antoine-pierre |
| Prix | 0,01384 € par heure |


### Résumé de la configuration :
<br>

![img](https://i.imgur.com/7U3h3k6.png)

<br>

## Connexion à la base de données :
<br>

Dans un premier temps, il faut se connecter à la base de données afin de créer la base, la table et les données :

```
mysql -h 51.159.113.222 --port 8821 -p -u admin
```
Ensuite, on rentre le mot de passe et on est directement connecté.

On crée la base de données, la choisi puis on crée une table en indiquant les champs que l'on souhaite :

```
mysql> create database tp1
[12:16]
mysql> use tp1;
[12:17]
mysql> create table user (nom VARCHAR(100), prénom VARCHAR(100), mail varchar(250));
```

On insère ensuite les données :

```
mysql> insert into user (nom, prénom, mail) VALUES ('Zachariades', 'Antoine', 'pierre.michel@ynov.com
');
Query OK, 1 row affected (0,17 sec)

mysql> insert into user (nom, prénom, mail) VALUES ('marchal', 'frederic', 'frederic.marchall@ynov.co
m');
Query OK, 1 row affected (0,09 sec)

mysql> insert into user (nom, prénom, mail) VALUES ('banner', 'jerome', 'jerome.banner@ynov.com');
Query OK, 1 row affected (0,18 sec)

mysql> insert into user (nom, prénom, mail) VALUES ('roland', 'luc', 'roland.luc@ynov.com');
Query OK, 1 row affected (0,16 sec)

mysql> insert into user (nom, prénom, mail) VALUES ('berto', 'luc', 'luc.berto@ynov.com');
Query OK, 1 row affected (0,14 sec)

mysql> insert into user (nom, prénom, mail) VALUES ('mura', 'valentin', 'valentin.mura@ynov.com');
Query OK, 1 row affected (0,22 sec)
```

On peut voir que les données sont bien insérés avec la commande :
```
select * from user;
```
![img](https://i.imgur.com/quNKe31.png)

## Sauvegardes de la base :

### Graphiquement :

Dans un premier temps, nous avons réaliser une sauvegarde via la console.

![img](https://i.imgur.com/zJLSU7b.png)

![img](https://i.imgur.com/SU33cG4.png)

![img](https://i.imgur.com/mSu20eQ.png)

## Restauration de la base :