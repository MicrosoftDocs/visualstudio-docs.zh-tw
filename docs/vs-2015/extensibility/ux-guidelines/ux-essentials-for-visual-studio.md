---
title: UX 基本資訊
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f3ed2d3f8bc52b21f6a87ac7d6da00f665f6b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181444"
---
# <a name="ux-essentials-for-visual-studio"></a>適用於 Visual Studio 的 UX 基本項目
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>最佳作法

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. 在 Visual Studio 環境中保持一致。

- 遵循 shell 中現有的互動模式。

- 設計功能，與 shell 的視覺語言和熱情技術需求一致。

- 使用共用的命令和控制項（如果有的話）。

- 瞭解 Visual Studio 階層，以及它如何建立內容和驅動 UI。

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. 將環境服務用於字型和色彩。

- 除非已在 [選項] 對話方塊的 [字型和色彩] 頁面中公開自訂，否則 UI 應該遵守目前的環境字型設定。

- UI 元素必須使用 VSColor 服務，其使用共用環境權杖或特定功能的權杖。

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. 將所有影像與新的 VS 樣式保持一致。

- 遵循圖示、圖像和其他圖形 Visual Studio 設計原則。

- 請勿將文字放在圖形元素中。

### <a name="4-design-from-a-user-centric-perspective"></a>4. 從以使用者為中心的觀點來設計。

- 在其中的個別功能之前建立工作流程。

- 熟悉您的使用者，並在您的規格中做出明確的知識。

- 查看 UI 時，請評估完整體驗以及詳細資料。

- 設計您的 UI，讓它保持運作且吸引人，不論地區設定或語言為何。

## <a name="screen-resolution"></a>螢幕解析度

### <a name="minimum-resolution"></a>最低解析度
 Visual Studio Dev14 的最小解析度是1280x1024。 這表示，雖然它 *可能不* 是最佳的使用者經驗，但仍可使用 Visual Studio 此解決方案。 不保證所有層面都能在解析度低於1280x1024 的情況下使用。

 初始對話大小不應超過1000圖元的高度，因此必須符合此最低解析度解析度（96 DPI）內的 IDE 框架。

### <a name="high-density-displays"></a>高密度顯示器
 Visual Studio 中的 UI 必須適用于 Windows 所支援的所有 DPI 縮放比例因素：150%、200% 和250%。

## <a name="anti-patterns"></a>反模式
 Visual Studio 包含了許多遵循指導方針和最佳作法的 UI 範例。 為了保持一致，開發人員通常會從類似于所建立的產品 UI 設計模式借用。 雖然這是很好的方法，可協助我們在使用者互動和視覺化設計方面保持一致性，但由於排程條件約束或瑕疵優先順序的緣故，我們會以一些不符合指導方針的詳細資料來傳送功能。 在這些情況下，我們不希望小組複製其中一種「反模式」，因為它們會在 Visual Studio 環境中增加不良或不一致的 UI。

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>預設顯示為錯誤狀態的必要欄位/設定

#### <a name="feature-team-goals"></a>功能小組目標

- 警告使用者已新增必須設定的元素。

- 將使用者的注意力吸引到需要輸入的區域。

#### <a name="anti-pattern-solution"></a>防模式方案
 一旦使用者啟動動作，並在完成此工作之前，請立即在需要設定的區域旁放置重大-停用圖示。

