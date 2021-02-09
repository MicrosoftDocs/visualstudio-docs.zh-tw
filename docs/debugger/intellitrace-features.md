---
title: IntelliTrace 功能 |Microsoft Docs
description: 瞭解 Visual Studio 中的 IntelliTrace 功能。 使用 IntelliTrace 來記錄應用程式中的事件和方法呼叫。
ms.custom: SEO-VS-2020
ms.date: 09/19/2018
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4c974b9056b41de2e021f5918963d1d28ffa3db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905006"
---
# <a name="intellitrace-features-c-visual-basic-c"></a>IntelliTrace 功能 (c #、Visual Basic、c + +) 

您可以使用 IntelliTrace 記錄您應用程式的事件和方法呼叫，以讓您檢查它在執行之不同時間點的狀態 (呼叫堆疊和區域變數值)。 只要像往常一樣開始偵錯工具，預設會開啟 IntelliTrace，而您可以在 [**事件**] 索引標籤下的 [新的 **診斷工具**] 視窗中看到 intellitrace 正在記錄的資訊。選取事件，然後按一下 [**啟用歷程記錄調試** 程式]，以查看針對此事件記錄的呼叫堆疊和區域變數。

如需逐步說明，請參閱[逐步解說：使用 IntelliTrace](../debugger/walkthrough-using-intellitrace.md)。

Visual Studio Enterprise 版本 (而非 Visual Studio Professional 或 Community 版本) 中提供 IntelliTrace。

若要確認已開啟 IntelliTrace，請開啟 [工具] > [選項] > [IntelliTrace] 選項頁面。 預設應該會選取 [啟用 IntelliTrace]。

> [!NOTE]
> [IntelliTrace] 選項頁面上所有設定的範圍是整個 Visual Studio，而不是個別專案或方案。 這些設定的變更會套用至所有 Visual Studio 執行個體、所有偵錯工作階段，以及所有專案或方案。

## <a name="choose-the-events-that-intellitrace-records-c-visual-basic"></a><a name="ChooseEvents"></a> 選擇 IntelliTrace 記錄 (c # Visual Basic 的事件) 

您可以開啟或關閉特定 IntelliTrace 事件的記錄。

