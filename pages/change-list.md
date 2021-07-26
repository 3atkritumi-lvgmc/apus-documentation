# Izmaiņas (changelist)

* 2021.07.26 - produkcijas vide
    * Pievienots jauna objekta (adreses) ievadīšanas webserviss. Vairāk skatīt [šeit](./facility-address.md)
    * Excel eksporta kolonnu tipi salaboti (skaitļu kolonnas tiek atpazīstas kā skaitļi)

* 2021.07.12 (tikai testa vide)
    * Pievienots jauna objekta (adreses) ievadīšanas webserviss. Vairāk skatīt [šeit](./facility-address.md)
    
    
* 2021.06.22
    * Izveidots jauna uzņēmuma ievadīšanas/ eksistējoša uzņēmuma labošanas webserviss, kā arī izmainīta uzņēmuma datu objekta struktūra webservisā (skatīt vairāk [Swagger-UI](https://services.proofit.lv/APUS/swagger-ui.html#/ws-organization-controller))
    * Atbilstoši MK noteikumiem ir pievienota iespēja kā nosūtītāju un pārvadātāju norādīt "Latvijas iedzīvotāji" - vairāk skatīt [šeit](./inhabitants-of-latvia.md)
    * Webservisa pavadzīmju saraksta GET serviss papildināts ar jaunu parametru "unsignedInvoices", kas ļauj vieglāk atlasīt pavadzīmes, kas uzņēmumam ir jāapstiprina
    * Webservisa pavadzīmju saraksta GET serviss papildināts ar parametriem, lai atbilstu atlases iespējām, kas ir lietotāju saskarnē
    * Facility (objektu/adrešu) GET serviss atgriež arī adreses lauku
    * Klasifikatoru GET serviss papildināts ar "Transportlīdzekļa veids" - "type-of-transport"
    * Pavadzīmes saskaņošanas blokā webservisā tiek atgriezta informācija ar iesaistītajām organizācijām un vai tās ir apstiprinājušas pavadzīmi vai nē
    * Labojums Swagger UI pavadzīmes statusa maiņas aprakstā - updateDate parametrs tagad uzrādās kā obligāts
    * Nokonfigurēts korekts fontu lietojums izdrukās, lai parādītos latviešu valodas diakritiskās zīmes
    * Labojums lietotāju saskarnē - neveikt validācijas dzēstām rindām blokā "Informācija par atkritumiem"
    * Pavadzīmju saraksta excel eksporta uzlabojumi
    * R & D kodi vairs nav obligāti pie statusa izmaiņām (precizēta prasībā saistībā ar MK noteikumiem)


* 2021.06.01
    * Blokā "Informācija par atkritumiem" laukam "Mērķis" nomainītas vērtības atbilstoši MK noteikumiem
    * [Klasifikatoru servisā](https://services.proofit.lv/APUS/swagger-ui.html#/web-service-controller/) pievienota "type-of-transport" klasifikatora ieguve
    * Blokā "Informācija par atkritumu pārvadātājiem" pievienots lauks "Puspiekabes valsts numurs" (webservice lauks "CarrierData.semitrailerRegNumber")
    * Blokā "Informācija par atkritumu tirgotāju vai pārvadāšanas starpnieku" pievienoti lauki
        * Valsts vides dienesta lēmuma par atkritumu tirgotāja vai atkritumu apsaimniekošanas starpnieka reģistrāciju Nr ("MediatorData.vvdDecisionNumber)
        * Datums ("MediatorData.vvdDecisionDate)
