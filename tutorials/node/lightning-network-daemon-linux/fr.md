---
name: Lightning Network Daemon sur Linux
description: Installer et tourner Lightning Network Daemon sur Linux
---

![cover-lightning-network-daemon](assets/cover.webp)

Le réseau Lightning est la deuxième couche de  l'implémentation Bitcoin qui permet à ce dernier de prendre des dimensions fulgurantes notamment grâce à la rapidité et aux faibles coûts de transactions proposées.

Dans ce tutoriel nous allons installer l'implémentation  Lightning Network Daemon sur notre machine Linux ( Distribution Ubuntu 24.04).  

# Qu'est ce que c'est Lightning Network Daemon ?  

Lightning Network Daemon est une implémentation complète en Go du réseau Lightning. Il a été créé par la société Lightning Labs et vous permet de tourner une instance complète d'un noeud Lightning sur votre machine. 
Autrement dit, avec cette implémentation, vous pouvez : 

- **Interagir avec le réseau Lightning** : Grâce aux lignes de commandes, vous pouvez performer des processus de création d'un portefeuille Lightning , la gestion des canaux et des routes de paiements, vous avez une multitude de possibilités directement depuis le terminal de votre machine.  
- **Relier un noeud Bitcoin distant ou votre propre instance de Bitcoin Core** : LND vous permet de relier une instance de Bitcoin et de vous en servir comme back-end pour votre utilisation, pour tourner donc cette implémentation, vous n'aurez pas besoin de tourner obligatoirement une instance de Bitcoin Core sur votre machine 


https://planb.network/fr/tutorials/node/bitcoin/bitcoin-core-linux-568c13a6-8746-4d63-8e95-f4a61c5ae0ed


Nous avons deux possibilités pour tourner une instance de l'implémentation LND sur notre machine. Nous pouvons configurer l'environnement sur notre machine même afin de pouvoir agir en local ou installer LND à partir d'un conteneur Docker.  

# Installer LND à partir du code source

## Pré-requis
LND étant écrit en Go, vous devez vous assurer d'avoir l'environnement GoLang sur notre machine Linux.  

- **Prérequis Matériel :**
Pour une expérience fluide et sans accro, votre machine devra avoir la capacité nécessaire pour tourner votre noeud lightning LND.  

Il vous faudra : 
1. **8 Go de RAM** pour une fluidité optimale, 
2. **Un processeur multi-core (quad-core ou plus)** pour gérer efficacement les actions de votre noeud, 
3. **Au moins 5 Go d'espace disque** pour un mode réduit (pruned node) et 1To pour tourner Bitcoin Core (facultatif si vous utilisez un noeud distant)

- **Installer les dépendances utiles :**
La commande ci-dessous vous permettra d'installer sur votre machines des outils nécessaires pour le bon fonctionnement de LND, vous aurez entre autres une installation de `Git` , un outil versionning et de `make` qui pourra exécuter et construire l'implémentation LND à partir du code source 

```bash
sudo apt install -y build-essential git make
```

- **Installer GoLang sur votre machine Linux**
```bash
sudo apt install -y golang-go
```
- **Vérifier l'installation**
```bash
go version
```
## Cloner le dépôt [Github de LND](https://github.com/lightningnetwork/lnd)

Vous allez utiliser git pour avoir une copie du code source de LND en locale sur votre machine 
```bash
git clone https://github.com/lightningnetwork/lnd.git
```

## Construire et installer 

L'outil `make` préalablement installé vous permettra de construire un exécutable à partir du code source LND et pouvoir procéder à votre installation.  

```bash
# Acceder au repertoire clonné 
cd lnd 

# construire LND
make 
# installer LND
make install
```
- **Vérifier votre installation**

Pour vous assurez que tout s'est bien déroulé , en exécutant cette commande, vous devriez obtenir la version de LND que vous tournez actuellement. 

```bash
lnd --version
```

