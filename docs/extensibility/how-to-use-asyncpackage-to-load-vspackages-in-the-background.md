---
title: 如何:使用異步包在後台載入 VS 包 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 77690a1947f82f97c4aa12809a80ea61335d216d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710622"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>如何:使用非同步包在後台載入 VS 套件
載入和初始化 VS 包可能會導致磁碟 I/O。 如果此類I/O發生在UI線程上,則可能導致回應問題。 為了解決這個問題,Visual Studio 2015<xref:Microsoft.VisualStudio.Shell.AsyncPackage>引入了允許在後台線程上載入包的類。

## <a name="create-an-asyncpackage"></a>建立非同步
 您可以開始建立 VSIX 專案**Project** > (**檔案** > **新專案** > **視覺化 C_** > 延伸**VSIX** > **專案**) 和向專案添加 VS 套件 (右鍵按一下專案,**新增新** > **專案** > **C# 專案** > **)擴展可視化** > **工作室套件**)。 然後,您可以創建服務並將這些服務添加到包中。

1. 從<xref:Microsoft.VisualStudio.Shell.AsyncPackage>派生包。

2. 如果您提供的服務查詢可能會導致載入您的套件:

    要向 Visual Studio 指示您的包對後台載入是安全的,並選擇加入<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>此行為, 您應該在屬性建構函數中將 **「允許後台載入**」屬性設置為 true。

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    要向 Visual Studio 指示在後台線程上實例化服務是安全的,應在構造<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A><xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>函數中 將屬性設置為 true。

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. 如果透過 UI 上下文載入,則<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>應將或值 (0x2) 的 **「包自動載入 Flags」** 指定到作為包自動載入條目的值編寫的標誌中的後台載入。

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. 如果要執行非同步初始化工作,則應重寫<xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>。 刪除`Initialize()`VSIX 範本提供的方法。 (`Initialize()`**非同步包**中的方法是密封的)。 可以使用任何<xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A>方法向包添加非同步服務。

    註:`base.InitializeAsync()`要 呼叫 ,您可以將原始碼變更為:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. 您必須注意不要從非同步初始化代碼(**初始化 Async**中)進行 RPC(遠端過程呼叫)。 當您直接或間接調用<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>時,可能會發生這些情況。  當需要同步載入時,UI 線程將<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>使用阻止。 默認阻止模型禁用 RPC。 這意味著,如果您嘗試使用來自非同步任務的 RPC,如果 UI 線程本身正在等待載入套件,則將死鎖。 通常的替代方法是,如果需要,請使用可**加入任務工廠**<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>或其他不使用 RPC 的機制將代碼封送到 UI 線程。  不要使用**ThreadHelper.generic.Invoke 或**通常阻止等待到達 UI 線程的調用線程。

    注意:您應該避免在方法`InitializeAsync`中使用**取得服務**或**查詢服務**。 如果必須使用這些線程,則需要首先切換到 UI 線程。 另一種方法是從<xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A>**Async 套件**中使用(將其強制<xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>轉換到 。)

   C#: 建立非同步套件:

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

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>將現有 VS 套件轉換為非同步套件
 大多數工作與創建新的**Async 包**相同。 按照上面的步驟 1 到 5。 您還需要格外小心以下建議:

1. 請記住刪除套件中的`Initialize`重寫。

2. 避免死鎖:代碼中可能有隱藏的 RPC。 現在發生在後台線程上。 請確保,如果要進行 RPC(例如 **,GetService),** 則需要 (1) 切換到主線程,或者 (2) 如果存在 API 的異步版本(例如 **,Get ServiceAsync)。**

3. 請勿在線程之間切換過於頻繁。 嘗試當地語系化在後台線程中可能發生的工作,以減少載入時間。

## <a name="querying-services-from-asyncpackage"></a>從非同步查詢服務
 **Async 包**可能載入,也可能不同步載入,具體取決於調用方。 例如，

- 如果呼叫者通話**取得服務**或**查詢服務**(同時使用同步 API)或

- 如果呼叫者來**叫 IVsShell:載入套件**(或**IVsShell5::loadPackage 與上下文**) 或

- 負載由 UI 上下文觸發,但您沒有指定 UI 上下文機制可以非同步載入您

  然後,您的包將同步載入。

  包仍然有機會(處於異步初始化階段)從 UI 線程執行工作,儘管 UI 線程將被阻止完成該工作。 如果調用方使用**IAsync ServiceProvider**對服務進行非同步查詢,則載入和初始化將以異步方式完成,前提是它們不會立即阻止生成的任務物件。

  C#:如何非同步查詢服務:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
