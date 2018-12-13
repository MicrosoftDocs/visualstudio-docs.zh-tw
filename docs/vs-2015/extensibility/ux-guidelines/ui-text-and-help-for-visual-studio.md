---
title: UI 文字和適用於 Visual Studio 的協助 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 208fdec375927c53c185465b4ded05f7ed3fb406
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777470"
---
# <a name="ui-text-and-help-for-visual-studio"></a>UI 文字與說明適用於 Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_UITextAndTerminology"></a> UI 文字和術語  
 可理解的文字是有效的 UI 很重要的。 軟體使用者傾向於讀取標籤第一次，也就是那些最容易完成手邊的工作。 靜態文字會讀取較少的頻率。 規劃使用者啟動其工作的工作階段與整個視窗中，後面接著讀取此大致順序 UI 的快速掃描：  
  
1.  在管理中心的互動式控制項  
  
2.  認可按鈕  
  
3.  其他地方找到的互動式控制項  
  
4.  主要指示  
  
5.  補充說明  
  
6.  視窗標題  
  
7.  其他主要內文中的靜態文字  
  
### <a name="usage-patterns-for-ui-text"></a>UI 文字的使用模式  
  
#### <a name="title-bar-text"></a>標題列文字  
 標題列文字必須符合繁衍 UI 的命令。  
  
#### <a name="instructional-text-helper-text"></a>說明文字 （協助程式）  
 在某些對話方塊中，很有幫助提供顯著的主要指示，說明在視窗或頁面中，該怎麼辦。 這有時候稱為 「 協助程式文字 」。  
  
##### <a name="writing-style-rules-for-helper-text"></a>撰寫協助程式文字的樣式規則  
  
-   不會解釋明顯。 除非絕對必要，否則不會包含說明文字。  
  
-   說明文字一律會放在對話方塊頂端，而且正在執行的工作應該參考。  
  
-   精確地向使用者說明他們的需要。 避免過多的通訊和備援能力。  
  
-   檢閱每個視窗，並排除重複的文字和陳述式。  
  
-   保持簡短的說明文字。 如果需要針對特定使用者或案例的詳細資訊，然後提供詳細的概念性線上主題的連結。  
  
-   撰寫您的文字，讓每個單字加權會保留，而且不需要。  
  
-   請遵循適用於現有的 Microsoft 指南[使用者介面文字](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)並[樣式和語氣](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx)。  
  
#### <a name="supplemental-instructions"></a>補充的指示  
 補充的指示會提供可協助使用者了解控制項或控制項群組的其他資訊。 這也可能包括必須了解何種格式的輸入的控制項所預期的提示文字。 盡量不要使用補充的指示。 您可以保留它們的情況下，很可能使用者完全不了解他們正在進行選擇的後果。  
  
 ![Visual Studio 中的補充文字](../../extensibility/ux-guidelines/media/0601-b-supplementaltext1.png "0601 b_SupplementalText1")  
  
 **Visual Studio 中的補充文字**  
  
 ![Visual Studio 中的補充文字](../../extensibility/ux-guidelines/media/0601-c-supplementaltext2.png "0601 c_SupplementalText2")  
  
 **Visual Studio 中的補充文字**  
  
