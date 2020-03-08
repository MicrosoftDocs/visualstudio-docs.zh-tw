---
title: 服務基本 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8817ca48ff0a3f44a973986a173e647ce89c662c
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409713"
---
# <a name="service-essentials"></a>服務的基本資訊
服務是兩個 Vspackage 之間的合約。 一個 VSPackage 會提供一組特定的介面，供另一個 VSPackage 使用。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 本身是 Vspackage 的集合，可提供服務給其他 Vspackage。

 例如，您可以使用 SVsActivityLog 服務取得 IVsActivityLog 介面，以便用來寫入至活動記錄。 如需詳細資訊，請參閱[如何：使用活動記錄](../../extensibility/how-to-use-the-activity-log.md)。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 也會提供一些未註冊的內建服務。 Vspackage 可以藉由提供服務覆寫來取代內建或其他服務。 任何服務都只允許一個服務覆寫。

 服務沒有探索能力。 因此，您必須知道您想要使用之服務的服務識別碼（SID），而且您必須知道它所提供的介面。 服務的參考檔會提供此資訊。

- 提供服務的 Vspackage 稱為「服務提供者」。

- 提供給其他 Vspackage 的服務稱為「全域服務」。

- 僅適用于執行這些服務的 VSPackage，或其所建立之任何物件的服務，都稱為「本機服務」。

- 取代內建服務或其他套件所提供服務的服務，稱為「服務覆寫」。

- 服務（或服務覆寫）視需要載入，也就是當另一個 VSPackage 要求服務提供者所提供的服務時，就會載入它。

- 為了支援隨選載入，服務提供者會向 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]註冊其全域服務。 如需詳細資訊，請參閱[如何：提供服務](../../extensibility/how-to-provide-a-service.md)。

- 取得服務之後，請使用[QueryInterface](/cpp/atl/queryinterface) （非受控碼）或轉換（managed 程式碼）來取得所需的介面，例如：

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Managed 程式碼會依其型別參考服務，而非受控碼會依其 GUID 參考服務。

- 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 載入 VSPackage 時，它會將服務提供者傳遞給 VSPackage，以授與 VSPackage 對全域服務的存取權。 這稱為「地點」 VSPackage。

- Vspackage 可以是所建立物件的服務提供者。 例如，表單可能會將色彩服務的要求傳送到其框架，這可能會將要求傳遞給 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

- 已深層嵌套或完全不代表的 Managed 物件，可能會呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>，以便直接存取全域服務。

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>使用 GetGlobalService

有時候，您可能需要從工具視窗或控制項容器中取得尚未找出的服務，或已將服務提供者與不知道您想要的服務相關聯。 例如，您可能想要從控制項內寫入活動記錄。 如需這些和其他案例的詳細資訊，請參閱[如何：針對服務進行疑難排解](../../extensibility/how-to-troubleshoot-services.md)。

您可以藉由呼叫靜態 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 方法來取得大部分的 Visual Studio 服務。

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 依賴第一次從 Package 衍生的任何 VSPackage 所放置的快取服務提供者。 您必須保證符合此條件，否則請為 null 服務準備。

幸好，<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 大部分的時間都能正常運作。

- 如果 VSPackage 提供僅供另一個 VSPackage 使用的服務，則要求服務的 VSPackage 就會放置在提供服務的 VSPackage 載入之前。

- 如果工具視窗是由 VSPackage 所建立，則 VSPackage 會在建立工具視窗之前放置。

- 如果控制項容器是由 VSPackage 所建立的工具視窗所主控，則 VSPackage 會在建立控制項容器之前放置。

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>從工具視窗或控制項容器中取得服務

- 將此程式碼插入至 [函式]、[工具視窗] 或 [控制項] 容器：

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

    這段程式碼會取得 SVsActivityLog 服務，並將它轉換成 IVsActivityLog 介面，以用來寫入活動記錄。 如需範例，請參閱[如何：使用活動記錄](../../extensibility/how-to-use-the-activity-log.md)。

## <a name="see-also"></a>另請參閱

- [可用服務清單](../../extensibility/internals/list-of-available-services.md)
- [使用和提供服務](../../extensibility/using-and-providing-services.md)
- [轉換和型別轉換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [轉型](/cpp/cpp/casting)