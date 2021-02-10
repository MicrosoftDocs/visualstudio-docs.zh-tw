---
title: Visual Studio 的動畫 |Microsoft Docs
description: 瞭解可協助確保 Visual Studio IDE 之間一致且方便使用之動畫樣式的規則。
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a7e8ea6514f29b99975b9e291d6a09ed2a0ad54e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934008"
---
# <a name="animations-for-visual-studio"></a>適用於 Visual Studio 的動畫
## <a name="animation-fundamentals"></a>動畫基礎

### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio 中的動畫最佳作法
請遵循這些規則，以確保 Visual Studio IDE 之間一致且方便使用的動畫樣式。

- **是選擇性的。** 將動畫限制為提供特定用途的動畫。

- **時機和速度很重要** ，可確保轉換感覺迅速且自然：

  - 在一半秒內完成動畫轉換， (500 毫秒) 。

  - 經常發生的動畫必須夠快，才不會中斷使用者的工作流程。 觀賞迴圈中的動畫，並調整時間直到感覺正確為止。

  - 動畫的速度不應太快或 jarring，因為它很難理解，而是讓轉換完成的不耐變得很慢。

  - 使用可變時機來強調重要性。 例如，流覽類別圖上的一連串專案時，加速專案之間的轉換，然後將焦點放在重要的專案上。

- 使用從某個狀態到另一個狀態的 **漸進式非線性簡化**，讓平靜和自然移動更加合理。

- 可能的話，請 **在滑鼠停留時使用微妙動畫** 來表示滑鼠下的互動式元素。

- 如果您高度依賴您的功能中的動畫，請 **提供一個方法，將** 您的所有功能的本機關閉 (，) 作為 [ **工具 > 選項** ] 對話方塊中的選項。

- 一 **次只能有一個動畫**，而且只會傳達一項資訊。 有一個以上的物件移動或嘗試傳遞多個專案可能會造成混淆。

- **奧妙很重要。** 在大部分的情況下，動畫不需要要求使用者注意來提供其用途。 時間、順序和行為的微妙變更可能會大幅影響感知，而且可以在有效和沒有效率的動畫之間產生差異。

- 當您使用動畫來強調某個事物時， **請務必中斷使用者** 的想法訓練。

- 透過動畫 **顯示進度或狀態時**：

  - 當基礎進程未前進時，停止顯示進度移動。

  - 區分不確定的進程與確定進程。

  - 確定動畫具有可識別的完成和失敗狀態。

  - 透過提供實際使用的其他資訊，將顯示狀態並確保其具有真正價值的效果動畫的使用降至最低。 範例包括暫時性狀態變更和緊急狀況

#### <a name="animation-donts"></a>動畫不應事項：

- 請勿使用小移動 (在) 的資源量內移動。 偏好淡化和移動物件的變更。

- 請勿使用在大型螢幕空間區域上進行的動畫。 不論大小為何，這個動畫樣式都會與使用者產生干擾。

- 請勿使用與使用者目前專注于或互動的物件無關的動畫。

- 請勿使用需要使用者互動的動畫來重設狀態，例如強制使用者回應閃爍的通知，以便停止閃爍。 以任何方式與其互動，應該就足以將它們關閉。

如需這些最佳作法的應用程式詳細資訊，請參閱 [動畫模式](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)。

### <a name="animation-metrics"></a>動畫計量

- 系統應該會在10毫秒內以明顯的方式回應使用者手勢。

- 動畫轉換的完成時間不應超過500毫秒。

- 補償需要較長時間之轉換的一種方法，就是將它分成兩個部分。 例如，動畫的第一個部分可能是空的內容容器 (最多500毫秒的) ，接著會將內容淡入容器 (最多500毫秒的) 。

- 針對可計算的載入時間，偏好的進度指標 (百分比-完成進度指標) 。

- 針對無法計算的載入時間， (載入或工作指標) 等忙碌的指標或內嵌的旋轉動畫都適用。

### <a name="animation-as-communicator"></a>作為 communicator 的動畫
在 Visual Studio UI 中，動畫只能做為通訊工具。  它是用來傳達各種資訊，例如 UI 中的結構變更 (例如，當功能表開啟或關閉) 時。 動畫可協助將複雜系統的時間相依行為視覺化，例如安裝進度視覺效果。 動畫也可以用來吸引出警示和通知的注意力。

 UI 動畫通常會以四種方式運作：視覺化、吸引注意力、模擬和回應時間/進度指標。

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

- 使用時間滑杆、拐點和往復式輪子，以及傳輸控制項 (播放、停止和暫停，來代表一段時間的變更) 

##### <a name="relationships"></a>關聯性

- 說明專案與另一個專案之間的關聯性，或專案與指定專案的關聯性

- 顯示階層和父子式或同級關聯性

- 一個元素會產生另一個專案

- 一個元素會最小化至另一個元素

- 一個元素行動網卡至另一個專案

##### <a name="state"></a>州

- 內容更新

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

##### <a name="time"></a>Time

- 顯示隨時間、時間間隔和螢幕錄製影片的變更

- 移至垃圾桶、復原和重做

- 還原歷程記錄狀態

#### <a name="attract-attention"></a>吸引關注
如果目標是要將使用者的注意力放在多個專案中，或要提醒使用者更新資訊，則可能會有適當的動畫。 例如，您的應用程式起始頁可能會採用在頁面載入之後滑入位置的開始使用按鈕。

