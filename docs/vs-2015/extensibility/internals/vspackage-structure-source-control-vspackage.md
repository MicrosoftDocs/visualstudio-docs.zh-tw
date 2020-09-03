---
title: VSPackage 結構 (原始檔控制 VSPackage) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08bb0a296daca0de1c02b905a75fb10ce05f254e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206001"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 結構 (原始檔控制 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

原始檔控制封裝 SDK 提供建立 VSPackage 的指導方針，可讓原始檔控制實施者將其原始檔控制功能與環境進行整合 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 VSPackage 是一種 COM 元件，通常是由 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 整合式開發環境視需要載入 (IDE) 根據封裝在其登錄專案中所公告的服務。 每個 VSPackage 都必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 。 VSPackage 通常會取用 IDE 所提供的服務 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，並這個本身的一些服務。  
  
 VSPackage 會宣告其功能表項目，並透過 .vsct 檔案建立預設專案狀態。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE 會顯示處於此狀態的功能表項目，直到載入 VSPackage 為止。 接著，會呼叫方法的 VSPackage 執行， <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 以啟用或停用功能表項目。  
  
## <a name="source-control-package-characteristics"></a>原始檔控制封裝特性  
 原始檔控制 VSPackage 已緊密整合至 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 VSPackage 語義包括：  
  
- 藉由 VSPackage 介面 (介面所執行的介面 `IVsPackage`)   
  
- UI 命令執行 ( .vsct 檔案和介面的執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>)   
  
- 使用註冊 VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
  原始檔控制 VSPackage 必須與下列其他 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 實體通訊：  
  
- 專案  
  
- 編輯器  
  
- 方案  
  
- Windows  
  
- 執行中的檔資料表  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>可能耗用的 Visual Studio 環境服務  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider 服務  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>執行並呼叫 VSIP 介面  
 原始檔控制封裝是 VSPackage，因此可以直接與向註冊的其他 Vspackage 互動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 為了提供原始檔控制功能的完整廣度，原始檔控制 VSPackage 可以處理專案或 shell 所提供的介面。  
  
 中的每個專案 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 都必須執行， <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> 才能辨識為 IDE 內的專案 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 不過，這個介面並非專門用於原始檔控制。 預期在原始檔控制下的專案會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 。 原始檔控制 VSPackage 會使用此介面來查詢專案的內容，並提供它的圖像和系結資訊 (所需的資訊，以建立伺服器位置與原始檔控制) 之專案的磁片位置之間的連接。  
  
 原始檔控制 VSPackage 會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> ，進而允許專案自行註冊原始檔控制，並取得其狀態圖像。  
  
 如需原始檔控制 VSPackage 必須考慮的介面完整清單，請參閱 [相關的服務和介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設計項目](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [相關的服務和介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
