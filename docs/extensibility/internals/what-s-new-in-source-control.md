---
title: 什麼&#39;s 原始檔控制的新功能 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b46730ab1acac6605af2e1ff1c418dbe8c886406
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-source-control"></a>什麼&#39;s 原始檔控制的新功能
在[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]您可以藉由實作 VSPackage 的原始檔控制提供緊密整合式原始檔控制方案。 本節描述原始檔控制 Vspackage 的功能，並提供實作步驟的概觀。  
  
## <a name="the-source-control-vspackage"></a>原始檔控制 VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援兩種類型的原始檔控制的解決方案。 在所有版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您仍然可以整合原始檔控制外掛程式 API 為基礎外掛程式。 您也可以建立 VSPackage 的原始檔控制提供深層整合[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]適用於需要高層級的複雜度，以及自主的原始檔控制方案的路徑。  
  
 VSPackage 可以加入幾乎任何類型的功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 原始檔控制 VSPackage 提供的完整原始檔控制功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，從 UI 呈現給使用者與原始檔控制系統的後端通訊。  
  
 實作 VSPackage 的原始檔控制需要 「 所有或執行任何動作 」 的策略。 原始檔控制 VSPackage 的建立者必須投入大量的心力實作幾個原始檔控制的介面和新的 UI 項目 （對話方塊、 功能表和工具列） 來涵蓋整個原始檔控制功能，以及介面成功整合所需的任何封裝[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 下列步驟提供所需實作原始檔控制封裝的一般概觀。 如需詳細資訊，請參閱[建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。  
  
1.  建立 proffers 私用的原始檔控制服務的 VSPackage。  
  
2.  在原始檔控制相關服務所提供的實作介面[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](例如，<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>介面)。  
  
3.  註冊您的原始檔控制 VSPackage。  
  
4.  實作所有的原始檔控制使用者介面，包括功能表項目、 對話方塊、 工具列和操作功能表。  
  
5.  為作用中，VSPackage 必須處理時，所有原始檔控制相關事件會傳遞至您的原始檔控制 VSackage。  
  
6.  您的原始檔控制 VSPackage 必須接聽事件，例如實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>介面以及追蹤專案文件 (TPD) 事件 (由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>介面)，並採取必要動作。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [概觀](../../extensibility/internals/source-control-integration-overview.md)   
 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)