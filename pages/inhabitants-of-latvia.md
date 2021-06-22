# Fizisku personu piegādātie atkritumi

Lai izveidotu pavadzīmi, kas atbilst MK noteikumiem par [fizisko personu piegādātajiem atkritumiem](https://likumi.lv/ta/id/321151#p26) "sender" blokā jānorāda lauks "legalType" ar vērtību "LAT" un bloks "carriers" ir jāatstāj pilnībā tukšs.

Piemērs:
```json
{
    "invoice": {
        "responsibleOrganization": {
            "id": 12345
        }
    },
    "sender": {
        "legalType": "LAT",
        "shipmentDate": "2021-06-04T10:43:16.190+03:00"
    },
    "carriers": [],
    "receiver": {
        "legalType": "JUR"
        ,"organization": {
            "id": 12345
        }
    },
    "content": [
        {
            "amountSend": 1.0,
            "amountReceived": 1.0,
            "target": {
                "code": "WASTE_DISPOSAL"
            },
            "wasteClass": {
                "code": "010304"
            }
        }
    ]
}
```
