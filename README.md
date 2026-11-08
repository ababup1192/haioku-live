# 廃屋配信

縦型のホラーノベル（ブラウザ版）。flix_game_engine 0.88.4 で作成。このリポジトリは書き出したゲームだけを置いています。

遊ぶ: https://ababup1192.github.io/haioku-live/

# 素材の出典とライセンス

『廃屋配信』の背景と怪異の画像・フォント・効果音と BGM の出典です。
ゲームの中のクレジット（タイトル画面の「クレジット」と、物語を読み終えた後）にも同じ表記を流します（`assets/novel.credits.json`）。
素材を差し替えたら、ここと `assets/novel.credits.json` の両方を書き直してください。

## 背景と怪異の画像

どれも本作の制作者が Codex で生成した画像です（作者は制作者）。夜の廃屋をスマホのカメラで撮ったように見える縦長の絵で、
ゲームの中ではシェーダーでセンサーのざらつき・四隅の落ち・ライトの丸い光を足して表示します（`src/Backdrop.flix`）。

| ファイル | 場面 |
|---|---|
| `assets/bg/gate.jpg` | 門の前（タイトル画面にも使う） |
| `assets/bg/entrance_out.jpg` | 玄関の前 |
| `assets/bg/genkan.jpg` | 玄関 |
| `assets/bg/hall1.jpg` | 一階の廊下 |
| `assets/bg/living.jpg` | 居間 |
| `assets/bg/kitchen.jpg` | 台所 |
| `assets/bg/stairs.jpg` | 階段（見上げ） |
| `assets/bg/stairs_down.jpg` | 階段（見下ろし。逃げて駆け下りる所） |
| `assets/bg/hall2.jpg` | 二階の廊下 |
| `assets/bg/room1.jpg` | 二階の一つ目の部屋 |
| `assets/bg/room_back.jpg` | 二階の奥の部屋 |
| `assets/bg/oshiire.jpg` | 押し入れの中 |
| `assets/bg/hall_endless.jpg` | 終わらない廊下 |
| `assets/bg/kaii_window.png` | 窓際の人影（使う所だけに切り抜いて縮めた透過 PNG） |
| `assets/bg/kaii_gap.png` | 襖の隙間越しの片目と髪（同上） |
| `assets/bg/blood_color.jpg`・`assets/bg/blood_key.png` | レンズを垂れる血（垂れの絵と、垂れの濃さ・届く時刻の地図を 540×960 に縮め、濃さと時刻を 1 枚の R と G にまとめた物） |

## 3D の場面の切り替え

`assets/walk/<場面>.glb` と `.jpg` は、上の背景の画像を Blender で粗い箱に投影して書き出した物です（本作の制作者が作成）。
`.jpg` は投影した絵を 1098×1920 に縮めた物、`assets/walk/walks.json` は Blender で作ったカメラの道筋・音の時刻・揺れの数です。

## フォント

- **しっぽり明朝**（`assets/ShipporiMincho-Regular.subset.ttf`）— Copyright 2021 The Shippori Mincho Project Authors
  （https://github.com/fontdasu/ShipporiMincho）。[SIL Open Font License 1.1](assets/OFL.txt)。
  JIS 第 1 水準の漢字・かな・英数と、シナリオ・画面の言葉に出てくる字だけを残した部分集合（サブセット）です。
  元のフォントに無い半角カナ（ｩ・ｽ）と ≠ は、元のフォントの全角の字を横に縮めた物・＝に／を重ねた物を合成の字として足しています。
  字を足した時は、元のフォントを用意して `make font-subset FONT_DIR=<元のフォントのフォルダ>` で作り直してください（作り直すまで、その字は表示されません）。
- **M PLUS 1p**（Bold・Medium。`assets/MPLUS1p-Bold.subset.ttf`・`assets/MPLUS1p-Medium.subset.ttf`）— Copyright 2016 The M+ Project Authors
  （https://github.com/coz-m/MPLUS_FONTS）。[SIL Open Font License 1.1](assets/OFL-MPLUS1p.txt)。
  配信の表示・スマホの状態バー（Bold）とコメント欄（Medium）に使うゴシック体。英数・かなと、シナリオ・画面の言葉に出てくる字だけを残したサブセットです。

## 音

効果音と BGM は、次の 2 つの配布元の素材を加工して使っています（どれも 16bit・モノラルの wav。
効果音と環境音は 32000 Hz、BGM は 22050 Hz。先頭の無音を切り、音量をおおよそそろえています）。
元のページと加工の中身は 1 本ずつ `assets/sfx/` の名前ごとに下の表にあります。

### 効果音・環境音 — 効果音ラボ（https://soundeffect-lab.info/）

