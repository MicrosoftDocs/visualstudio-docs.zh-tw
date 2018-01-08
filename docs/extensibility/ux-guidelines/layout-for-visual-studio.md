---
title: "適用於 Visual Studio 的版面配置 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ef3c590a82fc3a7b89d21684ffe2e4b0f216ca98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="layout-for-visual-studio"></a>適用於 Visual Studio 的版面配置
Visual Studio 對話方塊多數[公用程式對話方塊版面配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)，這是 unthemed 對話遵循標準[Windows 桌面對話方塊版面配置原則](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)。 隨著 Visual Studio 會移到重新整理其 UI，一些更重要的對話方塊會有新的設計，以建立它們，產品定義體驗。 這些[佈景主題對話方塊版面配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout)具有佈景主題的外觀。  
  
##  <a name="BKMK_UtilityDialogLayout"></a>公用程式的對話方塊版面配置  
  
-   公用程式 對話方塊中的所有控制項應該在左上角中啟動，並向下傳送。  
  
-   對話方塊，以填滿大型區域上的可用空間從未 center 控制項。  
  
-   使用環境字型的所有對話方塊文字。 在撰寫視覺化規格時，指定環境字型，而不是選取特定的字型和大小。 請參閱[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。  
  
-   使用一致的控制項間距和位置來支援目標中而成的品質。  
  
-   對話方塊會變得更複雜從大量的控制項、 唯一 juxtaposition 的控制項，或兩者。 這些複雜的情況下，可讓控制項群組，以剖析的邏輯流程授與使用者之間有足夠的空間。  
  
### <a name="utility-dialog-layout-examples"></a>公用程式的對話方塊版面配置範例  
 所有維度會以像素為單位都表示。  
  
 ![控制項上方之標籤的對話方塊間距](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 a_UtilitySpacingAbove")  
  
 **圖 08.01 a： 間距的指導方針與標籤控制項上方的公用程式對話方塊**  
  
 ![控制項左側之標籤的對話方塊間距](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 b_UtilitySpacingLeft")  
  
 **圖 08.01 b 間距的指導方針的控制項左邊的標籤與公用程式對話方塊**  
  
### <a name="layout-details"></a>版面配置詳細資料  
  
#### <a name="margins"></a>邊界  
  
-   所有對話都應該都有 12 個像素框線所有邊緣。  
  
-   在群組內的邊界都應該是 9 個像素框架的邊緣。  
  
-   索引標籤控制項中的邊界應該從索引標籤控制項的邊緣 6 個像素。  
  
#### <a name="command-buttons"></a>命令按鈕  
  
-   命令按鈕對框架對話方塊中，不在內容上進行操作。 它們應該放在下方正確，且必須有足夠變數空間上述設定絕對各自獨立的按鈕。  
  
-   有幾個操作的對話方塊內的水平按鈕，替代命令按鈕設定在右上方的垂直堆疊。 請參閱[內部命令按鈕](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons)下方。  
  
-   左邊的 [命令] 按鈕 （下方左/對話方塊的中央） 空間被視為 「 矩形 」 的作業對話方塊控制項的一部分。 唯一應該擅自在該空間的是與整體的工作或對話方塊的說明連結。  
  
-   命令按鈕應該是 75 x 23 像素為單位。  
  
-   命令按鈕應該位於 6 個像素。  
  
 ![基本按鈕對齊](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 c_ButtonAlign")  
  
 **圖 08.01 c： 基本按鈕對齊方式**  
  
#### <a name="labels"></a>標籤  
  
-   靠左對齊所有標籤。  
  
-   之標籤的控制項上方的位置，它們應該靠左對齊精確地具有其下的控制項和標籤的底部應高於其他控制項 （例如，下拉式方塊） 的前 5 個像素。  
  
-   對於坐控制項左邊的標籤，標籤和輸入的控制項之間的最小寬度為 10 個像素。 您應該建立隱含的第二個資料行，來對齊文字方塊、 下拉式方塊或其他控制項。  
  
-   標籤會句子大小寫，後面接著冒號。 請參閱[文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。  
  
#### <a name="distance-between-controls"></a>控制項之間的距離  
 合理堆疊控制項。 沒有任何絕對導線堆疊控制項之間的間距。 控制項之間 tightness 對話方塊之間可能會稍微不同。 20 像素垂直控制項/標籤配對，而 9 個像素水平控制項/標籤配對的建議的間距。 水平組的最小控制項間距是 6 個像素。  
  
 ![建議控制項之間的距離](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 d_ControlDistance")  
  
 **圖 08.01 d： 建議控制項之間的距離**  
  
#### <a name="control-indentation"></a>控制縮排  
 時為巢狀控制項，將內部的控制項，與上述，控制項通常標籤左邊緣的水平對齊。  
  
 ![巢狀控制項對齊效果](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 e_ControlAlign")  
  
 **圖 08.01 e： 巢狀控制項對齊效果**  
  
#### <a name="control-width"></a>控制項寬度  
 應該不能超過欄位的平均輸入文字方塊或其他類似之控制項的寬度。 平均的英文字組是五個字元。 例如，需要冗長的路徑名稱的文字方塊中應該只要允許水平配置，而下拉式清單中，平台名稱應該只被允許的最長的項目長度。  
  
#### <a name="helper-text"></a>Helper 文字  
  
-   一個對話方塊，可以顯示 helper 文字提供之對話方塊的用途相關的詳細資訊。 這通常位於頂端，並可以是 1-2 的句子。  
  
-   行的長度必須是剖析，並讀取使用者的舒適的寬度。 中度對話方塊應該超過 550 像素寬。  
  
####  <a name="BKMK_InteriorCommandButtons"></a>內部的命令按鈕  
 在更複雜的對話，內部的控制項可能有它自己相關的按鈕，可能會影響對話方塊的 [認可] 按鈕位於何處。  
  
-   使用內部的垂直對齊方式 （資料行） 的按鈕時**確定**/**取消**在右下角的水平方向。  
  
-   使用內部水平對齊方式 （資料列） 的按鈕時**確定**/**取消**右上角的垂直方向。 這種情況下會較不常見。  
  
-   內部的按鈕大小應將目標設為 75 x 23 像素，比對的大小的標準按鈕大小**確定**/**取消**盡可能的按鈕。 當按鈕標籤會超出標準按鈕大小的按鈕時，該集合中的其他按鈕應符合的該較寬的大小。  
  
 ![水平的 [確定] 和 [取消] 5d; 按鈕](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 f_HorizOKCan")  
  
 **圖 08.01 f： 垂直內部水平的 [確定] / [取消] 按鈕**  
  
 ![垂直的 [確定] 和 [取消] 5d; 按鈕](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 g_VertOKCan")  
  
 **圖 08.01 g： 水平內部的按鈕以垂直的 [確定] / [取消]**  
  
#### <a name="browse-button"></a>[瀏覽...]按鈕  
 **[瀏覽...]**依照文字方塊中的按鈕應該完整拼法 [瀏覽] 以完整模式，包括省略符號。 如果空間緊密，或有多個**[瀏覽...]**在畫面中，按鈕的按鈕可縮減為的省略符號。  
  
##  <a name="BKMK_ThemedDialogLayout"></a>佈景主題對話方塊版面配置  
 在 Visual Studio 佈景主題對話方塊具有較淡的外觀，並提供更多的泛空白字元。 印刷樣式提供強調越來越感興趣，提供更開啟行距和各式各樣的字型大小和加權。 如果可行，chrome 和標題列已減少或移除。 這些對話方塊的版面配置應該遵循這個基本模式：  
  
1.  對話方塊的背景是白色。  
  
2.  以中間值灰色沒有規則 1 像素框線。  
  
3.  不再對話方塊的標題位於標題列，但提供視覺效果和加強語氣，較大的點。 (請參閱中的字型大小一節[文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。)  
  
4.  應搭配其他的文字，例如描述、 標籤**環境字型 + 粗體**。  
  
5.  淺灰色的 1 像素規則，以分隔內部的資料行。  
  
6.  預設的連結會有沒有底線。 暫留 」 和 「 已按下的狀態有變更色彩再加上底線。  
  
7.  認可按鈕 (例如**確定**/**取消**) 在右下角。  
  
### <a name="themed-dialog-layout-examples"></a>佈景主題對話方塊版面配置範例  
 ![佈景主題對話方塊版面配置](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 h_ThemedDialog")  
  
 **圖 08.01 h:%m 佈景主題對話方塊**  
  
 ![佈景主題對話方塊維度](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 i_ThemedDialogDimensions")  
  
 **圖 08.01-i： 佈景主題對話方塊維度**  
  
 ![佈景主題對話方塊字型](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 j_ThemedDialogFonts")  
  
 **圖 08.01 j： 佈景主題對話方塊字型**  
  
 ![佈景主題對話方塊色彩](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 k_ThemedDialogColors")  
  
 **圖 08.01-k： 佈景主題對話方塊色彩**  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 的應用程式模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [控制項 (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [對話方塊 (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)