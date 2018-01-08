---
title: "VSPackage 結構 (來源控制 VSPackage) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 168aa0f7b93d20afaa30924dc17f05e0cac465bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 結構 (來源控制 VSPackage)
原始檔控制封裝 SDK 提供的指導方針建立 VSPackage，允許將他或她原始檔控制功能與整合原始檔控制實施者[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境。 VSPackage 是 COM 元件，通常會視需要而載入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 為基礎的服務，其登錄項目中的封裝會通告。 每個 VSPackage 必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。 VSPackage 通常會使用所提供的服務[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 和 proffers 自己的某些服務。  
  
 VSPackage 會宣告其功能表項目，並建立透過.vsct 檔的預設項目狀態。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 會顯示功能表項目處於此狀態直到載入 VSPackage。 接著，VSPackage 實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼叫方法來啟用或停用功能表項目。  
  
## <a name="source-control-package-characteristics"></a>原始檔控制封裝特性  
 VSPackage 緊密整合到原始檔控制[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 VSPackage 語意包括：  
  
-   必定正在 VSPackage 實作介面 (`IVsPackage`介面)  
  
-   UI 命令實作 (.vsct 檔與實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面)  
  
-   使用 VSPackage 的登錄[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 原始檔控制 VSPackage 必須與其進行通訊這些其他[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]實體：  
  
-   專案  
  
-   編輯器  
  
-   方案  
  
-   Windows  
  
-   執行中的文件表格  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>可以使用的 visual Studio 環境服務  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider 服務  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP 介面實作，而且呼叫  
 原始檔控制封裝是 VSPackage，以及因此它可以直接互動會向其他 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 為了提供全面性的原始檔控制功能，原始檔控制 VSPackage 可以處理專案或殼層所提供的介面。  
  
 在每個專案[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>中的專案被視為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。 不過，這個介面不特製化不足以原始檔控制。 必須是來源底下的專案控制實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>。 若要查詢其內容的專案，並提供它圖像 （glyph） 和繫結資訊 （所需的資訊來建立連接的伺服器位置與專案下的磁碟位置之間的原始檔控制 VSPackage 便會使用這個介面原始檔控制）。  
  
 實作 VSPackage 的原始檔控制<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>，依次讓專案，以自行註冊為原始檔控制和擷取其狀態的圖像 （glyph）。  
  
 原始檔控制 VSPackage 必須考量的介面的完整清單，請參閱[相關服務與介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)。  
  
## <a name="see-also"></a>請參閱  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [相關的服務與介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)