#### <a name="example-manifest-designer-declarations"></a>範例：資訊清單設計工具宣告
 將宣告新增至清單會立即將其置於錯誤狀態，而這會持續到使用者設定必要的屬性為止。

 在此情況下，有其他考慮，因為用於警示的圖示包含 "x"，因此不能在旁邊使用一般的移除圖示。 因此，UI 會使用 [移除] 按鈕，這是一個更相當笨拙的控制項。

 ![資訊清單設計工具錯誤聲明防&#45;模式](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti 模式")

 **依預設，將 UI 放置在錯誤狀態中是 Visual Studio 的反模式。**

#### <a name="alternatives"></a>替代方案
 解決這個問題的一個更好的方法是：

- 允許使用者在不發出警告的情況下新增宣告，然後立即移動以設定專案的屬性。

- 將 [警告] 圖示新增 (金三角形) 當焦點移出項目時，例如將另一個宣告加入至清單，或嘗試變更設計工具內的索引標籤。

- 如果使用者嘗試在設定任何宣告的屬性之前變更索引標籤，請先彈出一個對話方塊，說明該應用程式將不會建立 (或任何) 的含意，直到警告解決為止。 如果使用者關閉對話方塊並變更索引標籤，則會在 [宣告] 索引標籤中加入適當的) ， (重大或警告的圖示。

### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>強制使用者在關閉 UI 之前讀取文字

#### <a name="feature-team-goals"></a>功能小組目標
 不允許使用者在不先看到解說文字的情況下關閉 UI。

#### <a name="anti-pattern"></a>反模式
 小組將影片連結插入 VS UI 內的不同位置，是根據 UX 所指定的 X [關閉] 按鈕和工具提示說明的一般模式來決定，而改為執行下拉式清單和 [不要再顯示] 連結。

 ![解釋文字反&#45;模式 &#45; 不正確](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")

 **不正確：強制使用者在關閉 UI 之前讀取解說文字是 Visual Studio 內的反模式。**

#### <a name="result"></a>結果
 除了簡單的 [關閉] 按鈕 (按一下) ，使用者會被迫使用兩次點擊，只要在影片連結出現的每個位置關閉 UI 即可。

#### <a name="alternatives"></a>替代方案
 這種情況的正確設計是遵循 Internet Explorer、Office 和 Visual Studio 的通用模式：在滑鼠停留時，使用者可以看到工具提示的描述，然後按一下 [隱藏 UI]。

 ![解釋文字反&#45;模式 &#45; 正確](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-模式-正確")

 **正確：依設計，影片連結應該會顯示工具提示，其中包含有關暫留的額外資訊，而按一下 "X" 應該會關閉訊息，而不需要進一步的互動。**

### <a name="using-command-bars-for-settings"></a>使用命令列進行設定
 ![命令列反&#45;模式 &#45; 圖 A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-FigureA")

 **圖 A：命令列反模式**

 **圖 A** 代表這個反模式：將設定放在命令按鈕下，而不只是命令。 在此草圖中，除了開始偵錯工具之外，還有一些命令，例如在瀏覽器中查看、啟動而不進行偵錯工具，以及逐步執行，這些都將遵守選取的設定。

 ![命令列反&#45;模式 &#45; 圖 B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-pattern-FigureB")

 **圖 B：更好，但仍然是命令列反模式**

 這種類型的設定會稍微更好，但還是不太希望，如 **圖 B**所示。雖然分割按鈕需要較少的空間，因此改善了下拉式清單，但是這兩種設計仍會使用工具列來提升非命令的內容。

 ![命令列反&#45;模式 &#45; 圖 C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")

 **圖 C：正確使用 Visual Studio 命令列模式**

 在 **圖 C**中，此設定會系結至一系列的命令。 未設定全域設定，我們只是在四個命令之間切換。 這是可接受工具列中命令的唯一情況。

### <a name="control-anti-patterns"></a>控制反模式
 有些反模式就是不正確的使用方式或控制項或控制項群組的呈現方式。

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>用來當做群組標籤的底線，而不是超連結
 純文字只能用於超連結。

 **壞：**

 ![將群組標籤中的反&#45;模式加底線](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102-g_GroupLabelIncorrect")

 **不是超連結的加底線文字是 Visual Studio 的反模式。**

 **好：**

 ![將群組標籤中的反&#45;模式加底線 &#40;正確的&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102-h_GroupLabelCorrect")

 **正確樣式的非超連結文字會以未方式出現在環境字型中。**

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>按一下核取方塊會產生彈出對話方塊
 按一下 [發佈 Windows Azure 應用程式] 中的 [啟用所有角色的遠端桌面] 核取方塊，就會立即顯示一個快顯對話方塊，也就是 Visual Studio 的反模式。 此外，選取 [核取方塊] 欄位之後，[核取方塊] 欄位不會填入核取方塊，而是另一種互動反模式。

 ![核取方塊 pop&#45;反&#45;模式](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102-i_CheckboxPopup")

 **按一下核取方塊後，就會出現一個對話方塊，那就是 Visual Studio 的反模式。**

### <a name="hyperlink-anti-patterns"></a>超連結反向模式
 下列範例包含兩個反模式。

1. 停留時，前景會變成紅色，表示未使用來自字型服務的正確共用色彩。

2. 「深入瞭解」不是概念性主題連結的適當文字。 使用者的目標不是要深入瞭解，而是瞭解他們選擇的後果。

   ![超連結反&#45;模式](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")

   **略過色彩服務，並使用 [深入瞭解] 超連結的 Visual Studio 反模式。**

   **更好的解決方案：** 藉由按一下連結，提出使用者會詢問的問題。

- Windows Azure 服務如何運作？

- 何時需要 Windows Azure 行動服務專案？

#### <a name="using-click-here-for-links"></a>使用「按一下這裡」以取得連結
 超連結應該是自我描述的。 這是使用「按一下這裡」或任何類似變化的反模式。

 **錯誤：** 「按一下這裡以取得如何建立新專案的相關指示」。

 **好：** 「如何? 建立新專案嗎？」
