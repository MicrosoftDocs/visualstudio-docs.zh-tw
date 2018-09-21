---
title: IntelliTrace 功能 |Microsoft Docs
ms.custom: ''
ms.date: 09/19/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ba3225d793baed9325612ad5b88bd55d629c44f
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495722"
---
# <a name="intellitrace-features"></a>IntelliTrace 功能

您可以使用 IntelliTrace 記錄您應用程式的事件和方法呼叫，以讓您檢查它在執行之不同時間點的狀態 (呼叫堆疊和區域變數值)。 只要照常開始偵錯-根據預設，已開啟 IntelliTrace 和 IntelliTrace 所記錄在新的資訊請參閱 <<c0>  **診斷工具**下方視窗**事件** 索引標籤。選取事件，然後按一下**啟用歷程偵錯**以查看呼叫堆疊和區域變數記錄此事件。

如需逐步說明，請參閱 <<c0> [ 逐步解說： 使用 IntelliTrace](../debugger/walkthrough-using-intellitrace.md)。

Visual Studio Enterprise 版本 (而非 Visual Studio Professional 或 Community 版本) 中提供 IntelliTrace。

若要確認 IntelliTrace 已開啟，請開啟**工具 > 選項 > IntelliTrace**選項頁面。 **啟用 IntelliTrace**預設應該核取。

> [!NOTE]
> 上的所有設定的範圍**IntelliTrace**選項 頁面是 Visual Studio 為整個、 不是個別專案或解決方案。 這些設定的變更會套用至所有 Visual Studio 執行個體、所有偵錯工作階段，以及所有專案或方案。

## <a name="ChooseEvents"></a> 選擇的事件，IntelliTrace 記錄 （僅限 managed 程式碼）

您可以開啟或關閉特定 IntelliTrace 事件的記錄。

如果您正在偵錯，請停止偵錯。 移至**工具 > 選項 > IntelliTrace > IntelliTrace 事件**。 選擇您要 IntelliTrace 記錄的事件。

## <a name="Snapshots"></a> 收集的快照集

這不預設啟用，但 IntelliTrace 可以擷取您的應用程式，在每個中斷點和偵錯工具步驟事件的快照集，您可以在歷程記錄偵錯工作階段中檢視這些快照集。 快照集可讓您完整的應用程式的狀態檢視。 若要啟用擷取的快照集，請前往**工具 > 選項 > IntelliTrace > 一般**，然後選取**IntelliTrace 快照集 （managed 與原生）**。 如需詳細資訊，請參閱[檢視使用 IntelliTrace 倒退的快照集](../debugger/how-to-use-intellitrace-step-back.md)

快照集可用於 Visual Studio Enterprise 2017 15.5 版和更高版本，而且需要 Windows 10 年度更新版或更新版本。  針對.NET Core 和 ASP.NET Core 應用程式，Visual Studio Enterprise 2017 15.7 版則是必要項目。 原生應用程式目標設為 Windows，Visual Studio Enterprise 2017 版本 15.9 Preview 2 是必要。

## <a name="GoingFurther"></a> 收集 IntelliTrace 事件和呼叫資訊 （僅限 managed 程式碼）

這不預設啟用，但 IntelliTrace 可以記錄方法呼叫和事件。 若要啟用的方法呼叫，請移至集合**工具 > 選項 > IntelliTrace > 一般**，然後選取**IntelliTrace 事件和呼叫資訊 (僅限 managed)**。

呼叫資訊不是目前適用於.NET Core 和 ASP.NET Core 應用程式。 

這可讓您查看呼叫堆疊記錄，並在程式碼中逐步返回及逐步前進。 IntelliTrace 會記錄資料 (例如方法名稱、方法進入點與結束點，以及特定參數值與傳回值)。

