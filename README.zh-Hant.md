# AniSong-AppleMusic

[English](README.md) · [简体中文](README.zh-Hans.md) · **繁體中文** · [日本語](README.ja.md) · [한국어](README.ko.md) · [Deutsch](README.de.md) · [Polski](README.pl.md)

動畫主題曲（片頭曲、片尾曲和插曲）與Apple Music歌曲的對照表。每一首都按原版錄音核對過：不使用翻唱和現場版；Apple Music只有其他剪輯或其他演唱版本時，會標明是近似版本。

這是[PaperVN](https://papervn.jizpaper.com) App「主題曲」區塊所用的資料，每天更新，以[CC0 1.0](LICENSE)貢獻到公眾領域。

## 概覽

<!-- stats -->
截至版本`20261111-6e5a6212ee0c`：

| | |
|---|---|
| 歌曲 | 38,243首 |
| 在Apple Music上找到 | 26,953首 |
| 確認Apple Music上沒有 | 11,290首 |
| 動畫 | 9,969部 |
<!-- /stats -->

## 檔案

全部資料在[`AniSong-AppleMusic.json`](AniSong-AppleMusic.json)這一個檔案裡，每行一首歌，方便比較每天的變化。

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

### 鍵

- **正數**是MyAnimeList的主題曲ID，即MyAnimeList API v2中`opening_themes`和`ending_themes`每一項的`id`。
- **負數**是插曲：AnisongDB的`annSongId`取負。

### 值

`0`表示已經核對過，Apple Music上沒有這首歌。其餘是一個陣列：

| 位置 | 內容 | 說明 |
|---|---|---|
| 0 | 歌曲ID | Apple Music的歌曲ID |
| 1 | 藝人ID | 可能為`null` |
| 2 | 歌名 | 日本商店的寫法（原語言） |
| 3 | 藝人 | 日本商店的寫法 |
| 4 | 封面 | 600×600影像網址，可能為`null` |
| 5 | 近似版本 | 選用，見下文 |
| 6 | 實際歌名 | 選用：與動畫中使用的歌名不同時才有 |
| 7 | 實際藝人 | 選用：與動畫中的演唱者不同時才有 |
| 8 | 商店地區 | 選用：只在日本商店沒有這首歌時才有，例如`"cn"` |

第4項之後的內容為空時省略，中間的空缺用`null`補齊。打開歌曲的連結是`https://music.apple.com/{商店地區，沒有時為jp}/song/{歌曲ID}`。

檔案裡沒有列出的歌曲表示還沒有核對。

### 近似版本

Apple Music上沒有原版錄音時，可能會用相近的版本代替並加上標記：

- `short`：只有剪輯版本（例如TV Size）。
- `lineup`：同一首歌，演唱陣容不同。
- `version`：同一藝人的其他版本。

翻唱和現場錄音聽起來不一樣，不會用來代替。

### 索引

- `inserts`：MyAnimeList動畫ID → 在Apple Music上找到的插曲，按AnisongDB的順序。
- `themes`：MyAnimeList動畫ID → 片頭曲和片尾曲的鍵。

### 版本

`version`是產生日期（北京時間）加上內容摘要，內容有變化時摘要就會改變。

## 製作方式

片頭曲和片尾曲來自MyAnimeList，插曲來自AnisongDB。每首歌先在Apple Music目錄中自動比對，不確定的再人工複核。最近12個月的動畫每天重新檢查，新上架到Apple Music的歌曲會陸續補上。

## 回報錯誤

如果某首歌配錯了錄音或是缺漏，請[建立Issue](https://github.com/JiZPaper/AniSong-AppleMusic/issues)，寫上鍵和正確的Apple Music連結。也可以在PaperVN中回報。

## 授權

此對照表以[CC0 1.0通用](LICENSE)貢獻到公眾領域。你可以拷貝、修改並用於任何目的，無需取得許可；歡迎註明出處，但並非必要。

歌名、藝人名稱和封面歸各自的權利人所有，封面網址指向Apple的伺服器。Apple Music是Apple Inc.的商標。MyAnimeList和AnisongDB歸各自的擁有者所有。此專案與上述各方均無關聯，也未獲得其認可。
