# Adreses (objekti) un to papildināšana

**N.B.! - Šobrīd jauna objekta iesūtīšana ir pieejama tikai [APUS testa vidē](https://services.proofit.lv/APUS)!**

Objekts (facility) - APUS kontekstā ir nosūtīšanas vai saņemšanas adrese, kas ir reģistrēta organizācijai vai fiziskai personai. 
APUS šī datu struktūra tiek uzturēta komplicētāka kā vienkāršs adreses lauks, jo:
* Vienā adresē var atrasties vairāki uzņēmumi - tāpēc nepieciešams objekta nosaukuma lauks, kurā var precīzi aprakstīt, piemēram, noliktavu, no kuras ir nākuši atkritumi.
* Tekstuāls adreses lauks neļauj veikt datu agregāciju, piemēram, pa novadiem, ko ļauj veikt adrešu sadalīšana, izmantojot administratīvo teritoriju un teritoriālo vienību klasifikatoru.

## Objektu datu iegūšana

| Resurss                                   | HTTP metode   | Swagger URL                                                              |
| ---                                       | ---           | ---                                                                      |
| /rest/ws/facilities/{facilityRequestType} | GET           | https://services.proofit.lv/APUS/swagger-ui.html#/ws-facility-controller |

**facilityRequestType** iespējamās vērtības :
* senders - nosūtīšanas objekti
* receivers - saņemšanas objekti

## Jauna objekta pievienošana

| Resurss              | HTTP metode   | Swagger URL                                                              |
| ---                  | ---           | ---                                                                      |
| /rest/ws/facilities/ | POST          | https://services.proofit.lv/APUS/swagger-ui.html#/ws-facility-controller |

### Objektu lauki

| Lauks                 | Obligāts | Apraksts                                                                                                                                 |
| ---                   | ---      | ---                                                                                                                                      |
| name                  | Jā       | Objekta nosaukums, kas paskaidro adreses datus (piemēram, norāda konkrētu noliktavas ēku)                                                |
| code                  | Nē       | Šo lauku ģenerēs APUS. References lauks, ko vēlāk izmantot pavadzīmju iesūtīšanā                                                         |
| typeCode              | Jā       | Nosūtītāja vai saņēmēja tips - skatīt **/rest/ws/classifiers/facility-type**                                                             |
| description           | Nē       | Papildus lauks paskaidrojumiem                                                                                                           |
| fullAddress           | Jā       | Adrese - norādīta tekstuālā veidā, piemēram, "Latvijas Republika, Rīga, Baznīcas iela 19/23"                                             | 
| atvkCode*             | Daļēji   | ATVK klasifikatora kods. Obligāts, ja organization.id norādīta Latvijas Republikā reģistrēta organizācija                                |
| organization          | Daļēji   | Jānorāda **organization.id** vai arī **person.personCode**                                                                               |
| person                | Daļēji   | Jānorāda **organization.id** vai arī **person.personCode**                                                                               |
| addressRegistryCode** | Nē       | Valsts zemes dienesta adrešu reģistra ieraksta kods - ja Jūsu sistēma izmanto VZD adrešu reģistra, tad variet šo kodu norādīt jau šobrīd |
| email                 | Nē       |                                                                                                                                          |
| phone                 | Nē       |                                                                                                                                          |

[*] - ATVK iespējamo vērtību iegūšanu skatīt nodaļā "ATVK klasifikators"

[**] - Ir iespējams, ka sākot ar 2022. gada 1. janvāri APUS sistēmā nebūs vairs iespējams ievadīt lauku "fullAddress" - tikai lauku "addressRegistryCode", tāpēc variet sākt pielāgot Jūsu informācijas sistēmas jau šobrīd.

### ATVK klasifikators
APUS sistēma balstās uz [administratīvo teritoriju un teritoriālo vienību klasifikatoru](https://www.csb.gov.lv/lv/statistika/klasifikacijas/atvk).
Kā references lauks, tiek izmantots ATVK kods.
Lai atvieglotu ATVK izmantošanu, APUS izveidots galapunkts, kurā var meklēt nepieciešamos ATVK ierakstus.

| Resurss       | HTTP metode | Swagger URL                                                              |
| ---           | ---         | ---                                                                      |
| /rest/ws/atvk | GET         | https://services.proofit.lv/APUS/swagger-ui.html#/web-service-controller |

## Esoša objekta labošana
Šobrīd ir iespējams labot tikai WS izmantotā lietotāja piesaistīto organizāciju objektus. Mēģinot labot eksistējošu objektu tiks atgriezta kļūda
```json
[
    {
        "messageText": "CURRENT_USER_MUST_BE_INVOLVED", 
        "field": "relationPersonId"
    }
]
```
Ja iesūtītajā objektā (adresē) ir bijusi kļūda, tad iesakām izveidot jaunu objektu un samainīt attiecīgajā pavadzīmē, kur nepieciešams.

## Izmaiņas (braking changes)
Jāņem vērā, ka ir datu struktūras izmaiņas, kas var salauzt esošo funkcionalitāti:
* FacilityPublic datu struktūras lauks "address" jaunajā versijā saucas "fullAddress" - ja, piemēram, iesūtot pavadzīmi objektā tiks ievietots "facility" datu struktūra ar lauku "address", tad būs datu serializācijas kļūda.
Iesakām, iesūtot pavadzīmi, "facility" blokiem norādīt tikai lauku "code" un nenorādīt pārējos laukus.
