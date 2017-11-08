---
title: "Visual Studio 無法復原的程序錯誤 | Microsoft Docs"
ms.custom: 
ms.date: 02/23/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 2263956f-3ae0-4bdc-9d3a-4991dfaf4ddb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology:
- vs-ide-general
ms.translationtype: Human Translation
ms.sourcegitcommit: b5f39ea962f6b4dcc0e2c6947b2eeabf53d3329a
ms.openlocfilehash: ba0a0aacc68e2eb9a5cd9b5b672808a71e8c09eb
ms.contentlocale: zh-tw
ms.lasthandoff: 03/01/2017

---
# <a name="visual-studio-unrecoverable-process-error"></a>Visual Studio 無法復原的程序錯誤

Visual Studio 2017 會使用多個跨處理序的程序執行所需的背景工作，例如即時的單元測試、程式碼分析器等等。 這些程序會跨處理序執行，以保障 Visual Studio 效能優勢 (例如，在進行需要大量資源、長時間執行的工作時，確保 Visual Studio 得以快速回應)。 此外，由於 Visual Studio 是 32 位元處理序，跨處理序執行程序時，可讓需耗費大量記憶體的工作擁有較充沛的記憶體運作空間。

如果基於某些原因，導致任何必要的處理序結束，快顯資訊列會出現下列訊息：

「很抱歉，Visual Studio 所使用的處理序發生無法復原的錯誤。 建議您儲存工作，然後關閉並重新啟動 Visual Studio。」

如果您看到此訊息，應該立即儲存工作，然後關閉並重新啟動 Visual Studio。 如果您不這麼做，Visual Studio 可能會隨時當機。

## <a name="list-of-processes"></a>處理序清單

以下是 Visual Studio 必須跨處理序執行才能正常運作的程序清單。

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

