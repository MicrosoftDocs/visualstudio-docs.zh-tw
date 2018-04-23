---
title: UI 文字和 Visual Studio 的說明 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 697c794d17f3004b0f37e668ff67afb703490e18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ui-text-and-help-for-visual-studio"></a>UI 文字和 Visual Studio 的說明
##  <a name="BKMK_UITextAndTerminology"></a> UI 文字和術語  
 易於文字是有效的 UI 很重要的。 軟體使用者傾向於讀取標籤第一次，也就是那些最相關的完成工作的必要性。 靜態文字會讀取較少的頻率。 規劃使用者以他們工作的工作階段開頭後面接著這個按大致順序 UI 讀取整個視窗的快速掃描：  
  
1.  在中央互動式控制項  
  
2.  認可按鈕  
  
3.  其他地方找到互動式控制項  
  
4.  主要指示  
  
5.  補充的說明  
  
6.  視窗標題  
  
7.  在主要本文中其他靜態文字  
  
### <a name="usage-patterns-for-ui-text"></a>使用 UI 文字模式  
  
#### <a name="title-bar-text"></a>標題列文字  
 標題列文字必須符合繁衍 UI 的命令。  
  
#### <a name="instructional-text-helper-text"></a>說明文字 （helper 文字）  
 在某些對話方塊中，最好先提供顯著主要的指示，說明在視窗或頁面中，該怎麼辦。 這有時候稱為 「 協助程式文字 」。  
  
##### <a name="writing-style-rules-for-helper-text"></a>撰寫協助程式文字的樣式規則  
  
-   不會解釋明顯。 除非絕對需要否則不會包含說明文字。  
  
-   說明文字永遠會放在對話方塊的頂端，而且應該參考正在執行的工作。  
  
-   精確地向使用者說明他們的需要。 避免過多的通訊和備援。  
  
-   檢閱每個視窗，並消除重複的文字與陳述式。  
  
-   保持簡短的說明文字。 如果需要針對特定使用者或案例的詳細資訊，然後提供詳細的概念性線上主題的連結。  
  
-   撰寫您的文字，讓每個字都會保存加權，而且不需要。  
  
-   請依照下列指導現有 Microsoft[使用者介面文字](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)和[樣式以及色調](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx)。  
  
