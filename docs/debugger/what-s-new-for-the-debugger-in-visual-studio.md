---
title: 什麼是 Visual Studio 2017 中偵錯工具的新功能 |Microsoft Docs
titleSuffix: ''
ms.date: 01/22/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 9c6f2eb4be56be8cf5e25c3238a91819df3bc574
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "57867615"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Visual Studio 2017 中偵錯工具的新功能

偵錯工具會包含下列新功能：

- 在 15.5 版中，新**快照集偵錯工具**您感興趣的程式碼執行時，會在生產應用程式的快照集。 若要指示偵錯工具擷取快照集，您可以在程式碼中設定快照點和記錄點。 偵錯工具可讓您清楚了解發生什麼問題，而不會影響實際執行應用程式的流量。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

    快照集合適用於 Azure App Service 中執行的下列 Web 應用程式：

  * 執行 .NET Framework 4.6.1 或更新版本的 ASP.NET 應用程式。
  * 在 Windows 上執行 .NET Core 2.0 或更新版本的 ASP.NET Core 應用程式。

    如需詳細資訊，請參閱[使用快照偵錯工具偵錯即時 ASP.NET 應用程式](../debugger/debug-live-azure-applications.md)。

- 15.5 版 Visual Studio Enterprise 中，新**IntelliTrace 回溯**自動快照的應用程式在每個中斷點和偵錯工具逐步執行事件。 記錄的快照集可讓您回溯到先前的中斷點或步驟，以檢視應用程式過去的狀態。 如果您想要查看先前的應用程式狀態，但不想要重新啟動偵錯或重新建立所需的應用程式狀態，IntelliTrace 回溯可節省您的時間。

    您可以使用[偵錯] 工具列的 [逐步返回] 和 [逐步前進] 按鈕，來巡覽及檢視快照集。 這些按鈕可巡覽出現在 [診斷工具] 視窗之 [事件] 索引標籤中的事件。

    ![[逐步返回] 和 [逐步前進] 按鈕](../debugger/media/intellitrace-step-back-icons-description.png  "[逐步返回] 和 [逐步前進] 按鈕")

    如需詳細資訊，請參閱[使用 IntelliTrace 檢查先前的應用程式狀態](../debugger/view-historical-application-state.md)頁面。

- **例外狀況協助程式**取代例外狀況助理，並會出現在非強制回應對話方塊中，發生錯誤。 **例外狀況協助程式**提供更快速存取任何內部例外狀況，偵錯工具 （如果有的話），額外的分析和立即存取**例外狀況設定**例外狀況。 也可以將例外狀況協助程式拖曳至浮動的檢視，如果它會封鎖您需要查看的項目。

    例如， **NullReferenceException**現在會顯示變數，其中包含 null 參考 （額外的資訊）。

    ![偵錯工具的例外狀況協助程式](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    如需詳細資訊，請參閱 [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (在 Visual Studio 中使用新的例外狀況協助程式) 部落格文章。

- 您現在可以執行的程式碼行時暫停偵錯工具中，選取**執行到這裡**（您將看到程式碼行暫留時的圖示） 的綠色箭號圖示。 這樣就不需要設定暫時中斷點。

    ![偵錯工具的執行至點選處](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- 您可以設定條件中的例外狀況**例外狀況設定** 對話方塊中 (您可以利用**編輯條件**在例外狀況設定 對話方塊中，或使用滑鼠右鍵功能表上的圖示例外狀況。）目前支援的條件包括要包含或排除例外狀況的模組名稱。

    ![在例外狀況的條件](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- 附加至對話方塊包含新的搜尋功能，可協助您更快速地找出您要附加至處理序的處理序。

    ![中的搜尋 připojit k procesu](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

如需有關這些新功能的詳細資訊，請參閱 <<c0> [ 版本資訊[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.md)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)