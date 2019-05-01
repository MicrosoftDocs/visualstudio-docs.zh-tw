---
title: 適用於 Visual Studio 的版面配置 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e35cb321772354de29b7b8466b6136c96cabf98d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62798593"
---
# <a name="layout-for-visual-studio"></a>適用於 Visual Studio 的版面配置
就大部分的 Visual Studio 對話方塊[公用程式對話方塊版面配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)，這是 unthemed 對話方塊該遵循標準[Windows Desktop 對話方塊版面配置原則](/windows/desktop/uxguide/win-dialog-box)。 如 Visual Studio 會移到重新整理其 UI 中，一些更重要的對話方塊會有新的設計可建立它們，產品定義的體驗。 這些[佈景主題對話方塊版面配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout)具有佈景主題的外觀。

## <a name="BKMK_UtilityDialogLayout"></a> 公用程式的對話方塊版面配置

- 公用程式 對話方塊中的所有控制項應該在左上方開始，並往下流動。

- 在對話方塊中，以填滿大型區域上的可用空間永遠不會 center 控制項。

- 使用環境字型的對話方塊中的所有文字。 在撰寫 visual 規格時，指定環境字型，而不是選取特定字型和大小。 請參閱[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

- 使用一致的控制項的間距和位置來支援目標中而成的品質。

- 對話方塊會變得更複雜從較大量的控制項、 控制項、 唯一 juxtaposition 或兩者。 這些複雜的情況下，可讓控制項群組，讓使用者能夠剖析的邏輯流程之間有足夠的空間。

### <a name="utility-dialog-layout-examples"></a>公用程式的對話方塊版面配置範例
 所有維度是以像素為單位都表示。

 ![控制項上方之標籤的對話方塊間距](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 a_UtilitySpacingAbove")

 **圖 08.01 a:間距的指導方針與上方控制項標籤的公用程式對話方塊**

 ![控制項左側之標籤的對話方塊間距](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 b_UtilitySpacingLeft")

 **圖 08.01 b:間距的指導方針與控制項的左邊的標籤的公用程式對話方塊**

### <a name="layout-details"></a>版面配置詳細資料

#### <a name="margins"></a>邊界

- 所有對話都應該都有 12 個像素框線所有邊緣。

- 邊界群組範圍內應該是 9 個像素框架的邊緣。

- 邊界內的索引標籤控制項應該是 6 個索引標籤控制項的邊緣像素。

#### <a name="command-buttons"></a>命令按鈕

- 命令按鈕處理對話方塊外框，不是在內容上。 它們應該放在底部右側，而且應該足夠上述設定按鈕完全不同的變數空間。

- 操作 對話方塊中的水平按鈕時，替代命令按鈕設定就會是垂直的堆疊，右上方。 請參閱[內部的命令按鈕](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons)如下。

- 左邊的 [命令] 按鈕 （低/左中對話方塊的） 空間被視為 「 矩形 」 作業的對話方塊控制項的一部分。 應該會打擾到該空間的唯一項目是與整體的工作或對話方塊的說明連結。

- 命令按鈕應該是 75 x 23 像素為單位。

- 命令按鈕應該是分開的 6 個像素。

  ![基本按鈕對齊](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 c_ButtonAlign")

  **圖 08.01 c:基本按鈕對齊方式**

#### <a name="labels"></a>標籤

- 靠左對齊所有標籤。

- 標籤位於控制項上方，它們應該靠左對齊精確地具有其下的控制項，而且標籤的底部應該高於其他控制項 （例如，下拉式方塊） 的頂端的 5 個像素。

- 對於位於左側的控制項的標籤，標籤和輸入的控制項之間的最小寬度會是 10 個像素。 對齊文字方塊、 下拉式方塊或其他控制項，您應該建立隱含的第二個資料行。

- 標籤是句首大寫，後面接著冒號。 請參閱[文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。

#### <a name="distance-between-controls"></a>控制項之間的距離
 合理堆疊控制項。 沒有任何絕對的指導方針堆疊控制項之間的間距。 在控制項之間 tightness 會有些許之間對話。 20 個像素垂直的控制項/標籤配對，而 9 個像素水平控制項/標籤配對的建議的間距。 用於水平的括號的最小的控制項間距為 6 的像素。

 ![建議的控制項之間的距離](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 d_ControlDistance")

 **圖 08.01-d:控制項之間的距離的建議**

#### <a name="control-indentation"></a>控制縮排
 時為巢狀控制項，將內部的控制項，與上述，控制項通常標籤左邊緣的水平對齊。

 ![巢狀控制項對齊](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 e_ControlAlign")

 **圖 08.01-e:巢狀的控制項對齊方式**

#### <a name="control-width"></a>控制項寬度
 應該不超過欄位的平均輸入文字方塊或其他類似的控制項的寬度。 平均的英文斷是五個字元。 例如，需要長路徑名稱的文字方塊中應該只要允許水平版面配置，而下拉式清單中，平台名稱應該只被允許的最長的項目長度。

#### <a name="helper-text"></a>Helper 文字

- 一個對話方塊，可以顯示提供的對話方塊用途的詳細資訊的協助程式文字。 這通常位於頂端，並可以是 1 至 2 個句子。

- 行長度應該是剖析，並讀取使用者的舒適寬度。 中型對話方塊應該不超過 550 像素寬。

#### <a name="BKMK_InteriorCommandButtons"></a> 內部命令按鈕
 在更複雜的對話方塊中，內部的控制項可能有它自己相關的按鈕，這可能會影響對話方塊的 [認可] 按鈕的所在位置。

- 使用內部的垂直對齊方式 （資料行） 按鈕 **[確定]**/**取消**為水平導向在右下角。

- 使用內部的水平對齊方式 （資料列） 按鈕 **[確定]**/**取消**為垂直導向右上角。 這種情況下是較不常見。

- 內部的按鈕大小應為目標的標準按鈕大小為 75 x 23 像素，比對的大小 **[確定]**/**取消**盡可能的按鈕。 當按鈕的標籤會超出標準按鈕大小的按鈕時，該集合中的其他按鈕應該配合該寬度的大小。

  ![水平的 [確定] 和 [取消] 按鈕](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 f_HorizOKCan")

  **圖 08.01-f:垂直內部水平的 確定 / 取消 按鈕**

  ![垂直的 [確定] 和 [取消] 按鈕](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 g_VertOKCan")

  **圖 08.01-g:水平與垂直確定/取消的內部按鈕**

#### <a name="browse-button"></a>[瀏覽...]按鈕
 **[瀏覽...]** 遵循文字方塊中的按鈕應該拼出 [瀏覽...]完整，包括 [省略符號。 如果有緊密的空間，或有多個 **[瀏覽...]** 在畫面上，按鈕的按鈕可縮減為的省略符號。

## <a name="BKMK_ThemedDialogLayout"></a> 佈景主題對話方塊版面配置
 在 Visual Studio 中的佈景主題對話方塊具有較淺的外觀，並提供更多的泛空白字元。 印刷樣式會提供更多的強調和感興趣，提供更開放的行距和各式各樣的字型大小和權數。 可能的話，chrome 和標題列已降低或移除。 這些對話方塊的配置都應該遵循這個基本模式：

1. 對話方塊的背景是白色。

2. 以中間值灰色沒有規則 1 像素框線。

3. 對話方塊標題不再位於標題列，但提供視覺趣味與較大的點。 (請參閱中的字型的大小一節[文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。)

4. 加上額外的文字，例如描述、 標籤應**環境字型 + 粗體**。

5. 淺灰色的 1 像素規則，以分隔內部的資料行。

6. 預設的連結已經沒有底線。 暫留和已按下的狀態有變更色彩再加上底線。

7. 認可按鈕 (類似 **[確定]**/**取消**) 位在右上角。

### <a name="themed-dialog-layout-examples"></a>佈景主題對話方塊版面配置範例
 ![佈景主題對話方塊版面配置](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 h_ThemedDialog")

 **圖 08.01-h:佈景主題對話方塊**

 ![佈景主題對話方塊維度](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 i_ThemedDialogDimensions")

 **圖 08.01-i:佈景主題對話方塊-維度**

 ![佈景主題對話方塊字型](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 j_ThemedDialogFonts")

 **圖 08.01 j:佈景主題對話方塊-字型**

 ![佈景主題對話方塊色彩](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 k_ThemedDialogColors")

 **圖 08.01-k:佈景主題對話方塊-色彩**

## <a name="see-also"></a>另請參閱
- [適用於 Visual Studio 的應用程式模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [控制項 (Windows)](/windows/desktop/uxguide/controls)
- [對話方塊 (Windows)](/windows/desktop/uxguide/win-dialog-box)