---
title: ARM 電源裝置上的 Visual Studio
description: 在具有 ARM 型處理器的裝置上使用 Visual Studio 的建議。
ms.date: 09/10/2020
ms.topic: conceptual
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 31fb209a3f19c052c19e98691b8643bb098887ee
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295802"
---
# <a name="visual-studio-on-arm-powered-devices"></a>ARM 驅動裝置上的 Visual Studio

> [!IMPORTANT]
> 只有使用 x86 或 AMD64/x64 型處理器的裝置才支援 Visual Studio。

Visual Studio 是根據 x86 架構的目標處理器來建立的，而且 ARM 型處理器沒有任何版本的 Visual Studio。 不過，Windows 會 [在 ARM 上提供 x86 模擬](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation)，Visual Studio 可以執行。 透過 x86 模擬在 ARM 處理器上執行 Visual Studio 時，會嚴重降低 Visual Studio 的效能，而且 Visual Studio 中的數個功能並未設計成在此案例中運作。 因此，我們不建議在使用 ARM 型處理器的裝置上執行 Visual Studio，而改為建議遠端目標 ARM 裝置。

## <a name="remote-targeting-arm-devices"></a>遠端目標 ARM 裝置
為了獲得最佳體驗，我們建議您在不同的 x86 驅動電腦上使用 Visual Studio，並使用 Visual Studio 中的遠端部署和偵錯工具功能，將目標設為 ARM 型裝置。 若要在裝置上偵測到已安裝的 Windows 通用應用程式，請參閱 [已安裝的應用程式封裝](../debugger/debug-installed-app-package.md) 檔。 若要部署新的應用程式，請參閱 [執行 Windows Store 應用程式 remotley](../debugger/run-windows-store-apps-on-a-remote-machine.md)。 如需其他所有應用程式類型，請參閱 [遠端偵錯](../debugger/remote-debugging.md) 程式檔。

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>在 ARM 裝置上執行 Visual Studio 的秘訣

### <a name="use-only-when-needed"></a>只有在需要時才使用
只有當 ARM 特定工作需要時，才使用 Visual Studio 來優化您的時間。 任何 ARM 裝置上的效能都將變得很差，而且您可能會發現它無法正常使用。

### <a name="install-time"></a>安裝時間
規劃 Visual Studio 需要較長的時間才能安裝，並預期它會在一段時間內暫停，或需要重新開機。
 
### <a name="remote-tools"></a>遠端工具
若要對遠端裝置上執行的應用程式進行偵錯工具，您必須 [下載並安裝適用于 ARM 的遠端工具](../debugger/remote-debugging.md#download-and-install-the-remote-tools) 。

### <a name="start-debugging-f5"></a>開始偵錯 (F5)
並非所有 Visual Studio 專案都會設定為在您從 ARM 裝置啟動 (**F5**) 的偵錯工具時，在本機啟動專案。 即使您的應用程式是在本機執行，您可能還是需要設定遠端偵錯程式的 Visual Studio。 如需詳細資訊，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。

## <a name="we-need-your-help"></a>我們需要您的協助！
如果您想要 Visual Studio 在 ARM 裝置上以原生方式執行，我們很樂意知道所需的案例和支援。 您可以藉由在 [開發人員群體](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html)上張貼來聯繫我們。
