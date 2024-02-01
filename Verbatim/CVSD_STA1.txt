Timing Analysis 或者是簡稱 STA
那這邊就是今天的課程內容
然後我們首先會介紹一下
Timing Analysis 的一些基本概念
然後還有它在數位電路裡面的一些重要性
那再來會詳細的告訴大家說
Steady Timing Analysis 它具體來說要怎麼做
然後以及要做 STA 的話需要怎麼樣的環境設定
那最後則是會再介紹一些比較特別的 Timing Paths
那這些 Paths 主要可以讓我們在做 Design 的時候有更大的彈性
那我們就先來看一下為什麼要進行 Timing Analysis
那 Timing Analysis 它是 ASIC 或者是在 VLSI Design Flow 裡面
非常重要的一個步驟
那尤其是現在的數位電路大部分都是 Synchronous Design
那就必須要在符合 Timing 的情況下才能正常運作
那所以我們就會需要一套系統來幫我們判斷說
我們的電路能不能夠符合預期的 Timing Constraints
那大家可以看到下面這一張圖
就是假設我們今天很辛苦的設計了一個晶片
那如果這個晶片它的 Timing 是正確的話
就可能可以拿去把它賣錢
那就可以獲利嘛
那當然如果今天這個晶片裡面它有 Timing Violation 的話
那因為我們不確定它什麼時候它的 Function 會壞掉
那所以這個時候這個晶片可能就會變得沒有什麼價值
就會變成一顆石頭
那接下來我們來看一下 Timing Analysis 到底是
希望能夠達到什麼樣的目標
那 Timing Analysis 的話它會幫我們確保說
我們電路裡面的每一筆訊號
它必須要在固定的時間內到達它的終點
那太早到或者是太晚到都不行
那如果這個訊號太早到的話
它就會我們會把它叫做 Hold Violation
那如果太晚到的就會把它叫做 Setup Violation
那這兩個名詞後面都會有在做更進一步的解釋
那如果今天我們發現電路裡面有 Timing Violation 的話
我們可以第一個先檢查一下
Simulation 的環境還有一些設定是不是正確的
然後再來則是可以去調整一下我們給的
我們給 Synthesis Tool 裡面的一些設定
例如說我們可能把 Timing Consent 設得太嚴格了
那如果前面兩個檢查結果都是正確的話
那到最後一步我們可能就是要再重新對電路做一次設計
那接下來我們會來讓大家了解一下
Timing Analysis 的兩種不同做法
那第一種叫做 Dynamic Timing Analysis
或者是簡稱叫 DTA
那 DTA 的話它又可以被叫做 Test Bench Simulation
那它的意思就是說呢
它會需要先 input test vector 也就是 input pattern
把它 input 進電路裡面去做模擬
然後再讓 Simulator 針對電路的模擬
去同時去計算我每一個訊號的 value
以及它對應到的 delay
那但是這樣子做的
這樣子的做法它會有三個比較主要的缺點
第一個是它沒有辦法針對所有情況進行檢查
那主要原因就是在於因為 input vector
它的 space 可能非常的大
那要產生這些非常多的 input vector 除了很耗時間以外
我們也要用這個 input vector 進行檢查
我們也不容易去考慮到所有可能的情況
也就是這邊的 incomplete timing coverage
那第二個原因是
因為我們是同時去模擬電路的 function
以及它的 timing
那所以如果今天我們發現電路裡面有 bug 的話
我們其實很難去找到說這個 bug 到底是來自於
我們 code 沒有寫好
還是因為中間有 timing 的 failure
所以造成的一些訊號沒有被存取到
那第三個缺點就是在於說
因為它要對所有的 input vector 做模擬
那如果我們今天的 vector 可能有幾百萬種幾千萬種
那這個時候我們要全部跑完模擬的話
可能就會需要非常大量的記憶體以及 CPU 的資源
那另外一種 timing analysis 的做法就是今天的主題
也就是 static timing analysis
那相較於前面介紹過的 DTA 的話
STA 它最主要的優勢在於說
它是一個 exhaustive verification
那它的意思就是說它可以針對
我們電路裡面的每一條 timing pass
都去做檢查
然後檢查它們有沒有符合我們預期的 timing constraint
那它相較於 DTA 的話
它是不需要對電路做模擬的
那所以它也可以使用比較少的 CPU 以及記憶體的資源
那當然 STA 還是有它自己的缺點在
那這邊是列出了兩個
第一個是 STA 它只能用在 synchronous design
那第二個是
今天如果我們的電路稍微複雜一點
例如說它裡面的 timing pass 包括了
有 false pass 或是 multi-cycle pass
或甚至是我們電路裡面有不同的 clock 訊號
那這個時候我們就需要一一針對
這幾種不同的 pass 去做它的 constraint 上的設定
那這兩種 pass 後面也會
就是今天課程裡面也會再介紹給大家
好那再來我們就來看一下說什麼
在我們
那個電路的 design flow 裡面什麼時候會需要做 STA
那最主要的話就是在中間這三個部分
也就是在做完 synthesis
做完 DFT insertion
還有做完 place and route 之後
一般而言我們都會做一次 STA
然後檢查一下
到目前為止我們的電路有沒有符合我們預期的樣子
也就是它有沒有 timing violation
好那接下來的話我們
會介紹一下 STA 它具體的運作方式
那首先
STA 它大概可以被分成三個不同的步驟
那第一個是要先找到
design 裡面所有的 timing pass
然後第二個是根據這些 timing pass
我們要去計算每一條 pass 它的
它上面訊號的 arrival time
以及 require time
那有了這兩個不同的資訊之後呢
我們接下來就可以去計算每一條 pass 它的 slack
然後再根據這個算出來的 slack
來去判斷說我們的 timing pass 有沒有符合
我們給定的 timing constraint
那接下來就會實際來帶大家看一下
這三個不同的步驟它的內容是什麼
那首先是 timing pass 的部分
好那在電路裡面的話
總共我們可能會遇到四種不同的 timing pass
那第一種是 register to register 的 pass
那它的起點跟終點
就是顧名思義就是 register
那起點的話
我們會把它設定成是 register 的 clock pin
那終點的話則是在 register 的 input pin
就是 data pin 這邊
也就是第一的這個 pin
那第二種 timing pass 是 input to register
那它的起點就是在 input port
然後終點的話則是在 register 的 data pin
第三種的話是 register to output
那它的起點是 register 的 clock pin
然後終點則是 output port
那再來最後一種的話是 input to output
那這邊可以看到說它的起點就是 input port
然後 output 則是
然後終點則是 output port
那接下來我們就用一個簡單的例子
來讓大家就是找找看說
在電路裡面的四種不同的 pass
那首先是 register to register pass
那我們以下面這個電路來說的話
我們如果想要找到 register 到 register 的路徑的話
就是可能先找到起點跟終點都是 register
那以這個例子來說的話
就是先找到裡面 register 在哪裡
那就是 u0 u1 u2 還有 u3
那接下來我們就把這幾個 register
看它們能不能連在一起
那以這個例子來說的話
u0 跟 u1 中間就可以發現
它連出了一條 pass
所以這邊就有一條
那 u1 到 u2 中間也是一樣
可以連出一條 pass
所以這裡也是一條
那這個 u3 的話
因為沒有其他 register 有跟它做相連
那所以說
在這個電路裡面
它總共 register to register pass 就是這邊的兩條
那再來的話是 input to register pass
那我們可以看到說
那要找到這樣子的 pass 的話
我們可以先找到左邊的 input port
那這裡的話就是包刮了 a b c
三個不同的 port
然後再來我們就是看說
這三個 port 它連接到
它的終點是到哪個 register
那以 a 來說的話
就是它會連接到 u0
所以這邊就是有一條
那 b 的話
這邊可以看到說
它可以連接到 u2
那也可以連接到 u3
所以這邊在 b 這個位置的
input to register pass 就是兩條
那再來對 c 而言
它一樣可以
透過這些中間的路徑
去連接到 u2 以及 u3
那所以說
c 這邊的 input to register pass
也是一樣是兩條
那總共的話這個電路裡面
它就有五條 input to register pass
好
那再來是 register to output pass 的部分
那我們一樣可以用前面的概念
也就是先找到右邊的 output port
也就是 opq 這三個點
然後再來我們就可以把它往回推說
看它的路徑有沒有連接到
電路裡面的 register
那以 o 這個點來說的話
它往回推的話
我們會發現它連接到 u2 這個 register
那所以在 o 這個點
它就是有一條 pass
那再來 p 跟 q 的話
這兩個我們可以發現說
它們透過中間的一些路徑的話
它們會連接到 u1 這個 register
以及 u3 這個 register
那所以說
在 p 跟 q 這邊就是
它們各自有兩條 timing pass
那這裡加起來的話
就是這個電路裡面總共有五條
register to output pass
那最後是 input to output pass
這邊的話我們就是要找到
先看最左邊的 input port
以及最右邊的 output port
然後看說
在這個電路裡面
它們有沒有辦法直接做相連
然後不經過任何的 register
那以這個例子來說的話
我們就會發現到
b 跟 c 這兩個 input port
可以透過中間的這一條
這條路徑
直接連接到 p 跟 q
然後中間也沒有被 register 擋住
那所以說
我們就可以發現
b 到 p
b 到 q
然後 c 到 p 跟 c 到 q
這樣總共有四條 input to output pass
那再來就是
STA 的第二個步驟
也就是要去計算每一條 pass
它們對應的 arrival time 以及 require time
那在介紹 arrival time 以及 require time 之前
我們要先來
就是介紹一下
或是幫大家複習一下
set up time 以及 hold time 的概念
那首先是 set up time 的部分
那它指的就是
在 clock edge 拉起來之前
的某一段時間
也就是這個 TSU
我的資料要在這一段時間以前
抵達這個 register
那如果
我的資料在 TSU 之後
才抵達 register 的話
它可能就會發生 set up violation
那時間如果漸入發生 set up violation 的話
它就代表說我的 register
它可能會捕捉到錯誤的資料
那再來第二個是 hold time
那 hold time 它指的就是
在 clock edge 拉起來之後
我的資料應該要維持
一小段時間不能做變動
那這段時間就會被稱作 hold time
也就是這邊的 TH
那如果今天我的資料
太快發生改變
也就是在這個 TH 的時間內發生改變的話
我的電路就會發生 hold violation
那 hold violation 的話
它就代表我們的 register
它會列取出錯誤的資料
那接下來我們就來看一下
要怎麼去計算
就是 set up check 的時候
所需要的 arrival time 和
require time
那這裡我們先考慮
ideal clock 的情況
那假設我們今天的電路是
像最上面這一張圖
然後它對應到的 timing diagram
是中間的這一張圖片
那大家可以看到說
從 clock edge 拉起來
也就是這邊的 clock edge
拉起來開始
那我們的訊號如果要從
register 1 傳到 register 2 的話
它中間會需要先經過
register 1 的 clock to queue
delay 那也就是 tcq
的一段 delay
那接下來當我的 register 1
的 queue pin
資料發生變動的時候
那後面的 combinational logic
也會隨之而發生改變
那經過了
這一段 combinational logic 它的 delay
這邊我們假設它
就是 tpd
那所以說從 register 1
的 queue pin 到 register 2 的
d pin 中間發生了這一段
時間我們就把這邊
就要多一段 delay 叫做 tpd
我們從下面這張圖片就可以明顯
看到說我們資料的
arrival time 就可以表示成
從 clock edge 拉起來
的這個時間點也就是 t0
然後再加上
我們 register 1 的
clock to queue delay 也就是
tcq 再加上
combination logic 的 delay 也就是
tpd
然後最後這個我們的
資料就會在這一段時間
抵達 register 2 的
tpd
那再來是 require time 的部分
那
在這個例子裡面的話
我們可以看到說
因為我們前面有說過以
set time 來說它是要在
tsu 以前 data 就應該要
送到
那所以說在這個例子裡面我們就可以
把 require time 計算成是
從 t0 的這個時間點
開始
我們加了一個 clock
cycle 的時間之後也就是這邊的
tcycle 然後再來還要
減掉這個 tsu 也就是
set up time
那所以就代表說我們的資料
應該要在至少這個時間點
最晚最晚就要在這個時間點抵達
那接下來是 hold check 的部分
那一樣我們也是先考慮
ideal clock 的情況
那我們的電路
也是像剛剛的 setup track
所以一樣是長這個樣子
然後中間這邊也是它對應的 timing
diagram
那我們可以先來看一下 arrival
time 的計算方式
基本上 arrival time 的計算方式跟前面
set up time 是一樣的也就是當
我的 clock edge 在這邊拉起來之後
它要先經過
一段 register 1 的
clock to queue delay 也就是 tcq
然後以及中間的這個
combination logic 的 delay
也就是 tpd
那兩段 delay 之後我的資料才會
從 register 1 送到 register 2
的 dpng
那所以資料的 arrival time 就可以寫成是
t0
加上 tcq
加上 tpd
那再來是
require time 的部分
那 require time 的話我們前面
有講過說 hold check
它主要是要檢查說
我的資料有沒有在
clock edge 拉起來之後
經過了 hold time 這個時間之後
資料才發生改變嘛
那所以在這邊 hold check 它的 require time
就可以寫成是
t0 也就是這個 clock edge 拉起來的時間點
然後再加上 th
也就是 hold time 的數值
好 那但是剛剛
我們前面舉的兩個例子
它都是在 ideal clock 的情況
那但是在真實世界當中
我們的 clock 訊號其實是很容易
受到干擾的
那這邊就舉幾個例子
就是有哪幾種干擾
那第一種叫做 clock latency
那它包括了 source latency
以及 network latency
那大家可以看到下面這一張圖
就是 source latency 的話它指的就是
從我們 clock
的 source 到 clock definition point
也就是可能是
我們晶片的 clock
的那個角位
那這兩者之間的這個 latency
我們就會把它叫做 source latency
那再來是
network latency 的部分
那它指的就是從我們晶片的
clock 的這個角位
也就是 clock definition point
到我們實際上 sequential cell
例如說我們的 register
它的 clock pin
中間所發生的 latency
我們就會把它叫做 network latency
那再來是 clock uncertainty
那這邊我們是
這邊我們是用 clock skew
來當作一個例子
那在電路裡面
clock 的訊號它可能會根據
register 擺放的位置不一樣
然後發生有人的 clock
可能會先到
然後有人的 clock 可能後到
這樣子的不確定性
那 clock skew 的話它就是
要去表示說
這兩個先到跟後到
他們之間的差距是多少
那因為一般我們
在做合成的時候
其實我們很難去限制它說
我們的 register 到底放在哪裡
那所以
這就會產生一種
就是我們不知道
clock 它
先到後到的時間到底是多少
那就是一個不確定性
那所以我們這邊就把它叫做 clock uncertainty
也就是它希望能夠去 model
這樣子的不確定性
讓它在做 STA 的時候能夠
把這些情況統統考慮進來
那接下來我們就來看一下說
考慮了前面的 clock latency
以及 clock uncertainty 之後
arrival time 和
require time 在計算上面會有什麼樣的變化
那首先一樣是 setup check
的部分
那這裡我們是
一樣考慮跟前面一樣的電路
然後我們先看
arrival time 的部分
那在 arrival time 來說的話
大家可以看到說
原先我的 clock source
在這個 t0 的地方
clock edge 拉起來
那本來我們是
直接算到 tcq
跟 tpd 嘛
但是因為今天我們多了 clock latency
所以中間我們要再多
一段 delay 也就是這個
tclk1
那所以我的 arrival time 就會變成是
原本的 t0 加 tcq 加 tpd
然後再加一段 delay
也就是這個 tclk1
那接下來是
require time 的部分
那這邊的話我們可以看到
中間的 timing diagram
也就是
原本
如果我們現在考慮了 register2
的 clock latency 的話
那它從 clock source 這個時間點
也就是 clock edge 拉起來的時候開始
它會多了一段 tclk2
的 delay
那另外如果我們
再考慮 clock uncertainty 的話
因為我們要考慮到說
就是 clock edge 它可能會
提前拉起來的情況
也就是這邊的 tu
那所以整體來看的話
我們的 require time 就會變成是 t0
然後再加上 tclk
這段 delay
那再加上 tcycle 也就是往後延的
clock cycle
那再來就是考慮這兩種
這兩個 delay 的話就變成是要
減 tu 然後再減 tsu
那再來是
hold check 的部分
那我們一樣先討論
arrival time
那 arrival time 的話
其實也就跟 setup time 是一樣的
那它就是
在計算的時候
原本我們是從
clock source 這邊
edge 拉起來的時候
也就是這個 t0 開始計算
那它會經過
register1 的 clock to q delay
然後以及中間 combination
logic 的 delay
也就是 tpd
那接下來
在這裡我們考慮clock latency 之後
我們就要再多增加
這段 tclk1 的 delay
那所以整體而言就可以寫成
下面這樣子的式子
也就是在 hold check這邊
arrival time 等於 t0
加 tclk1 加 tcq
加 tpd
那接下來是
require time 的部分
那在這裡的話
我們可以看到中間的這個 timing diagram
那本來我們在計算
就是在 ideal clock 的時候
我們是直接算
t0 然後加上
th 吧
但是現在我們多了兩個東西要考慮
就是clock latency 和 clock uncertainty
那所以說
我們這邊就要再加上 tclk2
這一段 delay
以及在 uncertainty 這邊
它可能會把我們的 clock age
延後
才會拉起來
那所以這邊又要再加上一段 tu
那所以整體來看的話
我們 require time 的計算方式
就會變成是
t0 加 tclk2
然後加 tu 加 th
那接下來
我們前面都是假設說
電路裡面的 combinational logic
它的 delay 統一都是 tpd
那但是
因為其實我們實際在計算的時候
它中間的 combinational logic
可能會很複雜
那所以接下來我們就會來告訴大家
這個 tpd 到底要怎麼得到
那我們會用一個叫做
timing graph 的表示方式
也就是我們會把 netlist 表示成
一個 directed acyclic graph
或是簡稱到 dag
那
在這張 graph 裡面
每一個 node 它就是不同的 logic gate
像下面這張圖一樣
黃色的就代表是每一個 node
就是每一個不同的 logic gate
那
在 graph 的 age 的話呢
我們則是會把
就是拿來表示
logic gate 到 logic gate 之間的
delay
那也就是在這張圖裡面
藍色的這個箭頭
那每個藍色箭頭就代表是一個 delay
我們看最上面的 pass 的話
就可以看到說例如說
我從最開始 input
進來會先經過一個 wire
的 delay 也就是中間這一段
然後再來到了 logic gate 之後
可能又會經過一個 logic gate 的
delay 那接下來
又會經過一條 wire 的 delay
然後再來一樣 logic gate 的 delay
然後最後到 output 前
又有一段 wire 的
delay
那如果我們想要計算
arrival time 跟 require time 的話
我們就可以透過這個 timing graph
然後像我剛剛的做法一樣
從最左邊的 input 開始
然後一步一步的往右邊去
推算
然後最後算到最右邊的 output
我就可以知道
從我 input 的
時間點然後推算到 output
它的 arrival time
那這邊的話我們就實際該大家
去計算一次
那大家可以看到說在這一張 timing graph
裡面
我最左邊的
訊號
抵達的時間都是 0.1
那如果我們想要計算
那最右邊的訊號它的
arrival time 多少的話
我們就可以從最左邊這邊
開始算那我們先看
上面這條 path
以上面這條 path 而言的話
這邊 0.1
它會先加上這個
這邊也就是用來表示
clock to queue 的 delay 是 0.2
那所以就會變 0.3
那再來經過了這個 wire 的
delay 是 0.1 所以就變 0.4
然後再來我們就會發現
這邊又有一段 logic gate 的
delay 是 0.1
加上這一段之後就到了
這個 node 它就會變 0.5
那這樣子一步一步
推算下去的話
我們就可以得到說到了最後的
這個這條 timing path
的終點 比如說這個 register 的
deepin 它的 arrival time 會是
1.5
那再來我們來算一下下面的
這條 path 那一樣可以看到
說它的 arrival time 是 0.1
那我們就隨著它的
age 上面的 delay 不斷的
去累加它的 arrival time
然後最後就可以算出來
在這條 path 的
終點的這個 node 它的
訊號的 arrival time 會是 1.3
那大家可以看到說
中間的這個部分
這兩條 path 其實是有交會的
那我們原本
算出來的 delay
可能上面的 arrival time 是 0.85
然後下面是 0.9
那我們到底應該用哪一個
delay 當作是這個 node
的 arrival time
那這個時候就是我們要
因為假設我們現在是 set up time 來看的話
那我們是要找到 worst case
所以就算這個 0.85
這個訊號先到了
那它還是要等到 0.9 的這個訊號到了
它才能夠再往下一步
那所以在這邊的話
我們就要用 worst case
也就是 0.9 的這個 delay
當作這個 node 的 arrival time
然後才能繼續往下算
好 那再來是
require time 的部分
那 require time 它就會剛好跟
arrival time 反過來
也就是 require time 它是從右邊的
項目開始做計算
那這邊一樣我們來
帶大家算一次這兩條不同的
pass 它們的 require time
那首先是先看到上面這一條
那假設我們
這邊這一條 pass 它的 require time
是 1.5
那所以我們往回推
算這個 delay 是 0.1 我們
減掉這個 0.1 之後就可以知道
那它前一個 node
它的 require time 應該要是 1.4
那再來一樣減掉了
中間的這個 command
中間這個 logic gate 的
delay 是 0.15 之後
我們就可以知道這個 gate
它在 input 的這個點
它的 delay 應該要是
1.25
不好意思 require time 應該要是 1.25
那
再來的話
我們就可以一步一步的往前推算
然後最後就可以發現
這一條 pass 的起點的這個位置
它的 require time 是 0.1
那再來一樣也是下面這一條 pass
那我們可以發現說
它在這邊
終點的 require time 是 1.5
那所以我們往前推算的話
就是減掉
這個 wire 的 delay 也就是 0.1
那減掉之後
到了這個點
大家可以發現說
這兩個 pass 也交會了
那這個時候我們應該要用
1.4 當作它的 require time
還是 1.15 用它的 require time
那
一樣我們以 set up time 的意思來說
因為 set up time 它要
考慮 worst case 嘛
那所以在這邊的話
我們希望 require time
我們希望考慮最嚴格的 require time
所以這邊就要取比較小的
這個
比較小的這個當作是
這個 node 的 require time 也就是
1.15
那所以接下來再繼續往回
推算的話就可以得到說
下面這一條 pass 它在
起點的位置
它的 require time 是 0.1
那再來如果大家有辦法
計算 arrival time 和 require time 之後
再來就可以拿這兩個
資訊然後去計算
每一條 pass 它們對應的
slack
那這邊是
set up
set up 的 slack 跟 hold slack
的計算方式
那首先是 set up time 的部分
那因為我們前面有講過說
它是想要檢查
data 應該要在
require time 之前抵達
那所以這邊 set up slack 的計算方式就是
用 require time 去減掉 arrival time
那 hold check 的
部分的話
因為它是在檢查說
我們資料到達的時間
應該要比 hold time
還要晚嗎
那所以 hold slack 的計算方式就是
跟 set up slack 相反
是用 arrival time 減掉 require time
那算出來
這個 slack 之後呢
我們就可以用 slack 來判斷
我們的 timing pass 有沒有符合
我們給定的 timing constraint
那如果 slack 它是
大於等於零的話
那就代表我們的 pass
是符合 timing constraint
也就是你可能會在 report 上看到
mat 這個字
那如果算出來的 slack 是小於零的話
那這個時候就代表說
這條 pass 它是
它是違背
我們的 timing constraint 的
那你可能會在 report 上看到 violated
這個字
好
那接下來是 critical pass 的部分
那我們電路裡面
它可能同時會有很多條
pass 都違反了
我們給定的 timing constraint
那但是
我們會希望是找到說
就是違反最多的
那條 pass 也就是它有
worst negative slack
或是簡稱叫 WNS
那有 WNS 的這一條 pass 就是
所謂的 critical pass
那下面是一個 critical pass 的範例
就是這邊我們是用
合成的 tool
然後請它 report
這邊 max pass 1
也就是最差的那條 pass
那我們就可以發現說
它就會幫我們 report
這一條 timing 最差的
這一條 pass
然後這邊就是它的 slack
那再來是
要計算 slack 的話這邊
也分成兩種不同的方式
首先是
那它就是會先
計算出
就是把所有 pass 列出來
然後再一一去做計算
分別去計算它們的
arrival time 和 required time
然後最後再一條一條去檢查說
它們的 timing
有沒有
met
那以這個例子來說的話
因為這邊倒數第二條 pass
它的 arrival time 是 11
但是在這個終點我們可以看到
required time 是 10
那所以
10-11 就會變-1
所以這一條 pass 就會 fail
好那
第二種方式是 block-based
那這邊的話
它不是把一條一條 pass 列出來
而是它是在
它是在 timing pass 中的每一個 logic gate
或是每一個 node 上面
去算它對應的
arrival time 以及 required time
那大家可以看到
這張圖片就是一個例子
就是說它會去
對於每一個 logic gate
去計算說
在到了這個 gate 的時候
我只要的 arrival time 以及 required time
應該是怎麼樣
那基本上這兩種算法會得到相同的結果
也就是大家可以看到
在下面的這一條 pass
我的 arrival time
都比 required time 還要多
多 1
那我這邊算出來這整條 pass
它的 slack 都會是-1
也就代表說這整條 pass
都是 timing violation
那再來我們就用
前面得到的 timing graph
然後來算一下
它對應的 setup slack
那我們把
前面得到的 arrival time 的 graph
跟 required time 的 graph
做相減的話
在這邊就可以得到
這個 slack graph
那可以看到說
在左上角
到右下角這條 pass
它都是 slack 大於 0
那所以就代表說
這一條 pass 它是
有符合我們 timing constraint 的
那但是
在藍色這條 pass 可以看到說
它在每一個 node 上
它的 arrival time 跟 required time
都是差的-0.05
那因為這邊它 slack
那也就是它 slack 小於 0
那所以說
這一條 pass 它就是有 timing violation
那如果我們把這兩條 pass 相比的話
因為這邊
藍色這條 pass 它是
slack 最小的
那所以它就是這邊對應到的
critical pass
好那接下來
我們就實際的用一個 example
來帶大家
來換一下電路裡面的
一些 setup check
以及 hold check
那上面這張圖
就是我們的電路
然後
下面的話則是一些
這第一個表格是
register 的一些 timing
information 那包括了這個
register 它的 clock to q 的 delay
也就是 tcq 是 3ns
以及這個 register
它的 setup time tse 又是 ens
然後 hold time
th 也是 ens
那第二張表格的話
就是在這個電路裡面的每一個
logi gate 以及 net
它們對應到的
max delay 還有 min delay
那 net 的話指的就是
這些連接 gate 跟 gate
之間的 wire
好那再來是
要算 timing
那 timing 的話我們還要給定 clock
的 timing constraint 碼
那這邊就是首先是
clock 的 definition
那這邊我們會先定義
這個 clock 它的 period 是多少
也就是前面的 tcycle 那這邊我們假設
它的週期就是 14ns
然後第二個部分是 clock latency
的部分 那 clock latency 又分成
是 source latency
也就是這邊的 tclks
以及
network latency tclkn
那這邊假設 3ns
然後最後是 clock uncertainty 的部分
也就是 tu
那這邊假設是 ens
然後第二個是
我們還需要去考慮到
說我們電路它的 io 的
concern 是什麼 那這邊的話
我們就是假設
所有的 input delay 也就是 abc
三個 port
它們的 delay 都是 ens
那 output delay 的話則是 3ns
也就是在 y 這個位置
也就是 3ns
那接下來我們就來算算看
這個電路它的 setup check
那我們這邊是
先看
就是這三條
紅色藍色綠色這三條 paths 就好了
那這邊的話我們可以先
看一下說
紅色藍色綠色這三條 paths
分別是屬於哪一種
就是 timing paths
那首先是紅色的部分
也就是第一條 那我們可以看到說
它的起點是 a 的這個 port
也就是 input 然後終點
在這個 register 的 dpn
那所以說這條 paths 它就是
屬於 input register
那再來是第二條
也就是藍色這條 paths
我們可以看到說它的起點
是左邊的這個 register
然後終點是右邊這個 register
那所以說
再來是最後一條綠色的這條 paths
那我們可以看到說它的起點是
右邊的這個 register
然後終點在 y
這個 output port
那所以說
這裡我們就可以把它
歸類在 register to output paths
那它
那因為這三種 timing paths
它們都分別對應到不同的類別
那在計算上面也會有
一點點小小的差異
好 那再來我們就來看一下
就是各個 paths
它的
setup 的 arrival time
那首先是第一條 paths
也就是紅色這一條
那我們可以
就是先把
先不考慮 input delay
我們直接看說從訊號從 a 這個點
到這個
register 這個 dpn
然後
我們可以看到
這個 register 這個 dpn
中間的 delay 是多少
那它就是按照我們
前面講過的 timing graph
的算法從這邊
這個點開始一步一步往後推
因為是 2 然後
加 3 加 2 加 3 加 2
這樣子整個加起來就可以得到
12
那另外這邊再加上
前面提過的 input delay
的話就可以知道說
那我的資料從 a
傳到 dpn
它的 arrival time 會需要
da 加 12 這麼多
那再來是藍色的這一條 paths
那我們可以看到說
這條 paths 因為它是從 register 當做起點
所以我們這邊就是直接
從 clock pin
這邊開始做計算
那從 clock pin 開始的話
我們首先會遇到的是
clock to queue 的 delay
就是前面提過的 tc queue
那這邊的話前面有定義好
它是 3 跟 s
那再來到了 queue 這邊之後
我們一樣按照 timing graph
的計算方式一步一步往後推
所以它就會這條 paths
的 delay 就變成是 3 加 2
然後加 3 加 2 加 3 加 2
那全部加起來
就會得到它是 15
那另外因為它這邊
起點是跟 clock 有關
那所以我們另外還要再加上
clock 的兩個不同的 latency
也就是 source latency 以及
network latency
那再來是
最後一條 timing paths
也就是綠色這一條
那我們可以看到說
它一樣也是從 register
當做起點
所以它一開始就會先經過
clock to queue 的 delay
這邊的 3
然後再來也是一樣按照
timing graph 的算法一步一步往後推
這四個數字加起來
就會變成是 10
那一樣因為它
是從 clock 當做
一個起點所以我們前面
也要再加上 clock 訊號的兩個不同
latency 也就是這邊的
tclks 和 tclkn
那到這邊為止我們就可以計算好
這三條 paths 的 arrival time
那接下來則是
require time 的部分
那我們以第一條 timing paths
來看的話
因為它是一條 input to register paths
那所以說我們在計算上
它的終點是 register
那計算方式就是跟前面提過的一樣
也就是
我們可以把 tcycle
然後加上
兩個 clock latency
然後再減掉 clock uncertainty
然後再減掉 setup time
那最後這邊的結果就是
17ns
那對於第二條 timing paths
而言那因為
它的終點也是在
register 所以計算方式
就跟 timing paths 1 是一樣的
也就是 tcycle
然後加上 clock latency
減掉 clock uncertainty
再減掉 setup time
那這邊算出來就是
得到一樣的結果也就是 17ns
好
那再來是第三條 timing paths
那這條 paths 它
算法會稍微有點不同
那它的原因在於說它的終點
現在是 output
那我們可以看到下面的這張圖
那 output delay
它的意思就是說
我的這個 y 這個角位
它往外接還會接到
比如說接到一個 register
那我會希望
從 y 到 d-pin
它的 delay 是 3
那所以這邊就會把它定義成 output delay 是 3
那所以說
我在算 required time
的時候就變成是
我要改成是算我的 tcycle
然後直接減掉這個
output delay 因為我希望
我在 3 的這個時間點
之前資料就要送達
那所以就是減掉
這個 dy 也就是 3
那算出來的結果就會得到說
我的 required time 是 11ns
那接下來目前為止
我們就算好了這三條 timing paths
它們各自的
required time 跟 arrival time 了吧
那接下來我們就來算一下
它們各自的 setup slack
是多少
那因為是 setup slack 那所以它的
算法就是用 require time
去減掉 arrival time
那以第一條 paths 來說的話
我們這樣子做相減的結果
會發現它的 slack 是 4ns
那它的結果
大於人靈
所以就代表它這邊的 timing 是 met 的
那再來
第二條 paths 的話
因為它是
再來第二條 paths 的話
那我們一樣把它的 require time
減掉 arrival time
那這樣子做相減就會發現
結果是-3ns
那這邊的話
它的 slack 是負的
所以就代表說這條 paths
它是 timing violated
那再來最後一條 paths
一樣我們把它的 require time
減掉它的 arrival time
那這邊就可以得到說
結果是
-4ns
那一樣 slack 小於 0
代表它是 timing violated
那接下來我們看一下這三條 paths
它們的 slack 可以發現說
第三條 paths 它的 slack 最小
那所以說
對於這三條 paths 而言
我的 timing paths 3 就是我的 critical paths
好
那接下來我們來看一下 hold check 的部分
那我們一樣是考慮
紅色藍色跟綠色這三條不同的 timing paths
那首先是
arrival time 的部分
那在這裡的話
我們就可以計算出
這條紅色的
它的 arrival time 就是從
就是在這個 cycle 以前
抵達
那就會變成是
就會變成是
bb 然後加1
那再來是
timing paths 2
那這邊的話
它的算法就是像前面提過的
就是跟 setup check 那邊一樣
也就是它會變成是
這裡的 tclks 加 tclkn
然後加 8
那就是這整條 paths 上面的 delay
那再來是
timing paths 3 的部分
那它的 arrival time 一樣
就是計算方式跟前面一樣
也是加上了這兩個
clock latency 之後
然後再加上這個路徑上面的 delay
就會變成是
這邊這樣子的式子
那比較注意的是
我們這邊路徑上的 delay 用的是
min delay 而不是 max delay
那是不是因為就是對於
hold check 來說的話
我們是希望能夠檢查
資料最快什麼時候送到
所以我們要用 minimum delay
好 那接下來是
require time 的部分
那首先
對於第一條 paths 而言
我們要算 hold time 的
require time 的話
因為它終點是 register
所以就是用前面的方法
就是把兩個
clock latency 加起來
然後再加上 clock uncertainty
再加上 hold time
然後就會變成是
CNS
那再來是第二條 paths
那因為它的終點一樣是 register
所以計算方式就會跟
前面的一樣
是把兩個 clock latency
做相加
然後再加上 clock uncertainty
然後再加上 hold time
那這邊就會變成是
CNS
那第三條 paths 因為它的終點
是 output
那所以這邊它會比較特別一點
它的 require time 的計算方式是
直接拿 output delay 然後加一個
也就是這邊是負 3Ns
那接下來的話我們就可以來
算一下說
這三條 paths 的 hold slack 是多少
那以 hold slack 來說的話
我們前面有提過它是拿
arrival time 減掉 require time
那所以說這邊
我們以第一條 paths 而言
我們算出來是 2.7 也就是負 5Ns
那代表它這邊就是有
invalidated
那再來第二條 paths 的話
一樣我們拿它的 arrival time
減掉它的 require time
然後最後結果就可以得到是
6Ns 那這邊因為它
slack 大於等於 0
所以它的 timing 是 met 的
那再來最後一條 paths 的話
我們這邊可以計算得到說
它的 arrival time 減掉 require time
結果是 14Ns
那也是一樣它的 slack 大於等於 0
那所以它這邊
timing 也是 met 的
那接下來我們一樣看一下
這三條 paths 哪一條 paths 是 critical 的
那以這三條而言的話
因為只有第一條 paths
它的 slack 是負的
那所以它就是最小的那一條 paths
那對應到它就是
這三條裡面的 critical paths
好
那以上就是我們在進行
STA 的時候所會遇到的
一些運算的結果
來 俊偉在這邊先停一下
好
前面那個提到的
這些 static timing analysis
請同學
務必要搞懂
就相關的計算
在期中考
以往都是很容易出現的題目
另外呢
在實際操作的時候
當你發現
這個 timing analysis
有一些錯誤的時候
你有辦法從它提供的
這個 report 裡面找到可能發生的原因
所以請同學注意一下
另外也提醒一下
我們下個禮拜是期中考
好 那俊偉繼續了
老師
中間要休息一下嗎
OK 好 現在十分
那我們休息到
這個是十分鐘
還是二十分鐘
應該是十分鐘
