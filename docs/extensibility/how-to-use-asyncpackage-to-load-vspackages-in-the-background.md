---
title: 如何：在背景中使用 AsyncPackage 載入 Vspackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 7727d53c84ab876fe6616c8ec5d438033216481e
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905598"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>如何：在背景中使用 AsyncPackage 載入 Vspackage
載入和初始化 VS 封裝可能會導致磁片 i/o。 如果在 UI 執行緒上發生這類 i/o，可能會導致回應性問題。 為了解決這個情況，Visual Studio 2015 引進了 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 可在背景執行緒上載入封裝的類別。

## <a name="create-an-asyncpackage"></a>建立 AsyncPackage
 您可以從建立 VSIX 專案（[檔案 **] [**  >  **新**  >  **專案**] [  >  **Visual c #** 擴充性  >  **Extensibility**  >  **VSIX 專案**]）開始，然後將 VSPackage 加入至專案（以滑鼠右鍵按一下專案，然後**加入**  >  **新專案**  >  **c # 專案**擴充性  >  **Extensibility**  >  **Visual Studio 封裝**）。 接著，您可以建立服務，並將這些服務新增至您的套件。

1. 從衍生封裝 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 。

2. 如果您提供的服務可能會導致您的封裝載入：

    若要 Visual Studio 您的封裝可安全地進行背景載入並加入宣告此行為，您 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 應該在屬性的函式中將**AllowsBackgroundLoading**屬性設定為 true。

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    若要 Visual Studio 在背景執行緒上具現化您的服務是安全的，您應該 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> 在此函式中將屬性設定為 true <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 。

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. 如果您是透過 UI 內容載入，則應該將或值（0x2）指定為**PackageAutoLoadFlags** ，並 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 寫入為封裝自動載入專案值的旗標。

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. 如果您有要執行的非同步初始化工作，您應該覆寫 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> 。 移除 `Initialize()` VSIX 範本所提供的方法。 （ `Initialize()` **AsyncPackage**中的方法是密封的）。 您可以使用任何方法， <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> 將非同步服務新增至您的封裝。

    注意：若要呼叫 `base.InitializeAsync()` ，您可以將原始程式碼變更為：

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. 您必須小心不要從非同步初始化程式碼（在**InitializeAsync**中）執行 Rpc （遠端程序呼叫）。 當您直接或間接呼叫時，就會發生這些問題 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 。  需要同步處理負載時，UI 執行緒會使用封鎖 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> 。 預設封鎖模式會停用 Rpc。 這表示如果您嘗試使用非同步工作中的 RPC，而 UI 執行緒本身正在等候您的封裝載入，就會鎖死。 一般的替代方法是使用像是**Joinable 工作 Factory**的 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 或其他不使用 RPC 的其他機制，視需要將程式碼封送處理至 UI 執行緒。  請勿使用**ThreadHelper** ，或通常會封鎖等候進入 UI 執行緒的呼叫執行緒。

    注意：您應該避免在您的方法中使用**GetService**或**QueryService** `InitializeAsync` 。 如果您必須使用這些參數，您必須先切換至 UI 執行緒。 替代方法是 <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> 從您的**AsyncPackage**使用（將它轉換為 <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> ）。

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

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>將現有的 VSPackage 轉換成 AsyncPackage
 大部分的工作都與建立新的**AsyncPackage**相同。 遵循上面的步驟1到5。 您也需要特別注意下列建議：

1. 請記得移除 `Initialize` 您在封裝中的覆寫。

2. 避免鎖死：您的程式碼中可能有隱藏的 Rpc。 現在會在背景執行緒上發生。 如果您要建立 RPC （例如**GetService**），您需要（1）切換到主要執行緒，或（2）使用 API 的非同步版本（如果有的話）（例如**GetServiceAsync**）。

3. 請勿經常線上程之間切換。 嘗試將背景執行緒中可能發生的工作當地語系化，以縮短載入時間。

## <a name="querying-services-from-asyncpackage"></a>從 AsyncPackage 查詢服務
 **AsyncPackage**不一定會以非同步方式載入，視呼叫者而定。 例如，

- 如果呼叫端稱為**GetService**或**QueryService** （兩者都是同步 api）或

- 如果呼叫端稱為**ivsshell 出現：： LoadPackage** （或**IVsShell5：： LoadPackageWithCoNtext**）或

- 負載是由 UI 內容觸發，但是您未指定 UI 內容機制可以非同步載入

  然後，您的套件會以同步方式載入。

  您的套件仍有機會（在其非同步初始化階段）來執行 UI 執行緒的工作，不過 UI 執行緒將會被封鎖以完成該工作。 如果呼叫端使用**IAsyncServiceProvider**以非同步方式查詢您的服務，則您的負載和初始化會以非同步方式執行，假設它們不會立即封鎖產生的 task 物件。

  C #：如何以非同步方式查詢服務：

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
