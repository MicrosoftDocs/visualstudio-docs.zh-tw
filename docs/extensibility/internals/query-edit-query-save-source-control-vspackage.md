---
title: 查詢編輯查詢儲存 (原始檔控制 VSPackage) |Microsoft Docs
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
ms.openlocfilehash: d3bffdac79a9f4274fbd6465c33e8659caf9d1f6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341455"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>查詢編輯查詢儲存 (原始檔控制 VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 編輯器可以廣播查詢編輯查詢儲存 (QEQS) 事件。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 原始檔控制虛設常式實作 QEQS 服務，使其 QEQS 事件的收件者。 這些事件接著會委派至目前作用中的原始檔控制 VSPackage。 作用中的原始檔控制 VSPackage 實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>和其方法。 方法的`IVsQueryEditQuerySave2`介面通常只有在第一次，以及在儲存文件之前，編輯的文件之前，立即呼叫。

## <a name="queryeditquerysave-events"></a>QueryEditQuerySave 事件
 原始檔控制 VSPackage 必須藉由實作處理 QEQS 事件`IVsQueryEditQuerySave2`介面和需要的方法。 以下是 VSPackage 必須實作最小值的兩個方法的簡短描述。 實際的實作必須符合的原始檔控制模型的邏輯。

### <a name="queryeditfiles-method"></a>QueryEditFiles 方法
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>任何專案或編輯器想要修改的檔案時呼叫。 在理想情況下，會呼叫這個方法*之前*檔案遭到修改和儲存檔案時。 叫用時，`IVsQueryEditQuerySave2::QueryEditFiles`方法會檢查指定的檔案是否在原始檔控制、 它們是否需要簽出，以及是否載入。 如果情況下防止檔案被編輯，`IVsQueryEditQuerySave2::QueryEditFiles`方法會告訴呼叫端程式來取消編輯。 您也可讓呼叫者指定的引動過程模式。 在 「 無訊息 」 模式中，此方法會採用動作，才不會造成任何 UI 出現。 如果 UI 是無法避免的必須傳回旗標以指出問題。

 方法的行為以交易方式;也就是如果在單一檔案取消編輯，則所有檔案的已取消編輯。 相反地，如果允許編輯，它會允許所有檔案。 如果這個方法可讓您編輯一次針對一組指定的檔案，它必須永遠允許同一組檔案的後續呼叫上編輯。 允許編輯迴圈會繼續執行，直到檔案關閉、 儲存，並重新載入;直到及其屬性 （屬性） 變更;或者，直到變更原始檔控制套件。 請考慮實作的情況下`IVsQueryEditQuerySave2::QueryEditFiles`方法包含多個檔案，特殊的檔案，請取消使用者，與在記憶體中進行編輯。

### <a name="querysavefiles-method"></a>QuerySaveFiles 方法
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>任何專案或編輯器需要儲存一組檔案時呼叫。 叫用時，`IVsQueryEditQuerySave2::QuerySaveFiles`方法會檢查，如果指定的檔案是唯讀，不論是在原始檔控制。 如果需要簽出檔案，就會呼叫委派給原始檔控制封裝中。 如果情況下可防止檔案被儲存、`IVsQueryEditQuerySave2::QuerySaveFiles`方法必須告知編輯器取消儲存。 如同`IVsQueryEditQuerySave2::QueryEditFiles`方法，您就可以讓呼叫者指定的引動過程模式。 在 「 無訊息 」 模式中，此方法會採用動作，才不會造成任何 UI 出現。 如果 UI 是無法避免的必須傳回旗標以指出問題。

 這個方法的行為必須與交易的方式;亦即，如果儲存已取消在單一檔案中，儲存已取消的所有檔案。 相反地，如果允許儲存，它必須允許所有檔案。 如同`IVsQueryEditQuerySave2::QueryEditFiles`方法中，請考慮實作的情況下`IVsQueryEditQuerySave2::QuerySaveFiles`方法包含多個檔案，特殊的檔案，請取消使用者，與在記憶體中進行編輯。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>