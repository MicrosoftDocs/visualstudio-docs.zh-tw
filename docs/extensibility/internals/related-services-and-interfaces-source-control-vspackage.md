---
title: 相關的服務和介面 (原始檔控制 VSPackage) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f9e8e90fdda61524a9af107df452bc2b13cd90c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135348"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>相關的服務和介面 (原始檔控制 VSPackage)
此區段會列出所有的原始檔控制中的 VSPackage 相關介面[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。 原始檔控制 VSPackage 實作這些介面部分，並使用其他人來完成原始檔控制工作。  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>由和適用於原始檔控制的 Vspackage 實作的介面  
 下列介面詳述於[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，和原始檔控制 VSPackage 實作的子集它們根據其所需的功能集。 某些介面都會標示為需要，而且必須由每個原始檔控制 VSPackage 實作。  
  
 封裝未實作，這些介面[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供的預設實作。 請注意，預設實作針對案例沒有 VSPackage 註冊時並沒有任何專案被控制。 所有必要的介面，而不是離開這些介面的預設實作，可實作適當撰寫的原始檔控制 VSPackage。  
  
 原始檔控制 VSPackage 必須實作封裝部分或所有下列介面的私用服務。  
  
 介面是：  
  
-   必要： 適當的實體 （原始檔控制 VSPackage，原始檔控制虛設常式，專案） 必須實作的介面。  
  
-   建議使用： 實體應該實作這個介面。否則，原始檔控制功能可能會有所限制。  
  
-   選擇性： 實體可以實作這個介面可提供更豐富的功能集。  
  
|介面|用途|由實作|實作？|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|編輯器會呼叫這個介面修改或儲存檔案之前。 原始檔控制 VSPackage 可以簽出檔案，或如果簽出失敗，拒絕此作業。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|這個介面會提供基本的原始檔控制功能的專案中，例如註冊和取消登錄與原始檔控制專案和基本來源控制圖像 （glyph） 提供支援。|原始檔控制 VSPackage|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|這個介面取自<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>使用<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>函式，或直接轉型物件實作`IVsHierarchy`至`IVsSccProject2`。 它用來取得專案中的原始檔控制下的檔案或通知目前的原始檔控制狀態或位置的專案。|專案|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|整合模組會使用此介面來設定目前使用中的 VSPackage。|原始檔控制 VSPackage|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|這個介面根據訂閱模型。 任何 VSPackage 可以指示它要接收文件事件即將發生的事件通知的殼層。 實作，並由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，然後依序傳遞事件實作`IVsTrackProjectDocumentsEvents2`至 VSPackage。|原始檔控制虛設常式|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|這個介面會提供批次處理、 同步處理的讀取/寫入作業，以及進階`OnQueryAddFiles`方法。|原始檔控制虛設常式|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**方案總管 中**和專案的新檔案加入至專案，或重新命名或從專案刪除檔案和資料夾時，呼叫這個介面。 原始檔控制 VSPackage 可以簽出專案檔，或取消作業。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**方案總管 中**專案呼叫這個介面，以回應對 IVstrackProjectDocuments3 介面之方法的呼叫。 VSPackage 可以追蹤批次的作業，同步處理的原始檔控制讀取/寫入作業，並使用更進階`OnQueryAddFiles`方法。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|這個介面會提供針對 Web 專案登記的管理支援。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|這個介面用來擷取專案中的原始檔控制檔案的工具提示。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|這個介面提供延伸模組支援命名空間。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage 整合到命名空間擴充功能會使用這個介面**新增**，**開啟**，或**儲存**對話方塊。 因此，專案可以自動加入至原始檔控制建立時，或加入至原始檔控制時儲存作業就會生效。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage 會使用這個介面，以定義其他圖像 （glyph） 節點中的來源控制項圖像**方案總管 中**。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**新增**Web 專案 對話方塊會使用這個介面。 它提供瀏覽的原始檔控制位置和開啟 Web 專案之前加入原始檔控制儲存機制，在該位置中的方法。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|這個介面提供非同步 （背景） 載入，從原始檔控制專案的支援。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|這個介面可讓專案以觀察所起始的非同步載入的進度<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>。|專案|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|這個介面可讓查詢使用中的原始檔控制 VSPackage IDE。 IDE 會查詢不會有作用中來源控制註冊 VSPackage，即使有意義的原始檔控制設定的值。 這個介面會實作，並由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。|原始檔控制虛設常式|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|此介面用於註冊的原始檔控制 VSPackage。|原始檔控制虛設常式|必要|  
|<xref:EnvDTE.SourceControl>|在自動化中，會使用這個介面。 因此，它會公開可執行而不會顯示任何 UI 函式。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|這個介面用來儲存方案 (.sln) 檔案中原始檔控制設定。 設定包括原始檔控制位置和原始檔控制狀態旗標。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|這個介面用來儲存方案的選項 (.suo) 檔案中的原始檔控制設定。 這可能包括使用者專屬的原始檔控制設定，例如目前使用者的登錄位置。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|這個介面用來監視事件中，才能執行作業，例如簽入之前關閉方案，或開啟專案時，取得新的檔案從原始檔控制的專案檔案。|原始檔控制 VSPackage|建議|  
  
## <a name="see-also"></a>另請參閱  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)