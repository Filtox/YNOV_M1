# Calcul des coûts d’une Infrastructure as a Service en fonction de différents Cloud Provider
### Pierre Da Silva

<br>

**Pour chacune des infrastructures décrites ci-dessous calculer le coût sur 4 cloud providers (AWS, GCP, Azure et Scaleway). Faire apparaître le détail des calculs et comparer les résultats finaux.**

*Avant de démarrer vous devez récupérer les informations concernant les coûts des différents services. Si des éléments ne sont pas donnés dans les énoncés vous choisissez systématiquement l’option la moins chère !*
<br>
<br>


## Infrastructure n°1 :

● 1 serveur avec les ressources suivantes :

○ 16 Go de RAM minimum

○ 4 vCPU

○ 100 Go de stockage disque

<br>

| Azure | AWS | GCP | Scaleway|
| ------------- |:-------------:| -------:| -------:|
| 1 instance à 4 processeurs virtuels, 16 Go de RAM, stockage de 100 Go : 163,57 $ | 1 instance à 4 processeurs virtuels, 16 Go de RAM, stockage de 100 Go : 67,40 $ | 1 instance à 4 processeurs virtuels, 16 Go de RAM, stockage de 100 Go : 130,27 $ | 1 instance à 4 processeurs virtuels, 16 Go de RAM, stockage de 100 Go : 83,11 $ |
| **Total : 163,57 $** | **Total : 67,40 $** | **Total : 130,27 $** | **Total : 83,11 $** |

<br>
<br>

## Infrastructure n°2 :

● 6 serveurs avec les ressources suivantes :

○ 6 Go de RAM minimum

○ 3 vCPU

○ 20 Go de stockage disque par serveur

● Particularité : 3 serveurs sont éteints la nuit de 22h à 6h du matin

<br>

| Azure | AWS | GCP | Scaleway|
| ------------- |:-------------:| -------:| -------:|
| 3 instances à 4 cœurs, 8 Go de RAM, stockage de 40 Go pendant 1 mois : 486,23 $ | 3 instances à 3 cœurs, 6 Go de RAM, stockage de 20 Go pendant 1 mois : 214,79 $ | 3 instances à 4 cœurs, 6 Go de RAM, stockage de 20 Go pendant 1 mois : 297,13 $ | 3 instances à 4 processeurs virtuels, 16 Go de RAM, stockage de 20 Go pendant 1 mois : 245,52  $ |
|3 instances à 4 cœurs, 8 Go de RAM, stockage de 40 Go pendant 490 heures : 326,39 $ | 3 instances à 3 cœurs, 6 Go de RAM, stockage de 20 Go pendant 490 heures : 146,46 $ | 3 instances à 4 cœurs, 6 Go de RAM, stockage de 20 Go pendant 490 heures : 219,51 $ | 3 instances à 4 processeurs virtuels, 16 Go de RAM, stockage de 20 Go pendant 490 heures : 163,68  $
| **Total : 812,62 $** | **Total : 361,25 $** | **Total : 516,64 $** | **Total : 409,20 $** |

<br>
<br>

## Infrastructure n°3 :

● 3 serveurs avec les ressources suivantes :

○ 4 Go de RAM minimum

○ 2 vCPU

○ 50 Go de stockage disque par serveur

● 1 load balancer qui répartit 5 Mb/s de données équitablement vers les 3 serveurs ci-dessus

● 1 service de base de données managé

○ 8 Go de RAM minimum

○ 2 vCPU

<br>

| Azure | AWS | GCP | Scaleway|
| ------------- |:-------------:| -------:| -------:|
| 3 instances à 2 processeurs virtuels, 4 Go de RAM, stockage 75 de Go : 202,63 $ | 3 instances à 2 processeurs virtuels, 4 Go de RAM, stockage 50 de Go : 291,74 $ | 3 instances à 2 processeurs virtuels, 4 Go de RAM, stockage 50 de Go : 162,58 $ | 3 instances à 2 processeurs virtuels, 4 Go de RAM, stockage 50 de Go : 124,665 $ |
| 1 Load balancer avec 1 règle : 23,25 $ | 1 Load balancer : 33,12 $ | 1 Load balancer : 22,28 $ | 1 Load balancer : 10,416 $ |
| 1 base de données Azure pour MySQL à 2 vCore et 10 Go de stockage : 63,21 $ | 1 base de données à 2 vCore et 10 Go de stockage : 69,30 $ |    1 base de données à 2 vCPU, 8 Go de RAM et 150 Go de stockage : 150,99 $ | 1 base de données à 2 vCPU et 10 Go de stockage : 7,6 $ |
| **Total : 289,09 $** | **Total : 394,16 $** |   **Total : 335,85 $** | **Total :** 142,681 $ |
