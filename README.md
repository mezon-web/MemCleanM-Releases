# MemCleanM

必要なアプリのために、バックグラウンドアプリのRAM常駐量を整理するWindows向けツールです。アプリごとのメモリ使用量を確認し、用途別プリセットと保護設定で整理対象を管理できます。

## ダウンロード

現在の配布版は **v0.3.2（プレビュー版）** です。

- [MemCleanM-v0.3.2-win-x64.zip](https://github.com/mezon-web/MemCleanM-Releases/releases/download/v0.3.2/MemCleanM-v0.3.2-win-x64.zip)
- [SHA-256確認用ファイル](https://github.com/mezon-web/MemCleanM-Releases/releases/download/v0.3.2/MemCleanM-v0.3.2-win-x64.zip.sha256.txt)
- [画面付きHTMLマニュアル](https://github.com/mezon-web/MemCleanM-Releases/releases/download/v0.3.2/MemCleanM-v0.3.2-Manual-ja.html)（ダウンロードしてブラウザーで開く）
- [リリースの説明](https://github.com/mezon-web/MemCleanM-Releases/releases/tag/v0.3.2) / [配布一覧](https://github.com/mezon-web/MemCleanM-Releases/releases)

Windows 11 x64で検証しています。Windows 10 x64は実機未検証です。.NETランタイムを同梱し、インストールや管理者権限は不要です。

ZIPを展開し、`MemCleanM.exe`を起動してください。ZIPにはアプリと`使い方.txt`・画面付きの`使い方.html`が入っています。このリポジトリは案内・配布専用です。GitHubが自動表示する「Source code」のZIP/tar.gzはこの案内リポジトリの内容で、アプリ本体やアプリのソースコードではありません。

## 使い方

1. 利用可能メモリを確認し、「自動選択」で候補を追加するか、しばらく使わないアプリを選びます。
2. 下部の選択件数を確認して「選択プロセスを整理」を押します。
3. 同じ画面で結果を確認します。30秒後の再計測も履歴に記録します。

「ゲーム前」「画像生成前」など、よく使う組み合わせはプリセットへ登録できます。作業中のアプリや保護設定に登録したアプリは整理対象から除外します。任意で「自動実行 ON」にすると、メモリ不足と低負荷の条件が続く場合だけ整理します。起動時は必ずOFFです。自動起動・ネットワーク通信は行いません。

画面の見方と操作手順は[画面付きHTMLマニュアル](https://github.com/mezon-web/MemCleanM-Releases/releases/download/v0.3.2/MemCleanM-v0.3.2-Manual-ja.html)を参照してください。画像内蔵の1ファイルで、オフラインでも使えます。マニュアル内検索・画面例の拡大・印刷/PDF保存に対応しています。[テキスト版](使い方.txt)もあります。

## 主な機能

- 上端28px相当の統合ヘッダー、ウィンドウ操作とWindows 11スナップ用の入力判定

- 同じEXEのフルパスごとのアプリ集約、PID別の展開、一部選択
- 検索・絞り込みを変えても保持する選択、検索外の選択件数表示
- 用途別プリセットと共通／用途別の保護設定、未起動EXEの登録
- RAM常駐量、Private Bytes、CPU使用率、PC全体のメモリ状況の確認
- 整理直後と30秒後の計測、対象別の結果、最大100件の履歴
- 列幅・列順・ウィンドウ位置の保存、検索や選択のショートカット
- CPU・I/O・GPU・音声・最近の使用を考慮する自動選択
- 任意の自動実行、メモリ不足の継続判定、再整理待機、最小化中の継続とOFFによる停止

## 整理で起きること

Windowsの機能で対象プロセスのRAM常駐量を縮小します。アプリを終了したり、データを破棄したりする操作ではありません。必要になったメモリは再び読み込まれるため、次に使うときに遅くなる場合があります。

常駐量の合計には共有ページも含まれます。減少した常駐量と、PC全体で増えた空きメモリは同じとは限りません。メモリリーク・コミット上限・GPUのVRAM不足を解消するものではありません。メモリに余裕がある場合は整理不要です。

## 設定と更新

設定と履歴は`%LOCALAPPDATA%\MemCleanM`へ保存します。更新するときはアプリを終了し、新しいZIPを展開して起動してください。設定は引き継がれます。

## ファイルの確認

ZIPとSHA-256確認用ファイルを同じフォルダへ保存し、PowerShellで比較してください。

```powershell
Get-FileHash .\MemCleanM-v0.3.2-win-x64.zip -Algorithm SHA256
Get-Content .\MemCleanM-v0.3.2-win-x64.zip.sha256.txt
```

## 変更履歴

[v0.3.2の変更内容](release-notes/v0.3.2.md)
