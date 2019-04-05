---
title: HOW TO：使用 GetGlobalService |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 0161b3e44b44567166a337d94101778074561e80
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "58941461"
---
# <a name="how-to-use-getglobalservice"></a>HOW TO：使用 GetGlobalService
有時候您可能需要從 工具視窗取得服務或控制未設置，否則就不知道您想要的服務的服務提供者已決定位置的容器。 比方說，您可能要從控制項內的活動記錄檔寫入。 如需有關這些和其他案例的詳細資訊，請參閱[How to:疑難排解服務](../extensibility/how-to-troubleshoot-services.md)。  
  
 您可以取得大部分[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]服務，藉由呼叫靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 會初始化任何 VSPackage 衍生自第一次的快取的服務提供者會依賴<xref:Microsoft.VisualStudio.Shell.Package>設置。 您必須保證，這種情況成立，否則備妥以空值的服務。  
  
 幸運的是，<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>適用於大部分的情況。  
  
-   如果 VSPackage 提供另一個 VSPackage 才知道的服務，服務要求 VSPackage 設置之前 VSPackage 提供已載入該服務。  
  
-   如果 VSPackage 建立工具視窗時，建立工具視窗之前設置 VSPackage。  
  
-   如果控制項容器由建立 VSPackage 的工具視窗，在建立控制項容器之前設置 VSPackage。  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>若要取得的工具視窗或控制項的容器內的服務  
  
-   插入此程式碼中建構函式、 工具視窗或控制項容器：  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     此程式碼會取得 SVsActivityLog 服務，並將它轉換成<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面，可用來寫入活動記錄檔。 如需範例，請參閱[如何：使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：針對服務進行疑難排解](../extensibility/how-to-troubleshoot-services.md)   
 [使用和提供服務](../extensibility/using-and-providing-services.md)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)