作為規則，畫面上的最後一個移動元素吸引使用者的注意力。  在一連串的動畫專案中，使用者的注意將會遵循最後移動的物件。

##### <a name="alert"></a>警示

- 警示使用者、取得注意、顯示進度

- 顯示已正確或不正確地完成某項工作，或顯示進度或進度變更

- 在工作期間提示使用者，例如在線上尋找詳細資訊或學習目前的工作

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
Visual Studio 的動畫旨在提供特定的函式，而不會阻礙使用者的生產力。 一般而言，Visual Studio 中的動畫應該是：

- 小型和不顯眼

- 自然和真實

- 微妙和 subdued

- 快速且有效率

- 寬鬆，非急章

下圖顯示我們建議 Visual Studio 的動畫樣式。 沒有動畫或微妙的動畫，例如淡入/淡出的最常使用。 移動動畫的應用程式（例如 expand 和 contract、X 和 Y 位置變更和旋轉）有所限制。

![Visual Studio 的建議動畫樣式](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Visual Studio 的建議動畫樣式

#### <a name="appear-and-disappear"></a>出現並消失
使用這個模式時，專案會在沒有轉換動畫的情況下，從可見度切換為不顯示。

![出現並消失動畫](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />出現並消失動畫

##### <a name="correct-usage"></a>正確的使用方式
需要立即出現或消失的全新 UI 元素，讓使用者不會受到操作或阻礙。 此外，移動緩慢的動畫可能會被視為效能拖曳，這不會出現在出現和消失的樣式中。

##### <a name="incorrect-usage"></a>使用方式不正確
UI 出現的情況突然出現，使用者就不知道發生什麼事，而新增動畫可協助您瞭解內容。

##### <a name="animation-properties"></a>動畫屬性
時間延遲通常是零秒。

##### <a name="examples"></a>範例
- 自動隱藏工具視窗

- 鍵盤啟用的編輯器 UI，例如 IntelliSense 和參數說明

- 展開和折迭程式碼區域

#### <a name="fade-in-and-fade-out"></a>淡入和淡出
使用這個模式時，UI 專案會從不可見的 (0% 不透明度) 轉換為可見 (100% 不透明度) 或反之亦然。

![淡入和淡出動畫](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />淡入和淡出動畫

##### <a name="correct-usage"></a>正確的使用方式
這是最常見的建議 UI 動畫。 這是不會中斷流程而新增興趣的微妙效果。 在某些情況下，使用者可能根本不知道有動畫，察覺流暢且流動的 UI 系統。

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
使用這個模式時，UI 專案會從色彩 A 變更為色彩 B。

![色彩 blend 動畫](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />色彩 blend 動畫

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
使用這個模式時，UI 元素會以 X、Y 或雙向展開。

![展開和收縮動畫](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />展開和收縮動畫

##### <a name="correct-usage"></a>正確的使用方式
當 UI 專案將大小從某個內容變更為另一個內容時的動畫轉換。

##### <a name="animation-properties"></a>動畫屬性

- X 縮放：% 或特定維度 (圖元) 

- Y 比例：% 或特定維度 (圖元) 

- 錨點位置：從右至左的語言) 的左上角 (，或從右至左語言的右上方 () 

- 持續時間：在組合動畫序列中使用時，以200毫秒獨立，100毫秒

##### <a name="examples"></a>範例

- 架構瀏覽器面板展開和折迭

- Visual Studio 2017 起始頁專案展開和折迭

#### <a name="x-y-position-change"></a>X Y 位置變更
使用這個模式時，UI 元素會變更其 X 或 Y 位置或兩者。

![X 軸位置變更動畫](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />X 軸位置變更動畫

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

#### <a name="rotate"></a>Rotate
使用這個模式時，UI 元素會旋轉。

![UI 元素旋轉動畫](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />UI 元素旋轉動畫

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
![Tab 鍵開啟動畫](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Tab 鍵開啟動畫

- 樣式：出現

- 持續時間：零秒

#### <a name="tab-close"></a>Tab 關閉
![Tab 關閉動畫](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Tab 關閉動畫

- Style： X 位置變更

- 持續時間：200毫秒

#### <a name="tab-reorder"></a>Tab 鍵重新排列
![Visual Studio 中的索引標籤重新排序動畫](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Tab 鍵重新排列動畫

- Style： X 位置變更

- 持續時間：200毫秒

#### <a name="close-floating-document"></a>關閉浮動檔
![關閉浮動檔動畫](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />關閉浮動檔動畫

- 樣式：出現

- 持續時間：200毫秒

#### <a name="window-state-transition"></a>視窗狀態轉換
![視窗狀態轉換動畫](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />視窗狀態轉換動畫

- 樣式：若要與其他視窗保持一致，請讓目前的作業系統定義檔關閉動畫。

- 持續時間：200毫秒

#### <a name="menu-open"></a>開啟功能表
![功能表開啟動畫](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />功能表開啟動畫

- 樣式：淡化

- 持續時間：200毫秒

#### <a name="menu-close"></a>功能表關閉
![功能表關閉動畫](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />功能表關閉動畫

- 樣式：淡出

- 持續時間：200毫秒

#### <a name="auto-hide-tool-window-reveal"></a>自動隱藏工具視窗顯示
![自動隱藏工具視窗顯示動畫](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />自動隱藏工具視窗顯示動畫

- 樣式：出現

- 持續時間：零秒
