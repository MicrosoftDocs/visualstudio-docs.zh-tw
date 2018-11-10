---
title: Azure 雲端服務或虛擬機器，在 Visual Studio 中偵錯 |Microsoft Docs
description: 在 Visual Studio 中偵錯雲端服務或虛擬機器
author: mikejo5000
manager: douge
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: b2c67ce81a42df4a17761fcee2dcd2f8a67c4941
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002009"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Azure 雲端服務或虛擬機器，在 Visual Studio 中偵錯

Visual Studio 可讓您進行偵錯 Azure 雲端服務和虛擬機器的不同選項。

## <a name="debug-your-cloud-service-on-your-local-computer"></a>偵錯您本機電腦上的雲端服務

您可以節省時間和金錢，藉由使用 Azure 計算模擬器來偵錯雲端服務在本機電腦上。 您在部署之前，在本機偵錯服務，您可以改善可靠性和效能而不需支付運算時間。 不過，某些錯誤可能只有當您執行雲端服務在 Azure 中是本身。 如果您啟用遠端偵錯時您發佈您的服務，然後將偵錯工具附加至角色執行個體，您可以偵錯這些錯誤。

模擬器會模擬 Azure 運算服務，並使您可以測試和偵錯雲端服務，再將它部署在本機環境上執行。 模擬器會處理您的角色執行個體的生命週期，並且提供模擬的資源，例如本機儲存體的存取權。 當您偵錯，或從 Visual Studio 中執行您的服務時，它會自動啟動模擬器，做為背景應用程式，並接著將服務部署至模擬器。 若要檢視您的服務，在本機環境中執行時，您可以使用模擬器。 您可以執行完整版或精簡版的模擬器。 （從 Azure 2.3 起，精簡版是模擬器的預設值）。請參閱[來執行和偵錯雲端服務在本機使用 Emulator Express](vs-azure-tools-emulator-express-debug-run.md)。

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>若要偵錯您本機電腦上的雲端服務

