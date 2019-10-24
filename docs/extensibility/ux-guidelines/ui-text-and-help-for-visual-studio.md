---
title: Visual Studio 的 UI 文字和說明 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0477a0e1994e9c3b94df13ace4c1f3b4df51039
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748960"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Visual Studio 的 UI 文字和說明
## <a name="BKMK_UITextAndTerminology"></a>UI 文字與術語
 理解文字對於有效的 UI 很重要。 軟體使用者通常會先讀取標籤，也就是最適合用來完成工作的人。 以較少的頻率讀取靜態文字。 為使用者規劃啟動其工作會話，快速掃描整個視窗，然後依照這份近似的順序讀取 UI：

1. 中央的互動式控制項

2. 認可按鈕

3. 在別處找到互動式控制項

4. 主要指示

5. 補充說明

6. 視窗標題

7. 主要主體中的其他靜態文字

### <a name="usage-patterns-for-ui-text"></a>UI 文字的使用模式

#### <a name="title-bar-text"></a>標題列文字
 標題列文字必須符合產生 UI 的命令。

#### <a name="instructional-text-helper-text"></a>教學文字（helper text）
 在某些對話方塊中，提供顯著的主要指示來說明要在視窗或頁面中執行的動作，會很有説明。 這有時稱為「協助程式文字」。

##### <a name="writing-style-rules-for-helper-text"></a>撰寫 helper 文字的樣式規則

- 不要解釋明顯的。 除非絕對需要，否則請勿包含教學文字。

- 教學文字一律會放在對話方塊的頂端，而且應該參考所執行的工作。

- 準確地向使用者說明他們需要執行的工作。 避免過度通訊和重複。

- 請檢查每個視窗，並消除重複的單字和語句。

- 保持簡短的解說文字。 如需特定使用者或案例的詳細資訊，請提供詳細概念線上主題的連結。

- 撰寫文字，讓每個字都持有權數，而且是必要的。

- 遵循現有的 Microsoft 指引來取得[使用者介面文字](/windows/desktop/uxguide/text-ui)和[樣式和音調](/windows/desktop/uxguide/text-style-tone)。

