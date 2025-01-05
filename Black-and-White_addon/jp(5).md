<div class="pagetitle">

白黒-補足

</div>

## 異なる方法

### 概論

　より独創的な白黒画像を作成するために、3つの異なる方法を加えました。それぞれ違った効果を生みます。

1.  彩度低減を使う方法
2.  輝度イコライザを使う方法
3.  チャンネルミキサーを使う方法

　もちろん、これらの方法を使わなくとも、白黒画像を作るための簡単な方法がRawTherapeeには、既に備わっていることをお忘れなく：

1.  露光補正セクションの[彩度スライダーを](Exposure/jp#彩度 "wikilink")-100にする
2.  Lab調整セクションの[色度スライダーを](Lab_Adjustments/jp#色度 "wikilink")-100にする
3.  [フィルムシミュレーションで](Film_Simulation/jp "wikilink")白黒のHald
    CLUTファイル（Ilford,Kodak、フジ。。。）を使う

　でも、別の方法も用意したことで、白黒変換の多様性が広がりました。

　完全なグレートーンに関しては、[カラートーン調整を](Color_Toning/jp "wikilink")除き、処理プロセスの最後で、[Lab調整の](Lab_Adjustments/jp "wikilink")“a\*”と“b\*”の値がゼロに設定されます。

　尚、カラートーン調整との相互作用に関しては、後述の該当セクションを参照して下さい。

### 彩度低減

　この方式は、各ピクセル（R=G=B）にL＝0.299R+0.587G+0.114Bから得られる同じ輝度値を与えることで、完全なニュートラルグレーの画像を作ります。

　前述の彩度を下げる2つの既存の方法（彩度、或いは色度のスライダーを-100にする方法）はアルゴリズムが異なるので、違った白黒効果になります。露光補正セクションの彩度低減の方法は、HSV色空間の“S”（彩度）”をゼロにします。一方、Lab調整セクションの方法は、（a\*a+b\*b）の平方根で得られる“C（色度）”をゼロにしています。

### 輝度イコライザ

　この方法は[フラットカーブを](General_Comments_About_Some_Toolbox_Widgets/jp#フラットカーブ "wikilink")使って、色相に応じた輝度を調整し、白黒画像を作ります。

　RGBをLCH（色相に応じて輝度を変える）に変換、そして色域を調節したRGBに再び変換、というアルゴリズムを使います。

　一部の市販現像ソフトでは、限られた色だけをスライダーで調整しますが、RawTherapeeは全色調範囲に作用します。

　最後に、完全なグレートーンにするため、R、G、Bの値が同水準に設定されます。

　色域を抑制していますが、カーブ調整を極端にすれば、画像に特殊な効果を加えるが出来ます。

　この方法では、ピペットの利用が非常に便利です。例えば、暗くしたい部分をピペットで選び、グラフに追加された調整点を下に動かせば、思う所のトーンが暗くなります（明るくする場合は、上に）。

### チャンネルミキサー

　一見、非常に複雑な調整機能に見えますが、到って単純です。この方式は、チャンネルミキサーで画像の異なる色のバランスを、それぞれハイライト、中間トーン、シャドウ部分で、微妙にコントロールして調和させます。各色チャンネルの割合を計算し、合算します。

　表示される数字に注意して下さい。白飛びを避けるためには、色チャンネルの合計が100％以上にならないようにします。また、マイナス値を入力しないようにします。

　但し、独創性を求めるならば、a)合計値は100％以下、b)マイナスの値を入力しない、というルールに拘る必要はありません。ルールに拘らない自由な調整が特殊な効果を生み出すからです。それは以下で説明する、どのプリセット（赤外線効果、風景画、人物画、コントラストなど）でも同じです。

#### チャンネルミキサーの構成

##### プリセット

　以下の選択肢があります:

- プリセット (通常コントラスト、ハイコントラスト、輝度、人物画、風景画、
  高感度/低感度、
  パンクロマティック、ハイパーパンクロマティック、オクトクロマティック、赤外線)を使う
- 次の4つの基準で、貴方が設定を行う：

1.  　**絶対RGB**：
    制限なしにR、G、B、各チャンネルをミックスします。プラス値であれ、マイナス値であれ、また、合計が100％以下でも以上でも構いません。
2.  　**相対RGB**：R、G、B、各チャンネルをミックスしますが、制限があります。入力値はプラス値でもマイナス値でも構いませんが、合計は常に100％になります。例えば、R＝10％、G=10%
    、B＝30％と入力しても、合計は、R=20%
    、G=20%、B=60％と変換され合計が100％になります。全てのプリセットでこれがデフォルト設定になっています。例えば、“風景画”では、マイナス値を入力しない限り、相対RGBは、直感的、且つ、単純なR＝66％、G＝24％、B=24％です。
3.  　**絶対ROYGCBPM**（ROYGCBPMはレッド、オレンジ、イエロー、グリーン、シアン、ブルー、パープル、マゼンタの頭文字）：この特殊なミキサーには2つの面白いオプションがあります：
    - 補色を調整する：このオプションの場合、OYCPMのスライダーを動かすと、自動的に基本色（R、G、B）を補正します。
    - OYCPMアルゴリズムを使う: “リニア”に設定すると,
      望む強さと2つの基本色に対し、完全に比例配分されます、例えばオレンジはレッドとグリーンに影響します。“特殊効果”を選択すると、レッドとグリーンに対するオレンジの影響が非線形的になり、スライダーの設定値次第ではブルーにも影響することがあります。


    この方式は最も調整結果の予想が付け難い設定ですが、その分独創性が増すでしょう。
4.  **相対
    ROYGCBPM**：作用は上記と同じですが、3つの基本チャンネル、R,G,Bの合計が100％になるように制限がかかります。

##### カラーフィルター

　カラーフィルターモードは、レンズにカラーフィルターを装着して撮影した状態を真似たものです。これらフィルターは特定色の透過を減らすことで、画像の輝度に影響を与えます。例えば、レッドフィルターは青空の明るさを減らし、レッドを明るくします。このフィルターは、“プリセット”の設定値に対して乗数として働きます。

##### 自動

　このボタンを押すと、画像全体を解析し、3つの基本チャンネル、R、G、Bのバランスを取り、各チャンネルに同じ加重を加えます。

#### 注意

- プリセットの画像に更にチューニングを（“補色の調整”や“OYCPMアルゴリズム”）加えると、チャンネルミキサーの調整値（％）が変わります、その際プリセット名の下に表示される数値が、例えば、R=37.2％、G=-82.3％、B=126.6%
  、合計＝155％になるようなケースがあるかもしれません。追加調整により、各ピクセルは、ミキシングされる前のR、G、B値に乗算された値を持ちますが、この場合、調整済み画像の明度が元画像のそれを55%超えているという意味になります。
- 相対的モードにおけるプラス値の入力は、その効果が予想しやすいと思います。チャンネルミキサーは、相対モードが一般的です。白黒フィルムのシミュレーション、例えばIlford
  Delta
  100のR、G、B値は、ウェブ検索すれば、21、42、37であることが分ります。
- 一方、絶対的モードでは、マイナス値の入力や、“OYCPM”スライダーの使用、”特殊効果“アルゴリズムの適用により、予期せぬ結果を生むことがあります：画像が突然黒くなったり、アーティファクトが発生したりします。

## ガンマ補正

　ガンマ補正のスライダーを使って、各色チャンネル（R、G、B）のトーンを変えることが出来ます。概ね、この機能は、引き伸ばし機で焼き付けを行う（ハード、ノーマル、ソフト）ことを真似したものです。スライダーを左に動かす（マイナス値の入力）と画像イメージを暗くし、コントラストを高めます。逆に右に動かせば、ソフトなイメージにします。

　備考：ブルーチャンネルのスライダー効果が小さいと感じるかもしれませんが、これはバグではありません。作業色空間にProPhotoを使うと、ブルーチャンネルの作用が小さくなるのです。作業色空間をsRGBにすれば、効果は変わります。

## 調整“前”のカーブと“後”のカーブ'

　これらカーブは、露光タブの露光補正セクションにあるトーンカーブと使い方は同じです。単に、白黒変換ツール専用に、独立させただけです。

　備考：“後”のカーブのモードは、画像が白黒なので一つだけです。

## カラートーン調整

- 特殊効果を出すために、白黒ツールにも[カラートーン調整が](Color_toning/jp "wikilink")使えるようにしてあります。白黒フィルムのシミュレーションにもカラートーン調整が使えます、但しその場合、白黒ツールを有効にする必要があります。
- 相乗効果を最大にするために、“カラートーン調整”や“白黒”という機能をプログラムのアーキテクチャー（処理プロセスにおける各機能の適用順序）に採用したのです。
- 画像編集の多様性を高めるべく“カラートーン調整”が採用されていますが、[“シャドウ/中間トーン/ハイライトでバランス”という](Color_toning/jp#シャドウ/中間トーン/ハイライトでバランス "wikilink")方式が、最も高い多様性を持っています。
- 方式をS/M/Hでカラーバランスから、例えば
  “L\*a\*b\*モデルでブレンド”に変えたり、“ガンマ補正スライダー”や“白黒”ツールのカーブを使ったり、試して下さい。
- 画像に特殊な効果をもたらすためには、数多くのトライ＆エラーの繰り返しが必要でしょう。