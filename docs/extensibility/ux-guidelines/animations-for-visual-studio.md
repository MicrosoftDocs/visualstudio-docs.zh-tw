---
title: "Visual Studio 的動畫 |Microsoft 文件"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a554a52fc5ef42f81d1531dbe63bf320e1cd72e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="animations-for-visual-studio"></a>Visual Studio 的動畫
## <a name="animation-fundamentals"></a>動畫的基本概念  
  
### <a name="animation-best-practices-in-visual-studio"></a>在 Visual Studio 中的動畫最佳作法  
請遵循這些規則，以確保 Visual Studio IDE 一致且方便使用動畫樣式。  
  
-   **是選擇性的。** 限制具有特定用途的動畫。  
  
-   **計時和速度是非常重要**以確保轉換覺得快速和自然：  
  
    -   二分之一秒 （500 毫秒） 內完成動畫進行轉換。  
  
    -   需要快速它們不會中斷使用者的工作流程會經常發生的動畫。 監看在迴圈中的動畫，以及調整計時，直到它享受。 
  
    -   不應該是動畫，因此快或突兀，很難了解，但不是如此慢，它會使其中一個耐完成轉換。  
  
    -   使用變數的執行時間來強調重要性。 例如，當瀏覽類別圖表上的項目序列，加快項目之間的轉換，然後專注於重要的項目變慢。  
  
-   **使用漸進式非線性 easing**從一個狀態到另一個，讓平靜和自然的。  
  
-   如果可能的話，**暫留時顯示使用精巧的動畫**表示在滑鼠互動項目。  
  
-   如果您依賴動畫的功能，然後**提供一種機制以將其關閉**本機 （為所有的功能） 中的選項為**工具 > 選項**對話方塊。  
  
-   **只有一個動畫應該會發生一次**而且傳達的資訊只在一個片段。 多個物件移動，或嘗試傳遞多個項目可能會造成混淆。 
  
-   **請務必微妙的地方。** 在大部分情況下，動畫不必要求使用者注意到有其用途。 在時間、 順序和行為稍有變更可能會大幅影響感覺，而且可以有效和無效的動畫之間的差異。  
  
-   當使用動畫吸引使用者注意到某樣東西，**確定值得中斷使用者**的定型的想法。  
  
-   **顯示進度或狀態時**透過動畫：  
  
    -   停止顯示基礎程序時不逐步引導進行移動。 
  
    -   不確定處理序區別確定處理程序。  
  
    -   請確定動畫具有可識別完成與失敗的狀態。  
  
    -   最小化效果的動畫顯示的狀態，並確定它們有實際值的實際使用的其他資訊提供使用。 範例包括暫時性的狀態變更及緊急事件  
  
#### <a name="animation-donts"></a>動畫準則：
  
-   請勿使用小型的移動 （移動較小的耗用量）。 偏好淡化，並透過移動物件變更。  
  
-   請勿使用實際螢幕面積大型區域上發生的動畫。 不論大小，這種樣式是動畫的令人分心給使用者。  
  
-   不使用使用者目前為焦點的物件不相關或與其互動的動畫。  
  
-   請勿使用需要使用者介入即可重設的狀態，例如強制使用者回應閃爍的通知，以使其停止閃爍的動畫。 與其互動，以任何方式應該很足夠，關閉它們。  
  
如需有關這些最佳作法的應用程式的詳細資訊，請參閱[動畫模式](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)。  
  
### <a name="animation-metrics"></a>動畫度量  
  
-   系統應該明顯地回應為小於 10 毫秒中的使用者手勢。  
  
-   動畫的轉換不應該花費超過 500 毫秒完成。  
  
-   為了彌補需要較長的時間轉換的方法之一是分成兩個部分。 例如，動畫的第一個部分可能是空內容的容器 （最多 500 毫秒），後面接著內容淡出到容器 （最多 500 毫秒為單位）。  
  
-   可計算的載入時間，是慣用行列式進度列指示器 （百分比完成進度指標）。  
  
-   無法計算的載入時間，如資料指標或內嵌的旋轉動畫 （載入或使用指標） 為忙碌指標是合適的。  
  
