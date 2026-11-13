# AniSong-AppleMusic

**English** · [简体中文](README.zh-Hans.md) · [繁體中文](README.zh-Hant.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Deutsch](README.de.md) · [Polski](README.pl.md)

A mapping from anime theme songs — openings, endings and insert songs — to songs on Apple Music. Every match was checked against the original recording: covers and live versions are never used, and when Apple Music only has a different edit or performance, the match is labeled as such.

This is the dataset behind the theme song section of the [PaperVN](https://papervn.jizpaper.com) app. It is updated every day and released into the public domain under [CC0 1.0](LICENSE).

## At a Glance

<!-- stats -->
As of version `20261114-d676a2a67db3`:

| | |
|---|---|
| Songs | 38,333 |
| Found on Apple Music | 27,016 |
| Confirmed not on Apple Music | 11,317 |
| Anime | 9,971 |
<!-- /stats -->

## File

Everything is in a single file, [`AniSong-AppleMusic.json`](AniSong-AppleMusic.json), with one song per line so daily changes are easy to diff.

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

### Keys

- **Positive keys** are MyAnimeList theme song IDs — the `id` of each entry in `opening_themes` and `ending_themes` from the MyAnimeList API v2.
- **Negative keys** are insert songs: the negated `annSongId` from AnisongDB.

### Values

`0` means the song has been checked and is not on Apple Music. Otherwise the value is an array:

| Index | Field | Notes |
|---|---|---|
| 0 | Track ID | Apple Music song ID |
| 1 | Artist ID | May be `null` |
| 2 | Title | As written in the Japanese storefront (original language) |
| 3 | Artist | As written in the Japanese storefront |
| 4 | Artwork | 600×600 image URL, may be `null` |
| 5 | Approximate | Optional, see below |
| 6 | Actual title | Optional: the title used in the anime, when it differs |
| 7 | Actual artist | Optional: the performers in the anime, when they differ |
| 8 | Storefront | Optional: present only when the song isn't available in the Japanese storefront, e.g. `"cn"` |

Fields after index 4 are omitted when empty; earlier gaps are filled with `null`. To open a song, use `https://music.apple.com/{storefront or jp}/song/{track ID}`.

A song that isn't listed at all hasn't been checked yet.

### Approximate Matches

When Apple Music doesn't have the original recording, a close substitute may be used and labeled:

- `short` — Only an edited version (for example, TV size) is available.
- `lineup` — The same song performed by a different lineup.
- `version` — Another version of the song by the same artist.

Covers and live recordings sound different, so they're never used as substitutes.

### Indexes

- `inserts` — MyAnimeList anime ID → insert songs found on Apple Music, in AnisongDB order.
- `themes` — MyAnimeList anime ID → opening and ending song keys.

### Version

`version` is the build date (China Standard Time) followed by a content hash. The hash changes whenever the content changes.

## How It's Made

Openings and endings come from MyAnimeList; insert songs come from AnisongDB. Each song is matched against the Apple Music catalog automatically, and uncertain matches are reviewed by hand. Anime from the past 12 months are rechecked every day, so new releases are picked up as they appear on Apple Music.

## Reporting Errors

If a song is matched to the wrong recording or is missing, please [open an issue](https://github.com/JiZPaper/AniSong-AppleMusic/issues) with the key and the correct Apple Music link. You can also report it in PaperVN.

## License

The mapping is dedicated to the public domain under [CC0 1.0 Universal](LICENSE). You can copy, modify and use it for any purpose without asking permission; attribution is appreciated but not required.

Song titles, artist names and artwork belong to their respective rights holders, and artwork URLs point to Apple's servers. Apple Music is a trademark of Apple Inc. MyAnimeList and AnisongDB are the property of their respective owners. This project is not affiliated with or endorsed by any of them.
