---
title: 視覺化工作室的 UI 文本和説明 |微軟文檔
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0477a0e1994e9c3b94df13ace4c1f3b4df51039
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303124"
---
# <a name="ui-text-and-help-for-visual-studio"></a>適用於 Visual Studio 的 UI 文字和說明
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a>UI 文本和術語
 可理解的文本對於有效的 UI 至關重要。 軟體使用者傾向于首先閱讀標籤，即與完成手頭任務最相關的標籤。 讀取靜態文本的頻率較低。 計畫使用者通過對整個視窗進行快速掃描來開始其工作會話，然後按以下近似順序讀取 UI：

1. 中間的互動式控制項

2. 提交按鈕

3. 在其他地方找到的互動式控制項

4. 主要說明

5. 補充說明

6. 視窗標題

7. 主體中的其他靜態文本

### <a name="usage-patterns-for-ui-text"></a>UI 文本的使用模式

#### <a name="title-bar-text"></a>標題列文本
 標題列文本必須與生成 UI 的命令匹配。

#### <a name="instructional-text-helper-text"></a>教學文本（説明文本）
 在某些對話方塊中，提供突出顯示的主要說明來解釋在視窗或頁面中應該怎麼做是很有説明的。 這有時稱為"説明者文本"。

##### <a name="writing-style-rules-for-helper-text"></a>説明器文本的編寫樣式規則

- 不要解釋顯而易見的事實。 除非絕對需要，否則不要包含教學文本。

- 指令文本始終放在對話方塊的頂部，並應引用正在執行的任務。

- 向使用者準確解釋他們需要做什麼。 避免過多的溝通和冗余。

- 查看每個視窗並消除重複的單詞和語句。

- 保持教學文本簡短。 如果某些使用者或方案需要更多資訊，則提供指向詳細概念連線主題的連結。

- 寫你的課文，使每個單詞都保持重量，是必要的。

- 按照現有的微軟使用者介面[文本](/windows/desktop/uxguide/text-ui)和[樣式和色調](/windows/desktop/uxguide/text-style-tone)的指導。

