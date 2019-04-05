---
title: Animations
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241a9f628ab731552a01b2ccbefe55fe53dbe3e0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940161"
---
# <a name="animations-for-visual-studio"></a>適用於 Visual Studio 的動畫
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>動畫的基本概念

### <a name="animation-best-practices-in-visual-studio"></a>在 Visual Studio 中的動畫最佳作法
 請遵循這些規則，以確保 Visual Studio IDE 一致且容易使用的動畫樣式。

-   **是選擇性的。** 限制於特定用途的動畫。

-   **計時和速度很重要，** 以確保轉換可以快速且自然：

    -   二分之一秒 （500 毫秒） 內的完整動畫的轉換。

    -   需要快速而不中斷使用者的工作流程會經常發生的動畫。

    -   動畫不應該如此快速或突兀，很難了解，但無法這麼慢，它會使一個耐心不足以完成轉換。

    -   您可以使用變數的執行時間來強調重要性。 比方說，瀏覽時透過在類別圖上的項目序列，加快項目之間的轉換，然後將焦點放在重要的項目變慢。

-   **使用漸進式非線性加/減速**到另一個狀態，從提供的冷靜且自然的移動

-   可能的話，請**暫留時使用精巧的動畫**表示互動的項目，將滑鼠下方。

-   如果您依賴動畫功能，您再**能用來將它們關閉**在本機 （適用於所有的功能） 中的選項形式**工具 > 選項**對話方塊。

-   **一次應該只有一張動畫**和傳達只是一段資訊。

-   **一些微妙的差異很重要。** 在大部分情況下動畫不必要求使用者的注意力提供其用途。 細微的變更，在執行時間、 順序和行為可能會大幅影響 perception，而且可以有效和無效動畫之間的差異。

-   使用動畫來強調某樣東西時,**請確定它是值得中斷使用者**的訓練的想法。

-   **顯示進度或狀態時**透過動畫：

    -   停止顯示進行移動，當基礎程序不會逐步引導。

    -   確定處理序中區別不定的程序。

    -   請確定動畫有識別完成和失敗的狀態。

    -   最小化使用的顯示狀態，並確定它們有真正的值，藉由提供實際使用的其他資訊的效果動畫。 範例包括暫時性的狀態變更和緊急情況

#### <a name="do-not"></a>不執行：

- 使用小型的移動 （移動較小的使用量中），偏好淡出和變更透過移動物件。

- 使用透過螢幕面積的大型區域的動畫。 不論大小，這種動畫樣式是令人分心的使用者。

- 使用不與目前著重於使用者的物件或互動的動畫。

- 使用需要使用者介入即可重設狀態，例如強制使用者回應閃爍的通知，以使其停止閃爍的動畫。 與其進行互動，以任何方式應該就足以關閉它們。

  如需有關這些最佳作法的應用程式的詳細資訊，請參閱[動畫模式](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)。

### <a name="animation-metrics"></a>動畫計量

-   系統應該明顯地因應小於 10 毫秒中的使用者手勢。

-   動畫的轉換不應該超過 500 毫秒完成。

-   補償需要較長的時間轉換的方法之一是分成兩個部分;例如，動畫的第一個部分可能是後面內容淡出，到容器 （最多 500 毫秒） 的空白內容容器 （最多 500 毫秒為單位）。

-   可以計算的載入時間、 行列式進度列指示器 （%完成進度指標） 是慣用的。

-   無法計算的載入時間，例如資料指標或內嵌的旋轉的動畫 （載入或使用指標） 的忙碌指示器是合適的。

### <a name="animation-as-communicator"></a>為 communicator 的動畫
 在 Visual Studio 的 UI 中，動畫只會做的通訊工具。  它用來通訊的各項資訊，例如在 UI 中; 的結構化變更例如，當功能表開啟或關閉。 動畫可以協助您視覺化複雜的系統，例如 安裝進度的視覺效果的時間相關的行為，或用來吸引注意透過警示與通知。

 UI 動畫通常函式以四種方式： 視覺化、 吸引注意，模擬，並指出回應中/進行倍。

