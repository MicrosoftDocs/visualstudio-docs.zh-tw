---
title: 偵錯即時 ASP.NET Azure 應用程式
ms.description: Learn how to set snappoints and view snapshots with the Snapshot Debugger.
ms.custom: mvc
ms.date: 03/16/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 415e2ee4da01affd2d34b2bbb1aafb5de697767e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>偵錯使用快照集偵錯工具的即時 ASP.NET Azure 應用程式

您感興趣的程式碼執行時，快照集偵錯工具會擷取在實際執行應用程式的快照。 若要指示偵錯工具擷取快照集，您可以在程式碼中設定快照點和記錄點。 偵錯工具可讓您清楚了解發生什麼問題，而不會影響實際執行應用程式的流量。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

Snappoints 和 logpoints 類似於中斷點，但不同於中斷點、 snappoints 不停止應用程式叫用時。 通常，擷取快照時 snappoint 需要大約 10-20 毫秒為單位。 

快照集合適用於 Azure App Service 中執行的下列 Web 應用程式：

- 執行 .NET Framework 4.6.1 或更新版本的 ASP.NET 應用程式。
- 在 Windows 上執行 .NET Core 2.0 或更新版本的 ASP.NET Core 應用程式。

此外，快照集偵錯工具僅適用於 Visual Studio 2017 Enterprise 15.5 或更高版本的版本和基本或更高版本的應用程式服務方案。 

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 啟動快照集偵錯工具
> * 設定 snappoint 與檢視快照集
> * 設定 logpoint

## <a name="start-the-snapshot-debugger"></a>啟動快照集偵錯工具

