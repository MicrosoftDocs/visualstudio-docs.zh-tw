---
title: 在 Visual Studio 2017 偵錯工具的新功能 |Microsoft 文件
ms.custom: ''
ms.date: 03/07/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07f25edb63e3418bab44d71bc8314d3aa83e7a84
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>在 偵錯工具的新功能 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

偵錯工具會包含下列新功能：

- 新功能 15.5，**快照偵錯工具**您感興趣的程式碼執行時，會在實際執行應用程式的快照集。 若要指示偵錯工具擷取快照集，您可以在程式碼中設定快照點和記錄點。 偵錯工具可讓您清楚了解發生什麼問題，而不會影響實際執行應用程式的流量。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

    快照集合適用於 Azure App Service 中執行的下列 Web 應用程式：

    * 執行 .NET Framework 4.6.1 或更新版本的 ASP.NET 應用程式。
    * 在 Windows 上執行 .NET Core 2.0 或更新版本的 ASP.NET Core 應用程式。

    如需詳細資訊，請參閱[即時使用快照集偵錯工具的 ASP.NET 應用程式進行偵錯](../debugger/debug-live-azure-applications.md)。

- 新功能，在 Visual Studio Enterprise 15.5 **IntelliTrace 步驟後**自動快照的應用程式在每個中斷點和偵錯工具事件步驟。 記錄的快照集可讓您回溯到先前的中斷點或步驟，以檢視應用程式過去的狀態。 如果您想要查看先前的應用程式狀態，但不想要重新啟動偵錯或重新建立所需的應用程式狀態，IntelliTrace 回溯可節省您的時間。

    您可以使用[偵錯] 工具列的 [逐步返回] 和 [逐步前進] 按鈕，來巡覽及檢視快照集。 這些按鈕可巡覽出現在 [診斷工具] 視窗之 [事件] 索引標籤中的事件。

    ![逐步執行向後和向前按鈕](../debugger/media/intellitrace-step-back-icons-description.png  "步驟向後和向前按鈕")

    如需詳細資訊，請參閱[使用 IntelliTrace 回溯檢視快照集](../debugger/how-to-use-intellitrace-step-back.md)頁面。

- **例外狀況協助程式**取代例外狀況助理，而且會出現在非強制回應對話方塊中，發生錯誤。 **例外狀況協助程式**提供快速地存取任何內部例外狀況，偵錯工具 （如果有的話），其他的分析和立即存取**例外狀況設定**例外狀況。 也可以將例外狀況協助程式拖曳至浮動的檢視，如果它會封鎖您需要查看的項目。

    例如， **NullReferenceException**現在會顯示變數，其中包含 null 參考 （額外的資訊）。

    ![偵錯工具的例外狀況協助程式](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    如需詳細資訊，請參閱 [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (在 Visual Studio 中使用新的例外狀況協助程式) 部落格文章。

- 您現在可以執行的程式碼行暫停偵錯工具中所選取期間**執行這裡**綠色箭號圖示 （您將看到游標一行程式碼圖示）。 這樣就不需要設定暫時中斷點。

    ![偵錯工具的執行按一下](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

- 您可以設定條件中的例外狀況上**例外狀況設定**對話方塊 (您可以使用**編輯條件**例外狀況設定 對話方塊中或使用滑鼠右鍵功能表上的圖示例外狀況。）目前支援的狀況包括要包含或排除例外狀況的模組名稱。

    ![例外狀況的條件](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- 附加至對話方塊包含新的搜尋功能，可協助您快速找出您要附加至處理序的處理序。

    ![在搜尋附加至處理序](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch") 

如需有關這些新功能的詳細資訊，請參閱[版本資訊[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag)。
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯](../debugger/index.md)  
 [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)