# HALFTONE LAB

画像・プロシージャルソースをハーフトーン / ディザ / ASCII / モザイクに変換する、依存ゼロ・単一HTMLのデザインツール。
アニメーション（リップル / シェイプ / LEDブロック / サウンド波形）とWebM録画、SVG書き出し、コーダー向けコード書き出しに対応。

**→ 公開URL（GitHub Pages 設定後）: `https://<あなたのユーザー名>.github.io/halftone-lab/`**

## 主な機能

- **19のディザアルゴリズム** — 誤差拡散11種（Floyd–Steinberg / Atkinson / JJN / Stucki / Burkes / Sierra系 / Stevenson–Arce / Riemersma ほか）+ serpentine走査 + 誤差強度、Bayer 2–16 / ブルーノイズ / IGN ほか
- **面積補正ハーフトーン** — `r = cell·0.7071·√ink`（被覆面積∝r²の平方根補正）で正確な中間調
- **プロシージャルソース** — 同心円リップル / 回転シェイプ / LEDブロック点滅 / サウンド波形（シンメトリー・EQバー・オシロライン）
- **マスク** — 斜めバンド / サークル
- **書き出し** — 元解像度PNG（最近傍拡大）/ SVGベクター / クリップボード / WebM録画（3–8秒）/ **コード書き出し**（現在の見た目を再現する依存ゼロの単体HTML — コーダーにそのまま渡せる）
- **保存と共有** — マイプリセット（ブラウザ保存）/ 設定トークン / **共有リンク**（`#s=<token>` — URLを開くだけで同じ設定を復元）
- 分割比較・ズーム/パン・リニアライト処理・すべてブラウザ内処理（サーバー送信なし）

## ローカルで使う

`index.html` をブラウザで開くだけです。ビルド不要・依存なし。

## 公開する（GitHub Pages）

このフォルダで以下を実行（[gh CLI](https://cli.github.com/) がある場合）:

```bash
gh repo create halftone-lab --public --source=. --push
gh api repos/{owner}/halftone-lab/pages -X POST \
  -f "source[branch]=main" -f "source[path]=/"
```

数分後に `https://<ユーザー名>.github.io/halftone-lab/` で公開されます。

gh がない場合は、GitHubでリポジトリを作成してから:

```bash
git remote add origin https://github.com/<ユーザー名>/halftone-lab.git
git push -u origin main
```

その後 GitHub の **Settings → Pages → Branch: main / (root) → Save** で公開。

以降の更新は `git add -A && git commit -m "..." && git push` だけで自動反映されます。

## シェアの仕方

- **ツールを共有** → Pages のURLを渡す
- **「この見た目」を共有** → ツール内の **🔗 共有リンク** ボタン。設定一式がURLに埋め込まれ、開いた人は同じ状態から始められます
- **実装として渡す** → **⟨/⟩ コードで書き出し** で生成される `halftone-lab-embed.html` を渡す（冒頭の `state` を書き換えるだけで調整可能）

## リポジトリ構成

```
index.html               ツール本体（単一ファイル・依存ゼロ）
docs/teardown-report.html  競合9ツールの分解リサーチレポート
docs/references.html       リファレンス集（開発時の参考資料）
```

## ライセンス

MIT
