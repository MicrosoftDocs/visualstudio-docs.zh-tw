---
title: 文件鎖持有人管理 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9dd520f8ad5cab1f0cfee890c4bcc388c204bb1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712129"
---
# <a name="document-lock-holder-management"></a>文件鎖定者管理

正在執行的文件表 (RDT) 維護打開的文檔及其擁有的任何編輯鎖的計數。 當使用者在後台以程式設計方式編輯文檔時,可以在 RDT 中放置編輯鎖,而使用者卻看不到文檔視窗中打開的文檔。 通過圖形使用者介面修改多個文件的設計人員通常使用此功能。

## <a name="document-lock-holder-scenarios"></a>文件鎖定持有人方案

### <a name="file-a-has-a-dependence-on-file-b"></a>檔"a"依賴於檔"b"

請考慮以下情況:對於檔類型「a」實現標準編輯器「A」,並且類型為「a」的每個檔都引用(或依賴)類型為「b」的檔。 對於類型為"b"的檔,存在標準編輯器"B"。 當編輯器「A」打開檔「a」時,它會檢索對相應檔「b」的引用。 檔"b"不顯示,但編輯器"A"可以修改它。 編輯器「A」從該方法獲取對檔「b」的文件資料的引用,<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>並維護檔案「b」的編輯鎖。 編輯"A"修改完檔"b"後,可以通過調<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>用 方法來減少檔"b"的編輯鎖計數。 如果將參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>`dwRDTLockType`設定為_VSRDTFLAGS呼叫方法,則可以省略此步驟[。RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>檔案 「b」由不同的編輯器開啟

如果編輯「B」嘗試開啟檔「B」時,編輯「B」已經開啟該檔「b」,則有兩個單獨的方案需要處理:

- 如果檔「b」在相容編輯器中打開,則必須讓編輯器「A」使用方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>註冊檔「b」的文檔編輯鎖。 編輯"A"修改檔"b"後,使用方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>取消註冊文檔編輯鎖。

- 如果檔「b」以不相容的方式打開,則可以讓編輯「A」嘗試打開檔「b」失敗,也可以讓與編輯器「A」關聯的檢視部分打開並顯示相應的錯誤消息。 錯誤消息應指示使用者關閉不相容編輯器中的檔"b",然後使用編輯器"A"重新打開檔"a"。 還可以實現該方法[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>以提示使用者關閉在不相容編輯器中打開的檔"b"。 如果使用者關閉檔「b」,則編輯器「A」中檔「a」的打開將正常進行。

## <a name="additional-document-edit-lock-considerations"></a>其他文件編輯鎖定事項

如果編輯器「A」是檔「b」上唯一具有文檔編輯鎖的編輯器,則您會獲得不同的行為,如果編輯器「B」對檔「b」也持有文件編輯鎖,則不同。 在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中,**類別設計器**是可視化設計器的範例,該設計器不持有關聯的程式碼檔上的編輯鎖。 也就是說,如果使用者在設計檢視中打開了類圖,並且關聯的代碼檔同時打開,如果使用者修改了代碼檔但不保存更改,則更改也會丟失到類關係圖 (.cd) 檔。 如果**類設計器**在代碼檔上具有唯一的文檔編輯鎖,則在關閉代碼檔時不會要求使用者保存更改。 IDE 要求使用者僅在使用者關閉**類設計器**後保存更改。 保存的更改將反映在兩個檔中。 如果**類設計器**和代碼檔編輯器都持有代碼檔上的文檔編輯鎖,則在關閉代碼檔或窗體時,系統會提示使用者保存。 此時,保存的更改將反映在窗體和代碼檔中。 有關類關係圖的詳細資訊,請參閱[使用類關係圖(類設計器)。](../ide/class-designer/designing-and-viewing-classes-and-types.md)

請注意,如果需要在非編輯器的文檔上放置編輯鎖,則必須實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>該 介面。

很多時候,以程式設計方式修改代碼檔的 UI 設計器對多個檔進行更改。 在這種情況下,<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>該方法通過「**是否要儲存對以下項的更改?"** 對話框來處理一個或多個文件的保存。

## <a name="see-also"></a>另請參閱

- [執行文件表](../extensibility/internals/running-document-table.md)
- [持久性和正在執行的文件表](../extensibility/internals/persistence-and-the-running-document-table.md)
