---
title: 如何:在託管代碼中管理多個線程 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceaa0af4f57fe374cf9cf4b2dd8b4f40af74a852
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702786"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>如何:在託管代碼中管理多個線程
如果您有一個託管 VSPackage 擴展呼叫非同步方法,或是具有在 Visual Studio UI 線程以外的線程上執行的操作,則應遵循下面給出的準則。 您可以保持 UI 線程的回應速度,因為它不需要等待另一個線程的工作完成。 您可以提高代碼的效率,因為您沒有佔用堆疊空間的額外線程,並且您可以使其更可靠且更易於調試,因為可以避免死鎖和掛起。

 通常,可以從 UI 線程切換到其他線程,反之亦然。 當方法返回時,當前線程是最初調用它的線程。

> [!IMPORTANT]
> 以下準則在<xref:Microsoft.VisualStudio.Threading>命名空間中使用 API,特別是<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>類。 此命名空間中的 API[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]在 中是新的。 可以從<xref:Microsoft.VisualStudio.Shell.ThreadHelper>`ThreadHelper.JoinableTaskFactory`屬性獲取<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>的實例。

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>從 UI 線程切換到背景線程

1. 如果位於 UI 執行緒上,並且想要在後台線執行非同步工作,請使用`Task.Run()`:

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. 如果位於 UI 線程上,並且希望在對後台線程執行工作時同步阻止,<xref:System.Threading.Tasks.TaskScheduler>`TaskScheduler.Default`<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>請使用

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>從背景執行緒切換到 UI 線程

1. 如果您位於後台線程上,並且想在 UI 執行時執行某些作業,請使用<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     可以使用方法<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>切換到 UI 線程。 此方法將消息發佈到 UI 線程,並延續當前非同步方法,並與線程框架的其餘部分通信,以設置正確的優先順序並避免死鎖。

     如果後台線程方法不是非同步的,並且無法使其成為非同步,則仍可以使用`await`語法透過包裝<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>工作切換到 UI 線程,如以下範例所示:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
