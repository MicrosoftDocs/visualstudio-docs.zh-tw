---
title: 遠端偵錯 |微軟文檔
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9918a2de67693c0232c94a736f12c7af0a0b959c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302074"
---
# <a name="remote-debugging"></a>遠端偵錯
您可以偵錯已部署在不同電腦的 Visual Studio 應用程式。 若要這樣做，您可以使用 Visual Studio 遠端偵錯工具。

有關遠端偵錯的深入說明，請參閱這些主題。

|狀況|連結|
|-|-|-|
|Azure App Service|[Azure 上的快照調試器](../debugger/debug-live-azure-applications.md)或[遠端偵錯ASP.NET](../debugger/remote-debugging-azure.md)|
|Azure VM|[在 Azure 上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[調試 Azure 服務結構應用程式](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[遠端偵錯ASP.NET核心](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)調試或[遠端偵錯ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# 或 Visual Basic|[遠端偵錯 C# 或 Visual Basic 專案](../debugger/remote-debugging-csharp.md)|
|C++|[遠端偵錯C++專案](../debugger/remote-debugging-cpp.md)|
|通用 Windows 應用 （UWP）|[在遠端電腦上運行 UWP 應用](../debugger/run-windows-store-apps-on-a-remote-machine.md)或[調試已安裝的應用包](../debugger/debug-installed-app-package.md)|

如果您只想下載並安裝遠端偵錯器，並且不需要針對您的方案提供任何其他說明，請按照本文中的步驟操作。

## <a name="download-and-install-the-remote-tools"></a>下載及安裝遠端工具

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a>要求

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a>（可選）從檔共用運行遠端偵錯器

您可以在已安裝的視覺化工作室社區、專業版或企業版的電腦中找到遠端偵錯器 （*msvsmon.exe）。* 對於某些方案，設置遠端偵錯的最簡單方法是從檔共用運行遠端偵錯器 （msvsmon.exe）。 有關使用限制，請參閱遠端偵錯器的説明頁（遠端偵錯器中的**説明>使用方式**）。

1. 在與您的視覺工作室版本的目錄中查找*msvsmon.exe：*

   ::: moniker range=">=vs-2019"

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. 在視覺化工作室電腦上共用**遠端偵錯器**資料夾。

3. 在遠端電腦上，從共用資料夾中運行*msvsmon.exe。* 按照[設置說明](#bkmk_setup)操作。

> [!TIP]
> 有關命令列安裝和命令列引用，請參閱*msvsmon.exe*的説明頁，通過在安裝了``msvsmon.exe /?``Visual Studio 的電腦上的命令列中鍵入（或轉到遠端偵錯器中的**説明>使用方式**）。

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>設置遠端偵錯器

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> 設定遠端偵錯工具
在您第一次啟動遠端偵錯工具後，可以變更其組態的某些部分。

- 如果需要為其他使用者添加許可權以連接到遠端偵錯器，請選擇 **"工具>許可權**"。 您必須具有系統管理員權限才能授與或拒絕使用權限。

     > [!IMPORTANT]
     > 您可以在與 Visual Studio 電腦上使用的使用者帳戶不同的使用者帳戶下運行遠端偵錯器，但必須將不同的使用者帳戶添加到遠端偵錯器的許可權。

     或者，您可以使用**\</allow 使用者名>** 參數 **：msvsmon \< username@computer /allow>** 從命令列啟動遠端偵錯器。

- 如果需要更改身份驗證模式或埠號，或為遠端工具指定超時值：請選擇**工具>選項**。

     有關預設情況下使用的埠號的清單，請參閱[遠端偵錯器埠分配](../debugger/remote-debugger-port-assignments.md)。

     > [!WARNING]
     > 您可以選擇在 [非驗證] 模式下執行遠端工具，但非常不建議您使用這個模式。 在此模式中執行時不具有網路安全性。 只有在確定網路沒有面臨惡意或攻擊流量的風險時，才能選擇非驗證模式。

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a>（可選）將遠端偵錯器配置為服務
要在ASP.NET和其他伺服器環境中進行調試，必須作為管理員運行遠端偵錯器，或者，如果您希望它始終運行，則將遠端偵錯器作為服務運行。

 如果要將遠端偵錯器配置為服務，請按照以下步驟操作。

1. 尋找 [遠端偵錯工具組態精靈] **** (rdbgwiz.exe)。 （這是與遠端偵錯器不同的應用程式。僅當安裝遠端工具時，它才可用。 它不會隨 Visual Studio 一同安裝。

2. 開始執行 [組態精靈]。 當第一頁出現時，按一下 [下一步] ****。

3. 核取 [以服務方式執行 Visual Studio 2015 遠端偵錯工具] **** 核取方塊。

4. 加入使用者帳戶的名稱和密碼。

    您可能需要將 **"登錄"作為服務**使用者的權利添加到此帳戶（在 **"開始"** 頁或視窗中查找**本地安全性原則**（secpol.msc）（或在命令提示符處鍵入**秒分）。** 視窗出現時，請按兩下 [使用者權限指派] ****，然後在右窗格中尋找 [以服務方式登入] **** 。 對它按兩下。 將使用者帳戶新增至 [屬性]**** 視窗，然後按一下 [確定]****。 按 [下一步]****。

5. 選取您要遠端工具與之通訊的網路類型。 必須至少選取一種網路類型。 如果此電腦經由網域連線，您就必須選擇第一個項目。 如果此電腦經由工作群組或家用群組連線，您就必須選擇第二個或第三個項目。 按 [下一步]****。

6. 如果可以啟動服務，您就會看到 [您已順利完成 Visual Studio 遠端偵錯工具組態精靈] ****。 如果無法啟動服務，您就會看到 [無法完成 Visual Studio 遠端偵錯工具組態精靈] ****。 此頁面也會提供啟動服務所需遵循的一些祕訣。

7. 按一下 **[完成]**。

   此時 [遠端偵錯工具] 會以服務方式執行。 您可以通過訪問**控制台>服務和**查找**Visual Studio 2015 遠端偵錯器來**驗證這一點。

   可以從**控制台>服務**停止並啟動遠端偵錯器服務。

## <a name="set-up-debugging-with-remote-symbols"></a>使用遠端符號設置調試

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>另請參閱

- [首先查看調試器](../debugger/debugger-feature-tour.md)
- [配置用於遠端偵錯的 Windows 防火牆](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)
- [遠端 iIS 電腦上的遠端偵錯ASP.NET核心](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)