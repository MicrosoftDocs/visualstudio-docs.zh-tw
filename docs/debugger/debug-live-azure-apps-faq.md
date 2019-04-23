---
title: 快照集偵錯的常見問題集 | Microsoft Docs
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
ms.openlocfilehash: 7ea593ad5f88ba29f6b1c0d7c64a129b8f71c7f5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58857070"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Visual Studio 中快照集偵錯的常見問題集

以下是使用快照偵錯工具針對即時 Azure 應用程式進行偵錯時，可能出現問題的清單。

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>建立快照集的效能成本為何？

當快照偵錯工具擷取您應用程式的快照集時，它會分支應用程式的程序，並暫止分支複本。 當您針對快照集進行偵錯時，其實是針對程序的分支複本進行偵錯。 此程序只需要 10 到 20 毫秒，但不會複製應用程式的完整堆積。 而是只會複製頁面資料表，並將頁面設定為寫入時複製。 如果堆積中應用程式的部分物件有所變更，就會複製它們的個別頁面。 這是每個快照集都會佔用小部分記憶體 (對大多數應用程序而言，大約為幾百KB) 的原因。

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>如果我有相應放大的 Azure App Service (應用程式的多個執行個體) 的話，會發生什麼事？

當您的應用程式有多個執行個體時，快照點會套用至每一個執行個體。 只有使用指定條件叫用的第一個快照點會建立快照集。 如果有多個快照點，之後的快照集會來自建立第一個快照集的同一個執行處理。 傳送至輸出視窗的記錄點只會顯示來自一個執行個體的訊息，傳送至應用程式記錄檔的記錄點則會傳送來自每個執行個體的訊息。

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>快照偵錯工具如何載入符號？

快照偵錯工具要求在本機有您應用程式的相符符號，或將符號部署至您的 Azure App Service。 (目前不支援內嵌的 PDB。)快照偵錯工具會自動從您的 Azure App Service 下載符號。 從 Visual Studio 2017 15.2 版開始，部署至 Azure App Service 也會部署您應用程式的符號。

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>快照偵錯工具是否可用於應用程式的發行組建？

是 - 快照偵錯工具可用於發行組建。 在函式中置入快照點時，會將函式重新編譯回偵錯版本，因此可偵錯。 停止快照偵錯工具會讓函式回復成發行組建版本。

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>記錄點 會對生產環境應用程式造成副作用嗎？

否 - 新增至應用程式的任何記錄訊息都會以虛擬方式進行評估。 它們無法在您的應用程式中造成任何副作用。 不過，某些原生屬性可能無法使用記錄點存取。

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>如果我的伺服器負載很輕，快照偵錯工具是否可運作？

是。即使伺服器負載很輕，快照偵錯工具依然能夠運作。 在伺服器可用記憶體容量偏低的情況下，快照偵錯工具會進行節流且不會擷取快照集。

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>如何解除安裝快照偵錯工具？

可透過下列步驟，在 App Service 上解除安裝快照偵錯工具網站延伸模組：

1. 在 Visual Studio 或 Azure 入口網站中透過 Cloud Explorer 關閉 App Service。
1. 瀏覽至您 App Service 的 Kudu 網站 (也就是 yourappservice.**scm**.azurewebsites.net)，並瀏覽至 [網站延伸模組]。
1. 按一下快照偵錯工具網站延伸模組上的 X 即可將它移除。

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>為什麼會在快照偵錯工具工作階段期間開啟連接埠？

快照偵錯工具必須開啟一組連接埠，才能針對在 Azure 中建立的快照集進行偵錯，這些和進行遠端偵錯時所需的連接埠相同。 [您可以在此處找到連接埠清單](../debugger/remote-debugger-port-assignments.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.md)
- [使用快照集偵錯工具的即時 ASP.NET 應用程式進行偵錯](../debugger/debug-live-azure-applications.md)
- [偵錯即時 ASP.NET Azure 虛擬 Machines\Virtual 機器擴展集使用快照集偵錯工具](../debugger/debug-live-azure-virtual-machines.md)
- [偵錯即時 ASP.NET Azure Kubernetes 中使用快照集偵錯工具](../debugger/debug-live-azure-kubernetes.md)
- [疑難排解和已知問題的快照集偵錯](../debugger/debug-live-azure-apps-troubleshooting.md)