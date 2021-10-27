# Flow de souscription

## Contexte

Le flow de souscription est une étape d'acquisition client qui entre en jeu lorsque le propriétaire de l'animal a déjà connaissance de l'entreprise XXXX, il s'agit d'un prospect chaud se trouvant déjà sur le site internet que l'on souhaite convertir.

Ce projet part du principe qu'il n'y a aucune solution existante permettant de souscrire à XXXXX mis à part les contacter par mail ou par téléphone. Si une solution existante était présente, une étape importante serait de faire un état des lieux des résultats obtenus avec celle-ci et de quantifier les améliorations souhaitées après la refonte afin de jauger la réussite du projet.

## Identification du besoin

En tant qu'entreprise de services d'assurance, le besoin principal est de connecter XXXX aux propriétaires de chiens et chats afin de leur offrir un contrat adapté.
Le besoin se traduit par la concrétisation d'un lien entre XXXX et le propriétaire afin de lui offrir par la suite un devis et un contrat d'assurance.

XXXX doit collecter les données requises aux calculs des primes d'assurance et à la création d'une fiche client, d'un devis et d'un contrat.

Le prospect doit pouvoir aisément communiquer à XXXX ses informations afin d'être accompagné jusqu'à l'obtention du service.

## Problèmes / contraintes identifiés

- La phase de récupération de données peut créer du churn si l'expérience utilisateur est mauvaise
- Les informations données peuvent être erronées et/ou manquantes
- Un propriétaire peut avoir plusieurs animaux à assurer
- La collecte de données est régie par la loi de protection des données personnelles
- La structure des données évoluera dans le temps

## Critères influençant le choix de la stack technique

- **Légèreté du package:** on évite d'alourdir notre application avec des lib énormes dont on utilise qu'une toute petite partie.
- **Popularité:** on choisi de préférence une techno connue et largement utilisée pour profiter de la communauté permettant de signaler et corriger de nombreux problèmes. Egalement, les sites comme StackOverflow auront certainement du contenu intéressant et nous permettant de passer les obstacles aisément.
- **Maintenue à jour:** une techno à une durée de vie et même si elle a été populaire un temps, son état actuel importe beaucoup car l'environnement dans laquelle on va l'intégrer aura lui aussi évolué et de nouveaux conflits pourront apparaitre.
- **Documentation:** une techno doit être correctement documentée pour faciliter la team tech à la prendre en main.
- **Homogénéité:** Privilégier un language simple ou déjà existant pour l'équipe (facilite le recrutement par la suite et évite l'obligation d'avoir des profils rares).
- **Scalabilité à faible coût:** Privilégier les services à faible coût, voire gratuit, permettant de grandir petit à petit sans avoir a récrire ces même services une fois la charge importante atteinte.

## Version 0.1.0 - Minimum Viable Product

Mise en place d'un Google Form accessible depuis le site XXXX permettant d'alimenter un Google Sheet et d'effectuer des envois de devis manuellement.

Cette solution très simpliste nous permettra d'avoir un Time To Market extrêmement faible, des retours d'expérience et une source d'acquisition client fonctionnelle dès les premiers jours.

Stack technique:

- React (existant)
- Google Forms / Sheets

Stories:

- En tant qu'utilisateur, je peux accéder en un clic à partir du site web XXXX à un formulaire de souscription.
- En tant qu'utilisateur, je peux transmettre en moins de 5min toutes les informations requises à XXXX.
- En tant qu'employé XXXX, je peux concevoir et envoyer un devis à partir des données du formulaire.

## Version 1.0.0

Mise en place d'un formulaire intégré à l'application web XXXX permettant de nourrir une base de données automatiquement.
L'envoi du devis, de l'autorisation de prélèvement et du contrat définitif restent manuels.

Stack technique:

- React (existant) + lib. **React Hook Form** (formulaire)
- **AWS API Gateway / Lambda / DynamoDb** : architecture serverless permettant de créer un CRUD sur les informations des clients lors de leur souscription. Création de la route POST sur Gateway afin de trigger la fonction lambda correspondante ainsi que la GET pour exploiter les données.

Stories:

- En tant qu'utilisateur, je peux accéder directement (en un clic) sur l'application web XXXX à un formulaire de souscription.
- En tant qu'utilisateur, je peux transmettre toutes les informations requises à XXXX.
- En tant qu'employé XXXX, je peux concevoir et envoyer un devis à partir des données extraites depuis DynamoDb.

## Version 1.1.0

Mise en place d'un espace client permettant de consulter l'état de sa demande et de modifier ses informations.
L'envoi du devis, de l'autorisation de prélèvement et du contrat définitif restent manuels.

