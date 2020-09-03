---
title: 如何：在背景中使用 AsyncPackage 載入 Vspackage |Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: f59838913ed3f9bc6679336393f6db9181291e3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204021"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>如何︰在背景中使用 AsyncPackage 載入 VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

載入和初始化 VS 封裝可能會導致磁片 i/o。 如果 UI 執行緒上發生這類 i/o，則可能會導致回應性問題。 為了解決這個情況，Visual Studio 2015 引進了  <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 可在背景執行緒上載入封裝的類別。  
  
## <a name="creating-an-asyncpackage"></a>建立 AsyncPackage  
 您可以從建立 VSIX 專案 (的 [檔案] **/[新增]/[專案]/[Visual c #/擴充性/VSIX 專案** ]) ，然後將 VSPackage 新增至專案 (以滑鼠右鍵按一下專案，然後新增 **/新增專案/c # 專案/擴充性/Visual Studio 套件**) 。 然後，您可以建立服務，並將這些服務新增至您的套件。  
  
1. 從衍生封裝 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 。  
  
2. 如果您要提供的服務，其查詢可能會導致您的封裝載入：  
  
    若要 Visual Studio 您的封裝可以安全地進行背景載入，以及加入宣告這種行為，您 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 應該在屬性函式中將 **AllowsBackgroundLoading** 屬性設定為 true。  
  
   ```csharp  
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
   ```  
  
    若要 Visual Studio 可以安全地在背景執行緒上具現化您的服務，您應該在函式 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> 中將屬性設為 true <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 。  
  
   ```csharp  
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
   ```  
  
3. 如果您是透過 UI 內容載入，則應該為指定 **PackageAutoLoadFlags BackgroundLoad** ，或針對 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 以套件自動載入專案的值寫入的旗標中，指定值 (0x2) 。  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
   ```  
  
4. 如果您有要執行的非同步初始化工作，則應該覆寫 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> 。 移除 VSIX 範本所提供的 **Initialize ( # B1 ** 方法。  (**AsyncPackage**中的**Initialize ( # B2**方法是 sealed) 。 您可以使用任何方法， <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> 將非同步服務新增至您的封裝。  
  
    注意：若要 ** ( # B1 呼叫base.InitializeAsync **，您可以將原始程式碼變更為：  
  
   ```csharp  
   await base.InitializeAsync(cancellationToken, progress);  
   ```  
  
5. 您必須小心不要讓 Rpc (從您的非同步初始化程式碼) 移除程序呼叫， (在 **InitializeAsync**) 中。 這些可能會在您 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 直接或間接呼叫時發生。  需要同步載入時，UI 執行緒將會封鎖使用 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> 。 預設的封鎖模型會停用 Rpc。 這表示，如果您嘗試從非同步工作使用 RPC，當 UI 執行緒本身等候您的封裝載入時，您將會鎖死。 一般替代方式是在需要時，使用類似 Joinable 的工作 **Factory** <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 或其他未使用 RPC 的機制，將您的程式碼封送處理至 UI 執行緒。  請勿使用 **ThreadHelper** ，或通常會封鎖等候進入 UI 執行緒的呼叫執行緒。  
  
    注意：您應該避免在**InitializeAsync**方法中使用**GetService**或**QueryService** 。 如果您必須使用這些參數，您必須先切換至 UI 執行緒。 替代方法是將 <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> **AsyncPackage** 轉換為，以從您的 (使用 <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> 。 )   
  
   C #：建立 AsyncPackage：  
  
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
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>將現有的 VSPackage 轉換為 AsyncPackage  
 大部分的工作都與建立新的 **AsyncPackage**相同。 您必須遵循上述的步驟1到5。 您也需要特別注意下列事項：  
  
1. 請記得移除套件中的 **初始化** 覆寫。  
  
2. 避免鎖死：您的程式碼中可能會有隱藏的 Rpc，現在會在背景執行緒上發生。 您必須確保在進行 RPC (（例如 **GetService**) ）時，您需要 (1) 切換至主執行緒或 (2) 使用 API 的非同步版本（如果有的話） (例如 **GetServiceAsync**) 。  
  
3. 請勿太頻繁地線上程之間切換。 請嘗試將背景執行緒中可能發生的工作當地語系化。 這會減少載入時間。  
  
## <a name="querying-services-from-asyncpackage"></a>從 AsyncPackage 查詢服務  
 **AsyncPackage**可能會或可能不會以非同步方式載入，視呼叫端而定。 例如，  
  
- 如果名為 **GetService** 或 **QueryService** 的呼叫端 (同步 api) 或  
  
- 如果呼叫者呼叫 **ivsshell 出現：： LoadPackage** (或 **IVsShell5：： LoadPackageWithCoNtext**) 或  
  
- 使用者介面內容會觸發負載，但是您未指定 UI 內容機制可以用非同步方式載入  
  
  然後，您的套件會以同步方式載入。  
  
  請注意，您的套件仍有機會 (在其非同步初始化階段中，) 要在 UI 執行緒中執行工作，但 UI 執行緒將會封鎖該工作的完成。 如果呼叫者使用 **IAsyncServiceProvider** 以非同步方式查詢您的服務，則您的載入和初始化將會以非同步方式完成，前提是它們不會立即封鎖產生的工作物件。  
  
  C #：如何以非同步方式查詢服務：  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
