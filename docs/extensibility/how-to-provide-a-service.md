---
title: "如何: 提供的服務 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "提供的服務"
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何: 提供的服務
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage 可提供其他 VSPackages 可以使用的服務。 若要提供服務，VSPackage 必須使用 Visual Studio 註冊服務，以及新增的服務。  
  
 <xref:Microsoft.VisualStudio.Shell.Package> 類別會同時實作 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 和 <xref:System.ComponentModel.Design.IServiceContainer>。<xref:System.ComponentModel.Design.IServiceContainer> 包含要求提供服務的回呼方法。  
  
 如需服務的詳細資訊，請參閱 [服務的基本資訊](../extensibility/internals/service-essentials.md) 。  
  
> [!NOTE]
>  將要卸載 VSPackage 時，Visual Studio 會等到所有的 VSPackage 提供服務的要求已傳送。 它不允許這些服務的新要求。 您應該明確呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> 方法撤銷服務卸載。  
  
#### 實作服務  
  
1.  建立 VSIX 專案 \(**檔案 \/ 新增 \/ 專案 \/ Visual C\# \/ Extensiblity \/ VSIX 專案**\)。  
  
2.  加入專案中的 VSPackage。 選取專案節點中的 **方案總管\] 中** 按一下 **加入 \/ 新增項目 \/ Visual C\# 項目 \/ 擴充性 \/ Visual Studio 套件**。  
  
3.  若要實作的服務，您需要建立三種類型︰  
  
    -   描述服務的介面。 許多這些介面是空的也就是說，它們有沒有任何方法。  
  
    -   描述服務介面的介面。 這個介面包含要實作的方法。  
  
    -   實作服務和服務介面的類別。  
  
     下列範例示範三種類型的基本實作。 服務類別的建構函式必須設定服務提供者。  
  
    ```c#  
    public class MyService : SMyService, IMyService  
    {  
        private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
        private string myString;  
        public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
        {  
            Trace.WriteLine(  
                   "Constructing a new instance of MyService");  
            serviceProvider = sp;  
        }  
        public void Hello()  
        {  
            myString = "hello";  
        }  
        public string Goodbye()  
        {  
           return "goodbye";  
        }  
    }  
    public interface SMyService  
    {  
    }  
    public interface IMyService  
    {  
        void Hello();  
        string Goodbye();  
    }  
  
    ```  
  
### 註冊服務  
  
1.  若要註冊服務，將加入 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 來提供服務的 VSPackage。 範例如下︰  
  
    ```c#  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     這個屬性會註冊 `SMyService` 與 Visual Studio。  
  
    > [!NOTE]
    >  若要註冊相同的名稱，取代另一個服務的服務，使用 <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>。 請注意在允許的服務只能有一個覆寫。  
  
### 新增服務  
  
1.  1.	VSPackage 初始設定式中加入服務，並新增回呼方法，以建立服務。 以下是可讓變更 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法︰  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  實作回呼方法，而應該建立並傳回服務，或如果無法建立，則為 null。  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio 可以拒絕的要求提供服務。 如果另一個 VSPackage 已經提供服務，它可以這麼做。  
  
3.  現在您可以取得服務，並使用其方法。 我們將示範此初始設定式，但您可以取得任何地方您要使用服務的服務。  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     值 `helloString` 應該是"Hello"。  
  
## 請參閱  
 [如何: 取得服務](../Topic/How%20to:%20Get%20a%20Service.md)   
 [使用並提供服務](../extensibility/using-and-providing-services.md)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)