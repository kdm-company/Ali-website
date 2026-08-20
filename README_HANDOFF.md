# ALI Website Renewal — Handoff

## Build
- Version: old-site-restore v2（旧HP尊重版）
- Built: 2026-08-19
- 設計の正本: Notion「エイエルアイ サイト設計書」／旧サイト全文は「ALi旧サイト（ali2016.jp）テキスト・画像アーカイブ」
- Entry point: `index.html`

## Pages
- `/` → `index.html`（ヘッダー → ヒーロー → 旧スローガン → お知らせ → ALIにできること5項目 → WORKS → RECRUIT → CONTACT）
- `/tech` → `tech/index.html`（強み／加工事例／エイエルアイに出来ること Q&A・6件／設備一覧）
- `/company` → `company/index.html`（代表挨拶＝旧HP原文・写真なし構成／会社概要＝事業内容5項目・3工場／沿革／品質方針／アクセス＝地図埋め込み）
- `/recruit` → `recruit/index.html`（旧HPの募集要項・給与を復元。年齢不問・性別限定なし、電話は代表番号に統一）
- `/news` → `news/index.html`（旧HP全30記事を本文付きアコーディオンで全件掲載）
- `/contact` → `contact/index.html`（フォームは mailto 方式で info@ali2016.jp に送信）
- `/privacy`・`/sitemap` → 本文実装済み

## 2026-08-19 の主な修正
- 旧スローガン全文（ⓈⓅⓅⓞⓝ の一節を含む）をヒーロー直下に復元。文言は一字一句変更していない。
- 「ALIにできること」を旧HP /about の事業内容5項目に修正。
- 旧サイト画像（cdn.goope.jp 直リンク12点）を `assets/images/old/` にダウンロードしてローカル参照化。旧サイト解約後も表示が消えない。
- CTA背景のプレースホルダー表示（「背景写真（PC 1920×560 相当）」の文字）を撤去し、社員集合写真を適用。
- アンカー切れ（#turning/#machining/#works）、ダミーリンク（href="#"）、誤字（頃る／支えゃ／ご覚 等）、本番に出ていた内部メモ（「台数要確認」「確認後に追記」「現行条件要確認」）を修正。

## Remaining production checks
- ISO9001の認証番号・認定機関名は登録証を確認して品質方針セクションに追記する（推測での記載はしない方針）。
- FANUC ROBODRILL α-D21LiB5 は実台数が確定できないため「複数台」表記。確定後に台数へ差し替える。設備一覧のリード文も合計台数を出さない表現にしている。
- 代表写真（旧 `14-president.webp`）は代表本人と確認できないため削除済み。代表挨拶は写真なしで成立。実写真を入手したら差し替え可。
- お問い合わせフォームは mailto 方式で確定（今回対応分）。サーバーサイド送信が必要になったらフォームサービス導入を検討。

## Preview
```bash
python3 -m http.server 8080
```

---

## 2026-08-20 の修正（山上さんフィードバック対応）

### 1. 全体カラー
白＋赤（`--c-red:#E31E24`）の方向性は好評のため変更なし。

### 2. 加工事例の写真のバラつき
工場全景・製品マクロ・メーカー資料の切り抜きが混在していたため、
**実際の加工品／工程写真3点に統一**（TOP・技術ページとも同じ3点）。
`.work__ph` / `.card__ph` で高さとトリミングを統一しているので、
**写真を差し替えるだけでレイアウトは崩れません**（今後の差し替え前提）。

### 3. 動き
- ヒーロー：**6秒ごとの自動切替**（従来はJSがなく静止していた）＋ゆるやかなズーム、
  インジケーターをPC/SPとも表示・クリック可
- 全ページ：スクロールに合わせた淡いフェードイン（並び順に70msずつ遅延）
- `prefers-reduced-motion: reduce` の環境では自動的に無効化
- 表示制御はスクロール量で行っており、万一処理が止まっても内容が隠れたままにならない実装

#### 動画の組み込みについて（未実施・素材待ち）
ヒーローに動画を入れる場合は `assets/video/hero.mp4`（＋静止画 `hero-poster.jpg`）を置き、
`index.html` のヒーロー1枚目を下記に差し替えれば有効になります。
```html
<div class="set002-hero__slide set002-is-active">
  <video class="set002-hero__ph" autoplay muted loop playsinline
         poster="assets/images/old/old-factory-machines.jpg"
         style="object-fit:cover">
    <source src="assets/video/hero.mp4" type="video/mp4">
  </video>
</div>
```
※ 動画ファイルをお預かりでき次第、圧縮・SP用の静止画差し替え・自動再生の可否まで含めて実装します。

### 4. 各ページTOPの写真
5ページすべて別の写真に変更し、内容に合うものを割り当て（`asset-manifest.json` 参照）。
メーカー資料の白背景切り抜き（マシニングセンタ等）は**設備一覧の図版**へ移動し、
ページヘッダーやKVからは外しました。

### 5. 会社案内の従業員写真
旧メンバーが写る帯を削除。あわせて以下3点はサイト全体で不使用とし、リポジトリからも削除しました。
- `old-workplace.jpg`（氏名入りの個人写真）
- `old-factory2-exterior.jpg`（集合写真）
- `old-award-mono.jpg`（受賞時の2名）

### 今後の差し替え候補（優先度順）
1. お知らせ・お問い合わせページのヘッダー写真（内容との一致度が低い）
2. 加工事例3点（半導体装置向けの実製品写真があるとより説得力が出ます）
3. 採用ページの職場写真（現メンバーでの撮影）

## 2026-08-20 追加分（先方フィードバック対応）
- お知らせ／お問い合わせのヘッダーを**新規撮影の実写**に差し替え。
  - お知らせ = `assets/images/photo/01-factory-interior.jpg`（工場内観）
  - お問い合わせ = `assets/images/photo/15-factory-exterior.jpg`（本社工場外観）
- TOPに**会社紹介動画セクション（`#movie`）**を新設。YouTube限定公開動画「ALIのPV1」を埋め込み。
  - サムネイルがクリックされるまでYouTubeを読み込まない方式。未クリックなら外部リクエストもCookieも発生せず、表示速度に影響しない。
  - 埋め込み先は `youtube-nocookie.com`。
  - ポスター画像は自社の内観写真を使用（YouTube側のサムネイルには従業員が写るため不使用）。
- 支給された元PNGは `.gitignore` に追加。配信には `assets/images/photo/` の最適化JPEG（各約140KB）を使用。

### 動画を差し替える場合
`index.html` の `data-yt="CQzsZ1BKZSU"` を新しい動画IDに変更するだけで差し替わる。
ポスター画像は CSS の `.mv__poster` の `background-image` で指定している。

### 今後の写真差し替え
`tech` / `company` / `recruit` のヘッダーは旧サイト素材のまま。新規撮影分が揃い次第の差し替えを推奨。
割当は `asset-manifest.json` の `imageAssignments` に集約している。
