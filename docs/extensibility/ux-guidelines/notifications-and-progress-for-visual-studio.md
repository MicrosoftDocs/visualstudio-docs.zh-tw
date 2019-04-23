---
title: 通知和適用於 Visual Studio 的進度 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc5ddb4561c2c353271babe590a9e5b2b3c2e510
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044286"
---
# <a name="notifications-and-progress-for-visual-studio"></a>通知和適用於 Visual Studio 的進度
## <a name="BKMK_NotificationSystems"></a> 通知系統

### <a name="overview"></a>總覽
 有數種方式可以通知使用者發生的事情在 Visual Studio 中有關其軟體開發工作。

 當實作任何一種通知：

- **保留的最小值的通知數目**有效的數字。 通知訊息應該適用於大部分的 Visual Studio 使用者或特定功能/功能區域的使用者。 過度使用的通知可能 sidetrack 使用者，或降低認知的系統的使用便利性。

- **請確定您是要呈現清楚、 可採取動作的訊息**使用者可用來叫用適當的內容，進行更複雜的選擇和採取進一步動作。

- **適當地提供同步和非同步的訊息。** 同步通知表示需要立即處理，例如 web 服務的當機或程式碼擲回例外狀況。 立即的方式強制回應對話方塊中，例如需要他們的意見，這些情況下，應通知使用者。 非同步通知是使用者應該了解，但不需要採取動作立即執行，例如 web 站台部署或建置作業完成時完成。 這些訊息應該更環境並不會中斷使用者的工作流程。

- **使用強制回應對話方塊時所需採取進一步動作時，防止使用者，才**之前認可訊息或對話方塊中來決定。

- **已不再有效時，請移除環境的通知。** 不需要使用者關閉通知，如果他們已經採取來解決的問題所收到的動作。

- **請注意通知，可能會導致錯誤的關聯。** 使用者可能會認為，一或多個其動作已觸發通知時實際上有沒有因果關係。 要清除的通知訊息中有關內容、 觸發程序和通知的來源。

### <a name="choosing-the-right-method"></a>選擇正確方法
 您可以使用此表格來協助您選擇正確的方法，來通知訊息的使用者。

