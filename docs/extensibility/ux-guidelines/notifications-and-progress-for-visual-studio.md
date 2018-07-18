---
title: 通知和 Visual Studio 進行 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 237ed5c382a6ac880b0be59165a33ad338370976
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148437"
---
# <a name="notifications-and-progress-for-visual-studio"></a>通知和 Visual Studio 的進度
##  <a name="BKMK_NotificationSystems"></a> 通知系統  
  
### <a name="overview"></a>總覽  
 有幾種方式來通知使用者發生什麼事 Visual Studio 中對於軟體開發工作。  
  
 在實作任何一種通知：  
  
-   **保留的最少的通知數目**有效數字。 通知訊息應該套用至大部分的 Visual Studio 使用者或使用者的特定功能/功能區域。 過度使用的通知可能 sidetrack 使用者，或降低認知的容易使用的系統。  
  
-   **請確定您要呈現清除，即訊息**使用者可用來叫用適當的內容中更複雜的選項和採取進一步動作。  
  
-   **適當地呈現同步和非同步的訊息。** 同步通知表示發生需要立即處理，例如 web 服務發生當機或程式碼擲回例外狀況。 使用者應該了解這些情況下，立即以要求其輸入，例如強制回應對話方塊的方式。 非同步通知為的使用者應該了解，但不是需要作用於立即，例如 web 站台部署或建置作業完成時完成。 這些訊息應該更環境並不會中斷使用者的工作流程。  
  
-   **使用強制回應對話方塊時所需採取進一步動作時，防止使用者，才**之前認可訊息，或在對話方塊中的決定。  
  
-   **已不再有效時，請移除環境的通知。** 不需要使用者如果它們已採取動作來解決的問題已收到關閉通知。  
  
-   **請注意通知可能會導致產生錯誤的關聯。** 使用者可能會認為的一或多個其動作已經觸發通知時事實上是沒有因果關係。 要清除的通知訊息中有關內容、 觸發程序和通知的來源。  
  
### <a name="choosing-the-right-method"></a>選擇正確方法  
 您可以使用此表格來協助您選擇正確的方法，來通知您郵件的使用者。  
  
