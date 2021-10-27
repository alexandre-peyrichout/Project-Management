# Sprint 5: Version 1.3.0

Assign: Alexandre Peyrichout
Date: November 8, 2021 → November 12, 2021
Status: Not started

## Version 1.3.0

Le devis est accessible sur l'espace client et peut être accepté/signé directement depuis l'application. La suite du process reste manuelle.

Stack technique:

- React (existant) + React Hook Form (formulaire)
- AWS API Gateway / Lambda / DynamoDb / Step Functions :
- DocuSign: intégration à l'app, génération du document via une nouvelle fonction AWS lambda qui remplace celle qui créait le devis au format pdf

Stories:

- En tant qu'utilisateur, je peux accéder directement sur l'application web Dalma à un formulaire de souscription.
- En tant qu'utilisateur, je peux transmettre toutes les informations requises à Dalma.
- En tant qu'utilisateur, je peux recevoir automatiquement un devis par mail suite à la complétion du formulaire.
- En tant qu'utilisateur, je peux mettre à jour mes informations personnelles et générer un second envoi de devis par mail.
- En tant qu'utilisateur, je peux consulter et accepté (signer) mon devis directement depuis l'application Dalma.