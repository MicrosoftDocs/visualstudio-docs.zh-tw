---
title: 使用和提供服務 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: facf0bb9968e3ffbc9a68eb8eee906f300eb1859
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500392"
---
# <a name="using-and-providing-services"></a>使用和提供服務
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[使用和提供服務](https://docs.microsoft.com/visualstudio/extensibility/using-and-providing-services)。  
  
服務是兩個的 Vspackage 之間的合約。 一個 VSPackage 提供一組特定的介面使用的另一個 VSPackage。 例如，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]提供<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>維護任何 vspackage 載入。 此服務會提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面，可用來寫入活動記錄檔。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。  
  
 Vspackage 可以提供自己所使用的服務<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>介面...  
  
 Visual Studio 會提供重要的服務，如下所示：  
  
|IDE 服務|描述|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|提供存取 IDE 使用 Vspackage 和登錄基本功能服務處理。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本視窗化 」 與 UI 相關的功能，在 IDE 中，例如能夠建立工具和文件視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供基本方案相關的功能，例如能夠列舉專案、 建立新的專案，並監視專案的變更。|  
  
## <a name="in-this-section"></a>本節內容  
 [服務的基本資訊](../extensibility/internals/service-essentials.md)  
 提供 Visual Studio 服務的重要元素。  
  
 [如何︰取得服務](../extensibility/how-to-get-a-service.md)  
 討論如何要求 （取用） 服務。  
  
 [如何︰提供服務](../extensibility/how-to-provide-a-service.md)  
 討論如何提供服務。  
  
 [如何︰提供非同步的 Visual Studio 服務](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 討論如何提供非同步的服務。  
  
 [如何：針對服務進行疑難排解](../extensibility/how-to-troubleshoot-services.md)  
 討論常見的問題，並提供給他們的解決方案。  
  
## <a name="related-sections"></a>相關章節  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

