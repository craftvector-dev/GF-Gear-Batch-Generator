# GF Gear Batch Generator

**無料評価ベータ v0.7.0-beta.1 / Windows用 Autodesk Fusion Pythonアドイン**

歯車・ラック9種類を、CSV貼り付けや一覧からまとめて生成します。
GF Gear Generator 1.1.1の歯形生成を使用した独立した追加ツールです。元作者やAutodeskの公式製品ではありません。

## ダウンロード

[v0.7.0-beta.1 の配布ページ](https://github.com/craftvector-dev/GF-Gear-Batch-Generator/releases/tag/v0.7.0-beta.1) の Assets から **GF_Gear_Batch-0.7.0-beta.1.zip** を取得してください。
**Source code (zip / tar.gz) は配布案内のアーカイブで、アドイン本体を含みません。** 本体ZIPにPython実装、説明、BSDライセンス、検証資料を同梱しています。

## 今回の追加

- **はすばラック** `helical_rack` と **ダブルヘリカルラック** `double_helical_rack`。
- 共通／行別の種類、12列・17列CSV、AI回答の貼り付けから指定可能。
- 画面の「はすば・やまばラックの入力例」から入力例を表示。
- 元GFのラック処理を使用。やまばは半幅を生成し鏡像結合。widthは両側の全幅。

[ラックのCSVと寸法・左右方向](RACK_INPUT.md) / [コピーできるCSV例](helical-racks.csv) / [今回の検証範囲](RACK_TEST_RESULTS.md)

**新しいラックのFusionカーネル実行・ソリッド生成は未確認です。** オフラインテスト69件は、実際のCAD形状・印刷・歯面接触の成功を意味しません。
端面はGF原型の平面端。V字端面・連続分割・継ぎ目の位相合わせ・取付穴はこのCSV版では生成しません。

## 対応する種類

平歯車、内歯車、はすば、やまば、内歯はすば、内歯やまば、直歯ラック、はすばラック、やまばラック。
外歯車の丸穴・D穴・キー溝、CSV読み込み、AI定型CSV貼り付け、独立Component、X／グリッド配置、高速コピー、失敗分離に対応。
既存の7列／12列／17列CSVとの互換性を維持します。

## 使用方法

1. ZIPを展開し、`GF_Gear_Batch`フォルダー全体を `%APPDATA%\Autodesk\Autodesk Fusion 360\API\AddIns\GF_Gear_Batch` へコピー。
2. 更新時はアドインを停止してから同じフォルダーへ上書きし、再実行。
3. FusionのShift+Sで実行し、履歴付きの**ハイブリッドデザイン**でGF Gear Batchを開く。
4. [定型プロンプト](ai_prompt.txt)をAIに渡し、回答CSVを貼って「検証して一覧に取り込む」→「一括生成」。

元GFの別途インストールやpip、AI用のAPIキーは不要です。
[全種類の入力](GEAR_TYPES.md) / [AI貼り付け](AI_TEXT_INPUT.md) / [D穴・キー溝](BORE_INPUT.md)

## 検証と制限

v0.7.0はオフラインテスト69件合格。GF vendorとBSDライセンスは不変。
旧v0.6.0のFusion実形状17個などは[旧版の検証資料](BORE_TEST_RESULTS.md)です。
新しいラックのFusion実行、再起動、Undo、大規模負荷、他Fusion版、Mac、実印刷、強度は未確認。
はすばは正面（Radial）方式。かさ歯車、ウォーム、Normal方式、転位、STL／STEP一括出力は未対応。
組立位置・歯位相・バックラッシュ・はめあい・収縮補正・強度は自動設計しません。
入力上限は200行・1000個で、性能保証ではありません。

## 利用条件

Batch追加部分は[無料ベータ評価ライセンス](LICENSE.txt)。非商用の学習・評価向けです。
元GFとvendorの改変は[BSD 3-Clause](GF-Gear-Generator-LICENSE.txt)で、これらの権利は制限しません。
Autodesk Fusionの利用条件も適用されます。[第三者ライセンス表示](THIRD_PARTY_NOTICES.md)

[更新履歴](CHANGELOG.md) / [不具合報告](https://github.com/craftvector-dev/GF-Gear-Batch-Generator/issues)
