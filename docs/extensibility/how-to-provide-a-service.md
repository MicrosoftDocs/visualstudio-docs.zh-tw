---
title: 如何：提供服務 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30bfdd49d871919503be767ea930b3d5f2f0fd95
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905771"
---
# <a name="how-to-provide-a-service"></a>如何：提供服務
VSPackage 可以提供其他 Vspackage 可以使用的服務。 若要提供服務，VSPackage 必須向 Visual Studio 註冊服務，並新增服務。

 <xref:Microsoft.VisualStudio.Shell.Package>類別會同時執行 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 和 <xref:System.ComponentModel.Design.IServiceContainer> 。 <xref:System.ComponentModel.Design.IServiceContainer>包含可依需求提供服務的回呼方法。

 如需服務的詳細資訊，請參閱[Service essentials](../extensibility/internals/service-essentials.md) 。

> [!NOTE]
> 即將卸載 VSPackage 時，Visual Studio 會等到 VSPackage 提供之服務的所有要求都已傳遞為止。 不允許對這些服務提出新的要求。 在卸載時，您不應該明確地呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> 方法來撤銷服務。

## <a name="implement-a-service"></a>執行服務

1. 建立 VSIX**專案（檔案**  >  **新**  >  **專案**  >  **Visual c #** 擴充性  >  **Extensibility**  >  **VSIX 專案**）。

2. 將 VSPackage 新增至專案。 選取**方案總管**中的專案節點，然後按一下 [**加入**  >  **新專案**] [  >  **Visual c # 專案**] [擴充性]  >  **Extensibility**  >  **Visual Studio 封裝**]。

3. 若要執行服務，您需要建立三種類型：

   - 描述服務的介面。 其中有許多介面是空的，也就是說，它們沒有方法。

   - 描述服務介面的介面。 此介面包含要執行的方法。

   - 同時執行服務和服務介面的類別。

     下列範例顯示三種類型的基本實作為。 服務類別的函式必須設定服務提供者。

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

### <a name="register-a-service"></a>註冊服務

1. 若要註冊服務，請將新增 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 至提供服務的 VSPackage。 範例如下：

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     這個屬性會 `SMyService` 向 Visual Studio 註冊。

    > [!NOTE]
    > 若要註冊會取代另一個具有相同名稱之服務的服務，請使用 <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> 。 請注意，只允許服務的一個覆寫。

### <a name="add-a-service"></a>新增服務

1. 在 VSPackage 初始化運算式中，加入服務，並加入回呼方法來建立服務。 以下是對方法所做的變更 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> ：

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. 執行應建立並傳回服務的回呼方法，如果無法建立則為 null。

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio 可以拒絕提供服務的要求。 如果另一個 VSPackage 已經提供服務，它就會這麼做。

3. 現在您可以取得服務，並使用其方法。 下列範例顯示在初始化運算式中使用服務，但您可以在任何想要使用服務的地方取得服務。

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);

        MyService myService = (MyService) this.GetService(typeof(SMyService));
        myService.Hello();
        string helloString = myService.Goodbye();

        base.Initialize();
    }
    ```

     的值 `helloString` 應該是 "Hello"。

## <a name="see-also"></a>另請參閱
- [如何：取得服務](../extensibility/how-to-get-a-service.md)
- [使用並提供服務](../extensibility/using-and-providing-services.md)
- [服務基本](../extensibility/internals/service-essentials.md)