|方法|使用|請勿使用|
|------------|---------|----------------|
|[強制回應的錯誤訊息對話方塊](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|當繼續進行之前，需要使用者回應時使用。|請勿使用時則不需要封鎖使用者，並中斷其流程。 請避免使用強制回應對話方塊，如果可能的話，以顯示訊息，另一個、 較不干擾的方式。|
|[IDE 狀態列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|環境文字資訊狀態相關的處理程序時使用。|請勿使用單獨。 適用於搭配其他意見反應機制。|
|[內嵌資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|在工具視窗或文件視窗中，使用通知進度、 錯誤狀態、 結果和/或可付諸行動的資訊。|請勿使用是否不相關的資訊列所在的位置資訊。<br /><br /> 請勿使用外部文件/工具視窗。|
|[滑鼠游標會變更](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|可用來通知處理程序會在上。 也可用來通知的狀態變更滑鼠，例如滑鼠游標拖放時進行，或處於特定模式，例如繪圖模式。|請勿用於簡短的進度變更，或如果 fluttering 的資料指標有可能 （例如，當繫結至組件的時間執行的處理序而不是整個程序）。|
|[進度指標](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|當您要報告進度 （確定或未定） 時使用。 有各種不同的進度指標類型和每個特定的使用方式。 請參閱[進度指標](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)。||
|[Visual Studio 通知視窗](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|[通知] 視窗不是可公開可擴充的。 不過，它用來通訊的 Visual Studio 中，包括重大的問題，您的授權和資訊性通知更新至 Visual Studio 或套件的相關訊息的範圍。|請勿用於其他類型的通知。|
|[錯誤清單](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|當問題直接與使用者的目前開啟的方案，有問題 （錯誤/警告/資訊） 時，他們可能需要採取動作的程式碼。<br /><br /> 這包括，例如：<br /><br /> 編譯器訊息 （錯誤/警告/資訊）<br /><br /> 關於程式碼的程式碼分析/診斷訊息<br /><br /> -組建訊息<br /><br /> 可能很適合使用與專案或方案檔案的相關問題，但是先考慮的方案總管 中的指示。|請勿用於沒有任何關聯的使用者開啟的方案程式碼的項目。|
|編輯器通知：燈泡|當您有可供解決中開啟的檔案有問題的修正時使用。<br /><br /> 請注意燈泡也應該用來裝載快速動作會建立依需求，例如重構，使用者程式碼，但在此情況下不會出現 「 通知樣式 」。|請勿使用開啟的檔案沒有任何關聯的項目。|
|編輯器通知：波浪線|使用此選項，來提醒使用者其開啟的程式碼 （例如，紅色曲線的錯誤） 的特定範圍的相關問題。|請勿用於其開啟的程式碼的特定範圍無關的項目。|
|[內嵌的狀態列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|將提供相關內容或內容的特定工具視窗、 文件視窗或對話方塊視窗中的程序的狀態。|請勿用於一般產品通知、 處理序或特定範圍內沒有任何關聯性內容的項目。|
|[Windows 系統匣通知](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|用來呈現通知跨處理序的處理程序或附屬應用程式。|請勿使用與 IDE 的通知。|
|[通知泡泡](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|使用遠端程序的通知，或變更**外部**的 IDE。|請勿用於做為通知使用者的處理程序**內**IDE。|

### <a name="notification-methods"></a>通知方法

#### <a name="BKMK_ModalErrorMessageDialogs"></a> 強制回應的錯誤訊息對話方塊
 強制回應的錯誤訊息對話方塊用來顯示錯誤訊息，要求使用者確認或動作。

 ![強制回應的錯誤訊息](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901年 01_ModalErrorMessage")

 **警示無效的連接字串至資料庫的使用者強制回應的錯誤訊息對話方塊**

#### <a name="BKMK_IDEStatusBar"></a> IDE 狀態列
 使用者注意到狀態列文字的可能性相互關聯全能電腦體驗來與 Windows 平台特定的體驗。 Visual Studio 客戶群，通常會在這兩個區域中，有經驗，但即使是經驗豐富的 Windows 使用者可能會遺漏在狀態列中的變更。 因此，[狀態] 列最適合僅供參考之用，或做為備援提示的資訊顯示在其他位置。 在對話方塊中，或通知工具視窗中，應提供任何一種使用者必須立即解決的重要資訊。

 Visual Studio 的 [狀態] 列被設計來提供要顯示的數種類型的資訊。 它被劃分成的意見反應、 設計工具、 進度列、 動畫和用戶端區域。

 意見反應區域和設計工具區域永遠會顯示。 進度列和動畫區域一定是動態且根據使用者內容。 設計工具區域會有靜態寬度取決於提取來自隨附的資源的文字訊息字串的長度。 這可讓當地語系化，以調整寬度，而不需要變更程式碼。 適用於英文，這個字串的寬度約為 220 的像素。 設計工具區域的正常行為模式和意見反應區域會吸收剩餘的空間。

 [狀態] 列也會加入視覺趣味和功能的值由通訊，例如當 IDE 偵錯模式中的各種 IDE 狀態變更以色彩標示。

 ![IDE 狀態列色彩變更](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901年 02_IDEStatusBar")

 **IDE 狀態列色彩**

#### <a name="BKMK_EmbeddedInfobar"></a> 內嵌資訊列
 資訊列可以使用頂端的文件視窗或工具視窗，向使用者提示的狀態或條件。 它也可以提供命令，讓使用者可以有一個方法可以輕鬆地採取動作。 資訊列是標準的 shell 控制項。 請避免建立您自己，會採取行動，並會出現與其他人在 IDE 中不一致。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)實作詳細資料和使用指引。

 ![內嵌資訊列](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901年 03_EmbeddedInfobar")

 **資訊列會內嵌在文件視窗中，警示的使用者，IDE 會在 歷程偵錯模式中，並如同在標準偵錯模式中，編輯器不會在相同的方式回應。**

#### <a name="BKMK_MouseCursorChanges"></a> 滑鼠游標會變更
 將滑鼠游標變更，當使用繫結至 VSColor service，並已與資料指標相關聯的色彩。 游標會變更可用於指出進行中作業，以及叫用使用者停留所在可以拖曳、 置放，或用來選取物件的目標區域。

 前提是必須保留的作業，來表示任何進一步的輸入時，防止使用者的所有可用的 CPU 時間，請使用忙碌/等候滑鼠資料指標。 在大部分情況下，撰寫完善的應用程式使用多執行緒處理，當使用者將無法執行其他作業的時間應該很少見。

 請注意，游標會變更有很有用，因為多餘的資訊提示會顯示其他位置。 請勿依賴資料指標變更為至關重要的使用者必須解決的唯一方式與使用者通訊，尤其是要傳達的項目。

#### <a name="BKMK_NotSysProgressIndicators"></a> 進度指標
 進度指標需要超過幾秒鐘的時間才能完成的處理程序期間提供的使用者意見反應至關重要。 可顯示進度指標就地 （附近的啟動點的動作進行中），在內嵌的狀態列中、 在強制回應對話方塊中，或在 Visual Studio 的 [狀態] 列中。 請依照下列中的指導方針[進度指標](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)關於其使用與實作。

#### <a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio 通知視窗
 Visual Studio 通知視窗通知關於授權、 環境 (Visual Studio)，擴充功能和更新的開發人員。 使用者可以關閉個別的通知，或可以選擇忽略特定類型的通知。 在管理清單中，已忽略的通知**工具 > 選項**頁面。

 [通知] 視窗不是目前可延伸的。

 ![Visual Studio 通知視窗](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901年 06_VSNotificationsWindow")

 **Visual Studio 通知工具視窗**

#### <a name="BKMK_ErrorList"></a> 錯誤清單
 錯誤清單中的通知會指出錯誤和警告發生在編譯期間，或建置程序，並可讓使用者瀏覽至該特定程式碼錯誤的程式碼中。

 ![錯誤清單](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901年 08_ErrorList")

 **在 Visual Studio 中的錯誤清單**

#### <a name="BKMK_EmbeddedStatusBars"></a> 內嵌的狀態列
 IDE 狀態列為動態磁碟，以設定為使用中的文件視窗和資訊更新使用者的內容和/或系統回應其用戶端區域內容，因為很難維護資訊以持續顯示，或提供長期狀態非同步處理序。 比方說，IDE 狀態列不適當的多個執行及/或立即採取行動的項目選取項目執行的測試結果的通知。 請務必保留使用者進行選取，或啟動的處理序之文件或工具 視窗的內容中的這類狀態資訊。

 ![Embedded status bar](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **在 Visual Studio 中的內嵌的狀態列**

#### <a name="BKMK_WindowsTray"></a> Windows 系統匣通知
 Windows 通知區域位於旁邊系統時鐘在 Windows 工作列上。 許多公用程式和軟體元件提供此區域中的圖示，讓使用者可以取得整個系統的工作，例如變更螢幕解析度，或取得軟體更新的內容功能表。

 應該在 Visual Studio 通知中樞，而不 Windows 通知區域中提出環境層級通知。

#### <a name="BKMK_NotificationBubbles"></a> 通知泡泡
 通知泡泡可以顯示成編輯器/設計工具內的參考用訊息，或做為 Windows 通知區域的一部分。 使用者視為這些泡泡它們之後，就可以解決的問題即非關鍵的通知的權益。 泡泡會適當的使用者就必須立即解決的重要資訊。 如果您在 Visual Studio 中使用通知泡泡，請遵循[通知泡泡的 Windows 桌面指引](/windows/desktop/uxguide/mess-notif)。

 ![通知泡泡](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901年 07_NotificationBubbles")

 **使用適用於 Visual Studio 的 Windows 通知區域中的通知泡泡**

## <a name="BKMK_ProgressIndicators"></a> 進度指標

### <a name="overview"></a>總覽
 進度指示器都是提供使用者意見反應的通知系統很重要的一部分。 它們會告知使用者何時完成處理程序和作業。 熟悉的指標類型包括進度列、 旋轉的資料指標和動畫的圖示。 型別和進度列指示器的位置取決於內容，包括報告的內容和多久程序或作業才會完成。

#### <a name="factors"></a>因素
 為了判斷適合哪一個指標類型，您必須判斷下列因素。

1. **執行時間：** 作業所花的時間長度

2. **強制回應性：** 作業是強制性的環境 （鎖定 UI 程序完成之前）

3. **永續/暫時性：** 是否必須是時間較晚的報告及/或檢視進度的最終結果

4. **確定/未定：** 是否可以計算作業結束時間和進度

5. **圖形/Textual 位置：** 進度或處理程序是否擷取的內嵌訊息時或特定的控制項，例如樹狀結構控制項中的主體

6. **鄰近：** 進度應位於鄰近性與其相關的 UI。 （比方說，它可以在 [狀態] 列，可能會很遠的位置，或沒有要附近的按鈕，啟動處理序嗎？）

#### <a name="determinate-progress"></a>確定的進度

|進度型別|何時及如何使用|注意|
|-------------------|-------------------------|-----------|
|（確定） 的進度列|預期的持續時間 > 5 秒。<br /><br /> 可能包含處理序詳細資料的文字的描述。|**不**嵌入動畫中的文字。|
|資訊列|訊息內容的 UI 相關聯。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。<br /><br /> 可能包含處理序詳細資料的文字的描述。|**不**使用多個資訊列，當您想要表示多個處理序。 請改用堆疊的進度列。|
|輸出視窗|暫時性通知： 應用程式層級程序，使用者想要**檢閱**之後完成的詳細資料。|**不**如果使用者將需要稍後參考資料使用。|
|記錄檔|很重要時，搭配 intransient 的通知，萬一**儲存**之後完成的詳細資料。||
|狀態列|暫時性通知： 應用程式層級程序，使用者將會**不需要**之後完成的詳細資料。<br /><br /> 包含內嵌的進度列。<br /><br /> 可能包含處理序詳細資料的文字的描述。||

#### <a name="indeterminate-progress"></a>不確定的進度

|進度型別|何時及如何使用|注意|
|-------------------|-------------------------|-----------|
|進度列 （不定）|預期的持續時間 > 5 秒。<br /><br /> 可能包含處理序詳細資料的文字的描述。|**不**嵌入動畫中的文字。|
|Ants （水平點動畫）|往返伺服器。<br /><br /> 放置 near 點內容的父容器的頂端。|**不**如果沒有成為父代的整個容器使用。|
|微調按鈕 （進度環）|使用內容的 UI，或其中的空間是考量相關聯的處理程序。<br /><br /> 可能包含處理序詳細資料的文字的描述。||
|資訊列|訊息內容的 UI 相關聯。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。|**不**使用多個資訊列，當您想要表示多個處理序。 請改用堆疊的進度列。|
|輸出視窗|暫時性通知： 應用程式層級程序，使用者會想要**檢閱**之後完成的詳細資料。|**不**用於需要工作階段之間保存的資訊。|
|記錄檔|很重要時，搭配 intransient 的通知，萬一**儲存**之後完成的詳細資料。||
|狀態列|暫時性通知： 應用程式層級程序，使用者將會**不需要**之後完成的詳細資料。<br /><br /> 包含內嵌的進度列。<br /><br /> 可能包含處理序詳細資料的文字的描述。||

### <a name="progress-indicator-types"></a>進度指標類型

#### <a name="progress-bars"></a>進度列

##### <a name="indeterminate"></a>不定
 ![不確定的進度列](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901年 04_Indeterminate")

 **不確定的進度列**

 「 不定 」 表示作業的整體進度，或無法判斷處理程序。 針對需要無限制的一段時間的作業使用不確定的進度列，或存取物件的數目為 「 不明 」。 您可以使用的文字描述，伴隨發生的事情。 您可以使用逾時，為範圍提供時間為基礎的作業。 不確定的進度列會使用動畫來顯示進度正在進行，但未提供其他資訊。 不會選擇只根據單獨的精確度可能缺乏不確定的進度列。

##### <a name="determinate"></a>確定
 ![確定的進度列](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901年 05_Determinate")

 **確定的進度列**

 「 確定 」 表示 操作或處理程序，需要在限定的一段時間，即使無法準確預測的時間量。 清楚地表示完成。 不要讓進度列，除非在作業完成，請移至 100%。 確定的進度列動畫會移動左到右從 0 到 100%。

 永遠不會移動回溯作業期間的進度列指示器。 在列應該向前移動而持續穩定增加作業開始和結束時達到 100%。 進度列的重點是要讓使用者了解整個作業需要多久，不論涉及多少的步驟。

##### <a name="concurrent-reporting-stacked-progress-bars"></a>並行報告 （堆疊的進度列）
 如果作業需要很長的時間-或許可能使用幾個分鐘-則兩個進度列，其中一個，會顯示作業的整體進度，另一個用於目前步驟的進度。 比方說，如果安裝程式正在複製許多檔案，然後一個進度列可用來表示花多少時間的整個程序而第二個可能表示目前檔案的多少百分比，或複製的目錄。 不會報告超過五個並行作業或使用堆疊的進度列的程序。 如果您有五個以上的並行作業或報表的處理程序，使用強制回應對話方塊的 [取消] 按鈕和報表進度詳細資料，以 [輸出] 視窗。

##### <a name="textual-descriptions"></a>文字描述
 使用隨附的事情的文字描述和預估的完成時間。 如果無法判斷作業將會花多少時間，則可能是較好的選擇，提供意見反應，動畫的圖示，而不是一個進度列。

 Visual Studio 提供可供任何產品如果要整合至 Visual Studio 的狀態列中的標準進度列。 如需的情況時，進度列以動畫顯示的文字描述，可以更新狀態列文字。

#### <a name="other-progress-indicators"></a>其他的進度指示器

##### <a name="ants-animated-horizontal-dots"></a>Ants （水平點動畫）
 ![進度 ants](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903年 01_Ants")

 "Ants，「 動畫水平的點，提供視覺上的參考不定的反覆存取伺服器處理序。

##### <a name="spinner-progress-ring"></a>微調按鈕 （進度環）
 ![進度微調按鈕](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903年 02_Spinner")

 微調按鈕 （也稱為 「 進度環 」） 是主要是使用與內容相關的 UI 不確定的進度指示器。 接近其相關的內容，例如文字分類標頭、 訊息、 或控制項中顯示微調按鈕。

##### <a name="cursor-feedback"></a>資料指標的意見反應
 對於需要 2 到 7 秒的作業，提供資料指標的意見反應。 一般而言，這表示使用由作業系統提供將等待游標。 如需指引，請參閱 MSDN 文章[Cursors.Wait 屬性](/dotnet/api/system.windows.input.cursors.wait)。

#### <a name="progress-indicator-locations"></a>進度指標位置

##### <a name="status-bar"></a>狀態列
 [狀態] 列可讓您的應用程式為向使用者顯示訊息和有用的資訊，而不會中斷使用者的工作。 通常顯示在視窗底部，進度的狀態將會包含有關進度的量值的訊息搭配一個進度列指示器的工具提示窗格。

 ![具有進度列的狀態列](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903年 03_StatusBarProgressBar")

 **具有進度列的 [狀態] 列**

 ![具有傳訊的狀態列](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903年 04_StatusBarMessage")

 **提供文字說明的 [狀態] 列**

##### <a name="infobar"></a>資訊列
 類似於 [狀態] 列中，資訊列提供內容相關的通知和傳訊，這也可以搭配不確定的進度指標，例如進度列或微調。 資訊列時，不應提供細微的層級進行或確定的進度指示。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。

 ![具有進度列和傳訊的資訊列](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903年 05_InfoBar")

 **具有進度列和文字描述的資訊列**

 ![視窗內的資訊列](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903年 06_InfoBarInWindow")

##### <a name="inline"></a>內嵌
 內嵌進度指示可以表示任何進度載入器型別。 進度列指示器通常搭配訊息，但這不是需求。

 ![內嵌進度微調按鈕](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903年 07_InlineSpinner")

 **結合文字描述的微調按鈕**

 ![內嵌堆疊進度列](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903年 08_InlineStackedProgress")

 **確定堆疊的進度列**

 ![內嵌進度傳訊](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903年 09_InlineText")

 **伺服器總管內嵌文字：正在重新整理...**

##### <a name="tool-windows"></a>工具視窗
 位於工具列的正下方的不確定的進度列表示全域進度指示。

 ![全域不確定的進度列](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903年 23_GlobalIndeterminate")

 **Team Explorer 全域不確定的進度列**

##### <a name="dialogs"></a>對話方塊
 對話方塊可以包含任何進度載入器類型。 進度指標可以是搭配傳訊，以及結合多個層級的細微的表示及子程序的進度指示。

 ![具有多個進度指標類型的對話方塊](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903年 11_Dialog")

 **與並行處理多個進度指標類型的 visual Studio 對話方塊**

 ![具有進度載入器和傳訊的對話方塊](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903年 12_Dialog2")

 **具有進度載入器和傳訊內嵌命令的 visual Studio 對話方塊**

##### <a name="document-well"></a>文件區域
 文件也可以顯示多個進度載入器類型與控制項的組合。

 ![中的進度傳訊文件也](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903年 13_DocumentWell")

 **工具列下方的不確定的進度列**

##### <a name="output-window"></a>輸出視窗
 [輸出] 視窗也適用於處理程序進展和透過內嵌文字訊息的進行中的進度狀態。 您應該使用 [狀態] 列，以及任何輸出視窗進度報告。

 ![輸出視窗中的進度傳訊](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903年 14_OutputWindow")

 **進行中的處理序狀態與輸出視窗，並等候訊息**

## <a name="BKMK_Infobars"></a> 資訊列

### <a name="overview"></a>總覽
 資訊列提供使用者注意點接近指標，並使用共用的資訊列控制項可確保一致的視覺外觀和互動。

 ![Infobar](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **在 Visual Studio 中的資訊列**

#### <a name="appropriate-uses-for-an-infobar"></a>適當使用資訊列

- 若要授與使用者目前的內容相關的非封鎖式但重要訊息

- 若要表示 UI 處於特定狀態或條件，會帶來一些互動的影響，例如歷程偵錯

- 若要通知使用者系統已偵測到的問題，例如當擴充功能造成效能問題

- 若要提供使用者一個可以輕鬆地採取動作，例如當編輯器偵測到的檔案有混合的定位點和空格

##### <a name="do"></a>執行動作：

- 簡單地說，點，請保留資訊列訊息文字。

- 保持簡潔的上連結和按鈕的文字。

- 請確定您提供給使用者的 「 動作 」 選項很低，顯示必要的動作。

##### <a name="dont"></a>沒有此項目：

- 您可以使用資訊列，提供標準應放在工具列中的命令。

- 使用資訊列來強制回應對話方塊取代。

- 建立浮動視窗外部訊息。

- 在相同的視窗內的數個位置中使用多個資訊列。

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>可以將多個資訊列顯示在相同的時間
 是，可以顯示多個資訊列，在相同的時間。 它們會與第一個顯示以下的上方和其他資訊列顯示的資訊列顯示，以先服務的順序。

 使用者會看到三個資訊列最多一次之後，如果多個資訊列可供使用，資訊列區域將會變成可捲動。

### <a name="creating-an-infobar"></a>建立資訊列
 資訊列已從左到右的四個區段：

- **圖示：** 這是您可以在其中加入的任何圖示要顯示的資訊列，例如警告圖示。

- **文字：** 如有需要，您可以新增的文字描述的案例/情況使用者是，以及在的文字中的連結。 請務必保持簡潔的文字。

- **動作：** 此區段應該包含連結和按鈕，使用者可以在您的資訊列中採取的動作。

- **[關閉] 按鈕：** 右邊的最後一節中可以有 [關閉] 按鈕。

#### <a name="creating-a-standard-infobar-in-managed-code"></a>在 managed 程式碼中建立標準的資訊列
 InfoBarModel 類別可用來建立資料來源的資訊列。 使用其中一個這些四個建構函式：

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

 以下是範例會建立 InfoBarModel 部分文字具有超連結、 動作按鈕和圖示。

 ![具有超連結的資訊列](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904年 02_InfobarHyperlink")

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>在 原生程式碼中建立標準的資訊列
 實作 IVsInfoBar 介面，以提供原生程式碼資訊列。

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>從 資訊列中取得資訊列 UIElement
 InfoBarModel 或 IVsInfoBar 實作都必須轉換成 UIElement，若要顯示在 UI 中的資料模型。 將 uielement 設可以擷取與 SVsInfoBarUIFactory/IVsInfoBarUIFactory 服務。

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
 可以顯示資訊列，在一或多個下列位置：

- 工具視窗

- 內文件索引標籤

> [!IMPORTANT]
>  可以定位資訊列提供給全域內容的相關訊息。 工具列和文件區域之間會出現此選項。 這因為這會導致 「 跳和 jerk 」 的問題不建議使用的 IDE，應該加以避免，除非絕對必要且適當。

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>資訊列置於 ToolWindowPane
 ToolWindowPane.AddInfoBar(IVsInfoBar) 方法可用來加入工具視窗中的資訊列。 此 API 可以將新增的 IVsInfoBar （哪些 InfoBarModel 為預設的實作），或 IVsUIElement。

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>置於文件或非 ToolWindowPane 的資訊列
 若要將放置任何 IVsWindowFrame 資訊列，使用 ivswindowframe.getproperty 屬性來取得 IVsInfoBarHost 框架，然後再加入資訊列 UIElement。

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

#### <a name="placing-an-infobar-in-the-main-window"></a>資訊列置於主視窗
 要置於主視窗中的資訊列，使用的 ivsshell 出現服務 VSSPROPID_MainWindowInfoBarHost 取得主視窗的 IVsInfoBarHost，然後再加入資訊列 UIElement 給它。

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>我知道當使用者採取動作，在 我的資訊列？
 是，我們會傳回每個事件的動作為 資訊列作者。 然後是由在 IDE 中根據使用者在資訊列中選取採取動作的資訊列作者。 資訊列將從主應用程式的 [關閉] 按鈕已按下，會自動移除，但如果之後要移除的其他資訊列需要關閉，則需要額外的工作。 遙測也會需要每個資料列會獨立記錄。

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>在 ToolWindowPane 事件的接收資訊列
 ToolWindowPane 有兩個事件的資訊列。 關閉資訊列 ToolWindowPane 中的時，會引發 InfoBarClosed 事件。 按一下超連結或按鈕在資訊列時，會引發 InfoBarActionItemClicked 事件。

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>資訊列之事件的接收直接從 UIElement
 IVsInfoBarUIElement.Advise 可用來直接從資訊列的 UIElement 訂閱事件。 實作 IVsInfoBarUIEvents，可讓作者以關閉接收，然後按一下事件。

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="BKMK_ErrorValidation"></a> 驗證錯誤
 當使用者輸入不是可接受的例如必要的欄位就會略過或輸入資料格式不正確的資訊時，最好是使用控制驗證或意見反應，而不是使用封鎖的快顯錯誤對話方塊在控制項旁邊。

### <a name="field-validation"></a>欄位驗證
 表單和欄位的驗證是由三個元件所組成： 控制項、 一個圖示和工具提示。 雖然數種類型的控制項可以使用這個，文字方塊將用於做為範例。

 ![欄位驗證&#40;空白&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905年 01_FieldValidation")

 如果欄位是必要的應該要有加上浮水印文字指出**\<必要 >** 且欄位背景應指示燈黃色 (VSColor: `Environment.ControlEditRequiredBackground`) 和前景應為灰色 (VSColor: `Environment.ControlEditRequiredHintText`):

 ![欄位與 [必要] 標籤的驗證](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905年 02_FieldValidationRequired")

 程式可以判斷控制項是否處於的狀態為*輸入無效的內容*當焦點移到另一個控制項，或當使用者按一下 [確定] 認可 按鈕，或當使用者儲存文件或表單。

 無效的內容狀態決定，只要在控制項內，或只是它旁邊就會出現一個圖示。 描述錯誤的工具提示應該會出現暫留時的圖示或控制項。 此外，應該會建立無效的狀態的控制項周圍會出現 1 像素框線。

 ![欄位驗證版面配置規格](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905年 03_LayoutSpecs")

 **欄位驗證版面配置規格**

#### <a name="acceptable-variations-for-icon-location"></a>可接受的變化，圖示位置
 有無數的唯一情況，使用者需要以瞭解驗證錯誤。 考慮的控制項類型和組態 UI 中，選擇適用於您情況的圖示位置。

 ![可接受的圖示位置的位置](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905年 04_IconLocation")

 **欄位驗證圖示位置可接受的變化**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>需要往返伺服器或網路連線的驗證
 在某些情況下，往返伺服器，才可確認其內容，並會顯示錯誤狀態與使用者進行驗證，請務必。 下圖顯示此案例和建議的 UI 的範例。

 ![驗證涉及在伺服器之間往返](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905年 05_RoundTrip")

 **涉及往返伺服器的驗證**

 請注意，必須提供足夠的可用空間，右邊的控制項，來因應的 [驗證] 和 [重試] 文字。

#### <a name="in-place-warning-text"></a>就地警告文字
 當有足夠的空間可用來將錯誤訊息，接近控制項放在錯誤的狀態時，這是使用單獨的工具提示。

 ![在&#45;警告](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905年 06_InPlaceWarning")

 **就地警告文字**

#### <a name="watermarks"></a>浮水印
 有時候整個控制項或視窗，則處於錯誤狀態。 在此情況下，使用水位線以指出錯誤。

 ![Watermark](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **浮水印欄位驗證**