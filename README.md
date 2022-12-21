# API Vulcan UONET+ Uczeń+
## Modele
#### Dziennik
```js
{
  idDziennik: number = 0,
  rodzajDziennika: number = 1, // 0 - nieznany, 1 - dziennik ucznia, 2 - dziennik przedszkolaka, 3 - dziennik wychowanka
  dziennikDataOd: string = "1970-09-01T00:00:00+02:00",
  dziennikDataDo: string = "1971-02-01T00:00:00+02:00".
  isUczen: boolean = true,
  isPrzedszkolak: boolean = false,
  isWychowanek: boolean = false,
  key: string = "MC0wLTE=", // po odszyfrowaniu base64 wartość to `{idUcznia}-{idDziennika}-{rodzajDziennika}`
  uczen: string = "Jan Kowalski",
  oddzial: string = "1a",
  jednostka: string = "Publiczna Szkoła nr 1 w Powiecie Wulkanowym",
  jednostkaGodzinaOd: null = null,
  jednostkaGodzinaDo: null = null,
  isDorosli: boolean = false,
  isPolicealna: boolean = false,
  is13: boolean = false,
  isArtystyczna: boolean = false,
  isArtystyczna13: boolean = false,
  isSpecjalna: boolean = false,
  isOplaty: boolean = false,
  isPlatnosci: boolean = false,
  isZaplac: boolean = false,
  canMergeAccounts: boolean = false,
  pelnoletniUczen: boolean = false,
  opiekunUcznia: boolean = false,
  wymagaAutoryzacji: boolean = false,
  posiadaPesel: boolean = false,
  globalKeySkrzynka: string = "00000000-0000-0000-0000-000000000000"
}
```

#### OcenyUstawienia
```js
{
  isPunkty: boolean = false,
  isSrednia: boolean = false,
  isDorosli: boolean = false,
  isOcenaOpisowa: boolean = false,
  isOstatniOkresKlasyfikacyjny: boolean = false
}
```

#### OcenyPrzedmiot
```js
{
  przedmiotNazwa: string = "Nazwa przedmiotu",
  pozycja: number = 0,
  nauczyciele: array<string> = ["Nazwisko Imię [NI]"]
  ocenyCzastkowe: array<OcenaCzastkowa> = [OcenaCzastkowa]
  egzaminFormaPraktyczna: null = null,
  egzaminFormaUstna: null = null,
  egzaminOcenaProponowana: null = null,
  egzaminOcenaLaczna: null = null,
  sumaPunktow: null = null,
  srednia: number = 0,
  proponowanaOcenaOkresowa: string = " ",
  proponowanaOcenaOkresowaPunkty: null = null,
  ocenaOkresowa: string = " ",
  ocenaOkresowaPunkty: null = null,
  podsumowanieOceny: null = null
}
```

#### OcenaCzastkowa
```js
{
  wpis: string = "6 (komentarz)",
  dataOceny: string = "01.01.1970",
  kategoriaKolumny: string = "Kategoria kolumny",
  nazwaKolumny: string = "Nazwa kolumny",
  waga: number = 1.00,
  kolorOceny: number = 0,
  nauczyciel: string = "Nazwisko Imię [NI]",
  zmienionaOdOstatniegoLogowania: boolean = false
}
```

#### OcenyResponse
```js
{
  ocenyPrzedmioty: array<OcenyPrzedmiot> = [ocenyPrzedmiot],
  ustawienia: OcenaUstawienia = OcenaUstawienia
}
```

#### OkresKlasyfikacyjny
```js
{
  numerOkresu: number = 1,
  id: number = 0
}
```

#### CacheUnit
```js
{
  id: number = 0,
  symbol: string = "123456",
  skrot: string = "SZK 1",
  nazwa: string = "Publiczna Szkoła nr 1 w Powiecie Wulkanowym"
}
```

#### Cache
```js
{
  units: array<CacheUnit> = [CacheUnit],
  linkst: array<null> = [null]
  isStudent: boolean = true,
  isParent: boolean = false,
  isMenu: boolean = true,
  isOffice365: boolean = ture,
  isBetacomOn: boolean = ture,
  isNadzorOn: boolean = true,
  isUploadPhotosOn: boolean = false,
  isZglaszanieNieobecnosciOn: boolean = false,
  isPokazLekcjeZrealizowaneOn: boolean = false,
  isPokazLekcjiZaplanowaneOn: boolean = false,
  oneDriveClinetId: string = "00000000-0000-0000-0000-000000000000",
  isOneDriveAttachmentsHomeworksOs: boolean = true,
  isPodrecznikiOn: boolean = true
}
```

### SprawdzianZadanie
```js
{
  typ: number = 1,
  przedmiotNazwa: string = "Nazwa przedmiotu",
  data: string = "1970-01-01T00:00:00+01:00",
  hasAttachment: boolean = false,
  id: number = 0
}
```

## Endpointy
### `[GET] api/Cache`

#### Response

`Cache`

### `[GET] api/Context`

Pobiera listę dzienników uczniów

#### Response

`array<Dziennik>`

### `[GET] api/OkresyKlasyfikacyjne?idDziennik={idDziennika}`

Pobiera listę okresów klasyfikacyjnych (semestrów) danego dziennika

#### Response

`array<OkresKlasyfikacyjny>`

### `[GET] api/Oceny?key={keyDziennika}&idOkresKlasyfikacyjny={idOkresuKlasyfikacyjnego}`

Pobiera oceny danego ucznia z danego dziennika

#### Response

`OcenyResponse`

### `[GET] api/SprawdzianyZadaniaDomowe?key={keyDziennika}&dataOd={dataOd}&dataDo={dataDo}`

Pobiera sprawdziany i zadania domowe

#### Response

`array<SprawdzianZadanie>`