如果您正在偵錯，請停止偵錯。 移至 [ **工具 > 選項 > intellitrace > Intellitrace 事件**。 選擇您要 IntelliTrace 記錄的事件。

## <a name="collect-snapshots-c-visual-basic-c"></a><a name="Snapshots"></a> (c #、Visual Basic、c + + 收集快照集) 

依預設不會啟用此功能，但 IntelliTrace 可以在每個中斷點和偵錯工具步驟事件中，捕獲您應用程式的快照集，而且您可以在歷程記錄的偵錯工具中查看這些快照集。 快照集可讓您查看完整的應用程式狀態。 若要啟用快照集的捕獲，請移至 **[工具 > 選項 > IntelliTrace > 一般**]，然後選取 [ **intellitrace 快照] (managed 和原生)**。 如需詳細資訊，請參閱[使用 IntelliTrace 回溯檢查先前的應用程式狀態](../debugger/view-historical-application-state.md)。

快照集適用于 Visual Studio Enterprise 2017 15.5 版和更新版本，且需要 Windows 10 年度更新版或更高版本。  若為 .NET Core 和 ASP.NET Core 應用程式，則需要 Visual Studio Enterprise 2017 15.7 版。 若是以 Windows 為目標的原生應用程式，則需要 Visual Studio Enterprise 2017 15.9 版 Preview 2。

## <a name="collect-intellitrace-events-and-call-information-c-visual-basic"></a><a name="GoingFurther"></a> 收集 IntelliTrace 事件和呼叫資訊 (c #、Visual Basic) 

這預設不會予以啟用，但 IntelliTrace 可以記錄方法呼叫和事件。 若要啟用方法呼叫的收集，請移至 **[工具 > 選項 > IntelliTrace > 一般**]，然後選取 [ **intellitrace 事件] 和 [呼叫資訊] (僅限 managed)**。

目前無法使用 .NET Core 和 ASP.NET Core 應用程式的呼叫資訊。

這可讓您查看呼叫堆疊記錄，並在程式碼中逐步返回及逐步前進。 IntelliTrace 會記錄資料 (例如方法名稱、方法進入點與結束點，以及特定參數值與傳回值)。

> [!TIP]
> 預設不會啟用此選項，因為這樣會增加可觀的額外負荷。 IntelliTrace 不只需要攔截您應用程式所進行的每個方法呼叫，還需要在將它顯示在螢幕上或將它保存到磁碟時處理更大的資料集。
>
> 限制 IntelliTrace 所記錄的事件清單，以及將所收集的模組數目保持為最小值，即可減少效能額外負荷。 如需詳細資訊，請參閱[控制 IntelliTrace 記錄多少呼叫資訊](../debugger/intellitrace-features.md#ControlCallData)。

### <a name="use-the-navigation-gutter"></a>使用導覽裝訂邊

您可以使用出現在程式碼視窗左邊的巡覽邊。 如果您看不到巡覽邊，請移至 [工具] > [選項] > [IntelliTrace] > [進階]，然後選取 [在偵錯模式中顯示巡覽邊]。

巡覽邊可讓您以歷程偵錯模式向前及向後移動方法呼叫和事件。 如需歷程偵錯的詳細資訊，請參閱[歷程偵錯](../debugger/historical-debugging.md)。 它有一些命令：

|命令|描述|
|-|-|
|**在此設定偵錯工具內容**|將偵錯內容設定為它所在的呼叫時間範圍。<br /><br /> 這個圖示只會出現在目前呼叫堆疊上。|
|**返回呼叫位置**|將游標和偵錯內容向後移至呼叫目前函式的位置。<br /><br /> 如果您使用 [即時偵錯] 模式，此命令會開啟 [歷程偵錯]。 如果您導覽回到原始執行中斷，則會關閉 [歷程偵錯] 並開啟 [即時偵錯]。|
|**移至上一個呼叫或 IntelliTrace 事件**|將游標和偵錯內容向後移至上一個呼叫或事件。<br /><br /> 如果您使用 [即時偵錯] 模式，此命令會開啟 [歷程偵錯]。|
|**逐步執行**|逐步執行目前選取的函式。<br /><br /> 只有在您使用 [歷程偵錯] 模式時，才能使用這個命令。|
|**移至下一個呼叫或 IntelliTrace 事件**|將指標和偵錯內容向前移至存在 IntelliTrace 資料的下一個呼叫或事件。<br /><br /> 只有在您使用 [歷程偵錯] 模式時，才能使用這個命令。|
|**移至即時模式**|返回 [即時偵錯] 模式。|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>在 IntelliTrace 中搜尋某行或方法

只有在已啟用方法呼叫資訊時，才能搜尋方法。 您可以搜尋特定行或方法的 IntelliTrace 歷程。 偵錯工具執行停止時，以滑鼠右鍵按一下函式主體來查看操作功能表，然後按一下 [在 IntelliTrace 中搜尋這一行] 或 [在 IntelliTrace 中搜尋這個方法]。

### <a name="control-how-much-call-information-intellitrace-records"></a><a name="ControlCallData"></a> 控制 IntelliTrace 記錄多少呼叫資訊

IntelliTrace 預設會記錄您方案所使用之所有模組的資訊。 您可以設定 IntelliTrace 只記錄您感興趣之模組的呼叫資訊。 在 [工具] > [選項] > [IntelliTrace] > [模組] 中，您可以指定要包括的模組或要從 IntelliTrace 排除的模組。 IntelliTrace 只會收集源自所指定模組的事件，以及在您感興趣的模組內發生的方法呼叫。

若要加入多個模組，請在字串開頭或結尾使用萬用字元 *。 模組名稱必須使用檔案名稱，而非組件名稱。 不接受檔案路徑。

嘗試將模組數目保持為最小值。 因為要收集的資料比較少，所以效能會更好。 因為通過的資料較少，所以 UI 中的雜訊也會較少。

## <a name="save-intellitrace-data-to-file-c-visual-basic-c"></a><a name="SaveSession"></a> 將 IntelliTrace 資料儲存至 file (c #、Visual Basic、c + +) 

如果您正在進行偵錯，而且應用程式處於中斷狀態，則可以移至 [偵錯] > [IntelliTrace] > [儲存 IntelliTrace 工作階段] 來儲存 IntelliTrace 已收集的資料。 已停用此功能表項目，因此，如果應用程式仍在執行，或您已停止偵錯，則無法儲存 IntelliTrace 已收集的資料。

移至 [工具] > [選項] > [IntelliTrace] > [進階]，然後選取 [將 IntelliTrace 記錄儲存在這個目錄]，即可設定 IntelliTrace 自動儲存至檔案。 您也可以設定為產生的檔案所設定的大小，而這樣會讓 IntelliTrace 在空間不足時覆寫較舊的資料。 自動儲存 IntelliTrace 工作階段時，以及 Visual Studio 裝載處理序 (vshost.exe) 開啟時，Visual Studio 會針對每個工作階段建立兩個檔案。

> [!TIP]
> 為了節省磁碟空間，當您不再需要它們時，請關閉自動儲存檔案。 系統不會刪除所有現有檔案。 您一律可以從內容功能表依需要儲存至檔案。

將 IntelliTrace 資料儲存至檔案時，IntelliTrace 從中收集的每個處理序都會有一個 .itrace 檔案。 之後，移至 [檔案] > [開啟] > [檔案]，然後從 [開啟檔案] 對話方塊中選取 .itrace 檔案，即可在 Visual Studio 中開啟 .itrace 檔案。 如需詳細資訊，請參閱[使用儲存的 IntelliTrace 資料](../debugger/using-saved-intellitrace-data.md)。

## <a name="blogs"></a>部落格

[Visual Studio Enterprise 2015 中的 IntelliTrace (英文)](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)

[在 Visual Studio 2015 (文字編輯器中使用 IntelliTrace 進行即時偵錯工具的逐步解說) ](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)

[在 Visual Studio 2015 (社交俱樂部) 中使用 IntelliTrace 進行即時偵錯工具的逐步解說 ](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)

[Visual Studio Enterprise 2015 中的 IntelliTrace 現在支援 attach！](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)

[使用 IntelliTrace 獨立收集器從 windows 服務收集資料](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)

[編輯 IntelliTrace 收集計畫](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan)

[使用 IntelliTrace 的自訂 TraceSource 和調試](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)

[IntelliTrace 獨立收集器和在 Active Directory 帳戶下執行的應用程式集區](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)

## <a name="forums"></a>論壇

[Visual Studio 偵錯工具](https://social.msdn.microsoft.com/Forums/en-US/home)

## <a name="videos"></a>影片

[IntelliTrace 體驗](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[在 Microsoft Visual Studio Ultimate 2015 中使用 IntelliTrace 進行歷程記錄調試](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
