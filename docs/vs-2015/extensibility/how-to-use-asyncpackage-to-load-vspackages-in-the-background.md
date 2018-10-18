---
title: 如何： 使用 AsyncPackage 載入 Vspackage 在背景中的 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: 95a9efd6976f57b2466b82d9cbe4bec9e5bf2545
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262595"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>如何： 使用 AsyncPackage 載入 Vspackage 在背景中
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

正在載入和初始化的 VS 套件可能會導致磁碟 I/O。 如果這類的 I/O 會發生在 UI 執行緒上，它可能會導致回應性問題。 為了解決這個問題，Visual Studio 2015 導入了<xref:Microsoft.VisualStudio.Shell.AsyncPackage>類別，可讓背景執行緒上的封裝載入。  
  
## <a name="creating-an-asyncpackage"></a>建立 AsyncPackage  
 您可以開始建立 VSIX 專案 (**檔案 / 新增 / 專案 / Visual C# / 擴充性 / VSIX 專案**) 和專案中加入 VSPackage (以滑鼠右鍵按一下專案並**新增/新增項目 / C# 項目/擴充性 /visualStudio 封裝**)。 您接著可以建立您的服務，並將這些服務新增至您的套件。  
  
1.  衍生中的套件<xref:Microsoft.VisualStudio.Shell.AsyncPackage>。  
  
2.  如果您要提供其查詢可能會導致您的套件以載入的服務：  
  
     表示 Visual studio 封裝是安全的背景載入，以及選擇加入此行為，您<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>應該設定**AllowsBackgroundLoading**屬性設為 true，在屬性建構函式。  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     若要指出 Visual studio 會安全地具現化您的服務在背景執行緒上，您應該設定<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A>屬性設為 true，在<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>建構函式。  
  
    ```csharp  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  如果您透過 UI 內容載入，則您應該指定**PackageAutoLoadFlags.BackgroundLoad**如<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>或旗標的值 (0x2) 寫入做為您的封裝自動載入項目的值。  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  如果您有要執行的非同步初始化工作，您應該覆寫<xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>。 移除**initialize （)** VSIX 範本所提供的方法。 ( **Initialize （)** 方法中的**AsyncPackage**密封格式)。 您可以使用任一<xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A>方法，以非同步的服務加入您的套件。  
  
     注意： 若要呼叫**基底。InitializeAsync()**，您可以變更您的程式碼，以：  
  
    ```csharp  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  您必須小心進行 Rpc （移除程序呼叫） 從您的非同步初始化程式碼 (在**InitializeAsync**)。 這些可能是當您呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>直接或間接。  需要同步處理的負載時，UI 執行緒將會封鎖使用<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>。 預設封鎖模式中，會停用 Rpc。 這表示，如果您嘗試使用 RPC 從非同步工作時，您會鎖死 UI 執行緒是否正在等候您要載入的封裝本身。 一般的替代做法是您在 UI 執行緒的程式碼封送處理，如有需要使用類似**可聯結工作 Factory**的<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>或一些其他不會使用 RPC 的機制。  請勿使用**ThreadHelper.Generic.Invoke**或通常會封鎖呼叫執行緒等候取得至 UI 執行緒。  
  
     注意： 您應該避免使用**GetService**或是**QueryService**中您**InitializeAsync**方法。 如果您有使用這些，您必須先切換至 UI 執行緒。 替代方法是使用<xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A>從您**AsyncPackage** (藉由將它轉型<xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>。)  
  
 C#： 建立 AsyncPackage:  
  
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
 大部分的工作是建立新的相同**AsyncPackage**。 您必須遵循步驟 1 至 5 上述。 您還需要採取額外注意下列：  
  
1.  請記得去除**初始化**覆寫，您必須在您的套件。  
  
2.  避免死結 （deadlock）： 可能會隱藏在程式碼現在會發生在背景執行緒的 Rpc。 您必須確保，如果您正在使用 RPC (例如**GetService**)，您必須 (1) 切換至主執行緒，或 （2） 使用非同步版本的 API，如果有一個存在 (例如**GetServiceAsync**)。  
  
3.  請勿過於頻繁執行緒之間進行切換。 嘗試將當地語系化可能發生在背景執行緒中的工作。 這可減少載入時間。  
  
## <a name="querying-services-from-asyncpackage"></a>從 AsyncPackage 查詢服務  
 **AsyncPackage**可能會或可能不取決於呼叫端會以非同步方式載入。 比方說，  
  
-   如果呼叫端呼叫**GetService**或是**QueryService** (這兩個同步 Api) 或  
  
-   如果呼叫端呼叫**IVsShell::LoadPackage** (或**IVsShell5::LoadPackageWithContext**) 或  
  
-   UI 內容，就會觸發負載，但您未指定 UI 內容機制，您可以以非同步方式載入  
  
 然後會以同步方式載入封裝。  
  
 請注意，您的套件仍有機會 （在其非同步初始化階段） 來關閉 UI 執行緒執行工作雖然會封鎖 UI 執行緒，該工作完成。 如果呼叫端必須使用**IAsyncServiceProvider**來以非同步方式查詢您的服務，然後您的載入和初始化時，必須以非同步方式假設它們不會立即產生的工作物件上封鎖。  
  
 C# 中： 如何以非同步方式查詢服務：  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```