#### <a name="supplemental-instructions"></a>補充指示
 補充指示提供可協助使用者瞭解控制項或控制群組的其他資訊。 這也可能包含瞭解輸入控制項所預期格式所需的提示文字。 請謹慎使用增補指示。 當使用者可能無法完全瞭解所做的選擇時，請將它們保留起來。

 ![Visual Studio 中的補充文字](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Visual Studio 中的補充文字**

 ![Visual Studio 中的補充文字](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Visual Studio 中的補充文字**

#### <a name="infotips"></a>提示
 通常，教學文字可能太長而無法放入 UI 中，或可能只對新使用者很有用，覺得對經驗豐富的使用者感到雜亂。 在此情況下，教學/資訊文字應該放在資訊提示底下做為工具提示。

 提示應該放在與它們相關的控制項附近，而且應該使用特定的 [提示] 圖示，這是不顯眼但明顯的。

 ![Visual Studio 中的提示](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio 中的提示範例**

##### <a name="writing-style-rules-for-infotips"></a>撰寫提示的樣式規則

- 以完整句子的形式撰寫提示。 它們需要特定的動詞、句子大小寫和結束標點符號。

- 使用提示來補充您的主要指示或資訊。 如果您只是使用不同的單字來重新聲明主要的想法，就不需要提示。

- 讓提示保持簡短且非常棒。 使用支援和鼓勵使用者的小型單字和一般、日常語言。

- 遵循現有的 Microsoft 指引來取得[使用者介面文字](/windows/desktop/uxguide/text-ui)和[樣式和音調](/windows/desktop/uxguide/text-style-tone)。

#### <a name="control-labels"></a>控制項標籤
 控制項標籤應該簡短、簡潔，並遵循[Windows 桌面的控制項指引](/windows/desktop/uxguide/controls)。

 如需 UI 內控制項標籤格式和位置的詳細資訊，請參閱[Visual Studio 的版面](../../extensibility/ux-guidelines/layout-for-visual-studio.md)配置。

#### <a name="help-links"></a>說明連結
 說明連結可以放在教學文字或 UI 的主體中。 它們可以是 [說明] 或 [啟動內部] 對話方塊的連結。

##### <a name="visual-style-rules-for-help-links"></a>說明連結的視覺化樣式規則

- 針對超連結，請使用正確的環境色彩。 在按下時，適當樣式的超連結將不會短暫閃爍紅色。 如果您看到此情況，則表示未使用環境色彩。

- 底線應該僅用於滑鼠停留，或連結內嵌在段落中。

- 如需有關超連結之視覺效果和互動樣式的詳細資訊，請參閱按鈕和超連結。

##### <a name="writing-style-rules-for-help-links"></a>撰寫說明連結的樣式規則

- 啟動對話時，請維護省略號的標準：如果工作需要其他 UI，則不會有任何省略號用於導覽，橢圓形則為省略號。

     ![Visual Studio 中的說明連結](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **[說明] 連結中的省略號（...）表示工作將需要其他 UI。**

- 連結不應以「學習」開頭，因為這不是使用者的意圖。 使用者想要回答特定問題，而不是收到一般教育。

- 片語說明連結，讓他們詢問主題將回答的問題。

     不正確：「深入瞭解 Windows Azure Mobile Services 定價」

     正確：「Windows Azure 行動服務有哪些可用的定價選項？」

- 永遠不要使用 [*按一下 ...* ] 連結文字。

- 絕對不要只連結「這裡」這個字。 這對某些螢幕閱讀程式會造成問題，這只會以超連結的字組來語音。

     不正確：「在**這裡**尋找 Windows Azure 行動服務的資訊」

     正確：「Windows Azure 行動服務有哪些可用的定價選項？」

- 如需說明連結正確書寫樣式的詳細資訊，請參閱[Windows 桌面指引以取得協助](/windows/desktop/uxguide/winenv-help)。

#### <a name="hint-text"></a>提示文字
 提示文字會顯示為控制項內或控制項底下的浮水印。 使用適當的 VSColors token （`Environment.GrayText`）將會套用正確的格式。

 它可以出現在數種形式中。

- 取代控制項標籤：

     ![Visual Studio 中的提示文字](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- 使用動詞，提供指示：

     ![Visual Studio 中的提示文字](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- 包含表示必要專案的文字：

     ![Visual Studio 中的提示文字](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>浮水印文字
 在空白的設計介面上，文字應該會指出要執行的動作，以及提供連結來開啟其他相關視窗（如果適用的話）：

 ![Visual Studio 中的浮水印文字](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Visual Studio 中的浮水印文字範例**

### <a name="common-terminology"></a>常見術語

|詞彙|說明|註解|
|----------|-----------------|-------------|
|登入/登出|動詞使用同義搭配 web 來代表 web 屬性中的驗證。 在用戶端中，我們使用此一次做為登入和退出 IDE 使用者連線的最上層概念，這代表最上層的身分識別，可提供其他連線無法使用的更高層級功能，例如漫遊和授權。|IDE 使用者是唯一應該代表登入/登出動詞的功能，因為它代表最上層的 IDE 使用者。|
|連線/中斷連接|用於功能維護與線上服務之單一連線的位置。|伺服器總管，您一次只能有一個作用中的 Azure 連線，這是連接/中斷連線的範例。|
|新增/移除|不具破壞性。 新增或移除清單中的某個專案時使用。|[TFS 連線管理員伺服器清單] 對話方塊是 [新增/移除] 的範例。|
|刪除|毀滅性. 只有在移除的元素將從磁片永久捨棄或刪除時，才使用。|如果結果是從磁片刪除檔案，則「刪除」通常需要提示。|

## <a name="error-messages"></a>錯誤訊息

### <a name="overview"></a>總覽
 發生錯誤。 設定使用者可以執行之動作的限制，是防止肇因錯誤訊息的一個合理第一個步驟。 不過，當發生錯誤時，撰寫妥善的錯誤訊息可能會很長，以減輕問題。 錯誤訊息可以是使用者所看到的最重要通知類型之一，因為它們是同步的，並且表示需要解決的問題。 撰寫不良的錯誤訊息會讓使用者自行決定錯誤的原因，以及任何可能的解決方案。

 使用者可能會停止注意過度處理或令人困惑的錯誤訊息，因此只需撰寫將值加入至使用者體驗的必要訊息。 如果訊息只是通知，請使用替代的簡報。

### <a name="rules-for-creating-an-error-message"></a>建立錯誤訊息的規則

- 當您建立錯誤訊息時，請為物件選擇適當的錯誤層級。 適用于提供使用者可採取之動作的簡單摘要（如果有的話）。 不要陳述使用者不需要知道的任何專案。

- 提供建設性的協助。 您可以更輕鬆地讀取並採取包含指令的錯誤訊息。

- 請勿使用雙重否定。

- 針對您所撰寫的任何錯誤訊息，執行自動化和手動的文法和拼寫檢查。

- 如需複雜的錯誤訊息，請避免順序通訊。 不要針對錯誤訊息使用 F1 的連結。 訊息本身應該就足夠了。

- 請使用正確的圖示。

- 讓問題容易瞭解，並使用有清楚選擇的按鈕，例如「刪除」和「取消」。

- 針對警告，請清楚瞭解繼續進行的結果。 這些按鈕應該會指出結果。

- 如有任何錯誤，請說明使用者可以執行哪些動作來修正問題。 按鈕應該是動作或說「關閉」。 請不要使用 [確定] 按鈕來顯示錯誤訊息。

- 當您在建立錯誤訊息時，要詢問自己的一些問題：

  - 使用者是否可以判斷如何單獨解決此錯誤的問題？

  - 使用者是否使用與此錯誤相同的詞彙？

  - 此錯誤在多個情況下模棱兩可或共用？ 若是如此，您要如何引導使用者完成所需的解決方案？

#### <a name="build-errors"></a>建置錯誤
 因為 Visual Studio 是軟體發展工具，所以它的許多元件都有編譯、轉換或編碼步驟，可將開發人員的工作轉換成二進位格式。 當編譯器無法處理不正確撰寫的檔案，或編譯器選項未正確設定時，這些轉換可能會導致錯誤。

 Visual Studio 使用者可以花費大量的開發時數來解決組建錯誤。 當錯誤有相依性，或錯誤訊息寫入不當時，這個解決時間就會增加，因此難以發現錯誤的來源。

 最佳的組建錯誤就是不會發生的問題，這就是 Visual Studio 提供自動完成和 IntelliSense 波浪線的原因。 架構驗證程式和類似的工具提供了相同類型的意見反應。 這些機制會主動引導使用者建立格式正確的程式碼，減輕發生組建錯誤的機會。

 Visual Studio 提供一個工具視窗，使用者可以在其中閱讀並流覽其文件視窗中發生的錯誤。 提供鍵盤快速鍵，讓使用者可以快速流覽大量的程式碼，並直接移至問題的位置。 Visual Studio 也可以讓每個組建錯誤系結至特定的 Help 關鍵字/內容識別碼，讓使用者可以直接前往說明主題，提供有關錯誤的更深入資訊。

 撰寫清楚明瞭的組建錯誤：

- **使用純語言**來說明幾乎不含編譯器術語的問題。 組建錯誤的文字不應過度技術性。

- **概述可能的原因。** 例如，「（屬性）：（值） ' 宣告」中的屬性與值之間遺漏了冒號。

- 提供有關可能修正程式的詳細資料。 如果沒有足夠的空間，則可能會在對應的說明主題中加入其他詳細資料。

### <a name="components-of-a-well-written-error-message"></a>妥善撰寫錯誤訊息的元件

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>使用 shell 對話服務來取得錯誤訊息。
 使用 shell 對話方塊服務可讓您控制訊息的外觀，特別是字型，而不會對個別元素進行重大變更。 使用**IErrorInfo**機制，並使用**IVsUIShell：： SetErrorInfo/ReportErrorInfo**加以報告。

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>選擇有效且適當的通知簡報。
 如果需要立即採取動作來避免資料遺失（同步通知），請使用強制回應對話方塊與重大警告。 重要圖示會保留給關閉訊息而不讀取的情況，可能會造成負面後果。 遺失資料是需要警示層級回應的重大情況。 過度利用重要圖示 desensitizes 使用者的重要性。 如果錯誤訊息是本質上的資訊，請考慮使用強制回應對話方塊（非同步通知）的替代方案。

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>針對發生問題的原因提供清楚明瞭的說明，而不是技術說明。
 在說明中造成具有技術詳細資料的使用者，會使它們更容易忽略錯誤訊息。 良好訊息的範例：

- 「無法開啟要求的檔案。」

- 「無法連接到網際網路」。

#### <a name="provide-information-about-how-to-fix-the-problem"></a>提供如何修正問題的相關資訊。
 提供如何修正問題的使用者建議。 如果沒有任何建議，請與使用者誠實。 提供其他線上來源的直接連結，例如技術支援或社區支援。 嘗試將使用者指向與問題相關的特定線上資訊。 針對錯誤識別碼，請考慮將使用者連結到有關該特定錯誤的討論話題。 良好訊息的範例：

- 「請確定您已連線到網際網路，然後再試一次此操作。」

- 「請確定檔案存在，而且您有開啟它的許可權。」

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>撰寫簡短且指向該點的訊息。
 錯誤訊息可以通知、說明及提供解決方案，但如果太冗長，仍會予以忽略。 其中一個解決方案是使用漸進式洩漏和 [詳細資料] 按鈕。 例如，提供簡短的描述/解決方案，然後在 [詳細資料] 按鈕底下放入更多詳細資料。 如果使用者選擇閱讀有關錯誤的詳細資訊，他們就可以這麼做。

 訊息中的語言應該是：

- **適用網域。** 使用使用者將瞭解的語言。 即使我們的客戶是開發人員，他們通常不會擁有我們所擁有的內容和術語。

- **特殊.** 避免模糊用語，並提供相關物件的特定名稱和位置。 例如，「字元無效」之類的錯誤訊息並不實用。 哪一個字元？ 「找不到檔案。」 哪個檔案？

- **不致.** 不要讓使用者感到愚蠢，也不要使他們覺得不容易。 避免惡意或冒犯性的語言（kill、execute、terminate、嚴重、不合法）。 避免大寫文字，這通常會被視為 shouting，而且無法讀取。 請勿使用幽默。

- **正確性.** 請使用正確的拼寫和文法（即使是在 Alpha 中）。 錯誤的不夠專業和尷尬。

- **內容適當的。** 使用適當的按鈕文字。 請避免使用 [確定] 按鈕，並改用 [繼續] 或 [是/否]。

### <a name="error-message-examples"></a>錯誤訊息範例

|好|形象|
|----------|---------|
|「您所撥的號碼已不再處於服務中。 請檢查號碼，然後重新撥號，或撥打0作為操作員。」|-「錯誤（449）：不合法的數位」<br />-「此未處理的例外狀況錯誤表示作業已成功完成。」<br /><br /> ![Visual Studio 中的錯誤訊息](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog ")|

## <a name="accessing-help"></a>存取說明

### <a name="overview"></a>總覽
 除了 MSDN 中的檔之外，Visual Studio 的使用者在 UI 中有數個存取點可協助使用者。 為確保這些存取點一致使用，功能小組必須利用環境所提供的說明系統。 這些存取點包括：

- **對話方塊中的說明和補充文字。** 提供方向或說明的靜態文字，可以在 UI 介面上，或在滑鼠停留在資訊提示圖示上時提供。

- **F1**說明（僅限編輯器）。 在 [Visual Studio 編輯器] 中，使用者隨時都可以信任，按下 F1 會顯示目前選取範圍特有的說明主題。 確定與 F1 相關聯的主題是適當且有資訊的。

- **說明主題的超連結。** 對話方塊、工具視窗或設計介面中的超連結，可啟動主題以協助使用者深入瞭解技術、功能或如何完成工作的相關資訊。

- **Helper UI 機制，例如智慧標籤和建立對話方塊。** 這些機制會協助使用者瞭解 UI 元素，或加速工作，例如智慧標籤或產生器對話方塊。

- **UI 說明按鈕**（已被取代）。 標題列中的可見指標，可讓您存取相關的 F1 說明主題。

### <a name="text"></a>Text

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>對話方塊中的說明和補充文字
 在支援複雜工作的對話方塊中，可能需要在 UI 中提供指示文字，通常是在對話的頂端或接近複雜的控制項。 如需撰寫樣式的詳細資訊，請參閱[UI 文字和詞彙](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。

#### <a name="infotips"></a>提示
 通常，解說文字可能太長，無法放在 UI 中，或可能只對新使用者很有用，覺得對經驗豐富的使用者感到雜亂。 在此情況下，教學/資訊文字應該放在資訊提示底下做為工具提示。

 提示應該放在與它們相關的控制項附近，而且應該使用特定的 [提示] 圖示，這是不顯眼但明顯的。

 ![Visual Studio 中的提示](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio 中的提示範例**

### <a name="interactive-help-mechanisms"></a>互動式說明機制

#### <a name="f1-help"></a>F1 說明
 在編輯器或設計介面中，但在 Visual Studio 環境中的其他位置，則需要 F1 說明。

#### <a name="hyperlinks-to-help-topics"></a>說明主題的超連結
 超連結可以用來執行動作、在 IDE 內導覽，或在瀏覽器中啟動說明。 如需視覺效果和版面配置指導方針的語言和07.10.01 按鈕和超連結的詳細資訊，請參閱[UI 文字和詞彙](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>對話方塊標題列中的說明 [？] 按鈕（已被取代）
 在大部分的情況下，對話方塊標題列中的 [說明] [？] 按鈕已被取代。 UI 主題已不再是我們的檔模型的一部分，因此可能不會有相關的主題可連結至。 基本上，標題列按鈕與 F1 說明相同，而且在對話方塊中已不再需要。 在某些情況下，這仍然可以用來表示有更多概念或程式資訊可用，雖然較新的 UI 中較常使用超連結。

##### <a name="dialogs-created-through-the-environment"></a>透過環境建立的對話方塊
 許多 shell 對話方塊是透過**VBDialogBoxParam**函數所建立。 已更新此共用函式，以協助將 **[說明] 按鈕從**對話方塊移至 **？** 按鈕，同時保留可回溯相容和可擴充的架構。

 具體來說， **VBDialogBoxParam**函式會查看其 ID 為**IDHELP** （9）或卷**標為 [** 說明] 或 [ **&** 說明] 之按鈕的對話方塊範本。 如果找到 [說明] 按鈕，它會被隱藏，而**WS_EX_CONTEXTHELP**樣式會加入至對話方塊，這會放置 **？** 按鈕，在對話方塊的標題列中。

 建立對話方塊時，它會將對話進程推送至堆疊上，並使用名為**DialogPreProc**的前置處理對話方塊處理器叫用對話方塊。 當 **？** 按一下按鈕時，它會將**SC_CONTEXTHELP**的**WM_SYSCOMMAND**傳送至對話方塊。 **DialogPreProc**會捕捉此命令，並將它變更為**WM_HELP**訊息，傳遞至原始對話進程。

 大部分的環境建立對話方塊在對話方塊上都有 [說明] 按鈕。 當對話方塊出現時，[說明] 按鈕會自動隱藏，而且只會顯示 [ **？** ] 按鈕可運作。 如果 **？** 按鈕已在 Windows 中移除或變更，此解決方案可讓您快速切換回原始的 [說明] 按鈕。

 此解決方案會做出四個可能造成錯誤的假設：

- 對話方塊的 [說明] 按鈕是**IDHELP** （9）。

- 隱藏 [說明] 按鈕時，對話方塊會顯示正確。

- 對話方塊不會取代它的 winproc。

- 對話方塊不會內嵌在另一個對話方塊中。

  如果您的對話位於 msenv 中，而不使用**VBDialogBoxParam**，請先調查利用**VBDialogBoxParam** ，再執行自己的處理常式。

##### <a name="dialogs-created-through-other-packages"></a>透過其他封裝建立的對話方塊
 您可以針對位於 msenv 外部的對話方塊，執行自己的解決方案。 針對 VSPackage 中的共用對話方塊類別，請考慮將按鈕移至標題列，或在每個對話方塊上執行處理常式。 下列程式碼是可協助您開始使用的實作為基本架構：

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

##### <a name="help-buttons-in-managed-code"></a>Managed 程式碼中的說明按鈕
 在 managed 程式碼中，覆寫視窗標題列 [說明] 按鈕的預設行為很容易。 以下是示範此行為的完整示範應用程式。 基本上，您必須覆寫表單的**WndProc**方法，然後在攔截**SC_CONTEXTHELP**訊息時，引發 F1 說明要求。

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

## <a name="see-also"></a>請參閱
- [適用於 Visual Studio 的字型和格式設定](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [適用於 Visual Studio 的配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [適用於 Visual Studio 的通知和進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