1. 在功能表列上選擇 **偵錯**，**開始偵錯**執行您的 Azure 雲端服務專案。 或者，您可以按 F5。 您會看到一則訊息，正在啟動計算模擬器。 當模擬器啟動時，系統匣圖示可加以確認。

    ![在系統匣中的 azure 模擬器](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. 顯示計算模擬器的使用者介面，在通知區域中，開啟 Azure 圖示的捷徑功能表，然後選取**顯示計算模擬器 UI**。

    UI 的左的窗格會顯示目前已部署至計算模擬器和每個服務執行的角色執行個體的服務。 您可以選擇的服務或角色，以顯示在右窗格中的生命週期、 記錄和診斷資訊。 如果您將焦點放在包含視窗的上邊界時，它會展開以填滿右方窗格中。

3. 逐步執行應用程式上選取命令**偵錯**功能表，然後在您的程式碼中設定中斷點。 當您逐步執行偵錯工具中的應用程式時，窗格會更新與應用程式的目前狀態。 當您停止偵錯時，會刪除應用程式部署。 如果您的應用程式包含 web 角色，而且您已設定為啟動 web 瀏覽器的 [啟動] 動作屬性，Visual Studio 會在瀏覽器中啟動您的 web 應用程式。 如果您變更服務組態中角色執行個體的數目時，您必須停止雲端服務，並再重新啟動偵錯，以便您可以偵錯角色的這些新執行個體。

    **注意：** 當停止執行或偵錯您的服務時，不停止本機計算模擬器和儲存體模擬器。 您必須明確停止它們從通知區域。

## <a name="debug-a-cloud-service-in-azure"></a>測試 Azure 中的雲端服務進行偵錯

偵錯雲端服務從遠端電腦，您必須啟用該功能明確，因此需要執行您的角色執行個體的虛擬機器上已安裝服務 (例如 msvsmon.exe)，部署您的雲端服務時。 如果您未啟用遠端偵錯發佈的服務時，您必須重新發行服務啟用遠端偵錯。

如果您啟用遠端偵錯雲端服務，它不會出現效能降低或產生額外費用。 不使用遠端偵錯生產服務，因為用戶端使用的服務可能會造成不良影響。

> [!NOTE]
> 當您發行雲端服務，從 Visual Studio 時，您可以讓**IntelliTrace**該服務中以.NET Framework 4 或.NET Framework 4.5 為目標的任何角色。 藉由使用**IntelliTrace**，您可以檢查角色執行個體過去發生的事件，並重現當時的內容。 請參閱[偵錯發佈的雲端服務使用 IntelliTrace 和 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=623016)並[使用 IntelliTrace](https://msdn.microsoft.com/library/dd264915.aspx)。

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>若要啟用遠端偵錯雲端服務

1. 開啟 Azure 專案的捷徑功能表，然後選取**發佈**。

2. 選取 **臨時**環境並**偵錯**組態。

    這是只是指導方針。 您可以選擇在生產環境中執行您的測試環境。 不過，您可能會造成不良影響使用者如果您啟用遠端偵錯，在實際執行環境。 您可以選擇 [發行] 組態中，但偵錯組態可讓偵錯更容易。

    ![選擇偵錯組態](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. 請遵循往常的步驟，但選取**啟用遠端偵錯工具的所有角色** 核取方塊**進階設定** 索引標籤。

    ![偵錯組態](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>若要將偵錯工具附加至在 Azure 中雲端服務

1. 在 伺服器總管 中，展開 雲端服務的節點。

2. 開啟您想要附加，然後選取的角色或角色執行個體的捷徑功能表**附加偵錯工具**。

    如果您偵錯角色時，Visual Studio 偵錯工具附加至該角色的每個執行個體。 偵錯工具會在執行該行程式碼，並符合中斷點任何條件的第一個角色執行個體的中斷點上中斷。 如果您偵錯執行個體，該執行個體，以及該特定執行個體執行該行程式碼，並符合中斷點的條件時，才某個中斷點上中斷連接偵錯工具。

    ![附加偵錯工具](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. 偵錯工具附加至執行個體之後，如常進行偵錯。 偵錯工具會自動附加至適當的主控件程序，為您的角色。 根據角色的是，偵錯工具附加至 w3wp.exe、 WaWorkerHost.exe、 或 WaIISHost.exe。 若要確認附加偵錯工具的程序，展開 [伺服器總管] 中的執行個體節點。 請參閱[Azure 角色架構](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx)如需有關 Azure 的程序。

    ![選取程式碼類型對話方塊](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. 若要識別附加偵錯工具的處理程序，開啟 處理序 對話方塊，在功能表列選擇 偵錯、 Windows、 處理程序。 (鍵盤： Ctrl + Alt + Z)若要中斷連結特定處理序，請開啟其捷徑功能表，然後按**中斷處理序**。 或者，在伺服器總管 中找出執行個體節點、 尋找處理程序、 開啟其捷徑功能表，，然後選取**中斷處理序**。

    ![偵錯處理序](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> 避免長時間的停駐點在中斷點時遠端偵錯。 Azure 會將停止超過幾分鐘的時間為沒有回應，並停止將流量傳送到該執行個體的程序。 如果您停止太久，msvsmon.exe 會從處理序中斷連結。

若要中斷偵錯工具從所有處理序連結您的執行個體或角色中，開啟 偵錯時，並選取您的執行個體的角色的捷徑功能表**中斷偵錯工具**。

## <a name="limitations-of-remote-debugging-in-azure"></a>在 Azure 中的遠端偵錯的限制

從 Azure SDK 2.3 起，遠端偵錯具有下列限制：

* 啟用遠端偵錯，您就無法發佈雲端服務，其中的任何角色都有超過 25 個執行個體。
* 偵錯工具會使用連接埠 30400 至 30424、 31400 至 31424，以及 32400 至 32424。 如果您嘗試使用任何這些連接埠，您將無法發佈您的服務，以及其中一個下列的錯誤訊息會出現在活動記錄檔中，適用於 Azure:

  * 驗證.cscfg 檔案，根據.csdef 檔案時發生錯誤。
    保留的連接埠範圍 'range' 端點 Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector 的角色 'role' 與已定義的連接埠或範圍重疊。
  * 配置失敗。 請稍後再重試、 嘗試減少 VM 大小或角色執行個體數目，或嘗試部署至不同的區域。

## <a name="debugging-azure-virtual-machines"></a>偵錯 Azure 虛擬機器

您可以偵錯使用 Visual Studio 中的 [伺服器總管] 中，Azure 虛擬機器上執行的程式。 當您啟用 Azure 的虛擬機器上的遠端偵錯時，Azure 會在虛擬機器上安裝遠端偵錯擴充功能。 然後，您可以附加至虛擬機器上的處理序，並像平常一樣偵錯。

> [!NOTE]
> 透過 Azure resource manager 堆疊所建立的虛擬機器可以從遠端偵錯，Visual Studio 2015 中使用雲端總管。 如需詳細資訊，請參閱 <<c0> [ 使用雲端總管管理 Azure 資源](http://go.microsoft.com/fwlink/?LinkId=623031)。

### <a name="to-debug-an-azure-virtual-machine"></a>若要偵錯 Azure 虛擬機器

1. 在 [伺服器總管] 中，展開 [虛擬機器] 節點，然後選取您想要偵錯的虛擬機器的節點。

2. 開啟操作功能表，然後選取**啟用偵錯**。 當系統詢問您是否確定如果您想要啟用虛擬機器上，選取偵錯**是**。

    Azure 會以啟用偵錯的虛擬機器上安裝遠端偵錯擴充功能。

    ![虛擬機器啟用偵錯命令](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure 活動記錄檔](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. 遠端偵錯擴充功能安裝完成後，開啟虛擬機器的操作功能表，然後選取**附加偵錯工具...**

    Azure 虛擬機器上取得的處理序清單，並在 [附加至處理序] 對話方塊中顯示它們。

    ![附加偵錯工具命令](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. 在 **附加至處理序**對話方塊中，選取**選取**來限制結果清單，顯示您要偵錯的程式碼的類型。 您可以偵錯 32 位元或 64 位元 managed 程式碼、 原生程式碼，或兩者。

    ![選取程式碼類型對話方塊](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. 選取您想要在虛擬機器上偵錯，然後選取 處理程的序**附加**。 比方說，您可以選擇 w3wp.exe 處理序，如果您想要偵錯虛擬機器上的 web 應用程式。 請參閱[偵錯一或多個處理序，在 Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx)並[Azure 角色架構](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx)如需詳細資訊。

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>建立 web 專案和虛擬機器進行偵錯

之前發行 Azure 專案，您可能會發現它可支援偵錯和測試案例，以及您可以在其中安裝測試和監視程式可以在受控制環境中測試它很有用。 遠端偵錯您的虛擬機器上的應用程式是一種執行這類測試方法。

Visual Studio ASP.NET 專案提供選項，以便建立好用的虛擬機器，您可以使用應用程式測試。 虛擬機器包含經常需要的端點，例如 PowerShell、 遠端桌面和 WebDeploy。

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>若要建立 web 專案和虛擬機器進行偵錯

1. 在 Visual Studio 中建立新的 ASP.NET Web 應用程式。

2. 在 [新增 ASP.NET 專案] 對話方塊中，在 [Azure] 區段中，選擇**虛擬機器**下拉式清單方塊中。 離開**建立遠端資源**選取核取方塊。 選取 **確定**以繼續。

    **在 Azure 上建立虛擬機器** 對話方塊隨即出現。

    ![建立 ASP.NET web 專案 對話方塊](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    **注意：** 會要求您登入您的 Azure 帳戶如果您還沒登入。

3. 選取虛擬機器的各種設定，然後選取**確定**。 請參閱[虛擬機器](http://go.microsoft.com/fwlink/?LinkId=623033)如需詳細資訊。

    您輸入的 DNS 名稱會是虛擬機器的名稱。

    ![在 Azure 的對話方塊中建立虛擬機器](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure 建立虛擬機器，然後佈建並設定端點，例如遠端桌面和 Web Deploy

4. 虛擬機器完全設定之後，請在伺服器總管 中選取虛擬機器的節點。

5. 開啟操作功能表，然後選取**啟用偵錯**。 當系統詢問您是否確定如果您想要啟用虛擬機器上，選取偵錯**是**。

    Azure 會將遠端偵錯擴充功能安裝到虛擬機器，以啟用偵錯。

    ![虛擬機器啟用偵錯命令](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure 活動記錄檔](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. 發佈您的專案中所述[如何： 部署 Web 專案使用單鍵發行 Visual Studio 中](https://msdn.microsoft.com/library/dd465337.aspx)。 因為您想要在虛擬機器上進行偵錯**設定**頁**發佈 Web**精靈中，選取**偵錯**做為組態。 這可確保在偵錯時，程式碼符號可供使用。

    ![發行設定](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. 在 **檔案發佈選項**，選取**移除目的地上的其他檔案**如果稍早已部署專案。

8. 專案發佈，在 [伺服器總管] 中，虛擬機器的操作功能表上之後選取**附加偵錯工具...**

    Azure 虛擬機器上取得的處理序清單，並在 [附加至處理序] 對話方塊中顯示它們。

    ![附加偵錯工具命令](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. 在 **附加至處理序**對話方塊中，選取**選取**來限制結果清單，顯示您要偵錯的程式碼的類型。 您可以偵錯 32 位元或 64 位元 managed 程式碼、 原生程式碼，或兩者。

    ![選取程式碼類型對話方塊](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. 選取您想要在虛擬機器上偵錯，然後選取 處理程的序**附加**。 比方說，您可以選擇 w3wp.exe 處理序，如果您想要偵錯虛擬機器上的 web 應用程式。 請參閱[偵錯一或多個 Visual Studio 中的處理序](https://msdn.microsoft.com/library/jj919165.aspx)如需詳細資訊。

## <a name="next-steps"></a>後續步驟

* 使用**Intellitrace**從發行伺服器收集的呼叫和事件記錄檔。 請參閱[偵錯發佈的雲端服務使用 IntelliTrace 和 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=623016)。

* 使用**Azure 診斷**若要從角色內的程式碼執行記錄的詳細的資訊，不論角色執行在開發環境中或在 Azure 中。 請參閱[使用 Azure 診斷收集記錄資料](http://go.microsoft.com/fwlink/p/?LinkId=400450)。
