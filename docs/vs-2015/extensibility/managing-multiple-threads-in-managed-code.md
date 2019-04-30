---
title: 管理多個執行緒在 Managed 程式碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e7198623283fa3ef9c82d6a39a1f7c1db6c760c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433039"
---
# <a name="managing-multiple-threads-in-managed-code"></a>在受控碼中管理多個執行緒
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您有受管理的 VSPackage 擴充功能呼叫非同步方法或在 Visual Studio UI 執行緒以外之執行緒執行的作業，您應該遵循以下的指導方針。 您可以讓 UI 執行緒有回應，因為它不需要等候工作完成的另一個執行緒上。 您可以讓您的程式碼更有效率，因為您不需要額外的執行緒所佔用的堆疊空間，並可以先讓更可靠且更輕鬆地偵錯，因為您避免死結和懸置。  
  
 一般情況下，您可以從 UI 執行緒切換至不同的執行緒，或反之亦然。 方法傳回時，目前的執行緒就會是從其中所初次呼叫的執行緒。  
  
> [!IMPORTANT]
> 下列指導方針使用中的 Api<xref:Microsoft.VisualStudio.Threading>命名空間，特別是，<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>類別。 此命名空間中的 Api 是中的新[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]。 您可以取得的執行個體<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>從<xref:Microsoft.VisualStudio.Shell.ThreadHelper>屬性`ThreadHelper.JoinableTaskFactory`。  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>從 UI 執行緒切換到背景執行緒  
  
1. 如果您是在 UI 執行緒上，而且您想要在背景執行緒上的非同步工作，請使用 Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2. 如果您是在 UI 執行緒上，而且您想要以同步方式封鎖，您會在背景執行緒，使用在執行工作時<xref:System.Threading.Tasks.TaskScheduler>屬性`TaskScheduler.Default`內<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>從背景執行緒切換至 UI 執行緒  
  
1. 如果您是在背景執行緒上，而且您想要使用的 UI 執行緒上進行一些動作<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
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
