# はすば・やまばラックのCSV入力（v0.7.0）

`helical_rack` と `double_helical_rack` を追加しました。
「AIの回答を貼り付け」→「はすば・やまばラックの入力例」→「検証して一覧に取り込む」→「一括生成」で使用できます。
共通／行別の種類選択、ファイルCSV、既存の12列・17列CSVでも指定できます。

```csv
name,module,teeth,pressure_angle,width,bore,quantity,gear_type,ring_thickness,helix_angle,handedness,rack_height,bore_type,d_flat_depth,key_width,key_depth,bore_angle
RackDoubleR,2,30,20,15,0,3,double_helical_rack,0,25,right,3.5,round,0,0,0,0
RackDoubleL,2,30,20,15,0,3,double_helical_rack,0,25,left,3.5,round,0,0,0,0
```

上の例は右向き3個・左向き3個、計6個です。直歯ラックは従来の `rack` です。

| 項目 | 意味 |
|---|---|
| module / pressure_angle | 正面（Radial）方式。法線（Normal）方式は未対応 |
| teeth | GF原型の歯数6～250。全長の指定値ではありません |
| width | 全幅mm。やまばは半幅で生成し鏡像結合するので、15なら7.5＋7.5 mm |
| helix_angle | 0より大きく45度以下。直歯 `rack` では0 |
| handedness | rightは+Zに進むと歯すじがローカル+Xへ傾く向き、leftは-X。やまばは前半の向き |
| rack_height | 歯底から背面までの台座高さmm。背面～ピッチ線の寸法ではありません |
| bore / bore_type | 穴加工なし。必ず0 / round |

例のm2・20°では1ピッチは2π＝約6.283185 mm、歯の高さは4.5 mm、台座3.5 mmなら総高さ8 mmです。
歯数×ピッチは分割基準長であり、GF原型の端形状・斜歯のはみ出しを含む外形長とは一致しません。

端はGF原型の平面端です。このCSV版はV字端面・30歯分の連続分割・取付穴・継ぎ目位相合わせを生成しません。
同じ歯位相から独立生成した部品を、歯数×ピッチの位置へ移すだけで連続ラックになるとは限りません。
今回のV字分割機構用の専用スクリプトとは別機能です。

ラックは生成後にローカルXY外形の中心を原点へそろえ、Zは0～全幅で配置します。
左右の指定はラック自身のローカル座標基準です。相手ギアとの組立向き・歯位相は実際の配置で確認してください。
配置は部品を離して並べるためのものです。ギアとのかみ合う位置へは配置しません。

入力・GF呼び出し契約・配置範囲のオフラインテストを実施しました。
新しいCSV版のFusionカーネル実行、ソリッド生成、歯面接触、印刷、強度は未確認です。
