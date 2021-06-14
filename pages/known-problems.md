# Zināmās problēmas

* Latvijas iedzīvotāji kā pavadzīmes nosūtītājs un pārvadātājs - šī funkcionalitāte ir vēl izstrādes stadijā
* Jauna uzņēmuma ievadīšana, izmantojot webservisu (šobrīd vēl nav iespējama)
* Jauna objekta (nosūtīšanas/saņemšanas adreses) ievadīšana, izmantojot webservisu (šobrīd vēl nav iespējama)
* Norādot neeksistējošas organizācijas ID pavadzīmē (lietojot webservisu), tiek atgriezta grūti saprotama kļūda "org.hibernate.exception.ConstraintViolationException: could not execute statement"
* [Swagger UI](https://services.proofit.lv/APUS/swagger-ui.html#/ws-invoice-controller) dokumentācijā galapunktam "/rest/ws/invoices/{number}/status/{action}" query parametrs "updateDate" neuzrādās, kā obligāts (Swagger UI problēma)
* Objektu (nosūtīšanas/saņemšanas adrešu) galapunkts "/rest/ws/facilities/{facilityRequestType}" neatgriež adresi, lai gan pavadzīmes galapunkta "/rest/ws/invoices/{number}" datos šis lauks ir
* Testa vidē izdrukās netiek attēloti latviešu alfabēta simobli (garumzīmes)
* Blokā "Informācija par atkritumu pārvadātājiem" izplešot rindu, neparādās atļaujas informācija (lauks Atkritumu pārvadāšanas atļaujas Nr.)
* Izdrukas blokā "Informācija par atkritumu pārvadātājiem" neparādās atļaujas informācija
