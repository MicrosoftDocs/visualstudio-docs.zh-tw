---
title: Visual Studio 的 UI 文字和說明 |Microsoft Docs
description: 瞭解 Visual Studio 的說明資訊中所使用的 UI 文字和術語。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8635907b5c0190165855378fa692fb9abca4b0ec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105052654"
---
# <a name="ui-text-and-help-for-visual-studio"></a>適用於 Visual Studio 的 UI 文字和說明
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a> UI 文字和術語
 理解文字對有效的 UI 而言很重要。 軟體使用者通常會先讀取標籤，也就是最相關的標籤，以在手邊完成工作。 以較少的頻率讀取靜態文字。 規劃使用者使用整個視窗的快速掃描來啟動其工作會話，然後以這項近似順序讀取 UI：

1. 中心內的互動式控制項

2. 認可按鈕

3. 在其他地方找到互動式控制項

4. 主要指示

5. 補充說明

6. 視窗標題

7. 主體中的其他靜態文字

### <a name="usage-patterns-for-ui-text"></a>UI 文字的使用模式

#### <a name="title-bar-text"></a>標題列文字
 標題列文字必須符合產生 UI 的命令。

#### <a name="instructional-text-helper-text"></a> (helper text) 的解說文字
 在某些對話中，提供重要的主要指示來說明在視窗或頁面中要做什麼，會很有説明。 這有時稱為「協助程式文字」。

##### <a name="writing-style-rules-for-helper-text"></a>撰寫 helper 文字的樣式規則

- 請勿解釋明顯的。 除非絕對需要，否則請勿包含解說文字。

- 教學文字一定會放在對話的最上方，而且應該參考執行中的工作。

- 精確說明使用者需要進行的動作。 避免過度的通訊和冗余。

- 檢查每個視窗，並消除重複的單字和語句。

- 保持簡短的解說文字。 如果某些使用者或案例需要詳細資訊，請提供詳細概念線上主題的連結。

- 撰寫您的文字，讓每個單字都具有權數，而且是必要的。

- 遵循 [消費者介面文字](/windows/desktop/uxguide/text-ui) 和 [樣式和語氣](/windows/desktop/uxguide/text-style-tone)的現有 Microsoft 指引。

