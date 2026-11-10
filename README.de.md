# AniSong-AppleMusic

[English](README.md) · [简体中文](README.zh-Hans.md) · [繁體中文](README.zh-Hant.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · **Deutsch** · [Polski](README.pl.md)

Eine Zuordnung von Anime-Titelsongs – Openings, Endings und Insert-Songs – zu Titeln auf Apple Music. Jede Zuordnung wurde mit der Originalaufnahme abgeglichen: Cover- und Live-Versionen werden nie verwendet, und wenn Apple Music nur eine andere Fassung oder Besetzung hat, ist die Zuordnung entsprechend gekennzeichnet.

Dies ist der Datensatz hinter dem Bereich „Titelsongs“ der App [PaperVN](https://papervn.jizpaper.com). Er wird täglich aktualisiert und unter [CC0 1.0](LICENSE) in die Gemeinfreiheit entlassen.

## Überblick

Stand Version `20261110-d811aa2eb306`:

| | |
|---|---|
| Titel | 38.236 |
| Auf Apple Music gefunden | 26.946 |
| Nachweislich nicht auf Apple Music | 11.290 |
| Anime | 9.959 |

## Datei

Alle Daten stehen in einer einzigen Datei, [`AniSong-AppleMusic.json`](AniSong-AppleMusic.json), mit einem Titel pro Zeile, damit sich die täglichen Änderungen leicht vergleichen lassen.

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

### Schlüssel

- **Positive Schlüssel** sind Titelsong-IDs von MyAnimeList – die `id` jedes Eintrags in `opening_themes` und `ending_themes` der MyAnimeList API v2.
- **Negative Schlüssel** sind Insert-Songs: die negierte `annSongId` von AnisongDB.

### Werte

`0` bedeutet, dass der Titel geprüft wurde und nicht auf Apple Music verfügbar ist. Andernfalls ist der Wert ein Array:

| Index | Feld | Hinweise |
|---|---|---|
| 0 | Titel-ID | Apple Music-Titel-ID |
| 1 | Künstler-ID | Kann `null` sein |
| 2 | Titel | Schreibweise im japanischen Store (Originalsprache) |
| 3 | Künstler | Schreibweise im japanischen Store |
| 4 | Cover | Bild-URL in 600×600, kann `null` sein |
| 5 | Annäherung | Optional, siehe unten |
| 6 | Tatsächlicher Titel | Optional: der im Anime verwendete Titel, falls abweichend |
| 7 | Tatsächlicher Künstler | Optional: die Interpreten im Anime, falls abweichend |
| 8 | Store | Optional: nur vorhanden, wenn der Titel im japanischen Store nicht verfügbar ist, z. B. `"cn"` |

Felder nach Index 4 entfallen, wenn sie leer sind; Lücken davor werden mit `null` aufgefüllt. Ein Titel lässt sich unter `https://music.apple.com/{Store oder jp}/song/{Titel-ID}` öffnen.

Titel, die gar nicht aufgeführt sind, wurden noch nicht geprüft.

### Annäherungen

Wenn Apple Music die Originalaufnahme nicht hat, kann ein naher Ersatz verwendet und gekennzeichnet werden:

- `short` – Nur eine gekürzte Fassung (z. B. TV-Size) ist verfügbar.
- `lineup` – Derselbe Titel in einer anderen Besetzung.
- `version` – Eine andere Version desselben Künstlers.

Cover- und Live-Aufnahmen klingen anders und werden daher nie als Ersatz verwendet.

### Indizes

- `inserts` – MyAnimeList-Anime-ID → auf Apple Music gefundene Insert-Songs, in der Reihenfolge von AnisongDB.
- `themes` – MyAnimeList-Anime-ID → Schlüssel der Openings und Endings.

### Version

`version` besteht aus dem Erstellungsdatum (chinesische Normalzeit) und einem Inhalts-Hash. Der Hash ändert sich, sobald sich der Inhalt ändert.

## Entstehung

Openings und Endings stammen von MyAnimeList, Insert-Songs von AnisongDB. Jeder Titel wird automatisch mit dem Apple Music-Katalog abgeglichen, unsichere Zuordnungen werden von Hand geprüft. Anime der letzten 12 Monate werden täglich erneut geprüft, sodass Neuerscheinungen auf Apple Music nach und nach hinzukommen.

## Fehler melden

Wenn ein Titel einer falschen Aufnahme zugeordnet ist oder fehlt, [erstelle bitte ein Issue](https://github.com/JiZPaper/AniSong-AppleMusic/issues) mit dem Schlüssel und dem richtigen Apple Music-Link. Du kannst Fehler auch in PaperVN melden.

## Lizenz

Die Zuordnung ist unter [CC0 1.0 Universal](LICENSE) gemeinfrei. Du kannst sie ohne Erlaubnis kopieren, verändern und für jeden Zweck verwenden; eine Namensnennung ist willkommen, aber nicht erforderlich.

Titel, Künstlernamen und Cover gehören den jeweiligen Rechteinhabern, und Cover-URLs verweisen auf Server von Apple. Apple Music ist eine Marke der Apple Inc. MyAnimeList und AnisongDB sind Eigentum ihrer jeweiligen Inhaber. Dieses Projekt steht mit keinem von ihnen in Verbindung und wird von keinem von ihnen unterstützt.