規約（https://soundeffect-lab.info/agreement/）の要点:
商用・非商用とも無料で、ゲームへの組み込みは可。クレジット表記・報告・リンクは不要（任意）。
**効果音ファイルそのものの再配布は禁止**（加工した物の再配布も禁止）。直リンク禁止。AI の学習用データに使うのは禁止。

| ファイル | 元の音（効果音ラボでの名前） | 加工 |
|---|---|---|
| `amb_wind.wav` | 風が吹く3（環境音） | 19.5 秒を切り出し、頭と尾を 2 秒重ねてループ |
| `amb_house.wav` | シーンと静まり返る教室（環境音） | 低い音だけ残し、頭と尾を 2.5 秒重ねてループ |
| `se_cloth.wav` | 衣擦れ2（生活3） | |
| `se_gate.wav` | 門を開ける（生活） | |
| `se_door_heavy.wav` | 古びたドアを開ける（生活） | 音を低くして重く |
| `se_creak.wav` | 古びたドアを開ける（生活） | 軋みの頭 0.4 秒を低くして床板の音に |
| `se_timer.wav` | 携帯電話の着信音1（機械） | 最初のピピピピを 2 回つなぐ |
| `se_sliding.wav` | 引き戸を開ける2（生活） | |
| `se_groan.wav` | ゾンビの声1（戦闘2） | 高い音を削って小さめに |
| `se_groan_far.wav` | ゾンビの断末魔（戦闘2） | 低く・こもらせ・残響を足して遠くに |
| `se_knob.wav` | ドアノブをひねる1（生活） | ゆっくりに |
| `se_splash.wav` | 血がたれる1（戦闘） | |
| `se_run.wav` | 学校の廊下を走る＋古びたドアを開ける（生活） | 駆け足に床の軋みを 3 つ重ねる |
| `se_stairs_slow.wav` | 家の階段を下りる＋古びたドアを開ける（生活） | 1 歩と軋みを 1.15 秒おきに 4 回 |
| `se_stairs_down.wav` | 家の階段を下りる（生活） | 1.6 倍の速さ |
| `se_stairs_up.wav` | 家の階段を駆け上る（生活） | |
| `se_door_slam.wav` | ドアを閉める1（生活） | |
| `se_lock.wav` | 鍵を開ける1（生活） | |
| `se_fusuma.wav` | ふすまを開ける1＋ふすまを閉める（生活） | 開ける→閉めるをつなぐ |
| `se_futon.wav` | 布団の中でもぞもぞ（生活3） | |
| `se_lock_rattle.wav` | 開かないドア1（生活） | |
| `se_door_slow.wav` | 古びたドアを開ける（生活） | ゆっくりに |
| `se_step_heavy.wav` | 家の階段を下りる＋古びたドアを開ける（生活） | 1 歩に低い軋みを重ねる |
| `se_door_close.wav` | ドアを閉める2（生活） | |
| `se_heartbeat.wav` | 心臓の鼓動1（演出・アニメ） | 2 拍をループ |
| `se_breath.wav` | ゾンビの息遣い（戦闘2） | 息の切れ目で 6.5 秒を切り出してループ |
| `se_vibrate.wav` | 携帯電話のバイブレーション1（機械） | 1 回目の振動だけ |
| `se_noise.wav` | スマートフォンを落とす（生活3）＋トランシーバーのノイズ（機械） | 2 つを重ねる |
| `se_scream.wav` | 男性の悲鳴（演出・アニメ）＋倒れる（戦闘） | 2 つを重ねる |
| `se_comment.wav` | 決定ボタンを押す34（ボタン・システム音） | 小さめに |

### BGM — DOVA-SYNDROME（https://dova-s.jp/ ・2026 年 9 月に OpenTracks https://opentracks.com/ へ改名）

| ファイル | 曲名 | 作曲 | 元のページ |
|---|---|---|---|
| `bgm_suspense.wav` | Where the Light Never Speaks（トラック1・ループ版） | 松浦洋介 | https://dova-s.jp/bgm/detail/22730 |

作曲者の利用条件は「サイト準拠」（DOVA-SYNDROME / OpenTracks の音源利用ライセンス https://dova-s.jp/help/articles/license/ に従う）。要点:
有償・無償のゲームでの利用は可。著作権表示・クレジットは不要（任意）。
イントロを切る・ループに加工するなどの編集は可。**音源そのものの配布・販売は禁止**、AI のトレーニングに使うのは禁止。
ライセンスの禁止事項 8 は「コンバート等を行わず、エンドユーザーが音源ファイルに容易にアクセス・複製できる状態での利用」を禁じています。
この wav はモノラル化・音量変更をした物で、ブラウザ版の書き出しでは Opus（WebM）に変換されますが、元の wav も古い Safari 向けに書き出し先へ残ります。

### 合成した音

`ui_*`（カーソル・窓を開く・セーブ・戻る）は、`art/sfx.snd.star` から `bin/fge snd build` で合成した物です。
