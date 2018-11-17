---
title: 適用於 Visual Studio 的 UX 基本 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7c9c2fe1c076a8851b1b95a9957cd721c61ae21
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799492"
---
# <a name="ux-essentials-for-visual-studio"></a>適用於 Visual Studio 的 UX 基本
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>最佳作法  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1.是 Visual Studio 環境內保持一致。  
  
-   請遵循在殼層中的現有互動模式。  
  
-   設計與命令介面的視覺化語言和技術需求一致的功能。  
  
-   當其存在時，請使用共用的命令和控制項。  
  
-   了解 Visual Studio 階層架構，以及如何建立內容及磁碟機 UI。  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2.使用環境服務的字型和色彩。  
  
-   UI 應該採用目前的環境字型設定，除非它公開在 [選項] 對話方塊中的 [字型和色彩] 頁面的自訂。  
  
-   UI 項目必須使用 VSColor Service，使用共用的環境權杖或功能的特定權杖。  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3.使所有圖像和新的 VS 樣式一致。  
  
-   請遵循 Visual Studio 圖示、 圖像 （glyph） 和其他圖形的設計原則。  
  
-   圖形元素括住文字。  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4.以使用者為中心的觀點來設計。  
  
-   建立工作流程之前在其中的個別功能。  
  
-   熟悉您的使用者，並將該知識明確在您的規格中。  
  
-   檢閱 UI 時, 評估完整的體驗，以及詳細資料。  
  
-   設計您的 UI，讓它會維持運作且吸引人，不論地區設定或語言。  
  
## <a name="screen-resolution"></a>螢幕解析度  
  
### <a name="minimum-resolution"></a>最低解析度  
 Visual Studio Dev14 的最小解析度是 1280 x 1024。 這表示它是*可能*雖然它可能不是理想的使用者經驗，使用 Visual Studio 這個解析度。 沒有保證所有層面，都是可在低於 1280 x 1024 的解析度。  
  
 初始的對話方塊大小不應超過 1000年個像素的高度，以便容納在 IDE 內此最小的解析度 96 dpi 的範圍內。  
  
### <a name="high-density-displays"></a>高密度的顯示  
 Visual Studio 中的 UI 必須適用於所有的 DPI 縮放比例，Windows 支援現成的因素： 150%、 200%和 250%。  
  
## <a name="anti-patterns"></a>反向模式  
 Visual Studio 包含許多 UI 的範例，請遵循我們的指導方針和最佳作法。 為了保持一致，開發人員通常借用類似於他們要建置的產品的 UI 設計模式。 雖然這是個不錯的方法，幫助我們磁碟機中使用者互動和視覺效果設計的一致性，那就是執行在某些情況下不符合我們的指導方針，因為排程條件約束或脫離優先處理的一些詳細的功能。 在這些情況下，我們不想複製其中一種 「 反模式 」 小組因為他們不斷增加 Visual Studio 環境內的不正確或不一致的 UI。  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>必要的欄位/設定預設顯示處於錯誤狀態  
  
#### <a name="feature-team-goals"></a>功能小組目標  
  
-   警告使用者他們已必須設定的項目。  
  
-   繪製區域需要輸入使用者的注意力。  
  
#### <a name="anti-pattern-solution"></a>反向模式解決方案  
 只要使用者已起始動作，並已完成工作之前，立即將放在重大中斷圖示旁邊需要設定的領域。  
  
