---
title: "Visual Studio 的 UX Essentials |Microsoft 文件"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 368540b909536523515ea610e509b22600628f81
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio 的 UX Essentials
## <a name="best-practices"></a>最佳作法  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1.要在 Visual Studio 環境內一致。  
  
-   請遵循現有[互動模式](interaction-patterns-for-visual-studio.md)殼層內。  
  
-   設計功能與介面之視覺化語言一致和[技術需求](evaluation-tools-for-visual-studio.md)。  
  
-   使用共用命令，並控制其存在時。  
  
-   了解 Visual Studio 階層架構以及如何建立內容及磁碟機 UI。  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2.使用環境服務的字型和色彩。  
  
-   UI 應遵守目前[環境字型](fonts-and-formatting-for-visual-studio.md)設定，除非它會顯示在 [選項] 對話方塊中的 [字型和色彩] 頁面可自訂的。  
  
-   UI 項目必須使用[VSColor 服務](colors-and-styling-for-visual-studio.md)，使用共用環境權杖或特定功能的權杖。  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3.讓所有圖像一致的新 VS 樣式。  
  
-   請遵循 Visual Studio 圖示、 圖像 （glyph） 和其他圖形的設計原則。  
  
-   請不要將文字放圖形元素。  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4.設計以使用者為中心的觀點。  
  
-   建立工作流程內的個別功能之前。  
  
-   熟悉您的使用者，並將該知識明確您規格中。  
  
-   如果檢閱 UI 時，都會評估完整的經驗，以及詳細資料。  
  
-   設計您的 UI，讓它仍然功能且吸引人不論地區設定或語言。  
  
## <a name="screen-resolution"></a>螢幕解析度  
  
### <a name="minimum-resolution"></a>最低解析度  
 - Visual Studio Dev14 的最小解析是**1280 x 720**。 這表示它是*可能*解析度，使用 Visual Studio，即使它可能不是最佳的使用者體驗。 並不保證所有層面，將都會使用在賹槲 1280 x 720。  
  
 - Visual Studio 的目標解決方法是**1366x768**。 這是最低的解析度我們保證*良好*使用者經驗。

 - 初始對話方塊高度必須**小於 700 個像素**，因此它能容納的最小解析 IDE 框架 96 dpi。
  
### <a name="high-density-displays"></a>顯示適用之高密度  
 在 Visual Studio 中的 UI 必須作業適用於所有的 DPI 縮放比例 Windows 支援現成的因素： 150%、 200%和 %250。  
  
## <a name="anti-patterns"></a>反向模式  
 Visual Studio 包含許多使用者介面的範例，我們的方針和最佳作法，請依照下列。 為了盡力了一致，開發人員通常借用產品 UI 設計模式類似於它們所建置。 雖然這是一個好的方法，可協助我們磁碟機中與使用者互動和視覺化設計保持一致，我們不要在某些情況下隨附一些不符合我們的指導方針，由於排程條件約束或脫離優先順序的詳細資訊與功能。 在這些情況下，我們不想複製其中一種 「 反面模式 」 的小組因為它們不斷增加的 Visual Studio 環境中不正確或不一致的 UI。  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>必要的欄位/設定預設顯示處於錯誤狀態  
  
#### <a name="feature-team-goals"></a>功能小組目標  
  
-   加入這些項目必須設定的警告使用者。  
  
-   強調的使用者必須輸入的區域。  
  
#### <a name="anti-pattern-solution"></a>反面模式解決方案  
 一旦使用者已起始動作，而且他們已完成工作之前，立即將放在關鍵停止圖示旁邊的需要設定的區域。  
  
