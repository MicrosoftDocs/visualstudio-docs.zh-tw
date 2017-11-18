---
title: "偵錯已安裝的應用程式套件 (UWP) |Microsoft 文件"
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 354c574a890ae0385a58594a22b3314a13b9d6b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>偵錯已安裝的應用程式套件 Visual Studio (UWP)

您可以按一下 偵錯任何已安裝的應用程式套件**偵錯 > 其他偵錯目標 > 偵錯已安裝的應用程式套件**。 這個偵錯的方法有通用 Windows 應用程式 (UWP) 在這些裝置上：

* Windows 10 （不支援在手機上）
* XBox
* HoloLens
* IoT

如需有關這些功能的詳細資訊，請參閱部落格文章上更新[偵錯已安裝應用程式封裝](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/)和上的 post[建置通用 Windows 應用程式 (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/)。

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>偵錯已安裝的應用程式套件或在本機電腦或裝置上的執行應用程式

1. 您在 Visual Studio 中開啟的 UWP 專案，按一下**偵錯 > 其他偵錯目標 > 偵錯已安裝的應用程式套件**。

2. 選取 **本機**或**裝置**。

     如果您選擇**裝置**，您的電腦必須實際連接到 Windows 10 裝置。

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     目前正在執行安裝的應用程式封裝顯示底下**執行**節點。 安裝不顯示設定下執行的應用程式套件**未執行**。

3. 選取您想要在偵錯的應用程式名稱**執行**或**未執行**選擇**啟動**或者，如果應用程式已在執行中，選擇**附加**.

     如果您選取**不啟動，但在啟動時，將我的程式碼進行偵錯**，這會導致 Visual Studio 偵錯工具附加至您的應用程式，當您啟動在自訂階段。 這是有效的方式來偵錯控制路徑從[不同啟動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)，例如使用自訂參數的通訊協定啟動。

> [!NOTE]
> Visual Studio 也可以將附加至任何正在執行的 UWP 應用程式處理序藉由選取**偵錯**，然後**附加至處理序**。 附加至正在執行的處理序不需要原始的 Visual Studio 專案中，但載入處理序的符號將有助於大幅偵錯的處理序，您不需要的原始碼時。
  
## <a name="remote"></a>偵錯在遠端電腦上的安裝或執行應用程式 

當您在遠端電腦上安裝的應用程式封裝偵錯時第一次時，Visual Studio 會安裝適用於您的目標裝置的遠端工具的正確版本。 Windows 10 電腦、 XBox、 HoloLens 或 IoT 裝置，必須是您的目標裝置。

1. 在您的 Windows 10 裝置上啟用[開發人員模式下](/windows/uwp/get-started/enable-your-device-for-development)。

2. 如果您要連接至遠端電腦上執行前的建立者的更新版本的 Windows 10 中，第一次手動[安裝並啟動遠端偵錯工具](../debugger/remote-debugging.md)。

     為 XBox、 HoloLens 或 IoT 裝置和 Windows 裝置執行 Windows 10 建立者的更新，您不需要手動安裝遠端偵錯工具。 部署應用程式時，就會自動安裝遠端工具。

3. 按一下**偵錯 > 其他偵錯目標 > 偵錯已安裝應用程式套件**。

4. 從第一個下拉式清單中，選擇 **遠端機器**。

5. 輸入名稱或您想要將附加至電腦的 IP 位址。

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     如果您無法附加使用電腦名稱 (選擇之後**啟動**)，請改用 IP 位址。 使用 XBox、 HoloLens 或 IoT 裝置的 IP 位址。

5. 選擇如何選取中的選項來驗證**驗證模式**。

    針對大部分的應用程式，請保留預設值， **Universal （未加密的通訊協定）**。

6. 選取您想要在偵錯的應用程式名稱**執行**或**未執行**選擇**啟動**或 （適用於執行的應用程式）**附加**。

     如果您選取**不啟動，但在啟動時，將我的程式碼進行偵錯**，這會導致 Visual Studio 偵錯工具附加至應用程式套件，當您啟動在自訂階段。 這是有效的方式來偵錯控制路徑從[不同啟動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)，例如使用自訂參數的通訊協定啟動。

     當您已連接 XBox、 HoloLens 或 IoT 裝置上安裝的應用程式封裝偵錯時第一次時，Visual Studio 會安裝您的目標裝置的遠端偵錯工具的正確版本。 這可能需要一些時間，您會看到一則訊息``Starting remote debugger``而發生此問題。

     > [!NOTE]
> 在存在、 XBox 或 HoloLens 裝置會重新啟動應用程式如果它已經在執行附加了偵錯工具。

> [!NOTE]
> UWP 應用程式可以開發及編譯的 Windows 8.1 或更新版本，但需要執行的 Windows 10。 如果您正在開發 UWP 應用程式在 Windows 8.1 的電腦上，從遠端可以偵錯其他的 Windows 10 裝置上執行的 UWP 應用程式，前提是主控件和目標電腦位於相同的區域網路。 若要這樣做，請下載並兩台電腦上安裝 Visual Studio 遠端工具。 已安裝的版本必須符合現有版本的 Visual Studio 一起安裝，並選取 (x86、 x64) 的架構也必須符合您目標的應用程式的。
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯](../debugger/index.md)  
 [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)  
 [遠端偵錯](../debugger/remote-debugging.md)  
 [設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)