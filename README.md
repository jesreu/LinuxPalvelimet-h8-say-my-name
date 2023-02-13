# LinuxPalvelimet-h8-say-my-name
    Kirjoittanut: Jesse Reunamo
    Kurssi:       Linux-palvelimet
    Linkki:       https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/

## a)
Vuokrataan nimi h7-harjoituksessa luodulle palvelimelle käyttäen Namecheap nimipalvelua. Valitsin Namecheap palvelun, koska Github educations paketin kautta sain ilmaiseksi nimen käyttöön. Aloitetaan prosessi rekisteröitymällä Namecheap palveluun. Rekisteröitymiseen ei tarvita valtavia tietoja, mutta nimen hankintaan tarvitaan enemmän tietoja. 

Valitettavasti Github educations paketti tarjoaa ilmaiseksi vain .me top level domain osoitteen, joten sillä joudutaan menemään. Huomiona myös että nimen rekisteröinti menee erillisen nc.me sivun kautta.

![kusetusloppu](https://user-images.githubusercontent.com/112503770/218344052-5ab0ce79-075b-4ca2-a7e4-13ac0c3733e6.jpg)

Ilmeisesti kyseessä namecheapin education järjestelmä. Hankin jessereunamo.me nimen itselleni ja kas kuin ollakkaan domain ilmestyi namecheap:in normaalin sivuston alaisuuteen. 

![Domaini onnistui](https://user-images.githubusercontent.com/112503770/218344068-ebe97cf8-6410-4c86-8657-6a2db02559aa.jpg)


Nyt valitsemalla vaihtoehdon manage voidaan asettaa palvelimen ip hankimallemme osoitteelle. Navigoimalla advanced DNS välilehdelle voimme asettaa name recordit, joiden avulla nimipalvelu osaa yhdistää oikean nimen oikeaan osoitteesseen.

![Onnistunut muutetut nimitiedot](https://user-images.githubusercontent.com/112503770/218344084-95571605-3122-45b2-97f9-f5d8525548b0.jpg)


Nyt kokeillaan avata sivu klo 1.18. Ei ole vielä vaihtanut sivua oikein, koska hankittu nimi vastaa github pages error sivua. Luulen, että github edu paketti on ohjattuna githubin sivuihin rekordien mukaan, jotka jouduin poistamaan Namecheapin sivulta. Paras arvaus tällä hetkellä, että nimen siirtymisessä menee hetki, joten odotellaan. Vielä tuplatarkistin namecheapin tuki artikkelista, joka antaa noin 30 minuuttia arvion. Korjasin vielä kirjoitetut rekordit artikkelin mukaan (kaksi eriävää www rekordia)

Kuvassa väärä sivu.
![Errori](https://user-images.githubusercontent.com/112503770/218344088-85d6610b-1a59-4dcb-93af-b1b8a989fa0c.jpg)

Klo 1.42: Aika tekee tehtävänsä! Sivu toimii!

![Toimivatsivut](https://user-images.githubusercontent.com/112503770/218344368-6d0399ad-24a2-4b0e-be23-66491ec65501.jpg)


## b)
Tutkitaan hankittua domainia käytämällä host ja dig komentoja. Aloitan ajamalla:

    man host
    man dig
    
Ottaakseni selvää lisää komennoista. Komennoista host komennolla on kattavat man sivut, dig komennolla sivu ei aukea. Kokeillaa joka tapauksessa `host jessereunamo.me`

![host_tulokset](https://user-images.githubusercontent.com/112503770/218346587-69dd179f-5bf5-42d4-8e14-ba16056b3219.png)

Ensimmäinen tulostettu rivi on selkeä, joka kertoo nimeen yhdistetyn ip osoitteen. Seuraavat rivit näyttäisivät vastaavan erilaisia email edelleenlähetys servereitä. Namecheap tarjoaa palvelun ilmaiseksi, joten olettaisin, että niistä on kysymys.

Pienellä selvittämisellä näyttäisi, että dig komento tarvitsee paketin joten:

    sudo apt-get install dnsutils
    
Ajetaan komento `dig jessereunamo.me`

![dig_tulokset](https://user-images.githubusercontent.com/112503770/218346596-256fa12e-d642-463e-8204-2a501492eee9.png)

Tulkitaan tulostetta erittäin helposti lähteissä olevan ohjeiden avulla. Voidaan käydä komennon tuloste osioittain läpi. Ensimmäisenä ylhäällä on ohjelman versionumero, käyttöjärjestelmä ja komennon syöte. Got answer osiossa kerrotaan mitä palvelin vastasi komentoon. Opt osiossa on tiedot: edns dns järjestelmän laajennus, Flags eli käytetyt liput ja upd(user dependecy protocol) paketin koko. Question osiossa on kysytty sivu, in=internet ja a=address. Vastauksessa samat tiedot mutta lisättynä time to live ajanjakso, jolla rekordi päivittyy ja sivun IP osoite. Lopussa on statistiikkaa hausta: Hakuaika millisekunteina, dns serverin ip ja portti, aika jolloin komento ajettiin ja palautetun datan koko.
## Lähteet

    https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/
    https://www.namecheap.com/support/knowledgebase/article.aspx/319/2237/how-can-i-set-up-an-a-address-record-for-my-domain/
    https://www.namecheap.com/support/knowledgebase/article.aspx/308/2214/how-to-set-up-free-email-forwarding/
    https://phoenixnap.com/kb/linux-dig-command-examples
    
    