> [!TIP]
> 預設不會啟用此選項，因為這樣會增加可觀的額外負荷。 IntelliTrace 不只需要攔截您應用程式所進行的每個方法呼叫，還需要在將它顯示在螢幕上或將它保存到磁碟時處理更大的資料集。
>
> 限制 IntelliTrace 所記錄的事件清單，以及將所收集的模組數目保持為最小值，即可減少效能額外負荷。 如需詳細資訊，請參閱 <<c0> [ 控制多少呼叫資訊 IntelliTrace 記錄](../debugger/intellitrace-features.md#ControlCallData)。

### <a name="use-the-navigation-gutter"></a>使用巡覽邊

您可以使用出現在程式碼視窗左邊的巡覽邊。 如果您沒有看到巡覽邊，請移至**工具 > 選項 > IntelliTrace > 進階**，然後選取**顯示在偵錯模式中的巡覽邊**。

巡覽邊可讓您以歷程偵錯模式向前及向後移動方法呼叫和事件。 如需歷程偵錯的詳細資訊，請參閱[歷程偵錯](../debugger/historical-debugging.md)。 它有一些命令：

|||
|-|-|
|**在此設定偵錯工具內容**|將偵錯內容設定為它所在的呼叫時間範圍。<br /><br /> 這個圖示只會出現在目前呼叫堆疊上。|
|**返回呼叫位置**|將游標和偵錯內容向後移至呼叫目前函式的位置。<br /><br /> 如果您使用 [即時偵錯] 模式，此命令會開啟 [歷程偵錯]。 如果您導覽回到原始執行中斷，則會關閉 [歷程偵錯] 並開啟 [即時偵錯]。|
|**移至上一個呼叫或 IntelliTrace 事件**|將游標和偵錯內容向後移至上一個呼叫或事件。<br /><br /> 如果您使用 [即時偵錯] 模式，此命令會開啟 [歷程偵錯]。|
|**中的步驟**|逐步執行目前選取的函式。<br /><br /> 只有在您使用 [歷程偵錯] 模式時，才能使用這個命令。|
|**請移至下一個呼叫或 IntelliTrace 事件**|將指標和偵錯內容向前移至存在 IntelliTrace 資料的下一個呼叫或事件。<br /><br /> 只有在您使用 [歷程偵錯] 模式時，才能使用這個命令。|
|**移至即時模式**|返回 [即時偵錯] 模式。|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>在 IntelliTrace 中搜尋某行或方法

只有在已啟用方法呼叫資訊時，才能搜尋方法。 您可以搜尋特定行或方法的 IntelliTrace 歷程。 雖然偵錯工具執行停止時，若要查看內容功能表中，函式主體內按一下滑鼠右鍵，然後按一下**搜尋的這一行中 IntelliTrace**或**搜尋為此方法在 IntelliTrace**。

### <a name="ControlCallData"></a> 控制多少呼叫資訊的 IntelliTrace 記錄

IntelliTrace 預設會記錄您方案所使用之所有模組的資訊。 您可以設定 IntelliTrace 只記錄您感興趣之模組的呼叫資訊。 在 **工具 > 選項 > IntelliTrace > 模組**，您可以指定要包含的模組或要從 IntelliTrace 排除的模組。 IntelliTrace 只會收集源自所指定模組的事件，以及在您感興趣的模組內發生的方法呼叫。

若要加入多個模組，請在字串開頭或結尾使用萬用字元 *。 模組名稱必須使用檔案名稱，而非組件名稱。 不接受檔案路徑。

嘗試將模組數目保持為最小值。 因為要收集的資料比較少，所以效能會更好。 因為通過的資料較少，所以 UI 中的雜訊也會較少。

## <a name="SaveSession"></a> 將 IntelliTrace 資料儲存至檔案

您可以將儲存 IntelliTrace 已收集的資料移至**偵錯 > IntelliTrace > 儲存 IntelliTrace 工作階段**時進行偵錯，並在應用程式處於中斷狀態。 已停用此功能表項目，因此，如果應用程式仍在執行，或您已停止偵錯，則無法儲存 IntelliTrace 已收集的資料。

您可以設定 IntelliTrace 自動儲存至檔案，方法是前往**工具 > 選項 > IntelliTrace > 進階**，然後選取**存放區的 IntelliTrace 記錄儲存在此目錄**。 您也可以設定為產生的檔案所設定的大小，而這樣會讓 IntelliTrace 在空間不足時覆寫較舊的資料。 自動儲存 IntelliTrace 工作階段時，以及 Visual Studio 裝載處理序 (vshost.exe) 開啟時，Visual Studio 會針對每個工作階段建立兩個檔案。

> [!TIP]
> 若要節省磁碟空間，請關閉自動儲存檔案，當您不再需要它們。 系統不會刪除所有現有檔案。 您一律可以從內容功能表依需要儲存至檔案。

將 IntelliTrace 資料儲存至檔案時，IntelliTrace 從中收集的每個處理序都會有一個 .itrace 檔案。 您接著可以開啟 Visual Studio 中.itrace 檔案，方法是前往**檔案 > 開啟 > 檔案**並從 [開啟檔案] 對話方塊中選取.itrace 檔案。 如需詳細資訊，請參閱 <<c0> [ 儲存的 IntelliTrace 資料的使用](../debugger/using-saved-intellitrace-data.md)。

## <a name="blogs"></a>部落格

[Visual Studio Enterprise 2015 中的 IntelliTrace (英文)](https://blogs.msdn.microsoft.com/devops/2015/01/16/intellitrace-in-visual-studio-ultimate-2015/)

[逐步解說的即時使用 IntelliTrace 偵錯在 Visual Studio 2015 （文字編輯器）](https://blogs.msdn.microsoft.com/devops/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)

[逐步解說的即時偵錯在 Visual Studio 2015 （社團） 中使用 IntelliTrace](https://blogs.msdn.microsoft.com/devops/2015/04/29/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)

[在 Visual Studio Enterprise 2015 現在支援附加 IntelliTrace ！](https://blogs.msdn.microsoft.com/devops/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)

[從 windows 服務，使用 IntelliTrace 獨立收集器收集資料](https://blogs.msdn.microsoft.com/devops/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)

[編輯 IntelliTrace 收集計劃](https://blogs.msdn.microsoft.com/devops/2015/03/09/editing-the-intellitrace-collection-plan/)

[自訂 TraceSource 和使用 IntelliTrace 偵錯](https://blogs.msdn.microsoft.com/devops/2014/12/16/custom-tracesource-and-debugging-using-intellitrace/)

[Active Directory 帳戶下執行的 IntelliTrace 獨立收集器和應用程式集區](https://blogs.msdn.microsoft.com/devops/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)

## <a name="forums"></a>論壇

[Visual Studio 偵錯工具](http://go.microsoft.com/fwlink/?LinkId=262263)

## <a name="videos"></a>視訊

[IntelliTrace 經驗](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Microsoft Visual Studio 中的 IntelliTrace 歷程偵錯 Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