1. 安裝[Visual Studio 2017 Enterprise 版本 15.5](https://www.visualstudio.com/downloads/)或更新版本。 如果您要從舊版的 Visual Studio 2017 安裝更新，請執行 Visual Studio 安裝程式，並檢查 ASP.NET 及 web 程式開發工作負載中的快照集偵錯工具元件。

2. 開啟您想要的快照集進行偵錯的專案。 

    > [!IMPORTANT] 
    > 設為快照集偵錯，您需要開啟**相同版本的原始程式碼**發行到您的 Azure 應用程式服務。 

3. 在 Cloud Explorer 中 (**檢視 > Cloud Explorer**)，以滑鼠右鍵按一下您的專案部署至 Azure 應用程式服務，然後選取**附加偵錯工具的快照集**。

   ![啟動快照集偵錯工具](../debugger/media/snapshot-launch.png)

    您選取第一次**附加偵錯工具的快照集**，則會提示您安裝您的 Azure App Service 上的快照集偵錯工具的網站擴充功能。 此安裝需要重新啟動您的 Azure 應用程式服務。 

   Visual Studio 現在為偵錯模式的快照集。

    > [!NOTE]
    > Application Insights 的網站擴充功能也支援偵錯快照集。 如果您遇到的 「 網站過期的擴充功能 」 錯誤訊息，請參閱[疑難排解秘訣和已知的問題進行偵錯快照集](../debugger/debug-live-azure-apps-troubleshooting.md)升級詳細資料。

   ![快照集偵錯模式](../debugger/media/snapshot-message.png)

   **模組**視窗則會顯示所有模組的 Azure 應用程式服務已都載入時 (選擇**偵錯 / Windows / 模組**若要開啟此視窗)。

   ![核取 [模組] 視窗](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>設定 snappoint

1. 在程式碼編輯器中，按一下您感興趣設定 snappoint 的程式碼行旁邊的左側裝訂邊上。 請確定它是您知道將會執行的程式碼。

   ![設定 snappoint](../debugger/media/snapshot-set-snappoint.png)

2. 按一下**開始收集**snappoint 開啟。  

   ![開啟 snappoint](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > 您無法逐步檢視快照集時，但您可以遵循不同的行程式碼在執行的程式碼中放置多個 snappoints。 如果您在程式碼中有多個 snappoints，快照集偵錯工具可確保對應的快照集是從相同的使用者工作階段。 快照集偵錯工具會即使有許多使用者叫用您的應用程式。

## <a name="take-a-snapshot"></a>擷取快照

Snappoint 開啟時，它會擷取快照集，每當該行程式碼放置 snappoint 執行。 此執行可能被因伺服器上的實際要求。 若要強制您 snappoint 來叫用，請移至您的網站的瀏覽器檢視，以及採取任何動作需要，否則會導致您 snappoint 會叫用。

## <a name="inspect-snapshot-data"></a>檢查快照集資料

1. 遇到 snappoint 時，快照集出現在 診斷工具視窗。 若要開啟此視窗，請選擇**偵錯 / Windows / 顯示診斷工具**。

   ![開啟 snappoint](../debugger/media/snapshot-diagsession-window.png)

1. 按兩下以開啟程式碼編輯器中的快照集 snappoint。

   ![檢查快照集資料](../debugger/media/snapshot-inspect-data.png)

   從這個檢視中，您可以將滑鼠停留在變數上以檢視資料提示方塊中，使用**區域變數**，**監看**，和**呼叫堆疊**windows，並同時評估運算式。

    該網站本身就仍即時而且使用者不受影響。 根據預設只有一個快照集擷取每個 snappoint: snappoint 擷取快照集後會關閉。 如果您想要擷取在 snappoint 另一份快照，您可以按一下重新開啟 snappoint**更新集合**。

也可以將多個 snappoints 加入至您的應用程式並且利用開啟它們**更新集合** 按鈕。

**需要協助嗎？** 請參閱[疑難排解和已知的問題](../debugger/debug-live-azure-apps-troubleshooting.md)和[常見問題集的快照集偵錯](../debugger/debug-live-azure-apps-faq.md)頁面。

## <a name="set-a-conditional-snappoint"></a>設定條件式 snappoint

如果很難重新建立您的應用程式中的特定狀態，請考慮是否使用條件式 snappoint 可以協助。 條件式 snappoints 幫助您避免擷取快照之前，app 會進入預期的狀態，例如當變數具有您想要檢查的特定值。 您可以設定使用運算式，篩選條件或叫用次數。

#### <a name="to-create-a-conditional-snappoint"></a>若要建立條件式 snappoint

1. 以滑鼠右鍵按一下 snappoint 圖示 （中空球），然後選擇 **設定**。

   ![選擇設定](../debugger/media/snapshot-snappoint-settings.png)

1. 在 [snappoint 設定] 視窗中，輸入運算式。

   ![輸入的運算式](../debugger/media/snapshot-snappoint-conditions.png)

   在上圖中，只擷取快照的 snappoint 時`visitor.FirstName == "Dan"`。

## <a name="set-a-logpoint"></a>設定 logpoint

除了 snappoint 叫用時，取得快照集，您也可以設定 snappoint 記錄訊息 （也就是建立 logpoint）。 您可以設定 logpoints 而不必重新部署您的應用程式。 Logpoints 幾乎執行，但會造成任何影響或您執行的應用程式的副作用。

#### <a name="to-create-a-logpoint"></a>若要建立 logpoint

1. 以滑鼠右鍵按一下 snappoint 圖示 （藍色六邊形），然後選擇 **設定**。

1. 在 [snappoint 設定] 視窗中，選取**動作**。

    ![建立 logpoint](../debugger/media/snapshot-logpoint.png)

1. 在 [訊息] 欄位中，您可以輸入您想要記錄新的記錄檔訊息。 您也可以將它們全放置大括號內，來評估您的記錄檔訊息中的變數。

    如果您選擇**傳送到輸出視窗**、 遇到 logpoint 時，會在 診斷工具視窗中顯示的訊息。

    ![Logpoint diagsession 視窗中的資料](../debugger/media/snapshot-logpoint-output.png)

    如果您選擇**應用程式記錄檔傳送**、 遇到 logpoint 時，訊息會出現任何位置，您可以查看來自訊息`System.Diagnostics.Trace`(或`ILogger`.NET Core 中)，例如[App Insights](/azure/application-insights/app-insights-asp-net-trace-logs)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您學到如何使用快照集偵錯工具。 若要閱讀有關這項功能的更多詳細資料。

> [!div class="nextstepaction"]
> [快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)
