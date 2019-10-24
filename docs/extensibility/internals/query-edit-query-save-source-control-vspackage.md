---
title: 查詢編輯查詢儲存（原始檔控制 VSPackage） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be12297bdaeb112d7421b02da1153ed62d6d14f8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724776"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>查詢編輯查詢儲存 (原始檔控制 VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 編輯器可以廣播查詢編輯查詢儲存（QEQS）事件。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 原始檔控制存根會執行 QEQS 服務，使其成為 QEQS 事件的收件者。 這些事件接著會委派給目前作用中的原始檔控制 VSPackage。 作用中的原始檔控制 VSPackage 會實作用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 和其方法。 @No__t_0 介面的方法通常會在第一次編輯檔之前，以及在儲存檔之前立即呼叫。

## <a name="queryeditquerysave-events"></a>QueryEditQuerySave 事件
 [原始檔控制 VSPackage] 必須藉由執行 `IVsQueryEditQuerySave2` 介面和必要的方法來處理 QEQS 事件。 以下是 VSPackage 至少必須執行之兩種方法的簡短描述。 實際的執行必須符合原始檔控制模型的邏輯。

### <a name="queryeditfiles-method"></a>QueryEditFiles 方法
 當任何專案或編輯器想要修改檔案時，就會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>。 在理想的情況下，這個方法會在檔案被修改以及儲存檔案*之前*呼叫。 當叫用時，`IVsQueryEditQuerySave2::QueryEditFiles` 方法會檢查指定的檔案是否在原始檔控制之下、是否需要簽出，以及是否可以重載它們。 如果情況導致檔案無法編輯，`IVsQueryEditQuerySave2::QueryEditFiles` 方法會指示呼叫程式取消編輯。 呼叫者也可以指定叫用模式。 在「無訊息」模式中，這個方法只有在不會造成 UI 出現時才會採取動作。 如果無法避免 UI，則必須傳回旗標來表示問題。

 方法會以交易方式運作;也就是說，如果在單一檔案上取消編輯，則會取消所有檔案的編輯。 相反地，如果允許編輯，則會允許所有檔案使用。 如果這個方法可以針對一組指定的檔案編輯一次，它就必須一律允許在相同檔案集的後續呼叫上進行編輯。 [允許編輯] 迴圈會繼續進行，直到檔案關閉、儲存和重載為止;直到其屬性（屬性）變更為止;或直到原始檔控制封裝變更為止。 執行 `IVsQueryEditQuerySave2::QueryEditFiles` 方法時要考慮的案例包括多個檔案、特殊檔案、從使用者取消和記憶體中的編輯。

### <a name="querysavefiles-method"></a>QuerySaveFiles 方法
 當任何專案或編輯器需要儲存一組檔案時，就會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>。 當叫用時，`IVsQueryEditQuerySave2::QuerySaveFiles` 方法會檢查指定的檔案是否為唯讀，以及它們是否在原始檔控制之下。 如果需要簽出檔案，則會將呼叫委派給原始檔控制封裝。 如果情況導致無法儲存檔案，`IVsQueryEditQuerySave2::QuerySaveFiles` 方法就必須告知編輯器取消儲存。 如同 `IVsQueryEditQuerySave2::QueryEditFiles` 方法，呼叫者可以指定調用模式。 在「無訊息」模式中，這個方法只有在不會造成 UI 出現時才會採取動作。 如果無法避免 UI，則必須傳回旗標來表示問題。

 這個方法的行為必須以交易方式運作;也就是說，如果在單一檔案上取消儲存，則會取消所有檔案的儲存。 相反地，如果允許儲存，所有檔案都必須允許它。 如同 `IVsQueryEditQuerySave2::QueryEditFiles` 方法，要考慮執行 `IVsQueryEditQuerySave2::QuerySaveFiles` 方法的案例包括多個檔案、特殊檔案、取消使用者和記憶體中編輯。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>