---
title: How to：提供服務 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 565a8a91797c826b6419dc5a8488d7d3baf9cddc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838953"
---
# <a name="how-to-provide-a-service"></a>如何︰提供服務
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage 可以提供其他 Vspackage 可以使用的服務。 若要提供服務，VSPackage 必須向 Visual Studio 註冊服務，然後加入服務。  
  
 <xref:Microsoft.VisualStudio.Shell.Package>類別會同時執行 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 和 <xref:System.ComponentModel.Design.IServiceContainer> 。 <xref:System.ComponentModel.Design.IServiceContainer> 包含可依需求提供服務的回呼方法。  
  
 如需服務的詳細資訊，請參閱 [Service Essentials](../extensibility/internals/service-essentials.md) 。  
  
> [!NOTE]
> VSPackage 即將卸載時，Visual Studio 等候，直到已傳遞 VSPackage 提供的服務的所有要求為止。 不允許對這些服務提出新的要求。 當卸載時，您不應該明確地呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> 方法來撤銷服務。  
  
#### <a name="implementing-a-service"></a>執行服務  
  
1. 建立 VSIX 專案 (檔案 **/新增/專案/Visual c #/Extensiblity/VSIX 專案**) 。  
  
2. 將 VSPackage 新增至專案。 在 **方案總管** 中選取專案節點，然後按一下 [ **加入]/[新增專案]/[Visual c # 專案/擴充性/Visual Studio 套件**]。  
  
3. 若要執行服務，您必須建立三種類型：  
  
   - 描述服務的介面。 其中許多介面都是空的，也就是說，它們沒有任何方法。  
  
   - 描述服務介面的介面。 此介面包含要執行的方法。  
  
   - 同時執行服務與服務介面的類別。  
  
     下列範例顯示這三種類型非常基本的實作為。 服務類別的函式必須設定服務提供者。  
  
   ```csharp  
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
  
### <a name="registering-a-service"></a>註冊服務  
  
1. 若要註冊服務，請將加入 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 至提供服務的 VSPackage。 範例如下：  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     這個屬性會 `SMyService` 向 Visual Studio 註冊。  
  
    > [!NOTE]
    > 若要註冊服務來取代另一個具有相同名稱的服務，請使用 <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> 。 請注意，只允許一個服務覆寫。  
  
### <a name="adding-a-service"></a>新增服務  
  
1. 1.  在 VSPackage 初始化運算式中，加入服務並新增回呼方法來建立服務。 以下是對方法所做的變更 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> ：  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2. 假設回呼方法應該建立並傳回服務，如果無法建立則為 null。  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    > Visual Studio 可能會拒絕提供服務的要求。 如果另一個 VSPackage 已經提供服務，它就會這樣做。  
  
3. 現在您可以取得服務，並使用其方法。 我們將在初始化運算式中顯示這項功能，但您可以在想要使用服務的任何位置取得服務。  
  
    ```csharp  
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
  
     的值 `helloString` 應該是 "Hello"。  
  
## <a name="see-also"></a>另請參閱  
 [How to：取得服務](../extensibility/how-to-get-a-service.md)   
 [使用和提供服務](../extensibility/using-and-providing-services.md)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)
