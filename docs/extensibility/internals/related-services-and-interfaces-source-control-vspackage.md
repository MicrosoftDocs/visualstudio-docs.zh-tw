---
title: 相關的服務和介面 (原始檔控制 VSPackage)
titleSuffix: ''
description: 瞭解 Visual Studio SDK 中的原始檔控制 VSPackage 相關介面。 封裝會執行一些介面，並使用其他介面進行原始檔控制。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3cb7811816c4ad7a7ca6f6f0220f185799ee8b77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837186"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>相關的服務和介面 (原始檔控制 VSPackage)

此區段會列出中的所有原始檔控制 VSPackage 相關介面 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 。 原始檔控制 VSPackage 會實作為這些介面的一部分，並使用其他介面來完成原始檔控制工作。

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>由和針對原始檔控制 Vspackage 所執行的介面

 中描述下列介面 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ，而原始檔控制 VSPackage 會根據其所需的功能集來執行這些介面的子集。 某些介面會標示為必要，且必須由每個原始檔控制 VSPackage 來執行。

 針對封裝未執行的介面，會 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供預設的實值。 請注意，預設的執行是針對未註冊任何 VSPackage 且未控制任何專案的情況而設計。 正確撰寫的原始檔控制 VSPackage 會執行所有必要的介面，而不是將其保留為這些介面的預設執行。

 原始檔控制 VSPackage 必須執行可封裝下列部分或所有介面的私用服務。

 介面為：

- 必要：適當的實體 (原始檔控制 VSPackage、原始檔控制存根、專案) 必須執行介面。

- 建議：實體應該執行此介面;否則，原始檔控制功能可能會受到限制。

- 選擇性：實體可以執行這個介面，以提供更豐富的功能集。

| 介面 | 目的 | 實作為 | 實現？ |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | 編輯器會在修改或儲存檔案之前呼叫這個介面。 如果簽出失敗，原始檔控制 VSPackage 可以簽出檔案或拒絕作業。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | 這個介面會為專案提供基本的原始檔控制功能，例如使用原始檔控制註冊和取消註冊專案，並提供基本原始檔控制圖像的支援。 | 原始檔控制 VSPackage | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | 這個介面是使用函式來取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> ，或直接將實作為的物件轉換 `IVsHierarchy` 成 `IVsSccProject2` 。 它是用來取得專案中原始檔控制下的檔案，或是用來通知專案目前的原始檔控制狀態或位置。 | Project | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | 整合模組使用此介面來設定目前作用中的 VSPackage。 | 原始檔控制 VSPackage | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | 這個介面是以訂用帳戶模型為基礎。 任何 VSPackage 都可以表示它想要接收檔事件，並由 shell 針對即將發生的事件發出建議。 它是由執行和處理 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，進而將執行的事件傳遞 `IVsTrackProjectDocumentsEvents2` 至 VSPackage。 | 原始檔控制存根 | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | 此介面提供批次處理、同步處理的讀取/寫入作業，以及 advanced `OnQueryAddFiles` 方法。 | 原始檔控制存根 | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | 當新檔案新增至專案時，或從專案重新命名或刪除檔案和資料夾時，**方案總管** 和專案都會呼叫這個介面。 原始檔控制 VSPackage 可以簽出項目檔或取消作業。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **方案總管** 和專案會呼叫這個介面，以回應對 IVstrackProjectDocuments3 介面的方法所做的呼叫。 原始檔控制 VSPackage 可以追蹤批次作業、同步處理的讀取/寫入作業，以及使用更先進的 `OnQueryAddFiles` 方法。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | 這個介面會提供 Web 專案的登記管理支援。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | 這個介面是用來取得專案中原始檔控制檔案的工具提示。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | 這個介面會提供命名空間延伸模組支援。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | VSPackage 會使用這個介面，將命名空間延伸整合到 **新** 的、 **開啟** 的或 **儲存** 對話方塊中。 因此，專案可以在建立時自動加入原始檔控制，或在儲存作業生效時新增至原始檔控制。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | VSPackage 會使用這個介面，將其他字元定義為 **方案總管** 中節點的原始檔控制圖像。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Web 專案的 [ **加入** ] 對話方塊會使用此介面。 它會提供方法來流覽原始檔控制位置，以及開啟先前在該位置的原始檔控制存放庫中新增的 Web 專案。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | 這個介面可支援從原始檔控制載入專案的非同步 (背景) 。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | 這個介面可讓專案監看啟動非同步載入的進度 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> 。 | Project | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | 這個介面可讓 IDE 查詢作用中的原始檔控制 VSPackage。 IDE 會查詢原始檔控制設定的值，即使沒有註冊任何使用中的原始檔控制 VSPackage 亦是如此。 這個介面是由執行和處理 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 | 原始檔控制存根 | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | 這個介面是用來註冊原始檔控制 VSPackage。 | 原始檔控制存根 | 必要 |
| <xref:EnvDTE.SourceControl> | 此介面會在自動化中使用。 因此，它只會公開可在不顯示任何 UI 的情況下執行的函式。 | 原始檔控制 VSPackage | 選擇性 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | 這個介面是用來將方案中的原始檔控制設定儲存 ( .sln) 檔。 這些設定包括原始檔控制位置和原始檔控制狀態旗標。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | 這個介面是用來將 [方案選項] 中的原始檔控制設定儲存 ( .suo) 檔。 這可能包括使用者特定的原始檔控制設定，例如目前使用者的登記位置。 | 原始檔控制 VSPackage | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | 這個介面是用來監視事件，以便執行作業，例如在關閉方案之前簽入專案檔，或是在開啟專案時從原始檔控制取得新檔案。 | 原始檔控制 VSPackage | 建議 |

## <a name="see-also"></a>另請參閱
- [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)
