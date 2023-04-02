# Eesti Energia energiakaubanduse analüütiku test ülesanne

### Autor: Kertu Jõgi

Siin olen lahendanud Eesti Energia energiakaubanduse analüütiku test ülesande, mis koosnes neljast erinevast alaülesandest.
1. Vaatle ühe aasta kohta tuule- ja päikesetoodangu andmeid. Milliseid sesoonsusi leiad? Näita neid kas graafiliselt või tabeli kujul.
2. Kas päevakeskmine tuule- ja päikesetoodang kumbki vastavad normaaljaotusele? Leia andmete põhjal tuule P90 näitaja (vihje: kogus, mida toodetakse vähemalt 90% kordadel)
3. Analüüsi tuule- ja päikesetoodangu mõju Eesti elektrihinnale, kasutades lineaarregressiooni ja tekkinud hüpoteesides veendumiseks statistilisi teste. Kas kumbki (või nende kombinatsioon) on hea näitaja elektrihinna ennustamiseks?
4. Arvuta välja tuule- ja päikesetoodanguga teenitud tulu (kogus x hind) 2021-2022 perioodi peale kokku. Leia selle kaudu iga kuu kaupa kogusega kaalutud keskmine hind. Seleta, mida see tähendab.

### Vastused
1. Teise graafiku ('Päikesetoodangu ja tuuletoodangu aastaajaline graafik aastal 2021') pealt on näha, et keskmiselt päikesetoodang on kõige suurem suvekuudel. Vaadates esimest graafikut ('Päikesetoodangu ja tuuletoodangu kuugraafik aastal 2021') näeme, et kõige suurem päikesetoodang oli juunikuus (keskmiselt 77.2 MWh). Päikesetoodang on kõige madalam aga talvekuudel, kusjuures minimaalne päikesetoodang oli jaanuarikuus (keskmiselt 1,9 MWh). Tuuletoodang oli aga kõige suurem sügiskuudel, kus maksimum toodang oli oktoobris keksmiselt 112,9 MWh. Kõige väiksem tuuletoodang, vastupidiselt päikesetoodangule, oli aga suvekuudel. Minimaalselt juunikuus keksmiselt 64,3 MWh.
2. Päevakeskmine tuule- ja päikesetoodang kumbki eraldi ei vasta normaaljaotusele. Kui vaadelda tuule- ja päikesetoodangut koos, siis saab väita, et see vastab normaaljaotusele. Tuule P90 näitaja ehk kogus, mida toodetakse vähemalt 90% kordadel on 16.00 MWh.
3. Eelneva regressiooni mudeli pealt näeme, et EE tuul ja päike (MWh) koefitsent on negatiivne. See tähendab, et elektrihind langeb koos tuule- ja päikesetoodangu kasvuga. Samas mudeli R-ruudu väärtus on 0.005 ehk päikesetoodangu ja tuuletoodangu summa selgitab ainult 0,5% elektrihinna muutustest. See võib viidata sellele, et päikesetoodangu ja tuuletoodangu mõju Eesti elektrihinnale on väga väike.
Koostan ka paremaks analüüsiks T-testi.
Esmalt määran hüpoteesid: H0: tuule- ja päikesetoodangu ning elektrihinna vahel ei ole seost H1: tuule- ja päikesetoodangu ning elektrihinna vahel on seos
Valin siin α = 0,05.
Eelnevalt näeme, et p-väärtus < α. Ehk lükkan tagasi nullhüpoteesi (H0) ja väidan, et tuule- ja päikesetoodangu ning elektrihinna vahel on seos. Seda seost nägime ka regressioonimudeli pealt (elektrihind langeb kui tuule- ja päikesetoodang kasvab). Samas regressioonimudeli pealt võisime eeldada, et tuule- ja päikesetoodang ei ole antud andmete ajaraamistikus suurim hinna muutust põhjustav tegur.
Seega eelneva põhjal saab väita, et kombinatsioon regressioonimudeli ning statistilistest testidest annab hea ülevaate elektrihinna ennustamiseks. Samas veelgi täpsemaks ennustamiseks oleks vaja kaasata rohkem muutujaid, nagu näiteks energiatootmiseks kasutatavate kütuste hind, tarbimismustrid jne.
4. Perioodil 2021-2022 päikesetoodanguga teenitud tulu: 132162558.35 EUR
Perioodil 2021-2022 tuuletoodanguga teenitud tulu: 176022185.13 EUR
Perioodil 2021-2022 päikesetoodanguga ja tuuletoodanguga  kokku teenitud tulu: 308184743.48 EUR
Kogusega kaalutud keskmist hinda leitakse (selle ülesande puhul) järgnevalt: ((tuule- ja päikesetoodangu hinna summa) * tuule- ja päikesetoodangu kogus) / tuule- ja päikesetoodangu kogu koguste summa
Ülal arvutatud kogusega kaalutud keskmine hind arvutatati kaalutud keskmise hinna valemi abil, kus kaaluks on vastava rea päikesetoodangu ja tuuletoodangu summa (quantity) ning hinnaks on vastava rea päikesetoodangu ja tuuletoodangu summa (revenue) summa.
Tulemused väljastatakse DataFrame'ina, kus iga rea esindab ühte kuud ning tulpadeks on kuuga seotud päikesetoodangu tulu, tuuletoodangu tulu, päikesetoodangu kogus, tuuletoodangu kogus ja koguse kaalutud keskmine hind.

## Kood
Koodi kirjutamiseks olen kasutanud Pythonit. 
Selleks, et paremini mõista vastuseid tuleks vaadata ka 'Eesti Energia energiakaubanduse analüütiku testül.ipynb' faili.
