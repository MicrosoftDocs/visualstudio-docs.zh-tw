---
title: 服務 Essentials |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26bfa7ce51249adc883415d09689ed390b7dfabc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934401"
---
# <a name="service-essentials"></a>服務的基本資訊
服務是兩個的 Vspackage 之間的合約。 一個 VSPackage 提供一組特定的介面使用的另一個 VSPackage。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 本身是提供服務給其他 Vspackage 的 Vspackage 集合。  
  
 例如，您可以使用 SVsActivityLog 服務取得 IVsActivityLog 介面，可用來寫入活動記錄檔。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用活動記錄](../../extensibility/how-to-use-the-activity-log.md)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 也提供一些內建的服務未註冊的。 Vspackage 可以藉由提供服務的覆寫來取代內建或其他服務。 只有一個服務覆寫所允許的任何服務。  
  
 服務有沒有可測知性。 因此，您必須知道您想要使用的服務的服務識別碼 (SID)，而且您必須知道它所提供的介面。 服務的參考文件提供這項資訊。  
  
- 提供服務的 Vspackage 會呼叫服務提供者。  
  
- 其他 vspackage 提供的服務稱為 「 全域服務 」。  
  
- 僅適用於 VSPackage 實作它們，或它所建立的任何物件，會呼叫本機服務的服務。  
  
- 取代內建的服務或由其他套件，提供服務的服務稱為服務覆寫。  
  
- 視需要載入服務或服務的覆寫，另一個 VSPackage 要求它所提供的服務時，也就是載入服務提供者。  
  
- 若要支援依需求載入，服務提供者註冊其全域服務與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱 <<c0> [ 如何： 提供服務](../../extensibility/how-to-provide-a-service.md)。  
  
- 取得服務之後，請使用[QueryInterface](/cpp/atl/queryinterface) (unmanaged 程式碼) 或轉型 （managed 程式碼） 來取得所需的介面，例如：  
  
  ```vb  
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
  ```  
  
  ```csharp  
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  ```  
  
- Managed 程式碼是指服務依其型別，而未受管理的程式碼係指服務的 GUID 來。  
  
- 當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage 的載入，就會傳遞服務提供者至 VSPackage 的 VSPackage 的存取權給予全域服務。 這稱為 「 地點 」 VSPackage。  
  
- Vspackage 可以是服務提供者所建立的物件。 例如，表單可能會傳送色彩服務的要求至其的框架，可能會傳遞要求[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
- 受管理的物件深度巢狀，或未設置，可能會呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>全域服務的直接存取。   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>使用 GetGlobalService  
  
有時候您可能需要從 工具視窗取得服務或控制未設置，否則就不知道您想要的服務的服務提供者已決定位置的容器。 比方說，您可能要從控制項內的活動記錄檔寫入。 如需有關這些和其他案例的詳細資訊，請參閱 <<c0> [ 如何： 疑難排解服務](../../extensibility/how-to-troubleshoot-services.md)。  
  
您可以取得大部分的 Visual Studio 服務藉由呼叫靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 需要在快取的服務上設置會初始化任何 VSPackage 衍生自封裝第一次的提供者。 您必須保證，這種情況成立，否則備妥以空值的服務。  
  
幸運的是，<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>適用於大部分的情況。  
  
-   如果 VSPackage 提供另一個 VSPackage 才知道的服務，服務要求 VSPackage 設置之前 VSPackage 提供已載入該服務。  
  
-   如果 VSPackage 建立工具視窗時，建立工具視窗之前設置 VSPackage。  
  
-   如果控制項容器由建立 VSPackage 的工具視窗，在建立控制項容器之前設置 VSPackage。  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>若要取得的工具視窗或控制項的容器內的服務  
  
-   插入此程式碼中建構函式、 工具視窗或控制項容器：  
  
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
    
    此程式碼會取得 SVsActivityLog 服務，並將它轉換成 IVsActivityLog 介面，可用來寫入活動記錄檔。 如需範例，請參閱[如何： 使用活動記錄](../../extensibility/how-to-use-the-activity-log.md)。  
  
## <a name="see-also"></a>另請參閱  
 [可用服務清單](../../extensibility/internals/list-of-available-services.md)   
 [使用和提供服務](../../extensibility/using-and-providing-services.md)   
 [轉型和類型轉換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [轉型](/cpp/cpp/casting)