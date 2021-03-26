---
title: 服務基本 |Microsoft Docs
description: 深入瞭解服務，這是另一個 VSPackage 要使用的介面。 VSPackage 中的服務可以覆寫內建或其他服務。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69e7e1c5b18019c4ff063ec504fc702f47f7e023
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080823"
---
# <a name="service-essentials"></a>服務的基本資訊
服務是兩個 Vspackage 之間的合約。 其中一個 VSPackage 會提供一組特定的介面，供另一個要取用的 VSPackage 使用。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 本身是提供服務給其他 Vspackage 的 Vspackage 集合。

 例如，您可以使用 SVsActivityLog 服務取得 IVsActivityLog 介面，此介面可用來寫入活動記錄。 如需詳細資訊，請參閱 [如何：使用活動記錄](../../extensibility/how-to-use-the-activity-log.md)。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 也提供一些未註冊的內建服務。 Vspackage 可以藉由提供服務覆寫來取代內建或其他服務。 任何服務都只允許一個服務覆寫。

 服務沒有可搜尋的。 因此，您必須知道您想要取用之服務的服務識別碼 (SID) ，而且必須知道它所提供的介面。 服務的參考檔會提供此資訊。

- 提供服務的 Vspackage 稱為服務提供者。

- 提供給其他 Vspackage 的服務稱為「全域服務」。

- 只有執行這些服務的 VSPackage 或其所建立的任何物件才能使用這些服務，稱為本機服務。

- 取代其他封裝所提供的內建服務或服務的服務，稱為服務覆寫。

- 服務或服務覆寫會視需要載入，也就是當另一個 VSPackage 要求服務提供者所提供的服務時，就會載入服務提供者。

- 為了支援隨選載入，服務提供者會向註冊其全域服務 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 如需詳細資訊，請參閱 how [to：提供服務](../../extensibility/how-to-provide-a-service.md)。

- 取得服務之後，請使用 [QueryInterface](/cpp/atl/queryinterface) (非受控程式碼) 或轉換 (managed 程式碼) 以取得所需的介面，例如：

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Managed 程式碼是由其型別所參考的服務，而非受控碼則是透過其 GUID 來參考服務。

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入 VSPackage 時，它會將服務提供者傳遞給 VSPackage，以授與 VSPackage 對全域服務的存取權。 這稱為「地點」 VSPackage。

- Vspackage 可以是其所建立物件的服務提供者。 例如，表單可能會將色彩服務的要求傳送至其框架，而這可能會將要求傳遞至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- 具有深層嵌套或未放置的 Managed 物件，可能會呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 以直接存取全域服務。

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>使用 GetGlobalService

有時，您可能需要從尚未放置的工具視窗或控制項容器取得服務，或使用其他服務提供者不知道您想要的服務。 例如，您可能想要從控制項內寫入活動記錄。 如需有關這些案例和其他案例的詳細資訊，請參閱 [如何：針對服務進行疑難排解](../../extensibility/how-to-troubleshoot-services.md)。

您可以藉由呼叫靜態方法來取得大部分的 Visual Studio 服務 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 。

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 依賴快取的服務提供者，此提供者會在第一次從封裝衍生的任何 VSPackage 被放置時初始化。 您必須保證符合此條件，或為 null 服務做好準備。

幸運的 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 是，大部分的時間都能正常運作。

- 如果 VSPackage 提供僅知道另一個 VSPackage 的服務，則要求服務的 VSPackage 會在載入服務的 VSPackage 之前放置。

- 如果工具視窗是由 VSPackage 所建立，則 VSPackage 會在建立工具視窗之前放置。

- 如果控制項容器是由 VSPackage 所建立的工具視窗所主控，則 VSPackage 會在建立控制項容器之前放置。

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>從工具視窗或控制項容器內取得服務

- 在 [函式]、[工具視窗] 或 [控制項容器] 中插入此程式碼：

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    此程式碼會取得 SVsActivityLog 服務，並將其轉換為 IVsActivityLog 介面，可用來寫入活動記錄。 如需範例，請參閱 [如何：使用活動記錄](../../extensibility/how-to-use-the-activity-log.md)。

## <a name="see-also"></a>另請參閱

- [可用服務清單](../../extensibility/internals/list-of-available-services.md)
- [使用和提供服務](../../extensibility/using-and-providing-services.md)
- [轉換和類型轉換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [轉型](/cpp/cpp/casting)
