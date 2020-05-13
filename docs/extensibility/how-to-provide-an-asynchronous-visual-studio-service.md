---
title: 如何:提供異步視覺工作室服務 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65362e465beec5465903083beca069104a48166b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710759"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>如何:提供異步視覺工作室服務
如果要在不阻塞 UI 線程的情況下獲取服務,則應創建非同步服務並將包載入到後台線程上。 為此,<xref:Microsoft.VisualStudio.Shell.AsyncPackage>可以使用<xref:Microsoft.VisualStudio.Shell.Package>而不是 , 並使用非同步包的特殊非同步方法添加服務。

 有關提供同步 Visual Studio 服務的資訊,請參閱[如何:提供服務](../extensibility/how-to-provide-a-service.md)。

## <a name="implement-an-asynchronous-service"></a>實現非同步服務

1. 建立 VSIX 專案 (**檔案** > **新項目** > **Project** > **視覺化 C#** > **擴充性** > **VSIX 專案**)。 命名項目**TestAsync**。

2. 向專案添加 VS 包。 在**解決方案資源管理器**中選擇專案節點,然後單擊 **「添加新** > **專案** > **Visual C# 專案** > **擴展可視化** > **工作室包**」。 TestAsyncPackage.cs命名此*檔案。*

3. 在*TestAsyncPackage.cs*中,將包`AsyncPackage`更改`Package`為 從 繼承,而不是 :

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. 要建立服務,您需要建立三種類型:

    - 標識服務的介面。 其中許多介面為空,也就是說,它們沒有方法,因為它們僅用於查詢服務。

    - 描述服務介面的介面。 此介面包括要實現的方法。

    - 實現服務和服務介面的類。

5. 下面的示例顯示了三種類型的基本實現。 服務類的構造函數必須設置服務提供者。 在此範例中,我們將將服務添加到包代碼檔中。

6. 將以下使用指令加入到套件檔中:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. 下面是異步服務實現。 請注意,您需要設置非同步服務提供者,而不是建構函式中的同步服務提供者:

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
 要註冊服務,請將<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>添加到提供該服務的包。 與註冊同步服務不同,您必須確保包和服務都支援非同步載入:

- 您必須將 **「允許後台載入 =** 真實<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>」欄位 添加到,以確保包可以非同步初始化,有關包註冊屬性的詳細資訊,請參閱[註冊和取消註冊 VSPackage。](../extensibility/registering-and-unregistering-vspackages.md)

- 您必須將**IsAsync 可查詢 = 真實**欄位<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>添加到 中,以確保服務實例可以非同步初始化。

  下面是`AsyncPackage`具有非同步服務註冊的 範例:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>新增服務

1. 在*TestAsyncPackage.cs*中,`Initialize()`刪除方法`InitializeAsync()`並重寫 該方法。 添加服務,並添加回調方法來創建服務。 下面是非同步初始化器加入服務的範例:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    要使此服務在此套件之外可見,將升級標誌值設定為*true*作為最後一個參數:`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. 新增對*微軟的引用.VisualStudio.shell.Interop.14.0.DesignTime.dll*.

3. 將回調方法實現為創建和返回服務的非同步方法。

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>使用服務
 現在,您可以獲取服務並使用其方法。

1. 我們將在初始化程序中顯示這一點,但您可以在任何要使用該服務的地方獲取服務。

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

     不要忘記更改為`userpath`檔名和在電腦上有意義的路徑!

2. 生成並運行代碼。 當 Visual Studio 的實驗實例出現時,打開解決方案。 這將導致自動`AsyncPackage`載入。 初始化程式運行後,應在指定的位置找到檔。

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>在命令處理程式中使用非同步服務
 下面是如何在功能表命令中使用非同步服務的範例。 您可以使用此處顯示的過程在其他非非同步方法中使用服務。

1. 向專案添加功能表命令。 (在**解決方案資源管理器**中,選擇專案節點,右鍵單擊,然後選擇 **"** > **添加新項目** > **擴展性** > **自定義命令**."TestAsyncCommand.cs命名*命令檔。*

2. 自定義命令範本將`Initialize()`方法重新添加到*TestAsyncPackage.cs*檔,以便初始化該命令。 在`Initialize()`方法中,複製初始化命令的行。 它看起來應該如下所示：

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     將此行移到*AsyncPackageForService.cs*`InitializeAsync()`檔案中的方法。 由於這是異步初始化中,因此在使用<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>初始化命令之前,必須切換到主線程。 目前看起來應該如下所示：

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

4. *在 TestAsyncCommand.cs*檔案中,`MenuItemCallback()`尋找方法 。 刪除方法的正文。

5. 新增 using 指令:

    ```csharp
    using System.IO;
    ```

6. 新增名為`UseTextWriterAsync()`的 非同步方法,該方法取得服務並使用其方法:

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

7. 從`MenuItemCallback()`方法呼叫此方法:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. 建置方案並開始偵錯。 當 Visual Studio 的實驗實例出現時,轉到 **「工具」** 選單並查找 **「調用測試 Async 命令」** 選單項。 按下它時,TextWriterService 會寫入您指定的檔。 (您無需打開解決方案,因為呼叫該命令也會導致載入套件。

## <a name="see-also"></a>另請參閱
- [使用與提供服務](../extensibility/using-and-providing-services.md)
