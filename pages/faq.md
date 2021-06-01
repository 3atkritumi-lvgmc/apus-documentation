# Biežāk uzdotie jautājumi (BUJ)

## 1. “Neizdodas izsaukt nevienu citu servisu kā autentifikāciju – citiem servisiem atgriež “Unauthorized”. Kas ir nepareizi?”

Šajā gadījumā iesākām no sākuma izsaukt APUS lietojot Swagger UI. Apraksts, kā lietot Swagger UI, lai izsauktu APUS ir pieejams [šeit](./swagger-ui.md). Kad ir izdevies veiksmīgi izsaukt APUS, lietojot Swagger UI, tad iespējams iegūt skriptu, kas tādu pašu izsaukumu var veikt, lietojot [cURL](https://curl.se/) bibliotēku. Tajā ir norādītas gan izsaukuma adreses, “header” vērtības (autentifikācijai), kuras var nebūt tik uzskatāms, lietojot kādu citu REST klientu (piemēram, Postman).

## 2. “Vai ir pieejams uzņēmumu izveidošanas/labošanas serviss?”

Šobrīd jauna uzņēmuma izveidošanas/eksistējoša uzņēmuma labošanas serviss nav paredzēts (stājoties spēkā Ministru kabineta noteikumiem Nr. 113 ar 2021. gada 1.jūliju). Iespējams, ka šāds serviss tiks ieviests uz 2021. gada 1. janvāri, bet šobrīd (2021. gada 18. maijā) šādas izmaiņas nav pasūtītas.

## 3. “Cik bieži būtu vēlams sinhronizēt pavadzīmju datus ar APUS?”

Lai arī MK noteikumi Nr.113 nosaka, ka pavadzīmes dati jāiesūta APUS [ne retāk kā reizi piecās darbdienās](https://likumi.lv/ta/id/321151#p31), mēs tomēr ieteiktu sinhronizēties pie katrām pavadzīmes izmaiņām un iegūt sarakstu ar jaunākajām citu uzņēmumu veidotajām pavadzīmēm vismaz reizi dienā. Veidojot daudz pieprasījumus īsā laika sprīdī tiks lieki noslogots APUS serveris un tas var traucēt sistēmas kopējai darbībai.

## 4. “Vai nepieciešams iegūt jaunu JWT token pie katra webservice izsaukuma?”

JWT token derīguma termiņš ir 8 stundas un būtu nepieciešams to izmantot vairākas reizes, lai lieki nenoslogotu APUS serveri ar autentifikācijas pieprasījumiem. Klienta sistēmas JWT token vērtību var vai nu saglabāt atmiņā uz noteiktu laiku (“caching”) vai datubāzē. Ja tiks izmantots JWT token ar beigušos derīguma termiņu, tad APUS atgriezīs, ka pieprasījums nav autentificēts.

## 5. “APUS pavadzīmes pieprasījums atgriež ļoti daudz laukus. Vai tiešām tie visi ir jāievada iesūtot pavadzīmi?”

Nē – GET pieprasījums atgriež papildus paskaidrojošus datus, bet visi lauki nav jānorāda iesūtot datus APUS. Precīzāku lauku specifikāciju skatīt tabulā [“Pavadzīmes lauku sasaiste (UI vs. REST)”](./invoice-field-mapping.md) – kolonnā “Jāuzstāda JSON”.

## 6. “Atjaunojot datus pavadzīmē, APUS atgriež kļūdu “ENTITY_ALREADY_UPDATED”. Kāpēc?”

Datu versionēšanai tiek izmantots pavadzīmes lauks “updateDate”. Ja šis lauks APUS satur vērtību, kas ir lielāka par to, kas norādīta pavadzīmes saglabāšanas pieprasījumā, tad tiks atgriezts šāds kļūdas paziņojums. Korekta darbību secība, līdz ar to būtu, pirms dati tiek atjaunoti APUS, izgūt jaunāko pavadzīmes versiju no APUS un salīdzināt, vai “updateDate” vērtības sakrīt. Ja nē, tad atjaunot Jūsu sistēmā pavadzīmes datus un tikai tad nosūtīt APUS.

## 7. “Kādā formātā ir datumi jānodod APUS?”

APUS webservice izmanto [ISO-8601](https://en.wikipedia.org/wiki/ISO_8601) datuma formātu. Tas ļauj apstrādāt gan datumu, gan laiku, gan laika joslu. Piemērs – "2021-04-29T19:57:56.132+03:00". Tas nozīmē, ka iesūtot datus APUS, Jums ir jānorāda korektā Latvijas laika josla, lai nerastos problēmas ar datumu nobīdi. Ja laika josla netiek norādīta, tad tiek pieņemts, ka tiek izmantota UTC laika josla.

## 8. “Vai ir iespējams ievadīt jaunu fizisku personu?”

Jā – tas ir iespējams. Iesūtīt pavadzīmes datus, ja norāda pilnu informāciju par fizisku personu, bet šāda persona nav saglabāta APUS, tad saglabājot pavadzīmi, tiks saglabāta arī fiziskā persona.
Piemērs:
```
"sender": {
    "legalType": "FIZ",
    "person": {
        "firstName" : "Jānis",
        "lastName" : "Jansons",
        "personCode" : "111111-11111",
        "birthDate" : "2021-04-29T19:57:56.132+03:00",
        "birthPlace" : "Rīga",
        "email" : janis.jansons@test.test,
        "phone" : "12341234"
    },
    "personResponsibleForWasteShipmentName": "Jānis Jansons",
    "shipmentDate": "2021-04-29T19:57:56.132+03:00"
}
```
## 9. “Kā iespējams sinhronizēt APUS pavadzīmes atkritumu rindas (“content”)?”

Pēc pavadzīmes iesūtīšanas, APUS katrai rindai piešķir unikālu ID, kuri tiek atgriezti pieprasījuma atbildē. Līdz ar to pavadzīmes rindām jāsaglabā papildus ir gan lauks “id”, gan lauks “updateDate” un sūtot labojumus, šie abi lauki jānodod APUS.



