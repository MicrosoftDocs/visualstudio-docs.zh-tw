---
title: 自訂使用者介面 (原始檔控制 VSPackage) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7ae9333fd0e003bae6c823f7ae778dfc4b3770c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041200"
---
# <a name="custom-user-interface-source-control-vspackage"></a>自訂使用者介面 （原始檔控制 VSPackage）
VSPackage 會宣告它的功能表項目和其預設狀態，透過 Visual Studio 命令資料表 (*.vsct*) 檔案。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 會顯示在其預設狀態中的功能表項目直到載入 VSPackage。 接著，<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼叫方法來啟用或停用功能表項目。  
  
 VSPackage 可以設定登錄機碼，以便根據命令使用者介面 (UI) 內容可以自動載入 VSPackage，雖然通常原始檔控制 VSPackage 應而不只切換到特定的 UI 內容，是視需要載入。 如需詳細資訊**AutoLoadPackages**登錄機碼，請參閱[管理 Vspackage](../../extensibility/managing-vspackages.md)。  
  
## <a name="vspackage-ui"></a>VSPackage UI  
 原始檔控制套件實作為 VSPackage，而且不會使用從任何 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 每個原始檔控制 VSPackage 必須指定它自己的 UI 項目，例如功能表項目、 功能表群組中，工具視窗、 工具列和任何必要的使用者介面選項的特定設定原始檔控制 VSPackage。 靜態或動態方式，就可以啟用這些 UI 項目。 靜態的 UI 項目會定義於 *.vsct*檔案，並會顯示是否或未載入 VSPackage。 動態 UI 元素，例如可能會根據特定命令 UI 內容，顯示<xref:EnvDTE.Constants.vsContextNoSolution>，或呼叫的結果<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。 延遲載入 Vspackage 的策略符合動態的 UI 項目的可見性。  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>在 原始檔控制 Vspackage 的 UI 條件約束  
 因為無法從 IDE 中移除原始檔控制 VSPackage，會在載入之後，VSPackage 必須能夠進入非作用中狀態。 當 VSPackage 會收到通知，就無法再使用中時，VSPackage 會停用其 UI，並忽略任何外部的 IDE 互動。 VSPackage 實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>VSPackage 不在使用中時，方法應該隱藏命令。  
  
 VSPackage 必須實作每個原始檔控制`IVsSccProvider`介面。 在介面中，兩種方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>，VSPackage 必須實作。  
  
 原始檔控制 VSPackage 可能已訂閱各種 IDE 事件，由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>， <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>，依此類推。 此外，VSPackage 可能未實作已啟用登錄的回呼介面，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>。 這些介面必須全部忽略非使用中時。  
  
 下列清單會顯示受到原始檔控制 VSPackage 的作用中狀態的介面：  
  
- 追蹤專案的文件事件。  
  
- 解決方案的事件。  
  
- 解決方案的持續性介面。 當非作用中時，套件應該寫入 *.sln*並 *.suo*檔案。  
  
- 屬性擴充項。  
  
  所需<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>，就也與原始檔控制相關聯的任何選擇性介面不會呼叫原始檔控制 VSPackage 非作用中時。  
  
  當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 啟動時，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令 UI 內容設定為目前的預設原始檔控制 VSPackage 識別碼的識別碼 這會導致靜態的作用中的原始檔控制 VSPackage，才會出現在 IDE 中，而不用實際載入 VSPackage 的 UI。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 暫停向 vspackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>它可讓 VSPackage 的任何呼叫之前。  
  
  下表描述的特定詳細資料，關於如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 會隱藏不同的 UI 項目。  
  
| UI 項目 | 描述 |
| - | - |
| 功能表與工具列 | 原始檔控制套件必須將初始的功能表和工具列可見性狀態設定為中的原始檔控制封裝識別碼[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)一節 *.vsct*檔案。 這可讓[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 載入 VSPackage 和呼叫的實作不正確設定功能表項目的狀態<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。 |
| 工具視窗 | 原始檔控制 VSPackage 會隱藏進行非作用中時，它擁有任何工具視窗。 |
| 原始檔控制 VSPackage 特有選項頁面 | 登錄機碼**HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts**可讓 VSPackage 設定中，它需要其顯示的 [選項] 頁面的內容。 此機碼下的登錄項目，就必須建立使用服務識別碼 (SID) 的原始檔控制服務，並將它指派 1 的 DWORD 值。 UI 事件發生時的內容中原始檔控制 VSPackage 註冊，就會呼叫 VSPackage，如果是作用中。 |
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)