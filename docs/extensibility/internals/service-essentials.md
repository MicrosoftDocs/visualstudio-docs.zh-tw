---
title: "服務 Essentials |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 0b78b5f9bf1fb6d9c92657b99e6d21b58cab2728
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="service-essentials"></a>服務的基本資訊
服務是兩個 Vspackage 之間的合約。 一個 VSPackage 提供一組特定的另一個 VSPackage 也可以使用的介面。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本身是提供服務給其他 Vspackage 的 Vspackage 集合。  
  
 例如，您可以使用 SVsActivityLog 服務以取得 IVsActivityLog 介面，可用來寫入活動記錄檔。 如需詳細資訊，請參閱[How to： 使用活動記錄檔](../../extensibility/how-to-use-the-activity-log.md)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]也提供一些內建的服務未登錄。 Vspackage 可以藉由提供服務覆寫來取代內建或其他服務。 只有一個服務覆寫允許任何服務。  
  
 服務會有任何可搜尋性。 因此，您必須知道您想要使用，服務的服務識別項 (SID)，而且您必須知道它所提供的介面。 服務的參考文件提供這項資訊。  
  
-   服務提供者時，會呼叫提供服務的 Vspackage。  
  
-   其他 vspackage 所提供服務，稱為 「 全域服務 」。  
  
-   僅適用於 VSPackage 實作，或它會建立任何物件，稱為 「 本機服務的服務。  
  
-   取代內建的服務或其他封裝，提供服務的服務會呼叫服務覆寫。  
  
-   服務或服務覆寫，會視需要載入，它所提供的服務要求另一個 VSPackage 時，也就是載入的服務提供者。  
  
-   若要支援視需要載入，服務提供者註冊其全域服務與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱[How to： 提供服務](../../extensibility/how-to-provide-a-service.md)。  
  
-   取得服務之後，請使用[QueryInterface](/cpp/atl/queryinterface) (unmanaged 程式碼) 或轉型 （managed 程式碼） 以取得所需的介面，例如：  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    ```  
  
-   Managed 程式碼是指服務，方法是其類型，而 unmanaged 程式碼是指透過其 GUID 的服務。  
  
-   當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入的 VSPackage，就會傳遞服務提供者至全域服務讓 VSPackage 存取 VSPackage。 這被指 「 地點"VSPackage。  
  
-   Vspackage 可以是服務提供者所建立的物件。 表單，可能會將色彩服務的要求傳送至其框架，可能會傳遞要求[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   深度巢狀的或未設置完全受管理的物件可能會呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>全域服務直接存取。   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>使用 GetGlobalService  
  
有時候您可能需要從工具視窗取得服務或控制未設置，否則就不知道您想要的服務的服務提供者已決定位置的容器。 例如，您可以寫入活動記錄檔從控制項中。 如需有關這些和其他案例的詳細資訊，請參閱[如何： 疑難排解服務](../../extensibility/how-to-troubleshoot-services.md)。  
  
您可以藉由呼叫靜態取得大部分的 Visual Studio 服務<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>依賴設置上快取的服務提供者，它會初始化任何 VSPackage 衍生自封裝第一次。 您必須保證確認此條件符合時，否則先備妥，null 的服務。  
  
幸運的是，<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>運作正常，大部分的時間。  
  
-   如果 VSPackage 提供只有知道另一個 VSPackage 的服務，服務要求 VSPackage 設置之前 VSPackage 提供已載入該服務。  
  
-   如果 VSPackage 建立工具視窗，就會建立工具視窗之前設置 VSPackage。  
  
-   如果建立 VSPackage 的工具視窗所裝載的控制項容器，VSPackage 設置之前建立控制項的容器。  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>若要取得從工具視窗或控制項容器內的服務  
  
-   建構函式、 工具視窗或控制項容器中插入這個程式碼：  
  
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
    
    這段程式碼會取得 SVsActivityLog 服務，並將其轉換成 IVsActivityLog 介面，可用來寫入活動記錄檔。 如需範例，請參閱[How to： 使用活動記錄檔](../../extensibility/how-to-use-the-activity-log.md)。  
  
## <a name="see-also"></a>另請參閱  
 [可用服務清單](../../extensibility/internals/list-of-available-services.md)   
 [使用並提供服務](../../extensibility/using-and-providing-services.md)   
 [轉型和類型轉換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [轉型](/cpp/cpp/casting)
