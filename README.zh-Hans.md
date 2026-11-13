# AniSong-AppleMusic

[English](README.md) · **简体中文** · [繁體中文](README.zh-Hant.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Deutsch](README.de.md) · [Polski](README.pl.md)

动画主题曲（片头曲、片尾曲和插入曲）与Apple Music歌曲的对应表。每一首都按原版录音核对过：不使用翻唱和现场版；Apple Music只有其他剪辑或其他演唱版本时，会标明是近似版本。

这是[PaperVN](https://papervn.jizpaper.com) App“主题曲”区块所用的数据，每天更新，以[CC0 1.0](LICENSE)贡献到公有领域。

## 概览

<!-- stats -->
截至版本`20261114-d676a2a67db3`：

| | |
|---|---|
| 歌曲 | 38,333首 |
| 在Apple Music上找到 | 27,016首 |
| 确认Apple Music上没有 | 11,317首 |
| 动画 | 9,971部 |
<!-- /stats -->

## 文件

全部数据在[`AniSong-AppleMusic.json`](AniSong-AppleMusic.json)这一个文件里，每行一首歌，方便比较每天的变化。

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

### 键

- **正数**是MyAnimeList的主题曲ID，即MyAnimeList API v2中`opening_themes`和`ending_themes`每一项的`id`。
- **负数**是插入曲：AnisongDB的`annSongId`取负。

### 值

`0`表示已经核对过，Apple Music上没有这首歌。其余是一个数组：

| 位置 | 内容 | 说明 |
|---|---|---|
| 0 | 歌曲ID | Apple Music的歌曲ID |
| 1 | 艺人ID | 可能为`null` |
| 2 | 歌名 | 日本商店的写法（原语言） |
| 3 | 艺人 | 日本商店的写法 |
| 4 | 封面 | 600×600图像地址，可能为`null` |
| 5 | 近似版本 | 可选，见下文 |
| 6 | 实际歌名 | 可选：与动画中使用的歌名不同时才有 |
| 7 | 实际艺人 | 可选：与动画中的演唱者不同时才有 |
| 8 | 商店地区 | 可选：只在日本商店没有这首歌时才有，例如`"cn"` |

第4项之后的内容为空时省略，中间的空缺用`null`补齐。打开歌曲的链接是`https://music.apple.com/{商店地区，没有时为jp}/song/{歌曲ID}`。

文件里没有列出的歌曲表示还没有核对。

### 近似版本

Apple Music上没有原版录音时，可能会用相近的版本代替并加上标记：

- `short`：只有剪辑版本（例如TV Size）。
- `lineup`：同一首歌，演唱阵容不同。
- `version`：同一艺人的其他版本。

翻唱和现场录音听起来不一样，不会用来代替。

### 索引

- `inserts`：MyAnimeList动画ID → 在Apple Music上找到的插入曲，按AnisongDB的顺序。
- `themes`：MyAnimeList动画ID → 片头曲和片尾曲的键。

### 版本

`version`是生成日期（北京时间）加上内容摘要，内容有变化时摘要就会改变。

## 制作方式

片头曲和片尾曲来自MyAnimeList，插入曲来自AnisongDB。每首歌先在Apple Music目录中自动匹配，不确定的再人工复核。最近12个月的动画每天重新检查，新上架到Apple Music的歌曲会陆续补上。

## 报告错误

如果某首歌配错了录音或者缺失，请[创建Issue](https://github.com/JiZPaper/AniSong-AppleMusic/issues)，写上键和正确的Apple Music链接。也可以在PaperVN中报告。

## 许可

此对应表以[CC0 1.0通用](LICENSE)贡献到公有领域。你可以拷贝、修改并用于任何目的，无需获得许可；欢迎注明出处，但不是必须的。

歌名、艺人名称和封面归各自的权利人所有，封面地址指向Apple的服务器。Apple Music是Apple Inc.的商标。MyAnimeList和AnisongDB归各自的所有者所有。此项目与上述各方均无关联，也未获得其认可。
