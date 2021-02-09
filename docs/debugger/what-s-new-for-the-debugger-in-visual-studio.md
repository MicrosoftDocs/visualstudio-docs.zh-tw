---
title: Visual Studio 2017 中偵錯工具的新功能 |Microsoft Docs
titleSuffix: ''
description: 請參閱偵錯工具15.5 版中的新功能。 包含：已選取之生產環境應用程式的程式碼快照，以及 Intellitrace 回溯。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: bac5c7021146a0b9bc66e98e7de334bdbf05a7b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883944"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Visual Studio 2017 中偵錯工具的新功能

偵錯工具包含下列新功能：

- 版本15.5 的新功能， **快照偵錯工具** 在您感興趣的程式碼執行時，會取得生產環境中應用程式的快照集。 若要指示偵錯工具擷取快照集，您可以在程式碼中設定快照點和記錄點。 偵錯工具可讓您清楚了解發生什麼問題，而不會影響實際執行應用程式的流量。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

    快照集合適用於 Azure App Service 中執行的下列 Web 應用程式：

  * 執行 .NET Framework 4.6.1 或更新版本的 ASP.NET 應用程式。
  * 在 Windows 上執行 .NET Core 2.0 或更新版本的 ASP.NET Core 應用程式。

    如需詳細資訊，請參閱[使用快照偵錯工具偵錯即時 ASP.NET 應用程式](../debugger/debug-live-azure-applications.md)。

- 在 Visual Studio Enterprise 中，版本15.5 的新 **功能，IntelliTrace 回溯** 會在每個中斷點和偵錯工具步驟事件自動建立應用程式的快照集。 記錄的快照集可讓您回溯到先前的中斷點或步驟，以檢視應用程式過去的狀態。 如果您想要查看先前的應用程式狀態，但不想要重新啟動偵錯或重新建立所需的應用程式狀態，IntelliTrace 回溯可節省您的時間。

    您可以使用[偵錯] 工具列的 [逐步返回] 和 [逐步前進] 按鈕，來巡覽及檢視快照集。 這些按鈕可巡覽出現在 [診斷工具] 視窗之 [事件] 索引標籤中的事件。

    ![逐步執行和向前按鈕](../debugger/media/intellitrace-step-back-icons-description.png  "逐步執行和向前按鈕")

    如需詳細資訊，請參閱[使用 IntelliTrace 檢查先前的應用程式狀態](view-historical-application-state.md)頁面。

- 例外狀況協助程式會取代例外狀況小 **幫手** ，並顯示在發生錯誤的非強制回應對話方塊中。 **例外** 狀況協助程式可讓您更快速地存取任何內部例外狀況、偵錯工具的額外分析 (如果可用) ，以及立即存取例外狀況的 **例外狀況設定**。 如果例外狀況協助程式封鎖您需要查看的內容，也可以將它拖曳至浮動視圖。

    例如， **NullReferenceException** 現在會顯示具有 null 參考的變數 (額外的資訊) 。

    ![偵錯工具的例外狀況協助程式](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    如需詳細資訊，請參閱 [Using the New Exception Helper in Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) (在 Visual Studio 中使用新的例外狀況協助程式) 部落格文章。

- 您現在可以在偵錯工具中暫停程式碼，方法是選取 [ **執行到這裡** ] 綠色箭號圖示， (當您將滑鼠游標停留在程式碼) 上時，就會看到圖示。 這樣就不需要設定暫時中斷點。

    ![要按一下的偵錯工具執行](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- 您可以在 [ **例外狀況設定** ] 對話方塊中設定例外狀況的條件 (您可以使用 [例外狀況設定] 對話方塊中的 [ **編輯條件** ] 圖示，或使用例外狀況的滑鼠右鍵功能表來進行這項作業。 ) 目前支援的條件包括模組名稱 (s) 要包含或排除例外狀況。

    ![例外狀況的條件](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- [附加至進程] 對話方塊包含新的搜尋功能，可協助您更快速地找出需要附加到的進程。

    ![在 [附加至進程] 中搜尋](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

如需這些新功能的詳細資訊，請參閱的[版本 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes)資訊。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.yml)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)