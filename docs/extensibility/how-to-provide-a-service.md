---
title: 如何:提供服務 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60cae5e8048a0234114e1f9e7d97728e26ee40f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710778"
---
# <a name="how-to-provide-a-service"></a>如何:提供服務
VS 套件可以提供其他 VS 套件可以使用的服務。 要提供服務,VSPackage 必須向 Visual Studio 註冊服務並添加該服務。

 類別<xref:Microsoft.VisualStudio.Shell.Package>的與<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider><xref:System.ComponentModel.Design.IServiceContainer>。 <xref:System.ComponentModel.Design.IServiceContainer>包含按需提供服務的回調方法。

 有關服務的詳細資訊,請參閱[服務要點](../extensibility/internals/service-essentials.md)。

> [!NOTE]
> 當 VSPackage 即將卸載時,Visual Studio 會等待,直到 VSPackage 提供的所有服務請求都已送達。 它不允許對這些服務進行新請求。 在卸載時,<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>不應顯式調用 方法以撤銷服務。

## <a name="implement-a-service"></a>實現服務

1. 建立 VSIX 專案 (**檔案** > **新專案** > **Project** > **視覺化 C_** > **擴充 VSIX** > **專案**)。

2. 向專案添加 VS 包。 在**解決方案資源管理器**中選擇專案節點,然後單擊 **「添加新** > **專案** > **Visual C# 專案** > **擴展可視化** > **工作室包**」。

3. 要建立服務,您需要建立三種類型:

   - 描述服務的介面。 其中許多介面是空的,也就是說,它們沒有方法。

   - 描述服務介面的介面。 此介面包括要實現的方法。

   - 實現服務和服務介面的類。

     下面的示例顯示了三種類型的基本實現。 服務類的構造函數必須設置服務提供者。

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

1. 要註冊服務,請將<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>添加到提供服務的 VSPackage。 範例如下：

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     此屬性向`SMyService`Visual Studio 註冊。

    > [!NOTE]
    > 要註冊以相同名稱取代另一個服務的服務,請使用<xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>。 請注意,只允許一個服務重寫。

### <a name="add-a-service"></a>新增服務

1. 在 VSPackage 初始化器中,添加服務並添加回調方法來創建服務。 下面是對<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法的變更:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. 實現回調方法(應創建和返回服務)或 null(如果無法創建)。

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio 可以拒絕提供服務的請求。 如果另一個 VSPackage 已經提供服務,則這樣做。

3. 現在,您可以獲取服務並使用其方法。 下面的範例顯示了在初始化器中使用服務,但您可以在要使用該服務的任何地方獲取服務。

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

     的值`helloString`應該是"你好"。

## <a name="see-also"></a>另請參閱
- [如何:取得服務](../extensibility/how-to-get-a-service.md)
- [使用與提供服務](../extensibility/using-and-providing-services.md)
- [服務要點](../extensibility/internals/service-essentials.md)