|方法|使用|請勿使用|  
|------------|---------|----------------|  
|[強制回應的錯誤訊息對話方塊](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|當繼續進行之前，需要使用者回應時使用。|請勿使用時不需要封鎖使用者並中斷其流程。 請避免使用強制回應對話方塊，最好盡可能以顯示訊息，另一個、 較具侵入性的方式。|  
|[IDE 狀態列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|環境文字狀態相關的處理序的資訊時使用。|請勿單獨。 適用於搭配其他意見反應機制。|  
|[內嵌資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|在工具視窗或文件視窗中，使用通知的進度、 錯誤狀態、 結果，及/或可付諸行動之資訊。|請勿使用如果沒有與放置資料列的位置相關資訊。<br /><br /> 請勿使用外部文件/工具視窗。|  
|[滑鼠游標會變更](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|可能用來通知處理程序正在進行的作業。 也可用來通知是狀態變更滑鼠，例如滑鼠游標拖/放時進行，或中處於特定模式，例如繪圖模式。|不使用簡短進行變更，或如果 fluttering 的資料指標有可能 （例如，當繫結至組件的時間執行的處理序而不是整個程序）。|  
|[進度指標](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|當您要報告進度 （確定或未定） 時使用。 有各種不同的進度指標類型和每個特定的使用方式。 請參閱[進度指標](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)。||  
|[Visual Studio 通知視窗](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|[通知] 視窗不是可公開可擴充的。 不過，它用來傳達有關 Visual Studio，包括重大的問題與您的授權資訊更新至 Visual Studio 或套件的通知訊息的範圍。|請勿使用其他類型的通知。|  
|[錯誤清單](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|當問題直接相關的使用者有問題 （錯誤/警告/資訊） 目前開啟的方案時，他們可能需要的程式碼上採取的動作。<br /><br /> 這包括，例如：<br /><br /> 編譯器訊息 （錯誤/警告/資訊）<br /><br /> 程式關於程式碼的碼分析器/診斷訊息<br /><br /> 建置訊息<br /><br /> 可能是適用於專案或方案檔案，與相關的問題，但先考慮的方案總管 中的指示。|請勿使用不具有任何關聯的使用者開啟的方案程式碼項目。|  
|編輯器通知： 燈泡|當您有可供解決中開啟的檔案有問題的修正時使用。<br /><br /> 請注意燈泡也能用來裝載所持有的重構功能，例如視使用者的程式碼，但在此情況下不會出現 「 通知樣式。"的快速動作|請勿使用開啟的檔案沒有任何關聯的項目。|  
|編輯器通知： 波浪線|使用來提醒使用者開啟程式碼 （例如，紅色波浪線的錯誤） 的特定範圍的相關問題。|請勿使用開啟的程式碼的特定範圍無關的項目。|  
|[內嵌的狀態列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|使用提供的內容或內容的特定工具視窗、 文件視窗或對話方塊視窗中的程序相關的狀態。|請勿用於一般產品通知、 處理序或特定的視窗內沒有任何內容關聯的項目。|  
|[Windows 系統匣通知](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|用來呈現跨處理序的處理程序通知或附屬應用程式。|請勿使用與 IDE 的通知。|  
|[通知泡泡](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|使用遠端程序的通知，或變更**外**的 IDE。|請勿使用來通知使用者的處理序**內**IDE。|  
  
### <a name="notification-methods"></a>通知方法  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a> 強制回應的錯誤訊息對話方塊  
 強制回應的錯誤訊息對話方塊用來顯示錯誤訊息，要求使用者確認或動作。  
  
 ![強制回應的錯誤訊息](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901年 01_ModalErrorMessage")  
  
 **警示無效的連接字串至資料庫的使用者強制回應的錯誤訊息對話方塊**  
  
####  <a name="BKMK_IDEStatusBar"></a> IDE 狀態列  
 使用者注意到狀態列文字的可能性相互關聯其全能電腦體驗，以及特定 Windows 平台的經驗。 Visual Studio 客戶往往會有兩個區域中，有經驗，但即使經驗豐富的 Windows 使用者可能會因此喪失狀態列中的變更。 因此，[狀態] 列最適合僅供參考之用，或做為備援提示的其他位置顯示資訊。 通知工具視窗或對話方塊中，應提供任何類型的使用者必須立即解決的重要資訊。  
  
 Visual Studio 的 [狀態] 列被設計來顯示可供數種類型的資訊。 它被分割成區域的意見反應、 設計工具、 進度列、 動畫和用戶端。  
  
 意見反應區域和設計工具區域永遠會顯示。 進度列和動畫區域永遠是動態而且根據使用者內容。 設計工具區域都有靜態寬度取決於提取來自隨附的文字訊息的資源字串的長度。 這可讓當地語系化，以調整寬度，而不需要變更程式碼。 英文的寬度，這個字串的大約為 220 像素。 設計工具區域的正常行為，並且意見反應區域會吸收剩餘的空間。  
  
 [狀態] 列也標示有色彩藉由通訊各種 IDE 狀態變更，例如當 IDE 偵錯模式中加入視覺趣味和功能的值。  
  
 ![IDE 狀態列色彩變更](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901年 02_IDEStatusBar")  
  
 **IDE 狀態列色彩**  
  
####  <a name="BKMK_EmbeddedInfobar"></a> 內嵌資訊列  
 任何可用頂端的文件視窗或工具視窗來通知使用者的狀態或條件。 它也可以提供命令，讓使用者可以有方法可輕鬆地採取的動作。 資訊列是標準 shell 控制項。 應避免建立您自己，以處理並顯示與其他人在 IDE 中不一致。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)實作詳細資料和使用指引。  
  
 ![內嵌資訊列](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901年 03_EmbeddedInfobar")  
  
 **資訊列會內嵌在文件視窗中，警示使用者 IDE 歷程偵錯模式中，且編輯器 中將不會回應相同的方式與在標準偵錯模式中。**  
  
####  <a name="BKMK_MouseCursorChanges"></a> 滑鼠游標會變更  
 將滑鼠游標變更，當使用繫結到 VSColor 服務，而且已與資料指標相關聯的色彩。 游標會變更用於表示進行中作業，以及叫用使用者停留所在可以拖曳、 置放，或用來選取物件的目標區域。  
  
 只有在所有可用的 CPU 時間必須保留為作業，防止使用者來表示任何進一步的輸入時，請使用等候忙碌滑鼠游標。 編寫完善的應用程式使用多執行緒與大部分的情況下，當使用者將無法執行其他作業的時間應該很少見。  
  
 請記住，游標會變更是相當有用的資訊有重複提示呈現其他位置。 請勿依賴游標變更為必須解決的使用者嘗試傳遞的項目時，特別是，與使用者通訊的唯一方式。  
  
####  <a name="BKMK_NotSysProgressIndicators"></a> 進度指標  
 進度指標很重要需要超過幾秒鐘的時間才能完成的處理程序期間提供的使用者意見反應。 您可以顯示進度指標就地 （附近的啟動點的動作進行中），內嵌的狀態列、 強制回應對話方塊中，或在 Visual Studio 狀態列中。 請依照下列中的指導方針[進度指標](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)關於其使用與實作。  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio 通知視窗  
 Visual Studio 通知視窗通知開發人員授權、 環境 (Visual Studio)、 延伸及更新。 使用者可以關閉個別通知，或可以選擇忽略特定類型的通知。 已忽略的通知清單中管理**工具 > 選項**頁面。  
  
 [通知] 視窗不是目前可延伸的。  
  
 ![Visual Studio 通知視窗](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901年 06_VSNotificationsWindow")  
  
 **Visual Studio 通知工具視窗**  
  
####  <a name="BKMK_ErrorList"></a> 錯誤清單  
 錯誤清單中的通知會指出錯誤和警告發生在編譯期間，或建置程序，並可讓使用者瀏覽至該特定程式碼錯誤的程式碼中。  
  
 ![錯誤清單](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901年 08_ErrorList")  
  
 **在 Visual Studio 中的錯誤清單**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a> 內嵌的狀態列  
 IDE 狀態列是動態的其用戶端區域內容設定為使用中的文件視窗和更新使用者的內容和 （或） 系統回應的資訊，因為很難維護連續顯示資訊或提供長期狀態非同步處理序。 例如，IDE 狀態列不適合多執行及/或立即採取行動的項目選取項目執行的測試結果的通知。 請務必保留使用者做的選擇，或啟動的處理序之文件 或 工具 視窗的內容中的這類狀態資訊。  
  
 ![內嵌的狀態列](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901年 09_EmbeddedStatusBar")  
  
 **在 Visual Studio 中的內嵌的狀態列**  
  
####  <a name="BKMK_WindowsTray"></a> Windows 系統匣通知  
 Windows 通知區域旁邊系統時鐘在 Windows 工作列上。 許多公用程式和軟體元件提供此區域中的圖示，如此，使用者可以獲得全系統的工作，例如變更螢幕解析度，或取得軟體更新的內容功能表。  
  
 環境層級通知應該顯示在 Visual Studio 通知中樞，而不 Windows 通知區域中。  
  
####  <a name="BKMK_NotificationBubbles"></a> 通知泡泡  
 通知泡泡會顯示成參考用訊息編輯器/設計工具中，或做為 Windows 通知區域的一部分。 使用者感知這些 （泡泡） 為這些更新版本中，就可以解決的問題是一項優點非關鍵性的通知。 泡泡會適當的使用者就必須立即解決的重要資訊。 如果您使用 Visual Studio 中通知 （泡泡），請遵循[通知泡泡圖的 Windows 桌面指引](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx)。  
  
 ![通知泡泡](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901年 07_NotificationBubbles")  
  
 **使用 Visual Studio Windows 通知區域中的通知泡泡**  
  
##  <a name="BKMK_ProgressIndicators"></a> 進度指標  
  
### <a name="overview"></a>總覽  
 進度指標是很重要的一部分來提供使用者意見反應的通知系統。 程序和操作將會完成時，它們會告訴使用者。 熟悉的指標類型包括進度列、 旋轉的資料指標和動畫的圖示。 類型和位置進度列指示器，取決於需要的內容，包括報告的內容和多久程序或作業完成。  
  
#### <a name="factors"></a>因素  
 若要判斷適當指標類型，您必須判斷下列因素。  
  
1.  **執行時間：** 作業所花的時間長度  
  
2.  **樣式：** 作業是強制性環境 （鎖定，UI 程序完成之前）  
  
3.  **持續的/暫時性：** 進度的最終結果是否需要在稍後會報告和/或檢視  
  
4.  **確定/未定：** 是否可以計算作業的結束時間和進度  
  
5.  **圖形/Textual 位置：** 進度或處理序是否擷取的內嵌，本文的訊息或將特定的控制項，例如樹狀目錄控制項  
  
6.  **鄰近：** 是否進度應該非常接近與相關的 UI。 （比方說，它可以在 [狀態] 列，可能會遠，或者它有要附近的按鈕，啟動處理序嗎？）  
  
#### <a name="determinate-progress"></a>確定的進度  
  
|進行型別|何時及如何使用|注意|  
|-------------------|-------------------------|-----------|  
|進度列 （確定）|預期的持續時間 > 5 秒。<br /><br /> 可能包含文字描述的程序詳細資料。|**不要**嵌入動畫中的文字。|  
|資訊列|訊息內容的 UI 相關聯。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。<br /><br /> 可能包含文字描述的程序詳細資料。|**不要**使用多個資訊列，當您想要表示多個處理序。 請改用堆疊的進度列。|  
|輸出視窗|暫時性的通知： 應用程式層級程序，使用者想要**檢閱**完成後的詳細資料。|**不要**如果使用者將需要在日後參考資料使用。|  
|記錄檔|搭配 intransient 通知的情況下，很重要時**儲存**完成後的詳細資料。||  
|狀態列|暫時性的通知： 應用程式層級程序的使用者將會**不需要**完成後的詳細資料。<br /><br /> 包含內嵌的進度列。<br /><br /> 可能包含文字描述的程序詳細資料。||  
  
#### <a name="indeterminate-progress"></a>不確定的進度  
  
|進行型別|何時及如何使用|注意|  
|-------------------|-------------------------|-----------|  
|進度列 （不定）|預期的持續時間 > 5 秒。<br /><br /> 可能包含文字描述的程序詳細資料。|**不要**嵌入動畫中的文字。|  
|螞蟻 （水平動畫點）|往返伺服器。<br /><br /> 橫跨頂端的父容器中的 near 點的內容。|**不要**如果沒有成為父代整個容器所使用。|  
|微調按鈕 （進度環）|程序與相關聯內容的 UI，或其中的空間是考量的事項。<br /><br /> 可能包含文字描述的程序詳細資料。||  
|資訊列|訊息內容的 UI 相關聯。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。|**不要**使用多個資訊列，當您想要表示多個處理序。 請改用堆疊的進度列。|  
|輸出視窗|暫時性的通知： 應用程式層級處理序該使用者會想要**檢閱**完成後的詳細資料。|**不要**用於需要在工作階段之間保存的資訊。|  
|記錄檔|搭配 intransient 通知的情況下，很重要時**儲存**完成後的詳細資料。||  
|狀態列|暫時性的通知： 應用程式層級程序的使用者將會**不需要**完成後的詳細資料。<br /><br /> 包含內嵌的進度列。<br /><br /> 可能包含文字描述的程序詳細資料。||  
  
### <a name="progress-indicator-types"></a>進度指標類型  
  
#### <a name="progress-bars"></a>進度列  
  
##### <a name="indeterminate"></a>不定  
 ![不確定的進度列](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901年 04_Indeterminate")  
  
 **不確定的進度列**  
  
 「 不定 」 表示作業的整體進度，或無法判斷處理程序。 對於需要無限的時間量的作業使用不確定的進度列或可存取的物件數目不明。 使用的文字描述伴隨著發生什麼事。 使用逾時值，讓範圍以時間為基礎的作業。 不確定的進度列會使用動畫顯示進度正在進行，但未提供其他資訊。 未選擇只根據單獨的精確度可能缺乏的不確定的進度列。  
  
##### <a name="determinate"></a>確定  
 ![確定的進度列](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901年 05_Determinate")  
  
 **確定的進度列**  
  
 「 確定 」 表示 作業或處理程序需要在已繫結一段時間，即使無法準確預測的時間量。 清楚地表示完成。 不要讓進度列，除非在作業完成，請移至 100%。 確定的進度列動畫會移動左到右從 0 到 100%。  
  
 永遠不會移動作業期間回溯進度列指示器。 列應該向前移動穩定作業開始時，並結束時達到 100%。 進度列的重點是要讓使用者了解的整個作業的時間，不論所涉及的步驟數目。  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>並行 reporting （堆疊的進度列）  
 如果作業要花費較長的時間-或許可能使用數個分鐘-則兩個進度列，其中顯示作業的整體進度，以及另一個用於目前步驟的進度。 例如，如果安裝程式正在複製許多檔案，然後一個進度列可用來表示整個程序的時間而第二個表示百分比的目前檔案或目錄複製。 不會報告超過五個並行作業或使用堆疊的進度列處理程序。 如果您有五個以上的並行作業或報表的處理程序，使用強制回應對話方塊的 [取消] 按鈕與報表進度詳細資料，以 [輸出] 視窗。  
  
##### <a name="textual-descriptions"></a>文字描述  
 使用的文字描述伴隨著發生什麼事，預估的完成時間。 如果無法判斷作業將需要多少時間，則可能會比較好的選擇對於提供意見反應，動畫的圖示，而不是將進度列。  
  
 Visual Studio 提供標準進度列可供任何產品整合至 Visual Studio 的狀態列中。 如需進度列的動畫時所發生的文字描述，可以更新狀態列文字。  
  
#### <a name="other-progress-indicators"></a>其他的進度指示器  
  
##### <a name="ants-animated-horizontal-dots"></a>螞蟻 （水平動畫點）  
 ![進度流動外框](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903年 01_Ants")  
  
 "流動外框 」 動畫水平的點，提供不定反覆存取的伺服器處理序的視覺參考。  
  
##### <a name="spinner-progress-ring"></a>微調按鈕 （進度環）  
 ![進度微調按鈕](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903年 02_Spinner")  
  
 微調按鈕 （也稱為 「 進度環 」） 是不確定的進度指示器主要使用相對於內容的 UI。 顯示撥號盤非常接近其相關的內容，例如文字類別標頭、 訊息、 或控制項。  
  
##### <a name="cursor-feedback"></a>資料指標的意見反應  
 需要介於 2 到 7 秒的作業，提供資料指標的意見反應。 一般而言，這表示使用由作業系統提供將等待游標。 如需指引，請參閱 MSDN 文章： [Cursors.Wait 屬性](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx)。  
  
#### <a name="progress-indicator-locations"></a>進度指標位置  
  
##### <a name="status-bar"></a>狀態列  
 [狀態] 列可讓您的應用程式為使用者顯示訊息和有用的資訊，而不會中斷使用者的工作。 通常顯示在視窗底部，進度的狀態將會包含有關進度的量值的訊息與進度列指示器的工具提示窗格。  
  
 ![進度列，[狀態] 列](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903年 03_StatusBarProgressBar")  
  
 **具有進度列的狀態列**  
  
 ![具有傳訊的狀態列](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903年 04_StatusBarMessage")  
  
 **狀態列的文字描述**  
  
##### <a name="infobar"></a>資訊列  
 類似於狀態列，資訊列提供內容的通知和訊息，這也可以搭配不確定的進度指標，例如進度列或微調。 資訊列時，不應提供更細微的層級進行或確定的進度指示。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。  
  
 ![具有進度列和傳訊的資訊列](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903年 05_InfoBar")  
  
 **具有進度列和文字描述的資訊列**  
  
 ![在視窗內的資訊列](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903年 06_InfoBarInWindow")  
  
##### <a name="inline"></a>內嵌  
 內嵌進度指示可以透過任何進度載入器型別表示。 進度列指示器通常搭配訊息，但這並非必要條件。  
  
 ![內嵌進度微調按鈕](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903年 07_InlineSpinner")  
  
 **微調結合文字描述**  
  
 ![內嵌堆疊進度列](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903年 08_InlineStackedProgress")  
  
 **確定堆疊的進度列**  
  
 ![內嵌進度傳訊](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903年 09_InlineText")  
  
 **伺服器總管內嵌文字： 重新整理...**  
  
##### <a name="tool-windows"></a>工具視窗  
 全域進度指示是由位於工具列正下方的不確定的進度列表示。  
  
 ![全域不確定的進度列](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903年 23_GlobalIndeterminate")  
  
 **Team Explorer 全域不確定的進度列**  
  
##### <a name="dialogs"></a>對話方塊  
 對話方塊可以包含任何進度載入器類型。 進度指標可以是搭配傳訊，以及結合多個層級表示細微及子程序的進度指示。  
  
 ![具有多個進度指標類型對話方塊](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903年 11_Dialog")  
  
 **與並行處理序和多個進度指標類型的 visual Studio 對話方塊**  
  
 ![具有進度載入器和傳訊的對話方塊](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903年 12_Dialog2")  
  
 **具有進度載入器和傳訊內嵌指揮的 visual Studio 對話方塊**  
  
##### <a name="document-well"></a>文件區域  
 也在文件可以顯示多個進度載入器類型與控制項一起使用。  
  
 ![中的進度傳訊文件也](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903年 13_DocumentWell")  
  
 **工具列下方的不確定的進度列**  
  
##### <a name="output-window"></a>輸出視窗  
 [輸出] 視窗是適當的處理程序進展和透過內嵌文字訊息的進行中的進度狀態。 您應該使用 [狀態] 列，以及任何輸出視窗進度報告。  
  
 ![輸出視窗中的進度傳訊](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903年 14_OutputWindow")  
  
 **進行中的處理序狀態與輸出視窗，然後等候訊息**  
  
##  <a name="BKMK_Infobars"></a> 資訊列  
  
### <a name="overview"></a>總覽  
 資訊列授與使用者靠近注意其位置的指標，並使用共用的資訊列控制項，以確保一致的視覺外觀和互動。  
  
 ![Infobar](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")  
  
 **在 Visual Studio 中的資訊列**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>資料列的適當用法  
  
-   若要授與使用者目前的內容相關的非封鎖但重要訊息  
  
-   表示 UI 處於特定狀態或執行某些互動顧慮，例如歷程偵錯的條件  
  
-   若要通知使用者，系統偵測到問題，例如當擴充功能會造成效能問題  
  
-   要讓使用者能夠輕鬆地採取動作，例如當編輯器 中偵測到的檔案有混合定位點和空格  
  
##### <a name="do"></a>執行動作：  
  
-   簡單地說，並點，請保留資訊列訊息文字。  
  
-   保持簡潔上連結和按鈕的文字。  
  
-   請確定您提供給使用者的 「 動作 」 選項很低，顯示必要的動作。  
  
##### <a name="dont"></a>不要：  
  
-   您可以使用資訊列來提供標準應放在工具列中的命令。  
  
-   使用資訊列取代強制回應對話方塊。  
  
-   建立浮動視窗外的訊息。  
  
-   使用多個資訊列在相同的視窗內的多個位置。  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>可以將多個資訊列顯示在相同的時間  
 [是]，就可以同時顯示多個資訊列。 它們會顯示先到而來先服務的順序顯示在上方和其他資訊列顯示下列第一個資料列。  
  
 使用者會看到三個資訊列最多一次之後，如果多個資訊列可供使用，資訊列區域將會變成可捲動。  
  
### <a name="creating-an-infobar"></a>建立資料列  
 資料列已從左到右的四個區段：  
  
-   **圖示︰** 這是您可以在其中加入任何圖示您想要顯示的資訊列，例如警告圖示。  
  
-   **文字：** 您可以加入文字說明案例/情況使用者已在中，文字內的連結以及視需要。 請記得保持簡潔的文字。  
  
-   **動作：** 本節應該包含連結和按鈕，使用者可在您的資訊列中的動作。  
  
-   **[關閉] 按鈕：** 右邊最後一個區段都可以擁有 [關閉] 按鈕。  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>在 managed 程式碼中建立標準的資訊列  
 InfoBarModel 類別可以用來建立資料來源的資料列。 使用這些四個建構函式的其中一個：  
  
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
  
 以下是範例會建立 InfoBarModel 與一些文字與超連結、 動作按鈕和圖示。  
  
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
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>在原生程式碼中建立標準的資訊列  
 實作 IVsInfoBar 介面以提供原生程式碼的資訊列。  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>從資料列取得的資訊列 UIElement  
 InfoBarModel 或 IVsInfoBar 實作都必須轉換成 UIElement，若要顯示在 UI 中的資料模型。 UIElement 可以擷取與 SVsInfoBarUIFactory/IVsInfoBarUIFactory 服務。  
  
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
 資訊列可以顯示的一或多個下列位置：  
  
-   工具視窗  
  
-   內文件索引標籤  
  
> [!IMPORTANT]
>  很可能位置的資訊列，提供關於全域內容中的訊息。 工具列和文件區域之間會出現此選項。 這因為這會導致 「 跳和 jerk 」 的問題不建議使用的 IDE，應該加以避免，除非絕對必要且適當的。  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>資訊列置於 ToolWindowPane  
 ToolWindowPane.AddInfoBar(IVsInfoBar) 方法可以用來將資料列加入工具視窗。 此 API 可新增 IVsInfoBar （哪些 InfoBarModel 是預設的實作），或 IVsUIElement。  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>置於文件或非 ToolWindowPane 的資訊列  
 若要將放置任何 IVsWindowFrame 資訊列，使用 ivswindowframe.getproperty 屬性 IVsInfoBarHost 取得框架，然後再加入資訊列 UIElement。  
  
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
 將放置到資訊列在主視窗中，使用的 ivsshell 出現服務 VSSPROPID_MainWindowInfoBarHost 取得主視窗的 IVsInfoBarHost 然後再加入資訊列 UIElement 給它。  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>將知道當使用者採取動作，我資訊列？  
 是，我們會傳回每個事件動作的資訊列作者。 然後會決定要採取的動作依使用者選取資料列在 IDE 中的資訊列作者。 資訊列會自動從主機中移除已按下的 [關閉] 按鈕，但是如果之後要移除的其他資訊列需要關閉，則需要額外的工作。 遙測還需要每個資料列會單獨記錄。  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>ToolWindowPane 中接收的資訊列事件  
 ToolWindowPane 有兩個事件的資訊列。 關閉 ToolWindowPane 中的資訊列時，會引發 InfoBarClosed 事件。 按一下超連結或按鈕在資訊列內時，會引發 InfoBarActionItemClicked 事件。  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>接收的資訊列事件直接從 UIElement  
 IVsInfoBarUIElement.Advise 可以用於直接從資料列的 UIElement 訂閱事件。 實作 IVsInfoBarUIEvents 可讓作者，以關閉接收，然後按一下事件。  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a> 驗證錯誤  
 當使用者輸入不是可接受的例如必要的欄位則會略過，或當資料輸入格式不正確的資訊時，最好使用控制項的驗證或而不是使用封鎖的快顯錯誤對話方塊控制項附近的意見反應。  
  
### <a name="field-validation"></a>欄位驗證  
 表單和欄位的驗證是由三個元件所組成： 控制項、 一個圖示和工具提示。 雖然多種類型的控制項可以使用這個，文字方塊將使用做為範例。  
  
 ![欄位驗證&#40;空白&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905年 01_FieldValidation")  
  
 如果欄位是必要的則應該浮水印文字指出**\<必要 >** 欄位背景應該淺黃色 (VSColor: `Environment.ControlEditRequiredBackground`) 和前景應該是灰色 (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![欄位驗證來搭配 [必要] 標籤](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905年 02_FieldValidationRequired")  
  
 程式可以判斷控制項是否處於的狀態為*輸入無效的內容*當焦點移到另一個控制項，或當使用者按一下 [確定] 認可 按鈕，或當使用者儲存文件或表單。  
  
 決定無效的內容狀態後，在控制項內，或只旁邊會出現一個圖示。 描述錯誤的工具提示應該會出現暫留時顯示的圖示或控制項。 此外，用來建立無效的狀態控制項周圍的 1 像素框線應該會出現。  
  
 ![欄位驗證版面配置規格](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905年 03_LayoutSpecs")  
  
 **欄位驗證版面配置規格**  
  
#### <a name="acceptable-variations-for-icon-location"></a>圖示位置可接受的變化  
 有無數使用者要收到驗證錯誤的相關通知的唯一情況。 控制項型別和組態的使用者介面，請考慮選擇適合您情況的選項圖示位置。  
  
 ![圖示位置可接受位置](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905年 04_IconLocation")  
  
 **欄位驗證圖示位置可接受的變化**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>需要來回伺服器或網路連線的驗證  
 在某些情況下，往返伺服器，才能確認內容，並務必要顯示的使用者進行驗證和錯誤狀態。 下圖顯示此案例與建議的 UI 中的範例。  
  
 ![需要來回伺服器的驗證](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905年 05_RoundTrip")  
  
 **需要來回伺服器的驗證**  
  
 請注意，您必須提供足夠的可用空間，右邊的控制項能夠容納的 [驗證] 和 [重試] 文字。  
  
#### <a name="in-place-warning-text"></a>就地警告文字  
 當有足夠的空間可用來將錯誤訊息，接近控制項放在錯誤的狀態時，這是偏好使用單獨的工具提示。  
  
 ![在&#45;放置警告](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905年 06_InPlaceWarning")  
  
 **就地警告文字**  
  
#### <a name="watermarks"></a>浮水印  
 有時整個控制項或視窗會處於錯誤狀態。 在此情況下，使用浮水印以指出錯誤。  
  
 ![Watermark](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")  
  
 **浮水印欄位驗證**