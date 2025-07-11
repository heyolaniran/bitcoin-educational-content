 
![cover](assets/cover.webp)
 
Depuis son déploiement en 2009, le système de cash électronique pair à pair de Bitcoin a connu une croissance exponentielle donnant vie à des solutions qui lui permettent aujourd'hui d'être un système que nous pouvons utiliser instantanément dans nos actions quotidiennes notamment au travers du Lightning Network.
Cependant un problème majeur subsiste entre les couches du protocole Bitcoin : l'interopérabilité fluide. Il était impératif de trouver une solution qui permettait de faire des transactions entre les différentes couches du protocole pour pouvoir exploiter le plein potentiel de Bitcoin. C'est de ce besoin qu'est né en 2019, Boltz, un pont qui relie plusieurs couches de Bitcoin.
 
## Qu'est-ce que Boltz ?
 
[Boltz](https://boltz.exchange) est une plateforme non-custodial idéale pour toute personne qui souhaite faire des transactions entre les couches du protocole Bitcoin :
- **On Chain** : La chaîne principale de Bitcoin où les transactions sont confirmées toutes les 10 minutes en moyenne, les frais de transaction sont souvent élevés ,ce qui ne répond pas nécessairement aux besoins des utilisateurs.
- **Lightning Network** : La surcouche de Bitcoin permettant d'effectuer des paiements instantanés à des frais bas permettant d'utiliser bitcoin pour les paiements quotidiens.
- **Liquid Network** : une surcouche de Bitcoin créée par Blockstream permettant de faire des transactions rapides, confidentielles et aussi d'utiliser d'autres instruments financiers sur la base de Bitcoin
- **RockStock** : Une solution qui permet le développement de contrats intelligents sur le protocole Bitcoin.
 
![layers](assets/fr/01.webp)
 
Cela dit, l'importance de l'interopérabilité entre ces couches est principalement de fournir la flexibilité qu'il faut à un utilisateur pour exploiter tout ce que Bitcoin à offrir.
 
Boltz utilise les échanges atomiques qui sont des échanges directs, sans intermédiaire, entre différentes couches en utilisant des scripts Bitcoin pour garantir la sécurité et l'exécution simultanée des transactions.
 
Un échange atomique fonctionne avec des contrats [HTLC](https://planb.network/fr/resources/glossary/htlc) (Hashed Timelock Contract). Dans ce type de contrat, le montant est « verrouillé » dans un canal bidirectionnel et une restriction temporelle est introduite, de sorte que si la transaction n'est pas achevée dans un certain délai, le solde revient au déposant. C'est ce mécanisme qu'utilise la plateforme Boltz.
 
## Vos premiers échanges avec Boltz
 
Boltz est une plateforme web non dépositaire et ne requérant aucune information personnelle de votre part. Boltz possède une interface minimaliste, fluide qui vous permet d'initier vos échanges en moins d'une minute.
 
![boltz](assets/fr/02.webp)
 
Une fois sur la plateforme, vous pouvez créer des échanges atomiques entre les différentes couches du protocole Bitcoin.
 
![home](assets/fr/03.webp)
 
Vous y verrez le minimum et le maximum de satoshis (la plus petite unité de bitcoin) que vous pouvez échanger via Boltz incluant les frais réseaux et le pourcentage prélevé par Boltz compris entre 0,1% et 0,5%.
 
![fees](assets/fr/04.webp)
 
Sélectionnez ensuite la couche à partir de laquelle vous souhaitez faire un échange atomique puis sélectionnez la couche sur laquelle vous souhaitez recevoir les bitcoins.
 
![couches](assets/fr/05.webp)
 
Dans notre tutoriel nous nous focaliserons sur l'échange atomique de la couche principale vers le Lightning Network.
Vous pouvez configurer l'unité de base de vos échanges en choisissant entre les options :
- Bitcoin
- satoshis.
 
![unités](assets/fr/06.webp)
 
Une fois vos configurations de base terminées, insérez le montant de votre échange atomique puis créez une facture Lightning du montant équivalent ou insérez plus simplement votre LNURL.
 
https://planb.network/tutorials/wallet/mobile/aqua-8e6d7dd3-8c03-45cc-90dd-fe3899a7d125
 
https://planb.network/fr/tutorials/wallet/mobile/blitz-wallet-794bdac4-1af4-49d5-9ea5-abb8228ca196
 
![swap](assets/fr/07.webp)
 
Par mesure de sécurité, veuillez vérifier les paramètres de votre échange atomique pour exporter les clés de secours liées à votre échange.
Sur l'icône **Paramètres**, téléchargez la clé de secours et veuillez sauvegarder le fichier convenablement.
 
![settings](assets/fr/08.webp)
 
![rescue-key](assets/fr/09.webp)
 
Ce fichier contient les 12 mots clés du portefeuille associée à vos échanges atomiques. Nous vous recommandons de suivre les directives de notre tutoriel sur la sauvegarde des mots de récupération afin de préserver durablement cette information capitale.
 
https://planb.network/tutorials/wallet/backup/backup-mnemonic-22c0ddfa-fb9f-4e3a-96f9-46e2a7954270
 
Cliquez ensuite sur le bouton **Créer l'échange atomique** puis procédez au paiement du montant indiqué.
 
![payment](assets/fr/10.webp)
 
https://planb.network/tutorials/wallet/mobile/blue-wallet-2f4093da-6d03-4f26-8378-b9351d0dbc90
 
https://planb.network/fr/tutorials/wallet/mobile/blink-7ea5f5a4-e728-4ff9-b3f9-cf20aa6fc2bd
 
Une fois votre paiement effectué puis confirmé, vous recevez automatiquement l'équivalent sur votre portefeuille Lightning.
 
Dans le menu **Remboursement**, retrouvez l'historique de vos échanges atomiques pour identifier l'échange sur lequel vous souhaitez vous faire rembourser. Vous pouvez également importer une historique d'échanges que vous avez par exemple effectué sur un autre appareil en utilisant le fichier de clé secours qui est associé à ces échanges.
 
![refund](assets/fr/11.webp)
 
Dans le menu **Historique**, vous pouvez télécharger une historique plus détaillée de l'historique associée à votre clé secours en cliquant sur le bouton **Sauvegarde**.
 
![backup](assets/fr/12.webp)
 
⚠️ Veuillez ne pas divulguer ce fichier également car il contient toutes les informations associées à vos transactions et la clé de secours liées à ces transactions.
 
Boltz vous propose plus de confidentialité via sa plateforme Onion basée sur le réseau Tor. Effectuez des échanges atomiques en tout anonymat en cliquant sur le menu **Onion** après avoir activé la navigation Tor dans votre navigateur.
 
![onion](assets/fr/13.webp)
 
https://planb.network/tutorials/computer-security/communication/a847e83c-31ef-4439-9eac-742b255129bb
 
Vous connaissez désormais Boltz, une plateforme d'échange unique en son genre qui effectue l'interopérabilité entre différentes couches du protocole Bitcoin. Nous vous recommandons de découvrir également Bitfinex, l'une des premières plateformes d'échange pair à pair de Bitcoin.
 
https://planb.network/tutorials/exchange/centralized/bitfinex-dc306d39-bd96-4ab9-a278-a322316716db