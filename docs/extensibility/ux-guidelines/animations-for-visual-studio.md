---
title: 視覺工作室動畫 |微軟文件
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc11eb7bab69728be5ceaa55143f56e93cd1fca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698613"
---
# <a name="animations-for-visual-studio"></a>適用於 Visual Studio 的動畫
## <a name="animation-fundamentals"></a>動畫基礎知識

### <a name="animation-best-practices-in-visual-studio"></a>視覺化工作室中的動畫最佳實務
遵循這些規則,確保整個 Visual Studio IDE 的動畫樣式一致且使用者友好。

- **有選擇性。** 將動畫限制為用於特定目的的動畫。

- **時間和速度對於**確保過渡感覺快速自然非常重要:

  - 在半秒(500毫秒)內完成動畫過渡。

  - 經常發生的動畫需要足夠快,這樣它們就不會中斷使用者的工作流。 在迴圈中觀看動畫並調整計時,直到感覺正確為止。

  - 動畫不應該那麼快或不和諧,以至於很難理解,但不要那麼慢,以至於它讓人不耐煩地完成過渡。

  - 使用可變計時來強調重要性。 例如,在類圖上導航一系列專案時,快速流覽項之間的轉換,然後減慢速度以專注於重要項。

- 使用從一種狀態到另一種狀態**的漸進非線性緩動**,給人一種平靜和自然運動的感覺。

- 如果可能,**請使用懸停上的精細動畫**來指示滑鼠下方的互動式元素。

- 如果嚴重依賴要素中的動畫,則**提供一種在**「**工具>選項**」對話框中將其在本地(針對所有要素)關閉的方法。

- **一次只能出現一個動畫**,只傳達一條資訊。 多個對象移動或嘗試傳達多個內容可能會令人困惑。

- **微妙是很重要的。** 在大多數情況下,動畫不需要要求使用者注意來達到其目的。 時間、順序和行為的細微變化可能會顯著影響感知,並可以區分有效和無效的動畫。

- 當使用動畫來吸引對某物的注意時 **,請確保它值得打斷使用者的**思路。

- 以動畫**顯示進度或狀態時**:

  - 當基礎進程未前進時,停止顯示進度移動。

  - 區分不確定的流程和確定的進程。

  - 確保動畫具有可識別的完成和失敗狀態。

  - 通過提供實際使用的其他資訊,盡量減少顯示狀態的效果動畫的使用,並確保它們具有實際價值。 範例包括瞬態狀態更改和緊急情況

#### <a name="animation-donts"></a>動畫不:

- 不要使用小運動(在小尺寸內移動)。 首選淡入淡出和更改而不是移動的物件。

- 不要使用發生在大面積的螢幕空間的動畫。 無論大小,這種動畫樣式都會分散使用者的注意力。

- 不要使用與使用者當前關注的物件或與物件交互無關的動畫。

- 不要使用需要使用者交互來重置狀態的動畫,例如強制用戶回應閃爍的通知,以便停止閃爍。 以任何方式與他們互動應該足以解僱他們。

有關這些最佳實務的應用程式的詳細資訊,請參閱[動畫模式](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)。

### <a name="animation-metrics"></a>動畫指標

- 系統應在 10 毫秒內對用戶手勢做出明顯回應。

- 動畫轉換完成的時間不應超過 500 毫秒。

- 補償需要較長時間的過渡的一種方法是將其分為兩部分。 例如,動畫的第一部分可以是空內容容器(最多 500 毫秒),然後是內容淡入容器(最多 500 毫秒)。

- 對於可以計算的載入時間,首選決定因素進度指示器(完成進度指標的百分比)。

- 對於無法計算的載入時間,適合使用游標或嵌入式旋轉動畫(載入或工作指示器)等繁忙指示器。

### <a name="animation-as-communicator"></a>動畫作為傳播者
在可視化工作室 UI 中,動畫僅作為通信工具運行。  它用於傳達各種資訊,如 UI 中的結構更改(例如,當功能表打開或關閉時)。 動畫可以幫助可視化複雜系統的時間相關行為,如安裝進度可視化。 動畫還可用於通過警報和通知吸引注意力。

 UI 動畫通常以四種方式運行:可視化、吸引注意力、類比和回應時間/進度指示器。

#### <a name="visualize"></a>視覺化
動畫可以強調物件的三維性質,使用戶更容易可視化其空間結構。 為此,動畫可能需要將物件旋轉成一個完整的圓,緩慢地來回旋轉,或者使物件更近,並稍微增加其大小以強調翻轉或焦點。

儘管可以使用使用者控件移動三維物件,但設計人員應提前(以程式設計或手動方式)確定如何最好地為運動設置動畫,以便對物件進行最佳理解。 然後,使用者可以通過將游標放在對象上來啟動此程式設計動畫,而使用者控制的行動要求使用者瞭解如何操作物件。 將移動限制為一次的單個軸或方向;縮放、旋轉或平移,但同時執行多個操作。

可視化類別包括數據、關係、狀態、結構、順序和時間的各個方面。

