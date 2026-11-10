# AniSong-AppleMusic

[English](README.md) · [简体中文](README.zh-Hans.md) · [繁體中文](README.zh-Hant.md) · [日本語](README.ja.md) · **한국어** · [Deutsch](README.de.md) · [Polski](README.pl.md)

애니메이션 주제가(오프닝, 엔딩, 삽입곡)와 Apple Music 노래의 대응표입니다. 모든 곡은 원곡 음원과 대조했습니다. 커버나 라이브 버전은 사용하지 않으며, Apple Music에 다른 편집본이나 다른 가창 버전만 있는 경우 근사 버전임을 표시합니다.

[PaperVN](https://papervn.jizpaper.com) 앱의 '주제가' 섹션에서 사용하는 데이터입니다. 매일 업데이트되며 [CC0 1.0](LICENSE)으로 퍼블릭 도메인에 공개합니다.

## 개요

버전 `20261110-d811aa2eb306` 기준:

| | |
|---|---|
| 노래 | 38,236곡 |
| Apple Music에서 찾은 노래 | 26,946곡 |
| Apple Music에 없음을 확인한 노래 | 11,290곡 |
| 애니메이션 | 9,959편 |

## 파일

모든 데이터는 [`AniSong-AppleMusic.json`](AniSong-AppleMusic.json) 파일 하나에 들어 있습니다. 한 줄에 한 곡씩 기록되어 있어 매일의 변경 사항을 비교하기 쉽습니다.

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

### 키

- **양수**는 MyAnimeList 주제가 ID로, MyAnimeList API v2의 `opening_themes`와 `ending_themes` 각 항목의 `id`입니다.
- **음수**는 삽입곡으로, AnisongDB의 `annSongId`에 음수 부호를 붙인 값입니다.

### 값

`0`은 이미 대조했으며 Apple Music에 해당 노래가 없다는 뜻입니다. 그 외에는 배열입니다:

| 위치 | 내용 | 설명 |
|---|---|---|
| 0 | 노래 ID | Apple Music 노래 ID |
| 1 | 아티스트 ID | `null`일 수 있음 |
| 2 | 노래 제목 | 일본 스토어 표기(원어) |
| 3 | 아티스트 | 일본 스토어 표기 |
| 4 | 아트워크 | 600×600 이미지 URL, `null`일 수 있음 |
| 5 | 근사 버전 | 선택 사항, 아래 참조 |
| 6 | 실제 제목 | 선택 사항: 애니메이션에서 사용한 제목과 다를 때만 |
| 7 | 실제 아티스트 | 선택 사항: 애니메이션의 가창자와 다를 때만 |
| 8 | 스토어 | 선택 사항: 일본 스토어에 없는 노래만, 예: `"cn"` |

4번 이후의 항목은 비어 있으면 생략되고, 중간의 빈자리는 `null`로 채웁니다. 노래를 여는 링크는 `https://music.apple.com/{스토어, 없으면 jp}/song/{노래 ID}`입니다.

파일에 없는 노래는 아직 대조하지 않은 것입니다.

### 근사 버전

Apple Music에 원곡 음원이 없을 때는 비슷한 버전으로 대신하고 표시를 붙일 수 있습니다:

- `short`: 편집본(예: TV 사이즈)만 있음.
- `lineup`: 같은 곡을 다른 멤버 구성으로 부른 버전.
- `version`: 같은 아티스트의 다른 버전.

커버와 라이브 음원은 다르게 들리므로 대신 사용하지 않습니다.

### 인덱스

- `inserts`: MyAnimeList 애니메이션 ID → Apple Music에서 찾은 삽입곡(AnisongDB 순서).
- `themes`: MyAnimeList 애니메이션 ID → 오프닝과 엔딩의 키.

### 버전

`version`은 생성 날짜(중국 표준시)와 콘텐츠 해시입니다. 내용이 바뀌면 해시도 바뀝니다.

## 만드는 방법

오프닝과 엔딩은 MyAnimeList, 삽입곡은 AnisongDB에서 가져옵니다. 각 노래를 Apple Music 카탈로그와 자동으로 대조하고, 확실하지 않은 것은 사람이 직접 확인합니다. 최근 12개월의 애니메이션은 매일 다시 확인하므로 Apple Music에 새로 공개된 노래도 차례로 반영됩니다.

## 오류 신고

노래가 잘못된 음원에 연결되어 있거나 빠져 있다면 키와 올바른 Apple Music 링크를 적어 [Issue를 만들어](https://github.com/JiZPaper/AniSong-AppleMusic/issues) 주십시오. PaperVN에서도 신고할 수 있습니다.

## 라이선스

이 대응표는 [CC0 1.0 Universal](LICENSE)에 따라 퍼블릭 도메인에 공개됩니다. 허락 없이 복사, 수정하여 어떤 목적으로든 사용할 수 있습니다. 출처를 밝혀 주시면 감사하지만 필수는 아닙니다.

노래 제목, 아티스트 이름, 아트워크는 각 권리자에게 있으며, 아트워크 URL은 Apple의 서버를 가리킵니다. Apple Music은 Apple Inc.의 상표입니다. MyAnimeList와 AnisongDB는 각 소유자의 자산입니다. 이 프로젝트는 이들 중 어느 곳과도 제휴하거나 승인을 받지 않았습니다.