#### <a name="example-manifest-designer-declarations"></a>範例： 資訊清單設計工具的宣告  
 立即將宣告新增至清單設定為錯誤狀態，它會保存直到使用者設定必要的屬性。  
  
 在此情況下，沒有額外的考量因為警示使用的圖示會包含"&times;"圖示，因此無法使用一般移除圖示旁邊。 因此，UI 會使用移除 按鈕，更繁重的控制項。  
  
 ![將 UI 放處於錯誤狀態中，依預設是 Visual Studio 的反向模式。] (../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti 模式")<br />將 UI 放處於錯誤狀態中，依預設是 Visual Studio 的反向模式。
  
#### <a name="alternatives"></a>替代項目  
 這個問題比較好的解決方案是：  
  
-   允許使用者新增的宣告，而不發出警告，然後再移至的項目上設定屬性的 立即。  
  
-   新增的警告圖示 （金級三角形） 當焦點從移動項目，例如將另一個宣告新增至清單，或嘗試變更設計工具內的索引標籤。  
  
-   如果使用者嘗試變更索引標籤設定屬性上的任何宣告之前，快顯對話方塊，說明應用程式將不建立 （或任何含意） 之前會解決的警告。 如果使用者關閉對話方塊，並變更索引標籤還是然後圖示 （重大或警告、 視需要） 新增至宣告 索引標籤。  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>若要關閉 UI 點擊多次  
  
#### <a name="feature-team-goals"></a>功能小組目標  
 不允許使用者解除 UI，而不會第一個看到的說明文字。  
  
#### <a name="anti-pattern"></a>反面模式  
 VS UI 內的不同位置中插入視訊連結的小組決定針對常見的模式 」&times;"做為關閉的按鈕和工具提示說明指定 UX，改為實作下拉式清單和 「 不要再顯示 「 連結。  

#### <a name="example-video-links-in-team-explorer"></a>在 Team Explorer 中的範例： 視訊連結
強制使用者讀取之前解除 UI 的說明文字是在 Visual Studio 中的反向模式。 正確地設計、 視訊連結應該會顯示具有其他資訊的工具提示上暫留，然後按一下 「&times;"應該關閉訊息而需要進一步互動。


 ![說明文字反 &#45; 模式 &#45;不正確](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />不正確的視訊連結模式
  
#### <a name="result"></a>結果  
 而不是簡單關閉 按鈕 （按一下），強制使用者只需關閉視訊的連結會出現在每個位置中的 UI 使用兩次按一下。  
  
#### <a name="alternatives"></a>替代項目  
 正確的設計，這種情況下會遵循一般模式 Internet Explorer、 Office 及 Visual Studio： 停留的情況下，使用者可以看到工具提示描述，並按一下隱藏 UI。  
  
 ![說明文字反 &#45; 模式 &#45;正確](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti 模式更正")<br />正確的視訊連結模式
  
### <a name="using-command-bars-for-settings"></a>使用命令列設定  
 **圖 A**代表此反面模式： 放以外的更多的命令適用於命令按鈕下方的設定。 在此草圖，有命令除了開始偵錯 — 想檢視在瀏覽器、 啟動但不偵錯，以及逐步執行 —，會使用選取的設定。  

  ![圖 a： 命令列反面模式](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-模式-FigureA")<br />圖 a： 命令列反面模式
  
 稍微好一點，但仍然不置於設定此類型的工具列中所示**圖 B**。分割按鈕花較少的空間，因此改進透過下拉式清單，而這兩種設計仍在使用工具列來升級項目並非真正的命令。  
 
 ![圖 b： 愈好，但仍命令列反面模式](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-模式-FigureB")<br />圖 b： 更好，但仍命令列反面模式
 
  中所示的正確方法**圖 C**，此設定會繫結到一系列的命令。 沒有要設定全域設定，我們只四個命令之間切換。 這是唯一的工具列中的命令可接受的情況。 

 ![圖 c： 更正使用 Visual Studio 命令列模式](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-模式-FigureC")<br />圖 c： 正確使用 Visual Studio 命令列模式
   
### <a name="control-anti-patterns"></a>控制項的反向模式  
 某些反向模式為使用方式不只是正確或呈現的控制項或群組的控制項。  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>使用做為群組標籤，而非超連結加上底線  
 加上底線的文字應該只用於超連結。  
  
 **錯誤：**    
 ![不是超連結的底線的文字是 Visual Studio 的反向模式。] (../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")<br />不是超連結的底線的文字是 Visual Studio 的反向模式。
  
 **良好：**   
 ![正確地套用樣式，非超連結文字會顯示原始環境字型。] (../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")<br />正確地套用樣式，非超連結文字會顯示原始環境字型。
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>按一下核取方塊會導致快顯對話方塊  
 立即按一下 啟用所有角色的遠端桌面 核取方塊，在 發行 Windows Azure 應用程式 」 精靈會顯示快顯對話方塊中，Visual Studio 的反向模式。 此外，核取方塊欄位不會填入此核取方塊之後被選取，另一個互動反面模式。  
  
 ![使一個對話方塊之後按下核取方塊就是 Visual Studio 的反向模式。] (../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")<br />使一個對話方塊之後按下核取方塊就是 Visual Studio 的反向模式。
  
### <a name="hyperlink-anti-patterns"></a>超連結反向模式  
 下列範例包含兩個反向模式。  
  
1.  開啟動態顯示紅色前景表示不使用字型服務共用中正確的色彩。  
  
2.  "Learn more"不是適當的文字觀念性主題的連結。 使用者的目標不是要了解詳細資訊，以了解他們所選擇的後果。  
  
 ![忽略色彩服務，並使用 「 進一步了解"的超連結是 Visual Studio 的反向模式。] (../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")<br />忽略色彩服務，並使用 「 進一步了解"的超連結是 Visual Studio 的反向模式。  
  
 **更好的解決方案：**會造成使用者會按一下連結會問的問題。  
  
-   Windows Azure 服務如何運作？  
  
-   何時需要 Windows Azure Mobile Services 專案？  
  
#### <a name="using-click-here-for-links"></a>使用 「 按一下這裡 」 的連結  
 超連結應該自述性。 它是使用"按一下這裡"反面模式或任何類似的變化。  
  
 **錯誤：** "按一下這裡取得有關如何建立新的專案。 」
  
 **良好：** 「 如何建立新的專案？ 」