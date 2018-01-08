---
title: "使用並提供服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: "41"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fbba5070af77e1509ed3b3840a2045ae0f2c12b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-and-providing-services"></a>使用並提供服務
服務是兩個 Vspackage 之間的合約。 一個 VSPackage 提供一組特定的另一個 VSPackage 也可以使用的介面。 例如，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]提供<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>服務傳送至任何 VSPackage 它載入。 此服務會提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面，可用來寫入活動記錄檔。 如需詳細資訊，請參閱[How to： 使用活動記錄檔](../extensibility/how-to-use-the-activity-log.md)。  
  
 Vspackage 可以提供自己所使用的服務<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>介面...  
  
 Visual Studio 提供重要服務，如下所示：  
  
|IDE 服務|描述|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|提供 ide 的存取服務處理使用 Vspackage 和登錄基本功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本視窗化與 UI 相關的功能，在 IDE 中，例如建立工具和文件視窗的功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供基本方案相關的功能，例如列舉專案、 建立新的專案，以及監視專案的變更的能力。|  
  
## <a name="in-this-section"></a>本節內容  
 [服務的基本資訊](../extensibility/internals/service-essentials.md)  
 提供 Visual Studio 服務的重要元素。  
  
 [如何︰取得服務](../extensibility/how-to-get-a-service.md)  
 討論如何要求 （使用） 服務。  
  
 [如何︰提供服務](../extensibility/how-to-provide-a-service.md)  
 討論如何提供服務。  
  
 [如何︰提供非同步的 Visual Studio 服務](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 討論如何提供非同步服務。  
  
 [如何：針對服務進行疑難排解](../extensibility/how-to-troubleshoot-services.md)  
 討論常見的問題，並呈現這些解決方案。  
  
## <a name="related-sections"></a>相關章節  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)