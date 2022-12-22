# API Vulcan UONET+ Uczeń+
baseUrl: `https://uonetplus-uczenplus.{host}/{symbolGrupujacy}/{symbolJednostkiSprawozdawczej}`
## Menu
  - [api/Context](https://marioneq4958.github.io/uczenplus-docs/#api/context)
  - [api/Oceny](https://marioneq4958.github.io/uczenplus-docs/#api/oceny)
  - [api/OkresyKlasyfikacyjne](https://marioneq4958.github.io/uczenplus-docs/#api/okresyklasyfikacyjne)
  - [api/Cache](https://marioneq4958.github.io/uczenplus-docs/#api/Cache)
  - [api/SprawdzianyZadaniaDomowe](https://marioneq4958.github.io/uczenplus-docs/#api/sprawdzianyzadaniadomowe)
  - [api/WychowawcyTablica](https://marioneq4958.github.io/uczenplus-docs/#api/wychowawcytablica)
  - [api/WazneDzisiajTablica](https://marioneq4958.github.io/uczenplus-docs/#api/waznedzisiajtablica)
  - [api/SzczesliwyNumerTablica](https://marioneq4958.github.io/uczenplus-docs/#api/szczesliwynumertablica)
  - [api/PrzedmiotyUczniaWykresy](https://marioneq4958.github.io/uczenplus-docs/#api/przedmiotyuczniawykresy)
  - [api/FrekwencjaStatystyki](https://marioneq4958.github.io/uczenplus-docs/#api/frekwencjastatystyki)
## api/Context
Pobiera listę dzienników uczniów

### Request
```js
GET {baseUrl}/api/Context
```
```http
Content-Type: application/json; charset=utf-8
```

### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```js
array<Dziennik>
```
### Modele
#### Dziennik
```ts
{
  idDziennik: number = 0,
  rodzajDziennika: number = 1, // 0 - nieznany, 1 - dziennik ucznia, 2 - dziennik przedszkolaka, 3 - dziennik wychowanka
  dziennikDataOd: string = "1970-09-01T00:00:00+02:00",
  dziennikDataDo: string = "1971-02-01T00:00:00+02:00",
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
## api/Oceny
Pobiera oceny danego ucznia z danego dziennika

### Request
```js
GET {baseUrl}/api/Oceny?key={keyDziennika}&idOkresKlasyfikacyjny={idOkresuKlasyfikacyjnego}
```
```http
Content-Type: application/json; charset=utf-8
```

### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```js
array<OcenyResponse>
```
### Modele
#### OcenyUstawienia
```ts
{
  isPunkty: boolean = false,
  isSrednia: boolean = false,
  isDorosli: boolean = false,
  isOcenaOpisowa: boolean = false,
  isOstatniOkresKlasyfikacyjny: boolean = false
}
```

#### OcenyPrzedmiot
```ts
{
  przedmiotNazwa: string = "Nazwa przedmiotu",
  pozycja: number = 0,
  nauczyciele: array<string> = ["Nazwisko Imię [NI]"],
  ocenyCzastkowe: array<OcenaCzastkowa> = [OcenaCzastkowa],
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
```ts
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
```ts
{
  ocenyPrzedmioty: array<OcenyPrzedmiot> = [ocenyPrzedmiot],
  ustawienia: OcenaUstawienia = OcenaUstawienia
}
```
## api/OkresyKlasyfikacyjne

Pobiera listę okresów klasyfikacyjnych (semestrów) danego dziennika

### Request
```js
GET {baseUrl}/api/OkresyKlasyfikacyjne?idDziennik={idDziennika}
```
```http
Content-Type: application/json; charset=utf-8
```

### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```js
array<OkresKlasyfikacyjny>
```
### Modele
#### OkresKlasyfikacyjny
```ts
{
  numerOkresu: number = 1,
  id: number = 0
}
```

## api/Cache
### Request
```js
GET {baseUrl}/api/Cache
```
```http
Content-Type: application/json; charset=utf-8
```

### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```js
Cache
```
### Modele
#### CacheUnit
```ts
{
  id: number = 0,
  symbol: string = "123456",
  skrot: string = "SZK 1",
  nazwa: string = "Publiczna Szkoła nr 1 w Powiecie Wulkanowym"
}
```

#### Cache
```ts
{
  units: array<CacheUnit> = [CacheUnit],
  linkst: array<null> = [null],
  isStudent: boolean = true,
  isParent: boolean = false,
  isMenu: boolean = true,
  isOffice365: boolean = true,
  isBetacomOn: boolean = true,
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
### api/SprawdzianyZadaniaDomowe

Pobiera sprawdziany i zadania domowe

#### Request
```js
GET {baseUrl}/api/SprawdzianyZadaniaDomowe?key={keyDziennika}&dataOd={dataOd}&dataDo={dataDo}
```
```http
Content-Type: application/json; charset=utf-8
```

#### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```js
array<SprawdzianZadanie>
````
#### SprawdzianZadanie
```ts
{
  typ: number = 1,
  przedmiotNazwa: string = "Nazwa przedmiotu",
  data: string = "1970-01-01T00:00:00+01:00",
  hasAttachment: boolean = false,
  id: number = 0
}
```
### api/WychowawcyTablica
Pobiera listę wychowawców

### Request
```js
GET {baseUrl}/api/WychowawcyTablica?key={keyDziennika}
```
```http
Content-Type: application/json; charset=utf-8
```

### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```js
array<WychowawcaTablica>
````
### Modele
#### WychowawcaTablica
```ts
{
  imieNazwisko: str = "Imię Nazwisko",
  isGlowny: boolean = true,
  globalKeySkrzynka: string = "00000000-0000-0000-0000-000000000000"
}
```
### api/WazneDzisiajTablica

Pobiera listę dzisiejszych wydarzeń

### Request
```js
GET {baseUrl}/api/WazneDzisiajTablica?key={keyDziennika}
```
```http
Content-Type: application/json; charset=utf-8
```
### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```js
array<WazneWydarzenieTablica>
````
### Modele
#### WazneWydarzenieTablica
```ts
{
  przedmiot: string = "Nazwa przedmiotu",
  nazwaZdarzenia: string = "nazwa zdarzenia",
  nazwa: string = "Nazwa przedmiotu - nazwa zdarzenia"
}
```
### api/SzczesliwyNumerTablica

Pobiera dzisiejszy szczęsliwy numerek

### Request
```js
GET {baseUrl}/api/SzczesliwyNumerTablica?key={keyDziennika}
```
```http
Content-Type: application/json; charset=utf-8
```

### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```js
SzczesliwyNumerTablica
````
### Modele
#### SzczesliwyNumerTablica
```ts
{
  numer: number = 1,
  id: number = 0
}
```
### api/PrzedmiotyUczniaWykresy

Pobiera listę przedmiotów do statystyk

### Request
```js
GET {baseUrl}/api/PrzedmiotyUczniaWykresy?key={keyDziennika}&idOkresKlasyfikacyjny={idOkresuKlasyfikacyjnego}
```
```http
Content-Type: application/json; charset=utf-8
```

### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```js
array<StatystykiOcenPrzedmiot>
````
### Modele
#### StatystykiOcenPrzedmiot
```ts
{
  nazwa: string = "Nazwa przedmiotu",
  id: number = 0
}
```
### api/FrekwencjaStatystyki

Pobiera statystyki frekwencji

### Request
```js
GET {baseUrl}/api/FrekwencjaStatystyki?key={keyDziennika}
```
```http
Content-Type: application/json; charset=utf-8
```

### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```js
StatystykiFrekwencjiResponse
````
### Modele
#### StatystykaFrekwencjiMiesiac
```ts
{
  miesiac: number = 1,
  wartosc: number = 0
}
```

#### StatystykiKategoriaFrekwencji
```ts
{
  kategoriaFrekwencji: number = 1, // 1 - o, 2 - n, 3 - nu, 4 - ns, 5 - s, 6 - su, 7 - z
  miesiace: array<StatystykaFrekwencjiMiesiac> = [StatystykaFrekwencjiMiesiac],
  okresy: array<number> = [1, 1], // ilość wpisów danej kategorii w danym okresie klasyfikacyjnym,
  razem: number = 2 // ilość wpisów danej kategorii w całym roku szkolnym
}
```

#### StatystykiFrekwencjiResponse
```ts
{
  podsumowanie: number = 99.03,
  statystyki: array<StatystykiKategoriaFrekwencji> = [StaystykiKategoriaFrekwencji]
}
```
