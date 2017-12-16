---
title: "如何： 提供服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c37f4dc215027752da9c16fbdfba44b4e10c41c
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="how-to-provide-a-service"></a>如何： 提供的服務
VSPackage 可以提供其他 Vspackage 可以使用的服務。 若要提供服務，VSPackage 必須使用 Visual Studio 註冊服務，然後加入服務。  
  
 <xref:Microsoft.VisualStudio.Shell.Package>類別會同時實作<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>和<xref:System.ComponentModel.Design.IServiceContainer>。 <xref:System.ComponentModel.Design.IServiceContainer>包含回呼方法，提供要求的服務。  
  
 如需服務的詳細資訊，請參閱[服務 Essentials](../extensibility/internals/service-essentials.md) 。  
  
> [!NOTE]
>  將要卸載 VSPackage 時，Visual Studio 會等到所有 VSPackage 提供的服務要求已都傳送。 不允許新的要求，這些服務。 您不應該明確地呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>方法撤銷服務，當卸載。  
  
#### <a name="implementing-a-service"></a>實作服務  
  
1.  建立 VSIX 專案 (**檔案 > 新增 > 專案 > Visual C# > Extensiblity > VSIX 專案**)。  
  
2.  加入專案中的 VSPackage。 選取專案節點中的**方案總管 中**按一下**新增 > 新的項目 > Visual C# 項目 > 擴充性 > Visual Studio Package**。  
  
3.  若要實作的服務，您必須建立三種類型：  
  
    -   這個介面會描述服務。 許多這些介面是空的也就是說，它們有沒有任何方法。  
  
    -   這個介面會描述服務介面。 這個介面包含要實作的方法。  
  
    -   實作服務和服務介面的類別。  
  
     下列範例顯示三種類型的基本實作。 服務類別的建構函式必須設定的服務提供者。  
  
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
  
1.  若要註冊的服務，將<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>來提供服務的 VSPackage。 請看以下範例：  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     這個屬性會註冊`SMyService`與 Visual Studio。  
  
    > [!NOTE]
    >  若要註冊的服務，另一個服務取代為相同的名稱，請使用<xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>。 請注意在允許的服務只能有一個覆寫。  
  
### <a name="adding-a-service"></a>新增服務  
  
1.  VSPackage 初始設定式中加入服務，並加入回呼方法，以建立服務。 以下是對進行變更<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法：  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  實作的回呼方法應該建立並傳回服務，或如果無法建立，則為 null。  
  
    ```csharp  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio 可以拒絕的要求提供服務。 如果另一個 VSPackage 已經提供服務，它可以這麼做。  
  
3.  現在您可以取得服務，並使用它的方法。 我們將示範這個初始設定式，但您可以取得任意處您想要使用服務的服務。  
  
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
  
     值`helloString`應該是"Hello"。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 取得服務](../extensibility/how-to-get-a-service.md)   
 [使用並提供服務](../extensibility/using-and-providing-services.md)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)
