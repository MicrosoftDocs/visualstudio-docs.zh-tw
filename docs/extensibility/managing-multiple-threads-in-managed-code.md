---
title: 如何：在 Managed 程式碼中管理多個執行緒 |Microsoft Docs
description: 瞭解如何在程式碼中管理多個執行緒（如果 managed VSPackage 延伸模組呼叫非同步方法，或在 Visual Studio UI 執行緒中有作業）。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5486d5faa4f994883d2a32d152ceec59c65629ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924959"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>如何：在 managed 程式碼中管理多個執行緒
如果您的 managed VSPackage 延伸模組會呼叫非同步方法，或具有在 Visual Studio UI 執行緒以外的執行緒上執行的作業，您應該遵循下面所述的指導方針。 您可以讓 UI 執行緒保持回應，因為它不需要在另一個執行緒上等候工作完成。 您可以讓程式碼更有效率，因為您沒有額外的執行緒佔用堆疊空間，而且您可以讓它更可靠且更容易進行偵錯工具，因為您可以避免鎖死和沒有回應的程式碼。

 一般而言，您可以從 UI 執行緒切換至不同的執行緒，反之亦然。 當方法傳回時，目前的執行緒就是原始呼叫的執行緒。

> [!IMPORTANT]
> 下列指導方針會使用命名空間中的 Api <xref:Microsoft.VisualStudio.Threading> ，特別是 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> 類別。 這個命名空間中的 Api 是的新功能 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] 。 您可以從屬性取得的實例 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory` 。

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>從 UI 執行緒切換至背景執行緒

1. 如果您是在 UI 執行緒上，而且想要在背景執行緒上執行非同步工作，請使用 `Task.Run()` ：

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. 如果您是在 UI 執行緒上，而且想要在背景執行緒上執行工作時同步封鎖，請使用內的 <xref:System.Threading.Tasks.TaskScheduler> 屬性 `TaskScheduler.Default` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> ：

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>從背景執行緒切換至 UI 執行緒

1. 如果您是在背景執行緒上，並且想要在 UI 執行緒上執行某些動作，請使用 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> ：

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     您可以使用 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 方法切換至 UI 執行緒。 這個方法會將訊息張貼至 UI 執行緒，並接續目前的非同步方法，也會與執行緒架構的其餘部分進行通訊，以設定正確的優先順序並避免鎖死。

     如果您的背景執行緒方法不是非同步，而且您無法使其變成非同步，您仍然可以使用此 `await` 語法來切換至 UI 執行緒，方法是將您的工作包裝 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> 在中，如此範例所示：

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