### <a name="animation-as-communicator"></a>為 communicator 動畫  
在 Visual Studio UI 中，動畫只會當做通訊工具。  它用來通訊的各種資訊，像是結構已變更的 UI （例如，功能表就會開啟或關閉時）。 動畫可協助視覺化複雜的系統，例如安裝進度的視覺效果的時間相關的行為。 動畫也可用來吸引注意力警示和通知。  
  
 UI 動畫通常函式以四種方式： 視覺化、 吸引注意、 模擬，和回應時間/進度指標。  
  
#### <a name="visualize"></a>以視覺化方式檢視  
動畫可以強調 3d 物件的本質，並讓使用者更輕鬆地以視覺化方式檢視其空間的結構。 若要達成此目的，動畫可能需要啟動完整的圓形中的物件速度很慢，來回開啟或將接近的物件並稍微增加其大小，以強調換用 」 或 「 焦點。  
  
雖然 3d 物件可能會移動與使用者控制項設計工具 （以程式設計方式或手動） 應該事先決定如何以最佳動畫顯示為提供最佳的了解物件的移動。 這動畫可以程式化，然後啟動使用者將游標放到物件，而由使用者控制移動需要使用者了解如何操作物件。 限制單一軸或一次; 方向移動可能是縮放、 旋轉，或翻譯，但不要同時執行多個。  
  
視覺化類別包含的資料、 關聯性、 狀態、 層面結構、 順序和時間。  
  
##### <a name="data"></a>資料  
說明複雜和變數的資訊：  
  
-   移動資訊視覺效果，例如圖表及圖形  
  
-   逐步執行順序、 導覽，以及分頁  
  
-   呼叫詳細資料，指向，並反白顯示特定的資訊  
  
-   覆疊詳細資料和焦點的項目之上的其他資訊
  
-   從結構化或組織的一種表示變形到另一個  
  
-   代表一段時間使用時間滑桿、 j o g 快速滾輪和傳輸控制 」 （播放、 停止及暫停） 的變更 
  
##### <a name="relationships"></a>關聯性  
  
-   說明如何項目相互關聯，或指定的項目與相關聯的項目
  
-   顯示階層和父系-子系或同層級關聯性
  
-   有一個項目會產生另一個
  
-   有一個項目降到最低，另一個項目
  
-   有行動網卡到另一個項目
  
##### <a name="state"></a>狀態  
  
-   內容更新
  
-   使用者焦點和選取範圍  
  
-   進度  
  
-   錯誤  
  
##### <a name="structure"></a>結構  
  
-   樞紐分析一個節點上的結構  
  
-   Reorienting  
  
-   最小化和最大化，或展開和摺疊  
  
##### <a name="sequence"></a>序列  
  
-   投影片放映順序  
  
-   翻閱圖片  
  
##### <a name="time"></a>時間  
  
-   隨著時間、 時間間隔和錄影畫面的顯示變更  
  
-   移至資源回收筒、 復原和取消復原  
  
-   還原歷程記錄的狀態  
  
#### <a name="attract-attention"></a>吸引注意  
如果目標是單一項目從數個使用者注意或警示使用者更新的資訊，動畫可能適合。 例如，您的應用程式起始頁可能會採用後在頁面載入的位置到投影片入門按鈕。  
  
因此，最後在螢幕上的移動項目會吸引使用者注意。  在一系列的動畫項目，使用者注意會遵循的最後一個移動的物件。  
  
##### <a name="alert"></a>警示  
  
-   提醒使用者、 吸引、 顯示進度  
  
-   顯示的項目進行正確或不正確，或顯示進度或正在進行的變更  
  
-   工作，例如尋找線上的詳細資訊，或深入了解目前的工作過程中提示使用者  
  
##### <a name="notifications"></a>通知  
  
-   警示的錯誤狀況的相關使用者  
  
-   中斷使用者看到他們想要處理其他事務  
  
-   輕輕通知使用者處理序已完成，或變更，例如下載完成時。  
  
#### <a name="simulate"></a>模擬  
這個類別涵蓋了 physicality 和維度。  
  
-   說明物件來自何處，或在前往的位置  
  
-   展開和摺疊或開啟和關閉  
  
-   移動瀏覽、 捲動、 和頁面會開啟  
  
-   堆疊和 z 順序  
  
-   浮動切換和 accordion 設定  
  
-   翻轉和旋轉 UI  
  
#### <a name="response-and-progress-indicators"></a>回應與進度指標  
進度指標有幾個值得注意的優點：  
  
-   同時確定及不確定的進度指示器 reassure 的使用者，系統不當機，並正致力於問題。  
  
