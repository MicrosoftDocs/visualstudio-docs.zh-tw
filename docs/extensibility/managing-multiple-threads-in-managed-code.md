---
title: 如何： 管理中的多個執行緒的 Managed 程式碼 |Microsoft Docs
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
ms.openlocfilehash: e597f46160221b19fe678bbf665782d3f3f5a249
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636421"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>如何： 管理 managed 程式碼中的多個執行緒
如果您有受管理的 VSPackage 擴充功能呼叫非同步方法或在 Visual Studio UI 執行緒以外之執行緒執行的作業，您應該遵循以下的指導方針。 您可以讓 UI 執行緒有回應，因為它不需要等候工作完成的另一個執行緒上。 您可以讓您的程式碼更有效率，因為您不需要額外的執行緒所佔用的堆疊空間，並可以先讓更可靠且更輕鬆地偵錯，因為您避免死結和懸置。  
  
 一般情況下，您可以從 UI 執行緒切換至不同的執行緒，或反之亦然。 方法傳回時，目前的執行緒就會是從其中所初次呼叫的執行緒。  
  
> [!IMPORTANT]
>  下列指導方針使用中的 Api<xref:Microsoft.VisualStudio.Threading>命名空間，特別是，<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>類別。 此命名空間中的 Api 是中的新[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]。 您可以取得的執行個體<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>從<xref:Microsoft.VisualStudio.Shell.ThreadHelper>屬性`ThreadHelper.JoinableTaskFactory`。  
  
## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>從 UI 執行緒切換到背景執行緒  
  
1.  如果您是在 UI 執行緒上，而且您想要在背景執行緒使用的非同步工作`Task.Run()`:  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  如果您是在 UI 執行緒上，而且您想要以同步方式封鎖，您會在背景執行緒，使用在執行工作時<xref:System.Threading.Tasks.TaskScheduler>屬性`TaskScheduler.Default`內<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
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
  
1.  如果您是在背景執行緒上，而且您想要使用的 UI 執行緒上進行一些動作<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     您可以使用<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>，切換至 UI 執行緒的方法。 這個方法會將訊息張貼至 UI 執行緒與目前的非同步方法中，接續，而且也與執行緒的架構，來設定正確的優先順序，並避免死結的其餘部分通訊。  
  
     如果您的背景執行緒方法不是非同步，而且無法進行非同步，您仍然可以使用`await`語法，來包裝您的工作切換至 UI 執行緒<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>，如這個範例所示：  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```