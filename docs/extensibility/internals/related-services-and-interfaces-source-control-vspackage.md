---
title: 相關的服務和介面（原始檔控制 VSPackage） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ba041e1060f019e6b047fe4c589579112d690a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724399"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>相關的服務和介面 (原始檔控制 VSPackage)
此區段會列出 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 中的所有原始檔控制 VSPackage 相關介面。 [原始檔控制 VSPackage] 會執行其中一些介面，並使用其他介面來完成原始檔控制工作。

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>和針對原始檔控制 Vspackage 所實作為的介面
 下列介面會在 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 中描述，而原始檔控制 VSPackage 會根據其所需的功能集來執行其中的子集。 某些介面會標示為必要，且必須由每個原始檔控制 VSPackage 來執行。

 針對封裝不會執行的介面，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供預設的實值。 請注意，預設的執行是針對未註冊 VSPackage，且未控制任何專案的情況而設計的。 正確撰寫的原始檔控制 VSPackage 會執行所有必要的介面，而不是讓它成為這些介面的預設實值。

 原始檔控制 VSPackage 必須執行私用服務，以封裝下列部分或全部的介面。

 介面為：

- 必要：適當的實體（原始檔控制 VSPackage、原始檔控制 Stub、專案）必須執行介面。

- 建議：實體應該執行此介面;否則，原始檔控制功能可能會受到限制。

- 選擇性：實體可以執行此介面，以提供更豐富的功能集。

| 介面 | 用途 | 執行者 | 實作? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | 在修改或儲存檔案之前，編輯器會呼叫這個介面。 [原始檔控制 VSPackage] 可以簽出檔案，或在簽出失敗時拒絕作業。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | 這個介面提供專案的基本原始檔控制功能，例如在原始檔控制中註冊和取消註冊專案，以及提供基本原始檔控制字元的支援。 | 原始檔控制 VSPackage | 必要項 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | 這個介面是從使用 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 函式的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 取得，或直接將執行 `IVsHierarchy` 的物件轉換成 `IVsSccProject2`。 它是用來取得專案中原始檔控制下的檔案，或是用來通知專案目前的原始檔控制狀態或位置。 | 專案 | 必要項 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | 整合模組會使用此介面來設定目前作用中的 VSPackage。 | 原始檔控制 VSPackage | 必要項 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | 此介面是以訂用帳戶模型為基礎。 任何 VSPackage 都可能會指示它想要接收檔事件，並在即將發生的事件上使用 shell 來通知。 它會由 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 實及處理，然後將執行 `IVsTrackProjectDocumentsEvents2` 的事件傳遞給 VSPackage。 | 原始檔控制存根 | 必要項 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | 此介面提供批次處理、同步處理的讀取/寫入作業，以及 advanced `OnQueryAddFiles` 方法。 | 原始檔控制存根 | 必要項 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | 當新檔案新增至專案，或從專案重新命名或刪除檔案和資料夾時，**方案總管**和專案會呼叫這個介面。 原始檔控制 VSPackage 可以簽出項目檔，或取消作業。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **方案總管**和專案會呼叫這個介面，以回應對 IVstrackProjectDocuments3 介面的方法所做的呼叫。 [原始檔控制 VSPackage] 可以追蹤批次作業、同步處理的讀取/寫入作業，並使用更先進的 `OnQueryAddFiles` 方法。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | 這個介面會提供 Web 專案的登記管理支援。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | 這個介面是用來抓取專案中原始檔控制檔案的工具提示。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | 這個介面會提供命名空間延伸支援。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | VSPackage 會使用此介面，將命名空間延伸模組整合到 [**新增**]、[**開啟**] 或 [**儲存**] 對話方塊。 因此，專案可以在建立時自動加入至原始檔控制，或在儲存作業生效時加入至原始檔控制。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | VSPackage 會使用此介面，將其他字元定義為**方案總管**中節點的原始檔控制字元。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Web 專案的 [**加入**] 對話方塊會使用此介面。 它提供流覽原始檔控制位置，以及開啟先前在該位置的原始檔控制儲存機制中新增之 Web 專案的方法。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | 這個介面提供從原始檔控制載入專案的非同步（背景）支援。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | 此介面可讓專案監看 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> 起始的非同步載入進度。 | 專案 | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | 此介面可讓 IDE 查詢作用中的原始檔控制 VSPackage。 即使沒有註冊作用中的原始檔控制 VSPackage，IDE 也會查詢具有意義之原始檔控制設定的值。 這個介面是由 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 來執行和處理。 | 原始檔控制存根 | 必要項 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | 這個介面是用來註冊原始檔控制 VSPackage。 | 原始檔控制存根 | 必要項 |
| <xref:EnvDTE.SourceControl> | 此介面用於自動化。 因此，它只會公開可在不顯示任何 UI 的情況下執行的函式。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | 這個介面是用來儲存方案（.sln）檔案中的原始檔控制設定。 這些設定包括 [原始檔控制位置] 和 [原始檔控制狀態] 旗標。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | 這個介面是用來儲存方案選項（.suo）檔案中的原始檔控制設定。 這可能包括使用者特定的原始檔控制設定，例如目前使用者的登記位置。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | 這個介面是用來監視事件，以便執行作業，例如在關閉方案之前簽入專案檔，或在開啟專案時從原始檔控制取得新檔案。 | 原始檔控制 VSPackage | 建議 |

## <a name="see-also"></a>請參閱
- [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)