#### <a name="visualize"></a>以視覺化方式檢視
 動畫可以強調 3d 物件的本質，並讓使用者更輕鬆地以視覺化方式檢視其空間的結構。 若要達到此目的，動畫可能需要啟動完整的圓形中的物件緩時變來回，開啟或將接近的物件並稍微增加其大小，以強調變換或焦點。

 雖然三維物件可以使用來移動使用者控制項設計工具 （以程式設計方式或手動） 應該事先判斷如何以最佳以動畫顯示提供最佳的了解物件的移動。 此程式設計動畫可以，然後啟動使用者將游標移到物件，而使用者控制移動要求的使用者了解如何操作物件。 限制到單一座標軸或一次; 的方向移動可能是調整、 旋轉、 或翻譯，但不要同時執行多個。

 視覺化類別包含的層面的資料、 關聯性、 狀態、 結構、 序列和時間。

##### <a name="data"></a>資料
 說明複雜和多變的資訊：

-   資訊視覺效果，例如圖表和圖形中移動

-   透過一系列逐步執行、 導覽和分頁

-   呼叫的詳細資料、 指向，並反白顯示特定的資訊

-   覆疊詳細資料和焦點的項目上的其他資訊

-   到另一個結構化或組織的表示法從變形

-   代表一段時間的使用時間滑桿、 jog&lt 接駁車輪胎和傳輸控制項 （播放、 停止和暫停） 的變更。

##### <a name="relationships"></a>關聯性

-   說明如何項目之間的關聯性，或指定的項目與相關的項目。

-   顯示階層和父-子系或同層級關聯性

-   一個項目會產生另一個

-   一個項目最小化至另一個項目

-   行動網卡到另一個項目

##### <a name="state"></a>狀況

-   內容更新。

-   使用者焦點和選取範圍

-   進度

-   錯誤

##### <a name="structure"></a>結構

-   結構，其中一個節點上的進行樞紐分析

-   Reorienting

-   最小化和最大化，或展開和摺疊

##### <a name="sequence"></a>序列

-   投影片的順序

-   翻閱圖片

##### <a name="time"></a>時間

-   顯示變更的時間、 時間間隔和螢幕錄製影片

-   移至清除、 復原和取消復原

-   還原歷程記錄的狀態

#### <a name="attract-attention"></a>吸引注意
 如果目標是要繪製為單一項目，從數個使用者的注意力，或通知使用者有更新的資訊，動畫可能是適當的。 例如，您的應用程式起始頁可能採用網頁載入後，到投影片 [開始] 按鈕。

 因此，最後一個移動的項目，在螢幕上會吸引使用者的注意力。  在一系列的動畫元素中，使用者的注意力將遵循的最後一個移動的物件。

##### <a name="alert"></a>警示

-   提醒使用者注意，顯示進度

-   顯示的項目是正確或不正確，或顯示進度或進行變更

-   工作，例如尋找線上的詳細資訊，或深入了解目前的工作過程中提示使用者

##### <a name="notifications"></a>通知

-   警示的錯誤狀況的相關使用者

-   中斷使用者看到他們想要處理其他事情

-   輕輕通知之使用者的處理程序已完成，或變更，例如當下載完成時。

#### <a name="simulate"></a>模擬
 這個類別涵蓋了 physicality 和維度。

-   說明物件均來自或他們移至的位置

-   展開和摺疊或開啟和關閉

-   移動瀏覽、 向下捲動，以及網頁結果

-   堆疊和疊置順序

-   浮動切換和 accordion

-   翻轉和旋轉 UI

#### <a name="response-and-progress-indicators"></a>回應與進度指標
 進度指標有幾個值得注意的優點：

-   同時確定及不確定的進度指示器 reassure 的使用者，系統已不會當機，並會處理此問題。

