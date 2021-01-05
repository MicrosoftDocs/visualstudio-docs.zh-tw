---
title: Visual Studio 的通知和進度 |Microsoft Docs
description: 深入瞭解有幾種方式可通知使用者有關其軟體發展工作 Visual Studio 中發生的狀況。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56acfd96f8d9be575f6e13c727a294f28301bef4
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863786"
---
# <a name="notifications-and-progress-for-visual-studio"></a>適用於 Visual Studio 的通知和進度
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> 通知系統

### <a name="overview"></a>概觀
 有幾種方式可通知使用者有關其軟體發展工作的 Visual Studio 中發生什麼狀況。

 在執行任何一種通知時：

- **將通知數目維持在最小** 有效位數。 通知訊息應該適用于大部分的 Visual Studio 使用者或特定功能/功能區域的使用者。 過度使用通知可能會 sidetrack 使用者，或降低察覺到系統的易用性。

- **確定您正在呈現清楚、可採取** 動作的訊息，使用者可使用這些訊息來叫用適當的內容，以進行更複雜的選擇並採取進一步的動作。

- **適當地呈現同步和非同步訊息。** 同步通知表示有一些需要立即注意的內容，例如當 web 服務當機或擲回程序代碼例外狀況時。 使用者應立即以需要其輸入的方式（例如在強制回應對話方塊中）來通知這些情況。 非同步通知是使用者應該知道但不需要立即採取行動的通知，例如當組建作業完成或網站部署完成時。 這些訊息應該是更環境的，而不會中斷使用者的工作流程。

- **只有在必要時才使用強制回應對話方塊，以防止使用者** 在確認訊息或在對話方塊中顯示決策之前採取進一步的動作。

- **移除不再有效的環境通知。** 如果使用者已經採取動作來解決他們所收到的問題，則不需要使用者關閉通知。

- **請注意，通知可能會導致錯誤的相互關聯。** 使用者可能會認為一或多個動作已觸發通知，事實上沒有因果關係。 請清除有關內容、觸發程式和通知來源的通知訊息。

### <a name="choosing-the-right-method"></a>選擇正確的方法
 使用此表格可協助您選擇正確的方法來通知使用者您的訊息。

