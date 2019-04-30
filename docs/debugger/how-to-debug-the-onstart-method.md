---
title: HOW TO：偵錯 OnStart 方法 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2fc5e8a7e0bbc80fd7fa0aa2d242239a9be6a219
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894413"
---
# <a name="how-to-debug-the-onstart-method"></a>HOW TO：對 OnStart 方法進行偵錯
您可以藉由啟動服務並將偵錯工具附加到服務處理序，對 Windows 服務進行偵錯。 如需詳細資訊，請參閱[如何：偵錯 Windows 服務應用程式](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)。 但是若要對 Windows 服務的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> 方法進行偵錯，您必須從方法內啟動偵錯工具。

1. 在 <xref:System.Diagnostics.Debugger.Launch%2A> 方法的開頭加入對 `OnStart()`的呼叫。

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. 啟動服務 (您可以使用 `net start`，或在 [服務]  視窗中加以啟動)。

    您應該會看到如下所示的對話方塊：

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. 選取 [是，對 \<服務名稱> 進行偵錯]。

4. 在 [Just-In-Time 偵錯工具] 視窗中，選取您要用來偵錯的 Visual Studio 版本。

    ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Visual Studio 的新執行個體隨即啟動，並在 `Debugger.Launch()` 方法停止執行。

## <a name="see-also"></a>另請參閱
- [偵錯工具安全性](../debugger/debugger-security.md)
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