#### <a name="supplemental-instructions"></a>補充指示
 補充指示提供可協助使用者瞭解控制項或控制項群組的其他資訊。 這也可能包含必要的提示文字，以瞭解輸入控制項預期的格式。 請謹慎使用補充指示。 如果使用者可能無法完全瞭解所做選擇的後果，請將它們保留起來。

 ![顯示 [Internet Explorer 選項] 按鈕的螢幕擷取畫面，其中有補充文字，說明變更選項設定的影響。](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Visual Studio 中的補充文字**

 ![[選擇原始檔控制] 對話方塊的螢幕擷取畫面，其中 Visual Studio 顯示描述每個原始檔控制系統選項的補充文字。](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Visual Studio 中的補充文字**

#### <a name="infotips"></a>提示
 通常，解說文字可能太長，而無法就地放置在 UI 中，或可能只對新使用者很有用，而感覺像是有經驗的使用者。 在此情況下，教學/資訊文字應該放在資訊提示底下作為工具提示。

 提示應放置在與其相關的控制項附近，而且應該使用特定的 [提示] 圖示，這並不顯眼但明顯。

 ![Visual Studio 中的資訊提示](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio 中的提示範例**

##### <a name="writing-style-rules-for-infotips"></a>撰寫提示的樣式規則

- 將提示撰寫成完整的句子。 它們需要特定的動詞、句子大小寫和結束標點符號。

- 使用提示來補充您的主要指示或資訊。 如果您只是使用不同的單字來重新聲明主要的概念，就不需要提示。

- 保持提示的簡短和最佳。 使用支援和鼓勵使用者的小型單字和純文字語言。

- 遵循 [消費者介面文字](/windows/desktop/uxguide/text-ui) 和 [樣式和語氣](/windows/desktop/uxguide/text-style-tone)的現有 Microsoft 指引。

#### <a name="control-labels"></a>控制項標籤
 控制項標籤應該簡短、簡潔，並遵循 [Windows 桌面的控制項指引](/windows/desktop/uxguide/controls)。

 如需有關 UI 內控制項標籤格式和位置的詳細資訊，請參閱 [Visual Studio 的版面](../../extensibility/ux-guidelines/layout-for-visual-studio.md)配置。

#### <a name="help-links"></a>說明連結
 說明連結可以放在教學文字或 UI 主體內。 它們可以是協助或啟動內部對話的連結。

##### <a name="visual-style-rules-for-help-links"></a>說明連結的視覺化樣式規則

- 針對超連結使用正確的環境色彩。 按一下時，正確樣式的超連結將不會短暫地閃爍。 如果您看到這種情況，則表示未使用環境色彩。

- 底線應僅用於滑鼠停留，或在連結內嵌于段落時使用。

- 如需有關超連結的視覺效果和互動樣式的詳細資訊，請參閱按鈕和超連結。

##### <a name="writing-style-rules-for-help-links"></a>撰寫說明連結的樣式規則

- 當啟動對話方塊時，請維持省略號的標準：如果工作需要額外的 UI，則不會有任何省略號用於導覽，省略號。

     ![Visual Studio 中的 [說明] 連結](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **說明連結中的省略號 ( ... ) 指出工作將需要額外的 UI。**

- 連結不能以「學習」開頭，因為這不是使用者的意圖。 使用者想要回答特定問題，而不是獲得一般教育。

- 片語說明連結，讓他們詢問主題將回答的問題。

     不正確：「深入瞭解 Windows Azure Mobile Services 定價」

     正確：「Windows Azure 行動服務有哪些定價選項？」

- 請勿使用 [ *按一下 ...* ] 連結文字。

- 絕對不要連結 "here" 這個字。 這對某些螢幕讀取器而言是有問題的，因此只會以超連結的文字為語音。

     不正確：「在 **此** 尋找有關 Windows Azure Mobile Services 的資訊」

     正確：「Windows Azure 行動服務有哪些定價選項？」

- 如需說明連結正確書寫樣式的詳細資訊，請參閱 [Windows 桌面指引以取得協助](/windows/desktop/uxguide/winenv-help)。

#### <a name="hint-text"></a>提示文字
 提示文字會顯示為控制項內或控制項下方的浮水印。 將會使用適當的 VSColors token 來套用正確的格式設定 `Environment.GrayText` 。

 它可以出現在許多表單中。

- 取代控制項標籤：

     ![下拉式控制項的螢幕擷取畫面，其中包含 [搜尋方案總管 (Ctrl +; ) ] 控制項標籤的提示文字。](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- 使用動詞，提供指示：

     ![在控制項中顯示「輸入您的名稱」之提示文字的文字方塊螢幕擷取畫面。](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- 具有指出必要專案的文字：

     ![螢幕擷取畫面：控制項中的提示文字會顯示為「必要」 \< \> 。](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>浮水印文字
 在空白設計介面上，文字應該會指出要執行的動作，以及提供連結來開啟其他相關視窗（如果有的話）：

 ![Visual Studio 中的浮水印文字](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Visual Studio 中的浮水印文字範例**

### <a name="common-terminology"></a>常見術語

|詞彙|說明|註解|
|----------|-----------------|-------------|
|登入/登出|使用同義搭配 web 的動詞，以將驗證表示至 web 屬性。 在用戶端中，我們會使用這一次作為登入和退出 IDE 使用者連線的最上層概念，這代表最上層的身分識別，可提供較高層級的功能，例如無法與其他所有連線一起使用的漫遊與授權。|IDE 使用者是唯一應該代表登入/登出動詞的功能，因為它代表最上層的 IDE 使用者。|
|連線/中斷連接|在功能維護單一連接至線上服務的地方使用。|伺服器總管，您一次只能有一個作用中的 Azure 連線，就是連線/中斷連接的範例。|
|新增/移除|非破壞性。 在清單中新增或移除某個內容時使用。|[TFS 連線管理員伺服器清單] 對話方塊是 [新增/移除] 的範例。|
|刪除|破壞性。 只有在移除的元素將從磁片永久捨棄或刪除時，才使用。|如果結果是從磁片刪除檔案，則 [刪除] 通常需要提示。|

## <a name="error-messages"></a>錯誤訊息

### <a name="overview"></a>概觀
 發生錯誤。 設定使用者可執行之動作的限制，是防止肇因錯誤訊息的第一個步驟。 不過，當發生錯誤時，妥善撰寫的錯誤訊息可能會很長的方法來緩和問題。 錯誤訊息是使用者看到的最重要通知類型之一，因為它們是同步的，且表示需要解決的問題。 撰寫不當的錯誤訊息會讓使用者自行決定錯誤的原因，以及任何可能的解決方案。

 使用者可能會停止注意過度使用或令人困惑的錯誤訊息，因此只會撰寫必要的訊息，以增加使用者體驗的價值。 如果訊息只是通知，則使用替代的簡報。

### <a name="rules-for-creating-an-error-message"></a>建立錯誤訊息的規則

- 當您建立錯誤訊息時，請為物件選擇適當的錯誤層級。 以簡單的摘要為目標，提供使用者可採取的動作（如果適用）。 請勿陳述使用者不需要知道的任何事項。

- 提供建設性的協助。 您可以更輕鬆地讀取和處理包含指令的錯誤訊息。

- 請勿使用雙否定。

- 針對您所撰寫的任何錯誤訊息，執行自動和手動文法及拼寫檢查。

- 針對複雜的錯誤訊息，請避免順序通訊。 請勿針對錯誤訊息使用 F1 的連結。 訊息本身應該就已足夠。

- 使用正確的圖示。

- 讓您輕鬆瞭解問題，並使用具有明確選擇的按鈕，例如 [刪除] 和 [取消]。

- 針對警告，請清楚瞭解繼續的結果。 按鈕應該會指出結果。

- 如有錯誤，請說明使用者可以如何解決問題。 按鈕應該是動作，或說「關閉」。 請勿使用 [確定] 按鈕來取得錯誤訊息。

- 當您建立錯誤訊息時，需要自問一些問題：

  - 使用者可以找出如何單獨解決這個錯誤的問題嗎？

  - 使用者是否使用與此錯誤相同的詞彙？

  - 此錯誤在多個情況下模棱兩可或共用嗎？ 如果有，您要如何引導使用者前往所需的解決方案？

#### <a name="build-errors"></a>建置錯誤
 由於 Visual Studio 是軟體發展工具，因此它的許多元件都有編譯、轉換或編碼步驟，可將開發人員的工作轉換成二進位格式。 當編譯器無法處理不當撰寫的檔案，或編譯器選項未正確設定時，這些轉換可能會造成錯誤。

 Visual Studio 使用者可以花大量的開發時間來解決組建錯誤。 當錯誤具有相依性，或錯誤訊息寫入不良時，此解決時間會增加，這可能會導致難以找出錯誤的來源。

 最佳的組建錯誤就是不會在第一次發生的錯誤，這也是 Visual Studio 提供自動完成和 IntelliSense 波浪線的原因。 架構驗證程式和類似的工具提供相同類型的意見反應。 這些機制會主動引導使用者建立格式正確的程式碼，減輕組建錯誤的機率。

 Visual Studio 提供一個工具視窗，讓使用者可以在其檔視窗中讀取和流覽發生的錯誤。 系統會提供鍵盤快速鍵，讓使用者可以快速流覽大量的程式碼，並直接移至問題的位置。 Visual Studio 也可讓每個組建錯誤都系結至特定的說明關鍵字/內容識別碼，讓使用者可以直接前往說明主題，以提供更深入的錯誤相關資訊。

 撰寫明確、精確的組建錯誤：

- **使用簡單** 或無編譯器術語的一般語言來說明問題。 組建錯誤的文字應該不太技術性。

- **概述可能的原因。** 例如，' (屬性中的屬性與值之間遺漏了冒號) ： (值) ' 宣告」。

- 提供有關潛在修正的詳細資料。 如果沒有足夠的空間，則可能會將其他詳細資料放入對應的說明主題。

### <a name="components-of-a-well-written-error-message"></a>妥善撰寫的錯誤訊息的元件

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>使用 shell 對話服務來取得錯誤訊息。
 使用 shell 對話服務可讓您控制訊息的外觀，特別是在沒有個別元素的重大變更的情況下使用字型。 使用 **IErrorInfo** 機制，並使用 **IVsUIShell：： SetErrorInfo/ReportErrorInfo** 來報告這些機制。

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>選擇有效且適當的通知展示。
 如果需要立即動作以避免資料遺失 (同步通知) ，請使用具有重大警告的強制回應對話方塊。 重要圖示會保留在未讀取訊息的情況下，可能會造成負面的後果。 遺失資料是需要警示層級回應的重要情況。 過度利用重要圖示 desensitizes 使用者的重要性。 如果錯誤訊息的本質僅供參考，請考慮使用強制回應對話方塊的替代方案， (非同步通知) 。

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>提供簡潔明瞭的原因，說明為何發生問題，而不是技術說明。
 在說明中造成具有技術詳細資料的使用者，可讓他們更有可能忽略錯誤訊息。 良好訊息的範例：

- 「無法開啟要求的檔案。」

- 「無法連接到網際網路」。

#### <a name="provide-information-about-how-to-fix-the-problem"></a>提供如何修正問題的相關資訊。
 提供如何修正問題的使用者建議。 如果沒有任何建議，請與使用者誠實。 提供其他線上來源的直接連結，例如技術支援或社區支援。 請嘗試將使用者指向與問題相關的特定線上資訊。 針對錯誤識別碼，請考慮將使用者連結到有關該特定錯誤的討論主題。 良好訊息的範例：

- 「請確定您已連線到網際網路，然後再試一次此操作」。

- 「請確定檔案存在，而且您有開啟檔案的許可權。」

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>撰寫簡短且指向該點的訊息。
 錯誤訊息可以通知、解釋和提供解決方案，但如果冗長太過，仍會予以忽略。 其中一個解決方法是使用 [漸進式洩漏] 與 [詳細資料] 按鈕。 例如，提供簡短的描述/方案，然後在 [詳細資料] 按鈕下放置更多詳細資料。 如果使用者選擇閱讀有關錯誤的詳細資訊，他們可以這樣做。

 訊息中的語言應該是：

- **適用網域。** 使用使用者將瞭解的語言。 雖然我們的客戶是開發人員，但它們通常沒有我們所擁有的內容和術語。

- **特定。** 避免模糊的用語，並為相關的物件提供特定的名稱和位置。 例如，「字元無效」之類的錯誤訊息並不實用。 哪一個字元？ 「找不到檔案。」 哪個檔案？

- **禮貌。** 不要讓使用者感到安心，或讓他們覺得更愚蠢。 避免惡意或冒犯性的語言 (終止、執行、終止、嚴重、不合法) 。 避免大寫文字，這通常會被視為 shouting，而且不是可讀取的。 請勿使用幽默。

- **正確。** 即使在 Alpha) 中，也請使用正確的拼寫和文法 (。 輸入錯誤是不專業和尷尬。

- **內容適用。** 使用適當的按鈕文字。 請避免使用 [確定] 按鈕，並改為使用 [繼續] 或 [是/否]。

### <a name="error-message-examples"></a>錯誤訊息範例

|好|不良|
|----------|---------|
|「您撥打的號碼已不再處於服務中。 請檢查號碼，然後再按一次電話號碼，或撥打操作員撥打0。」|-"Error (449) ：不合法的數位"<br />-「此未處理的例外狀況錯誤表示作業已順利完成。」<br /><br /> ![Visual Studio 中錯誤的錯誤訊息](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>存取說明

### <a name="overview"></a>概觀
 除了 MSDN 中的檔之外，Visual Studio 使用者還有數個存取點，可在 UI 中協助使用者。 為了確保這些存取點一致地可用，功能小組需要利用環境所提供的說明系統。 這些存取點包括：

- **對話中的教學和補充文字。** 提供方向或說明的靜態文字，無論是在 UI 介面上，或是在資訊提示圖示上停留時都可以使用。

- **F1** 說明 (編輯器只) 。 在 [Visual Studio 編輯器] 中，使用者可以隨時信任該專案，按下 F1 將會顯示目前選取範圍的特定說明主題。 確定與 F1 相關聯的主題都適當且有資訊。

- **說明主題的超連結。** 對話方塊、工具視窗或設計介面內的超連結，可啟動主題以協助使用者深入瞭解如何完成工作的相關技術、功能或資訊。

- **Helper UI 機制，例如智慧標籤和建立對話方塊。** 這些機制協助使用者瞭解 UI 元素，或協助工作，例如智慧標籤或產生器對話方塊。

- **UI 說明按鈕** (已淘汰的) 。 標題列中的可見指標，可讓您存取相關的 F1 說明主題。

### <a name="text"></a>Text

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>對話方塊中的教學和補充文字
 在支援複雜工作的對話方塊中，可能需要在 UI 中提供解說文字，通常是在對話方塊頂端或接近複雜的控制項。 如需撰寫樣式的詳細資訊，請參閱 [UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 。

#### <a name="infotips"></a>提示
 通常，解說文字可能太長，而無法就地放置在 UI 中，或可能只對新使用者很有用，而感覺像是有經驗的使用者。 在此情況下，教學/資訊文字應該放在資訊提示底下作為工具提示。

 提示應放置在與其相關的控制項附近，而且應該使用特定的 [提示] 圖示，這並不顯眼但明顯。

 ![Visual Studio 中的資訊提示](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio 中的提示範例**

### <a name="interactive-help-mechanisms"></a>互動式說明機制

#### <a name="f1-help"></a>F1 說明
 在編輯器或設計介面中需要 F1 說明，但 Visual Studio 環境中的其他地方則不需要。

#### <a name="hyperlinks-to-help-topics"></a>說明主題的超連結
 您可以使用超連結來執行動作、在 IDE 中流覽，或在瀏覽器中啟動 [說明]。 如需有關語言和07.10.01 按鈕的詳細資訊，以及視覺效果和版面配置方針的超連結，請參閱 [UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 。

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>對話方塊標題列中的 Help [？] 按鈕 (已淘汰) 
 在大部分的情況下，對話方塊標題列中的 [說明] 按鈕會被取代。 UI 主題不再是檔模型的一部分，因此可能不會有相關的主題連結。 基本上，標題列按鈕與 F1 說明相同，而且在對話方塊中不再需要。 在某些情況下，這仍然可以用來表示有更多可用的概念或程式資訊，但較常在較新的 UI 中使用超連結。

##### <a name="dialogs-created-through-the-environment"></a>透過環境建立的對話
 許多 shell 對話方塊都是透過 **VBDialogBoxParam** 函式所建立。 此共用函式已更新，可協助您 **將 [說明] 按鈕從** 對話方塊移至 **？** 按鈕，同時保留可回溯相容且可擴充的架構。

 具體來說， **VBDialogBoxParam** 函式會查看識別碼為 **IDHELP** (9 之按鈕的對話方塊範本，) 或標籤 **是 [** 說明] 或 [ **&協助**]。 如果找到 [說明] 按鈕，就會隱藏它，並將 **WS_EX_CONTEXTHELP** 樣式新增至對話方塊，以放置 **？** 按鈕（在對話方塊的標題列中）。

 建立對話方塊時，它會將對話程式推送至堆疊，並使用名為 **DialogPreProc** 的前置處理對話方塊程式來叫用對話方塊。 當 **？** 按一下按鈕，就會將 **SC_CONTEXTHELP** 的 **WM_SYSCOMMAND** 傳送給對話方塊。 **DialogPreProc** 會捕捉此命令，並將其變更為傳遞給原始對話程式的 **WM_HELP** 訊息。

 大部分環境建立的對話方塊都有對話方塊的 [說明] 按鈕。 顯示對話方塊時，[說明] 按鈕會自動隱藏，而只有 **？** 按鈕運作。 如果 **？** 按鈕會在 Windows 中移除或變更，此解決方案可讓您快速移回原始的 [說明] 按鈕。

 此解決方案會進行四個可能導致錯誤的假設：

- 對話方塊的 [說明] 按鈕 **IDHELP** (9) 。

- 隱藏 [說明] 按鈕時，對話方塊會顯示正確。

- 對話方塊不會取代其 winproc。

- 對話方塊不會內嵌在另一個對話方塊中。

  如果您的對話位於 msenv 內且未使用 **VBDialogBoxParam**，請在執行您自己的處理常式之前，先調查利用 **VBDialogBoxParam** 。

##### <a name="dialogs-created-through-other-packages"></a>透過其他套件建立的對話
 您可以針對位於 msenv 外部的對話，執行自己的解決方案。 針對 VSPackage 中的共用對話方塊類別，請考慮將按鈕移至標題列，或在每個對話方塊上執行處理常式。 下列程式碼是可協助您開始使用之實作為的基本架構：

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

##### <a name="help-buttons-in-managed-code"></a>受控碼中的說明按鈕
 在 managed 程式碼中，您可以輕鬆覆寫視窗標題列的 [說明] 按鈕的預設行為。 以下是示範此行為的完整示範應用程式。 基本上，您需要覆寫表單的 **WndProc** 方法，然後在攔截 **SC_CONTEXTHELP** 訊息時引發 F1 說明要求。

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
- [適用於 Visual Studio 的字型和格式設定](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [適用於 Visual Studio 的配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [適用於 Visual Studio 的通知和進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
