---
title: "如何： 載入 Vspackage 在背景中的使用 AsyncPackage |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
ms.openlocfilehash: 8adc348553ba613898117f10ccd21a6e5cd02ab8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>如何： 使用 AsyncPackage 載入 Vspackage 在背景中
正在載入和初始化 VS 套件可能會導致磁碟 I/O。 如果這類 I/O 情況發生在 UI 執行緒上，它可能會導致回應性問題。 為了解決這個問題，Visual Studio 2015 導入了<xref:Microsoft.VisualStudio.Shell.AsyncPackage>類別，可讓封裝載入背景執行緒上的。  
  
## <a name="creating-an-asyncpackage"></a>建立 AsyncPackage  
 您可以藉由建立 VSIX 專案啟動 (**檔案 / 新增 / 專案 / Visual C# / 擴充性 / VSIX 專案**) 並加入 VSPackage 專案 (專案上按一下滑鼠右鍵和**新增/新增項目 / C# 項目/擴充性 /visualStudio Package**)。 您可以建立您的服務，並將這些服務加入至您的封裝。  
  
1.  衍生中的封裝<xref:Microsoft.VisualStudio.Shell.AsyncPackage>。  
  
2.  如果您要提供的服務的查詢可能會導致您要載入的封裝：  
  
     若要表示 Visual Studio 封裝是安全的背景載入並選擇此行為，您<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>應該設定**AllowsBackgroundLoading**屬性設定為 true，在屬性建構函式。  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     若要指出 Visual Studio 來具現化您的服務在背景執行緒安全，您應該設定<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A>屬性設定為 true，在<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>建構函式。  
  
    ```csharp  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  如果您透過 UI 內容載入，則您應該指定**PackageAutoLoadFlags.BackgroundLoad**如<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>或旗標的值 (0x2) 寫入做為您的封裝自動載入項目的值。  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  如果您有要執行的非同步初始化工作，您應該覆寫<xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>。 移除**initialize （)** VSIX 範本所提供的方法。 ( **Initialize （)**方法中的**AsyncPackage**已密封)。 您可以使用任一<xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A>方法，以非同步的服務加入您的封裝。  
  
     注意： 若要呼叫**基底。InitializeAsync()**，您可以變更至您的原始程式碼：  
  
    ```csharp  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  您必須小心不要 Rpc （遠端程序呼叫） 從非同步的初始化程式碼 (在**InitializeAsync**)。 當您呼叫可能會發生這些<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>直接或間接。  需要同步處理的負載時，UI 執行緒會封鎖使用<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>。 預設封鎖模式會停用 Rpc。 這表示，如果您嘗試使用 RPC 從非同步工作，您將會發生死結，如果 UI 執行緒正在等候您要載入的封裝本身。 一般替代方式是視需要使用類似，封送處理程式碼 UI 執行緒**可加入工作 Factory**的<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>或其他一些機制，不會使用 RPC。  請勿使用**ThreadHelper.Generic.Invoke**或通常會封鎖呼叫執行緒等待取得 UI 執行緒。  
  
     注意： 您應該避免使用**GetService**或**QueryService**中您**InitializeAsync**方法。 如果您有使用中，您必須先切換至 UI 執行緒。 若要使用的替代方案是<xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A>從您**AsyncPackage** (透過將它轉型<xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>。)  
  
 C# 中： 建立 AsyncPackage:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>將現有的 VSPackage 轉換成 AsyncPackage  
 大部分的工作會建立新相同**AsyncPackage**。 您必須遵循步驟 1 到 5 上述。 您還需要採取額外注意下列：  
  
1.  請務必移除**初始化**您必須在封裝中的覆寫。  
  
2.  避免死結： 可能會隱藏您現在就可能發生在背景執行緒的程式碼中的 Rpc。 您必須確保，如果您要進行 RPC (例如**GetService**)，您需要切換至主執行緒 (1) 或 （2） 使用的 API，如果一個非同步版本存在 (例如**GetServiceAsync**)。  
  
3.  頻率太高執行緒之間切換。 若要當地語系化的工作可能會發生在背景執行緒中再試一次。 這會減少載入時間。  
  
## <a name="querying-services-from-asyncpackage"></a>從 AsyncPackage 查詢服務  
 **AsyncPackage**可能或可能不根據呼叫端會以非同步方式載入。 例如，  
  
-   如果呼叫端呼叫**GetService**或**QueryService** (這兩種同步的 Api) 或  
  
-   如果呼叫端呼叫**IVsShell::LoadPackage** (或**IVsShell5::LoadPackageWithContext**) 或  
  
-   UI 內容中，會觸發負載，但未指定 UI 內容機制可以非同步載入您  
  
 然後您的封裝將會以同步方式載入。  
  
 請注意，您的套件仍有機會 （在其非同步初始化階段） 來執行工作，關閉 UI 執行緒，雖然 UI 執行緒會封鎖該工作完成。 如果呼叫端使用**IAsyncServiceProvider**來以非同步方式查詢您的服務，然後您的載入和初始化都是以非同步方式假設才不會立即產生的工作物件上阻擋。  
  
 C# 中： 如何以非同步方式查詢服務：  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
  
