---
title: 如何：提供非同步服務 |Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c58b0be10bf10a21b783a48d52806bf769381ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204108"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>如何︰提供非同步的 Visual Studio 服務
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您想要取得服務而不封鎖 UI 執行緒，您應該建立異步服務，並在背景執行緒上載入封裝。 基於這個目的，您可以使用 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 而不是 <xref:Microsoft.VisualStudio.Shell.Package> ，並使用非同步封裝的特殊非同步方法來新增服務。

 如需有關提供同步 Visual Studio 服務的詳細資訊，請參閱 how [to：提供服務](../extensibility/how-to-provide-a-service.md)。

## <a name="implementing-an-asynchronous-service"></a>執行非同步服務

1. 建立 VSIX 專案 (檔案 **/新增/專案/Visual c #/Extensiblity/VSIX 專案**) 。 將專案命名為 **TestAsync**。

2. 將 VSPackage 新增至專案。 在 **方案總管** 中選取專案節點，然後按一下 [ **加入]/[新增專案]/[Visual c # 專案/擴充性/Visual Studio 套件**]。 將這個檔案命名為 **TestAsyncPackage.cs**。

3. 在 TestAsyncPackage.cs 中，將封裝變更為繼承自 AsyncPackage，而不是封裝：

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. 若要執行服務，您必須建立三種類型：

    - 描述服務的介面。 其中許多介面都是空的，也就是說，它們沒有任何方法。

    - 描述服務介面的介面。 此介面包含要執行的方法。

    - 同時執行服務與服務介面的類別。

5. 下列範例顯示這三種類型非常基本的實作為。 服務類別的函式必須設定服務提供者。 在此範例中，我們只會將服務新增至封裝程式碼檔案。

6. 將下列 using 語句加入至封裝檔案：

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7. 以下是非同步服務的執行。 請注意，您必須在函式中設定非同步服務提供者，而不是同步服務提供者：

    ```
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)
        {
            serviceProvider = provider;
        }
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
        public TaskAwaiter GetAwaiter()
        {
            return new TaskAwaiter();
        }
    }
    public interface STextWriterService
    {
    }
    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
        TaskAwaiter GetAwaiter();
    }
    ```

## <a name="registering-a-service"></a>註冊服務
 若要註冊服務，請將加入 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 至提供服務的封裝。 註冊同步服務有兩個不同之處：

- 如果您要自動載入功能封裝，您必須將 <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad 值加入至屬性。 如需自動載入功能 Vspackage 的詳細資訊，請參閱 [載入 vspackage](../extensibility/loading-vspackages.md)。

- 您必須將 **AllowsBackgroundLoading = true** 欄位加入至 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 。 如需 PackageRegistrationAttribute 的詳細資訊，請參閱 [註冊和取消註冊 vspackage](../extensibility/registering-and-unregistering-vspackages.md)。

  以下是使用非同步服務註冊 AsyncPackage 的範例：

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>新增服務

1. 在 TestAsyncPackage.cs 中，移除 `Initialize()` 方法並覆寫 `InitializeAsync()` 方法。 新增服務，並新增回呼方法來建立服務。 以下是非同步初始化運算式新增服務的範例：

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2. 新增 Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll 的參考。

3. 將回呼方法實作為建立和傳回服務的非同步方法。

    ```csharp
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        STextWriterService service = null;
        await System.Threading.Tasks.Task.Run(() => {
                    service = new TextWriterService(this);
             });

        return service;
    }

    ```

## <a name="using-a-service"></a>使用服務
 現在您可以取得服務，並使用其方法。

1. 我們將在初始化運算式中顯示這項功能，但您可以在想要使用服務的任何位置取得服務。

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     別忘了變更 *\<userpath>* 為電腦上合理的檔案名和路徑！

2. 建立並執行程式碼。 當 Visual Studio 的實驗實例出現時，開啟方案。 這會造成 AsyncPackage 自動載入。 當初始化運算式執行時，您應該會在指定的位置中找到檔案。

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>在命令處理常式中使用非同步服務
 以下是如何在功能表命令中使用非同步服務的範例。 您可以使用此處所示的程式，在其他非非同步方法中使用此服務。

1. 將功能表命令新增至您的專案。  (在 **方案總管**中，選取專案節點，按一下滑鼠右鍵，然後選取 [新增 **/新增專案/擴充性/自訂命令**]。 ) 將命令檔命名為 **TestAsyncCommand.cs。**

2. 自訂命令範本會將方法重新新增至 TestAsyncPackage.cs 檔案，以便 `Initialize()` 初始化命令。 在 Initialize ( # A1 方法中，複製初始化命令的行。 其看起來應該如下：

    ```
    TestAsyncCommand.Initialize(this);
    ```

     將這一行移至 `InitializeAsync()` AsyncPackageForService.cs 檔中的方法。 由於這是在非同步初始化中，因此您必須先切換到主執行緒，才能使用初始化命令 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 。 目前看起來應該如下所示：

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        TestAsyncCommand.Initialize(this);

        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync((<userpath>, "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

3. 刪除 `Initialize()` 方法。

4. 在 TestAsyncCommand.cs 檔案中，尋找 `MenuItemCallback()` 方法。 刪除方法的主體。

5. 新增 using 陳述式：

    ```
    using System.IO;
    ```

6. 新增名為的非同步方法 `GetAsyncService()` ，這個方法會取得服務並使用其方法：

    ```csharp
    private async System.Threading.Tasks.Task GetAsyncService()
    {
        ITextWriterService textService =
           this.ServiceProvider.GetService(typeof(STextWriterService))
              as ITextWriterService;
        // don’t forget to change <userpath> to a local path
        await writer.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7. 從方法呼叫這個方法 `MenuItemCallback()` ：

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8. 建置方案並開始偵錯。 當 Visual Studio 的實驗實例出現時，請移至 [ **工具** ] 功能表，並尋找 [叫用 **TestAsyncCommand** ] 功能表項目。 當您按一下它時，TextWriterService 會寫入您指定的檔案。  (您不需要開啟方案，因為叫用命令也會造成封裝載入。 ) 

## <a name="see-also"></a>另請參閱
 [使用和提供服務](../extensibility/using-and-providing-services.md)
