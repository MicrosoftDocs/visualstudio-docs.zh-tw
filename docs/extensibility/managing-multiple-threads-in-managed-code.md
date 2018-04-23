---
title: 如何： 管理多個執行緒在 Managed 程式碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c0888a0f65f36d624deffac60ceee032d3f3d13a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>如何： 管理多個執行緒在 Managed 程式碼
如果您有受管理的 VSPackage 擴充功能呼叫非同步方法或在 Visual Studio UI 執行緒以外的執行緒執行的作業，您應該遵循下面提供的指導方針。 您可以將 UI 執行緒能繼續回應，因為它不需要等候另一個執行緒完成的工作。 您可以讓您的程式碼更有效率，因為您不需要額外的執行緒所佔用的堆疊空間，您還可以讓更可靠且更容易偵錯，因為您避免死結和當機。  
  
 一般情況下，您可以從 UI 執行緒切換至不同的執行緒，反之亦然。 方法傳回時，目前的執行緒是從中所初次呼叫的執行緒。  
  
> [!IMPORTANT]
>  下列指導方針的使用中的 Api<xref:Microsoft.VisualStudio.Threading>命名空間，特別是，<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>類別。 此命名空間中的 Api 中新增了[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]。 您可以取得的執行個體<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>從<xref:Microsoft.VisualStudio.Shell.ThreadHelper>屬性`ThreadHelper.JoinableTaskFactory`。  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>從 UI 執行緒切換到背景執行緒  
  
1.  如果您是在 UI 執行緒上，而且您想要在背景執行緒上的非同步工作，使用 Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  如果您是在 UI 執行緒上，而且您想要以同步方式封鎖您在背景執行緒、 使用中執行工作時<xref:System.Threading.Tasks.TaskScheduler>屬性`TaskScheduler.Default`內<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>從背景執行緒切換到 UI 執行緒  
  
1.  如果您是在背景執行緒，且您想要執行 UI 執行緒上、 使用的一些動作<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     您可以使用<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>切換到 UI 執行緒的方法。 此方法會公佈訊息至 UI 執行緒與目前的非同步方法的接續，而且也與其他執行緒的架構，以便設定正確的優先順序，並且避免發生死結的通訊。  
  
     如果您的背景執行緒方法不是非同步，且無法進行非同步，您仍然可以使用`await`語法來包裝您的工作來切換至 UI 執行緒<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>，如這個範例所示：  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```