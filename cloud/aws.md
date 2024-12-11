---
title: Amazon Web Service | AWS
description: 
published: true
date: 2024-12-11T08:38:46.864Z
tags: 
editor: markdown
dateCreated: 2024-12-11T08:38:46.864Z
---

# Amazon Web Service
> Comment définir AWS ?
> 
> On pourrait commencer par dire qu’AWS est une plateforme de services cloud issue d’Amazon qui a fait ses débuts en 2006, l’idée principale fut d’isoler les différentes parties d’une infrastructure sous forme de composants pour l’OS.
{.is-info}


> A sa sortie, seul S3 et EC2 (stockage et instances que nous verrons plus tard) était disponible.
> Rapidement d’autres services ont été ajoutés et nous sommes maintenant aux alentours de 100 services Cloud offerts par la plateforme.
{.is-info}


![aws_services.png](/images/cloud/aws_service.png)

- **EC2** Elastic Compute Cloud
Il permet de gérer des serveurs en VM.
- **S3** Simple Storage Service
Est un service de stockage et de distribution de fichiers.
- **RDS** Relational Database Service
Permet de gérer des bases de données sans se préocuper de la partie logicielle.
- **VPC** Virtual Private Cloud
Permet de gérer ses réseaux privés.
- **IAM** Identity and Access Management
Permet de gérer les règles d'accès à votre AWS.
- Et bien d'autres ...

# Matryoshka Doll - Articulation d'AWS

![matryoshka-doll-png.png](/images/cloud/matryoshka-doll-png.png =50%x)

![aws_schema.png](/images/cloud/aws_schema.png)
# Prenons en main AWS

> AWS est gratuit la première année de votre inscription avec de nombreux services.

> Lors de l'inscription et pour éviter les fraudes, AWS vous demandera un numéro de carte bancaire.
{.is-warning}

![list_service.png](/images/cloud/list_service.png)

# EC2

> En cours de rédaction
{.is-warning}

EC2 est un service "Elastique", c'est-à-dire qu'il peut s'adapter à votre demande. 
Si vous souhaitez 2 serveurs au lieu de 1, allez y 😉 !

![ec2_2_1.png](/images/cloud/ec2_2_1.png)

1. La liste de toutes les ressources que vous utilisez actuellement.
2. La possiblité de lancer une nouvelle instance.
3. Toutes les options possibles avec EC2

Maintenons explorons un peu les services proposés par EC2. Des services qui evoluent constament (vous connaissez Amazon 🙄)


# Tabs {.tabset}
## Instances

Cette page affiche la liste des serveurs EC2 qui tournent 

![ec2_instance.png](/images/cloud/ec2_instance.png)

## Images

Les AMI (pas les collègues) (Amazon Machine Image) contient les images de vos instances.
Un peu comme l'utilisation de vos VM, on peut utiliser des images proposé par Amazon ou la communauté.


![image.png](/images/cloud/ec2_ami.png)

## Elastic Block Store

Affiche les volumes (disques) utilisés par l'ensemble de vos serveurs ainsi que les instantanés (les sauvegardes).

![ec2_ebs.png](/images/cloud/ec2_ebs.png))
## Réseau & Sécurité

- Les groupes de sécurité sont en quelques sortent les règles de pare-feu.

- IP élastiques sont les IP statiques attribués à vos instances

- Les paires de clés sont les clés RSA (publique et privée pour pouvoir se connecter en SSH)

![ec2_network_security.png](/images/cloud/ec2_network_security.png)

## Equilibrage de charge

L'équilibrage de charge permet, comme son nom indique, d'équilibrer la surchage d'un serveur vers d'autres serveurs.

## Auto Scaling

L'auto scaling permet d'ajuster automatiquement le nombre de serveur à utiliser selon le trafic et les règles définies.
  

#

# RDS

> En cours de rédaction
{.is-warning}

# S3
> En cours de rédaction
{.is-warning}