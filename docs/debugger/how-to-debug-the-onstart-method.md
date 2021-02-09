---
title: Debug OnStart 方法 |Microsoft Docs
description: 瞭解如何在方法內啟動偵錯工具，以在 Visual Studio 中進行 Windows 服務的 OnStart 方法的偵錯工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 51096d7a47de80be7434659936165ba0a29f7c67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899287"
---
# <a name="how-to-debug-the-onstart-method"></a>如何：偵錯 OnStart 方法
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

    ![Visual Studio 即時偵錯工具] 對話方塊的螢幕擷取畫面，其中顯示 WindowsService-Asis.exe 中發生未處理的 .NET Framework 例外狀況。](../debugger/media/onstartdebug.png)

3. 選取 **[是，Debug] \<service name> 。**

4. 在 [Just-In-Time 偵錯工具] 視窗中，選取您要用來偵錯的 Visual Studio 版本。

    ![Visual Studio 即時偵錯工具視窗的螢幕擷取畫面，其中已在可能的偵錯工具清單中選取 [Microsoft Visual Studio 2015 的新實例]。](../debugger/media/justintimedebugger.png)

5. Visual Studio 的新執行個體隨即啟動，並在 `Debugger.Launch()` 方法停止執行。

## <a name="see-also"></a>另請參閱
- [偵錯工具安全性](../debugger/debugger-security.md)
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
