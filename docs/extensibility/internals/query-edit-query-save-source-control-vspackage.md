---
title: 查詢編輯查詢儲存 (原始檔控制 VSPackage) |Microsoft Docs
description: 瞭解 Query-Edit Query-Save 事件的角色，以及原始檔控制 VSPackage 如何處理這些事件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e320d6f7b6126736719eb2a428d47a39a61730ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837264"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>查詢編輯查詢儲存 (原始檔控制 VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 編輯器可以廣播查詢編輯查詢儲存 (QEQS) 事件。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 原始檔控制存根會執行 QEQS 服務，因此它是 QEQS 事件的收件者。 這些事件接著會委派給目前作用中的原始檔控制 VSPackage。 作用中的原始檔控制 VSPackage 會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 和其方法。 介面的方法 `IVsQueryEditQuerySave2` 通常會在檔首次編輯之前，以及在檔儲存之前立即呼叫。

## <a name="queryeditquerysave-events"></a>QueryEditQuerySave 事件
 原始檔控制 VSPackage 必須藉由執行介面和必要的方法來處理 QEQS 事件 `IVsQueryEditQuerySave2` 。 以下是 VSPackage 至少必須執行的兩個方法的簡短描述。 實際的實作為必須符合原始檔控制模型的邏輯。

### <a name="queryeditfiles-method"></a>QueryEditFiles 方法
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>當任何專案或編輯器想要修改檔案時，就會呼叫。 在理想的情況下，會在檔案修改 *之前* 和儲存檔案時呼叫這個方法。 叫用時， `IVsQueryEditQuerySave2::QueryEditFiles` 方法會檢查指定的檔案是否位於原始檔控制之下，是否需要簽出它們，以及是否可以重載它們。 如果情況導致無法編輯檔案，則方法會 `IVsQueryEditQuerySave2::QueryEditFiles` 告知呼叫程式取消編輯。 呼叫端也可以指定調用模式。 在「無訊息」模式中，這個方法只有在不會造成任何 UI 出現時才會採取動作。 如果無法避免 UI，則必須傳回旗標來指出問題。

 方法會以交易方式運作;也就是說，如果在單一檔案上取消編輯，則會取消所有檔案的編輯。 相反地，如果允許編輯，則所有檔案都允許使用。 如果這個方法可以針對一組指定的檔案進行一次編輯，則在後續呼叫同一組檔案時，一律必須允許編輯。 允許編輯迴圈會繼續執行，直到檔案關閉、儲存和重載為止;在屬性 (屬性之前) 變更;或直到原始檔控制封裝變更為止。 在實施方法時要考慮的案例 `IVsQueryEditQuerySave2::QueryEditFiles` 包括多個檔案、特殊檔案、取消使用者，以及記憶體內部編輯。

### <a name="querysavefiles-method"></a>QuerySaveFiles 方法
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>當任何專案或編輯器需要儲存一組檔案時，就會呼叫。 叫用時， `IVsQueryEditQuerySave2::QuerySaveFiles` 方法會檢查指定的檔案是否為唯讀，以及它們是否在原始檔控制之下。 如果需要簽出檔案，則會將呼叫委派給原始檔控制封裝。 如果情況導致無法儲存檔案，則 `IVsQueryEditQuerySave2::QuerySaveFiles` 方法必須告訴編輯器取消儲存。 如同方法一樣 `IVsQueryEditQuerySave2::QueryEditFiles` ，呼叫端也可以指定調用模式。 在「無訊息」模式中，這個方法只有在不會造成任何 UI 出現時才會採取動作。 如果無法避免 UI，則必須傳回旗標來指出問題。

 這個方法必須以交易方式運作;也就是說，如果在單一檔案上取消儲存，則會取消所有檔案的儲存。 相反地，如果允許儲存，則所有檔案都必須允許使用。 如同 `IVsQueryEditQuerySave2::QueryEditFiles` 方法，要考慮採用方法的案例 `IVsQueryEditQuerySave2::QuerySaveFiles` 包括多個檔案、特殊檔案、取消使用者，以及記憶體內部編輯。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
