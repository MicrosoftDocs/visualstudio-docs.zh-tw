---
title: 如何：提供非同步 Visual Studio 服務 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c34995a49a785061c67f1324c9c9cd5b5316178
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633113"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>如何：提供非同步 Visual Studio 服務
如果您想要取得服務而不封鎖 UI 執行緒，您應該建立異步服務，並在背景執行緒上載入封裝。 基於此目的，您可以使用 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 而不是 <xref:Microsoft.VisualStudio.Shell.Package>，並使用非同步封裝的特殊非同步方法來新增服務。

 如需提供同步 Visual Studio 服務的相關資訊，請參閱[如何：提供服務](../extensibility/how-to-provide-a-service.md)。

## <a name="implement-an-asynchronous-service"></a>執行非同步服務

1. 建立 VSIX**專案（檔案** > **新**的  > **專案** > **Visual C#**   > **Extensiblity** 0**VSIX 專案**）。 將專案命名為**TestAsync**。

2. 將 VSPackage 新增至專案。 在 [**方案總管**中選取專案節點，然後按一下 [**加入** > **新專案**]  >  [ **C# Visual 專案** **]  >  擴充**性  > **Visual Studio 套件**]。 將此檔案命名為*TestAsyncPackage.cs*。

3. 在*TestAsyncPackage.cs*中，將封裝變更為繼承自 `AsyncPackage`，而不是 `Package`：

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. 若要執行服務，您需要建立三種類型：

    - 識別服務的介面。 其中有許多介面是空的，也就是說，它們沒有方法，因為它們只用于查詢服務。

    - 描述服務介面的介面。 此介面包含要執行的方法。

    - 同時執行服務和服務介面的類別。

5. 下列範例顯示三個型別的非常基本實作為。 服務類別的函式必須設定服務提供者。 在此範例中，我們只會將服務新增至封裝程式碼檔案。

6. 將下列 using 指示詞新增至封裝檔案：

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. 以下是非同步服務的執行。 請注意，您必須在此函式中設定非同步服務提供者，而不是同步服務提供者：

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>註冊服務
 若要註冊服務，請將 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 新增至提供服務的封裝中。 不同于註冊同步服務，您必須確定封裝和服務都支援非同步載入：

- 您必須將**AllowsBackgroundLoading = true**欄位新增至 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>，以確保可以非同步初始化封裝，以取得 PackageRegistrationAttribute 的詳細資訊，請參閱[註冊及取消註冊 vspackage](../extensibility/registering-and-unregistering-vspackages.md)。

- 您必須將**IsAsyncQueryable = true**欄位加入至 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>，以確保服務實例可以非同步初始化。

  以下是具有非同步服務註冊 `AsyncPackage` 的範例：

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>新增服務

1. 在*TestAsyncPackage.cs*中，移除 `Initialize()` 方法，並覆寫 `InitializeAsync()` 方法。 新增服務，並新增回呼方法來建立服務。 以下是非同步初始化運算式新增服務的範例：

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```

2. 新增對 VisualStudio 的參考。 *DesignTime .dll*中的。

3. 將回呼方法實作為可建立及傳回服務的非同步方法。

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>使用服務
 現在您可以取得服務，並使用其方法。

1. 這會在初始化運算式中顯示，但您可以在任何想要使用服務的地方取得服務。

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     別忘了將 `userpath` 變更為在您的電腦上有意義的檔案名和路徑！

2. 建立並執行程式碼。 當 Visual Studio 的實驗實例出現時，請開啟方案。 這會導致 `AsyncPackage` autoload。 當初始化運算式執行時，您應該會在指定的位置中找到檔案。

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>在命令處理常式中使用非同步服務
 以下是如何在功能表命令中使用非同步服務的範例。 您可以使用此處所示的程式，在其他非非同步方法中使用此服務。

1. 將功能表命令加入至您的專案。 （在 **方案總管**中，選取專案節點，按一下滑鼠右鍵，然後選取 **新增  >  新專案** ** >  擴充**性  > **自訂命令**）。將命令檔命名為*TestAsyncCommand.cs*。

2. 自訂命令範本會將 `Initialize()` 方法重新加入至*TestAsyncPackage.cs*檔案，以便初始化命令。 在 `Initialize()` 方法中，複製初始化命令的程式列。 內容應該看起來如下：

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     將這一行移至*AsyncPackageForService.cs*檔案中的 `InitializeAsync()` 方法。 因為這是在非同步初始化中，所以您必須先切換到主執行緒，再使用 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 初始化命令。 它現在看起來應該像這樣：

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. 刪除 `Initialize()` 方法。

4. 在*TestAsyncCommand.cs*檔案中，尋找 `MenuItemCallback()` 方法。 刪除方法的主體。

5. 新增 using 指示詞：

    ```csharp
    using System.IO;
    ```

6. 新增名為 `UseTextWriterAsync()` 的非同步方法，以取得服務並使用其方法：

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. 從 `MenuItemCallback()` 方法呼叫這個方法：

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. 建置方案並開始偵錯。 當 Visual Studio 的實驗實例出現時，請移至 [**工具**] 功能表，然後尋找 [叫用**TestAsyncCommand** ] 功能表項目。 當您按一下它時，TextWriterService 會寫入您指定的檔案。 （您不需要開啟方案，因為叫用命令也會導致封裝載入。）

## <a name="see-also"></a>請參閱
- [使用並提供服務](../extensibility/using-and-providing-services.md)
