---
title: 如何：使用 GetGlobalService |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62948178"
---
# <a name="how-to-use-getglobalservice"></a>如何：使用 GetGlobalService
有時，您可能需要從尚未放置的工具視窗或控制項容器取得服務，或使用其他服務提供者不知道您想要的服務。 例如，您可能想要從控制項內寫入活動記錄。 如需有關這些案例和其他案例的詳細資訊，請參閱 [如何：針對服務進行疑難排解](../extensibility/how-to-troubleshoot-services.md)。  
  
 您可以藉 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 由呼叫靜態方法來取得大部分的服務 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 依賴快取的服務提供者，其會在第一次衍生自的任何 VSPackage 時初始化 <xref:Microsoft.VisualStudio.Shell.Package> 。 您必須保證符合此條件，或為 null 服務做好準備。  
  
 幸運的 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 是，大部分的時間都能正常運作。  
  
- 如果 VSPackage 提供僅知道另一個 VSPackage 的服務，則要求服務的 VSPackage 會在載入服務的 VSPackage 之前放置。  
  
- 如果工具視窗是由 VSPackage 所建立，則 VSPackage 會在建立工具視窗之前放置。  
  
- 如果控制項容器是由 VSPackage 所建立的工具視窗所主控，則 VSPackage 會在建立控制項容器之前放置。  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>從工具視窗或控制項容器內取得服務  
  
- 在 [函式]、[工具視窗] 或 [控制項容器] 中插入此程式碼：  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     這段程式碼會取得 SVsActivityLog 服務，並將它轉換成 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 介面，可用來寫入活動記錄。 如需範例，請參閱 [如何：使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：針對服務進行疑難排解](../extensibility/how-to-troubleshoot-services.md)   
 [使用和提供服務](../extensibility/using-and-providing-services.md)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)