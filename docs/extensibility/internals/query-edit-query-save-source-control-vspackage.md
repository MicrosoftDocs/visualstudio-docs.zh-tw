---
title: "查詢 (原始檔控制 VSPackage) 儲存的編輯查詢 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e3428e51dda2f8cc8410b6ac67f5779f7c2300ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="query-edit-query-save-source-control-vspackage"></a>(原始檔控制 VSPackage) 儲存的查詢編輯查詢
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]編輯器可以廣播查詢編輯查詢儲存 (QEQS) 事件。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始檔控制虛設常式實作 QEQS 服務，使其具備 QEQS 事件的收件者。 這些事件然後委派給目前作用中的原始檔控制 VSPackage。 VSPackage 實作的作用中的原始檔控制<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>及其方法。 方法的`IVsQueryEditQuerySave2`介面通常稱為第一次，以及在儲存文件之前，編輯的文件之前。  
  
## <a name="queryeditquerysave-events"></a>QueryEditQuerySave 事件  
 原始檔控制 VSPackage 必須藉由實作處理 QEQS 事件`IVsQueryEditQuerySave2`介面和需要的方法。 以下是兩種方法，VSPackage 必須實作最少的簡短描述。 實際的實作必須符合的原始檔控制模型的邏輯。  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles 方法  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>任何專案或編輯器想要修改的檔案時呼叫。 在理想情況下，會呼叫這個方法*之前*會修改檔案，並儲存檔案時。 叫用時，`IVsQueryEditQuerySave2::QueryEditFiles`方法會檢查指定的檔案是否在原始檔控制、 它們是否需要簽出，及是否載入。 如果情況下防止檔案被編輯的`IVsQueryEditQuerySave2::QueryEditFiles`方法會告知呼叫的程式，以取消編輯。 它也可能會呼叫端若要指定叫用模式。 在 「 無訊息 」 模式中，這個方法不會顯示任何 UI 時，才會執行。 如果 UI 是無可避免的必須傳回旗標以指出問題。  
  
 方法的行為，以交易方式;亦即，如果在單一檔案取消編輯，則所有檔案的已取消編輯。 相反地，如果允許編輯，便會允許所有檔案。 如果此方法可讓您一次編輯一組指定的檔案，它必須永遠允許在同一組檔案的後續呼叫上編輯。 允許編輯迴圈會繼續執行，直到關閉、 儲存，以及重新載入; 檔案直到其屬性 （屬性） 變更。或直到變更原始檔控制封裝。 請考慮實作的情況下`IVsQueryEditQuerySave2::QueryEditFiles`方法包含多個檔案，特殊的檔案，請取消從使用者，並在記憶體中編輯。  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles 方法  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>任何專案或編輯器需要儲存一組檔案時呼叫。 叫用時，`IVsQueryEditQuerySave2::QuerySaveFiles`方法會檢查，如果指定的檔案是唯讀，不論它們是否在原始檔控制。 如果您需要將檔案簽出，呼叫會委派至原始檔控制封裝。 如果情況下防止檔案被儲存、`IVsQueryEditQuerySave2::QuerySaveFiles`方法必須告知編輯器中，以取消儲存。 如同`IVsQueryEditQuerySave2::QueryEditFiles`方法時，可能會呼叫端若要指定叫用模式。 在 「 無訊息 」 模式中，這個方法不會顯示任何 UI 時，才會執行。 如果 UI 是無可避免的必須傳回旗標以指出問題。  
  
 這個方法的行為必須如同以交易方式;也就是說，如果儲存已取消在單一檔案，儲存已取消的所有檔案。 相反地，如果允許儲存，它必須允許所有檔案。 如同`IVsQueryEditQuerySave2::QueryEditFiles`方法時，請考慮實作的情況下`IVsQueryEditQuerySave2::QuerySaveFiles`方法包含多個檔案，特殊的檔案，請取消從使用者，並在記憶體中編輯。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>