##### <a name="data"></a>資料
說明複雜和可變的資訊:

- 瀏覽圖表及圖像化資訊視覺化效果

- 單步執行序列、導遊和分頁

- 呼叫詳細資訊、指向與突顯特定資訊

- 疊加焦點元素頂部的詳情和其他資訊

- 從一個結構或組織表示形式轉變為另一個結構或組織代表

- 使用時間滑塊、慢跑和穿梭輪以及運輸控制(播放、停止和暫停)表示隨時間的變化

##### <a name="relationships"></a>關聯性

- 說明專案如何彼此關聯,或哪些專案與給定項目相關

- 顯示層次結構和父子或兄弟姐妹關係

- 元素產生另一個元素

- 元素最小化到另一個元素

- 一個元素被拴在另一個元素上

##### <a name="state"></a>State

- 內容更新

- 使用者焦點與選擇

- 進度

- Errors

##### <a name="structure"></a>結構

- 在一個節點上透視結構

- 調整方向

- 最小化和最大化或展開和折疊

##### <a name="sequence"></a>順序

- 投影片放映序列

- 翻閱圖片

##### <a name="time"></a>Time

- 顯示隨時間推移、時間推移和截屏的變更

- 移至垃圾、復原和重做

- 復原歷史狀態

#### <a name="attract-attention"></a>吸引注意力
如果目標是將使用者的注意力吸引到多個元素中的單個元素,或提醒使用者更新資訊,則動畫可能是合適的。 例如,應用程式起始頁可能使用「入門」按鈕,該按鈕在頁面載入後滑入到位。

通常,螢幕上的最後一個移動元素會吸引使用者的注意。  在一系列動畫元素中,使用者的注意力將跟隨最後一個移動物件。

##### <a name="alert"></a>警示

- 提醒使用者,引起注意,顯示進度

- 顯示某些操作執行正確或不正確或顯示進度或進度變更

- 在工作期間提示使用者,例如線上搜尋更多資訊或瞭解有關目前的工作的資訊

##### <a name="notifications"></a>通知

- 提醒使用者有關錯誤準則

- 中斷使用者以查看他們是否想關注其他內容

- 輕輕地通知用戶進程已完成或更改,例如下載完成時。

#### <a name="simulate"></a>Simulate
此類別涵蓋物理性和維度性。

- 說明物件來自何處或它們去向何處

- 展開與摺疊或開啟與關閉

- 平移、滾動和頁面翻頁

- 堆疊與 z 排序

- 旋轉木馬和手風琴

- 翻轉及旋轉 UI

#### <a name="response-and-progress-indicators"></a>反應與進度指標
進度指標有幾個顯著的優勢:

- 確定進度指標和不確定進度指示器都向使用者保證系統尚未崩潰,並且正在處理該問題。

- 確定指標使用戶瞭解操作的進展有多遠,以及接近完成的感覺。

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a>動畫模式

### <a name="overview"></a>概觀
Visual Studio 中的動畫旨在在不妨礙使用者工作效率的情況下提供特定功能。 通常,可視化工作室中的動畫應該是:

- 小而不顯眼

- 自然和現實

- 微妙和柔和

- 快速高效

- 放鬆,不匆忙

此圖顯示了我們為 Visual Studio 推薦的動畫樣式。 沒有動畫或微妙的動畫,如淡入淡出/淡出是最常用的。 運動動畫(如擴充和收縮、X 和Y位置更改以及旋轉)的應用有限。

