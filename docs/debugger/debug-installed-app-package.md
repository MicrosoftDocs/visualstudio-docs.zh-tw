---
title: 偵錯已安裝的應用程式套件 (UWP) |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 291f24c6ffdf885cf3d24c5ff163c2f4f911d7ce
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279550"
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>偵錯已安裝的應用程式封裝在 Visual Studio (UWP)

您可以將任何已安裝的應用程式套件偵錯，即可**偵錯 > 其他偵錯目標 > 偵錯 Installed App Package**。 這個偵錯的方法是使用適用於通用 Windows 應用程式 (UWP) 在這些裝置上：

* Windows 10 （不支援在手機上）
* XBox
* HoloLens
* IoT

如需這些功能的詳細資訊，請參閱部落格文章上的更新[偵錯已安裝的應用程式套件](https://blogs.msdn.microsoft.com/devops/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/)並在 post[建置通用 Windows App (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/)。

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>已安裝的應用程式套件或在本機電腦或裝置上執行的應用程式進行偵錯

1. 您在 Visual Studio 中開啟的 UWP 專案，按一下**偵錯 > 其他偵錯目標 > 偵錯 Installed App Package**。

2. 選取 **本機電腦**或是**裝置**。

     如果您選擇**裝置**，您的電腦必須實際連線到 Windows 10 裝置。

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     正在安裝應用程式套件會顯示下的**執行**節點。 安裝不顯示設定下執行的應用程式套件**未執行**。

3. 選取您想要在偵錯的應用程式名稱**執行**或**未執行**，然後選擇 **啟動**或者，如果應用程式已在執行中，選擇 **附加**.

     如果您選取**不啟動，但啟動時，將我的程式碼進行偵錯**，這會導致 Visual Studio 偵錯工具附加至您的應用程式，當您啟動在自訂的時間。 這是偵錯中的控制路徑的有效辦法[不同的啟動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)，例如，使用自訂參數的通訊協定啟用。

> [!NOTE]
> Visual Studio 也可以附加至任何執行中 UWP 應用程式處理序選取**偵錯**，然後**附加至處理序**。 附加至執行中處理序並不需要原始的 Visual Studio 專案中，但您不需要的原始碼的程序進行偵錯時載入處理序的符號可大幅協助。
  
## <a name="remote"></a> 偵錯遠端電腦上的安裝或執行應用程式 

當您第一次偵錯遠端電腦上已安裝的應用程式套件時，Visual Studio 會安裝適用於您的目標裝置的遠端工具的正確版本。 Windows 10 電腦、 XBox、 HoloLens、 或 IoT 裝置，必須是您的目標裝置。

1. 在您的 Windows 10 裝置上啟用[開發人員模式](/windows/uwp/get-started/enable-your-device-for-development)。

2. 如果您要連接至遠端電腦上執行預先建立者更新版本的 Windows 10 中，第一次手動[安裝並啟動遠端偵錯工具](../debugger/remote-debugging.md)。

     XBox、 HoloLens、 或 IoT 裝置，以及執行 Windows 10 Creator's Update 的 Windows 裝置，您不需要手動安裝遠端偵錯工具。 當您部署應用程式時，就會自動安裝遠端工具。

3. 按一下 **偵錯 > 其他偵錯目標 > 偵錯已安裝應用程式套件**。

4. 從第一個下拉式清單中，選擇**遠端機器**。

5. 輸入名稱或您想要附加至電腦的 IP 位址。

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     如果您不能附加使用電腦名稱 (您選擇後**啟動**)，改為使用的 IP 位址。 使用 XBox、 HoloLens、 或 IoT 裝置的 IP 位址。

5. 選擇如何藉由選取的選項中進行驗證**驗證模式**。

    對於大多數的應用程式，請保留預設值，**通用 （未加密的通訊協定）**。

6. 選取您想要在偵錯的應用程式名稱**執行**或是**未執行**，然後選擇 **啟動**或 （適用於執行應用程式）**附加**。

     如果您選取**不啟動，但啟動時，將我的程式碼進行偵錯**，這會導致 Visual Studio 偵錯工具附加至應用程式套件，當您啟動在自訂的時間。 這是偵錯中的控制路徑的有效辦法[不同的啟動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)，例如，使用自訂參數的通訊協定啟用。

     當您第一次偵錯連接 XBox、 HoloLens、 或 IoT 裝置上已安裝的應用程式套件時，Visual Studio 會安裝正確版本的目標裝置的遠端偵錯工具。 這可能需要一些時間，您會看到一則訊息``Starting remote debugger``而發生此問題。

     > [!NOTE]
> 在存在、 XBox 或 HoloLens 裝置將會重新啟動應用程式偵錯工具附加，如果已在執行。

如需遠端部署的 UWP 應用程式的進階選項的資訊，請參閱 [部署和偵錯 UWP apps]((/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)。 
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯](../debugger/index.md)  
 [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)  
 [遠端偵錯](../debugger/remote-debugging.md)  
 [設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)