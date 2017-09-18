---
title: "如何︰ 提供非同步的 Visual Studio 服務 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何︰ 提供非同步的 Visual Studio 服務
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您想要取得服務，而不封鎖 UI 執行緒，您應該建立非同步的服務，並在背景執行緒將封裝載入。 為此，您可以使用 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 而 <xref:Microsoft.VisualStudio.Shell.Package>, ，然後利用非同步封裝的特殊的非同步方法中加入服務  
  
 如需提供同步的 Visual Studio 服務資訊，請參閱 [如何: 提供的服務](../extensibility/how-to-provide-a-service.md)。  
  
## 實作非同步服務  
  
1.  建立 VSIX 專案 \(**檔案 \/ 新增 \/ 專案 \/ Visual C\# \/ Extensiblity \/ VSIX 專案**\)。 將專案命名為 **TestAsync**。  
  
2.  加入專案中的 VSPackage。 選取專案節點中的 **方案總管\] 中** 按一下 **加入 \/ 新增項目 \/ Visual C\# 項目 \/ 擴充性 \/ Visual Studio 套件**。 將這個檔案命名 **TestAsyncPackage.cs**。  
  
3.  在 TestAsyncPackage.cs，變更要繼承自 AsyncPackage，而不是封裝的封裝︰  
  
    ```c#  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  若要實作的服務，您需要建立三種類型︰  
  
    -   描述服務的介面。 許多這些介面是空的也就是說，它們有沒有任何方法。  
  
    -   描述服務介面的介面。 這個介面包含要實作的方法。  
  
    -   實作服務和服務介面的類別。  
  
5.  下列範例示範三種類型的基本實作。 服務類別的建構函式必須設定服務提供者。 在此範例中我們會將服務加入封裝的程式碼檔案。  
  
6.  新增下列 using 陳述式封裝檔案︰  
  
    ```c#  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  以下是非同步的服務實作。 請注意，您必須設定於建構函式的非同步服務提供者，而不是同步服務提供者︰  
  
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
  
## 註冊服務  
 若要註冊服務，將加入 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 提供服務的套件。 有兩個登錄同步服務的差異︰  
  
-   如果您是自動載入封裝，您必須新增 <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad 值給屬性。 如需自動載入 Vspackage 的詳細資訊，請參閱 [載入 Vspackage](../extensibility/loading-vspackages.md)。  
  
-   您必須新增 **AllowsBackgroundLoading \= true** 欄位 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>。 如需 PackageRegistrationAttribute 的詳細資訊，請參閱 [註冊和取消註冊 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)。  
  
 非同步服務註冊 AsyncPackage 的範例如下︰  
  
```c#  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## 新增服務  
  
1.  在 TestAsyncPackage.cs，移除 `Initialize()` 方法，並覆寫 `InitializeAsync()` 方法。 新增服務，以及新增回呼方法來建立服務。 新增服務的非同步初始設定式的範例如下︰  
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  加入 Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll 的參考。  
  
3.  實作回呼方法做為非同步方法，以建立並傳回服務。  
  
    ```c#  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## 使用服務  
 現在您可以取得服務，並使用其方法。  
  
1.  我們將示範此初始設定式，但您可以取得任何地方您要使用服務的服務。  
  
    ```c#  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     別忘了變更 *\< userpath \>* 至檔案名稱，並在您的電腦有意義的路徑 ！  
  
2.  建置並執行程式碼。 Visual Studio 的實驗執行個體出現時，請開啟的方案。 這會導致自動載入 AsyncPackage。 當初始設定式執行時，您應該在您指定的位置尋找檔案。  
  
## 命令處理常式中使用非同步的服務  
 以下是如何使用非同步的服務中的功能表命令的範例。 您可以使用如下所示，以在其他非非同步方法中使用服務的程序。  
  
1.  將功能表命令加入至您的專案。 \(在 **方案總管\] 中**, ，選取專案節點、 按一下滑鼠右鍵，然後選取 **加入 \/ 新的項目 \/ 擴充性 \/ 自訂命令**。\) 命令檔命名 **TestAsyncCommand.cs。**  
  
2.  自訂命令範本重新加入 `Initialize()` TestAsyncPackage.cs 檔案，以初始化命令的方法。 在 initialize （） 方法中，複製初始化命令列。 它看起來應該像這樣︰  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     移至這一行 `InitializeAsync()` AsyncPackageForService.cs 檔案中的方法。 由於這是在非同步初始化期間，您必須切換到主執行緒在初始化命令使用之前 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>。 它現在看起來應該像這樣︰  
  
    ```c#  
  
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
  
3.  刪除 `Initialize()` 方法。  
  
4.  在 TestAsyncCommand.cs 檔案中，尋找 `MenuItemCallback()` 方法。 刪除方法的主體。  
  
5.  加入 using 陳述式︰  
  
    ```  
    using System.IO;  
    ```  
  
6.  新增名為非同步方法 `GetAsyncService()`, ，它取得的服務，並使用它的方法︰  
  
    ```c#  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don’t forget to change <userpath> to a local path  
        await writer.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  呼叫這個方法從 `MenuItemCallback()` 方法︰  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        GetAsyncService();  
    }  
  
    ```  
  
8.  建置方案並開始偵錯。 Visual Studio 的實驗執行個體出現時，請移至 **工具** 功能表，然後尋找 **叫用 TestAsyncCommand** 功能表項目。 當您按一下它時，TextWriterService 會寫入您指定的檔案。 （您不需要開啟的方案，因為叫用命令時也會導致要載入之封裝。）  
  
## 請參閱  
 [使用並提供服務](../extensibility/using-and-providing-services.md)