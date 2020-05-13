---
title: 查詢編輯查詢儲存(來源控制 VS 套件) |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c09ac0cb4f51b8f2484b95d403ff6d0445631479
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705964"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>查詢編輯查詢儲存 (原始檔控制 VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]編輯人員可以廣播查詢編輯查詢保存 (QEQS) 事件。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]源代碼管理存根實現 QEQS 服務,因此它是 QEQS 事件的接收者。 然後,這些事件將委派給當前活動的原始程式碼管理 VSPackage。 活動源控件 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>實現 及其方法。 `IVsQueryEditQuerySave2`介面的方法通常在文檔首次編輯之前和文檔保存之前立即調用。

## <a name="queryeditquerysave-events"></a>查詢編輯儲存事件
 原始碼管理 VSPackage 必須`IVsQueryEditQuerySave2`透過實作介面和必要的方法來處理 QEQS 事件。 以下是 VSPackage 必須至少實現的兩種方法的簡要說明。 實際實現必須符合原始程式碼管理模型的邏輯。

### <a name="queryeditfiles-method"></a>查詢編輯檔案方法
 您<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>可以變更檔案時, 將呼叫 。 理想情況下,在修改檔並保存檔*之前*調用此方法。 呼叫時,`IVsQueryEditQuerySave2::QueryEditFiles`該方法會檢查給定檔是否處於原始碼管理之下,是否需要簽出這些檔,以及是否可以重新載入這些檔。 如果情況阻止檔可編輯,`IVsQueryEditQuerySave2::QueryEditFiles`則該方法會告訴調用程式取消編輯。 調用方也可以指定調用模式。 在"靜默"模式下,此方法僅在它不導致出現任何 UI 時才執行操作。 如果 UI 不可避免,則必須返回標誌以指示問題。

 該方法以事務方式運行;也就是說,如果單個檔上取消編輯,則取消所有檔的編輯。 相反,如果允許編輯,則允許對所有文件進行編輯。 如果此方法允許對一組給定的文件進行編輯一次,則必須始終允許對同一組檔的後續調用進行編輯。 允許編輯迴圈將繼續,直到關閉、保存和重新載入檔;直到他們的屬性(屬性)發生變化;或直到源控制包被更改。 實現`IVsQueryEditQuerySave2::QueryEditFiles`該方法時需要考慮的情況包括多個檔、特殊文件、使用者取消和記憶體內編輯。

### <a name="querysavefiles-method"></a>查詢儲存檔案方法
 您<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>可以在任何項目或編輯器需要儲存一組檔案時,將呼叫 。 呼叫時,`IVsQueryEditQuerySave2::QuerySaveFiles`該方法會檢查給定檔是否為唯讀檔,以及這些檔案是否處於原始碼管理之下。 如果需要簽出檔,則調用將委派給原始程式碼管理包。 如果情況阻止保存檔,`IVsQueryEditQuerySave2::QuerySaveFiles`則方法必須告訴編輯器取消保存。 與方法`IVsQueryEditQuerySave2::QueryEditFiles`一樣,調用方可以指定調用模式。 在"靜默"模式下,此方法僅在它不導致出現任何 UI 時才執行操作。 如果 UI 不可避免,則必須返回標誌以指示問題。

 此方法必須以事務方式運行;也就是說,如果單個檔中的保存被取消,則所有檔的保存將被取消。 相反,如果允許保存,則必須允許所有文件進行保存。 與該方法一`IVsQueryEditQuerySave2::QueryEditFiles`樣,在`IVsQueryEditQuerySave2::QuerySaveFiles`實現 該方法時需要考慮的案例包括多個檔、特殊檔、使用者取消和記憶體內編輯。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
