---
title: 原始檔控制的新功能
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31b55c57f47f25814eff24f13bcf91408468d0f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200945"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>Visual Studio 2015 中原始檔控制的新功能&#39;

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在中 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] ，您可以藉由執行原始檔控制 VSPackage，提供更緊密整合的原始檔控制解決方案。 本節說明原始檔控制 Vspackage 的功能，並提供執行步驟的總覽。  
  
## <a name="the-source-control-vspackage"></a>原始檔控制 VSPackage  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 支援兩種類型的原始檔控制解決方案。 在所有版本的中 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，您仍然可以整合原始檔控制外掛程式 API 型外掛程式。 您也可以建立原始檔控制的 VSPackage，以提供 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 適用于原始檔控制解決方案的深層整合路徑，這些解決方案需要高層級的複雜和自主性。  
  
 VSPackage 可將幾乎任何類型的功能加入至 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 原始檔控制 VSPackage 提供的完整原始檔控制功能 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，從向使用者呈現的 UI 到與原始檔控制系統的後端通訊。  
  
 執行原始檔控制 VSPackage 需要「全部」或「無」策略。 原始檔控制 VSPackage 的建立者必須投資大量的工作，以實行一些原始檔控制介面和新的 UI 元素， (對話方塊、功能表和工具列) 來涵蓋整個原始檔控制功能，以及任何封裝成功整合所需的介面 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 下列步驟提供執行原始檔控制封裝所需功能的一般總覽。 如需詳細資訊，請參閱 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。  
  
1. 建立這個私用原始檔控制服務的 VSPackage。  
  
2. 在 (推出的原始檔控制相關服務中執行介面 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，例如， <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> 介面) 。  
  
3. 註冊您的原始檔控制 VSPackage。  
  
4. 執行所有原始檔控制 UI，包括功能表項目、對話方塊、工具列和快顯功能表。  
  
5. 所有原始檔控制相關事件都會傳遞至您的原始檔控制 VSackage （當其為使用中時），而且必須由您的 VSPackage 處理。  
  
6. 您的原始檔控制 VSPackage 必須接聽事件（例如，執行介面的事件），以及 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> 追蹤專案檔案 (TPD 由) 介面所執行的) 事件 (<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 並採取必要動作。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [概述](../../extensibility/internals/source-control-integration-overview.md)   
 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
