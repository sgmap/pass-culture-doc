### Fournisseurs

Ceci décrit l'API à implémenter par les partenaires techniques de Pass Culture qui souhaitent fournir des stocks.

Pass Culture s'identifie auprès des partenaires techniques via un certificat client SSL. La clé publique est publiée sur le site Pass Culture, et les partenaires sont prévnus à l'avance en cas de changement de clé via notre liste de diffusion email "partenaires techniques".

#### Les Stocks [/stocks/{siret}]

+ Parameters

  + siret (optional, string) - Identifiant "siret" du commerce.
  + after (optional, string) - pagination : EAN13 de la dernière entrée traitée (le dernier de la page précédente)
  + limit (optional, integer) - pagination : nombre maximum d'entrées à renvoyer pour cette requête
  + modifiedSince (optional, string) - date au format 2012-04-23T18:25:43.511Z. L'API ne renvoie que les stocks modifiés depuis cette date

###### Lister les stocks disponible pour un établissement [GET /stocks/12345678901234?after=1978212345681&limit=2]

Les références renvoyées sont les EAN13 du code barre du produit. Le prix est optionnel pour les livres (prix unique).

+ Request

+ Response 200 (application/json)

    + Body

            [
              {
                  "ref": "1978212345680",
                  "available": 27,
                  "price": 22.99
              },
              {
                  "ref": "1978212345682",
                  "available": 3
              }
            ]

+ Response 400 (application/json)

    + Body

            [
              {
                 "text": "Siret invalide"
              }
            ]