#### <a name="infotips"></a>資訊提示  
 通常，指示的文字可能太長的時間來定位 UI 中的就地或可能是新的使用者，混亂的情形有經驗的使用者，都覺得很有用。 在此情況下，指示/資訊文字應該放在工具提示的工具提示的形式。  
  
 資訊提示應該放置該控制它們與相關，而且應該使用尚不顯眼的特定資訊提示圖示附近明顯。  
  
 ![在 Visual Studio 中的資訊提示](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601 d_InfoTip")  
  
 **在 Visual Studio 中的資訊提示的範例**  
  
##### <a name="writing-style-rules-for-infotips"></a>資訊提示的撰寫樣式規則  
  
-   撰寫提示做為完整的句子。 它們需要特定的指令動詞、 句首大寫和結束的標點符號。  
  
-   您可以使用資訊提示以補充您的主要指示或資訊。 如果您只要使用不同的單字重新聲明主要概念，您不需要的資訊提示。  
  
-   保持簡短且清楚的資訊提示。 使用短字詞和一般、 日常的語言支援，並鼓勵使用者。  
  
-   請遵循適用於現有的 Microsoft 指南[使用者介面文字](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)並[樣式和語氣](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx)。  
  
#### <a name="control-labels"></a>控制項標籤  
 控制項標籤應該是簡短的簡潔，並遵循[控制項的 Windows 桌面指引](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx)。  
  
 如需有關控制標籤的格式和使用者介面內的位置的詳細資訊，請參閱[Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)。  
  
#### <a name="help-links"></a>說明連結  
 指示文字內或在 UI 的主體中，不被置於說明連結。 它們可以是 [說明] 連結，或啟動內部對話方塊。  
  
##### <a name="visual-style-rules-for-help-links"></a>說明連結的視覺化樣式規則  
  
-   使用正確的環境色彩的超連結。 正確地指定樣式的超連結將不會簡短地閃爍紅色時按下。 如果您看到這項目，則表示，未使用的環境色彩。  
  
-   底線應該只用於上暫留時在段落中內嵌的連結。  
  
-   如需詳細的超連結的視覺效果與互動樣式的詳細資訊，請參閱按鈕和超連結。  
  
##### <a name="writing-style-rules-for-help-links"></a>撰寫說明連結的樣式規則  
  
-   當您啟動對話方塊時, 維護的標準，省略符號： 瀏覽，省略符號，若工作需要額外的 UI 沒有省略符號。  
  
     ![在 Visual Studio 中的 [說明] 連結](../../extensibility/ux-guidelines/media/0601-e-helplink.png "0601 e_HelpLink")  
  
     **省略符號 （...） 在 [說明] 連結會指出工作會需要額外的 UI。**  
  
-   連結應該啟動與 「 深入了解，"，因為這不是使用者的意圖。 使用者想要回答特定問題，不會收到一般的教育。  
  
-   片語說明連結，讓他們要求的主題將回答問題。  
  
     不正確：  
     「 了解有關 Windows Azure 行動服務定價詳細資訊 」  
  
     修正：  
     「 何種定價選項是適用於 Windows Azure 行動服務？ 」  
  
-   絕對不要使用*按一下...* 連結文字。  
  
-   永遠不會連結僅文字 「 在這裡。 」 這是有問題的某些螢幕助讀程式，將語音超連結的文字。  
  
     不正確：  
     「 尋找有關 Windows Azure 行動服務**此處**"  
  
     修正：  
     「 何種定價選項是適用於 Windows Azure 行動服務？ 」  
  
-   如需有關說明連結的正確撰寫樣式的詳細資訊，請參閱[說明的 Windows 桌面指引](https://msdn.microsoft.com/library/windows/desktop/dn742494\(v=vs.85\).aspx)。  
  
#### <a name="hint-text"></a>提示文字  
 提示文字會顯示為浮水印的控制項內，或在控制項下方。 將套用正確的格式使用適當的 VSColors 語彙基元， `Environment.GrayText`。  
  
 它可以出現在數種格式。  
  
-   取代控制項標籤中：  
  
     ![提示在 Visual Studio 中的文字](../../extensibility/ux-guidelines/media/0601-f-hinttext1.png "0601 f_HintText1")  
  
-   具有動詞命令，提供的指示：  
  
     ![提示在 Visual Studio 中的文字](../../extensibility/ux-guidelines/media/0601-g-hinttext2.png "0601 g_HintText2")  
  
-   以文字表示的必要項目：  
  
     ![提示在 Visual Studio 中的文字](../../extensibility/ux-guidelines/media/0601-h-hinttext3.png "0601 h_HintText3")  
  
#### <a name="watermark-text"></a>浮水印文字  
 空白設計介面上，文字應指出要執行，以及提供連結以開啟其他相關的 windows 中，如果適當的項目：  
  
 ![在 Visual Studio 中的文字加上浮水印](../../extensibility/ux-guidelines/media/0601-i-watermarktext.png "0601 i_WatermarkText")  
  
 **在 Visual Studio 中的浮水印文字的範例**  
  
### <a name="common-terminology"></a>常見術語  
  
|詞彙|說明|註解|  
|----------|-----------------|-------------|  
|登入/登出|代表驗證的 web 屬性與 web 用來表示相同意義的動詞命令。 內的用戶端，我們使用此一次作為最上層概念登入和移出 IDE 使用者連線，代表最上層的身分識別可提供較高層級的功能，例如漫遊和授權，不適用於其他所有連接。|IDE 使用者是唯一的功能應該代表的登入 / 登出動詞，因為其代表最上層的 IDE 使用者。|  
|連接/中斷連線|使用其中一項功能會維持線上服務的單一連接的地方。|伺服器總管 中，其中只能有一個作用中的 Azure 連線一次，是連線/中斷連線的範例。|  
|新增/移除|非破壞性。 當新增或從清單移除項目時使用。|TFS 連接管理員伺服器清單 對話方塊是新增或移除的範例。|  
|刪除|破壞性。 要移除的項目將永久捨棄或從磁碟中刪除時，才使用。|「 刪除 」 通常需要提示，如果結果從磁碟刪除檔案。|  
  
## <a name="error-messages"></a>錯誤訊息  
  
### <a name="overview"></a>總覽  
 發生錯誤。 設定限制使用者可以執行是合理的第一個步驟，防止適當的錯誤訊息。 不過，錯誤發生時，撰寫完善的錯誤訊息即可對緩和此問題。 錯誤訊息可說是其中一個最重要的使用者會看到，因為它們是同步的則表示問題需要解決的通知類型。 撰寫不夠周全的錯誤訊息會讓使用者在他們自己決定錯誤的原因以及任何可能的解決方案。  
  
 使用者可能會停止，並注意過度使用而使或混淆的錯誤訊息，因此寫入只需要將值新增至使用者的訊息才會遇到。 如果只是通知訊息，然後使用的替代表示方式。  
  
### <a name="rules-for-creating-an-error-message"></a>建立一則錯誤訊息的規則  
  
-   建構時的錯誤訊息，請選擇適當的錯誤層級的對象。 如果適用，可能需要直接了當的摘要，可為使用者提供動作的目標。 沒有任何使用者不需要知道的項目狀態。  
  
-   提供建設性的協助。 它是您更輕鬆地讀取和處理包含指示的錯誤訊息。  
  
-   請勿使用雙重否定的意義。  
  
-   執行這兩種自動化和手動的文法與拼字檢查您所撰寫的任何錯誤訊息。  
  
-   對於複雜的錯誤訊息，避免循序的通訊。 絕對不要使用 F1 連結錯誤訊息。 訊息本身應該就已足夠。  
  
-   使用正確的圖示。  
  
-   提出問題更容易了解和使用按鈕具有清楚的選項，例如 [刪除] 和 [取消]。  
  
-   警告，能清楚了解繼續執行的結果會是。 按鈕應該會指出結果。  
  
-   對於錯誤，描述使用者可以做什麼來修正此問題。 按鈕應該是動作或說出 「 關閉 」。 請勿使用錯誤訊息的 [確定] 按鈕。  
  
-   要建構的錯誤訊息時，問問自己幾個問題：  
  
    -   使用者可以了解如何解決此錯誤單獨的問題嗎？  
  
    -   使用者不會與此錯誤使用相同的詞彙？  
  
    -   此錯誤模稜兩可，或在多個情況下共用？ 如果是的話，如何您引導使用者至所需的方案？  
  
#### <a name="build-errors"></a>建置錯誤  
 由於 Visual Studio 是一種軟體開發工具，許多元件已編譯中，將轉換，或步驟，將開發人員的工作轉換為二進位格式的編碼方式。 這些轉換可能會導致錯誤，或未正確設定編譯器選項時，編譯器無法處理不正確撰寫的檔案。  
  
 Visual Studio 使用者可以花費大量的開發時間解決建置錯誤。 錯誤會有相依性或當錯誤訊息不佳所撰寫，如此可讓它難以發現錯誤的來源時，會增加這個的解決時間。  
  
 最佳的建置錯誤可讓您為這些並不會發生在第一個位置，這也是為什麼 Visual Studio 提供自動完成和 IntelliSense 波浪線。 結構描述驗證和類似的工具會提供相同類型的意見反應。 這些機制主動引導使用者建構格式正確的程式碼，降低建置錯誤的機會。  
  
 Visual Studio 提供的工具視窗，其中使用者可以讀取和瀏覽其文件視窗中發生的錯誤。 提供鍵盤快速鍵，讓使用者可以快速瀏覽大量程式碼並直接跳到問題的位置。 Visual Studio 也可讓每個組建錯誤，以便使用者可以直接移至 [說明] 主題提供有關錯誤的詳細深入資訊繫結至特定的說明關鍵字/內容識別碼。  
  
 撰寫清楚、 簡潔的建置錯誤：  
  
-   **使用純文字的語言**說明少量或沒有編譯器術語的問題。 建置錯誤的文字不應該過度技術。  
  
-   **說明可能的原因。** 比方說，「 遺漏冒號之間的屬性和值 '（屬性）: （值）' 宣告。 」  
  
-   提供有關可能的修正方法的詳細資料。 如果沒有足夠的空間，其他詳細資料可能會放入對應的 [說明] 主題。  
  
### <a name="components-of-a-well-written-error-message"></a>編寫完善的錯誤訊息的元件  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>使用殼層對話服務的錯誤訊息。  
 使用殼層對話服務可讓您控制訊息的出現 — 特別的字型，而不會個別元素的主要變更。 使用**IErrorInfo**機制，並回報使用**IVsUIShell::SetErrorInfo/ReportErrorInfo**。  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>選擇有效且適當通知簡報。  
 如果需要立即採取行動來避免遺失資料 （同步通知），則您可以使用重大警告強制回應對話方塊。 重要圖示會保留的情況下關閉而不閱讀訊息可能會導致負面後果。 資料遺失是嚴重的問題所需的警示層級回應。 重大圖示的過度使用 desensitizes 其重要性的使用者。 如果錯誤是參考訊息在本質上，請考慮強制回應對話方塊 （非同步通知） 的替代方案。  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>提供的全新且簡潔而不是技術說明發生問題的原因說明。  
 會造成過度負荷中說明的技術詳細資料的使用者，將會使其更容易忽略錯誤訊息。 良好的傳訊的範例：  
  
-   「 無法開啟要求的檔案。 」  
  
-   「 無法連線到網際網路。 」  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>提供如何修正此問題的相關資訊。  
 提供如何修正此問題的使用者建議。 如果不有任何建議，則會誠實與使用者。 提供以替代線上來源的詳細資訊，例如技術支援人員或社群支援的直接連結。 請嘗試將使用者指向特定的線上資訊相關的問題。 錯誤識別碼，請考慮將使用者連結到該特定錯誤相關的討論。 良好的傳訊的範例：  
  
-   「 請確定您連線到網際網路，然後再試一次此作業。 」  
  
-   「 請確定檔案存在，而且您擁有開啟它的權限。 」  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>寫入訊息，而且簡短的點。  
 可以通知錯誤訊息，說明，並提供解決方案但仍然會忽略它是否過於冗長。 一個解決方案是使用漸進式揭露與詳細資料 按鈕。 例如，提供簡短描述/解決方案，並將更多詳細資料，在詳細資料 按鈕下方。 如果使用者選擇要閱讀有關錯誤的詳細資訊，他們可以這麼做。  
  
 應該在訊息中的語言：  
  
-   **適當網域。** 使用使用者就能了解的語言。 雖然我們的客戶開發人員，他們通常不需要的內容與我們的術語。  
  
-   **特定的。** 避免含糊不清的文字，並提供特定的名稱和位置的相關物件。 比方說，一則錯誤訊息例如 」 字元是無效的 「 不是很有用。 哪些字元？ 「 找不到檔案 」。 哪些檔案？  
  
-   **休息。** 不責怪使用者或讓他們覺得蠢笨。 避免惡意或冒犯性語言 （kill、 執行、 終止，嚴重的不合法）。 避免使用大寫的文字，通常會視為喊叫而不是為讀取。 請勿使用幽默。  
  
-   **更正。** 請使用正確的拼字和文法 （即使是在 alpha)。 錯字是不夠專業和尷尬。  
  
-   **顯示符合當前。** 使用適當的按鈕文字。 避免 [確定] 按鈕，並改為使用"Continue"或"Yes/no"。  
  
### <a name="error-message-examples"></a>錯誤訊息範例  
  
|好|不正確|  
|----------|---------|  
|「 您撥接的號碼已不存在於服務。 請檢查號碼和撥號一次 或 0 的運算子。 」|-「 錯誤 (449): 不合法的數字 」<br />-: 這項處理的例外狀況錯誤指出作業已順利完成 」。<br /><br /> ![在 Visual Studio 中的錯誤的錯誤訊息](../../extensibility/ux-guidelines/media/0602-a-errordialog.png "地區 0602 a_ErrorDialog")|  
  
## <a name="accessing-help"></a>存取說明  
  
### <a name="overview"></a>總覽  
 除了 MSDN 中的文件，Visual Studio 使用者都有數個存取點，以協助使用者在 UI 中。 若要確保以一致的方式提供這些存取點，feature 小組需要利用環境所提供的 [說明] 系統。 這些存取點是：  
  
-   **在對話方塊中的指示和補充文字。** 可讓方向或說明，在 UI 介面或將滑鼠停駐的工具提示圖示上可用的靜態文字。  
  
-   **F1 說明**（只有編輯器）。 在 Visual Studio 編輯器中，使用者可信任，隨時按下 f1 鍵將會顯示目前的選取範圍到特定的說明主題。 請確定 F1 相關聯的主題是適當的和有用的資訊。  
  
-   **[說明] 主題的超連結。** 對話方塊、 工具視窗中或啟動主題，以協助使用者深入了解技術、 功能或如何完成工作的相關資訊的設計介面內超連結。  
  
-   **協助程式 UI 機制，例如智慧標籤和建立對話方塊。** 這些機制會協助使用者了解 UI 項目，或簡化工作，例如智慧標籤或產生器 對話方塊。  
  
-   **UI 說明按鈕**（已過時）。 提供的存取權相關的 F1 說明主題的標題列中顯示的指示器。  
  
### <a name="text"></a>文字  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>在對話方塊中的指示和補充文字  
 在支援複雜工作的對話，可能需要通常頂端或附近複雜的控制項的對話方塊提供 UI，內的說明文字。 請參閱[UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)如需有關撰寫樣式。  
  
#### <a name="infotips"></a>資訊提示  
 通常，說明文字可能太長的時間，在 UI 中的位置，或可能是新的使用者，混亂的情形有經驗的使用者，都覺得很有用。 在此情況下，指示/資訊文字應該放在工具提示的工具提示的形式。  
  
 資訊提示應該放置該控制它們與相關，而且應該使用尚不顯眼的特定資訊提示圖示附近明顯。  
  
 ![在 Visual Studio 中的資訊提示](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601 d_InfoTip")  
  
 **在 Visual Studio 中的資訊提示的範例**  
  
### <a name="interactive-help-mechanisms"></a>互動式說明機制  
  
#### <a name="f1-help"></a>F1 說明  
 F1 說明是必要的編輯器或設計介面內，但不是適用其他地方在 Visual Studio 環境中。  
  
#### <a name="hyperlinks-to-help-topics"></a>[說明] 主題的超連結  
 若要執行的動作、 在 ide 中，瀏覽或在瀏覽器中啟動說明可用的超連結。 請參閱[UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)如需有關語言和 07.10.01 按鈕和視覺效果和配置的指導方針的超連結。  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>協助 （已過時） 的對話方塊標題列中的 [？] 按鈕  
 大部分的情況下，說明 [？] 按鈕的對話方塊標題列中已被取代。 UI 主題不再是我們的文件模型的一部分，因此可能不會有相關的主題，以連結至。 基本上，標題列按鈕的 F1 說明的一樣，已不再需要在對話方塊中。 在某些情況下，這仍然可用來當做指標有可用概念或程序的詳細資訊，雖然較新的 UI 更常用於超連結。  
  
##### <a name="dialogs-created-through-the-environment"></a>透過在環境建立的對話方塊  
 透過建立許多殼層對話**VBDialogBoxParam**函式。 此共用的函式已經更新，以協助您移動**幫助**從對話方塊按鈕**嗎？** 按鈕，同時保留與舊版的架構相容且可延伸。  
  
 具體而言， **VBDialogBoxParam**函式會查看其識別碼是一個按鈕的對話方塊範本**IDHELP** (9) 或標籤**協助**或 **& 協助**. 如果找到的 [說明] 按鈕時，它隱藏和**WS_EX_CONTEXTHELP**樣式加入對話方塊中，而放置**嗎？** 對話方塊的標題列中的按鈕。  
  
 建立對話方塊時，它將推送至堆疊的對話方塊程序，並叫用 [] 對話方塊中，使用前置處理的對話方塊程序，名為**DialogPreProc**。 當**嗎？** 按一下按鈕時，它會傳送**WM_SYSCOMMAND**的**SC_CONTEXTHELP**對話方塊。 **DialogPreProc**會擷取此命令，並將其變更**WM_HELP**傳遞至原始對話方塊處理的訊息  
  
 大部分的環境建立對話方塊對對話方塊的 [說明] 按鈕。 [說明] 按鈕顯示對話方塊時，會自動隱藏，而且只**嗎？** 按鈕可以運作。 如果**嗎？** 按鈕曾經是移除或變更 Windows 中，此解決方案可讓您快速地移回原始的 [說明] 按鈕。  
  
 此解決方案可讓您可能會導致 bug 的四個假設：  
  
- 對話方塊的 [說明] 按鈕**IDHELP** (9)。  
  
- 隱藏 [說明] 按鈕時，對話方塊看起來正確無誤。  
  
- 對話方塊不會取代其 winproc。  
  
- 對話方塊不會內嵌在另一個對話方塊中。  
  
  如果您的對話方塊內 msenv，但未使用**VBDialogBoxParam**，調查運用**VBDialogBoxParam**實作您自己的處理常式之前。  
  
##### <a name="dialogs-created-through-other-packages"></a>透過其他封裝所建立的對話方塊  
 您可以實作自己的解決方案了外部 msenv 的對話方塊。 在 VSPackage 中共用的對話方塊類別，請考慮將按鈕移至標題列，或實作在每個對話方塊上的處理常式。 下列程式碼是一個實作來幫助您入門的基本架構：  
  
```  
struct DLGPROCITEM  
{  
    FARPROC proc; // The info used to create the dialog.  
    DLGPROCITEM* procPrev;  
};  
  
DLGPROCITEM* g_dlgProcStack = NULL;  
  
// A dialog starter/wrapper function is used to push the new  
// dialog proc to the top of our dialog proc stack.  
  
int SomeDialogStarterFunction(hinst, id, proc, etc)  
{  
    if (g_dlgProcStack == NULL)  
    {  
        g_dlgProcStack = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = NULL;  
    }  
    else  
    {  
        DLGPROCITEM* procItem = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = g_dlgProcStack;  
        g_dlgProcStack = procItem;  
    }  
}  
  
// Pop this dialog proc off the dialog proc stack.  
  
DialogBoxIndirectParam...(...)  
{  
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;  
    delete g_dlgProcStack;  
    g_dlgProcStack = procItem;  
}  
  
// A wrapper dialog procedure will allow us to capture the  
// SC_CONTEXTHELP button on the title bar from Windows and  
// forward it as a simple WM_HELP message back to the dialog.  
  
INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,  
    WPARAM wParam, LPARAM lParam)  
{  
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)  
    {  
        uMsg = WM_HELP;  
        wParam = 0;  
        lParam = 0;  
    }  
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,  
        hwndDlg, uMsg, wParam, lParam);  
}  
```  
  
##### <a name="help-buttons-in-managed-code"></a>在 managed 程式碼中的 [說明] 按鈕  
 覆寫視窗標題列說明按鈕的預設行為是以 managed 程式碼容易。 以下是完整的示範應用程式，示範此行為。 基本上，您需要覆寫您的表單**WndProc**方法，然後引發 F1 說明關閉要求時**SC_CONTEXTHELP**攔截訊息。  
  
```  
using System;  
using System.Windows.Forms;  
  
public class HelpForm : Form  
{  
    private const int SC_CONTEXTHELP = 0xF180;  
    private const int WM_SYSCOMMAND = 0x0112;  
  
    public HelpForm()  
    {  
        this.ClientSize = new System.Drawing.Size(300, 250);  
        this.HelpButton = true;  
        this.MaximizeBox = false;  
        this.MinimizeBox = false;  
        this.Name = "HelpForm";  
        this.Text = "Help Form";  
    }  
  
    protected override void WndProc(ref Message m)  
    {  
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)  
            ShowHelp();  
        else  
            base.WndProc(ref m);  
    }  
  
    private void ShowHelp()  
    {  
        MessageBox.Show("F1 Help goes here.");  
    }  
  
     [STAThread]  
    static void Main()  
    {  
        Application.EnableVisualStyles();  
        Application.EnableRTLMirroring();  
        Application.Run(new HelpForm());  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [字型和格式適用於 Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [適用於 Visual Studio 的版面配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [適用於 Visual Studio 的通知和進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