|方法|用途|請勿使用|
|------------|---------|----------------|
|[強制回應錯誤訊息對話方塊](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|在需要使用者回應才能繼續之前使用。|不需要封鎖使用者並中斷其流程時，請勿使用。 如果有可能以另一個較不具侵入性的方式顯示訊息，請避免使用強制回應對話方塊。|
|[IDE 狀態列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|當有關于進程狀態的環境文字資訊時，請使用。|請勿單獨使用。 最好與另一個意見反應機制搭配使用。|
|[內嵌資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|在工具視窗或文件視窗中，使用來通知進度、錯誤狀態、結果及/或可採取動作的資訊。|如果資訊與資訊列的放置位置無關，請不要使用。<br /><br /> 請勿在檔/工具視窗之外使用。|
|[滑鼠游標變更](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|可以用來通知進程正在進行中。 也可用來通知滑鼠中有狀態變更，例如當拖放進行中或滑鼠游標處於特定模式時（例如繪圖模式）。|請勿用於簡短的進度變更，或者如果資料指標的 fluttering 可能 (例如，系結至較長執行進程的元件，而不是整個進程) 。|
|[進度指示器](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|當您需要 (確定或不定) 報告進度時，請使用。 有各種不同的進度指標類型和特定的使用方式。 查看 [進度指示器](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)。||
|[Visual Studio 的 [通知] 視窗](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|[通知] 視窗無法公開擴充。 不過，它是用來傳達有關 Visual Studio 的訊息範圍，包括您的授權的重大問題，以及 Visual Studio 或封裝之更新的語音總機。|請勿用於其他類型的通知。|
|[錯誤清單](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|當問題直接與使用者目前開啟的解決方案有問題 (錯誤/警告/資訊) 時，他們可能需要對程式碼採取行動。<br /><br /> 例如，這包括：<br /><br /> -編譯器訊息 (錯誤/警告/資訊) <br /><br /> -程式碼的程式碼分析器/診斷訊息<br /><br /> -組建訊息<br /><br /> 可能適用于專案或方案檔的相關問題，但請先考慮方案總管的指示。|請勿使用與使用者開啟的方案程式碼沒有任何關聯的專案。|
|編輯器通知：燈泡|當您有可用的修正程式來補救存在於開啟檔案中的問題時，請使用此方法。<br /><br /> 請注意，燈泡也應該用來裝載在使用者的程式碼上依需求（例如重構）採取的快速動作，但在這種情況下，不會顯示「通知樣式」。|請勿使用與開啟的檔案沒有任何關聯的專案。|
|編輯器通知：波浪線|用來警示使用者特定範圍的開放程式碼問題 (例如，) 的紅色波浪線。|請勿用於與開啟程式碼的特定範圍無關的專案。|
|[內嵌狀態列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|用來提供特定工具視窗、文件視窗或對話方塊視窗內容中內容或流程的相關狀態。|請勿用於與特定視窗內的內容沒有任何關聯的一般產品通知、處理常式或專案。|
|[Windows 系統匣通知](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|用來呈現跨進程進程或附屬應用程式的通知。|請勿使用與 IDE 相關的通知。|
|[通知的氣泡](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|用來通知遠端進程或在 IDE **外部** 變更。|請勿使用做為在 IDE **中** 通知使用者進程的方法。|

### <a name="notification-methods"></a>通知方法

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> 強制回應錯誤訊息對話方塊
 [強制回應錯誤訊息] 對話方塊是用來顯示需要使用者確認或動作的錯誤訊息。

 ![強制回應錯誤訊息](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **強制回應錯誤訊息對話方塊會警示使用者對資料庫不正確連接字串**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> IDE 狀態列
 使用者注意到狀態列文字的可能性，與他們的電腦體驗和 Windows 平臺的特定體驗有相互關聯。 Visual Studio 的客戶群通常會在這兩個領域都有經驗，但即使是有經驗的 Windows 使用者可能會錯過狀態列中的變更。 因此，狀態列最適合用來做為資訊用途，或做為其他地方所提供資訊的重複提示。 您應在對話方塊或 [通知] 工具視窗中提供使用者必須立即解決的任何一種重要資訊。

 Visual Studio 狀態列的設計是為了允許顯示數種類型的資訊。 它分為意見反應、設計師、進度列、動畫和用戶端的區域。

 意見反應區域和設計工具區域一律可見。 進度列和動畫區域一律為動態且以使用者內容為基礎。 設計工具區域具有靜態寬度，取決於從文字訊息的伴隨資源提取的字串長度。 這可讓當地語系化調整寬度，而不需要變更程式碼。 若為英文，此字串的寬度大約為220圖元。 設計工具區域會正常運作，且意見反應區域會吸收剩餘的空間。

 狀態列也以色彩標示由溝通各種 IDE 狀態變更（例如當 IDE 處於「偵測」模式時）來新增視覺利息和功能值。

 ![IDE 狀態列色彩變更](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **IDE 狀態列色彩**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> 內嵌的資訊列
 您可以在文件視窗或工具視窗的頂端使用資訊列來通知使用者狀態或條件。 它也可以提供命令，讓使用者可以輕鬆地採取動作。 資訊列是標準的 shell 控制項。 請避免建立您自己的，這會在 IDE 中與其他人一起運作並出現不一致的情況。 請參閱 [資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) ，以取得執行詳細資料和使用方式指引。

 ![內嵌資訊列](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **內嵌在文件視窗中的資訊列會警示使用者，IDE 處於歷程偵測模式，而編輯器的回應方式與在標準的偵錯工具模式中的方式相同。**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> 滑鼠游標變更
 變更滑鼠游標時，請使用與 VSColor 服務系結的色彩，而且已經與資料指標產生關聯。 資料指標變更可用來指出進行中的作業，以及使用者將滑鼠停留在可拖曳、卸載或用來選取物件的目標上的點擊區域。

 只有在所有可用的 CPU 時間都必須保留給作業，以防止使用者表示任何進一步的輸入時，才使用忙碌/等候滑鼠游標。 在大部分的情況下，使用多執行緒處理的應用程式會很罕見，但防止使用者執行其他作業的時間則很罕見。

 請記住，資料指標變更很適合用來做為其他地方所呈現資訊的重複提示。 請勿依賴資料指標變更，這是與使用者通訊的唯一方法，尤其是在嘗試傳達使用者必須解決的重要事項時。

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> 進度指示器
 進度指標很重要，可在處理常式期間提供超過幾秒鐘的時間來完成使用者的意見反應。 進度指示器可以就地顯示 (接近進行中動作的啟動點) 、內嵌的狀態列、強制回應對話方塊或 Visual Studio 狀態列中。 遵循 [進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) 指標中有關其使用和執行的指引。

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio 通知視窗
 Visual Studio 通知視窗會通知開發人員有關授權、環境 (Visual Studio) 、延伸模組和更新。 使用者可以解除個別通知，也可以選擇忽略特定類型的通知。 已忽略通知的清單會在 [ **工具 > 選項** ] 頁面中進行管理。

 [通知] 視窗目前不是可擴充的。

 ![Visual Studio 的 [通知] 視窗](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio 通知工具視窗**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> 錯誤清單
 錯誤清單中的通知表示在編譯和或建立進程期間發生的錯誤和警告，並可讓使用者在程式碼中流覽至該特定程式碼錯誤。

 ![錯誤清單](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Visual Studio 中的錯誤清單**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> 內嵌狀態列
 由於 IDE 狀態列是動態的，且其用戶端區域內容會設定為使用中文件視窗以及在使用者的內容和/或系統回應上進行更新，因此很難維護連續顯示資訊或提供長期非同步處理常式的狀態。 例如，IDE 狀態列不適合用于多個執行及/或立即可操作專案選取專案的測試回合結果通知。 務必將這類狀態資訊保留在使用者進行選取或啟動處理常式的檔或工具視窗內容中。

 ![內嵌狀態列](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Visual Studio 中的內嵌狀態列**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Windows 系統匣通知
 Windows 通知區域是 Windows 工作列上系統時鐘的旁邊。 許多公用程式和軟體元件都提供此區域中的圖示，讓使用者可以取得全系統工作的內容功能表，例如變更螢幕解析度或取得軟體更新。

 環境層級的通知應該會出現在 Visual Studio 通知中樞，而不是 Windows 通知區域中。

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> 通知的氣泡
 通知反升可以在編輯器/設計工具或 Windows 通知區域中顯示為資訊。 使用者會將這些冒泡視為可以稍後解決的問題，這是非關鍵通知的優點。 針對使用者必須立即解決的重要資訊，反升不適合。 如果您在 Visual Studio 中使用通知反升，請遵循 [Windows 桌面指引以取得通知的氣泡](/windows/desktop/uxguide/mess-notif)。

 ![通知泡泡](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Windows 通知區域中用於 Visual Studio 的通知反升**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> 進度指示器

### <a name="overview"></a>概觀
 進度指示器是通知系統的重要部分，可提供使用者意見反應。 他們會在進程和作業完成時告訴使用者。 熟悉的指標類型包括進度列、旋轉游標以及動畫圖標。 進度指標的類型和位置會視內容而定，包括所報告的內容，以及處理常式或作業完成所需的時間。

#### <a name="factors"></a>因素
 若要判斷哪一個是適當的指標類型，您需要判斷下列因素。

1. **時間：** 作業將花費的時間長度

2. 模式 **：** 作業是否為環境的強制回應 (會在程式完成之前鎖定 UI) 

3. **持續性/暫時性：** 進度的最終結果是否需要報告及/或在稍後查看

4. **確定/不定：** 是否可以計算作業的結束時間和進度

5. **圖形/文字位置：** 進度或流程是以內嵌方式、訊息主體或特定控制項（例如樹狀目錄控制項）的形式捕獲

6. **鄰近性：** 進度是否應接近與其相關的 UI。  (例如，它可以在狀態列中，它可能會很遠，還是必須靠近啟動處理常式的按鈕 ) 

#### <a name="determinate-progress"></a>確定進度

|進度類型|時機和使用方式|附註|
|-------------------|-------------------------|-----------|
|進度列 (確定) |預期的 >持續期間（5秒）。<br /><br /> 可能包含流程詳細資料的文字描述。|**不要** 將文字內嵌至動畫。|
|資訊列|與內容相關 UI 相關聯的訊息。 請參閱 [資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。<br /><br /> 可能包含流程詳細資料的文字描述。|當您需要指出多個進程時，**請勿** 使用多個資訊列。 請改用堆疊進度列。|
|輸出視窗|暫時性通知：使用者想要在完成後 **檢查** 詳細資料的應用層級進程。|當使用者稍後需要參考資料時，**請勿** 使用。|
|記錄檔|在完成後 **儲存** 詳細資料的重要情況下，與 intransient 通知配對。||
|狀態列|暫時性通知：使用者在完成後將 **不需要** 詳細資料的應用層級進程。<br /><br /> 包含內嵌的進度列。<br /><br /> 可能包含流程詳細資料的文字描述。||

#### <a name="indeterminate-progress"></a>不定進度

|進度類型|時機和使用方式|附註|
|-------------------|-------------------------|-----------|
|進度列 (不定) |預期的 >持續期間（5秒）。<br /><br /> 可能包含流程詳細資料的文字描述。|**不要** 將文字內嵌至動畫。|
|Ants (動畫水準點) |來回行程至伺服器。<br /><br /> 在上層容器的上層放置接近的內容點。|如果不是整個容器的父代，**請勿** 使用。|
|微調 (進度環形) |與內容相關 UI 相關聯的進程，或空間是考慮的地方。<br /><br /> 可能包含流程詳細資料的文字描述。||
|資訊列|與內容相關 UI 相關聯的訊息。 請參閱 [資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。|當您需要指出多個進程時，**請勿** 使用多個資訊列。 請改用堆疊進度列。|
|輸出視窗|暫時性通知：使用者會想要在完成後 **檢查** 詳細資料的應用層級進程。|**請勿** 使用需要跨會話保存的資訊。|
|記錄檔|在完成後 **儲存** 詳細資料的重要情況下，與 intransient 通知配對。||
|狀態列|暫時性通知：使用者在完成後將 **不需要** 詳細資料的應用層級進程。<br /><br /> 包含內嵌的進度列。<br /><br /> 可能包含流程詳細資料的文字描述。||

### <a name="progress-indicator-types"></a>進度指標類型

#### <a name="progress-bars"></a>進度列

##### <a name="indeterminate"></a>定
 ![不定的進度列](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **不定的進度列**

 「不定」表示無法判斷操作或進程的整體進度。 針對需要無限制時間或存取未知物件數目的作業，請使用不定的進度列。 使用文字描述來伴隨發生的情況。 使用超時來提供以時間為基礎之作業的界限。 不定的進度列會使用動畫來顯示正在進行的進度，但不提供任何其他資訊。 請勿只根據可能缺少的精確度來選擇不定的進度列。

##### <a name="determinate"></a>確定
 ![確定進度列](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **確定進度列**

 「確定」表示作業或進程需要限定的時間量，即使該時間量無法準確預測也一樣。 明確指出完成。 除非作業已完成，否則不要讓進度列移至100%。 確定進度列動畫從0往右移動至100%。

 永遠不會在作業期間將進度列指示器往下移。 當作業開始時，此橫條應該會穩定地向前移動，並于結束時到達100%。 進度列的點是讓使用者瞭解整個作業所花費的時間，不論涉及多少步驟。

##### <a name="concurrent-reporting-stacked-progress-bars"></a>並行報表 (堆疊的進度列) 
 如果作業需要很長的時間（可能需要幾分鐘的時間），則可能會使用兩個進度列，其中一個會顯示作業的整體進度，另一個則用於目前步驟的進展。 例如，如果安裝程式正在複製許多檔案，則可以使用一個進度列來指出整個程式所花費的時間長度，而第二個會指出目前檔案或目錄的複製百分比。 請勿使用堆疊進度列報告五個以上的並行作業或處理常式。 如果您有五個以上的並行作業或要報告的進程，請使用具有 [取消] 按鈕的強制回應對話方塊，並向輸出視窗報告進度詳細資料。

##### <a name="textual-descriptions"></a>文字描述
 使用文字描述來伴隨發生的情況和預估完成的時間。 如果無法判斷作業需要多少時間，則提供意見反應的較佳選擇可能是動畫圖標，而不是進度列。

 Visual Studio 在狀態列中提供標準的進度列，可供任何整合至 Visual Studio 的產品使用。 如需進度列動畫時所發生狀況的文字描述，可以更新狀態列文字。

#### <a name="other-progress-indicators"></a>其他進度指示器

##### <a name="ants-animated-horizontal-dots"></a>Ants (動畫水準點) 
 ![進度流動外框](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 「Ants」的動畫水準點，提供不定往返伺服器進程的視覺參考。

##### <a name="spinner-progress-ring"></a>微調 (進度環形) 
 ![進度微調按鈕](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 微調 (也稱為「進度環形」 ) 是與內容 UI 相關的非確定性進度指標。 顯示靠近其相關內容（例如文字類別標頭、訊息或控制項）的微調按鈕。

##### <a name="cursor-feedback"></a>資料指標意見反應
 針對花費在2-7 秒之間的作業，請提供資料指標的意見反應。 一般而言，這表示使用作業系統所提供的等候游標。 如需指引，請參閱 MSDN 文章資料 [指標. Wait 屬性](/dotnet/api/system.windows.input.cursors.wait)。

#### <a name="progress-indicator-locations"></a>進度指標位置

##### <a name="status-bar"></a>狀態列
 狀態列可讓您的應用程式在不中斷使用者工作的情況下，向使用者顯示訊息和有用的資訊。 通常會顯示在視窗底部，進度的狀態會是 [工具提示] 窗格，其中包含與進度列指標結合進度量值的相關訊息。

 ![具有進度列的狀態列](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **具有進度列的狀態列**

 ![具有傳訊的狀態列](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **具有文字描述的狀態列**

##### <a name="infobar"></a>資訊列
 與狀態列類似，資訊列會提供內容相關的通知和訊息，也可以與不定的進度指示器（例如進度列或微調）配對。 資訊列不應提供細微等級的進度或確定進度指示。 請參閱 [資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。

 ![具有進度列和傳訊的資訊列](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **包含進度列和文字描述的資訊列**

 ![視窗內的資訊列](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>內嵌
 內嵌進度指示可以用任何一種進度載入器類型來表示。 進度指標通常會與訊息配對，但這不是必要條件。

 ![內嵌進度微調按鈕](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **與文字描述結合的微調**

 ![內嵌堆疊進度列](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **確定堆疊進度列**

 ![內嵌進度傳訊](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **伺服器總管內嵌文字：正在重新整理 .。。**

##### <a name="tool-windows"></a>工具視窗
 全域進度指示是以不確定的進度列（位於工具列正下方）來表示。

 ![全域不確定的進度列](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer 全域不定的進度列**

##### <a name="dialogs"></a>對話方塊
 對話可以包含任何進度載入器類型。 進度指示器可以與訊息配對，也可以與多層的進度指示結合，以代表細微和子進程。

 ![具有多個進度指標類型的對話方塊](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **具有並行進程和多個進度指標類型的 Visual Studio 對話方塊**

 ![具有進度載入器和傳訊的對話方塊](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **具有進度載入器和訊息內嵌命令的 Visual Studio 對話方塊**

##### <a name="document-well"></a>檔妥善
 檔也可以與控制項一起顯示多個進度載入器類型。

 ![文件井中的進度傳訊](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **在工具列下方有不定的進度列**

##### <a name="output-window"></a>輸出視窗
 [輸出] 視窗適用于透過內嵌文字訊息處理進程進度和持續進度狀態。 您應該使用狀態列以及任何輸出視窗進度報告。

 ![輸出視窗中的進度傳訊](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **具有進行中進程狀態和等候訊息的輸出視窗**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> 資訊列

### <a name="overview"></a>概觀
 資訊列可為使用者提供接近關注點的指標，並使用共用的資訊列控制項確保視覺外觀和互動中的一致性。

 ![靠近](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Visual Studio 中的資訊列**

#### <a name="appropriate-uses-for-an-infobar"></a>資訊列的適當用途

- 為使用者提供與目前內容相關的非封鎖但重要訊息

- 表示 UI 處於特定狀態或具有某些互動含意的條件，例如歷程記錄偵錯工具

- 通知使用者系統偵測到問題，例如當擴充功能造成效能問題時

- 讓使用者可以輕鬆地採取動作，例如當編輯器偵測到檔案具有混合的索引標籤和空格時

##### <a name="do"></a>可行事項：

- 將資訊列訊息內容保持簡短和點。

- 讓連結和按鈕的文字簡潔明瞭。

- 確定您提供給使用者的「動作」選項很短，只顯示必要的動作。

##### <a name="dont"></a>不要：

- 您可以使用資訊列來提供應放置在工具列中的標準命令。

- 使用資訊列來取代強制回應對話方塊。

- 在視窗外建立浮動訊息。

- 在相同視窗中的數個位置使用多個資訊列。

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>可以同時顯示多個資訊列嗎？
 是，多個資訊列可以同時顯示。 首先會以第一次服務的順序顯示，第一個資訊列顯示在下方，而其他資訊列顯示于下方。

 使用者一次最多會看到三個資訊列，在這之後，如果有更多資訊列可用，資訊欄區域就會變成可滾動的。

### <a name="creating-an-infobar"></a>建立資訊列
 此資訊列有四個區段，從左至右：

- **圖示：** 您可以在這裡新增任何您想要為資訊列顯示的圖示，例如警告圖示。

- **文字：** 您可以新增文字來描述使用者所在的案例/狀況，以及文字內的連結（如有需要）。 請記得將文字保持簡潔。

- **動作：** 此區段應該包含使用者可在您的資訊列中採取動作的連結和按鈕。

- **關閉按鈕：** 右邊的最後一個區段可以有 [關閉] 按鈕。

#### <a name="creating-a-standard-infobar-in-managed-code"></a>在 managed 程式碼中建立標準資訊列
 InfoBarModel 類別可以用來建立資訊列的資料來源。 使用下列四個函式的其中一個：

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

 以下範例會建立具有一些文字的 InfoBarModel，其中含有超連結、動作按鈕和圖示。

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>以原生程式碼建立標準資訊列
 執行 IVsInfoBar 介面，以便從機器碼提供資訊列。

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>從資訊列中取得資訊列 UIElement
 InfoBarModel 或 IVsInfoBar 實作為必須轉換成 UIElement 才能顯示在 UI 中的資料模型。 您可以使用 SVsInfoBarUIFactory/IVsInfoBarUIFactory 服務來抓取 UIElement。

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
 資訊列可以顯示在下列一或多個位置：

- 工具視窗

- 在 [檔] 索引標籤中

> [!IMPORTANT]
> 您可以定位資訊列來提供全域內容的相關訊息。 這會出現在工具列和檔之間。 不建議這麼做，因為它會導致 IDE 的「跳躍與直覺式」發生問題，除非絕對必要和適當，否則應該避免。

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>將資訊列放在 ToolWindowPane 中
 ToolWindowPane. AddInfoBar (IVsInfoBar) 方法可以用來將資訊列新增至工具視窗。 此 API 可以新增 IVsInfoBar (，其中 InfoBarModel 是預設的執行) 或 IVsUIElement。

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>將資訊列放入檔或非 ToolWindowPane
 若要將資訊列放入任何 IVsWindowFrame，請使用 VSFPROPID_InfoBarHost 屬性取得框架的 IVsInfoBarHost，然後新增資訊列 UIElement。

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
 若要將資訊列放在主視窗中，請使用 Ivsshell 出現服務的 VSSPROPID_MainWindowInfoBarHost 來取得主視窗的 IVsInfoBarHost，然後在其中新增資訊列 UIElement。

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>當使用者在我的資訊列中採取動作時，是否會知道？
 是，我們會將每個事件動作傳回到資訊列作者。 然後，資訊列作者可以根據使用者在資訊列中選取的專案，在 IDE 中採取動作。 資訊列將會自動從已按下 [關閉] 按鈕的主機移除，但如果其他資訊列需要在關閉後移除，則需要額外的工作。 遙測也必須個別記錄在每個資訊列中。

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>接收 ToolWindowPane 中的資訊列事件
 ToolWindowPane 有兩個資訊列的事件。 當 ToolWindowPane 中的資訊列關閉時，就會引發 InfoBarClosed 事件。 按一下資訊列內的超連結或按鈕時，就會引發 InfoBarActionItemClicked 事件。

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>直接從 UIElement 接收資訊列事件
 IVsInfoBarUIElement 可用於直接從資訊列的 UIElement 訂閱事件。 執行 IVsInfoBarUIEvents 可讓作者接收 close 和 click 事件。

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> 錯誤驗證
 當使用者輸入無法接受的資訊時（例如，略過必要欄位時或輸入不正確格式的資料時），最好在控制項附近使用控制項驗證或意見反應，而不是使用封鎖快顯視窗錯誤對話方塊。

### <a name="field-validation"></a>欄位驗證
 表單和欄位驗證是由三個元件所組成：控制項、圖示和工具提示。 雖然有數種類型的控制項可以使用這種方式，但您也可以使用文字方塊做為範例。

 ![欄位驗證 &#40;空白&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 如果欄位是必要的，則應該要有浮水印文字， **\<Required>** 而欄位背景應該是淺黃色 (VSColor： `Environment.ControlEditRequiredBackground`) ，而且前景應為灰色 (VSColor： `Environment.ControlEditRequiredHintText`) ：

 ![具有 [必要] 標籤的欄位驗證](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 此程式可判斷當焦點移至另一個控制項時，或當使用者按一下 [確定] 認可按鈕時，或當使用者儲存檔或表單時，控制項所 *輸入的內容無效* 的狀態。

 當判斷出不正確內容狀態時，圖示會出現在控制項內或在它的旁邊。 顯示錯誤的工具提示應該會出現在 [圖示] 或 [控制項] 的游標處。 此外，建立無效狀態的控制項周圍應該會出現一個1圖元的框線。

 ![欄位驗證版面配置規格](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **欄位驗證的版面配置規格**

#### <a name="acceptable-variations-for-icon-location"></a>圖示位置可接受的變化
 在無數的情況下，使用者必須收到驗證錯誤的相關資訊。 考慮 UI 的控制項類型和設定，請選擇適合您情況的圖示位置。

 ![圖示位置可接受的位置](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **欄位驗證圖示位置可接受的變化**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>需要往返伺服器或網路連接的驗證
 在某些情況下，需要伺服器的來回行程才能確認內容，而且請務必顯示使用者進度、驗證和錯誤狀態。 下圖顯示此案例的範例和建議的 UI。

 ![需要來回伺服器的驗證](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **需要來回伺服器的驗證**

 請注意，必須提供控制項右邊的足夠可用空間，才能容納「正在驗證 ...」和「重試」文字。

#### <a name="in-place-warning-text"></a>就地警告文字
 當有可用空間可將錯誤訊息放在錯誤狀態中的控制項附近時，最好是單獨使用工具提示。

 ![在&#45;放置警告](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **就地警告文字**

#### <a name="watermarks"></a>浮水印
 有時候整個控制項或視窗都處於錯誤狀態。 在此情況下，請使用浮水印來指出錯誤。

 ![浮水印](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **浮水印欄位驗證**
