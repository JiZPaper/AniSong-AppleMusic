# AniSong-AppleMusic

[English](README.md) · [简体中文](README.zh-Hans.md) · [繁體中文](README.zh-Hant.md) · **日本語** · [한국어](README.ko.md) · [Deutsch](README.de.md) · [Polski](README.pl.md)

アニメの主題歌（オープニング、エンディング、挿入歌）とApple Musicの曲の対応表です。すべての曲をオリジナル音源と照合しています。カバーやライブ音源は使わず、Apple Musicに別の編集やほかの歌唱版しかない場合は、近似バージョンであることを明記しています。

[PaperVN](https://papervn.jizpaper.com) Appの「主題歌」セクションで使われているデータです。毎日更新され、[CC0 1.0](LICENSE)でパブリックドメインに提供しています。

## 概要

<!-- stats -->
バージョン`20261110-d811aa2eb306`時点：

| | |
|---|---|
| 曲 | 38,236曲 |
| Apple Musicで見つかった曲 | 26,946曲 |
| Apple Musicにないことを確認した曲 | 11,290曲 |
| アニメ | 9,959作品 |
<!-- /stats -->

## ファイル

すべてのデータは[`AniSong-AppleMusic.json`](AniSong-AppleMusic.json)の1ファイルにまとまっています。1行に1曲なので、毎日の差分を比較しやすくなっています。

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

### キー

- **正の数**はMyAnimeListの主題歌IDです。MyAnimeList API v2の`opening_themes`と`ending_themes`の各項目の`id`です。
- **負の数**は挿入歌で、AnisongDBの`annSongId`の符号を反転したものです。

### 値

`0`は照合済みで、Apple Musicにその曲がないことを示します。それ以外は配列です：

| 位置 | 内容 | 説明 |
|---|---|---|
| 0 | 曲ID | Apple Musicの曲ID |
| 1 | アーティストID | `null`の場合があります |
| 2 | 曲名 | 日本のストアでの表記（原語） |
| 3 | アーティスト | 日本のストアでの表記 |
| 4 | アートワーク | 600×600の画像URL。`null`の場合があります |
| 5 | 近似バージョン | 任意。下記を参照 |
| 6 | 実際の曲名 | 任意。アニメで使われた曲名と異なる場合のみ |
| 7 | 実際のアーティスト | 任意。アニメでの歌唱者と異なる場合のみ |
| 8 | ストア | 任意。日本のストアにない曲の場合のみ。例：`"cn"` |

4番目より後の項目は空の場合省略され、途中の空きは`null`で埋められます。曲を開くリンクは`https://music.apple.com/{ストア、ない場合はjp}/song/{曲ID}`です。

ファイルにない曲はまだ照合されていません。

### 近似バージョン

Apple Musicにオリジナル音源がない場合、近いバージョンで代用し、印を付けることがあります：

- `short`：編集版（TVサイズなど）しかない。
- `lineup`：同じ曲を別のメンバー構成で歌ったもの。
- `version`：同じアーティストによる別バージョン。

カバーやライブ音源は聞こえ方が違うため、代用には使いません。

### インデックス

- `inserts`：MyAnimeListのアニメID → Apple Musicで見つかった挿入歌（AnisongDBの順）。
- `themes`：MyAnimeListのアニメID → オープニングとエンディングのキー。

### バージョン

`version`は生成日（中国標準時）とコンテンツのハッシュです。内容が変わるとハッシュも変わります。

## 作成方法

オープニングとエンディングはMyAnimeList、挿入歌はAnisongDBから取得しています。各曲をApple Musicのカタログと自動で照合し、確信度の低いものは人の手で確認しています。過去12か月のアニメは毎日再確認しているため、Apple Musicに新しく配信された曲も順次反映されます。

## エラーの報告

曲が違う音源に対応付けられている、または抜けている場合は、キーと正しいApple Musicのリンクを添えて[Issueを作成](https://github.com/JiZPaper/AniSong-AppleMusic/issues)してください。PaperVNからも報告できます。

## ライセンス

この対応表は[CC0 1.0 Universal](LICENSE)によりパブリックドメインに提供されています。許可なくコピー、改変し、あらゆる目的に使用できます。出典の表示は歓迎しますが、必須ではありません。

曲名、アーティスト名、アートワークはそれぞれの権利者に帰属し、アートワークのURLはAppleのサーバを指しています。Apple MusicはApple Inc.の商標です。MyAnimeListとAnisongDBはそれぞれの所有者に帰属します。このプロジェクトはこれらのいずれとも提携しておらず、承認も受けていません。
