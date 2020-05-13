---
title: 視覺工作室的通知和進度 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f6a7ddd5d1a5a7257617b03098722e1341017b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699875"
---
# <a name="notifications-and-progress-for-visual-studio"></a>適用於 Visual Studio 的通知和進度
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a>通知系統

### <a name="overview"></a>概觀
 有幾種方法可以告知使用者 Visual Studio 中有關其軟體開發任務的情況。

 實作任何類型的通知時:

- **將通知數保持在最小**有效數量。 通知消息應應用於大多數 Visual Studio 使用者或特定功能/功能區域的使用者。 過度使用通知可能會使用戶感到輕鬆,或降低系統的易用性。

- **確保您呈現清晰、可操作的消息**,使用者可以使用這些消息調用適當的上下文,以便做出更複雜的選擇並採取進一步操作。

- **適當地顯示同步和異步消息。** 同步通知指示某些內容需要立即關注,例如當 Web 服務崩潰或引發代碼異常時。 應立即以需要輸入的方式通知用戶這些情況,例如在模式對話方塊中。 非同步通知是使用者應該知道的,但不需要立即執行,例如生成操作完成或網站部署完成時。 這些消息應更具環境性,而不是中斷用戶的任務流。

- **僅在必要時使用模態對話框,以防止使用者**在確認消息或做出對話框中顯示的決定之前採取進一步操作。

- **當環境通知不再有效時,請將其刪除。** 如果使用者已採取措施解決他們收到通知的問題,則不要要求使用者關閉通知。

- **請注意,通知可能會導致錯誤的相關性。** 使用者可能認為,他們的一個或多個行為觸發了通知,而實際上沒有因果關係。 在有關上下文、觸發器和通知源的通知消息中要清楚。

### <a name="choosing-the-right-method"></a>選擇正確的方法
 使用此表可説明您選擇正確的方法來通知使用者您的消息。

