---
title: 動畫
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c07fb0887ae01ec917b39f5d7537d5a78fb5a4c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825363"
---
# <a name="animations-for-visual-studio"></a>適用於 Visual Studio 的動畫
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>動畫基礎

### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio 中的動畫最佳作法
 遵循這些規則，確保 Visual Studio 的 IDE 之間有一致且方便使用的動畫樣式。

- **是選擇性的。** 將動畫限制為提供特定用途的動畫。

- **時機和速度很重要** ，可確保轉換感覺迅速且自然：

  - 在一半秒內完成動畫轉換， (500 毫秒) 。

  - 經常發生的動畫必須夠快，才不會中斷使用者的工作流程。

  - 動畫的速度不應太快或 jarring，因為它很難瞭解，但不太慢，因為這會造成轉換完成的一個不耐。

  - 使用可變時機來強調重要性。 例如，流覽類別圖上的一連串專案時，加速專案之間的轉換，然後將焦點放在重要的專案上。

- 使用從某個狀態到另一個狀態的**漸進式非線性簡化**，讓您有意義的平靜和自然移動

- 可能的話，請 **在滑鼠停留時使用微妙動畫** 來表示滑鼠下的互動式元素。

- 如果您高度依賴功能中的動畫，則會 **提供一種方法，將** 您的所有功能的本機 () 為 [ **工具 > 選項** ] 對話方塊中的選項。

- 一**次只能有一個動畫**，而且只會傳達一項資訊。

- **奧妙很重要。** 在大部分情況下，動畫並不需要要求使用者注意來提供其用途。 時間、順序和行為的微妙變更可能會大幅影響感知，而且可以在有效和沒有效率的動畫之間產生差異。

- 當您使用動畫來強調某個事物時， **請確定它可以中斷使用者**的想法訓練。

- 透過動畫**顯示進度或狀態時**：

  - 當基礎進程未前進時，停止顯示進度移動。

  - 區分不確定的進程與確定進程。

  - 確定動畫具有可識別的完成和失敗狀態。

  - 透過提供實際使用的其他資訊，將顯示狀態並確保其具有真正價值的效果動畫的使用降至最低。 範例包括暫時性狀態變更和緊急狀況

#### <a name="do-not"></a>請勿：

- 使用小型移動 (在較少的空間) 中移動，偏好將移動物件淡化和變更。

- 使用在大型螢幕空間區域上進行的動畫。 不論大小為何，這個動畫樣式都會與使用者產生干擾。

- 使用與使用者目前專注于或互動的物件無關的動畫。

- 使用需要使用者互動的動畫來重設狀態，例如強制使用者回應閃爍的通知，以便停止閃爍。 以任何方式與其互動，應該就足以將它們關閉。

  如需這些最佳作法的應用程式詳細資訊，請參閱 [動畫模式](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)。

### <a name="animation-metrics"></a>動畫計量

- 系統應該會在10毫秒內以明顯的方式回應使用者手勢。

- 動畫轉換的完成時間不應超過500毫秒。

- 補償需要較長時間之轉換的一種方法，是將它分成兩個部分：例如，動畫的第一個部分可以是空的內容容器 (最多500毫秒) 接著會將內容淡入容器 (最多500毫秒的) 。

- 針對可計算的載入時間，偏好的進度指標 (百分比-完成進度指標) 。

- 針對無法計算的載入時間， (載入或工作指標) 等忙碌的指標或內嵌的旋轉動畫都適用。

### <a name="animation-as-communicator"></a>作為 communicator 的動畫
 在 Visual Studio 的 UI 中，動畫只能做為通訊工具。  它是用來傳達各種資訊，例如 UI 中的結構化變更;例如，開啟或關閉功能表時。 動畫可協助將複雜系統的時間相依行為視覺化，例如安裝進度視覺效果，或用來吸引出警示和通知的注意力。

 UI 動畫通常會以四種方式運作：視覺化、吸引注意力、模擬及指出回應時間/進度。

#### <a name="visualize"></a>視覺化
 動畫可以強調物件的三維本質，讓使用者更容易將其空間結構視覺化。 若要達到此目的，動畫可能需要以完整圓形旋轉物件、慢慢地來回轉換，或讓物件更接近且稍微增加，以強調變換或焦點。

 雖然三維物件可以透過使用者控制項來移動，但設計工具應該事先判斷 (以程式設計方式或手動方式) 如何以程式設計的方式，更有效地為物件提供最佳的理解效果。 然後，使用者可以藉由將游標放在物件上，而使用者控制的移動需要使用者瞭解如何操作物件，來啟動這個程式設計的動畫。 一次將移動限制為單一軸或方向;調整、旋轉或轉譯，但不要同時進行多項作業。

 視覺化類別包含資料、關聯性、狀態、結構、順序和時間的層面。

##### <a name="data"></a>資料
 說明複雜和變數資訊：

- 移動圖表和圖形等資訊視覺效果

- 逐步執行序列、引導式導覽和分頁

- 呼叫詳細資料，指向並反白顯示特定資訊

- 在焦點元素上方覆迭詳細資料和其他資訊

