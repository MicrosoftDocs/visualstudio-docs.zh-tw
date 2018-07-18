---
title: 自訂使用者介面 (原始檔控制 VSPackage) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebd2361e94e9b1430f5bac99f2e71dc53a02ebf1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131876"
---
# <a name="custom-user-interface-source-control-vspackage"></a>自訂使用者介面 (原始檔控制 VSPackage)
VSPackage 透過 Visual Studio 命令表 (.vsct) 檔案中宣告它的功能表項目和其預設狀態。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 會顯示在其預設狀態中的功能表項目直到載入 VSPackage。 接著，<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼叫方法來啟用或停用功能表項目。  
  
 VSPackage 可以設定登錄機碼，讓 VSPackage 可以根據命令使用者介面 (UI) 內容自動載入，而不是剛切換到特定 UI 內容視雖然原始檔控制通常應該載入 VSPackage。 如需 AutoLoadPackages 登錄機碼的詳細資訊，請參閱[管理 Vspackage](../../extensibility/managing-vspackages.md)。  
  
## <a name="vspackage-ui"></a>VSPackage UI  
 原始檔控制封裝實作為 VSPackage，而且不會使用從任何 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 每個原始檔控制 VSPackage 必須指定它自己的 UI 項目，例如功能表項目、 功能表群組、 工具視窗、 工具列和任何必要的 UI 選項的特定設定原始檔控制 VSPackage。 靜態或動態，您可以啟用這些 UI 項目。 靜態的 UI 項目.vsct 檔案中所定義，或未載入 VSPackage 是否會顯示。 動態 UI 元素，例如可能會顯示特定命令 UI 內容中，根據<xref:EnvDTE.Constants.vsContextNoSolution>，或呼叫導致<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。 動態 UI 項目可見性符合延遲載入 Vspackage 的策略。  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>原始檔控制 Vspackage UI 條件約束  
 因為無法從 IDE 中移除原始檔控制 VSPackage，載入後再，VSPackage 必須能夠進入非作用中狀態。 當 VSPackage 收到通知，就無法再使用中時，VSPackage 會停用其 UI，並忽略任何外部的 IDE 互動。 VSPackage 實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>VSPackage 不在作用中時，方法應該隱藏命令。  
  
 VSPackage 必須實作每個原始檔控制`IVsSccProvider`介面。 在介面中，兩個方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>，VSPackage 必須實作。  
  
 VSPackage 可能已訂閱各種 IDE 事件，由原始檔控制<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>， <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>，依此類推。 此外，VSPackage 可能未實作登錄啟用回呼介面，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>。 這些必須全部忽略非使用中時。  
  
 下列清單會顯示受到原始檔控制 VSPackage 的使用中狀態的介面：  
  
-   追蹤專案文件的事件。  
  
-   方案的事件。  
  
-   解決方案的持續性介面。 非使用中，當封裝不應該寫入.sln 和.suo 的檔案。  
  
-   屬性擴充項。  
  
 所需<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>，和也與原始檔控制相關聯的任何選擇性介面不會呼叫非作用中的原始檔控制 VSPackage 時。  
  
 當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 啟動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令 UI 內容設定為目前的預設原始檔控制 VSPackage 識別碼的識別碼 這會導致靜態 UI 的使用中的原始檔控制無法顯示在 IDE 中實際載入 VSPackage 的 VSPackage。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 向註冊 vspackage 暫停[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>exports VSPackage 的任何呼叫之前。  
  
 下表描述的特定詳細資料，關於如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 會隱藏不同的 UI 項目。  
  
|UI 項目|描述|  
|-------------|-----------------|  
|功能表與工具列|原始檔控制封裝必須設定初始的功能表和工具列可見性狀態中的原始檔控制封裝識別碼[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .vsct 檔的區段。 這可讓[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]適當地設定功能表項目的狀態，而不載入 VSPackage 和呼叫的實作 IDE<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。|  
|工具視窗|原始檔控制 VSPackage 隱藏變成非作用中時，它擁有任何工具視窗。|  
|原始檔控制特定的 VSPackage 選項頁|登錄機碼 HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts 可讓 VSPackage 設定中需要顯示其選項頁面的內容。 此機碼下的登錄項目，就必須建立使用識別碼 (SID) 的原始檔控制服務的服務，並將其指派為 1 的 DWORD 值。 UI 事件發生時的內容中向註冊 VSPackage 的原始檔控制，則會呼叫 VSPackage，是否在作用中。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [管理 VSPackage](../../extensibility/managing-vspackages.md)