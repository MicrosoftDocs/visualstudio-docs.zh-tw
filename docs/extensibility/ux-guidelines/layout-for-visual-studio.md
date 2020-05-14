---
title: 視覺工作室的佈局 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698399"
---
# <a name="layout-for-visual-studio"></a>適用於 Visual Studio 的配置
大多數可視化工作室對話框是[實用程式對話框佈局](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout),這是遵循標準[Windows 桌面對話框佈局原則](/windows/desktop/uxguide/win-dialog-box)的無主題對話方塊。 當 Visual Studio 開始刷新其 UI 時,一些比較突出的對話方塊具有新的設計,可將其確立為產品定義體驗。 這些[主題對話框佈局](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout)具有主題外觀。

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a>實用程式對話框佈局

- 實用程式對話框中的所有控制項都應從頂部 / 左側開始並向動。

- 切勿將控件居中以填充大面積。

- 對所有對話框文字使用環境字型。 編寫可視化規範時,請指定環境字型,而不是選擇特定的字體和大小。 請參考[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

- 使用一致的控制間距和放置來支援工藝質量的目標。

- 從大量控件、控件的唯一並列或兩者同時,對話框可能會變得更加複雜。 對於這些複雜情況,在控制分組之間留出足夠的空間,為使用者提供要分析的邏輯流。

### <a name="utility-dialog-layout-examples"></a>實用程式對話框配置範例
 所有尺寸均以圖元表示。

 ![控制項上方之標籤的對話方塊間距](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **圖 08.01-a:具有上方控制式標籤的實用程式對話框的間距指南**

 ![控制項左側之標籤的對話方塊間距](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **圖 08.01-b:控制項左側帶有標籤的實用程式對話框間距指南**

### <a name="layout-details"></a>佈局詳細資訊

#### <a name="margins"></a>邊界

- 所有對話框都應在所有邊上具有 12 像素的邊框。

- 組幀中的邊距應為距幀邊緣的 9 圖元。

- 選項卡控制項中的邊距應為距選項卡控制項邊緣的 6 圖元。

#### <a name="command-buttons"></a>命令按鈕

- 命令按鈕在對話框框架上操作,而不是在內容上操作。 它們應放置在右下角,並且應具有足夠的可變空間,以便將按鈕設置為明顯分開。

- 如果對話框中存在操作的水準按鈕,則備用命令按鈕配置是右上角的垂直堆疊。 請參考下一個下面的[內部命令按鈕](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons)。

- 命令按鈕左側的空間(對話框的左下/居中)被視為對話方塊操作控制件「波段」的一部分。 唯一應該侵入該空間的是與整個任務或對話框相關的幫助連結。

- 命令按鈕應為 75x23 圖元。

- 命令按鈕應相距 6 圖元。

  ![基本按鈕對齊方式](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **圖 08.01-c:基本按鈕對齊**

#### <a name="labels"></a>標籤

- 左對齊所有標籤。

- 對於控件上方的標籤,它們應與控件下方的控制元件精確對齊,標籤底部應高於其他控制項頂部 5 圖元(例如,組合框)。

- 對於位於控制項左側的標籤,標籤和輸入控制項之間的最小寬度為10圖元。 應建立用於對齊文本框、組合框或其他控件的隱含第二列。

- 標籤是句子大小寫,後跟冒號。 請參考[文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。

#### <a name="distance-between-controls"></a>控制項之間的距離
 堆疊控件合理。 堆疊控件之間的間距沒有絕對準則。 控件之間的緊密性可能因對話框而異。 垂直控制/標籤對的建議間距為 20 像素,水準控制/標籤對為 9 圖元。 水準對的最小控制間距為 6 圖元。

 ![控制項的建議間距](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **圖 08.01-d:控制項之間的距離建議**

#### <a name="control-indentation"></a>控制縮排
 嵌套控制項時,將內部控制元件與上面控制元件的左邊緣(通常是標籤)水準對齊。

 ![巢狀控制項對齊方式](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **圖 08.01-e:嵌套控制對齊**

#### <a name="control-width"></a>控制寬度
 文本框或其他類似控件的寬度不應超過欄位的平均輸入。 平均英語單詞是五個字元。 例如,需要長路徑名稱的文本框應為水平佈局允許的時間,而平臺名稱的下拉清單應僅應為允許最長條目的長度。

#### <a name="helper-text"></a>說明者文字

- 對話框可以顯示幫助器文本,該文本提供有關對話方塊用途的詳細資訊。 這通常位於頂部,可以是 1-2 個句子。

- 線長應為使用者解析和讀取的舒適寬度。 中等對話框的寬度不應超過 550 圖元。

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a>內部指令按鈕
 在更複雜的對話框中,內部控制可能具有其自己的相關按鈕,這可能會影響對話方塊的提交按鈕的位置。

- 當 **「確定**/**取消」** 在右下角水準方向時,使用內部按鈕的垂直對齊(列)。

- 當 **「確定**/**取消」** 在右上角垂直定向時,使用內部按鈕的水準對齊(行)。 這種情況不太常見。

- 內部按鈕大小應針對 75x23 像素的標準按鈕大小,盡可能匹配**OK**/**取消**按鈕的大小。 如果按鈕標籤使按鈕超過標準按鈕大小,則該集中的其他按鈕應與該較寬的大小對齊。

  ![水平並排 [確定] 和 [取消] 按鈕](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **圖 08.01-f:具有水準 OK/取消的垂直內部按鈕**

  ![垂直並排 [確定] 和 [取消] 按鈕](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **圖 08.01-g:具有垂直 OK/取消水平內部按鈕**

#### <a name="browse-button"></a>[流覽...]按鈕
 **[流覽...]** 文本框後按鈕應拼寫出"流覽..."完整,包括省略號。 如果空間很緊或螢幕上有多個 **[Browse...]** 按鈕,則可以將按鈕減少到僅省略號。

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a>主題對話框佈局
 Visual Studio 中的主題對話框外觀更輕,並提供更多的空白。 排版提供了更多的強調和興趣,提供了更多的開放線間距和字體大小和權重的變化。 在可能的情況下,鉻和標題條已減少或刪除。 這些對話框的佈局應遵循以下基本模式:

1. 對話框的背景為白色。

2. 中間值灰色中有一個 1 像素規則邊框。

3. 對話框標題不再位於標題列中,而是以較大的點大小提供視覺興趣和強調。 (請參閱[文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)中的字體大小部分。

4. 與附加文字(如說明)加上的標籤應為 **「環境」字型 = 粗體**。

5. 內部列由淺灰色 1 像素規則分隔。

6. 默認連結沒有下劃線。 懸停和按下狀態的顏色變化加下劃線。

7. 提交按鈕(如**OK**/**取消**)位於右下角。

### <a name="themed-dialog-layout-examples"></a>主題對話框佈局範例
 ![佈景主題對話方塊版面配置](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **圖 08.01-h:主題對話框**

 ![佈景主題對話方塊維度](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **圖 08.01-i:主題對話框 - 尺寸**

 ![佈景主題對話方塊字型](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **圖 08.01-j:主題對話框 - 字型**

 ![佈景主題對話方塊色彩](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **圖 08.01-k:主題對話框 - 顏色**

## <a name="see-also"></a>另請參閱
- [適用於 Visual Studio 的應用程式模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [控制項(視窗)](/windows/desktop/uxguide/controls)
- [對話框(視窗)](/windows/desktop/uxguide/win-dialog-box)