- **Maintenance et Mise à jour** 

```bash
cd lnd
git pull
make clean && make && make install
```

# Configurer Lightning Network Daemon 

La configuration d'un noeud Lightning LND est similaire à  celle de Bitcoin, elle se fait dans un fichier de configuration contenant tout les paramètres de votre noeud. Pour cela , à la racine de votre machine vous pouvez créer un dossier caché `.lnd` puis créer votre fichier de configuration `lnd.conf`.  

```bash
mkdir -p ~/.lnd

cd ~/.lnd

# Fichier de configuration
touch lnd.conf
```

Dans le fichier de configuration vous pouvez paramétrer votre noeud LND

```
noseedbackup=1
debuglevel=debug

[Bitcoin]
bitcoin.active=1
bitcoin.mainnet=1
bitcoin.node=bitcoind

[Bitcoind]
bitcoind.rpcuser=lightning
bitcoind.rpcpassword=lightning
bitcoind.zmqpubrawblock=tcp://127.0.0.1:28332
bitcoind.zmqpubrawtx=tcp://127.0.0.1:28333

```

- **Comprendre votre configuration**

Il est important pour vous de comprendre la configuration minimale que vous devez avoir pour une installation correcte et complète de votre noeud LND.  

En vous basant sur le contenu du fichier `~/.lnd/lnd.conf`, voici le détails des champs: 

1. **noseedbackup** : Permet de choisir si vous souhaitez que LND effectue des sauvegardes automatiques de vos portefeuilles.  

2. **debuglevel** : Permet de définir le niveau de details des erreurs et des journaux en cas d'erreurs survenues lors d'une action.  

3. **bitcoin.active**: Permet d'indiquer à LND de fonctionner en tant que noeud Bitcoin et d'interagir avec le réseau Bitcoin.

4. **bitcoin.mainnet**: Spécifie à LND de se connnecter au réseau principal de Bitcoin (mainnet)

5. **bitcoin.node** : Spécifie à LND le type de noeud Bitcoin auquel il devra se connecter de se connecter

6. **bitcoin.rpcuser**  et **bitcoin.rpcpassword**: Représentent
respectivement les identifiants ( utilisateur , mot de passe)  pour se connecter à votre noeud Bitcoin 

7. **bitcoind.zmqpubrawblock** et **bitcoind.zmqpubrawtx**: Définit respectivement les endpoints ZeroMQ pour recevoir les notifications à propos de nouveaux blocs et des nouvelles transactions présentes sur le réseau Bitcoin


# Vérifier son installation avec LND 

Vous souhaitez probablement vous assurer que le processus a bien été réussi et que vous vous synchronisez au réseau Lightning pour avoir les informations à jour sur votre noeud.  

Pour demarrer l'implementation LND , rien de plus simple , dans votre terminal, tapez la commande : 
```bash
lnd getinfo
```

# Bonnes pratiques et sécurité de votre noeud LND. 
La sécurité est primordiale lors de l'utilisation d'un noeud Bitcoin/ Lightning. Voici quelques points pour renforcer la sécurité de votre installation : 

- Conservez votre `seed phrase` dans un endroit sécurisé et hors ligne.  

- Faites des sauvegardes régulières du fichier `~/.lnd/channel.backup`
- Ne desactivez pas `noseedbackup` dans votre fichier de configuration
- Gardez votre système à jour. 

# Dépannage Courant
## Problèmes fréquents
- **Erreur de connexion à bitcoind**: Vérifiez vos identifiants RPC
- **Synchronisation bloquée**: Vérifiez votre connexion internet
- **Erreur de permission**: Vérifiez les droits du dossier ~/.lnd


Vous êtes donc à la fin de ce tutoriel , n'hesitez pas à poser vos questions et à reporter les problèmes que vous rencontrez tout au long de votre installation dans [notre groupe Telegram dédié aux contributions](https://t.me/PlanBNetwork_ContentBuilder).