![Visual Studio 的建議動畫樣式](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Visual Studio 的建議動畫樣式

#### <a name="appear-and-disappear"></a>出現並消失
使用此模式,元素從可見切換到視圖外,無需過渡動畫即可返回。

![顯示與消失動畫](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />顯示與消失動畫

##### <a name="correct-usage"></a>正確的用法
需要立即顯示或消失的新鮮 UI 元素,以便使用者不會分心或受阻。 此外,慢動作動畫可能被視為性能拖動,這在顯示和消失樣式中不會發生。

##### <a name="incorrect-usage"></a>使用不正確
UI 突然出現,使用者不知道發生了什麼,添加動畫將有助於上下文理解。

##### <a name="animation-properties"></a>動畫屬性
時間延遲通常為零秒。

##### <a name="examples"></a>範例
- 自動隱藏工具視窗

- 鍵盤啟動編輯器 UI,如智慧感知和參數説明

- 擴充及摺疊碼區域

#### <a name="fade-in-and-fade-out"></a>淡入淡出
使用此模式,UI 元素從不可見(0% 不公開性)轉換為可見(100% 不公開性),反之亦然。

![淡入與淡出動畫](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />淡入與淡出動畫

##### <a name="correct-usage"></a>正確的用法
這是最常推薦的 UI 動畫。 這是一種微妙的效果,在不中斷流量的情況下增加興趣。 在某些情況下,使用者甚至可能沒有意識到有一個動畫,感知一個平滑和流動的 UI 系統。

##### <a name="animation-properties"></a>動畫屬性

- 開始不一用性:0%用於淡入,100%用於淡出

- 結束不成性:100%用於淡入,0%用於淡出

- 持續時間:獨立 200 毫秒,用作組合動畫序列的一部分時為 100 毫秒

- 放鬆風格:因內

##### <a name="examples"></a>範例

- 自動隱藏工具視窗

- 選單開啟與關閉

- 背景與前景選項卡過渡

#### <a name="color-blend-from-a-to-b"></a>顏色混合從 A 到 B
使用此模式,UI 元素從顏色 A 更改為顏色 B。

![色彩混合動畫](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />色彩混合動畫

##### <a name="correct-usage"></a>正確的用法
當 UI 元素將顏色從一個上下文或狀態更改為另一個上下文或狀態時,作為動畫過渡。

##### <a name="animation-properties"></a>動畫屬性

- 起始顏色:特定於 UI

- 結束顏色:特定於 UI

- 持續時間:獨立 200 毫秒,用作組合動畫序列的一部分時為 100 毫秒

- 放鬆風格:因內

##### <a name="examples"></a>範例

- 文件視窗狀態轉換(活動、上次活動與非活動)

- 工具視窗狀態轉換 (焦點與非焦點)

#### <a name="expand-and-contract"></a>擴充和收縮
使用此模式,UI 元素在 X、Y 或兩個方向中展開。

![展開並收縮動畫](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />展開並收縮動畫

##### <a name="correct-usage"></a>正確的用法
當 UI 元素將大小從一個上下文更改為另一個上下文時,作為動畫過渡。

##### <a name="animation-properties"></a>動畫屬性

- X 比例:% 或特定大小 (以像素為單位)

- Y 比例:% 或特定尺寸 (以像素為單位)

- 錨點位置:一般左上角(從左至右語言)或右上方(對於從右到左的語言)

- 持續時間:獨立 200 毫秒,用作組合動畫序列的一部分時為 100 毫秒

##### <a name="examples"></a>範例

- 結構結構資源管理員面板展開和折疊

- 視覺化工作室 2017 起始頁項目展開和摺疊

#### <a name="x-y-position-change"></a>X-Y 位置變化
使用此模式,UI 元素將更改其 X 或 Y 位置或兩者。

![X-Y 位置改變動畫](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />X-Y 位置改變動畫

##### <a name="correct-usage"></a>正確的用法
當 UI 元素將位置從一個上下文更改為另一個上下文時,作為動畫過渡。

##### <a name="animation-properties"></a>動畫屬性

- 啟動 X 與 Y 位置:特定於 UI

- 結束 X 與 Y 位置:特定於 UI

- 運動路徑:無

- 持續時間:獨立 200 毫秒,用作組合動畫序列的一部分時為 100 毫秒

- 放鬆風格:因內

##### <a name="example"></a>範例
選項卡重新排序

#### <a name="rotate"></a>旋轉
使用此模式,UI 元素將旋轉。

![UI 元素旋轉動畫](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />UI 元素旋轉動畫

##### <a name="correct-usage"></a>正確的用法
僅適用於不確定的旋轉進度指示器。

##### <a name="animation-properties"></a>動畫屬性

- 旋轉程度: 360

- 旋轉中心:物件中間

- 持續時間:連續

##### <a name="example"></a>範例
不確定進度指示器(旋轉)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>常見的 shell UI 操作和建議的動畫

#### <a name="tab-open"></a>選項卡開啟
![選項卡開啟動畫](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />選項卡開啟動畫

- 樣式:顯示

- 持續時間:零秒

#### <a name="tab-close"></a>選項卡關閉
![選項卡關閉動畫](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />選項卡關閉動畫

- 樣式:X 位置變化

- 持續時間: 200 毫秒

#### <a name="tab-reorder"></a>選項卡重新排序
![Visual Studio 中的索引標籤重新排序動畫](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />選項卡重新排序動畫

- 樣式:X 位置變化

- 持續時間: 200 毫秒

#### <a name="close-floating-document"></a>關閉浮動文件
![關閉浮動文件動畫](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />關閉浮動文件動畫

- 樣式:顯示

- 持續時間: 200 毫秒

#### <a name="window-state-transition"></a>視窗狀態轉換
![視窗狀態轉換動畫](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />視窗狀態轉換動畫

- 樣式:要與其他視窗一致,讓當前操作系統定義文檔關閉動畫。

- 持續時間: 200 毫秒

#### <a name="menu-open"></a>選單開啟
![選單開啟動畫](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />選單開啟動畫

- 樣式:淡入

- 持續時間: 200 毫秒

#### <a name="menu-close"></a>選單關閉
![選單關閉動畫](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />選單關閉動畫

- 樣式:淡出

- 持續時間: 200 毫秒

#### <a name="auto-hide-tool-window-reveal"></a>自動隱藏工具視窗顯示
![自動隱藏工具視窗顯示動畫](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />自動隱藏工具視窗顯示動畫

- 樣式:顯示

- 持續時間:零秒
