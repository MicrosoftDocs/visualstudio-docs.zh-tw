---
title: 時間移動偵錯即時 ASP.NET Azure 虛擬機器
description: 了解如何記錄並重新執行快照集偵錯工具使用的 Azure 虛擬機器上的即時 ASP.NET 應用程式。
ms.custom: ''
ms.date: 04/11/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 3a81f6aa138b361a44a272ebda3557d27a914c64
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112348"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>記錄並重新執行快照集偵錯工具使用的 Azure 虛擬機器上的即時 ASP.NET 應用程式

時間移動偵錯 (TTD) 預覽 Visual Studio Enterprise 中的提供記錄執行在 Azure 虛擬機器 (VM) 的 Web 應用程式，準確地重新建構然後重新執行的執行路徑。 TTD 與快照集偵錯工具整合，並允許您倒轉並重新執行每一行程式碼次數想，協助您找出並識別可能只會出現在生產環境的問題。

擷取 TTD 記錄將不會停止應用程式。 不過，TDD 錄製您執行的程序，讓它變慢根據這些因素包括的大小和作用中的執行緒數目會增加相當大的負擔。

這項功能處於預覽版本的 Visual Studio 2019 移的即時授權。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 開始時間的移動啟用偵錯的快照集偵錯工具
> * 設定貼齊點和一次傳送記錄的收集
> * 開始偵錯一次移動記錄

## <a name="prerequisites"></a>必要條件

* 時間移動的偵錯的 Azure 虛擬機器 (VM) 僅適用於 Visual Studio 2019 企業版或更高版本**Azure 開發工作負載**。 (您可以在 [個別元件] 索引標籤下的 [偵錯和測試] > [快照偵錯工具]底下找到它。)

    如果尚未安裝，安裝[Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/)。

* 時間移動偵錯是適用於下列的 Azure VM web 應用程式：
  * 執行 ASP.NET 應用程式 (AMD64) 在.NET Framework 4.8 或更新版本。

## <a name="open-your-project-and-start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>開啟您的專案，並開始時間的移動啟用偵錯的快照集偵錯工具

1. 開啟專案針對您要收集時間的移動記錄。

    > [!IMPORTANT]
    > 若要啟動 TTD，您必須開啟*相同版本的原始程式碼*發行您的 Azure VM 服務。

1. 選擇 [偵錯] > [附加快照偵錯工具]。選取您的 web 應用程式部署至 Azure VM 和 Azure 儲存體帳戶。 選取 **啟用時間的移動偵錯**預覽選項，然後按一下**附加**。

      ![選取 Azure 資源](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > 第一次為 VM 選取 [附加快照偵錯工具] 時，IIS 會自動重新啟動。

    中繼資料**模組**一開始未啟動。 瀏覽至 web 應用程式和**開始收集**按鈕就會變成作用中。 Visual Studio 現在已經處於快照集偵錯模式。

   ![快照集偵錯模式](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Application Insights 網站延伸模組也支援快照集偵錯。 如果遇到「網站延伸模組過期」錯誤訊息，請參閱[快照集偵錯的疑難排解祕訣與已知問題](../debugger/debug-live-azure-apps-troubleshooting.md)了解升級詳細資料。

   **模組**視窗會顯示您的 Azure vm 時載入所有模組 (選擇**偵錯 > Windows > 模組**若要開啟此視窗)。

   ![檢查 [模組] 視窗](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>設定貼齊點和一次傳送記錄的收集

1. 在程式碼編輯器中，按一下您感興趣設定貼齊點的方法中的左裝訂邊。 確定這是您將執行的程式碼。

   ![設定快照點](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. 以滑鼠右鍵按一下 貼齊點圖示 （空心的球），然後選擇 **動作**。 在 [**快照集設定**] 視窗中，按一下**動作**核取方塊。 然後按一下**這個方法的結尾收集時間的移動追蹤**核取方塊。

   ![收集時間的移動追蹤之方法的結尾](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. 按一下 [開始收集] 以開啟快照點。

   ![開啟快照點](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>建立快照集

當開啟貼齊點時，它會擷取快照集時貼齊點所在的程式碼行執行。 這項執行可能因您的伺服器上的實際要求。 若要強制叫用快照點，請移至網站的瀏覽器檢視，並採取可使得系統叫用快照點的任何必要動作。

## <a name="start-debugging-a-time-travel-recording"></a>開始偵錯一次移動記錄

1. 叫用快照點時，[診斷工具] 視窗中會顯示快照點。 若要開啟此視窗，請選擇 [偵錯] > [Windows] > [顯示診斷工具]。

   ![開啟快照點](../debugger/media/snapshot-diagsession-window.png)

1. 按一下 檢視快照集連結以開啟程式碼編輯器中所記錄的時間移動。
  
   您可以執行每一行程式碼使用記錄 TTD**繼續**並**反向繼續**按鈕。 此外，**偵錯**工具列可以用來**顯示下一個陳述式**，**逐步執行**，**不進入函式**，**跳離函式**，**步驟回到**，**回進入**，**步驟回**。

   ![開始偵錯](../debugger/media/time-travel-debugging-step-commands.png)

   您也可以使用**區域變數**，**監看式**，並**呼叫堆疊**windows，並同時評估運算式。

   ![檢查快照集資料](../debugger/media/time-travel-debugging-start-debugging.png)

    在網站本身是仍然即時和終端使用者不會受到任何後續的 TTD 活動。 每個快照點預設只會擷取一個快照集：擷取快照集之後，快照點就會關閉。 如果想要在快照點擷取另一個快照集，可以按一下 [更新集合] 以重新開啟快照點。

**需要協助嗎？** 請參閱[疑難排解和已知問題](../debugger/debug-live-azure-apps-troubleshooting.md)與[快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)頁面。

## <a name="set-a-conditional-snappoint"></a>設定條件式快照點

如果很難在應用程式中重新建立特定狀態，請考量使用條件式快照點是否能有所幫助。 條件式貼齊點幫助您避免收集一次移動記錄直到應用程式進入所需的狀態，例如當變數只有您想要檢查的特定值。 [您可以設定使用運算式，篩選條件或叫用次數](../debugger/debug-live-azure-apps-troubleshooting.md)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何收集記錄適用於 Azure 虛擬機器時間移動。 若要閱讀更多詳細資料，關於快照集偵錯工具。

> [!div class="nextstepaction"]
> [快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)