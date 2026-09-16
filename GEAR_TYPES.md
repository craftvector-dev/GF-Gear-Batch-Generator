# 歯車の種類（v0.5.0）

Fusion 2705.1.15で7種類15個の生成を確認しました。条件と未確認事項は[MULTITYPE_TEST_RESULTS.md](MULTITYPE_TEST_RESULTS.md)を参照してください。

| 画面の種類 | CSVのgear_type | 種類別の指定 |
|---|---|---|
| Spur Gear | spur | 平歯車。Boreは軸穴径 |
| Internal Gear | internal | 標準内歯車。Ringは歯底から外周までの厚み、Bore=0 |
| Helical Gear | helical | はすば。HAはねじれ角、方向はright/left |
| Double Helical Gear | double_helical | やまば。Wは両側を合わせた全幅、方向はZ=0側 |
| Internal Helical Gear | internal_helical | 内歯はすば。Ring、HA、方向を指定、Bore=0 |
| Internal Double Helical Gear | internal_double_helical | 内歯やまば。Ring、HA、方向を指定、Bore=0。Wは全幅 |
| Rack | rack | 直線ラック。歯数、W=厚さ、Base=歯底からの台座高さ、Bore=0 |

## 画面から入力

共通のGear Typeを選び、必要なら「種類別の共通寸法」を開きます。
歯車一覧の「種類」「方向」は「共通」または行別指定を選べます。
Ring、HA、Baseを含む数値欄は空欄なら共通値です。
内歯・ラックを行別指定するときは、その行のBoreを0にしてください。
共通Gear Typeを内歯・ラックへ切り替えると共通Boreは0になります。
手入力で不要な種類別値は無視します。エラー行は生成時に失敗として記録し、後続へ進みます。

## AI／CSVから入力

```csv
name,module,teeth,pressure_angle,width,bore,quantity,gear_type,ring_thickness,helix_angle,handedness,rack_height
Ring40,1,40,20,8,0,1,internal,3,0,right,0
Helix20,1,20,20,8,5,2,helical,0,20,right,0
Rack12,1,12,20,8,0,1,rack,0,0,right,5
```

内歯1個、はすば2個、ラック1個の計4個です。
AI貼り付けでは12項目を全て明記し、使わない寸法は0、使わない方向はrightを指定します。
矛盾した不要寸法も取り込みエラーにします。以前の7列CSVは平歯車として読み込めます。
ファイルCSVの数値の空欄は従来どおり共通設定を使います。

共通範囲は歯数6～250、圧力角14.5～30度、モジュール・Wは正数。
Ring・Baseは使用する種類では正数、HAは0より大きく45度以下です。
角度は度、長さはmm。外歯車のBoreは歯底径未満です。
はすばのモジュールと圧力角はGFのRadial（正面）方式です。
rightはZの増加に伴いXY角度が正方向へ進むねじれ、leftは逆方向として渡します。

## 配置・複製

内歯車は外周厚みを含めて配置します。ラックはローカルXY中心を原点へそろえ、
外形の対角線で余白を確保するため、丸歯車より大きめに間隔が空く場合があります。
噛み合う組立配置や強度計算は行いません。
種類・外周厚み・ねじれ角・方向・台座高さも高速コピーの照合条件に含めます。

## 未対応

かさ歯車、ウォーム、斜歯ラック、非標準内歯車、転位歯車、Normal方式。