#### <a name="example-manifest-designer-declarations"></a>範例： 資訊清單設計工具的宣告  
 立即加入至清單的宣告會處於錯誤狀態，它會保存，直到該使用者需設定必要的屬性。  
  
 在此情況下，會額外的考量，因為用於警示的圖示會包含一個"x"，因此一般移除無法使用圖示旁邊。 如此一來，UI 會使用移除 按鈕，更笨拙的控制項。  
  
 ![資訊清單設計工具錯誤宣告反&#45;模式](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti 模式")  
  
 **將 UI 放在錯誤狀態中，依預設是 Visual Studio 反模式。**  
  
#### <a name="alternatives"></a>替代項目  
 此問題較理想的方案，是將：  
  
-   允許使用者新增的宣告，而不發出警告，然後再移至項目上設定屬性的 立即。  
  
-   新增警告圖示 （金級三角形） 時焦點從移動項目，例如將另一個宣告新增至清單，或嘗試變更索引標籤的設計工具內。  
  
-   如果使用者嘗試變更索引標籤設定屬性的任何宣告之前，快顯對話方塊，說明不會建置應用程式 （或任何影響） 的警告，在解決之前。 如果使用者關閉對話方塊，並將索引標籤變更仍然後圖示 （重要或警告，視需要） 會新增至宣告 索引標籤。  
  
### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>強制使用者先關閉 UI 讀取文字  
  
#### <a name="feature-team-goals"></a>功能小組目標  
 不允許使用者關閉 UI，而不會第一個看到的說明文字。  
  
#### <a name="anti-pattern"></a>反向模式  
 決定針對 X 的常見的模式與 UI 內的不同位置中插入視訊的連結，小組會關閉 UX，所指定的按鈕和工具提示說明，並改為實作的下拉式清單和 「 不要再顯示 連結。  
  
 ![說明文字反&#45;模式&#45;不正確](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")  
  
 **不正確： 強制使用者讀取的說明文字之前關閉 UI 是在 Visual Studio 中的反模式。**  
  
#### <a name="result"></a>結果  
 而不是簡單關閉按鈕 （按一下），強制使用者只需關閉視訊的連結會出現在每個位置中的 UI 使用點選兩次。  
  
#### <a name="alternatives"></a>替代項目  
 這種情況下正確的設計會遵循一般模式 Internet Explorer、 Office 和 Visual Studio： 暫留時，使用者可以看到工具提示描述，並按一下隱藏 UI。  
  
 ![說明文字反&#45;模式&#45;正確](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti 模式更正")  
  
 **正確： 視訊連結依照設計，應該暫留時即會顯示工具提示的其他資訊，並按一下 [X] 應該關閉訊息而不需要進一步的互動。**  
  
### <a name="using-command-bars-for-settings"></a>使用命令列進行設定  
 ![反的命令列&#45;模式&#45;圖 A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-模式-FigureA")  
  
 **圖 A:JSON 命令列反面模式**  
  
 **圖 A**代表此反模式： 將設定套用至不只是命令的命令按鈕下方。 此草圖，在中，有除了開始偵錯的命令 — 例如瀏覽器、 啟動但不偵錯，以及逐步執行中的檢視 — 會遵守所選的設定。  
  
 ![反的命令列&#45;模式&#45;圖 B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-模式-FigureB")  
  
 **圖 b： 更好，但仍命令列反面模式**  
  
 稍微更好，但仍不會讓這種設定工具列中，在中所示**圖 B**。分割按鈕花較少的空間，因此改進透過下拉式清單，而這兩個設計仍在使用工具列來升級的不是命令的項目。  
  
 ![反的命令列&#45;模式&#45;圖 C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-模式-FigureC")  
  
 **圖 c： 正確使用 Visual Studio 命令列模式**  
  
 在  **圖 C**，此設定會繫結至一系列的命令。 沒有設定任何全域設定，我們只四個命令之間切換。 這是唯一在工具列中的命令可接受的情況。  
  
### <a name="control-anti-patterns"></a>控制項反向模式  
 某些反向模式只是不正確的使用方式的控制項或控制項群組的呈現方式。  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>加上底線做為群組標籤，而不是超連結  
 加上底線的文字應該只用於超連結。  
  
 **錯誤：**  
  
 ![加上底線反&#45;群組標籤中的模式](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102 g_GroupLabelIncorrect")  
  
 **加底線的文字不是超連結是 Visual Studio 反模式。**  
  
 **良好：**  
  
 ![加上底線反&#45;群組標籤中的模式&#40;正確&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102 h_GroupLabelCorrect")  
  
 **正確地套用樣式，非超連結文字會顯示未修飾環境字型。**  
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>按一下核取方塊會導致快顯的對話方塊  
 立即按一下 [啟用所有角色的遠端桌面] 核取方塊，在 「 發行 Windows Azure 應用程式 」 精靈會顯示快顯對話方塊中，Visual Studio 的反向模式。 此外，核取方塊欄位不會填入此核取方塊之後被選取，另一種互動反模式。  
  
 ![核取方塊快顯&#45;最新的反&#45;模式](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102 i_CheckboxPopup")  
  
 **按下核取方塊就是 Visual Studio 的反向模式之後，請將對話方塊。**  
  
### <a name="hyperlink-anti-patterns"></a>超連結反向模式  
 下列範例包含兩個反向模式。  
  
1. 暫留時開啟紅色前景表示未使用正確的共用的色彩從字型服務。  
  
2. 「 了解更多 」 不是適當的文字，概念性主題的連結。 使用者的目標不是為了深入了解它是了解他們所選擇的後果。  
  
   ![反的超連結&#45;模式](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")  
  
   **忽略色彩服務，並使用 「 了解更多 」 超連結是 Visual Studio 的反向模式。**  
  
   **更好的解決方案：** 造成按的連結，會詢問使用者問題。  
  
-   Windows Azure 服務如何運作？  
  
-   何時需要 Windows Azure 行動服務專案？  
  
#### <a name="using-click-here-for-links"></a>使用 「 按一下這裡 」 的連結  
 超連結應該自述性。 它會使用反模式，可使用 「 按一下這裡 」 或任何類似的變體。  
  
 **錯誤：** 「 按一下這裡的指示來建立新的專案。 」  
  
 **良好：** 「 如何建立新的專案？ 」

