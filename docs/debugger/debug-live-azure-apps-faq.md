---
title: 偵錯快照集的常見問題集 |Microsoft 文件
ms.date: 11/07/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
caps.latest.revision: 1
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fd2ca2bf48c50b0ea5b44654d0711ba162313f04
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Asked Questions for Visual Studio 偵錯快照集

以下是使用快照集偵錯工具的即時 Azure 應用程式進行偵錯時可能出現的問題的清單。

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>取得快照集的效能成本為何？

當快照集偵錯工具會擷取您的應用程式的快照集時，它是分支應用程式的程序，暫停的分岔的複本。 當您偵錯快照集時，您正在偵錯程序的分岔的複本。 此程序會採用只有 10 20 毫秒為單位，但不會複製完整的堆積，應用程式。相反地，它會複製頁面資料表，並設定頁面，以寫入複製。 如果您的應用程式物件在堆積的變更部分，然後複製其各自的頁面。 每個快照集，因此有非常小的記憶體成本 （大約數百 kb 大部分的應用程式）。 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>如果我有向外延展 Azure 應用程式服務 （我的應用程式的多個執行個體），會發生什麼情況？

當您有多個應用程式執行個體時，snappoints 取得套用至每個單一執行個體。 第一個 snappoint 叫用指定的條件建立快照集。 如果您有多個 snappoints，後續的快照集是來自相同的執行個體建立第一個快照集。 Logpoints 傳送至輸出視窗只會顯示訊息從一個執行個體，而 logpoints 傳送到應用程式記錄檔從每個執行個體傳送訊息。 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>快照集偵錯工具如何載入符號？

快照集偵錯工具需要您有相符的符號為您的應用程式可能是在本機或是部署到您的 Azure 應用程式服務 （內嵌的 Pdb 目前不支援）。 快照集偵錯工具會從您的 Azure 應用程式服務自動下載符號。 自 Visual Studio 2017 版本 15.2，部署至 Azure App Service 也會將部署應用程式的符號。

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>運作快照偵錯工具對應用程式的發行組建？

是-快照集偵錯工具會針對發行的組建工作。 Snappoint 放置函式中，重新編譯函式至偵錯版本，因此可偵錯。 當您停止快照集偵錯工具時，函式會傳回其發行組建。 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Logpoints 可能在實際執行應用程式造成副作用嗎？

否-任何記錄檔訊息，您將加入至您的應用程式將會幾乎評估。 它們無法在應用程式中造成任何副作用。 不過，某些原生屬性可能無法存取與 logpoints。 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>如果我的伺服器是在負載下，快照集偵錯工具是否已可運作？

[是]，偵錯快照集可在負載下的伺服器。 快照集偵錯工具會先調節並不會擷取中的情況下的快照集是在伺服器上的可用記憶體很少。

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>如何解除安裝快照偵錯工具？

您可以解除安裝快照偵錯工具的網站擴充功能，您的應用程式服務，執行下列步驟：

1. 關閉應用程式服務透過 Cloud Explorer for Visual Studio 或 Azure 入口網站。
1. 瀏覽至您的應用程式服務 Kudu 網站 (也就是 yourappservice。**scm**。 名稱是.azurewebsites.net) 並瀏覽至**站台擴充程式**。
1. 按一下 X 快照偵錯工具的網站擴充功能上將它移除。

## <a name="see-also"></a>另請參閱

[Visual Studio 偵錯](../debugger/index.md)  
[偵錯即時使用快照集偵錯工具的 ASP.NET 應用程式](../debugger/debug-live-azure-applications.md)  
[疑難排解和已知問題進行偵錯快照集](../debugger/debug-live-azure-apps-troubleshooting.md)
