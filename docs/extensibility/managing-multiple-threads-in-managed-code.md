---
title: 如何：在 Managed 程式碼中管理多個執行緒 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe5cef9f7aebcbfc93ffd057a109647e45b5967
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387066"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>如何：在 managed 程式碼中管理多個執行緒
如果您的 managed VSPackage 延伸模組會呼叫非同步方法，或具有在 Visual Studio UI 執行緒以外的執行緒上執行的作業，您應該遵循下面所提供的指導方針。 您可以讓 UI 執行緒保持回應，因為它不需要等候另一個執行緒上的工作完成。 您可以讓程式碼更有效率，因為您沒有佔用堆疊空間的額外線程，而且您可以讓它更可靠且更容易進行調試，因為您可以避免鎖死和沒有回應的程式碼。

 一般來說，您可以從 UI 執行緒切換到不同的執行緒，反之亦然。 當此方法傳回時，目前的執行緒就是原本呼叫它的執行緒。

> [!IMPORTANT]
> 下列指導方針會使用命名空間中的 Api <xref:Microsoft.VisualStudio.Threading> ，特別是 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> 類別。 這個命名空間中的 Api 是的新功能 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] 。 您可以從屬性取得的實例 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory` 。

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>從 UI 執行緒切換至背景執行緒

1. 如果您是在 UI 執行緒上，而您想要在背景執行緒上執行非同步工作，請使用 `Task.Run()` ：

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. 如果您在 UI 執行緒上，而且想要在背景執行緒上執行工作時同步封鎖，請在 <xref:System.Threading.Tasks.TaskScheduler> 內部使用屬性 `TaskScheduler.Default` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> ：

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

1. 如果您是在背景執行緒上，而您想要在 UI 執行緒上執行某些動作，請使用 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> ：

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     您可以使用 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 方法來切換至 UI 執行緒。 這個方法會使用目前非同步方法的接續，將訊息張貼至 UI 執行緒，也會與執行緒架構的其餘部分通訊，以設定正確的優先順序並避免鎖死。

     如果您的背景執行緒方法不是非同步，而且您無法將它設為非同步，您仍然可以使用此語法，藉 `await` 由包裝您的工作來切換至 UI 執行緒 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> ，如下列範例所示：

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
