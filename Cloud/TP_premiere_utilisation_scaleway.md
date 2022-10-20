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
<br><br>

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

## Configuration instance base de données :

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

## Création instance serveur :

```
scw instance server create type=DEV1-S zone=nl-ams-1 image=ubuntu_jammy root-volume=l:20G name=scw-sleepy-lehmann ip=new project-id=77f6b02d-83f3-4ca6-9ee0-6a23ce1dcfa0
```

### Résumé de la configuration :
<br>

![img](https://i.imgur.com/TAiIA9D.png)

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
<br>
<br>

## Sauvegardes de la base :
<br>

### Graphiquement :
<br>
Dans un premier temps, nous avons réaliser une sauvegarde via la console.
<br>
<br>

![img](https://i.imgur.com/zJLSU7b.png)

![img](https://i.imgur.com/SU33cG4.png)

![img](https://i.imgur.com/mSu20eQ.png)

### Via le CLI :

Dans un second temps, on va faire la même opération mais sous forme CLI.

```
scw rdb backup create instance-id=c2691882-afe5-46f3-8c60-113fe8fd8c82 database-name=rdb name=sauvegarde region=fr-par
ID            446125eb-2b15-4967-8e4b-7a05472e87de
InstanceID    c2691882-afe5-46f3-8c60-113fe8fd8c82
DatabaseName  rdb
Name          sauvarge
Status        creating
CreatedAt     now
InstanceName  rdb-antoine-pierre
Region        fr-par
SameRegion    false
```

## Restauration de la base :

### Graphiquement :
<br>

![img](https://i.imgur.com/xIel69I.png)

![img](https://i.imgur.com/beqR9Ph.png)

<br>

### Via CLI :
<br>

Etant donné que l'on ne connait pas l'ID de restauration, il faut lister les différentes restaurations :

```
scw rdb backup list
ID                                    Name                                   Status  Instance ID                           Exported

446125eb-2b15-4967-8e4b-7a05472e87de  sauvarge                               ready   c2691882-afe5-46f3-8c60-113fe8fd8c82  true
```

Et voici la commande de restauration :

```
scw rdb backup restore 446125eb-2b15-4967-8e4b-7a05472e87de instance-id=c2691882-afe5-46f3-8c60-113fe8fd8c82 region=fr-par
ID                    446125eb-2b15-4967-8e4b-7a05472e87de
InstanceID            c2691882-afe5-46f3-8c60-113fe8fd8c82
DatabaseName          rdb
Name                  sauvarge
Status                restoring
Size                  840 B
CreatedAt             14 minutes ago
UpdatedAt             14 minutes ago
InstanceName          rdb-antoine-pierre
DownloadURL           https://s3.nl-ams.scw.cloud/65940610-0e5e-4a98-9306-568aa4eb3673/c2691882-afe5-46f3-8c60-113fe8fd8c82/446125eb-2b15-4967-8e4b-7a05472e87de.sql.gz?X-Amz-Algorithm=AWS4-HMAC-SHA256&-Amz-Credential=SCWBTK7RYYS1750DS37K%2F20221020%2Fnl-ams%2Fs3%2Faws4_request&X-Amz-Date=20221020T131043Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Signature=a51612ea02e1fb17289c1b39b4c54e5349ededcf38f52eaf42e5f5fd25961141
DownloadURLExpiresAt  23 hours from now
Region                fr-par
SameRegion            false
azachariades@GTD-TLS-LAP040:
```
<br>

On peut vérifier que la suppression et la restauration à bien fonctionné :
<br>
Cette capture d'écran illustre la suppression des données de la table user, dans laquelle  était contenu les données utilisateur, puis l'affichage de cette même table.
<br>
Ensuite, on restaure la table via la console et le CLI et la table remplie réapparait.
<br>
<br>

![img](https://i.imgur.com/4GshGOa.png)