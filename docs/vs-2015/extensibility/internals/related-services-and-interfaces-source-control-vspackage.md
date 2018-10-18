---
title: 相關的服務和介面 (原始檔控制 VSPackage) |Microsoft Docs
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
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 05ee2b91204c9dca07f59e088ab07db7ee9ceaca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210128"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>相關的服務和介面 (原始檔控制 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

此區段會列出所有的原始檔控制 VSPackage 相關的介面，在[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]。 原始檔控制 VSPackage 實作這些介面部分，並使用其他人來完成原始檔控制工作。  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>原始檔控制 Vspackage 和所實作的介面  
 下列介面詳述於[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]，和原始檔控制 VSPackage 實作根據其所需的功能集的子集。 某些介面中會標示為需要，而且必須由每個原始檔控制 VSPackage 實作。  
  
 封裝不會實作，這些介面[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]提供的預設實作。 請注意，預設實作專為不註冊任何 VSPackage 的情況下並沒有任何專案被控制。 適當撰寫的原始檔控制 VSPackage 實作所有必要的介面，而不是讓這些介面的預設實作。  
  
 原始檔控制 VSPackage 必須實作封裝部分或所有下列介面的私用服務。  
  
 介面包括：  
  
-   必要： 適當的實體 （原始檔控制 VSPackage，原始檔控制虛設常式，專案） 必須實作介面。  
  
-   建議： 實體應該實作這個介面;否則，原始檔控制功能可能有限。  
  
-   選擇性： 實體可以實作這個介面，以提供更豐富的功能集。  
  
|介面|用途|藉由將|實作？|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|編輯器呼叫這個介面之前修改或儲存檔案。 原始檔控制 VSPackage 可以簽出檔案，或拒絕作業，如果簽出失敗。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|這個介面會提供基本的原始檔控制功能，針對專案，例如註冊和取消註冊與原始檔控制的專案和基本來源控制圖像 （glyph） 提供支援。|原始檔控制 VSPackage|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|這個介面取自<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>使用<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>函式，或只轉型物件，實作`IVsHierarchy`至`IVsSccProject2`。 它用來取得專案中的原始檔控制下的檔案或通知目前的原始檔控制狀態或位置的專案。|專案|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|整合模組會使用此介面來設定目前作用中的 VSPackage。|原始檔控制 VSPackage|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|這個介面是以訂用帳戶模型為基礎。 任何的 VSPackage 可以發出信號，它想要接收的文件事件，以及建議的殼層，即將發生的事件。 它會實作，而且由[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，這接著會將事件傳遞實作`IVsTrackProjectDocumentsEvents2`vspackage。|原始檔控制虛設常式|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|這個介面會提供批次處理、 同步處理的讀取/寫入作業，以及進階`OnQueryAddFiles`方法。|原始檔控制虛設常式|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**方案總管 中**專案呼叫這個介面，當新檔案新增至專案，或重新命名或從專案刪除檔案和資料夾。 原始檔控制 VSPackage 可以簽出專案檔，或取消作業。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**方案總管 中**專案呼叫以回應對 IVstrackProjectDocuments3 介面的方法呼叫這個介面。 原始檔控制 VSPackage 可以追蹤批次的作業，同步處理的讀寫作業，並使用更進階`OnQueryAddFiles`方法。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|這個介面提供登錄的管理支援 Web 專案。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|此介面用來擷取工具提示的原始檔控制專案中的檔案。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|這個介面提供的命名空間延伸模組支援。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage 會使用這個介面整合到命名空間延伸模組**的新**，**開放**，或**儲存**對話方塊。 因此，專案會自動新增至原始檔控制在建立後，或加入原始檔控制時儲存作業就會生效。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage 會使用這個介面定義為原始檔控制圖像 （glyph） 節點中的其他字符**方案總管 中**。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**新增**Web 專案 對話方塊中會使用此介面。 它提供瀏覽的原始檔控制位置和開啟 Web 專案，在該位置的原始檔控制儲存機制中先前新增的方法。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|這個介面提供非同步 （背景） 載入，從原始檔控制專案的支援。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|這個介面可讓專案，以查看所起始的非同步載入進度<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>。|專案|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|此介面可讓查詢使用中的原始檔控制 VSPackage IDE。 IDE 會查詢有意義，即使不是在 VSPackage 註冊任何使用中的原始檔控制的原始檔控制設定的值。 這個介面是實作，而且由[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。|原始檔控制虛設常式|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|這個介面用於註冊的原始檔控制 VSPackage。|原始檔控制虛設常式|必要|  
|<xref:EnvDTE.SourceControl>|這個介面用於自動化。 因此，它會公開可執行而不會顯示任何 UI 函式。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|此介面用來儲存原始檔控制設定方案 (.sln) 檔案中。 設定包括的原始檔控制位置和原始檔控制狀態旗標。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|此介面用來儲存方案選項 (.suo) 檔案中的原始檔控制設定。 這可能包括使用者專屬的原始檔控制設定，例如目前使用者的登錄位置。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|若要執行作業，例如簽入之前關閉方案，或開啟專案時，取得新的檔案從原始檔控制的專案檔，這個介面用來監視事件。|原始檔控制 VSPackage|建議|  
  
## <a name="see-also"></a>另請參閱  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)

