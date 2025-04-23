---
name: Lightning Network Daemon sur Linux
description: Installer et tourner Lightning Network Daemon sur Linux
---

![cover-lightning-network-daemon](assets/cover.webp)

Le réseau Lightning est la deuxième couche de  l'implémentation Bitcoin qui permet à ce dernier de prendre des dimensions fulugrentes notamment grâce à la rapidité et aux faibles coûts de transactions proposées.

Dans ce tutoriel nous allons installer l'implémentation  Lightning Network Daemon sur notre machine Linux ( Distribution Ubuntu 24.04).  

# Qu'est ce que c'est Lightning Network Daemon ?  

Lightning Network Daemon est une implémentation complète en Go du réseau Lightning. Il a été créé par la société Lightning Labs et vous permet de tourner une instance complète d'un noeud Lightning sur votre machine. 
Autrement dit, avec cette implémentation, vous pouvez : 

- **Interagir avec le réseau Lightning** : Grâce aux lignes de commandes, vous pouvez performer des processus de création d'un portefeuille Lightning , la gestions des canneaux et des routes de paiements, vous avez une multitude de possibilités directement depuis le terminal de votre machine.  
- **Relier un noeud Bitcoin distant ou votre propre instance de Bitcoin Core** : LND vous permet de relier une instance de Bitcoin et de vous en servir comme back-end pour votre utilisation, pour tourner donc cette implémentation, vous n'aurez pas besoin de tourner obligatoirement une instance de Bitcoin Core sur votre machine 


https://planb.network/fr/tutorials/node/bitcoin/bitcoin-core-linux-568c13a6-8746-4d63-8e95-f4a61c5ae0ed


Nous avons deux possibilités pour tourner une instance de l'implémentation LND sur notre machine. Nous pouvons configurer l'environnement sur notre machine même afin de pouvoir agir en local ou installer LND à partir d'un conteneur Docker.  

# Installer LND à partir du code source

## Pré-requis
LND étant écrit en Go, vous devez vous assurer d'avoir l'environnement GoLang sur notre machine Linux.  

- **Installer les dépendances utiles :**
La commande ci-dessous vous permettra d'installer sur votre machines des outils nécéssaires pour le bon fonctionnnement de LND, vous aurez entre autres une installation de `Git` , un outil versionning et de `make` qui pourra éxecuter et construire l'implémentation LND à partir du code source 

```
sudo apt install -y build-essential git make
```

- **Installer GoLang sur votre machine Linux**
```
sudo apt install -y golang-go
```
- **Vérifier l'installation**
```
go version
```
## Cloner le dépôt [Github de LND](https://github.com/lightningnetwork/lnd)

Vous allez utiliser git pour avoir une copie du code source de LND en locale sur votre machine 
```
git clone https://github.com/lightningnetwork/lnd.git
```

## Construire et installer 

L'outil `make` préalablement installé vous permettra de construire un exécutable à partir du code source LND et pouvoir procéder à votre installation.  

```
# Acceder au repertoire clonné 
cd lnd 

# construire LND
make 
# installer LND
make install
```
- **Vérifier votre installation**

Pour vous assurez que tout s'est bien déroulé , en exécutant cette commande, vous devriez obtenir la version de LND que vous tournez actuellement. 

```
lnd --version
```

# Configurer Lightning Network Daemon 

La configuration d'un noeud Lightning LND est similaire à  celle de Bitcoin, elle se fait dans un fichier de configuration contenant tout les paramètres de votre noeud. Pour cela , à la racine de votre machine vous pouvez créer un dossier caché `.lnd` puis créer votre fichier de configuration `lnd.conf`.  

```
mkdir -p ~/.lnd

cd ~/.lnd

# Fichier de configuration
touch lnd.conf
```

Dans le fichier de configuration vous pouvez parametrer votre noeud LND

```
noseedbackup=1
debuglevel=debug
bitcoin.node=bitcoind

[Bitcoind]
bitcoind.rpcuser=lightning
bitcoind.rpcuser=lightning
bitcoind.zmqpubrawblock=
bitcoind.zmqpubrawtx=

```

# Vérifier son installation avec LND 

Vous souhaitez probablement vous assurer que le processus a bien été réussi et que vous vous synchronisez au réseau Lightning pour avoir les informations à jour sur votre noeud.  

Pour demarrer l'implementation LND , rien de plus simple , dans votre terminal, tapez la commande : 
```
lnd
```



Vous êtes donc à la fin de ce tutoriel , n'hesitez pas à poser vos questions et à reporter les problèmes que vous rencontrez tout au long de votre isntallation dans [notre groupe Telegram dédié aux contributions](https://t.me/PlanBNetwork_ContentBuilder).



