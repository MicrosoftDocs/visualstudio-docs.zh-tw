---
title: "如何： 提供非同步的 Visual Studio 服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ea22a30d6f31099ca5d69d9cd8178188577febfe
ms.sourcegitcommit: a80e7ef2f0a0f6d906a44f4d696aeb208bc1ad70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2018
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>如何： 提供非同步的 Visual Studio 服務
如果您想要取得服務，而不封鎖 UI 執行緒，您應該建立非同步的服務，並載入背景執行緒上的套件。 您可以針對此用途使用<xref:Microsoft.VisualStudio.Shell.AsyncPackage>而不是<xref:Microsoft.VisualStudio.Shell.Package>，然後以非同步的封裝特殊的非同步方法中加入服務。
  
 如需提供同步的 Visual Studio 服務的資訊，請參閱[How to： 提供服務](../extensibility/how-to-provide-a-service.md)。  
  
## <a name="implementing-an-asynchronous-service"></a>實作非同步服務  
  
1.  建立 VSIX 專案 (**檔案 > 新增 > 專案 > Visual C# > Extensiblity > VSIX 專案**)。 將專案命名**TestAsync**。  
  
2.  加入專案中的 VSPackage。 選取專案節點中的**方案總管 中**按一下**新增 > 新的項目 > Visual C# 項目 > 擴充性 > Visual Studio Package**。 將這個檔案命名**TestAsyncPackage.cs**。  
  
3.  在 TestAsyncPackage.cs，來變更要繼承自 AsyncPackage，而不是封裝的封裝：  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  若要實作的服務，您必須建立三種類型：  
  
    -   識別服務介面。 許多這些介面是空的也就是說，它們有沒有任何方法因為它們只用於查詢服務。
  
    -   這個介面會描述服務介面。 這個介面包含要實作的方法。  
  
    -   實作服務和服務介面的類別。  
  
5.  下列範例顯示三種類型的基本實作。 服務類別的建構函式必須設定的服務提供者。 在此範例中我們只會將服務新增至封裝的程式碼檔案。  
  
6.  加入下列 using 陳述式的封裝檔案：  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```  
  
7.  以下是非同步的服務實作。 請注意，您必須設定於建構函式的非同步服務提供者，而不是同步的服務提供者：  
  
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
            // We have to use JoinableTaskFactory as code will switch to main thread in some parts
            await ThreadHelper.JoinableTaskFactory.RunAsync(async () =>
            {
                await TaskScheduler.Default;
                // do background operations that involve IO or other async methods
                
                await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);               
                // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
                // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.
                
                IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
                // use Visual Studio services to continue initialization
            });
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
  
## <a name="registering-a-service"></a>註冊服務  
 若要註冊的服務，將<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>提供服務的封裝。 不同註冊同步服務，您必須確定封裝和服務支援非同步載入：
  
-   您必須新增**AllowsBackgroundLoading = true**欄位設為<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>為了確保封裝可以以非同步方式初始化的 PackageRegistrationAttribute 的詳細資訊，請參閱[註冊和取消登錄 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)。  
  
-   您必須新增**IsAsyncQueryable = true**欄位設為<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>以確保能夠以非同步方式初始化服務執行個體。

 使用非同步服務註冊 AsyncPackage 的範例如下：
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>新增服務  
  
1.  在 TestAsyncPackage.cs，移除`Initialize()`方法，並覆寫`InitializeAsync()`方法。 加入服務，並加入要建立服務的回呼方法。 以下是範例的非同步加入服務的初始設定式：  
  
    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }  
  
    ```  
  
2.  加入 Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll 的參考。  
  
3.  為非同步方法，建立並傳回服務實作的回呼方法。  
  
    ```csharp  
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        TextWriterService service = new TextWriterService(this);  
        await service.InitializeAsync(cancellationToken);
        return service;
    }  
  
    ```  
  
## <a name="using-a-service"></a>使用服務  
 現在您可以取得服務，並使用它的方法。  
  
1.  我們將示範這個初始設定式，但您可以取得任意處您想要使用服務的服務。  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync(<userpath>), "this is a test");  
  
    }  
  
    ```  
  
     別忘了變更 *\<userpath >*檔名和路徑，在您的電腦上有意義 ！  
  
2.  建置並執行程式碼。 Visual Studio 的實驗執行個體出現時，請開啟的方案。 這會導致自動載入至 AsyncPackage。 當初始設定式執行時，您應該在您指定的位置尋找檔案。  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>在命令處理常式中使用非同步服務  
 以下是如何使用非同步服務中的功能表命令的範例。 您可以使用如下所示，在其他非非同步方法中使用服務的程序。  
  
1.  將功能表命令加入至您的專案。 (在**方案總管 中**，選取專案節點，按一下滑鼠右鍵，並選取**新增 / 新項目 / 擴充性 / 自訂命令**。)命令檔命名**TestAsyncCommand.cs。**  
  
2.  自訂命令範本重新加入`Initialize()`TestAsyncPackage.cs 檔案，以便初始化命令的方法。 在 initialize （） 方法中，複製初始化命令列。 內容應該看起來如下：  
  
    ```csharp
    TestAsyncCommand.Initialize(this);  
    ```  
  
     移至這一行`InitializeAsync()`AsyncPackageForService.cs 檔案中的方法。 由於這是在非同步初始化期間，您必須切換到主要執行緒在初始化命令使用之前<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>。 它現在看起來應該像這樣：  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  

        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync((<userpath>, "this is a test");  
  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        TestAsyncCommand.Initialize(this);
    }  
  
    ```  
  
3.  刪除`Initialize()`方法。  
  
4.  在 TestAsyncCommand.cs 檔案中，尋找`MenuItemCallback()`方法。 刪除方法主體。  
  
5.  新增 using 陳述式：  
  
    ```csharp 
    using System.IO;  
    ```  
  
6.  加入名為的非同步方法`UseTextWriterAsync()`，它取得的服務，並使用它的方法：  
  
    ```csharp  
    private async System.Threading.Tasks.Task UseTextWriterAsync()  
    {  
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =   
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))  
              as ITextWriterService;  

        // don't forget to change <userpath> to a local path  
        await textService.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  呼叫這個方法從`MenuItemCallback()`方法：  
  
    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        UseTextWriterAsync();  
    }  
  
    ```  
  
8.  建置方案並開始偵錯。 Visual Studio 的實驗執行個體出現時，請移至**工具**功能表並尋找**叫用 TestAsyncCommand**功能表項目。 當您按一下它時，TextWriterService 會寫入您指定的檔案。 （您不需要開啟的方案，因為叫用命令也會導致要載入之封裝。）  
  
## <a name="see-also"></a>另請參閱  
 [使用和提供服務](../extensibility/using-and-providing-services.md)
