---
title: 遠端偵錯 |Microsoft Docs
description: 使用 Visual Studio 遠端偵錯程式，對已部署在不同電腦上的 Visual Studio 應用程式進行 Debug 錯。
ms.custom:
- remotedebugging
- seodec18
- SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f67035dc2f7a33fb436c0c51ba2214272ab2cf79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891419"
---
# <a name="remote-debugging"></a>Remote Debugging
您可以偵錯已部署在不同電腦的 Visual Studio 應用程式。 若要這樣做，您可以使用 Visual Studio 遠端偵錯工具。

如需遠端偵錯程式的深入指示，請參閱下列主題。

|狀況|連結|
|-|-|-|
|Azure App Service|[Azure 上的遠端偵錯程式 ASP.NET](../debugger/remote-debugging-azure.md) ，或 Visual Studio Enterprise 的 [快照偵錯工具](../debugger/debug-live-azure-applications.md)|
|Azure VM|[在 Azure 上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[對 Azure Service Fabric 應用程式進行偵錯工具](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[遠端偵錯 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) 或 [遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# 或 Visual Basic|[對 C# 或 Visual Basic 專案進行遠端偵錯](../debugger/remote-debugging-csharp.md)|
|C++|[對 C++ 專案進行遠端偵錯](../debugger/remote-debugging-cpp.md)|
| (UWP) 的通用 Windows 應用程式|[在遠端電腦上執行 UWP 應用程式](../debugger/run-windows-store-apps-on-a-remote-machine.md)，或[將已安裝的應用程式套件進行調試](../debugger/debug-installed-app-package.md)程式|

如果您只想要下載並安裝遠端偵錯程式，且您的案例不需要任何額外的指示，請遵循本文中的步驟。

## <a name="download-and-install-the-remote-tools"></a>下載及安裝遠端工具

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> 需求

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> (選擇性) 從檔案共用執行遠端偵錯程式

您可以在已安裝 Visual Studio Community、Professional 或 Enterprise 的電腦上，找到 (*msvsmon.exe*) 的遠端偵錯程式。 在某些案例中，設定遠端偵錯程式最簡單的方式，就是從檔案共用執行遠端偵錯程式 ( # A0) 。 如需使用限制，請參閱遠端偵錯程式的說明頁面 (**協助 >** 在遠端偵錯程式中的使用方式) 。

1. 在符合您 Visual Studio 版本的目錄中尋找 *msvsmon.exe* ：

   ::: moniker range=">=vs-2019"

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. 共用 Visual Studio 電腦上的 [ **遠端偵錯程式** ] 資料夾。

3. 在遠端電腦上，從共用資料夾執行 *msvsmon.exe* 。 遵循 [安裝指示](#bkmk_setup)。

> [!TIP]
> 如需命令列安裝和命令列參考，請在已安裝 Visual Studio 的電腦上輸入命令列以查看 *msvsmon.exe* 的 [說明] 頁面 ``msvsmon.exe /?`` (或移至 [說明] **>** [遠端偵錯程式]) 中的使用方式。

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> 設定遠端偵錯程式

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> 設定遠端偵錯工具
在您第一次啟動遠端偵錯工具後，可以變更其組態的某些部分。

- 如果您需要為其他使用者新增許可權，以連接到遠端偵錯程式，請選擇 [ **工具] > 許可權**。 您必須具有系統管理員權限才能授與或拒絕使用權限。

     > [!IMPORTANT]
     > 您可以在使用者帳戶下執行遠端偵錯程式，該帳戶與您在 Visual Studio 電腦上使用的使用者帳戶不同，但您必須將不同的使用者帳戶新增至遠端偵錯程式的許可權。

     或者，您也可以從命令列使用 **\<username> /allow** 參數： **msvsmon/allow \<username@computer>** 啟動遠端偵錯程式。

- 如果您需要變更驗證模式或通訊埠編號，或指定遠端工具的超時值：選擇 [ **工具] > 選項**]。

     如需預設使用的埠號碼清單，請參閱 [遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)。

     > [!WARNING]
     > 您可以選擇在 [非驗證] 模式下執行遠端工具，但非常不建議您使用這個模式。 在此模式中執行時不具有網路安全性。 只有在確定網路沒有面臨惡意或攻擊流量的風險時，才能選擇非驗證模式。

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> (選擇性) 將遠端偵錯程式設定為服務
若要在 ASP.NET 和其他伺服器環境中進行偵錯工具，您必須以系統管理員身分執行遠端偵錯程式，或者，如果您想要一律執行，請以服務的形式執行遠端偵錯程式。

 如果您想要將遠端偵錯程式設定為服務，請遵循下列步驟。

1. 尋找 [遠端偵錯工具組態精靈]  (rdbgwiz.exe)。  (這是與遠端偵錯程式不同的應用程式。 ) 只有在安裝遠端工具時才能使用。 它不會隨 Visual Studio 一同安裝。

2. 開始執行 [組態精靈]。 當第一頁出現時，按一下 [下一步] 。

3. 核取 [以服務方式執行 Visual Studio 2015 遠端偵錯工具]  核取方塊。

4. 加入使用者帳戶的名稱和密碼。

    您可能需要將 [**以服務方式登** 入] 使用者權限新增至此帳戶 (在 [**開始**] 頁面或視窗中尋找 [**本機安全性原則**] ([secpol.msc])  (或在命令提示字元中輸入 **secpol.msc**) 。 視窗出現時，請按兩下 [使用者權限指派] ，然後在右窗格中尋找 [以服務方式登入]  。 對它按兩下。 將使用者帳戶新增至 [屬性] 視窗，然後按一下 [確定]。 按一下 [下一步] 。

5. 選取您要遠端工具與之通訊的網路類型。 必須至少選取一種網路類型。 如果此電腦經由網域連線，您就必須選擇第一個項目。 如果此電腦經由工作群組或家用群組連線，您就必須選擇第二個或第三個項目。 按一下 [下一步] 。

6. 如果可以啟動服務，您就會看到 [您已順利完成 Visual Studio 遠端偵錯工具組態精靈] 。 如果無法啟動服務，您就會看到 [無法完成 Visual Studio 遠端偵錯工具組態精靈] 。 此頁面也會提供啟動服務所需遵循的一些祕訣。

7. 按一下 [完成] 。

   此時 [遠端偵錯工具] 會以服務方式執行。 您可以前往 **主控台 > 服務** ，並尋找 **Visual Studio 2015 遠端偵錯程式**，來確認這一點。

   您可以從 **主控台 > 服務** 停止和啟動遠端偵錯程式服務。

## <a name="set-up-debugging-with-remote-symbols"></a>使用遠端符號設定調試

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>另請參閱

- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [設定 Windows 防火牆以進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)
- [遠端偵錯 ASP.NET Core 在遠端 IIS 電腦上](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)