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
