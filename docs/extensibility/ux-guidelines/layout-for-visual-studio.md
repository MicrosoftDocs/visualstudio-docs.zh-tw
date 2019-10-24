---
title: Visual Studio 的版面配置 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dfafa26b314c35f81e5caf9c433b1b630d916f4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747172"
---
# <a name="layout-for-visual-studio"></a>Visual Studio 的版面配置
大部分的 Visual Studio 對話方塊都是[公用程式對話版面](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)配置，其為遵循標準[Windows 桌面對話版面配置原則](/windows/desktop/uxguide/win-dialog-box)的 unthemed 對話方塊。 當 Visual Studio 移動以重新整理其 UI 時，有些較明顯的對話方塊會有新的設計，將其建立為產品定義體驗。 這些[主題的對話版面](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout)配置具有主題的外觀。

## <a name="BKMK_UtilityDialogLayout"></a>公用程式對話方塊版面配置

- 公用程式對話方塊中的所有控制項都應該從左上方開始，並向下流動。

- 永遠不要在對話方塊上將控制項置中，以填滿大型區域。

- 使用所有對話方塊文字的環境字型。 撰寫 visual 規格時，請指定環境字型，而不是選取特定字型和大小。 請參閱[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

- 使用一致的控制間距和位置，以支援熱情技術品質的目標。

- 對話方塊可能會變得更複雜，從較大量的控制項、控制項的唯一 juxtaposition 或兩者。 針對這些複雜的情況，請允許控制項群組之間有足夠的空間，讓使用者能夠進行剖析的邏輯流程。

### <a name="utility-dialog-layout-examples"></a>公用程式對話版面配置範例
 所有維度都會以圖元表示。

 ![控制項上方標籤的對話方塊間距](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **圖 08.01-a：在控制項上方具有標籤的公用程式對話方塊間距方針**

 ![控制項左邊標籤的對話方塊間距](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **圖 08.01-b：具有控制項左邊標籤之公用程式對話方塊的間距方針**

### <a name="layout-details"></a>版面配置詳細資料

#### <a name="margins"></a>邊界

- 所有的對話都應該在所有邊緣周圍都有12圖元的框線。

- 群組框架內的邊界應該是距框架邊緣9圖元。

- 索引標籤控制項內的邊界應該是從 [索引標籤] 控制項邊緣6個圖元。

#### <a name="command-buttons"></a>命令按鈕

- 命令按鈕會在對話方塊框架上運作，而不是在內容上操作。 它們應該放在右下方，而且上面應該有足夠的變數空間，才能將按鈕設定成截然不同的。

- 如果在對話方塊內有可運作的水準按鈕，則 [替代命令] 按鈕設定是右上方的垂直堆疊。 請參閱下方的[內部命令按鈕](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons)。

- 命令按鈕左邊的空間（對話方塊的左下方/中央）會被視為對話作業控制項的「波段」的一部分。 唯一應該在該空間上 intrude 的事項，是與整體工作或對話方塊相關的說明連結。

- 命令按鈕應為75x23 圖元。

- 命令按鈕的間距應為6圖元。

  ![基本按鈕對齊](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **圖 08.01-c：基本按鈕對齊**

#### <a name="labels"></a>標籤

- 靠左對齊所有標籤。

- 針對位於控制項上方的標籤，它們應該靠左對齊，而標籤的底部應該是另一個控制項上方的5圖元（例如，下拉式方塊）。

- 針對位於控制項左邊的標籤，標籤和輸入控制項之間的最小寬度為10圖元。 應該建立隱含的第二個數據行，以對齊文字方塊、下拉式方塊或其他控制項。

- 標籤是句子大小寫，後面接著冒號。 請參閱[文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。

#### <a name="distance-between-controls"></a>控制項之間的距離
 堆疊控制項相當合理。 堆疊控制項之間的間距沒有絕對的指導方針。 控制項之間的 tightness 可能會稍有不同的對話方塊。 建議的間距是20圖元的垂直控制項/標籤配對，而9圖元適用于水準控制項/標籤配對。 水準配對的最小控制間距為6個圖元。

 ![控制項之間的建議距離](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **圖 08.01-d：控制項之間距離的建議**

#### <a name="control-indentation"></a>控制項縮排
 當控制項已嵌套時，會以上面控制項的左邊緣水準對齊內部控制項，通常是標籤。

 ![嵌套控制項對齊](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **圖 08.01-e：嵌套控制項對齊**

#### <a name="control-width"></a>控制寬度
 文字方塊或其他類似控制項的寬度不應超過欄位的平均輸入。 一般的英文字是五個字元。 例如，需要長路徑名稱的文字方塊應該是水準配置所允許的時間，而平臺名稱的下拉式清單應該只是允許最長專案的長度。

#### <a name="helper-text"></a>Helper 文字

- 對話方塊可以顯示協助程式文字，以提供有關對話方塊用途的詳細資訊。 這通常位於最上層，而且可以是1-2 句子。

- 行長度應該是適合使用者進行剖析和讀取的舒適寬度。 「中」對話方塊的寬度不能超過550圖元。

#### <a name="BKMK_InteriorCommandButtons"></a>內部命令按鈕
 在更複雜的對話方塊中，內部控制項可能會有自己的相關按鈕，這可能會影響對話的 [認可] 按鈕所在的位置。

- 當 **[確定]** 時，請使用內部按鈕的垂直對齊（資料行） / [**取消**] 會在右下角水準方向。

- 當 **[確定]** 時，使用內部按鈕的水準對齊（資料列） / [**取消**] 會在右上角垂直方向。 這種情況較不常見。

- 內部按鈕大小應以75x23 圖元的標準按鈕大小為目標，盡可能符合 **[確定] / [** **取消**] 按鈕的大小。 如果按鈕標籤讓按鈕超過標準按鈕的大小，則該集合中的其他按鈕應該會對齊該較寬的大小。

  ![水準 [確定] 和 [取消] 按鈕](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **圖 08.01-f：具有水準 [確定]/[取消] 的垂直內部按鈕**

  ![垂直 [確定] 和 [取消] 按鈕](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **圖 08.01-g：具有垂直 [確定]/[取消] 的水準內部按鈕**

#### <a name="browse-button"></a>[流覽 ...]button
 **[流覽 ...]** 緊接在文字方塊後面的按鈕應該拼出「流覽 ...」完整，包括省略號。 如果空間已緊密型，或螢幕上有多個 **[流覽 ...]** 按鈕，則按鈕可以縮小為省略號。

## <a name="BKMK_ThemedDialogLayout"></a>主題對話版面配置
 Visual Studio 中的主題對話方塊具有較淡的外觀，並提供更多空白字元。 印刷樣式提供更多的強調和感，提供更多開放的行距和字型大小和加權的變化。 可能的話，已減少或移除 chrome 和標題列。 這些對話的版面配置應該遵循此基本模式：

1. 對話的背景是白色。

2. 中間值灰色有一個1圖元的規則框線。

3. 對話方塊標題不再位於標題列中，但會以較大的點大小提供視覺效果和強調。 （請參閱[文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)中的字型大小一節）。

4. 加上其他文字的標籤（例如描述）應為**環境字型 + 粗體**。

5. 內部資料行是以淺灰色的1圖元規則分隔。

6. 預設連結沒有底線。 暫留和按下狀態具有色彩變更加底線。

7. [認可] 按鈕（如 **[確定]** / [**取消**]）位於右下角。

### <a name="themed-dialog-layout-examples"></a>主題對話版面配置範例
 ![主題對話版面配置](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **圖 08.01-h：主題對話方塊**

 ![主題對話方塊維度](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **圖 08.01-i：主題對話方塊-維度**

 ![主題對話方塊字型](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **圖 08.01-j：主題對話方塊-字型**

 ![主題對話方塊色彩](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **圖 08.01-k：主題對話方塊-色彩**

## <a name="see-also"></a>請參閱
- [適用於 Visual Studio 的應用程式模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [控制項（Windows）](/windows/desktop/uxguide/controls)
- [對話方塊（Windows）](/windows/desktop/uxguide/win-dialog-box)