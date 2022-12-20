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

## Endpointy
#### `[GET] api/Context`

Pobiera listę dzienników uczniów

#### Response

list[Dziennik]

