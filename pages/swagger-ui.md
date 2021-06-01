# Swagger UI lietošana

Adrese : https://services.proofit.lv/APUS/swagger-ui.html

APUS izmanto [Swagger UI](https://swagger.io/tools/swagger-ui/) bibliotēku, lai pārlūkā attēlotu pieejamos webservice galapunktus (endpoints).

## Swagger UI
1.	Attēlo pieejamos webservice galapunktus;
2.	Attēlo webservice pieprasījumu datu struktūru;
3.	Attēlo webservice atbildes datu struktūru un iespējamos HTTP kļūdu kodus;
4.	Ļauj izsaukt APUS webservice, norādot parametrus;
5.	Izgūt veiktos pieprasījumus CURL formātā.

## APUS webservice izsaukšana, lietojot Swagger UI

* Sadaļā “authentication” atver endpoint “/rest/login” un nospiež pogu “Try it out”.

![Authentification](../assets/swagger-ui/Picture1.png)

* Aizpilda lauku “userName” un “apiPassword”

![Fields](../assets/swagger-ui/Picture2.png)

* Spiež “Execute”

![Execute](../assets/swagger-ui/Picture3.png)

* Gala rezultātā iegūst autentifikācijai lietojamo JWT token.

![Token](../assets/swagger-ui/Picture4.png)

* Nokopē iegūtā token vērtību un nospiež “Authorize” lapas augšpusē

![Authorize](../assets/swagger-ui/Picture5.png)

* Token vērtību ievada laukā “Value” un nospiež “Authorize”

![Value](../assets/swagger-ui/Picture6.png)

* Pēc veiksmīgas autentifikācijas, nospiež “Close”

![Close](../assets/swagger-ui/Picture7.png)

Swagger UI ir veiksmīgi autentificēts un ir iespējams izsaukt citus webservice endpoint, ievadot lietotāju saskarnē obligātos parametrus un saņemot atbildes.