#### <a name="supplemental-instructions"></a>補充的指示  
 補充的指示提供可協助使用者了解控制項或群組的 control 的其他資訊。 這也可能包含必須了解何種格式所預期的輸入的控制項的提示文字。 謹慎地使用補充的指示。 保留它們的情況下，很可能使用者完全不了解的成員進行的選擇。  
  
 ![Visual Studio 中的補充文字](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601 b_SupplementalText1")  
  
 **Visual Studio 中的補充文字**  
  
 ![Visual Studio 中的補充文字](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601 c_SupplementalText2")  
  
 **Visual Studio 中的補充文字**  
  
#### <a name="infotips"></a>資訊提示  
 通常，指示文字可能會在 UI 中定位就地過於冗長，或者可能只給新使用者覺得混淆有經驗的使用者很有用。 在此情況下，指示/資訊文字應放在工具提示的工具提示的方式。  
  
 資訊提示應該放置在靠近它們與相關的控制項的應該使用特定的資訊提示圖示尚不顯眼明顯。  
  
 ![在 Visual Studio 中的資訊提示](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **在 Visual Studio 中的資訊提示的範例**  
  
##### <a name="writing-style-rules-for-infotips"></a>資訊提示的撰寫樣式規則  
  
-   撰寫提示做為完整的句子。 它們需要特定動詞，句子的情況下，並結束的標點符號。  
  
-   您可以使用資訊提示來補充您的主要指示或資訊。 如果您只要重新聲明主要概念使用不同的字，則不需要以資訊提示。  
  
-   保持簡短且清楚的資訊提示。 使用小型字和一般、 日常語言的支援，並可鼓勵使用者。  
  
-   請依照下列指導現有 Microsoft[使用者介面文字](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)和[樣式以及色調](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx)。  
  
#### <a name="control-labels"></a>控制項標籤  
 控制項標籤應該是簡短、 簡潔，並且遵照[控制項的 Windows 桌面指引](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx)。  
  
 如需控制項標籤格式並放置在此 UI 中的詳細資訊，請參閱[for Visual Studio 的版面配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md)。  
  
#### <a name="help-links"></a>說明連結  
 說明文字或 UI 的內文中可以被置於說明連結。 也可以說明的連結伺服器或啟動內部對話方塊。  
  
##### <a name="visual-style-rules-for-help-links"></a>說明連結的視覺化樣式規則  
  
-   使用正確環境色彩的超連結。 已正確設定的樣式的超連結將不會簡要閃爍紅色時按下。 如果您發現此情形，則表示，未使用的環境色彩。  
  
-   底線應該只用於暫留，或當嵌入段落中的連結。  
  
-   視覺效果且互動的超連結樣式的詳細資訊，請參閱按鈕和超連結。  
  
##### <a name="writing-style-rules-for-help-links"></a>撰寫說明連結的樣式規則  
  
-   當啟動對話方塊，維護省略符號的標準： 沒有省略符號瀏覽，若工作需要額外的 UI 的省略符號。  
  
     ![在 Visual Studio 中的 [說明] 連結](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601 e_HelpLink")  
  
     **說明連結中的省略符號 （...） 會指出工作會需要額外的 UI。**  
  
-   連結應該開始 「 學習 」，因為這不是使用者的意圖。 使用者想要回答特定的問題，不會收到一般的教育。  
  
-   片語說明連結，讓他們要求的主題會回答問題。  
  
     不正確：  
     「 深入了解 Windows Azure 行動服務定價"  
  
     修正：  
     「 哪些定價選項是適用於 Windows Azure Mobile Services？ 」  
  
-   絕對不要使用*按一下...*連結文字。  
  
-   永遠不會連結只有單字"here"。 這是有問題的一些螢幕助讀程式，將語音超連結的文字。  
  
     不正確：  
     「 找到有關 Windows Azure Mobile Services**這裡**"  
  
     修正：  
     「 哪些定價選項是適用於 Windows Azure Mobile Services？ 」  
  
-   如需有關說明連結的正確撰寫樣式的詳細資訊，請參閱[說明的 Windows 桌面指引](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx)。  
  
#### <a name="hint-text"></a>提示文字  
 提示文字會顯示為浮水印的控制項中，或在控制項下方。 將會使用適當的 VSColors 語彙基元，來套用正確的格式`Environment.GrayText`。  
  
 它可以出現在數種格式。  
  
-   取代控制項標籤：  
  
     ![提示 Visual Studio 中的文字](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601 f_HintText1")  
  
-   具有動詞命令，提供指示：  
  
     ![提示 Visual Studio 中的文字](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601 g_HintText2")  
  
-   以文字表示的必要項目：  
  
     ![提示 Visual Studio 中的文字](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601 h_HintText3")  
  
#### <a name="watermark-text"></a>浮水印文字  
 空白設計介面上，文字應該指出要執行，以及提供連結，即可開啟其他相關的 windows 中，如果適當項目：  
  
 ![浮水印 Visual Studio 中的文字](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601 i_WatermarkText")  
  
 **Visual Studio 中的浮水印文字的範例**  
  
### <a name="common-terminology"></a>常見的術語  
  
|詞彙|說明|註解|  
|----------|-----------------|-------------|  
|登入/登出|用於意義與 web 表示成 web 屬性驗證的動詞命令。 在用戶端，我們會使用一次為最上層概念的登入和移出 IDE 使用者連接代表最上層的身分識別，提供更高層級的功能，例如漫遊和授權，不適用於其他所有連接。|IDE 使用者是唯一的功能，應該代表登入 / 登出動詞命令，因為它代表最上層的 IDE 使用者。|  
|連接/中斷連線|在其中一項功能會維持線上服務的單一連接的地方使用。|伺服器總管 中，其中您可以只有一個使用中的 Azure 連接一次，是連線/中斷連線的範例。|  
|新增/移除|非破壞性。 當加入或從清單移除項目時使用。|TFS 連接管理員的伺服器清單對話方塊是新增或移除的範例。|  
|刪除|破壞性。 要移除的項目將會永久捨棄或從磁碟中刪除時，才使用。|「 刪除 」 通常需要提示，如果結果從磁碟刪除檔案。|  
  
## <a name="error-messages"></a>錯誤訊息  
  
### <a name="overview"></a>總覽  
 發生錯誤。 設定限制使用者可以執行是合理的第一個步驟，在避免屆時錯誤訊息。 不過，發生錯誤時的編寫完善的錯誤訊息可以移對緩和此問題。 錯誤訊息可說是其中一個最重要的使用者會看到，因為它們是同步，則表示需要解決問題的通知類型。 撰寫不夠周全的錯誤訊息會保留使用者在他們自己決定錯誤的原因以及任何可能的解決方案。  
  
 注意過度使用而使或混淆的錯誤訊息，因此遇到將值加入至使用者的寫入只需要訊息，使用者可能會停止。 如果只是通知訊息，然後使用替代的簡報。  
  
### <a name="rules-for-creating-an-error-message"></a>規則，以建立錯誤訊息  
  
-   建構時的錯誤訊息，請選擇適當的錯誤層級的對象。 適用時，可以採取直接的摘要，可提供使用者動作的目標。 沒有任何不需要知道使用者的項目狀態。  
  
-   提供建設性的回饋的協助。 它是容易讀取和處理錯誤訊息，其中包含指令。  
  
-   請勿使用雙否定。  
  
-   執行這兩個自動化和手動文法與拼字檢查在您撰寫的任何錯誤訊息。  
  
-   對於複雜的錯誤訊息，避免循序通訊。 絕對不要使用 F1 連結的錯誤訊息。 訊息本身應該很足夠。  
  
-   使用正確的圖示。  
  
-   讓您輕鬆地了解及使用有清楚的選項，例如 「 刪除 」 和 [取消]。 按鈕問題  
  
-   警告，是有關繼續執行的結果將會清除。 按鈕應會顯示結果。  
  
-   為錯誤，說明使用者可以來修正問題。 按鈕應該是動作或說 「 關閉 」。 請勿使用錯誤訊息 [確定] 按鈕。  
  
-   要建構的錯誤訊息時，請詢問自己的一些問題：  
  
    -   使用者可以了解如何解決此錯誤單獨的問題？  
  
    -   使用者沒有與此錯誤使用相同的詞彙嗎？  
  
    -   此錯誤模稜兩可，或在有多個情況中共用？ 如果是，如何您引導使用者至所需的方案？  
  
#### <a name="build-errors"></a>建置錯誤  
 由於 Visual Studio 軟體開發工具，許多元件都有編譯中，轉換時，或編碼成二進位格式的開發人員的工作的步驟。 這些轉換可能會導致錯誤，或未正確設定編譯器選項時，編譯器無法處理撰寫不正確的檔案。  
  
 Visual Studio 使用者可以縮短對有大量的開發小時解決建置錯誤。 錯誤上面會有相依性或錯誤訊息不良寫入時，這可能會使它困難以發現錯誤的來源時，會增加此解決時間。  
  
 最佳的建置錯誤，並不會發生在第一個位置，這也是為什麼 Visual Studio 提供 [自動完成]，IntelliSense 波浪線。 結構描述驗證和類似的工具可提供同類的意見反應。 這些機制主動指引使用者建構語式正確的程式碼，因而發生建置錯誤的機會。  
  
 Visual Studio 提供的工具視窗，其中使用者可以讀取和瀏覽其文件視窗中所發生的錯誤。 提供鍵盤快速鍵，讓使用者可以快速瀏覽大量程式碼並直接前往問題的位置。 Visual Studio 也可讓每個建置錯誤，以便使用者可以直接前往說明主題，可提供更多深入資訊錯誤繫結至特定的說明關鍵字/內容識別碼。  
  
 撰寫清楚、 簡潔的建置錯誤：  
  
-   **使用純文字的語言**解說少量或沒有編譯器術語的問題。 建置錯誤的文字不能過於技術。  
  
-   **概述可能的原因。** 例如，「 遺漏的屬性與值之間的分號 '（屬性）: （值）' 宣告。 」  
  
-   提供有關可能的修正方法的詳細資料。 如果沒有足夠的空間，其他詳細資料可能會放入對應的說明主題。  
  
### <a name="components-of-a-well-written-error-message"></a>編寫完善的錯誤訊息的元件  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>使用命令介面 對話方塊服務的錯誤訊息。  
 使用 shell 對話方塊服務，可讓您控制的訊息，字型外觀特別的是，不需要主要變更個別項目。 使用**IErrorInfo**機制，並回報使用**IVsUIShell::SetErrorInfo/ReportErrorInfo**。  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>選擇有效率且適當的通知簡報。  
 如果需要立即採取行動來避免遺失資料 （同步通知），則您可以使用重要警告強制回應對話方塊。 重大圖示被保留的情況下關閉訊息，但讀取可能會導致負面結果。 資料遺失會是重要的情況下需要警示層級回應。 重大圖示的過度使用 desensitizes 其重要性的使用者。 如果錯誤是參考訊息在本質上，請考慮強制回應對話方塊 （非同步通知） 的替代方案。  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>提供的全新、 簡潔而不是技術說明發生問題的原因說明。  
 充滿中說明的技術詳細資料的使用者會讓它們更容易忽略錯誤訊息。 良好的傳訊範例：  
  
-   「 無法開啟要求的檔案。 」  
  
-   「 無法連線到網際網路。 」  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>提供如何修正此問題的相關資訊。  
 提供如何修正此問題的使用者的建議。 老實說與使用者是否有任何建議。 提供替代線上來源的詳細資訊，例如，技術支援人員或社群支援的直接連結。 請嘗試將使用者指向特定的線上資訊相關的問題。 錯誤識別碼，請考慮將使用者連結到有關該特定錯誤的討論。 良好的傳訊範例：  
  
-   「 請確定您已連線至網際網路，然後再次嘗試這項作業。 」  
  
-   「 請確定檔案存在，而且您有權限來開啟它。 」  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>撰寫簡短並且點的訊息。  
 可以通知的錯誤訊息，說明，並提供解決方案但仍會忽略是否太喘。 其中一種解決方案是使用漸進式洩漏與詳細資料 按鈕。 例如，提供簡短描述/方案，然後放置在 [詳細資料] 按鈕下方的更多詳細資料。 如果使用者選擇要閱讀有關錯誤的詳細資訊，他們可以這樣做。  
  
 應該在訊息中的語言：  
  
-   **適當網域。** 使用就可以了解使用者的語言。 雖然我們的客戶是開發人員，通常不會擁有的內容與我們的術語。  
  
-   **特定的。** 避免模糊的文字，並提供特定名稱和位置相關的物件。 比方說，錯誤訊息如 「 字元無效 」 不是很有用。 哪些字元？ 「 找不到檔案 」。 哪些檔案？  
  
-   **禮貌。** 不責怪使用者或讓他們覺得蠢笨。 避免惡意或冒犯意味的語言 （kill、 執行、 終止，嚴重的不合法）。 避免大寫的文字，通常會視為喊叫，而且不是以可讀取。 請勿使用幽默。  
  
-   **更正。** 使用正確的拼字和文法 （即使在 alpha)。 打錯字為不夠專業和免於。  
  
-   **當前。** 使用適當的按鈕文字。 避免 [確定] 按鈕，並改為使用"Continue"或"Yes/no"  
  
### <a name="error-message-examples"></a>錯誤訊息範例  
  
|好|不正確|  
|----------|---------|  
|「 您撥接的號碼已不存在於服務。 請檢查號碼和撥號再次 或 0 的運算子。 」|-「 錯誤 (449): 不合法的數目 」<br />-「 此處理的例外狀況錯誤表示作業順利完成 」。<br /><br /> ![Visual Studio 中的錯誤的錯誤訊息](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 a_ErrorDialog")|  
  
## <a name="accessing-help"></a>存取說明  
  
### <a name="overview"></a>總覽  
 除了 MSDN 中的文件，Visual Studio 使用者都有數個存取點，以協助使用者在 UI 中。 若要確保這些存取點會一直處於可用狀態，功能小組需要利用環境所提供的說明系統。 這些存取點是：  
  
-   **在對話方塊中的指示和補充文字。** 提供方向或說明 UI 介面或使用暫留時顯示資訊提示圖示上的靜態文字。  
  
-   **F1 說明**（只編輯器）。 在 Visual Studio 編輯器中，使用者可信任，隨時按下 f1 鍵會顯示目前選取範圍到特定的說明主題。 請確認適當和資訊性 F1 相關聯的主題。  
  
-   **說明主題的超連結。** 超連結對話方塊、 工具視窗中或啟動主題來協助使用者更深入的技術、 功能或如何完成工作的相關資訊的設計介面中。  
  
-   **協助程式 UI 機制，例如智慧標籤和建立對話方塊。** 這些機制協助使用者了解 UI 項目，或簡化的工作，例如智慧標籤或產生器對話方塊。  
  
-   **UI 說明按鈕**（已被取代）。 提供的存取權的相關的 F1 說明主題的標題列中顯示的指標。  
  
### <a name="text"></a>Text  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>在對話方塊中的指示和補充文字  
 對話方塊中，支援複雜的工作，可能需要提供使用者介面，內的說明文字通常頂端或附近的複雜控制項的對話方塊。 請參閱[UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)如書寫風格的詳細資訊。  
  
#### <a name="infotips"></a>資訊提示  
 通常，說明文字可能太長的時間來定位在 UI 中的位置，或只給新使用者覺得混淆有經驗的使用者相當實用。 在此情況下，指示/資訊文字應放在工具提示的工具提示的方式。  
  
 資訊提示應該放置在靠近它們與相關的控制項的應該使用特定的資訊提示圖示尚不顯眼明顯。  
  
 ![在 Visual Studio 中的資訊提示](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **在 Visual Studio 中的資訊提示的範例**  
  
### <a name="interactive-help-mechanisms"></a>互動式說明機制  
  
#### <a name="f1-help"></a>F1 說明  
 F1 說明無須編輯器或設計介面中，但其他位置不在 Visual Studio 環境中。  
  
#### <a name="hyperlinks-to-help-topics"></a>說明主題的超連結  
 超連結可以用於執行的動作，在 ide 中，瀏覽或在瀏覽器中啟動說明。 請參閱[UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)如需詳細資料語言和 07.10.01 上按鈕和超連結，如 visual 和配置的指導方針。  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>說明 （已過時） 的對話方塊標題列中的 [？] 按鈕  
 大部分的情況下，對話方塊的標題列中的 [？] 說明按鈕，已被取代。 UI 主題不再是我們的文件模型的一部分，因此可能不會有相關的主題，以連結至。 基本上，標題列按鈕已 F1 說明，相同的動作，而且不再需要在對話方塊中。 在某些情況下，這仍可用來當作指標有可用概念或程序的詳細資訊，雖然超連結會更常用於較新的 UI。  
  
##### <a name="dialogs-created-through-the-environment"></a>透過在環境建立的對話方塊  
 透過建立許多殼層對話方塊**VBDialogBoxParam**函式。 已更新此共用的函式，以協助您移動**協助**對話方塊按鈕**嗎？** 按鈕，同時保留與舊版的架構相容且可延伸。  
  
 具體來說， **VBDialogBoxParam**函式會查看其識別碼是一個按鈕的對話方塊範本**IDHELP** (9) 或標籤是**協助**或**（& a) 協助**. 如果找到說明 按鈕，它隱藏和**WS_EX_CONTEXTHELP**樣式加入至對話方塊中，而放置**嗎？** 在對話方塊的標題列按鈕。  
  
 建立對話方塊時，推入至堆疊的對話方塊程序，並使用名為前置處理的對話方塊程序叫用對話方塊**DialogPreProc**。 當**嗎？** 按一下按鈕時，它會傳送**WM_SYSCOMMAND**的**SC_CONTEXTHELP**對話方塊。 **DialogPreProc**擷取此命令，並且其變更為**WM_HELP**訊息，傳遞至原始的對話方塊程  
  
 大部分的環境建立對話方塊對對話方塊的說明 按鈕。 [說明] 按鈕顯示對話方塊時，會自動隱藏，而且只**嗎？** 按鈕的功能。 如果**嗎？** 按鈕會永遠移除或變更 Windows 中，此解決方案可讓您快速地移回原始的 [說明] 按鈕。  
  
 此解決方案會進行可能會導致 bug 的四個假設：  
  
-   對話方塊的 [說明] 按鈕是**IDHELP** (9)。  
  
-   隱藏 [說明] 按鈕時，對話方塊看起來正確。  
  
-   對話方塊不會取代其 winproc。  
  
-   對話方塊不會內嵌在另一個對話方塊內。  
  
 如果您的對話方塊內 msenv 位於，而且不會使用**VBDialogBoxParam**，調查運用**VBDialogBoxParam**實作您自己的處理常式之前。  
  
##### <a name="dialogs-created-through-other-packages"></a>透過其他封裝建立的對話方塊  
 您可以實作自己的解決方案位於 msenv 之外的對話方塊。 在 VSPackage 中共用的對話方塊類別，請考慮將按鈕移至標題列，或實作每個對話方塊上的處理常式。 下列程式碼是要幫助您開始實作的基本架構：  
  
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
  
##### <a name="help-buttons-in-managed-code"></a>Managed 程式碼中的 [說明] 按鈕  
 覆寫視窗標題列說明按鈕的預設行為是以 managed 程式碼輕鬆。 以下是完整的範例應用程式，示範此行為。 基本上，您需要覆寫您的表單**WndProc**方法，然後引發 F1 說明關閉要求時**SC_CONTEXTHELP**攔截訊息。  
  
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
 [字型及格式設定適用於 Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [適用於 Visual Studio 的版面配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [適用於 Visual Studio 的通知和進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)