- 從一個結構化或組織標記法變形至另一個

- 使用時間滑杆、拐點和往復式輪子，以及傳輸控制 (播放、停止和暫停) ，來代表一段時間的變更。

##### <a name="relationships"></a>關聯性

- 說明專案與另一個專案之間的關聯性，或專案與指定專案的關聯性。

- 顯示階層和父子式或同級關聯性

- 一個元素會產生另一個專案

- 一個元素會最小化至另一個元素

- 一個元素行動網卡至另一個專案

##### <a name="state"></a>State

- 內容更新。

- 使用者焦點和選取

- 進度

- Errors

##### <a name="structure"></a>結構

- 在一個節點上旋轉結構

- Reorienting

- 最小化和最大化，或展開和折迭

##### <a name="sequence"></a>順序

- 投影片放映順序

- 翻轉圖片

##### <a name="time"></a>時間

- 顯示隨時間、時間間隔和螢幕錄製影片的變更

- 移至垃圾桶、復原和重做

- 還原歷程記錄狀態

#### <a name="attract-attention"></a>吸引關注
 如果目標是要將使用者的注意力放在多個專案中，或要提醒使用者更新資訊，則可能會有適當的動畫。 例如，您的應用程式啟動頁面可能會採用在頁面載入之後滑入位置的消費者入門按鈕。

 作為規則，畫面上的最後一個移動元素吸引使用者的注意力。  在一連串的動畫專案中，使用者的注意將會遵循最後移動的物件。

##### <a name="alert"></a>警示

- 警示使用者、取得注意、顯示進度

- 顯示已正確或不正確地完成某項工作，或顯示進度或進度變更

- 在工作期間提示使用者，例如尋找線上的詳細資訊，或瞭解目前的工作

##### <a name="notifications"></a>通知

- 警示使用者有關錯誤狀況

- 中斷使用者，看看他們是否想要參與其他內容

- 將已完成或已變更的進程（例如下載完成時），輕輕通知使用者。

#### <a name="simulate"></a>Simulate
 此類別涵蓋 physicality 和維度。

- 說明物件來自或移至何處

- 展開和折迭或開啟和關閉

- 移動流覽、滾動和翻頁

- 堆疊和 z 順序

- 浮動切換和可折疊

- 翻轉和旋轉 UI

#### <a name="response-and-progress-indicators"></a>回應和進度指示器
 進度指示器有幾個值得注意的優點：

- 確定和不定進度指標都會讓使用者，指出系統尚未損毀，而且正在處理此問題。

- 確定指標可讓使用者瞭解動作進展的進度，以及更接近完成的感覺。

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> 動畫模式

### <a name="overview"></a>概觀
 Visual Studio 中的動畫旨在提供特定功能，而不會妨礙使用者的生產力。 要遵守的一般動畫特性包括：

- 小型和不顯眼

- 自然和真實

- 微妙和 subdued

- 快速且有效率

