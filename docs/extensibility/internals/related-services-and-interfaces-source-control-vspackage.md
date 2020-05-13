---
title: 相關服務和介面(原始程式碼管理 VS 包) |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 533f1bf4fcfbaebb25ec10908abf4a46ddacd521
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705632"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>相關的服務和介面 (原始檔控制 VSPackage)
本節列出了[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]中 與 VSPackage 相關的所有原始程式碼管理介面。 原始碼管理 VSPackage 實現了其中一些介面,並使用其他介面來完成原始程式碼管理任務。

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>由 原始碼管理 VS 套件的介面,並為源碼管理 VS 套件實作
 以下介面在 中介紹[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], 原始程式碼管理 VSPackage 根據其所需的功能集實現其中的子集。 某些介面被標記為必需,並且必須由每個原始程式碼管理 VSPackage 實現。

 對於包未實現的介面,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供預設實現。 請注意,默認實現是為未註冊 VSPackage 且未控制項目的情況而設計的。 正確編寫的原始程式碼管理 VSPackage 實現所有必要的介面,而不是將其留給這些介面的默認實現。

 源代碼管理 VSPackage 必須實現專用服務,該服務封裝了以下部分或全部介面。

 介面包括:

- 必需:適當的實體(原始程式碼管理 VS 包、原始碼管理存根、專案)必須實現介面。

- 建議:實體應實現此介面;否則,原始程式碼管理功能可能會受到限制。

- 可選:實體可以實現此介面,以提供更豐富的功能集。

| 介面 | 目的 | 實施者 | 實現? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | 編輯人員在修改或保存檔之前呼叫此介面。 如果簽出失敗,原始程式碼管理 VSPackage 可以簽出檔或拒絕操作。 | 原始碼管理 VS 套件 | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | 此介面為專案提供基本原始程式碼管理功能,例如使用原始程式碼管理註冊和取消註冊專案,以及支援基本原始程式碼管理字形。 | 原始碼管理 VS 套件 | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | 此<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面是從 使用函<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>數獲得 ,或者`IVsHierarchy`只需將實現的物件`IVsSccProject2`強制轉換到 。 它用於在專案中使文件處於原始程式碼管理之下,或通知專案當前原始程式碼管理狀態或位置。 | 隨附此逐步解說的專案 | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | 集成模組使用此介面設置當前活動 VSPackage。 | 原始碼管理 VS 套件 | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | 此介面基於訂閱模型。 任何 VSPackage 都可以發出信號,表明它要接收文檔事件,並且 shell 會就即將發生的事件提供建議。 它由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]實現和處理,後者又將實現的`IVsTrackProjectDocumentsEvents2`事件 傳遞給 VSPackage。 | 原始碼管理 | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | 此介面提供批處理、同步讀/寫操作和高級`OnQueryAddFiles`方法。 | 原始碼管理 | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | 當向專案添加新檔案或從專案重新命名或刪除檔案和資料夾時,**解決方案資源管理員**和專案將調用此介面。 原始碼管理 VSPackage 可以簽出專案檔或取消操作。 | 原始碼管理 VS 套件 | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **解決方案資源管理員**和專案調用此介面以回應對IVtrackProjectDocuments3介面方法的調用。 原始碼管理 VSPackage 可以追蹤批次處理操作、同步讀/寫操作,以及使用`OnQueryAddFiles`更進階的方法。 | 原始碼管理 VS 套件 | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | 此介面為 Web 專案提供登記管理支援。 | 原始碼管理 VS 套件 | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | 此介面用於檢索專案中源控制檔的 ToolTips。 | 原始碼管理 VS 套件 | 選用 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | 此介面提供命名空間擴展支援。 | 原始碼管理 VS 套件 | 選用 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | VSPackage 使用此介面將命名空間擴展整合到 **"新建****"、"打開"** 或 **"儲存"** 對話框中。 因此,可以在創建時自動將專案添加到原始程式碼管理中,或在保存操作生效時將其添加到原始程式碼管理。 | 原始碼管理 VS 套件 | 選用 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | VSPackage 使用此介面將其他字形定義為**解決方案資源管理器**中節點的原始程式碼管理字形。 | 原始碼管理 VS 套件 | 選用 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Web 專案的 **「新增**」對話框使用此介面。 它提供了用於流覽原始程式碼管理位置的方法,以及打開以前添加到該位置的原始程式碼管理儲存庫中的 Web 專案的方法。 | 原始碼管理 VS 套件 | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | 此介面支援從原始程式碼管理載入專案的非同步(後台)載入。 | 原始碼管理 VS 套件 | 選用 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | 此介面允許項目監視由<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>啟動的非同步載入的進度。 | 隨附此逐步解說的專案 | 選用 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | 此介面允許 IDE 查詢活動源控制項 VSPackage。 IDE 查詢原始程式碼管理設定的值,即使未註冊活動原始程式碼管理 VSPackage,這些設置也具有意義。 此介面由實現[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和處理。 | 原始碼管理 | 必要 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | 此介面用於註冊原始程式碼管理 VSPackage。 | 原始碼管理 | 必要 |
| <xref:EnvDTE.SourceControl> | 此介面用於自動化。 因此,它只公開可以在不顯示任何 UI 的情況下執行的功能。 | 原始碼管理 VS 套件 | 選用 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | 此介面用於將原始程式碼管理設定保存在解決方案 (.sln) 檔案中。 這些設置包括原始碼管理位置和原始程式碼管理狀態標誌。 | 原始碼管理 VS 套件 | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | 此介面用於將原始程式碼管理設定保存在解決方案選項 (.suo) 檔案中。 這可能包括特定於使用者的原始程式碼管理設置,如當前使用者的登記位置。 | 原始碼管理 VS 套件 | 建議 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | 此介面用於監視事件,以便執行操作,例如在關閉解決方案之前簽入專案檔,或在打開專案時從原始程式碼管理獲取新檔。 | 原始碼管理 VS 套件 | 建議 |

## <a name="see-also"></a>另請參閱
- [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)
