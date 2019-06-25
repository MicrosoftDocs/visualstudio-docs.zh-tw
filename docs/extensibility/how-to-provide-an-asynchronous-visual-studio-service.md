---
title: 作法：提供非同步的 Visual Studio 服務 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebba3ca9434d704fff25f3d3519748930db12aa7
ms.sourcegitcommit: 34807a6b6105ae7839adde8ff994c85182ad3aff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2019
ms.locfileid: "67342397"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>作法：提供非同步的 Visual Studio 服務
如果您想要取得服務，而不會封鎖 UI 執行緒，您應該建立非同步的服務，並在背景執行緒上的將封裝載入。 基於此目的，您可以使用<xref:Microsoft.VisualStudio.Shell.AsyncPackage>而非<xref:Microsoft.VisualStudio.Shell.Package>，然後以非同步的封裝特殊的非同步方法中加入服務。

 提供同步的 Visual Studio 服務的相關資訊，請參閱[How to:提供服務](../extensibility/how-to-provide-a-service.md)。

## <a name="implement-an-asynchronous-service"></a>實作非同步服務

1. 建立 VSIX 專案 (**檔案** > **新增** > **專案** > **Visual C#**  > **擴充性** > **VSIX 專案**)。 將專案命名為**TestAsync**。

2. 加入專案中的 VSPackage。 選取專案節點，在**方案總管**，按一下 **新增** > **新項目** > **Visual C# 項目**  > **擴充性** > **Visual Studio 套件**。 這個檔案命名*TestAsyncPackage.cs*。

3. 在  *TestAsyncPackage.cs*，變更為繼承封裝`AsyncPackage`而非`Package`:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. 若要實作服務，您需要建立三種類型：

    - 識別服務的介面。 許多這些介面是空的亦即，它們有沒有任何方法，它們只能用來查詢服務。

    - 描述服務介面的介面。 這個介面包含要實作的方法。

    - 實作服務和服務介面的類別。

5. 下列範例顯示三種類型的基本實作。 服務類別的建構函式必須設定服務提供者。 在此範例中，我們只是將封裝的程式碼檔案，以新增服務。

6. 新增下列 using 陳述式的封裝檔案：

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. 以下是非同步的服務實作。 請注意，您必須設定建構函式的非同步服務提供者，而不是同步的服務提供者：

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

            await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
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
 若要註冊的服務，將新增<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>提供服務的套件。 不同註冊同步服務，您必須確定封裝和服務支援非同步載入：

- 您必須新增**AllowsBackgroundLoading = true**欄位設為<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>若要確保可以以非同步方式初始化封裝，如需 PackageRegistrationAttribute 詳細資訊，請參閱[註冊和取消註冊 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)。

- 您必須新增**IsAsyncQueryable = true**欄位設為<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>以確保能夠以非同步方式初始化服務執行個體。

  以下是範例`AsyncPackage`使用非同步服務註冊：

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>新增服務

1. 在  *TestAsyncPackage.cs*，移除`Initialize()`方法，並覆寫`InitializeAsync()`方法。 新增服務，以及建立服務的回呼方法。 以下是非同步的初始設定式新增服務的範例：

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```

2. 將參考加入*Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*。

3. 為非同步方法，建立並傳回服務實作的回呼方法。

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>使用服務
 現在您可以取得服務，並使用它的方法。

1. 我們將示範這在初始設定式，但您可以取得任何地方您要使用服務的服務。

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

     別忘了變更`userpath`檔案名稱和您的電腦有意義的路徑 ！

2. 建置並執行程式碼。 Visual Studio 的實驗執行個體出現時，請開啟方案。 這會導致`AsyncPackage`自動載入。 當初始設定式執行時，您應該在您指定的位置中找到檔案。

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>在命令處理常式中使用非同步的服務
 以下是如何使用非同步的服務中的功能表命令的範例。 您可以使用如下所示，在其他非非同步方法中使用服務的程序。

1. 將功能表命令加入至您的專案。 (在**方案總管**，選取專案節點、 按一下滑鼠右鍵，然後選取**新增** > **新項目** >  **擴充性** > **自訂命令**。)將檔案命名為命令*TestAsyncCommand.cs*。

2. 自訂命令範本重新加入`Initialize()`方法，以*TestAsyncPackage.cs*以便初始化命令的檔案。 在 `Initialize()`方法中，複製初始化命令列。 內容應該看起來如下：

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     移至這一行`InitializeAsync()`方法中的*AsyncPackageForService.cs*檔案。 由於這是在非同步初始化期間，您必須切換至主執行緒在初始化命令使用之前<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>。 它現在看起來應該像這樣：

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

3. 刪除`Initialize()`方法。

4. 在  *TestAsyncCommand.cs*檔案中，尋找`MenuItemCallback()`方法。 刪除方法的主體。

5. 新增 using 陳述式：

    ```csharp
    using System.IO;
    ```

6. 新增名為非同步方法`UseTextWriterAsync()`，它取得的服務，並使用它的方法：

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

7. 呼叫這個方法從`MenuItemCallback()`方法：

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. 建置方案並開始偵錯。 當 Visual Studio 的實驗性執行個體，時請前往**工具**功能表，然後尋找**叫用 TestAsyncCommand**功能表項目。 當您按一下它時，TextWriterService 會寫入您指定的檔案。 （您不需要開啟的方案，因為叫用此命令也會導致要載入之封裝。）

## <a name="see-also"></a>另請參閱
- [使用，並提供服務](../extensibility/using-and-providing-services.md)
