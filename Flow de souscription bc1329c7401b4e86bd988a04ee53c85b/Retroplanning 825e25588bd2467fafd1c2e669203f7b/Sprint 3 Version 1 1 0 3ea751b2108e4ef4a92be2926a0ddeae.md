# Sprint 3: Version 1.1.0

Assign: Alexandre Peyrichout
Date: October 25, 2021 → October 29, 2021
Status: Not started

## Version 1.1.0

Mise en place d'un espace client permettant de consulter l'état de sa demande et de modifier ses informations.
L'envoi du devis, de l'autorisation de prélèvement et du contrat définitif restent manuels.

Stack technique:

- React (existant) + lib. React Hook Form (formulaire)
- **AWS API Gateway / Lambda / DynamoDb** : Création/maj des routes GET, PUT, DELETE sur Gateway afin de trigger les 3 fonctions lambda correspondantes.

Stories:

- En tant qu'utilisateur, je peux accéder directement sur l'application web Dalma à un formulaire de souscription.
- En tant qu'utilisateur, je peux transmettre toutes les informations requises à Dalma.
- En tant qu'utilisateur, je peux mettre à jour mes informations personnelles.
- En tant qu'utilisateur, je peux consulter l'état de ma demande de devis.
- En tant qu'employé Dalma, je peux concevoir et envoyer un devis à partir des données du dashboard admin de l'application Dalma.
- En tant qu'employé Dalma, je peux mettre à jour le statut de la demande de devis du client.