|方法|使用|請勿使用|
|------------|---------|----------------|
|[模式錯誤訊息對話框](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|在需要使用者回應之前,在繼續操作時使用。|當不需要阻止使用者並中斷其流時,請勿使用。 如果可以用另一種不太侵入性的方式顯示消息,則避免使用模式對話方塊。|
|[IDE 狀態列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|當有有關進程狀態的環境文本資訊時使用。|不要單獨使用。 最佳與其他反饋機制結合使用。|
|[內嵌資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|在工具視窗或文件視窗中,用於通知進度、錯誤狀態、結果和/或可操作資訊。|如果資訊與放置資訊欄的位置無關,請勿使用。<br /><br /> 請勿在文檔/工具視窗外使用。|
|[滑鼠游標變更](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|可用於通知進程正在進行。 還用於通知滑鼠中存在狀態更改,例如拖動/放置正在進行或滑鼠游標處於特定模式(如繪圖模式)時。|請勿用於短期進度更改或如果可能飄動遊標(例如,綁定到運行較長的進程的部分而不是整個進程)。|
|[進度指標](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|當您需要報告進度(不確定或不確定)時使用。 每種進度指標類型和特定用法都有多種。 請參考[進度指示器](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)。||
|[Visual Studio 的 [通知] 視窗](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|通知視窗不可公開擴展。 但是,它用於傳達有關 Visual Studio 的一系列消息,包括許可證的關鍵問題以及 Visual Studio 或包更新的資訊性通知。|請勿用於其他類型的通知。|
|[錯誤清單](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|當問題與使用者當前打開的解決方案有問題(錯誤/警告/資訊)直接相關時,他們可能需要對代碼執行操作。<br /><br /> 例如,這將包括:<br /><br /> - 編譯器訊息 (錯誤/ 警告/ 資訊)<br /><br /> - 代碼分析器/有關代碼的診斷訊息<br /><br /> - 產生訊息<br /><br /> 可能適用於與專案或解決方案文件相關的問題,但首先考慮解決方案資源管理員指示。|不要用於與使用者打開的解決方案代碼沒有任何關係的項。|
|編輯器通知:燈泡|當您有可用於修復修復打開檔中存在的問題時,請使用。<br /><br /> 請注意,燈泡還應用於託管按需對用戶代碼執行的操作,例如重構,但在這種情況下不會出現"通知樣式"。|不要用於與打開文件沒有任何關係的項。|
|編輯器通知: 搖擺|用於提醒使用者其打開代碼的特定範圍的問題(例如,錯誤的紅色波浪)。|不要用於與其打開代碼的特定範圍無關的專案。|
|[內嵌式狀態列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|用於提供與特定工具視窗、文檔視窗或對話框視窗上下文中的內容或進程相關的狀態。|請勿用於與特定視窗中的內容沒有任何關係的一般產品通知、流程或專案。|
|[視窗匣通知](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|用於為行程外進程或配套應用程序顯示通知。|不要用於與 IDE 相關的通知。|
|[通知氣泡](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|用於通知遠端進程或 IDE**外部**的更改。|請勿使用作為通知使用者 IDE**中**的進程的方法。|

### <a name="notification-methods"></a>通知方法

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>模式錯誤訊息對話框
 模式錯誤消息對話框用於顯示需要使用者確認或操作的錯誤消息。

 ![強制回應錯誤訊息](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **傳送此資料發出未正確的連線字串到資料庫的模式錯誤訊息對話框**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>IDE 狀態列
 使用者注意到狀態列文本的可能性與其全面的計算機體驗和 Windows 平臺的特定體驗相關。 Visual Studio 客戶群往往在這兩個方面都有經驗,但即使是知識淵博的 Windows 使用者也可能錯過狀態列中的更改。 因此,狀態列最適合用於資訊目的或作為在其他地方顯示的資訊冗餘提示。 用戶必須立即解決的任何類型的關鍵資訊都應在對話框中或在「通知」工具視窗中提供。

 Visual Studio 狀態列旨在允許顯示多種類型的資訊。 它分為反饋、設計器、進度列、動畫和用戶端的區域。

 反饋區域和設計器區域始終可見。 進度列和動畫區域始終動態,並且基於使用者上下文。 設計器區域具有靜態寬度,由從文本消息的隨附資源提取的字串的長度決定。 這允許當地語系化調整寬度大小,而無需更改代碼。 對於英語,此字串的寬度約為 220 圖元。 設計器區域將運行正常,反饋區域將吸收剩餘空間。

 狀態列還著色,通過傳達各種 IDE 狀態更改(如 IDE 處於調試模式時)來增加視覺興趣和功能值。

 ![IDE 狀態列色彩變更](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **IDE 狀態列顏色**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>嵌入式資訊列
 資訊列可以在文件視窗或工具視窗的頂部用於通知用戶狀態或條件。 它還可以提供命令,以便使用者可以有一種輕鬆執行操作的方法。 資訊欄是一個標準外殼控件。 避免創建自己的,這將在 IDE 中的行為和行為與其他操作不一致。 有關實現詳細資訊和使用指南[,請參閱資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。

 ![內嵌資訊列](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **嵌入在文件視窗中的資訊列,提醒使用者 IDE 處於歷史除錯模式,編輯器的回應方式與標準除錯模式不同。**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>滑鼠游標變更
 更改滑鼠游標時,請使用綁定到 VSColor 服務且已與游標關聯的顏色。 游標更改可用於指示正在進行的操作,以及用戶將滑鼠懸停在可拖動、拖到或用於選擇物件的目標上的命中區域。

 僅當必須為操作保留所有可用的 CPU 時間時,才使用忙/ 等待滑鼠游標,以防止使用者表示任何進一步輸入。 在大多數情況下,使用多線程編寫良好的應用程式時,阻止使用者執行其他操作的時間應該很少。

 請記住,游標更改對於其他地方提供的資訊非常有用。 不要依賴游標更改作為與使用者通信的唯一方式,尤其是在嘗試傳達使用者必須解決的關鍵內容時。

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>進度指標
 進度指示器對於在需要幾秒鐘以上才能完成的流程期間向使用者提供反饋非常重要。 進度指示器可以就地顯示(靠近正在進行的操作的啟動點)、嵌入式狀態列、模態對話框或 Visual Studio 狀態列。 遵循[進度指標](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)中有關其使用和實施的指導。

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>視覺化工作室通知視窗
 "可視化工作室通知"視窗通知開發人員有關許可、環境(可視化工作室)、擴展和更新。 用戶可以關閉單個通知,也可以選擇忽略某些類型的通知。 忽略的通知列表在 **「工具>選項**」頁中管理。

 通知視窗目前不可擴展。

 ![Visual Studio 的 [通知] 視窗](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **視覺化工作室通知工具視窗**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a>錯誤清單
 錯誤清單中的通知指示編譯和生成過程中發生的錯誤和警告,並允許使用者在代碼中導航到該特定代碼錯誤。

 ![錯誤清單](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **視覺化工作室中的錯誤清單**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>內嵌式狀態列
 由於 IDE 狀態列是動態的,其用戶端區域上下文設置為活動文件視窗,並在使用者的上下文和/或系統回應上更新資訊,因此很難保持資訊的持續顯示或對長期非同步進程的狀態。 例如,IDE 狀態列不適用於多個運行和/或立即可操作項選擇的測試運行結果通知。 請務必在用戶進行選擇或啟動進程的文檔或工具視窗的上下文中保留此類狀態資訊。

 ![內嵌狀態列](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **視覺工作室中的嵌入式狀態列**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>視窗匣通知
 Windows 通知區域位於 Windows 任務列上的系統時鐘旁邊。 許多實用程式和軟體元件在此區域中提供圖示,以便使用者可以獲取系統範圍任務的上下文菜單,例如更改螢幕解析度或獲取軟體更新。

 環境級通知應出現在可視化工作室通知中心,而不是Windows通知區域。

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>通知氣泡
 通知氣泡可以在編輯器/設計器中顯示為資訊,也可以顯示為 Windows 通知區域的一部分。 用戶將這些氣泡視為以後可以解決的問題,這對非關鍵通知是有好處的。 氣泡不適合用戶必須馬上解決的關鍵資訊。 如果在 Visual Studio 中使用通知氣泡,請按照[Windows 桌面指南進行通知氣泡](/windows/desktop/uxguide/mess-notif)。

 ![通知泡泡](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **以視覺化工作室的 Windows 通知區域中的通知氣泡**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>進度指標

### <a name="overview"></a>概觀
 進度指標是通知系統向用戶反饋的重要組成部分。 他們告訴使用者何時完成流程和操作。 熟悉的指示器類型包括進度條、旋轉游標和動畫圖示。 進度指標的類型和位置取決於上下文,包括報告的內容以及流程或操作完成的時間。

#### <a name="factors"></a>因素
 為了確定適合哪個指標類型,您需要確定以下因素。

1. **時間:** 動作需要多時間

2. **模式:** 操作是否對環境模態(鎖定 UI 直到該過程完成)

3. **持久/暫時性:** 是否需要在以後報告和/或查看進度的最終結果

4. **確定/不確定:** 是否可以計算操作結束時間和進度

5. **圖形/文字位置:** 進度或行程是內聯、消息正文中捕捉還是特定控制項(如樹控制件)

6. **鄰近:** 進度是否應靠近與其相關的 UI。 (例如,它是在狀態列中(可能距離很遠),還是必須靠近啟動進程的按鈕?)

#### <a name="determinate-progress"></a>確定進度

|進度類型|何時以及如何使用|注意|
|-------------------|-------------------------|-----------|
|進度列(確定 )|預計持續時間為>5 秒。<br /><br /> 可能包括過程詳細資訊的文本描述。|**不要**將文字嵌入動畫中。|
|資訊列|與上下文 UI 關聯的消息。 請參考[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。<br /><br /> 可能包括過程詳細資訊的文本描述。|當您需要指示多個行程時,**不要**使用多個資訊列。 改用堆疊進度條。|
|輸出視窗|臨時通知:使用者希望在完成後**查看**其詳細資訊的應用級進程。|如果使用者以後需要參考數據,**請不要**使用。|
|記錄檔|在完成後**保存**詳細資訊很重要的情況下,與臨時通知配對。||
|狀態列|瞬態通知:使用者在完成後**不需要**的詳細資訊的應用級進程。<br /><br /> 包括嵌入進度列。<br /><br /> 可能包括過程詳細資訊的文本描述。||

#### <a name="indeterminate-progress"></a>不確定進度

|進度類型|何時以及如何使用|注意|
|-------------------|-------------------------|-----------|
|進度列(不確定 )|預計持續時間為>5 秒。<br /><br /> 可能包括過程詳細資訊的文本描述。|**不要**將文字嵌入動畫中。|
|螞蟻(動畫水平點)|伺服器往返。<br /><br /> 放置在父容器頂部的上下文點附近。|如果不由整個容器父級,**請勿**使用。|
|微調器(進度環)|與上下文 UI 關聯的進程,或空間是考慮因素的位置。<br /><br /> 可能包括過程詳細資訊的文本描述。||
|資訊列|與上下文 UI 關聯的消息。 請參考[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。|當您需要指示多個行程時,**不要**使用多個資訊列。 改用堆疊進度條。|
|輸出視窗|臨時通知:使用者希望在完成後**查看**其詳細資訊的應用級進程。|**不要**用於需要跨會話保留的資訊。|
|記錄檔|在完成後**保存**詳細資訊很重要的情況下,與臨時通知配對。||
|狀態列|瞬態通知:使用者在完成後**不需要**的詳細資訊的應用級進程。<br /><br /> 包括嵌入式進度條。<br /><br /> 可能包括過程詳細資訊的文本描述。||

### <a name="progress-indicator-types"></a>進度指示器類型

#### <a name="progress-bars"></a>進度條

##### <a name="indeterminate"></a>定
 ![不確定的進度列](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **不確定的進度列**

 "不確定"是指無法確定操作或流程的總體進度。 對需要無限時間或訪問未知數量的物件的操作使用不確定的進度條。 使用文本說明來伴隨正在發生的事情。 使用超時為基於時間的操作提供邊界。 不確定的進度條使用動畫來顯示正在取得進展,但沒有提供其他資訊。 不要僅根據可能缺乏準確性來選擇不確定的進度條。

##### <a name="determinate"></a>確定
 ![確定的進度列](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **確定的進度列**

 "確定"是指操作或過程需要有限的時間量,即使無法準確預測該時間量。 清楚地表示已完成。 除非操作已完成,否則不要讓進度條轉到 100%。 確定進度條動畫從左到右從 0 移至 100%。

 切勿在操作期間向後移動進度指示器。 當操作開始時,柱線應穩步向前移動,並在操作結束時達到 100%。 進度條的要點是讓使用者了解整個操作需要多長時間,而不管涉及多少步驟。

##### <a name="concurrent-reporting-stacked-progress-bars"></a>併發報告(堆疊進度條)
 如果操作需要很長時間(也許幾分鐘),則可以使用兩個進度條,一個顯示操作的總體進度,另一個顯示當前步驟的進度。 例如,如果安裝程式正在複製許多檔,則一個進度列可用於指示整個過程需要多長時間,而第二個進度列可以指示正在複製當前檔或目錄的百分比。 不要使用堆疊進度條報告超過五個併發操作或進程。 如果要報告五個以上併發操作或進程,請使用帶有"取消"按鈕的模式對話框,並將進度詳細資訊報告給輸出視窗。

##### <a name="textual-descriptions"></a>文字描述
 使用文本說明來配合正在發生的事情和估計的完成時間。 如果無法確定操作需要多長時間,則提供反饋的更好選擇可能是動畫圖示而不是進度欄。

 Visual Studio 在狀態列中提供了一個標準進度列,可用於整合到 Visual Studio 的任何產品。 對於在動畫處理進度欄時發生的情況的文本說明,可以更新狀態欄文本。

#### <a name="other-progress-indicators"></a>其他進展指標

##### <a name="ants-animated-horizontal-dots"></a>螞蟻(動畫水平點)
 ![進度流動外框](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Ants",動畫水平點,為不確定的往返伺服器進程提供視覺參考。

##### <a name="spinner-progress-ring"></a>微調器(進度環)
 ![進度微調按鈕](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 微調器(也稱為"進度環")是一個不確定的進展指示器,主要用於上下文 UI。 顯示與其相關內容(如文本類別標題、消息傳遞或控制項)非常接近的微調器。

##### <a name="cursor-feedback"></a>游標反饋
 對於需要 2-7 秒的操作,提供游標反饋。 通常,這意味著使用操作系統提供的等待游標。 有關指導,請參閱 MSDN 文章[Cursors.Wait 屬性](/dotnet/api/system.windows.input.cursors.wait)。

#### <a name="progress-indicator-locations"></a>進度指示器位置

##### <a name="status-bar"></a>狀態列
 狀態列為應用程式提供了在不中斷使用者工作的情況下向用戶顯示消息和有用資訊的位置。 通常顯示在視窗底部,進度狀態將是一個工具提示窗格,其中包含有關進度度量與進度條指示器結合使用的消息。

 ![具有進度列的狀態列](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **具有進度列的狀態列**

 ![具有傳訊的狀態列](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **引入文字描述的狀態列**

##### <a name="infobar"></a>資訊列
 與狀態列類似,資訊列提供上下文通知和消息傳遞,也可以與不確定的進度指示器(如進度列或微調器)配對。 資訊欄不應提供粒度級別進度或確定進度指示。 請參考[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。

 ![具有進度列和傳訊的資訊列](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **包含進度列與文字描述的資訊列**

 ![視窗內的資訊列](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>內嵌
 內聯進度指示可以由任何進度載入程式類型表示。 通常,進度指示器與消息傳遞配對,但這不是要求。

 ![內嵌進度微調按鈕](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **微調器與文字描述相結合**

 ![內嵌堆疊進度列](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **確定堆疊進度列**

 ![內嵌進度傳訊](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **伺服器資源管理員內聯文字:刷新...**

##### <a name="tool-windows"></a>工具視窗
 全域進度指示由位於工具列正下方的不確定進度條表示。

 ![全域不確定的進度列](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **小組資源管理員不確定進度列**

##### <a name="dialogs"></a>對話方塊
 對話框可以包含任何進度載入程序類型。 進度指示器可以與消息傳遞配對,並與多個級別的進度指示相結合,以表示粒度和子流程。

 ![具有多個進度指標類型的對話方塊](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **具有併發行程和多個進度指示器類型的視覺化工作室對話框**

 ![具有進度載入器和傳訊的對話方塊](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **帶進度載入器和訊息線上指令的視覺化工作室對話框**

##### <a name="document-well"></a>文件良好
 文檔井可以結合控制項顯示多個進度載入程序類型。

 ![文件井中的進度傳訊](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **工具列下方不確定進度列**

##### <a name="output-window"></a>輸出視窗
 輸出窗口適用於通過內聯文本消息處理進程進度和持續進度狀態。 您應該使用狀態列以及任何「輸出」視窗進度報告。

 ![輸出視窗中的進度傳訊](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **輸出視窗,具有正在進行的程序狀態和等待訊息**

## <a name="infobars"></a><a name="BKMK_Infobars"></a>資訊列

### <a name="overview"></a>概觀
 資訊列為使用者提供了接近其注意點的指示器,使用共用資訊欄控件可確保視覺外觀和交互的一致性。

 ![資訊列](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **視覺化工作室中的資訊列**

#### <a name="appropriate-uses-for-an-infobar"></a>資訊列的適當用途

- 為使用者提供與當前上下文相關的非阻塞但重要的消息

- 指示 UI 處於具有某些交互影響的特定狀態或條件,例如歷史調試

- 通知使用者系統偵測到問題,例如當擴充導致效能問題時

- 為使用者提供一種輕鬆執行操作的方法,例如當編輯器偵測到檔案具有混合選項卡和空白時

##### <a name="do"></a>建議事項：

- 保持資訊列消息文本簡短且指向點。

- 保持連結和按鈕上的文本簡潔。

- 確保提供給使用者的「操作」選項最小,僅顯示所需的操作。

##### <a name="dont"></a>不要:

- 使用資訊列提供應放置在工具列中的標準命令。

- 使用資訊列代替模式對話方塊。

- 在視窗外創建浮動消息。

- 在同一視窗中的多個位置使用多個資訊列。

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>多個資訊列可以同時顯示嗎?
 是,可以同時顯示多個資訊欄。 它們將以先到先得的順序顯示,第一個資訊欄顯示在頂部,下面顯示其他資訊欄。

 使用者一次最多會看到三個資訊欄,之後,如果有更多的資訊列可用,資訊欄區域將變為可滾動。

### <a name="creating-an-infobar"></a>建立資訊列
 資訊列有四個部分,從左到右:

- **圖示:** 這是要為資訊列添加任何圖示的位置,例如警告圖示。

- **文字:** 如果需要,可以添加文本來描述使用者所處的方案/情況以及文本中的連結。 記住要保持文本簡潔。

- **操作:** 此部分應包含使用者可以在資訊列中執行的操作的連結和按鈕。

- **關閉按鈕:** 右側的最後一個部分可以有一個關閉按鈕。

#### <a name="creating-a-standard-infobar-in-managed-code"></a>在託管代碼中建立標準資訊列
 InfoBarModel 類可用於為資訊列創建數據源。 使用以下四個建構函數之一:

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);
```

 下面是一個示例,該示例創建一個資訊欄模型,其中包含一些帶有超連結、操作按鈕和圖示的文本。

 ![具有超連結的資訊列](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

```
var infoBar = new InfoBarModel(
    textSpans: new[]
    {
        new InfoBarTextSpan("This is a "),
        new InfoBarHyperlink("hyperlink"),
        new InfoBarTextSpan(" InfoBar.")
    },
    actionItems: new[]
    {
        new InfoBarButton("Click Me")
    },
    image: KnownMonikers.StatusInformation,
    isCloseButtonVisible: true);

```

#### <a name="creating-a-standard-infobar-in-native-code"></a>在本機代碼中建立標準資訊列
 實現 IVsInfoBar 介面,以便提供來自本機代碼的資訊列。

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>從資訊列取得資訊列 UIElement
 InfoBarModel 或 IVsInfoBar 實現是數據模型,必須轉換為 UIElement 才能顯示在 UI 中。 可以使用 SVInfoBarUIFactory/IVsInfoBarUIFactory 服務檢索 UIElement。

```
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)
{
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;
    if (infoBarUIFactory == null)
    {
        uiElement = null;
        return false;
    }

    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);
    return uiElement != null;
}
```

### <a name="placement"></a>放置
 資訊列可以在以下一個或多個位置顯示:

- 工具視窗

- 在文件選項卡中

> [!IMPORTANT]
> 可以定位資訊欄來提供有關全域上下文的消息。 這將顯示在工具列和文件之間。 不建議這樣做,因為它會導致IDE的"跳躍和抖動"問題,除非絕對必要和適當,否則應避免這樣做。

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>在工具視窗窗格中放置資訊列
 工具視窗窗格.AddInfoBar(IVsInfoBar)方法可用於向工具視窗添加資訊列。 此 API 可以添加 IVsInfoBar(其中 InfoBarModel 是預設實現)或 IVsUI 元素。

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>在文件或非工具視窗窗格中放置資訊列
 要將資訊列放置在任何 IVWindowFrame 中,請使用VSFPROPID_InfoBarHost屬性獲取框架的 IVsInfoBarHost,然後添加資訊列 UIElement。

```
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)
{
    IVsInfoBarHost infoBarHost;
    if (TryGetInfoBarHost(frame, out infoBarHost))
    {
        infoBarHost.AddInfoBar(uiElement);
    }
}
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)
{
    object infoBarHostObj;
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))
    {
        infoBarHost = null;
        return false;
    }

    infoBarHost = infoBarHostObj as IVsInfoBarHost;
    return infoBarHost != null;
}

```

#### <a name="placing-an-infobar-in-the-main-window"></a>在主視窗中放置資訊列
 要在主視窗中放置資訊列,請使用 IVsShell 服務VSSPROPID_MainWindowInfoBarHost獲取主視窗的 IVsInfoBarHost,然後將資訊列 UIElement 添加到其中。

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>我是否會知道使用者何時在我的資訊欄中執行操作?
 是的,我們將將每個事件操作返回給資訊欄作者。 然後,資訊列作者根據資訊列中的用戶選擇在IDE中執行操作。 資訊列將自動從按下其"關閉"按鈕的主機中刪除,但如果關閉後需要刪除其他資訊列,則需要執行其他工作。 遙測還需要由每個資訊欄獨立記錄。

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>在工具視窗窗格中接收資訊列事件
 工具視窗窗格有兩個用於資訊列的事件。 關閉工具視窗窗格中的資訊列時,將引發資訊列關閉事件。 按一下資訊列內的超連結或按鈕時,將引發資訊欄項目單擊事件。

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>直接從 UIElement 接收資訊列事件
 IVsInfoBarUIElement.建議可用於直接從資訊列的 UIElement 訂閱事件。 實施 IVsInfoBarUI 事件將允許作者接收關閉和單擊事件。

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a>錯誤驗證
 當使用者輸入不可接受的資訊時(例如跳過所需欄位或以不正確的格式輸入資料時)時,最好在控制件附近使用控制驗證或反饋,而不是使用阻塞彈出錯誤對話方塊。

### <a name="field-validation"></a>欄位驗證
 表單和字段驗證由三個元件組成:控制件、圖示和工具提示。 雖然可以使用多種類型的控制項,但文本框將用作範例。

 ![欄位驗證&#40;空白&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 如果需要該字段,則應該有浮浮水印文本,說明`Environment.ControlEditRequiredBackground``Environment.ControlEditRequiredHintText`**\<所需的>,** 欄位背景應為淺黃色 (VSColor: ), 前景應為灰色 (VSColor: ):

 ![具有 [必要] 標籤的欄位驗證](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 程式可以確定控制項處於在焦點移動到其他控制項時或當使用者單擊 [OK] 提交按鈕或當使用者儲存文檔或表單時*輸入的無效內容*的狀態。

 確定無效內容狀態后,控件內或位於控件旁邊會出現一個圖示。 描述錯誤的工具提示應出現在圖示或控制項的懸停上。 此外,在創建無效狀態的控制器周圍應顯示 1 畫素邊框。

 ![欄位驗證版面配置規格](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **現場驗證的佈局規範**

#### <a name="acceptable-variations-for-icon-location"></a>圖示位置的可接受變體
 在無數獨特的情況下,使用者需要了解驗證錯誤。 考慮 UI 的控制類型和配置,選擇適合您的情況的圖示位置。

 ![圖示位置可接受的位置](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **欄位驗證圖示位置的可接受變數**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>需要往返伺服器或網路連線的驗證
 在某些情況下,需要往返伺服器來驗證內容,顯示使用者進度、已驗證和錯誤狀態非常重要。 下圖顯示了此案例的範例和建議的 UI。

 ![需要來回伺服器的驗證](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **需要來回伺服器的驗證**

 請注意,必須提供足夠的可用空間,以容納"驗證..."和"重試"文字。

#### <a name="in-place-warning-text"></a>就地警告文字
 當有空間將錯誤消息置於錯誤狀態時,最好僅使用工具提示。

 ![在&#45;位置警告](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **就地警告文字**

#### <a name="watermarks"></a>浮水印
 有時,整個控件或視窗處於錯誤狀態。 在此情況下,使用水印指示錯誤。

 ![水印](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **水印欄位驗證**