-   確定指標給的使用者的幅度沿著動作的意義上的進度，以及取得完成更接近的感覺。  
  
##  <a name="BKMK_AnimationPatterns"></a>動畫模式  
  
### <a name="overview"></a>概觀  
在 Visual Studio 中的動畫，旨在提供特定的函式不會影響使用者產能。 一般而言，在 Visual Studio 中的動畫應：  
  
-   小型和不顯眼  
  
-   自然且真實方式呈現  
  
-   細微和同胞  
  
-   快速又有效率  
  
-   比較不嚴謹、 不 hurried  
  
下圖顯示動畫樣式，我們建議您針對 Visual Studio。 最常使用沒有動畫或難以察覺的動畫，像是淡入 / 淡出。 移動動畫像擴大和縮減的有限的應用程式，X 和 Y 位置變更和旋轉。 
  
![Visual Studio 的建議動畫樣式](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202 a_VSAnimStyles")<br />Visual Studio 的建議動畫樣式
  
#### <a name="appear-and-disappear"></a>會出現並會消失  
此模式中，項目切換從顯示出的檢視而不會轉換動畫。  
  
![顯示和消失動畫](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202 b_AppearAndDisappear")<br />顯示和消失動畫  
  
##### <a name="correct-usage"></a>正確使用方式  
全新的 UI 項目需要立即出現或消失，讓使用者為以致於產生比都受到阻擋。 此外，緩慢的動畫可能認為效能拖曳，將不會發生的顯示和消失的樣式。  
  
##### <a name="incorrect-usage"></a>使用方式不正確  
案例中即會出現 UI 因此突然使用者擁有不知道發生了什麼事，而且將動畫加入可與關聯式的理解。  
  
##### <a name="animation-properties"></a>動畫屬性  
時間延遲通常是零秒。  
  
##### <a name="examples"></a>範例    
-   自動隱藏工具視窗  
  
-   鍵盤啟動編輯器 UI，像是 IntelliSense 和參數說明  
  
-   展開和-摺疊程式碼區域  
  
#### <a name="fade-in-and-fade-out"></a>淡入與淡  
此模式中，UI 項目則是從不可見 （0%不透明） 轉換為可見 （100%不透明），反之亦然。  
  
![淡入與淡動畫](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202 c_FadeInFadeOut")<br />淡入與淡動畫  
  
##### <a name="correct-usage"></a>正確使用方式  
這是最常建議 UI 動畫。 它是將感興趣，而不會中斷流程微妙效果。 在某些情況下，使用者可能甚至不知道是動畫，察覺 smooth 及流送 UI 系統。  
  
##### <a name="animation-properties"></a>動畫屬性  
  
-   啟動不透明度： 淡的 0%，淡的 100%  
  
-   結束不透明度： 100%，淡入、 淡的 0%  
  
-   持續時間： 200 毫秒獨立、 100 毫秒組合動畫順序的一部分使用時  
  
-   Easing 樣式： 正弦 InOut  
  
##### <a name="examples"></a>範例  
  
-   自動隱藏工具視窗  
  
-   功能表開啟和關閉  
  
-   背景和前景 索引標籤的轉換  
  
#### <a name="color-blend-from-a-to-b"></a>從 A 到 B 的色彩混合  
此模式中，UI 項目用來變更色彩的色彩 b。  
  
![色彩調和動畫](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202 d_ColorBlend")<br />色彩 blend 動畫  
  
##### <a name="correct-usage"></a>正確使用方式  
與時的 UI 項目從一個內容或狀態色彩變更為另一個動畫轉換。  
  
##### <a name="animation-properties"></a>動畫屬性  
  
-   開始色彩： 特定的 UI  
  
-   結束色彩： 特定的 UI  
  
-   持續時間： 200 毫秒獨立、 100 毫秒組合動畫順序的一部分使用時  
  
-   Easing 樣式： 正弦 InOut  
  
##### <a name="examples"></a>範例  
  
-   文件視窗狀態轉換 (作用中，最後一個作用中、 與非作用中)  
  
-   工具視窗狀態轉換 （專注於目標和未取得焦點）  
  
#### <a name="expand-and-contract"></a>擴大和縮減  
此模式中，UI 項目會展開 X、 Y，或兩個方向。  
  
![展開和收合動畫](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202 e_ExpandContract")<br />展開和收合動畫  
  
##### <a name="correct-usage"></a>正確使用方式  
與 UI 項目大小從一個內容變更至另一個動畫轉換。  
  
##### <a name="animation-properties"></a>動畫屬性  
  
-   X 小數位數: %或特定維度 （以像素為單位）  
  
-   Y 比例: %或特定維度 （以像素為單位）  
  
-   錨點位置： 通常左上角 （適用於由左到右的語言） 或 （適用於由右至左語言） 的右上方  
  
-   持續時間： 200 毫秒獨立、 100 毫秒組合動畫順序的一部分使用時  
  
##### <a name="examples"></a>範例  
  
-   架構總管面板會展開和摺疊  
  
-   起始的頁項目展開和摺疊  
  
#### <a name="x-y-position-change"></a>X，Y 位置變更  
此模式中，UI 項目變更其 X 或 Y 位置，或兩者。  
  
![X，Y 位置變更動畫](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202 f_XYPositionChange")<br />X，Y 位置變更動畫  
  
##### <a name="correct-usage"></a>正確使用方式  
與 UI 項目從一個內容變更位置至另一個動畫的轉換。  
  
##### <a name="animation-properties"></a>動畫屬性  
  
-   啟動 X 和 Y 位置： 特定的 UI  
  
-   結束的 X 和 Y 位置： 特定的 UI  
  
-   移動路徑： 無  
  
-   持續時間： 200 毫秒獨立、 100 毫秒組合動畫順序的一部分使用時  
  
-   Easing 樣式： 正弦 InOut  
  
##### <a name="example"></a>範例  
重新排列索引標籤  
  
#### <a name="rotate"></a>旋轉  
此模式中，會旋轉的 UI 項目。  
  
![UI 項目旋轉動畫](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202 g_Rotate")<br />UI 項目旋轉動畫  
  
##### <a name="correct-usage"></a>正確使用方式  
僅針對不定微調進度列指示器。  
  
##### <a name="animation-properties"></a>動畫屬性  
  
-   旋轉的角度： 360  
  
-   旋轉中心： 中間的物件  
  
-   持續時間： 連續  
  
##### <a name="example"></a>範例  
不確定的進度指示器 （旋轉）  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>一般的殼層 UI 動作和建議的動畫  
  
#### <a name="tab-open"></a>索引標籤上開啟  
![索引標籤開啟動畫](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202 h_TabOpen")<br />索引標籤開啟動畫  
    
-   樣式： 出現  
  
-   零秒持續時間：  

#### <a name="tab-close"></a>關閉索引標籤  
![索引標籤關閉動畫](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202 i_TabClose")<br />索引標籤關閉動畫  
  
-   Style: X 位置變更  
  
-   持續時間： 200 毫秒  
  
#### <a name="tab-reorder"></a>索引標籤重新排序  
![索引標籤 Visual Studio 中的重新排序動畫](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202 j_TabReorder")<br />索引標籤重新排序動畫

-   Style: X 位置變更  
  
-   持續時間： 200 毫秒  
    
#### <a name="close-floating-document"></a>關閉浮動文件  
![關閉浮動文件動畫](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202 k_CloseFloatingDocument")<br />關閉浮動文件動畫  
   
-   樣式： 出現  
  
-   持續時間： 200 毫秒   
 
#### <a name="window-state-transition"></a>視窗狀態轉換  
![視窗狀態轉換動畫](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202 l_WindowStateTransition")<br />視窗狀態轉換動畫  
    
-   Style： 若要與其他 windows 一致，讓定義文件關閉動畫目前的作業系統。  
  
-   持續時間： 200 毫秒  
  
#### <a name="menu-open"></a>開啟功能表  
![功能表開啟動畫](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202 m_MenuOpen")<br />功能表開啟動畫  
    
-   樣式： 淡入  
  
-   持續時間： 200 毫秒  
  
#### <a name="menu-close"></a>關閉功能表  
![功能表關閉動畫](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202 n_MenuClose")<br />功能表關閉動畫  
    
-   樣式： 淡  
  
-   持續時間： 200 毫秒  
  
#### <a name="auto-hide-tool-window-reveal"></a>自動隱藏工具視窗中顯示  
![自動隱藏工具視窗中顯示動畫](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")<br />自動隱藏工具視窗中顯示動畫  

-   樣式： 出現  
  
-   零秒持續時間：