- 寬鬆，非急章

  下圖顯示建議在 Visual Studio 中使用的動畫樣式。 沒有動畫和微妙的動畫，例如淡入/淡出的最常使用。 移動動畫的有限應用，例如展開和收縮、X 和 Y 位置變更和旋轉。

  ![Visual Studio 的建議動畫樣式](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202-a_VSAnimStyles")

  **Visual Studio 的建議動畫樣式**

#### <a name="appear-and-disappear"></a>出現並消失
 使用這個模式時，專案會在沒有轉換動畫的情況下，從可見度切換為不顯示和回復：

 ![出現&#47;Visual Studio 中消失的動畫](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202-b_AppearAndDisappear")

##### <a name="correct-usage"></a>正確的使用方式
 需要立即出現或消失的全新 UI 元素，讓使用者不會受到操作或阻礙。 此外，緩慢的移動動畫可能會被視為效能拖曳，而不會出現在出現和消失的樣式中。

##### <a name="incorrect-usage"></a>使用方式不正確
 UI 出現的情況突然出現，使用者就不知道發生什麼事，而新增動畫可協助您瞭解內容。

##### <a name="animation-properties"></a>動畫屬性
 時間延遲通常是零秒。

##### <a name="examples"></a>範例

- 自動隱藏工具視窗

- 鍵盤啟用的編輯器 UI，例如 IntelliSense 和參數說明

- 展開和折迭程式碼區域

#### <a name="fade-in-and-fade-out"></a>淡入和淡出
 使用這個模式時，UI 專案會從不可見的 (0% 不透明度) 轉換為可見 (100% 不透明度) 或反之亦然：

 ![淡化&#45;的&#47;淡出&#45;動畫 Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202-c_FadeInFadeOut")

##### <a name="correct-usage"></a>正確的使用方式
 這是最常見的建議 UI 動畫。 這是不會中斷流程而新增興趣的微妙效果。 在某些情況下，使用者可能不會察覺到有動畫，而只是感覺流暢、流動的 UI 系統。

##### <a name="animation-properties"></a>動畫屬性

- 開始不透明度：淡化的0%，淡出的100%

- 結束不透明度：淡化的100%，淡出的0%

- 持續時間：在組合動畫序列中使用時，以200毫秒獨立，100毫秒

- 簡化樣式：正弦 InOut

##### <a name="examples"></a>範例

- 自動隱藏工具視窗

- 開啟和關閉功能表

- 背景和前景 tab 轉換

#### <a name="color-blend-from-a-to-b"></a>從 A 到 B 的色彩 blend
 使用這個模式時，UI 專案會從色彩 A 變更為色彩 B：

 ![Visual Studio 中的色彩調和動畫](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202-d_ColorBlend")

##### <a name="correct-usage"></a>正確的使用方式
 當 UI 專案將色彩從某個內容或狀態變更為另一個內容時的動畫轉換。

##### <a name="animation-properties"></a>動畫屬性

- 開始色彩： UI 特定

- 結束色彩： UI 特定

- 持續時間：在組合動畫序列中使用時，以200毫秒獨立，100毫秒

- 簡化樣式：正弦 InOut

##### <a name="examples"></a>範例

- 檔視窗狀態轉換 (作用中、最後使用中和非使用中) 

- 工具視窗狀態轉換 (聚焦和未取得焦點) 

#### <a name="expand-and-contract"></a>展開和合約
 使用這個模式時，UI 元素會以 X、Y 或雙向展開：

 ![在 Visual Studio 中展開&#47;合約動畫](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202-e_ExpandContract")

##### <a name="correct-usage"></a>正確的使用方式
 當 UI 專案將大小從某個內容變更為另一個內容時的動畫轉換。

##### <a name="animation-properties"></a>動畫屬性

- X 縮放：% 或特定維度 (圖元) 

- Y 比例：% 或特定維度 (圖元) 

- 錨點位置：從右至左的語言) 的左上角 (，或從右至左語言的右上方 () 

- 持續時間：在組合動畫序列中使用時，以200毫秒獨立，100毫秒

##### <a name="examples"></a>範例

- 架構瀏覽器面板展開和折迭

- 展開和折迭起始頁專案

#### <a name="x-y-position-change"></a>X Y 位置變更
 使用這個模式時，UI 元素會變更其 X 或 Y 位置或兩者：

 ![X&#47;Y 位置變更動畫 Visual Studio](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202-f_XYPositionChange")

##### <a name="correct-usage"></a>正確的使用方式
 當 UI 元素變更從某個內容到另一個內容的位置時，這會成為動畫轉換。

##### <a name="animation-properties"></a>動畫屬性

- 開始 X 和 Y 位置： UI 特定

- 結束 X 和 Y 位置： UI 特定

- 移動路徑：無

- 持續時間：在組合動畫序列中使用時，以200毫秒獨立，100毫秒

- 簡化樣式：正弦 InOut

##### <a name="example"></a>範例
 Tab 重新排列

#### <a name="rotate"></a>旋轉
 使用這個模式時，UI 元素會旋轉：

 ![Visual Studio 中的旋轉動畫](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202-g_Rotate")

##### <a name="correct-usage"></a>正確的使用方式
 僅適用于不定的旋轉進度指標。

##### <a name="animation-properties"></a>動畫屬性

- 旋轉角度：360

- 旋轉中心：物件的中間

- 持續時間：連續

##### <a name="example"></a>範例
 不定的進度指標 (旋轉) 

### <a name="common-shell-ui-actions-and-recommended-animations"></a>常用的 shell UI 動作和建議的動畫

#### <a name="tab-open"></a>Tab 鍵開啟

- 樣式：出現

- 持續時間：零秒

  ![Visual Studio 中的索引標籤開啟動畫](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202-h_TabOpen")

#### <a name="tab-close"></a>Tab 關閉

- Style： X 位置變更

- 持續時間：200毫秒

  ![Visual Studio 中的索引標籤關閉動畫](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202-i_TabClose")

#### <a name="tab-reorder"></a>Tab 鍵重新排列

- Style： X 位置變更

- 持續時間：200毫秒

  ![Visual Studio 中的索引標籤重新排序動畫](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202-j_TabReorder")

#### <a name="close-floating-document"></a>關閉浮動檔

- 樣式：出現

- 持續時間：200毫秒

  ![Visual Studio 中的關閉浮動文件動畫](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202-k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>視窗狀態轉換

- 樣式：若要與其他視窗保持一致，請讓目前的作業系統定義檔關閉動畫。

- 持續時間：200毫秒

  ![Visual Studio 中的視窗狀態轉換動畫](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202-l_WindowStateTransition")

#### <a name="menu-open"></a>開啟功能表

- 樣式：淡化

- 持續時間：200毫秒

  ![Visual Studio 中的功能表開啟動畫](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202-m_MenuOpen")

#### <a name="menu-close"></a>功能表關閉

- 樣式：淡出

- 持續時間：200毫秒

  ![Visual Studio 中的功能表關閉動畫](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202-n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>自動隱藏工具視窗顯示

- 樣式：出現

- 持續時間：零秒

  ![自動&#45;在 Visual Studio 中隱藏工具視窗動畫](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")
