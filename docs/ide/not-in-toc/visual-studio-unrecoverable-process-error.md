---
title: 處理序發生無法復原的錯誤
description: 瞭解 Visual Studio 正常作業期間可能會發生無法復原錯誤的處理常式。
ms.custom: SEO-VS-2020
ms.date: 09/10/2020
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e44f96e0a8056a369b164e725aca6832b5a349cb
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871479"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Visual Studio 無法復原的程序錯誤

Visual Studio 會使用多個處理序外之程序來執行所需的背景工作，例如 Live Unit Testing、程式碼分析器等等。 這些處理序會跨處理序執行，以保障 Visual Studio 效能優勢 (例如，在執行長時間且需要大量資源的工作時，確保 Visual Studio 得以快速回應)。 此外，由於 Visual Studio 是 32 位元處理序，跨處理序執行程序時，可讓需耗費大量記憶體的工作擁有較充沛的記憶體運作空間。

如果 *ServiceHub.RoslynCodeAnalysisService.exe* 或 *ServiceHub.RoslynCodeAnalysisService32.exe* 處理序因某個原因而結束，則會出現快顯資訊列，訊息如下：

**「很可惜，Visual Studio 使用的進程發生無法復原的錯誤。建議您儲存工作，然後關閉並重新啟動 Visual Studio。」**

如果您看到此訊息，應該儲存工作，然後關閉並重新啟動 Visual Studio。

## <a name="list-of-processes"></a>處理序清單

以下是 Visual Studio 所使用之跨處理序的處理序清單。 此清單包含特定工作流程或情節中啟動的處理序；因此，在大部分情況下，它們不會全部同時執行。

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- MSBuild.exe
- PerfWatson2.exe
- ScriptedSandbox64.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.VSDetouredHost.exe
- VBCSCompiler.exe
- VsHub.exe
- vstest.discoveryengine.x86.exe
- WaAppAgent.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe

如果所有這些處理序意外終止，則 Visual Studio 內的某些功能會停止運作。 針對某些處理序，遺失功能可能不重要。 針對其他處理序，則會影響 Visual Studio 的穩定性，並顯示錯誤訊息。

> [!NOTE]
> 如果您遇到此頁面未提及的問題，請透過 [回報 [問題](../../ide/how-to-report-a-problem-with-visual-studio.md) ] 工具向我們報告，該工具會出現在 Visual Studio 安裝程式和 Visual Studio IDE 中。
