好啦,不好意思,剛剛回答了一些問題,有點期待喔
好,那我們就來上課喔
這堂課會比較無聊一點喔
這堂課我們要講APR的TOOL
這邊是整個APR TOOL的流程
就是要做這個Layout的流程
我們上一堂課已經講說我們把它合成成Gate Level
那我們就要從Gate Level的檔案再把它合成成Transition Level的Code
所以它會有一些,就是整個所有的步驟
就是你要準備一些檔案,然後把檔案import進來
做這些烏龜龜的操作
這裡面大部分的東西我都會
因為它就是一個流水帳的投影片,所以相當的無聊
大家回去就是到時候做作業的時候
就是照著順序一個一個做就好了
然後後面如果有一些東西要提醒的話,我會另外再提醒大家
那這邊可以跟大家稍微提前講一下的事情是
這個CTS,Collab Tree Synthesis跟Power Roth這兩個東西
這兩個步驟呢
我有在一些流程上看到說他們兩個會反過來做這樣子
那我們在這堂課呢,我用的流程是這樣子
那反過來做的流程好像會有一些好處
不過據我所知應該是你們用這個流程就可以了
那到時候如果說有需要的話
有問題的話可以再寄信給我
但是我覺得應該是照目前的流程就可以了
但是如果你去查到一些其他資料
或者是你原本就有學過一些Layout的東西的話
確實是有把這兩個步驟反過來做的做法這樣子
但是應該是都可以做好啦
但是因為不同的製程啊
還有不同的版本之類的
它的這個做法會不一樣
反正就是這樣
就是有一個,如果有人有一些Background的話
稍微講一下這件事情
好,也就是比較前情提要啦
那再來就是一些比較無聊的事情
首先呢,你就要把你的一些檔案整理好
這個資料夾呢,就照著這裡面這樣子擺放
會有一些什麼Synthesis的SDF檔
Synthesis的.V檔
GSMC,我們剛剛說有E3.V
有Negative.V這樣子
然後就是你的Synthesis檔案
通通放到Synthesis的資料夾裡面
到時候要讀取的時候呢
會比較方便一點
那會有另外一個SDC檔
SDC檔呢,前面就是APR.SDC
APR是Auto Place and Route的縮寫
就是自動擺放跟繞線這樣
所以呢,大家如果
大家有時候會有點好奇
就是SYN問的小寫,這個是大寫
因為這是三個英文的縮寫
所以就是Auto Place and Route
但是這個是Synthesis的縮寫
它就只有一個單字
所以它就是小寫,這是大寫
可是我們合成的時候呢
就會用SYN作為一些
就是前最後對字,這樣子
然後Layout的時候呢
就會用APR作為
你的標示,這樣子
那這個SDC檔呢
裡面呢,它也會有
這個Set Cycle這一行
那當然還有一些雜七雜八的東西
值得注意的是這個SDC啊
它的這個合成跟Layout
合成跟這個APR的時候
用的是不同的檔案
所以大家要小心不要搞混了
那當然這個Cycle呢
也是可以去調整的
那也要特別注意就是說
我們說你會模擬
就是你需要去跑這個Gate Level的
從RTL Level要模擬
然後Gate Level合成的時候
要設定一個Clock Cycle
然後Gate Level要跑模擬
然後這個Layout的時候呢
這個現在這邊呢
又要設定一個Clock Cycle
然後最後呢,Layout完之後
Layout結束了APR檔案
你還要再跑一次模擬
所以這邊有五個Clock Cycle
除了第一個RTL
我們說那個時間
它基本上隨便亂跑
所以不要理它
剩下的四個呢
你的Clock Cycle都要一致
全部都要設定一樣的
那你說
我如果前面設定5
後面要設定6的話
我後來突然發現
做不出來的話
那要怎麼辦呢
我想要把它放寬條件的話
那要怎麼辦呢
沒錯就是那個
大家心裡想的最糟的狀況
你就是要回到最前面那個步驟
然後把它全部都設成6
然後重頭再做一次
所以呢
這就是一個
有點繁瑣的過程
所以大家到時候在做Project
或者是在做下一個作業的時候
你想要把速度變快的時候
我先保險一點
我先用10ns去做合成
合成完之後呢
我跑完Layout之後呢
發現我10ns可以
我跑得過
但是這樣成績比較低呀
那我看了一下Slack
不然我調整成
6ns去合成好了
那我就要回到合成這個步驟
然後合成
跑Game Level Simulation
再Layout
然後跑Layout的API Simulation
所以
很繁瑣呀
然後因為我們又說這個
合成的時候又要花一些時間
有時候運氣好的話
可能幾十分鐘搞定
運氣不好可能要幾個小時
然後Layout也要花一些時間
也要幾個小時
反正就全部跑完一次
然後看結果
結果如果不好
你又要回到上面去重新跑這樣
反正就有點麻煩呀
就是如果Constraint
這個Cycle Time Constraint
如果要改的話呢
就會遇到一些麻煩
不過
就通常你合成的階段
把它壓到5
如果你把它壓到5
然後它就已經壓不下去了的話
那通常後面就不會
後面就不會再變快
後面只會變慢而已
這樣
對
好
那
這是什麼東西
就是你要跑Layout的時候
要Source嘛
Source我們要用的軟體呢
叫做Innovus
Innovus
它的前身是Encounter啦
不過現在改名了
改名叫Innovus
把它Source這些東西
然後呢
你就可以開這個Innovus
這個軟體這樣子
那
到Layout這個資料夾
因為我們要執行
執行這些東西呀
它有一些東西
有些時候會有一些相對路徑
除非你非常搞得清楚
自己在幹嘛
不然的話
相對路徑都把它
就是照著這樣子去擺放
然後
在這個資料夾裡面開Innovus
這樣子
才不會說
影片跟我說
什麼檔案找不到啊之類的
會寄信跟我說這個問題啦
通常就是
這個資料沒有照這樣擺放
這樣
好
那就是進到
Layout這個資料夾之後
再打開Innovus
那
值得注意的是
Innovus在打開的時候呢
它會有圖形化介面
然後它也會有Terminal的介面
就是可以Device
那個打指令的那個地方
所以我們後面就不加一個end
這樣子的話
你兩邊的這個介面都可以使用
這樣
好
那就是前置準備
那把Innovus打開之後呢
就可以開始
照著步驟按
照著步驟按
這就開始有點無聊了
反正
這個
聽了也是有點沒意思
好
反正就是把Design Info進來吧
File Info Design Load
然後把你的檔案選擇了之後呢
欸不是
這邊要選擇這個
某一個什麼
點Global的檔案
這個也是助教有提供
反正就把它
Load把它選擇了之後呢
然後Open
OK
整個都照著按
就好了
那這邊呢
特別跟大家講一件事情
就是說
你隨時啊
都可以在某一個步驟
進行到任何步驟的時候
可以儲存
到目前的狀態
那你可以幫它取一個名字
這樣子
那
像這邊呢
就是File Save Design
然後勾選Innovus
記得要勾這個喔
那個OA那個檔案
我其實不會用
我沒用過
勾選Innovus之後呢
檔案名稱看你要設定什麼
然後按OK
然後呢
你如果說
檔案那個程式關掉了
還是什麼後面的步驟
執行的不順利啊
你要回到中間的步驟
去重新調整的話呢
你可以把它
就是Restore Design
File Restore Design
然後也是要勾選Innovus
然後去Browse
這個資料夾
然後去找到這個
右邊這個東西
就是
CTS就是我們剛剛講的
Cloud Tree Synthesis
就是Post CTS
不知道這個字
會不會太小
反正就是
你在各個Stage
存檔的時候呢
會有你存的檔名嘛
那它是沒有副檔名的
對
就是這個檔案
然後你去選它
然後按Open
這樣子
然後再按OK
那它就會讀取
你目前
就是當時儲存的這個狀態
這樣子
好
那再來就是
有一大堆步驟啊
就是你到時候
打開這個Innovus的介面
然後把它照著按
這個
Global Net Connect
就是要把所有Standard Cell的
Power跟Ground的Pin
通通連接到他們的
VDD VSS上面
對
連接到Global的VDD VSS上面
這樣子
那要操作就是
Power Connect Global Net
去點
點這個東西
然後裡面就會有選項
就會出現一個視窗
然後你就要Connect
選Pin
然後Pin Name
填入VDD
Scope也要選
然後To Global Net這邊
要用手打VDD
然後按Add List
然後你就要按很多次Add List
下面這個也是一樣
這是VDD
這是VSS
然後呢
也是一樣
手打VSS
然後也是Add List
然後呢
再來呢
要把這個
有夠無聊
我覺得有人已經快睡著了
1B0 1B1
把它接到VDD VSS
Connect這次呢
剛剛是選Pin
這次要選Tie High
反正這個
我們也沒有實際操作
所以大家看起來
一定超無聊的
然後Tie High
然後呢
Scope也是一樣
然後To Global Net填VDD
按下Add List
另外一個也是
VSS也是一樣
Add List
它是Tie Low
好
四個
因為這個
實在是太多次充了
所以我也沒有
給大家看
反正大家
就是照著這步驟
按而已
其實還蠻
單純的
下一個步驟
就是Floor Plan
Floor Plan呢
至少我可以
稍微講一點點
有技術性一點的東西
就是
這邊呢
你就可以
填入這個
填入你的數值
就是你這邊
可以設計
你的這個
面積
你想要
你的這個
這個晶片
想要
它的長寬比
想要怎麼樣
你如果想要正方形
它的長寬比
這邊又有一個Ratio
你就可以設1
那Core Utilization呢
比較有趣一點
就是說
因為你把一些
Sensor Cell
放進去之後
它要用一些電線
把它接起來
你的一些Function
要用電線
把它接起來
它才會Work
對不對
所以呢
這個
我看一下
我看一下時間
好
這個
這邊呢
就會有一個
就是
這些電線呢
它也需要一些面積
所以你要留一些面積
給它去把這些線
繞線繞出來
這樣子
所以呢
Core Utilization
就是
你留
留的一些空白的部分
留給它
留給它這個
繞線的面積
這樣
那當然你
Core Utilization
把它設的越低
這是
0到1的數值
就你使用的
使用的面積
如果越低
通常
它留下
留下這個
給它繞線的空間
就越多嘛
那它就會
越容易
做的
做到一些
好的結果
這樣子
但是你的面積
當然就會相對比較大
就你的Standard Cell
如果面積就是100
那你Core Utilization
用0.5
那你整個的
Chip面積
可能就會
它就會預設
可能大概200給你
這樣
然後
讓它剩下100
去繞線這樣
那一般呢
一個比較經驗上的
數值是這樣
就是如果你是
很複雜的Design的話
我會建議設
0.4到0.6左右
算是複雜的Design
就是碩論那種等級的
那至於這種
Homework這種等級的
通常我們會設
0.7以上
就是
Homework
如果你的Code
不要寫得太亂
然後
不要太
太難
就是你寫的這個邏輯
很
很軟體
很不硬體的話
它就會不好繞線
那
那你這個可能
就要設低一點
之類的
反正就是
你作業等級的話
我的經驗上來說
設0.9
0.9
0.9
0.9
可能都還繞得出來
這樣子
對
但是一般的Design的話
普通的Design可能是0.7
然後複雜一點
Design可能是0.5左右
對
這是一個比較經驗的數值
對
然後這個什麼
這個這個
Code IO Boundary
就照著設就好了
這些東西就是
框起來的地方
就是你需要填的數值
這樣
那這個就是
你可以自己去選
好
那再來就是
中間會有一些
就是你要把
把一些元件放進去的步驟
這個Placement的部分
Placement
那Floor Plan Mode
那就是照著按
Place Standard Cell
那就會把Standard Cell
先把它放進去
這樣子
好
那執行完之後呢
你這邊呢
也可以選這個
不同的Design View
去看看說
你的Layout現在長什麼樣子
可以按按看
有點有趣這樣
然後就是
Run Placement in Floor Plan Mode
去按這個東西
那Optimize的Option
要取消勾選這個
這個
就先不要做這個東西
按OK
它就會去Place出來
那就可以去看說
它不同的View
長什麼樣子
還有不同的View
什麼Scan Maintain View
還是什麼的
就去看這三個按鈕
這樣
好
那在各個階段呢
我們會做很多次的
Timing Analysis
那
就是
其實就是大概確保一下
確保一下你現在
做出來的這個Layout
有沒有符合
你的這個時間要求
那
步驟的話
就按照這邊按
就是
Timing Report Timing之後呢
你現在是在一個
Preplace的這個階段
所以呢
這個Design State
你就選這個
按OK
Tool就會開始分析
然後做RC的這個Instruction
然後算出一些Delay之後呢
分析這個整個的
Critical Path
這樣子
然後Tool跑完之後呢
它在Terminal
Terminal
就是黑底白字那個地方
就是不是圖形化界面的地方
那就會有分析的結果
那主要就是要看
WNS這個東西
那這個值
就是跟我們前面那個
Slack一樣
它就是Worst Negative Slack
跟你在Compiler
Design Vision的時候
看到那個Slack是一樣的
就是它一定要是0
或者是大於0
正的
就不可以是負的
那就是如果是負的的話呢
會有補救的方法
就是後面
後面會講解
反正這邊呢
理論上來在這個步驟
基本上不太可能會是負的
那如果這邊是負的的話
很可能
就是越前面的步驟
越前面的步驟出錯的話
後面就會越容易
Layout失敗
所以呢
在這個步驟是負的的話
你可以不要理它
這邊是說你可以不要理它
後面會去補救
不過我會建議
你要改變
就是要去調整Coding Style
這個時候
通常這時候會出錯
就表示你Coding Style
真的很
很不適合硬體這樣
那再來呢
就是要去
就是真正的Full Placement
然後再做Power Plan
這些都是一些
各個階段的名稱
就是要把Standard Cell
再按一次
Place Standard Cell
但是這次呢
你就要選擇Run Full Placement
然後取消勾選這個東西
然後按Mode
然後加選這個東西
Cloud Gating Awareness
這樣按OK
按OK之後
它就開始跑Placement
那執行完之後呢
它這個
就要再按一次Refine
Refine Placement
它的這個
讓Cell擺放的方向
它有時候上下
很擺反了之類的
它就會用這個步驟去
Refine這樣子
然後最後呢
就還是要再執行
Timing Before Timing
各個步驟
反正你就一直Check
說你現在的Timing
到底有沒有符合要求這樣
那Design Stage呢
是Pre-CTS
就是你下一步
就要做CTS了
所以就是Pre-CTS
然後這個時候呢
如果說
Slack為負的話呢
就可以執行
Timing Optimization
那就是只要是Slack為負
通常就是要執行這個
然後呢
步驟就是按照下面這邊按
那這邊呢
這邊呢
Design Stage選Pre-CTS
那值得注意的是
Timing Optimization
如果做出來還是負的
你可以多做幾次
它會越來越好
但是
但是就是
進步的幅度會越來越小嘛
這是當然
對對對
那通常啊
我們可能會做個
三四次之類的
那如果說
真的不妙的話
可能就要重新設計
或是放寬考試這樣
好
那再來是
加上一些Power的部分
就是在周圍打一圈Power Ring
首先是要打Power Ring
一圈
一邊是VED
一邊是VSS
那把它繞一圈
然後就是Power Ring
那
那這樣子的話
就是避免IR Drop啦
就是把它繞
弄一圈這樣子
它比較不會IR Drop
然後
等一下
OK
然後再來就是按
然後Refine Placement
然後按OK
就是這個部分呢
就會把
剛剛
因為Timing Analysis
它其實會產生一些
垃圾
然後我也不知道為什麼
它不自動拿掉
反正呢
你就是要
剛剛前面我們有說
Timing Analysis
就要把這個東西
執行一次
它就會把那些垃圾拿掉
這樣子
然後呢
你可以看Physical View的話
可以看到裡面原本有一些線
它就會被移除這樣
那Power Ring打完之後呢
就是會加上外面這一圈
那再來呢
你要打Power Strike
不好意思
還沒有
我們還沒把Power Ring加完
不好意思
Power Planning
然後Add Ring
這個時候才會把Ring加上去
那這個地方呢
就是按照步驟按
Net要選VED跟VSS
然後Ring Configuration
裡面呢
你就要選這些東西
把這個Top Button
也改成Metal 7
然後Horizontal
然後
左右呢
改成Metal 6
是這個Vertical
Width
就是照著設
這些都是一些
比較適合大家
目前Design的經驗數值
填完之後呢
按一下Spacing
下面有一個Update的按鈕
然後勾選這個Offset這個東西
然後切換到Advanced的這個
上面有一個那個分頁
Advanced的分頁
然後勾選這個東西
勾選這個東西
Number of Bits填入2
然後做完之後呢
你會看到剛剛那個一圈的東西
就會跑出來
然後一圈的東西跑出來之後呢
接下來我們就要加Power Stripe
就是這兩根
基本上呢
就是說
也是要讓供電更均勻一點
就是如果中間離四個角都很遠
如果你晶片面積很大的話
那它就會有
比較嚴重的那種
Ion Drop之類的問題
所以呢
就要加上這種Stripe
那加上Stripe呢
它就會定一些Constraint
譬如說
從左邊到
左邊到第一根
至少要多少
它才會打第一根
然後這兩個距離多近的時候
它才會打
它就會打第二根
這樣子
然後右邊的距離是多少
這些都有設定
設定在哪裡呢
設定在這邊
你就是要按Power
然後Power Planning
這是要加Add Stripe
然後呢
設定就會在下面這邊
Net就選VDVSS
Layer選Metal Set
因為我們這個是直的Stripe
所以我們就是選Metal Set
就是我們剛剛Metal Set是Vertical
那
如果你想要打橫的
呃
因為只要打一種而已嘛
那通常我都是
通常
對
通常我都只打一種
你想要兩個都打
好像也可以
反正我們這個
這個Design很小啦
所以很可能按一按之後
甚至連Stripe都不會跑出來
也有可能
如果你面積很小的話
它可能是沒有Stripe的
對
那就是
看你下面的設定
Set to Set Distance呢
就是兩根Stripe之間的距離
然後
有First跟Last Stripe的這個
Start的Decision
那就是
跟Stop的
Stop的這個
Distance
它就是從
我們剛剛說從左邊到第一根
跟從右邊到最後一根
它的距離
那這邊都設30的話
那你就想說
如果你寬度小於60
那它就是
一根都沒有
對
對
所以打完之後
它有可能什麼都不加
也有可能
對
Elements
這邊就是Switch Layer Over Obstruction
反正就是
一些詳細的設定啦
Wide Group跟Interleaving
把它勾選起來
Number of Bits
我們這次選1就好
因為Stripe細一點就好了
如果看上頁的圖
就看到Stripe比較小
Stripe只有一根
然後Rim有兩根
那個就是Number of Bits
還蠻無聊的
大家應該
反正
大家這個隨便聽
應該是不會
覺得
就是
沒有操作應該是很沒感覺
可是因為步驟寫蠻詳細的
回去就是照著按就好
好了
那這個時候呢
按Verify Geometry
這個時候呢
就已經出現一些
可能會有DRC Violation的部分了
你說
這又不是我自己畫的
怎麼會有DRC Violation
因為這些Tool
處理的問題是那種
比較NPComplete
就是
反正就是
它
做這種繞線的事情
其實是很難的
所以它有的時候呢
你可以想像
這支Tool有Bug
然後
它繞出來的線
不是那麼的好的話呢
可能就會產生
DRC的這個Violation
那
就是可以看Terminal
有沒有任何Violation
就是
跑這個之後呢
如果有出現Violation的話
會有XX
對
Layout上面會有
印象中是白色的XX
對
那你可以重新做Placement
就是回到上面的步驟
或者是手動
手動去學
學著在
有點像是
有點像是大家在畫Layout的
那種做法
就是去調整一些線寬啊
什麼東西的
把那個Violation修掉
就是像Homework 1
那個時候做的一樣
對
或者是你就回去
回去上一個步驟
因為它中間會有一些
Random Process
所以呢你跑了之後
搞不好它
重新跑一次之後
就會把這個DRC修掉
也有可能
對
通常我會建議重Layout
反正在各個步驟
出現一些我們很難
處理的問題的時候
因為這個EDA Tool
很多東西
不是我們自己可以控制的
所以大家其實經常問我說
很多時候我的答案會是
那你就重Layout
重頭Layout
或者是放寬條件
然後重Layout
對
通常都是這樣
好
那這邊呢
就是繼續照著步驟做
DRC確定沒有問題之後呢
接下來就是要Add Highlight
在Highlight Title的這個Cell
那
首先呢
也是要先做一下Timeline Analysis
剛做了一些事情
又還沒做Timeline Analysis
就先做這個Timeline Analysis
這次呢
也是要Pre-CTS
因為我們還是還沒做CTS
然後也是一樣
WMS如果是負的
也是做這個Ultimate Design
這樣子
然後呢
Ultimate Design
這個地方呢
這個Ultimate Type
這邊可以加選一些東西
按OK
那就可以再多做幾次
這邊就是我們說
可以做個三四次
直到這個
WMS修好為止
然後
Add Highlight Title Cell
我們剛剛說要做這件事情
把這個東西
連到Highlight跟Title Cell上面
怎麼做呢
執行
Place
Highlight Title Cell
Add Mode
然後選
Highlight Row
Cell Name
要首打這兩個東西
然後勾選這個東西
這個要設定為10
來吧
勾選起來
後面那個框框要點10
然後
Specify Maximum Distance
只有100
按OK
不好意思
喝個水
好
那Cell Name這邊呢
它應該已經幫你設定為
Highlight跟Title
然後按OK
它中間應該會有空格啦
對
好
然後呢
再來就是我們剛剛講了好幾次的CTS
那
對
就是CTS跟Power Rob
我們剛剛前面說這兩個步驟
如果
你有看到有調換的
那是正常的
CTS呢
就是你要產生Cloud Tree
Cloud Tree
老師上課應該會有講過
為了避免一些Skill
還有一些問題
它就要長得有點像Tree
它要很對稱之類的
一個一個長出去
兩個兩個分出去
這樣子
那
基本上呢
這些設定呢
我們都有給
給一些
給一些Script檔啊
或者是一些設定檔啊
都給大家
所以呢
就是
要在Terminal
輸入指令
去執行那一些
我們給大家的檔案
要設定這個東西
基本的參數呢
你只要去Source
這個檔案
它是Tcl檔
Tcl檔就是Tcl檔
它就是一個Script的檔案
可以點開來
應該也是可以直接讀取的
可以去看看它寫了什麼
反正你就直接Source它就好
東西也都不用改
然後根據你的
這個就是你的Design嘛
APR.SDC
APR的SDC檔
那它會產生對應的一些參數
那這就是要Create
然後Create之後呢
反正就是照著這些指令打
然後Source這個東西
它Create出來是這個檔案
CCout.spec
然後Source它
Source完之後呢
就可以打這個東西
CCout.design
然後空格-cts
有的時候這個
這個投影片上面的-啊
你可以看到這邊的-比較小
這個-比較大
這有可能是全型的
所以這個如果你複製的話
它有時候如果
你要注意指令
它會不會跟你講說沒有
就是指令執行出錯
這個我記得
有的時候它會自動給我變成全型的
我記得我改過
可是它
我改了好幾年了
可是它每次都這樣子
就是
就會給我跳掉
我也不知道為什麼
反正就是它複製的時候
有時候要小心這個-號
好
那做完
剛剛那樣子
其實它就會自動幫你生成-cts
這個CloudTree了
那CloudTree之後呢
就是
CloudTree生成之後呢
你就要做Post-cts的Timing Analysis
Post-cts呢
就是-cts之後的Timing Analysis
它就會比較複雜一點
它要多做一個事情
就是
你Timing Report Timing之後呢
選這個Post-cts之後呢
Analyze Type呢
你就要選Setup跟Hold的兩種
兩種都要做分析
Setup Time跟Hold Time都要做分析
那
對
如果Setup Time跟Hold Time是什麼東西
不知道呢
可以在
另外再來問我
對
然後一樣
就是看WMS是不是負的
如果是負的
那就是ECO Optimize Design
然後呢
Stage要換
現在是Post-cts
按OK
重複執行很多次
直到WMS修好為止
為什麼會有一個11.4
反正就是
一樣是重複執行
反正就是你如果
這個有Timing Violation
就是要重複執行
到它為正為止
好
那
再來就是PowerRoute
Power呢
有一些比較詳細的東西
你要去重新
就是再接著做這樣子
現在呢
你做完PowerRoute之後呢
應該下面會長這個樣子
你要選Route
Special Route裡面呢
它就會有這個
要選這個Basic Next
然後
加入這個點點點之後呢
你要加入VCC跟VSS
那
這個SRoute這個Page呢
那個Block裡面呢
只留下這個Follow Pins
然後按OK
就裡面有很多勾選的東西
你只留下這個東西就好
然後按OK
那就可以看到這個
Coastal的那些藍色線呢
就會連到左右的PowerRoute上面
就會跑出這些藍色線
好
然後呢
這個時候呢
你又做了兩三件事情
我們又要重新
又要重新做這個DRC的Check
然後Connectivity的Check這樣子
那反正就是Connectivity也是
Design Rule Check的其中一個
一個項目啦
這樣
就是也是DRC的一個Rule
這樣子
它也是
要先把這個
我們剛剛說這個
就是一些雜七雜八的垃圾
把它清除掉
Refine Placement
它就會清除掉那些垃圾
然後呢
就是Verify Connectivity
然後Net Type選Special Only
然後Check取消掉這個
這個Unrouted Net
按OK
它就會去做這個DRC的Connectivity的Check
這樣
然後呢
如果有任何Violation的話
一樣
我們就是說你可以用
想辦法用手動的方式去
把問題修正
或者是回到前面的步驟
重新Layout
重新跑一些
重新執行一些步驟這樣子
對
這是我們說的
一千零一招
重Lay
對
之後呢
就是確認
就是重複執行這個Verify
執行到它沒有Connectivity為止
這樣
沒有Violation為止
快結束了
大家再忍耐一下
好
下一步呢
是Nanoroute
Nanoroute呢
就是你要選這個
Route Nanoroute
然後Route
然後就會跑出一個視窗
那勾選呢
就勾這個東西
然後後面會有
叫你填Cell Name
就填Antenna
然後勾選Timing Driven
勾選這個
然後按OK之後
右邊會有Attribute
然後
不是按OK
是按OK右邊的Attribute
然後打開之後呢
也是選這個東西
這我已經有點忘記它長什麼樣子了
反正它應該是一個視窗
然後把這個東西填進去
把Weight跟Spacing填進去
然後Avoid Detour
意思就是說
就是
繞圈的時候越短越好按
然後按OK
然後
反正它是兩層的視窗
按OK
按OK之後開始Routing
看有沒有violation
到這邊呢
基本上繞線就幾乎完成了
繞出來的結果可能就會長這樣
然後Post Route的Timing Analysis
快結束了
快結束了
我們在做這個Timing Analysis
然後呢
Analyze Mode呢
要在Terminal
特別輸入這個指令
輸入這個指令之後呢
再回到這個
GUI的介面
執行Timing Report
Report Timing
這樣
然後Design Stage
這次呢
已經是Post Route了
快結束了
然後Analyze Tab
也是一樣
我們會有分成Setup跟Hold兩種
那一樣
WMS為副的話呢
也是要Optimize Design
Design Stage要記得改成Post Route
而且要加選Maximum Banout
就是前面沒有做的事情
按OK
然後它就可以幫你去Optimize Design
直到你WMS修為正的為止
這些東西都是自動修的
所以如果修不好的話
我也沒辦法
只能重做幾次
或者是放寬條件
或者是重勒
最後呢
就是要做DRC Check
也是一樣
Verify Verify Geometry
按OK
然後如果沒有
如果出錯的話
也是像前面說的一樣
手動去修它
然後再來就是存檔
終於要結束了
太棒了
存檔
存檔呢
我們說現在是Post Layout Simulation
所以呢
它就是
Post Sim的這個Stage
然後
按File Save Netlist
那這時候呢
你就會存出你的APR.V檔
Netlist File呢
填入你的
這個作業的這個
這個Module的名稱
底線APR
大寫的.V
按OK
然後呢
一樣
我們說
在
合成之後的Stage呢
都會有時間的資訊
所以呢
Timer這邊啊
就要把這個SDF檔也要存出來
我們說SDF檔是
Sender Delay Format
存一些時間的資訊在裡面
那就是取消勾選這個Idea Clock
然後Output的檔名也是一樣
跟前面一樣
但是後面是點SDF
那按OK
所以你的Gate Level跟APR Level
它的這個SDF檔是不同的
這樣
然後Generate Area Report
就是
寫Area Report
我們到時候這個
這個評分的時候
也會看這個面積的Report
那就是File
Report
Summary
然後選Text Only
然後存一個檔案出來
看到時候作業要求是
要求什麼
那要求什麼檔名
然後按OK之後呢
我們會看的是
Total Area of Core
大家可以去看這個東西
這是我們要大家看的面積
也就是你Chip的中心
Core的地方的這個面積啊
看到關閉Innovus很開心
就是要把GDS存出來
那這個跟我們作業的時候一樣
會有GDS檔案
那也是
按照步驟按
按一按之後呢
左邊欄位可以選這個
Stream Out
然後取消勾選這個東西
按OK
File
Save
GDS這個東西
然後Output File Name
打跟前面一樣
點GDS
然後Map File
這個要手動打這個東西
這個要手動打
對 要記得這個東西
然後勾選Merge File
然後也是要填入這些東西
我記得這個好像也都是要手動打的
中間要用空格隔開
然後勾選Write Abstract Information
for LEF Macros Unit 1000
反正這個就是照著填
按OK
之後呢
你的GDS就會吐出來了
你就可以關閉Innovus了
好 到此為止
無聊的東西
總算是結束了
那我們影片也只剩下兩張
前面那些無聊的東西呢
大家就是照著按就好了
就是我剛剛重複很多遍了
因為我們不太有辦法
實際在這邊操作給大家看
所以就是大家
辛苦大家隨便聽一聽
我的流水帳這樣
那這邊再來就比較重要
大家可能需要稍微專注聽一下
就是Post Layout Simulation
就是我們剛剛說
Layout之後呢
還會有一次Simulation
那這次呢
就是要做Layout之後的Simulation
我們通常會叫Post Sim
那就是
你可以有兩種方法去做這個Simulation
其實它其實是一種方法
就是你可以打這個
NZ Babylog
然後Test Feature
就是你的這個Test Bench
然後你這個某某檔案的
這個APR.V
然後要加-V
然後這個TSMC E3
底線Negative.V
這個東西也要加進來
一起做Simulation
然後後面我們說
會有這個Define SDF
加SDF啊
加FSDB啊
那是什麼東西
這個要看
這個作業2的這個
檔案裡面
有時候大家說
模擬的指令應該要加什麼
那有時候可能你要加SS加R
這邊我就沒有打出來
最重要的是你要加這個
NC Max Delay
有同學常常沒有打這個S喔
然後跟我說
跑出來的結果有問題
然後我就Debug很久
然後發現這個東西沒打
這東西要打
而且要記得還是有S的
然後這個指令啊
你其實可以把它
打在一個檔案裡面
然後你就可以
把它取名叫
用底線APR.F
檔名可以隨便取啊
反正就是你可以
ncvlog-f
它就會去讀這裡面的檔案
也是把它當作是一個
Script檔來處理這樣子
它就會去執行後面這個東西
這樣
那如果模擬沒有過的話呢
一樣就是我們說
你可以慢慢提高這個
Test Bench的Cycle Time
這樣子
然後也是可能
你要重新Layout啊
重新合成啊
這樣
就是要避免
就是不能有這個
我們說Reset之前不能有
Reset之後不能有
Timing Violation
Reset之前的就還可以
這樣
所以這個Timing Violation呢
它後面會寫一些時間點
後面這邊會有一些
在哪裡啊
在這個
最下面這邊會有Time
12秒
12秒這邊
然後後面呢
就會
如果你程式執行
Pass的話
它就會出現這個結果
所以只要在Reset之前的話
就還OK
對
那最後呢
是一些常見的問題
就是
平常助教呢
大家常常會遇到一些問題
那把它列在這邊
那大家回去可以參考一下
就是
我看一下
這就是我們前面有特別講到
就是說
你合成啊
跟Layout的各種
各個Step啊
你在做合成
在做Layout
在做Gate Level Simulation
在做Post Layout Simulation的時候呢
這些Cycle
通通是要一致的
然後
這個
APR的時候呢
有的時候大家會不小心選錯
選成Synthesis的Stage的
SDF檔跟.V檔
Synthesis的Stage是這個東西嘛
那APR的時候是這個檔案
就是不要去選錯
選錯了之後
它就沒有
它就不一致嘛
它就不是Transistor Level的
這個Simulation這樣
然後
這邊也是我們剛剛前面
有稍微講一下
就是說
如果你調整Timing Constraint的話
你最好是要回到合成的階段
重新做一次合成
然後再重新做Layout這樣
然後
OK
Simulation如果失敗的話呢
這裡面有一些選項啦
就是大家常見的問題
首先呢
就是你很有可能
這個Variable跟SDF檔
選錯了
或者是甚至沒有選
你沒有Define SDF
或者是你SDF檔
所在的資料夾不在這裡
甚至你沒有寫出來之類的
記得去把它
就是Check這個東西
還有一些相對路徑
或者是這個連結
確認它是正確的
然後
如果不行的話呢
那你就是要放寬
這個Timing Constraint的條件
然後Repeat Synthesis跟Layout
就我們剛剛講的
放寬條件
重Lay跟重合成
重合成跟重Lay這樣
然後呢
在做Layout Simulation的時候
有的時候你設定
譬如說10秒
然後它
Timing的這個
這個Check它過了
WMS是正的
但是
實作上呢
我們確實是會遇到
有的時候
它還是
Simulation還是會有
Timing Violation這樣
那原因呢
會有很多種
那我這邊就不把它
全部講出來
因為實在蠻多的
但是
通常啊
你可以在Test Page裡面呢
試著先把Clock Cycle放寬
那放寬之後呢
看看它的
它的結果怎麼樣
通常我用10秒去做
那通常到
可能到15、16
或許都還是合理的
對
好那再來
如果真的不行的話
你就是要開N-Web
然後看
所有的這個
Register有什麼問題
好
那我想
大概就到這邊
那大家如果有什麼問題的話
可以
來問我
或者是
老師要接著上課嗎
中間有下課
接著上喔
那不然就是
我會在
國立430
所以如果大家有
事情的話
想要問我問題的話
有沒有什麼問題
現在要直接問
那如果沒有的話
直接問
好啊
剛剛好像有同學
想要問我問題
還是你們
上完課之後
來國立430找我
上課應該是
那亞明你等一下
我3點
好
不然我就先在這邊
等一下好了
OK
