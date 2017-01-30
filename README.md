#%RAML 0.8
baseUri: http://aras-poc-exp-web.cloudhub.io/api
title: Aras PoC Experience Mobile API
version: 1.0

traits:
  - client-id-required:
      queryParameters:
        client_id:
          type: string
        client_secret:
          type: string
        
/Cargo:
  /PickdownAndDebit:
    post:
      is: [client-id-required]
      body: 
        application/json:
          example: |
            {
              "KargoBarkod": "13364589898987751214545",
              "BirimKodu": "1236548988",
              "PersonelKodu": "03256655"
            }
      responses: 
        201:
          body: 
            application/json:
              example: |
                {
                  "IslemSonucu": true,
                  "KargoDurum": "Zimmetlendi"
                }
        400:
          body: 
            application/json:
              example: |
                {
                  "HataKodu" : "ERR_CODE",
                  "HataAciklama" : "ERR_DESC"
                }                  
