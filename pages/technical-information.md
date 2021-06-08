# Tehniskā informācija

Webservice ir izveidots RESTful tehnoloģijā ar JSON kā datu apmaiņas formātu. Autentifikācijai tiek izmantoti JWT žetoni (tālāk token).

Tehniskais resursu apraksts ir pieejams adresē: [https://services.proofit.lv/APUS/swagger-ui.html](https://services.proofit.lv/APUS/swagger-ui.html). Šajā aprakstā ir pieejama informācija par pieejamajiem resursiem, datu tipiem un izmantotajām HTTP metodēm.
Vairāk par Swagger UI lietošanu lasīt [šeit](./swagger-ui)

Testa vides WEB adrese ir : [https://services.proofit.lv/APUS/](https://services.proofit.lv/APUS/)

Testa vides webservice adrese ir : [https://services.proofit.lv/APUS/rest/](https://services.proofit.lv/APUS/rest/)

Lai izstrādātu sistēmu integrāciju, izstrādes laikā lūdzam izmantot testa vidi.

Lai varētu veikt korektu datu sinhronizāciju, APUS izmanto lauku “updateDate” kā versijas lauku. Ja tiek iesūtīti dati ar “updateDate” lauku, kas nav vienāds ar to, kas glabājas APUS, tad šādu datu iesūtīšana atgriezīs kļūdu un dati netiks saglabāti.
