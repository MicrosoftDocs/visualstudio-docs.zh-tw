---
title: 快照集偵錯的常見問題集 |Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0899b70ce4a917b0479a9ac6623e33ee8bcdbe22
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335099"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>B80acca24f64">frequently Asked Questions for Visual Studio 偵錯快照集

以下是使用快照集偵錯工具的即時 Azure 應用程式進行偵錯時，可能會想到的問題清單。

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>建立快照集的效能成本為何？

當快照集偵錯工具會擷取您的應用程式的快照集時，它是分支應用程式的程序，並暫停分支的複本。 當您偵錯快照集時，您正在偵錯程序的分支的複本。 此程序只需要 10 到 20 毫秒，但不會複製應用程式的完整的堆積。 相反地，它會複製只有頁面的資料表，並設定頁面，以寫入複製。 如果您的應用程式物件在堆積變更部份，之後會複製個別頁面。 每個快照集，因此有小型的記憶體成本 （大約數百個對於大多數應用程式的 kb 為單位）。 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>如果我有相應放大 Azure App Service （我的應用程式的多個執行個體），會發生什麼事？

當您有多個應用程式執行個體時，貼齊點套用至每個單一執行個體。 只有第一個貼齊點叫用指定的條件會建立快照集。 如果您有多個貼齊點時，後續的快照集是來自相同的執行個體建立第一個快照集。 記錄點傳送至輸出視窗只會顯示訊息從一個執行個體，而傳送至應用程式記錄檔的記錄點從每個執行個體傳送訊息。 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>快照集偵錯工具如何載入符號？

快照集偵錯工具，您需要相符的符號的本機或已部署您的應用程式到 Azure App Service。 （內嵌的 Pdb 目前不支援。）快照集偵錯工具會從您的 Azure App Service，自動下載符號。 Visual Studio 2017 版本 15.2，部署至 Azure App Service 也會部署您的應用程式的符號。

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>快照集偵錯工具會針對我的應用程式的發行組建運作？

是-快照集偵錯工具被要用於發行組建。 貼齊點放置在函式之後，重新編譯函式回到偵錯版本，因此可偵錯。 當您停止快照集偵錯工具時，函式會傳回至其發行組建。 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>記錄點造成副作用在生產環境應用程式嗎？

否-您將新增至您的應用程式的任何記錄訊息會幾乎評估。 它們無法在您的應用程式中，會造成任何副作用。 不過，某些原生屬性可能會無法存取與記錄點。 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>如果我的伺服器是在負載下，快照集偵錯工具是否已可運作？

[是]，快照集偵錯可在負載下的伺服器。 快照集偵錯工具節流並不會擷取快照情況下的沒有在伺服器上的可用記憶體很少。

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>如何解除安裝快照偵錯工具？

您可以在您的 App Service，執行下列步驟來解除安裝快照偵錯工具網站延伸模組：

1. 請關閉您的應用程式服務透過 Visual Studio 或 Azure 入口網站中的 [雲端總管]。
1. 瀏覽至您的 App Service Kudu 網站 (也就是 yourappservice。**scm**。 azurewebsites.net) 並瀏覽至**網站延伸模組**。
1. 按一下快照集偵錯工具網站延伸模組上的 X 即可移除它。

## <a name="see-also"></a>另請參閱

[Visual Studio 偵錯](../debugger/index.md)  
[使用快照集偵錯工具的即時 ASP.NET 應用程式進行偵錯](../debugger/debug-live-azure-applications.md)  
[偵錯即時 ASP.NET Azure 虛擬 Machines\Virtual 機器擴展集使用快照集偵錯工具](../debugger/debug-live-azure-virtual-machines.md)  
[偵錯即時 ASP.NET Azure Kubernetes 中使用快照集偵錯工具](../debugger/debug-live-azure-kubernetes.md)  
[疑難排解和已知問題的快照集偵錯](../debugger/debug-live-azure-apps-troubleshooting.md)
