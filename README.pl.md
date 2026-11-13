# AniSong-AppleMusic

[English](README.md) · [简体中文](README.zh-Hans.md) · [繁體中文](README.zh-Hant.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Deutsch](README.de.md) · **Polski**

Zestawienie piosenek przewodnich z anime – openingów, endingów i piosenek wstawionych – z utworami w Apple Music. Każde dopasowanie sprawdzono z oryginalnym nagraniem: covery i wersje koncertowe nigdy nie są używane, a gdy Apple Music ma tylko inną wersję montażową lub inny skład wykonawców, dopasowanie jest odpowiednio oznaczone.

To dane, z których korzysta sekcja „Piosenki przewodnie” w aplikacji [PaperVN](https://papervn.jizpaper.com). Są aktualizowane codziennie i przekazane do domeny publicznej na licencji [CC0 1.0](LICENSE).

## W skrócie

<!-- stats -->
Stan na wersję `20261114-d676a2a67db3`:

| | |
|---|---|
| Utwory | 38 333 |
| Znalezione w Apple Music | 27 016 |
| Potwierdzono brak w Apple Music | 11 317 |
| Anime | 9 971 |
<!-- /stats -->

## Plik

Wszystkie dane znajdują się w jednym pliku, [`AniSong-AppleMusic.json`](AniSong-AppleMusic.json), po jednym utworze w wierszu, dzięki czemu łatwo porównać codzienne zmiany.

```json
{
  "version": "20261110-d811aa2eb306",
  "format": 1,
  "songs": {
    "62608": [1182264674, 185088141, "アンサー", "BUMP OF CHICKEN", "https://is1-ssl.mzstatic.com/…/600x600bb.jpg"],
    "21189": 0,
    "-49848": [1822904632, 577028285, "雪の進軍", "あんこうチーム", "https://is1-ssl.mzstatic.com/…/600x600bb.jpg", "lineup", "雪の進軍", "Satomi Moriya"]
  },
  "inserts": { "61227": [-49848] },
  "themes": { "31646": [58368, 58369, 58370, 62608, 62609] }
}
```

### Klucze

- **Klucze dodatnie** to identyfikatory piosenek przewodnich z MyAnimeList – `id` każdej pozycji w `opening_themes` i `ending_themes` z MyAnimeList API v2.
- **Klucze ujemne** to piosenki wstawione: zanegowany `annSongId` z AnisongDB.

### Wartości

`0` oznacza, że utwór został sprawdzony i nie ma go w Apple Music. W przeciwnym razie wartość jest tablicą:

| Indeks | Pole | Uwagi |
|---|---|---|
| 0 | ID utworu | ID utworu w Apple Music |
| 1 | ID wykonawcy | Może być `null` |
| 2 | Tytuł | Zapis z japońskiego sklepu (język oryginału) |
| 3 | Wykonawca | Zapis z japońskiego sklepu |
| 4 | Okładka | Adres obrazu 600×600, może być `null` |
| 5 | Przybliżenie | Opcjonalne, zob. niżej |
| 6 | Rzeczywisty tytuł | Opcjonalne: tytuł użyty w anime, jeśli jest inny |
| 7 | Rzeczywisty wykonawca | Opcjonalne: wykonawcy w anime, jeśli są inni |
| 8 | Sklep | Opcjonalne: tylko gdy utworu nie ma w japońskim sklepie, np. `"cn"` |

Pola po indeksie 4 są pomijane, gdy są puste; wcześniejsze luki wypełnia `null`. Utwór można otworzyć pod adresem `https://music.apple.com/{sklep lub jp}/song/{ID utworu}`.

Utwory, których w ogóle nie ma w pliku, nie zostały jeszcze sprawdzone.

### Dopasowania przybliżone

Gdy Apple Music nie ma oryginalnego nagrania, może zostać użyty bliski zamiennik z oznaczeniem:

- `short` – Dostępna jest tylko wersja skrócona (np. TV size).
- `lineup` – Ten sam utwór w innym składzie wykonawców.
- `version` – Inna wersja tego samego wykonawcy.

Covery i nagrania koncertowe brzmią inaczej, więc nigdy nie są używane jako zamienniki.

### Indeksy

- `inserts` – ID anime z MyAnimeList → piosenki wstawione znalezione w Apple Music, w kolejności z AnisongDB.
- `themes` – ID anime z MyAnimeList → klucze openingów i endingów.

### Wersja

`version` to data utworzenia (czas chiński) i skrót zawartości. Skrót zmienia się przy każdej zmianie zawartości.

## Jak powstają dane

Openingi i endingi pochodzą z MyAnimeList, a piosenki wstawione z AnisongDB. Każdy utwór jest automatycznie dopasowywany do katalogu Apple Music, a niepewne dopasowania są sprawdzane ręcznie. Anime z ostatnich 12 miesięcy są sprawdzane codziennie, więc nowości w Apple Music pojawiają się na bieżąco.

## Zgłaszanie błędów

Jeśli utwór jest dopasowany do niewłaściwego nagrania lub go brakuje, [utwórz zgłoszenie](https://github.com/JiZPaper/AniSong-AppleMusic/issues) z kluczem i prawidłowym linkiem do Apple Music. Błędy można też zgłaszać w PaperVN.

## Licencja

Zestawienie jest przekazane do domeny publicznej na licencji [CC0 1.0 Universal](LICENSE). Możesz je kopiować, modyfikować i wykorzystywać w dowolnym celu bez pytania o zgodę; podanie źródła jest mile widziane, ale nie jest wymagane.

Tytuły, nazwy wykonawców i okładki należą do odpowiednich właścicieli praw, a adresy okładek wskazują na serwery Apple. Apple Music jest znakiem towarowym Apple Inc. MyAnimeList i AnisongDB należą do swoich właścicieli. Ten projekt nie jest powiązany z żadnym z nich ani przez nie popierany.