-   確定指標提供進行了解動作過程的進展，以及能一目了然的完成時間接近的使用者。

##  <a name="BKMK_AnimationPatterns"></a> 動畫模式

### <a name="overview"></a>總覽
 在 Visual Studio 中的動畫是用來提供特定功能並不會妨礙使用者產能。 包含符合一般動畫特性：

- 小又不礙眼

- 自然且真實方式呈現

- 細微和同胞

- 快速又有效率

- 放寬，不 hurried

  下圖顯示建議您在 Visual Studio 中使用的動畫樣式。 沒有動畫和細微的動畫例如淡入/淡出最常使用。 有限的應用程式的擴大和縮減這類的動畫的移動，X 和 Y 位置變更及旋轉。

  ![Visual Studio 的建議動畫樣式](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202 a_VSAnimStyles")

  **Visual Studio 的建議的動畫樣式**

#### <a name="appear-and-disappear"></a>顯示和消失
 使用此模式時，項目從切換可見到外的檢視而不會轉換動畫：

 ![顯示&#47;消失在 Visual Studio 中的動畫](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202 b_AppearAndDisappear")

##### <a name="correct-usage"></a>正確使用方式
 全新的 UI 項目需要立即出現或消失，讓使用者不會分心或擋住。 此外，緩慢移動的動畫可能被視為效能拖曳，會出現和消失樣式不會發生一次。

##### <a name="incorrect-usage"></a>不正確的使用方式
 案例中即會出現 UI 因此突然使用者根本不知道發生了什麼事，並將動畫新增有助於了解內容。

##### <a name="animation-properties"></a>動畫屬性
 時間延遲通常是零秒。

##### <a name="examples"></a>範例

-   自動隱藏工具視窗

-   鍵盤啟用編輯器 UI，例如 IntelliSense 和參數說明

-   展開-和-摺疊程式碼區域

#### <a name="fade-in-and-fade-out"></a>淡入與淡出
 使用此模式時，UI 項目則是從看不到 （0%不透明） 轉換為可見 （100%不透明），反之亦然︰

 ![淡出&#45;中&#47;淡出&#45;Visual Studio 中的動畫解](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202 c_FadeInFadeOut")

##### <a name="correct-usage"></a>正確使用方式
 這是最常建議 UI 動畫。 它是一個微妙效果將感興趣，而不需中斷流程。 在某些情況下，使用者甚至不知道有是動畫，並直接察覺到平滑的流動 UI 系統。

##### <a name="animation-properties"></a>動畫屬性

-   開始的不透明度：淡入，淡出的 100%的 0%

-   結束不透明度：淡入，淡出的 0%的 100%

-   持續時間：200 毫秒獨立，當做組合動畫順序的一部分使用時的 100 毫秒

-   加/減速樣式：InOut 的正弦值

##### <a name="examples"></a>範例

-   自動隱藏工具視窗

-   功能表開啟和關閉

-   Background 和 foreground 索引標籤轉換

#### <a name="color-blend-from-a-to-b"></a>從 A 到 B 的色彩 blend
 使用此模式時，UI 項目用來變更從色彩的色彩 b:

 ![在 Visual Studio 中的動畫的色彩調和](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202 d_ColorBlend")

##### <a name="correct-usage"></a>正確使用方式
 與時的 UI 項目從一個內容或狀態色彩變更為另一個動畫轉換。

##### <a name="animation-properties"></a>動畫屬性

-   開始色彩：UI 特定

-   結束色彩：UI 特定

-   持續時間：200 毫秒獨立，當做組合動畫順序的一部分使用時的 100 毫秒

-   加/減速樣式：InOut 的正弦值

##### <a name="examples"></a>範例

-   文件視窗狀態轉換 (作用中，最後一個作用中、 與非作用中)

-   工具視窗狀態轉換 （專注於目標和未取得焦點）

#### <a name="expand-and-contract"></a>進行擴大和縮減
 使用此模式時，UI 項目展開的 X、 Y 或兩個方向中：

 ![依序展開&#47;合約在 Visual Studio 中的動畫](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202 e_ExpandContract")

##### <a name="correct-usage"></a>正確使用方式
 與時的 UI 項目從一個內容大小變更為另一個動畫轉換。

##### <a name="animation-properties"></a>動畫屬性

-   X 小數位數: %或特定維度 （以像素為單位）

-   Y 比例: %或特定維度 （以像素為單位）

-   錨點位置：一般而言，左上角 （適用於左到右的語言） 或者 （適用於從右至左的語言） 的右上方

-   持續時間：200 毫秒獨立，當做組合動畫順序的一部分使用時的 100 毫秒

##### <a name="examples"></a>範例

-   架構總管面板展開和摺疊

-   起始的頁的項目展開和摺疊

#### <a name="x-y-position-change"></a>X Y 位置變更
 利用此模式中，UI 項目會變更其 X 或 Y 位置，或兩者：

 ![X&#47;Y 位置變更 Visual Studio 中的動畫](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202 f_XYPositionChange")

##### <a name="correct-usage"></a>正確使用方式
 與 UI 項目從一個內容位置變更到另一個動畫的轉換。

##### <a name="animation-properties"></a>動畫屬性

-   從 X 和 Y 位置：UI 特定

-   結束 X 和 Y 位置：UI 特定

-   移動路徑：None

-   持續時間：200 毫秒獨立，當做組合動畫順序的一部分使用時的 100 毫秒

-   加/減速樣式：InOut 的正弦值

##### <a name="example"></a>範例
 重新排列索引標籤

#### <a name="rotate"></a>旋轉
 使用此模式時，會旋轉的 UI 項目：

 ![Visual Studio 中的旋轉動畫](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202 g_Rotate")

##### <a name="correct-usage"></a>正確使用方式
 只會針對不定的旋轉進度列指示器。

##### <a name="animation-properties"></a>動畫屬性

-   旋轉的角度：360

-   旋轉中心：物件的

-   持續時間：持續

##### <a name="example"></a>範例
 不確定的進度指示器 （旋轉）

### <a name="common-shell-ui-actions-and-recommended-animations"></a>常見的殼層 UI 動作和建議的動畫

#### <a name="tab-open"></a>索引標籤上開啟

- 樣式：出現

- 持續時間：零秒

  ![索引標籤上開啟 Visual Studio 中的動畫](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202 h_TabOpen")

#### <a name="tab-close"></a>關閉索引標籤

- 樣式：X 位置變更

- 持續時間：200 毫秒

  ![索引標籤關閉 Visual Studio 中的動畫](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202 i_TabClose")

#### <a name="tab-reorder"></a>索引標籤重新排序

- 樣式：X 位置變更

- 持續時間：200 毫秒

  ![索引標籤上的 Visual Studio 中的重新排序動畫](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202 j_TabReorder")

#### <a name="close-floating-document"></a>關閉浮動文件

- 樣式：出現

- 持續時間：200 毫秒

  ![關閉 Visual Studio 中浮動文件動畫](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202 k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>視窗狀態轉換

- 樣式：若要配合其他視窗，可讓定義文件關閉動畫目前的作業系統。

- 持續時間：200 毫秒

  ![在 Visual Studio 中的視窗狀態轉換動畫](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202 l_WindowStateTransition")

#### <a name="menu-open"></a>功能表中開啟

- 樣式：淡入

- 持續時間：200 毫秒

  ![在 Visual Studio 中的功能表開啟動畫](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202 m_MenuOpen")

#### <a name="menu-close"></a>關閉功能表

- 樣式：Fade-out

- 持續時間：200 毫秒

  ![在 Visual Studio 中的功能表關閉動畫](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202 n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>自動隱藏工具視窗中顯示

- 樣式：出現

- 持續時間：零秒

  ![自動&#45;隱藏在 Visual Studio 中的工具視窗動畫](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")
