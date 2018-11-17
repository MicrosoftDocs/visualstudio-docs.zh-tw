---
title: VSPackage 結構 (原始檔控制 VSPackage) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6eaad545d1c1b3fe96ecbad3a88cc7636b777a54
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737985"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 結構 (原始檔控制 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

原始檔控制封裝 SDK 提供的指導方針建立 VSPackage，允許將他或她原始檔控制功能與原始檔控制實施者[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]環境。 VSPackage 是 COM 元件，通常會視需要而載入[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]及其登錄項目中的封裝會通告服務為基礎的整合式的開發環境 (IDE)。 每個 VSPackage 必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。 VSPackage 通常會使用所提供的服務[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE 並提供其本身的某些服務。  
  
 VSPackage 會宣告其功能表項目，並建立透過.vsct 檔的預設項目狀態。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 會顯示在此狀態的功能表項目直到載入 VSPackage。 接著，VSPackage 實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼叫方法來啟用或停用功能表項目。  
  
## <a name="source-control-package-characteristics"></a>原始檔控制封裝特性  
 原始檔控制 VSPackage 深度整合到[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
 VSPackage 語意包括：  
  
- 因為 VSPackage 實作介面 (`IVsPackage`介面)  
  
- UI 命令實作 (.vsct 檔並實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面)  
  
- 使用 VSPackage 註冊[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
  原始檔控制 VSPackage 必須與這些其他[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]實體：  
  
- 專案  
  
- 編輯器  
  
- 方案  
  
- Windows  
  
- 執行中的文件表格  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio 環境服務使用  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider 服務  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP 介面實作，並呼叫  
 原始檔控制套件的 VSPackage，且因此可直接與其他已向的 Vspackage 中互動[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 為了提供原始檔控制功能的完整範圍，原始檔控制 VSPackage 可以處理專案或殼層所提供的介面。  
  
 每個專案中的[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>中的專案被視為[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE。 不過，此介面不特製化足夠用於原始檔控制。 應該是來源底下的專案控制實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>。 這個介面是由原始檔控制 VSPackage 來查詢其內容的專案，並提供它圖像 （glyph） 和繫結資訊 （所需的資訊來建立的伺服器位置與專案下的磁碟位置之間的連線原始檔控制）。  
  
 原始檔控制 VSPackage 實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>，這可讓專案以註冊其本身的原始檔控制，並擷取其狀態的圖像 （glyph）。  
  
 原始檔控制 VSPackage 必須考量的介面的完整清單，請參閱 <<c0> [ 相關的服務與介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [相關的服務和介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