Stack technique:

- React (existant) + lib. React Hook Form (formulaire)
- **AWS API Gateway / Lambda / DynamoDb / Cognito / Step Functions** : Création/maj des routes POST, GET, PUT, DELETE sur Gateway afin de trigger les fonctions lambda correspondantes. Création d'un compte utilisateur via lambda et cognito

Stories:

- En tant qu'utilisateur, je peux accéder directement sur l'application web XXXX à un formulaire de souscription.
- En tant qu'utilisateur, je peux transmettre toutes les informations requises à XXXX.
- En tant qu'utilisateur, je peux me logger et mettre à jour mes informations personnelles avec des champs modifiables.
- En tant qu'utilisateur, je peux consulter l'état de ma demande de devis.
- En tant qu'employé XXXX, je peux concevoir et envoyer un devis à partir des données du dashboard admin de l'application XXXX.
- En tant qu'employé XXXX, je peux mettre à jour le statut de la demande de devis du client en un clic.

## Version 1.2.0

Après complétion du formulaire, les calculs de prime sont automatisés et le devis est automatiquement envoyé à l'adresse mail du client. La suite du process reste manuelle.

Stack technique:

- React (existant) + lib. React Hook Form (formulaire) + Json Web Token
- AWS API Gateway / Lambda / DynamoDb / Cognito / Step Functions / **SES**:  ajout de Step Functions et du service SES pour orchestrer les nouvelles fonctions lambda (calcul des primes, création du devis pdf, envoi du devis par mail) lors d'un POST et d'un PUT.

Stories:

- En tant qu'utilisateur, je peux accéder directement sur l'application web XXXX à un formulaire de souscription.
- En tant qu'utilisateur, je peux transmettre toutes les informations requises à XXXX.
- En tant qu'utilisateur, je peux recevoir automatiquement un devis par mail suite à la complétion du formulaire.
- En tant qu'utilisateur, je peux mettre à jour mes informations personnelles et générer un second envoi de devis par mail.

## Version 1.3.0

Le devis est accessible sur l'espace client et peut être accepté/signé directement depuis l'application. La suite du process reste manuelle.

Stack technique:

- React (existant) + React Hook Form (formulaire) + Json Web Token
- AWS API Gateway / Lambda / DynamoDb / Cognito / Step Functions / SES :
- DocuSign: intégration à l'app, génération du document via une nouvelle fonction AWS lambda qui remplace celle qui créait le devis au format pdf

Stories:

- En tant qu'utilisateur, je peux accéder directement sur l'application web XXXX à un formulaire de souscription.
- En tant qu'utilisateur, je peux transmettre toutes les informations requises à XXXX.
- En tant qu'utilisateur, je peux recevoir automatiquement un devis par mail suite à la complétion du formulaire.
- En tant qu'utilisateur, je peux mettre à jour mes informations personnelles et générer un second envoi de devis par mail.
- En tant qu'utilisateur, je peux consulter et accepté (signer) mon devis directement depuis l'application XXXX.

## Version 1.4.0

Après validation du devis par le client, l'enregistrement d'un moyen de paiement est disponible et son succès génère l'envoi du contrat définitif au client ainsi qu'une confirmation de paiement.

Stack technique:

- React (existant) + lib. React Hook Form (formulaire) + Json Web Token
- AWS API Gateway / Lambda / DynamoDb / Cognito / Step Functions / SES :
- DocuSign
- Stripe

Ajout des fonctions lambda qui trigger suite au paiement réussi permettant l'envoi du contrat définitif.

Stories:

- En tant qu'utilisateur, je peux accéder directement sur l'application web XXXX à un formulaire de souscription.
- En tant qu'utilisateur, je peux transmettre toutes les informations requises à XXXX.
- En tant qu'utilisateur, je peux recevoir automatiquement un devis par mail suite à la complétion du formulaire.
- En tant qu'utilisateur, je peux mettre à jour mes informations personnelles et générer un second envoi de devis par mail.
- En tant qu'utilisateur, je peux consulter et accepté (signer) mon devis directement depuis l'application XXXX.
- En tant qu'utilisateur, je peux enregistrer un moyen de paiement après acceptation du devis.
- En tant qu'utilisateur, je reçois une confirmation de paiement et une copie de contrat définitif.

![Flow Dalma.jpg](Flow%20de%20souscription%20bc1329c7401b4e86bd988a04ee53c85b/Flow_Dalma.jpg)

[Retroplanning](Flow%20de%20souscription%20bc1329c7401b4e86bd988a04ee53c85b/Retroplanning%20825e25588bd2467fafd1c2e669203f7b.csv)