---
title: 使用和提供服務 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f58e29797e9a7760aa0f48c68868199f51b3c92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177432"
---
# <a name="using-and-providing-services"></a>使用和提供服務
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

服務是兩個 Vspackage 之間的合約。 其中一個 VSPackage 會提供一組特定的介面，供另一個要取用的 VSPackage 使用。 例如， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 會將服務提供給它所載入的任何 VSPackage。 此服務提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 介面，可用來寫入活動記錄。 如需詳細資訊，請參閱 [如何：使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。  
  
 Vspackage 可以使用介面來提供自己的服務。 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>  
  
 Visual Studio 提供重要的服務，如下所示：  
  
|IDE 服務|描述|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|提供對處理基本功能、Vspackage 和登錄的 IDE 服務的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|在 IDE 中提供基本視窗和 UI 相關的功能，例如建立工具和文件視窗的能力。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供與解決方案相關的基本功能，例如列舉專案、建立新專案及監視專案變更的能力。|  
  
## <a name="in-this-section"></a>本節內容  
 [服務的基本資訊](../extensibility/internals/service-essentials.md)  
 提供 Visual Studio 服務的重要元素。  
  
 [如何︰取得服務](../extensibility/how-to-get-a-service.md)  
 討論如何要求 (使用) 服務。  
  
 [如何︰提供服務](../extensibility/how-to-provide-a-service.md)  
 討論如何提供服務。  
  
 [如何︰提供非同步的 Visual Studio 服務](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 討論如何提供非同步服務。  
  
 [如何：針對服務進行疑難排解](../extensibility/how-to-troubleshoot-services.md)  
 討論常見的問題，並為其提供解決方案。  
  
## <a name="related-sections"></a>相關章節  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
