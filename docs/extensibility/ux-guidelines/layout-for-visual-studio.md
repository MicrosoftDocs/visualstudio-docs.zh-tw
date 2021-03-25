---
title: Visual Studio 的版面配置 |Microsoft Docs
description: 瞭解 Visual Studio 對話方塊的版面配置，包括 unthemed 對話方塊及具有主題外觀的新對話方塊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1c15b7458bfd18314015bbb9228c212a06fcd82f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072971"
---
# <a name="layout-for-visual-studio"></a>適用於 Visual Studio 的配置
大部分的 Visual Studio 對話方塊都是 [公用程式對話](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)配置，其為遵循標準 [Windows 桌面對話版面配置原則](/windows/desktop/uxguide/win-dialog-box)的 unthemed 對話方塊。 當 Visual Studio 移動以重新整理其 UI 時，某些較重要的對話會有新的設計，可將其建立為產品定義體驗。 這些 [主題的對話版面](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) 配置具有主題的外觀。

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> 公用程式對話版面配置

- 公用程式對話方塊內的所有控制項都應該從左上方開始，然後往下流動。

- 絕對不要在對話方塊上將控制項置中以填滿大型區域。

- 使用所有對話文字的環境字型。 撰寫 visual 規格時，請指定環境字型，而不是選取特定字型和大小。 請參閱 [環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

- 使用一致的控制間距和位置，以支援熱情技術中的品質目標。

- 對話方塊可能會變得更複雜，因為控制項數目較大、控制項的獨特 juxtaposition 或兩者。 在這些複雜的情況下，允許控制項群組之間有足夠的空間，讓使用者能夠進行剖析的邏輯流程。

### <a name="utility-dialog-layout-examples"></a>公用程式對話版面配置範例
 所有維度都會以圖元表示。

 ![控制項上方之標籤的對話方塊間距](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **圖 08.01-a：具有上方標籤之公用程式對話方塊的間距指導方針**

 ![控制項左側之標籤的對話方塊間距](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **圖 08.01-b：公用程式對話方塊的間距指導方針，以及控制項左邊的標籤**

### <a name="layout-details"></a>版面配置詳細資料

#### <a name="margins"></a>邊界

- 所有的對話都應該在所有邊緣周圍都有一個12圖元的框線。

- 群組框架內的邊界應為框架邊緣的9圖元。

- 索引標籤控制項內的邊界應該是從索引標籤控制項邊緣6圖元。

#### <a name="command-buttons"></a>命令按鈕

- 命令按鈕會在對話方塊框架上操作，而不是在內容上操作。 它們應該放在右下方，而且在上方應該有足夠的變數空間，才能以截然不同的分隔按鈕。

- 如果對話方塊中有操作的水準按鈕，則替代的命令按鈕設定會是右上方的垂直堆疊。 請參閱下方的 [內部命令按鈕](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) 。

- 命令按鈕左邊的空間 (在對話方塊的左下方/中央) 被視為對話作業控制項「頻外」的一部分。 應該在該空間上 intrude 的唯一內容是與整體工作或對話方塊相關的說明連結。

- 命令按鈕應該是75x23 圖元。

- 命令按鈕的間隔應該是6圖元。

  ![基本按鈕對齊方式](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **圖 08.01-c：基本按鈕對齊**

#### <a name="labels"></a>標籤

- 將所有標籤靠左對齊。

- 針對位於控制項上方的標籤，這些標籤應以精確對齊其下的控制項，而且標籤的底部應該是位於其他控制項上方的5圖元 (例如，下拉式方塊) 。

- 如果是位於控制項左邊的標籤，則標籤與輸入控制項之間的最小寬度為10圖元。 應該建立隱含的第二個數據行，以對齊文字方塊、下拉式方塊或其他控制項。

- 標籤是句子大小寫，後面接著冒號。 請參閱 [文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。

#### <a name="distance-between-controls"></a>控制項之間的距離
 合理的堆疊控制項。 堆疊控制項之間的間距沒有絕對的指導方針。 控制項之間的 tightness 在對話之間可能稍微不同。 建議的間距是垂直控制項/標籤配對的20圖元，以及水準控制項/標籤配對的9個圖元。 水準配對的最小控制間距為6圖元。

 ![控制項的建議間距](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **圖 08.01-d：控制項之間的距離建議**

#### <a name="control-indentation"></a>控制項縮排
 當控制項進行嵌套時，會以上述控制項的左邊緣水準對齊內部控制項，通常是標籤。

 ![巢狀控制項對齊方式](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **圖 08.01-e：嵌套控制項對齊**

#### <a name="control-width"></a>控制項寬度
 文字方塊或其他類似控制項的寬度不應超過欄位的平均輸入。 英文單字的平均是五個字元。 例如，需要長路徑名稱的文字方塊應該只要水準配置允許，而平臺名稱的下拉式清單應該只是允許最長專案的長度。

#### <a name="helper-text"></a>Helper 文字

- 對話方塊可顯示協助程式文字，以提供有關對話用途的詳細資訊。 這通常位於頂端，而且可以是1-2 句子。

- 行長度應該是方便使用者剖析和讀取的慣用寬度。 中型對話的寬度不應超過550圖元。

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> 內部命令按鈕
 在更複雜的對話中，內部控制項可能會有自己的相關按鈕，這可能會影響對話方塊的 [認可] 按鈕所在的位置。

- 當 **[確定** / **取消**] 在右下角以水準方向方向時，使用垂直對齊 (資料行) 內部按鈕。

- 當 **[確定** / **取消**] 在右上角垂直方向時，請使用 [內部] 按鈕的水準對齊 (資料列) 。 這種情況較不常見。

- 內部按鈕大小應以75x23 圖元的標準按鈕大小為目標，並盡可能符合 **[確定** / **取消**] 按鈕的大小。 如果按鈕標籤讓按鈕超過標準按鈕的大小，則該集合中的其他按鈕應與較大的大小對齊。

  ![水平並排 [確定] 和 [取消] 按鈕](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **圖 08.01-f：垂直的內部按鈕（具有水準的 [確定]/[取消]）**

  ![垂直並排 [確定] 和 [取消] 按鈕](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **圖 08.01-g：水準的內部按鈕與垂直的 [確定]/[取消]**

#### <a name="browse-button"></a>[流覽 ...]按鈕
 **[流覽 ...]** 文字方塊後面的按鈕應該會將「流覽 ...」完整，包括省略號。 如果空間太過了，或螢幕上有多個 **[流覽 ...]** 按鈕，則按鈕可以縮減為只有省略號。

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> 主題對話版面配置
 Visual Studio 中的主題對話方塊有較輕的外觀，並提供更多的空白字元。 印刷樣式可提供更多的強調和興趣，並提供更多的開放行間距以及字型大小和加權的變化。 可能的話，已減少或移除 chrome 和標題列。 這些對話方塊的版面配置應遵循下列基本模式：

1. 對話方塊的背景是白色。

2. 中間值灰色有一個1圖元的規則框線。

3. 對話方塊標題不再位於標題列中，而是以較大的點大小提供視覺效果和強調。  (查看 [文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)中的字型大小區段。 ) 

4. 加上其他文字的標籤（例如描述）應該是 **環境字型 + 粗體**。

5. 內部資料行以淺灰色的1圖元規則分隔。

6. 預設連結沒有底線。 [暫止] 和 [已按下] 狀態的色彩變更加底線。

7. 認可按鈕 (例如 **[確定** / **取消**]，) 位於右下角。

### <a name="themed-dialog-layout-examples"></a>主題對話版面配置範例
 ![佈景主題對話方塊版面配置](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **圖 08.01-h：主題對話方塊**

 ![佈景主題對話方塊維度](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **圖 08.01-i：主題對話方塊-維度**

 ![佈景主題對話方塊字型](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **圖 08.01-j：主題對話方塊-字型**

 ![佈景主題對話方塊色彩](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **圖 08.01-k：主題對話方塊-色彩**

## <a name="see-also"></a>另請參閱
- [適用於 Visual Studio 的應用程式模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [ (Windows) 的控制項 ](/windows/desktop/uxguide/controls)
- [ (Windows) 的對話方塊 ](/windows/desktop/uxguide/win-dialog-box)