#### <a name="supplemental-instructions"></a>補充說明
 補充說明提供了其他資訊，可説明使用者瞭解控制項或控制分組。 這還可能包括必要的提示文本，以瞭解輸入控制項所需的格式。 請謹慎使用補充說明。 保留它們，以便使用者可能無法完全理解他們做出的選擇的後果。

 ![Visual Studio 中的補充文字](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Visual Studio 中的補充文字**

 ![Visual Studio 中的補充文字](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Visual Studio 中的補充文字**

#### <a name="infotips"></a>資訊提示
 通常，指令性文本可能太長，無法將位置放在 UI 中，或者可能僅對新使用者有用，對有經驗的使用者來說，這感覺雜亂無章。 在這種情況下，教學/資訊文本應作為工具提示放置在 InfoTip 下。

 InfoTips 應放置在它們相關的控制項附近，並且應該使用特定的 InfoTip 圖示，該圖示不顯眼但明顯。

 ![Visual Studio 中的資訊提示](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **視覺化工作室中的資訊提示示例**

##### <a name="writing-style-rules-for-infotips"></a>為資訊提示編寫樣式規則

- 將資訊提示寫成完整的句子。 它們需要特定的動詞、句子大小寫和結束標點符號。

- 使用資訊提示補充您的主要說明或資訊。 如果您只是使用不同的詞來重提主要想法，則不需要 InfoTip。

- 保持資訊提示簡短而甜美。 使用支援和鼓勵使用者的小單詞和普通的日常語言。

- 按照現有的微軟使用者介面[文本](/windows/desktop/uxguide/text-ui)和[樣式和色調](/windows/desktop/uxguide/text-style-tone)的指導。

#### <a name="control-labels"></a>控制標籤
 控制項標籤應簡短、簡潔，並遵循[控制項的 Windows 桌面指南](/windows/desktop/uxguide/controls)。

 有關控制項標籤格式和在 UI 中放置的詳細資訊，請參閱[視覺化工作室的佈局](../../extensibility/ux-guidelines/layout-for-visual-studio.md)。

#### <a name="help-links"></a>說明連結
 説明連結可以放置在教學文本中或 UI 正文中。 它們可以是指向"説明"或"啟動內部對話方塊"的連結。

##### <a name="visual-style-rules-for-help-links"></a>説明連結的可視樣式規則

- 對超連結使用正確的環境顏色。 正確樣式的超連結在按一下時不會短暫閃爍紅色。 如果看到這一點，則表示未使用環境顏色。

- 底線應僅在懸停或連結嵌入段落時使用。

- 有關超連結的可視樣式和交互樣式的更多詳細資訊，請參閱按鈕和超連結。

##### <a name="writing-style-rules-for-help-links"></a>為説明連結編寫樣式規則

- 啟動對話方塊時，維護橢圓的標準：沒有用於導航的橢圓，如果任務需要額外的 UI，則省略號。

     ![Visual Studio 中的 [說明] 連結](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **説明連結中的省略號 （...） 表示任務將需要其他 UI。**

- 連結不應以"學習"開頭，因為這不是使用者的意圖。 使用者希望回答特定問題，而不是接受普通教育。

- 短語説明連結，以便他們提出主題將回答的問題。

     不正確："瞭解有關 Windows Azure 移動服務定價的更多資訊"

     正確："Windows Azure 移動服務有哪些定價選項？

- 切勿使用 *"按一下..."* 連結文本。

- 切勿只連結"此處"一詞。 這對某些螢幕閱讀器來說是個問題，因為螢幕閱讀器將只發出超連結單詞的語音。

     不正確："**在此處**查找 Windows Azure 移動服務的資訊"

     正確："Windows Azure 移動服務有哪些定價選項？

- 有關説明連結的正確書寫樣式的詳細資訊，請參閱["説明"的 Windows 桌面指南](/windows/desktop/uxguide/winenv-help)。

#### <a name="hint-text"></a>提示文本
 提示文本在控制項內或控制項下方顯示為浮水印。 將使用相應的 VSColors 權杖應用正確的格式`Environment.GrayText`。

 它可以以多種形式顯示。

- 代替控制標籤：

     ![Visual Studio 中的提示文字](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- 用動詞，給出指示：

     ![Visual Studio 中的提示文字](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- 文本指示必需的條目：

     ![Visual Studio 中的提示文字](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>浮水印文本
 在空的設計介面上，文本應指明要執行哪些操作，並提供適當的連結以打開其他相關視窗：

 ![Visual Studio 中的浮水印文字](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **視覺工作室中的浮水印文本示例**

### <a name="common-terminology"></a>常用術語

|詞彙|說明|註解|
|----------|-----------------|-------------|
|登錄/登出|動詞與 Web 同義用於表示 Web 屬性中的身份驗證。 在用戶端中，我們一次使用此概念作為登錄和登出 IDE 使用者連接的頂級概念，該概念表示提供更高級別的功能（如漫遊和許可）的頂級標識，而所有其他連接都不可用。|IDE 使用者是唯一應表示登錄/登出謂詞的功能，因為它表示頂級 IDE 使用者。|
|連接/斷開連接|用於功能與聯機服務保持單個連接的位置。|伺服器資源管理器（一次只能有一個活動 Azure 連接）是連接/斷開連接的示例。|
|添加/刪除|無損。 從清單中添加或刪除內容時使用。|TFS 連線管理員伺服器清單對話方塊是添加/刪除的示例。|
|刪除|破壞性。 僅當要刪除的元素將被永久丟棄或從磁片中刪除時，才使用。|如果結果從磁片中刪除檔，則"刪除"通常需要提示。|

## <a name="error-messages"></a>錯誤訊息

### <a name="overview"></a>概觀
 會發生錯誤。 設置使用者可以做什麼的限制是防止可避免錯誤訊息的明智第一步。 但是，當發生錯誤時，編寫良好的錯誤訊息可以很好地緩解問題。 錯誤訊息可以說是使用者看到的最重要通知類型之一，因為它們是同步的，並且指示需要解決的問題。 編寫不良的錯誤訊息使使用者自行決定錯誤的原因和任何可能的解決方案。

 使用者可能會停止關注過度使用或混淆的錯誤訊息，因此只編寫為使用者體驗增加價值的必要消息。 如果消息只是通知，則使用備用演示文稿。

### <a name="rules-for-creating-an-error-message"></a>創建錯誤訊息的規則

- 構造錯誤訊息時，為訪問群體選擇適當的錯誤級別。 旨在獲取提供使用者可以執行的操作（如果適用）的簡單摘要。 不要說明使用者不需要知道的任何內容。

- 提供建設性援助。 閱讀和操作包含指令的錯誤訊息更容易。

- 不要使用雙底片。

- 對您編寫的任何錯誤訊息執行自動和手動語法和拼寫檢查。

- 對於複雜的錯誤訊息，請避免順序通信。 切勿對錯誤訊息使用 F1 連接。 消息本身應足夠。

- 使用正確的圖示。

- 使問題易於理解，並使用具有明確選擇的按鈕，如"刪除"和"取消"。

- 對於警告，要明確操作的後果。 按鈕應指示結果。

- 對於錯誤，請描述使用者可以採取哪些措施來解決此問題。 按鈕應該是操作或說"關閉"。 不要對錯誤訊息使用"確定"按鈕。

- 構造錯誤訊息時要問自己的一些問題：

  - 使用者能否單獨找出如何僅使用此錯誤解決問題？

  - 使用者是否使用此與此錯誤相同的詞彙表？

  - 此錯誤是大錯還是在多種情況下共用？ 如果是，您如何引導使用者找到他們需要的解決方案？

#### <a name="build-errors"></a>建置錯誤
 由於 Visual Studio 是一個軟體發展工具，因此其許多元件都有編譯、轉換或編碼步驟，可將開發人員的工作轉換為二進位形式。 當編譯器無法處理創作不當的檔或編譯器選項設置不正確時，這些轉換可能會導致錯誤。

 Visual Studio 使用者可以花費大量開發時間來解決建置錯誤。 當錯誤具有依賴關係或錯誤訊息寫得不好時，此解決時間會增加，這會使發現錯誤源變得困難。

 最好的建置錯誤是那些首先不會發生的錯誤，這就是為什麼 Visual Studio 提供自動完成和 IntelliSense 擺動的原因。 架構驗證器和類似的工具提供相同類型的回饋。 這些機制主動引導使用者構建格式良好的代碼，從而減少建置錯誤的可能性。

 Visual Studio 提供了一個工具視窗，使用者可以在其中讀取和導航其文件視窗中發生的錯誤。 提供鍵盤快速鍵，以便使用者可以快速導航大量代碼並直接轉到問題的位置。 Visual Studio 還允許將每個建置錯誤綁定到特定的説明關鍵字/上下文 ID，以便使用者可以直接轉到"説明"主題，該主題提供有關該錯誤的更深入資訊。

 編寫清晰、簡潔的建置錯誤：

- **使用簡單的語言**來解釋問題，很少或沒有編譯器行話。 建置錯誤的文本不應過於技術化。

- **概述可能的原因。** 例如，"在 '（屬性）：（值）'聲明中的屬性和值之間缺少一個冒號。

- 提供有關潛在修復的詳細資訊。 如果沒有足夠的空間，則其他詳細資訊可能會放入相應的說明主題中。

### <a name="components-of-a-well-written-error-message"></a>寫得很好的錯誤訊息的元件

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>對錯誤訊息使用 shell 對話方塊服務。
 使用 shell 對話方塊服務可以控制訊息的外觀，尤其是字體，而無需對單個元素進行重大更改。 使用**IErrorInfo**機制並使用**IVsUIShell：：設置ErrorInfo/報告錯誤資訊**報告它們。

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>選擇有效和適當的通知演示文稿。
 如果需要立即採取行動以避免資料丟失（同步通知），請使用帶有嚴重警告的模態對話方塊。 關鍵圖示保留用於在不閱讀消息的情況下關閉郵件可能會導致負面後果的情況。 資料丟失是需要報警級回應的危急情況。 過度使用關鍵圖示會使使用者對其重要性失去敏感性。 如果錯誤訊息具有資訊性，請考慮強制回應對話方塊（非同步通知）的替代方法。

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>提供清晰、簡潔的解釋，說明問題發生的原因，而不是技術解釋。
 在解釋中給使用者帶來技術細節負擔過重會使他們更有可能忽略錯誤訊息。 良好消息傳遞的示例：

- 無法打開請求的檔。

- "無法連接到互聯網。

#### <a name="provide-information-about-how-to-fix-the-problem"></a>提供有關如何解決此問題的資訊。
 為使用者提供如何解決此問題的建議。 如果沒有建議，要誠實地對待使用者。 提供指向其他線上來源的直接連結，例如技術支援或社區支援。 嘗試將使用者指向與問題相關的特定連線資訊。 對於錯誤 ID，請考慮將使用者連結到有關該特定錯誤的討論執行緒。 良好消息傳遞的示例：

- "請確保您已連接到互聯網，然後重試此操作。

- 確保檔存在，並且您有權打開該檔。

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>寫一條簡短而正確的消息。
 錯誤訊息可以通知、解釋和提供解決方案，但如果過於措辭，仍被忽略。 一種解決方案是使用帶有詳細資訊按鈕的漸進式披露。 例如，給出一個簡短的描述/解決方案，然後將更多詳細資訊放在詳細資訊按鈕下。 如果使用者選擇閱讀有關該錯誤的詳細資訊，則可以這樣做。

 消息中的語言應為：

- **適合域。** 使用使用者將理解的語言。 儘管我們的客戶是開發人員，但他們通常沒有我們的上下文和術語。

- **特定。** 避免措辭模糊，並給出所涉物體的具體名稱和位置。 例如，錯誤訊息（如"字元無效"）沒有用處。 哪個角色？ "找不到檔。 哪個檔？

- **禮貌。** 不要責怪使用者或讓他們感到愚蠢。 避免使用敵對或冒犯性語言（殺戮、執行、終止、致命、非法）。 避免大寫文本，這通常被視為喊話，並且不可讀。 不要用幽默。

- **正確。** 使用正確的拼寫和語法（即使在 Alphas 中）。 泰波斯是不專業和尷尬的。

- **上下文適當。** 使用適當的按鈕文本。 避免使用"確定"按鈕，而是使用"繼續"或"是/否"。

### <a name="error-message-examples"></a>錯誤訊息示例

|好|不良|
|----------|---------|
|您撥打的號碼不再在服務中。 請檢查該號碼並再次撥號，或撥打 0 的接線員。|- "錯誤 （449）： 非法號碼"<br />- "此未處理的異常錯誤表示操作成功完成。<br /><br /> ![Visual Studio 中錯誤的錯誤訊息](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>存取說明

### <a name="overview"></a>概觀
 除了 MSDN 中的文檔之外，Visual Studio 使用者還有多個存取點在 UI 中説明使用者。 為了確保這些存取點始終可用，功能團隊需要利用環境提供的説明系統。 這些存取點包括：

- **對話方塊中的教學和補充文本。** 在 UI 表面上提供方向或說明的靜態文本，或在 InfoTip 圖示上可用。

- **F1 説明**（僅限編輯器）。 在 Visual Studio 編輯器中，使用者可以相信，在任何時候都按 F1 將顯示特定于當前選擇的說明主題。 確保與 F1 相關的主題是適當且內容豐富的。

- **指向說明主題的超連結。** 對話方塊、工具視窗或設計介面中的超連結，用於啟動主題，以説明使用者瞭解有關如何完成任務的技術、功能或資訊的詳細資訊。

- **説明器 UI 機制，如智慧標籤和生成對話方塊。** 這些機制可説明使用者瞭解 UI 元素，或促進任務（如智慧標籤或產生器對話方塊）。

- **UI 説明按鈕**（已棄用）。 標題列中允許訪問相關 F1 說明主題的可見指示器。

### <a name="text"></a>Text

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>對話方塊中的教學和補充文本
 在支援複雜任務的對話方塊中，可能需要在 UI 中（通常在對話方塊頂部或複雜控制項附近）提供指令文本。 有關書寫樣式的詳細資訊，請參閱[UI 文本和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。

#### <a name="infotips"></a>資訊提示
 通常，指令性文本可能太長，無法在 UI 中定位，或者可能僅對新使用者有用，對有經驗的使用者來說，感覺雜亂無章。 在這種情況下，教學/資訊文本應作為工具提示放置在 InfoTip 下。

 InfoTips 應放置在它們相關的控制項附近，並且應該使用特定的 InfoTip 圖示，該圖示不顯眼但明顯。

 ![Visual Studio 中的資訊提示](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **視覺化工作室中的資訊提示示例**

### <a name="interactive-help-mechanisms"></a>互動式説明機制

#### <a name="f1-help"></a>F1 說明
 F1 説明在編輯器或設計介面中是必需的，但在視覺化工作室環境中的其他位置則不需要 F1 説明。

#### <a name="hyperlinks-to-help-topics"></a>指向說明主題的超連結
 超連結可用於在 IDE 中執行操作、在 IDE 中導航或在瀏覽器中啟動説明。 有關語言和 07.10.01 按鈕和超連結的詳細資訊，請參閱[UI 文本和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)，瞭解視覺化和佈局指南。

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>對話方塊標題列中的説明 [？] 按鈕（已棄用）
 在大多數情況下，對話方塊標題列中的"説明"按鈕將被棄用。 UI 主題不再是文檔模型的一部分，因此可能沒有要連結到的相關主題。 從本質上講，標題列按鈕與 F1 説明相同，在對話方塊中不再需要。 在某些情況下，這仍可用作可用更多概念或過程資訊的指示器，儘管超連結在較新的 UI 中更常用。

##### <a name="dialogs-created-through-the-environment"></a>通過環境創建的對話方塊
 許多 shell 對話方塊都是通過**VBDialogBoxParam**函數創建的。 此共用函數已更新，以説明將 **"説明"** 按鈕從對話方塊移動到 **"** 按鈕，同時保留向後相容和可擴展的體系結構。

 具體來說 **，VBDialogBoxParam**函數查看一個按鈕的對話方塊範本，該按鈕的**IDHELP** （9） 或標籤是 **"説明**"或 **"説明"&**。 如果找到"説明"按鈕，則該按鈕將隱藏，**並將WS_EX_CONTEXTHELP**樣式添加到對話方塊中，對話方塊中放置**了 "説明"按鈕。** 對話方塊標題列中的按鈕。

 創建對話方塊時，它會將對話方塊進程推送到堆疊上，並調用對話方塊，預處理對話方塊進程名為**DialogPreProc**。 何時 **？** 按一下按鈕，它將**SC_CONTEXTHELPWM_SYSCOMMAND**發送到對話方塊**WM_SYSCOMMAND**。 **DialogPreProc**捕獲此命令並將其更改為**WM_HELP**消息，該消息將傳遞到原始對話方塊進程。

 大多數環境創建的對話方塊在對話方塊上都有"説明"按鈕。 顯示對話方塊時，"説明"按鈕將自動隱藏，並且僅隱藏 **"説明"按鈕。** 按鈕工作正常。 如果 **？** 按鈕在 Windows 中被刪除或更改，此解決方案允許您快速移回原始説明按鈕。

 此解決方案會做出四種可能導致 bug 的假設：

- 對話方塊的説明按鈕是**IDHELP** （9）。

- 隱藏"説明"按鈕時，該對話方塊看起來正確。

- 該對話方塊不能替換其 winproc。

- 對話方塊未嵌入到另一個對話方塊中。

  如果對話方塊位於 msenv 中，並且不使用**VBDialogBoxParam，** 請先調查利用**VBDialogBoxParam，** 然後再實現您自己的處理常式。

##### <a name="dialogs-created-through-other-packages"></a>通過其他包創建的對話方塊
 您可以為駐留在 msenv 外部的對話方塊實現自己的解決方案。 對於 VSPackage 中的共用對話方塊類，請考慮將按鈕移動到標題列或在每個對話方塊上實現處理常式。 以下代碼是實現的框架，可説明您入門：

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

##### <a name="help-buttons-in-managed-code"></a>託管代碼中的説明按鈕
 在託管代碼中，重寫視窗標題列"説明"按鈕的預設行為非常簡單。 下面是演示此行為的完整演示應用程式。 從本質上講，您需要重寫表單的**WndProc**方法，然後在截獲**SC_CONTEXTHELP**消息時觸發 F1 説明請求。

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
