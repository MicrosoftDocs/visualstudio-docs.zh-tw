---
title: 檔鎖定持有者管理 |Microsoft Docs
description: 瞭解如何在執行檔資料表中的檔上放置編輯鎖定，而使用者在文件視窗中看不到開啟的檔。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c15696d81be92f0549069bad354e65356f7b2e7c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995898"
---
# <a name="document-lock-holder-management"></a>檔鎖定持有者管理

執行中的檔資料表 (RDT) 維護已開啟檔的計數，以及它們所擁有的任何編輯鎖定。 當您在背景中以程式設計方式編輯 RDT 中的檔時，可以在該檔上放置編輯鎖定，而使用者不會在文件視窗中看到開啟的檔。 透過圖形化使用者介面修改多個檔案的設計師通常會使用這項功能。

## <a name="document-lock-holder-scenarios"></a>檔鎖定持有者案例

### <a name="file-a-has-a-dependence-on-file-b"></a>檔案 "a" 相依于檔案 "b"

假設您針對檔案類型 "a" 執行標準編輯器 "A"，且類型為 "a" 的每個檔案都有 (的參考，或相依于) "b" 類型的檔案。 "B" 類型的檔案有標準編輯器 "B"。 當編輯器「A」開啟檔案 "a" 時，它會抓取對應檔案 "b" 的參考。 檔案 "b" 未顯示，但編輯器 "A" 可加以修改。 編輯器 "A" 會從方法取得檔案 "b" 的檔資料參考 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> ，也會在檔案 "b" 上維護編輯鎖定。 在編輯器 "A" 完成修改檔案 "b" 之後，您可以呼叫方法，以遞減檔案 "b" 的編輯鎖定計數 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> 。 如果您已呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 方法並將參數 `dwRDTLockType` 設定為 _VSRDTFLAGS，則可以省略這個步驟 [。RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>)。

### <a name="file-b-is-opened-by-a-different-editor"></a>檔案 "b" 是由不同的編輯器開啟

當編輯器「A」嘗試開啟檔案 "b" 時，如果編輯器 "B" 開啟了檔案 "b"，有兩個不同的案例要處理：

- 如果在相容的編輯器中開啟檔案 "b"，您必須使用方法，讓編輯器「A」在檔案 "b" 上註冊檔編輯鎖定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> 。 在編輯器「A」完成修改檔案 "b" 之後，請使用方法取消註冊檔編輯鎖定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> 。

- 如果檔案 "b" 是以不相容的方式開啟，您可以讓編輯器「A」嘗試開啟檔案 "b"，或是讓視圖與編輯器「A」建立關聯，並顯示適當的錯誤訊息。 錯誤訊息應指示使用者關閉不相容編輯器中的檔案 "b"，然後使用編輯器 "A" 重新開啟檔案 "a"。 您也可以執行 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> ，提示使用者關閉在不相容編輯器中開啟的檔案 "b"。 如果使用者關閉檔案 "b"，則在編輯器 "A" 中開啟檔案 "a" 會繼續正常執行。

## <a name="additional-document-edit-lock-considerations"></a>其他檔編輯鎖定考慮

如果編輯器「A」是唯一的編輯器，而且只有在檔案 "b" 上有檔編輯鎖定，而且編輯器 "B" 也持有檔案 "b" 的檔編輯鎖定，您就會看到不同的行為。 在中 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ， **類別設計工具** 是未在相關聯的程式碼檔案上保存編輯鎖定的視覺化設計工具範例。 也就是說，如果使用者在設計檢視中開啟類別圖表，並同時開啟相關聯的程式碼檔案，而且使用者修改了程式碼檔案但未儲存變更，則在類別圖表 ( 的) 檔案中也會遺失變更。 如果 **類別設計工具** 只有程式碼檔案的檔編輯鎖定，則在關閉程式碼檔案時，不會要求使用者儲存變更。 IDE 會要求使用者在關閉 **類別設計工具** 之後，才儲存變更。 儲存的變更會反映在這兩個檔案中。 如果 **類別設計工具** 和程式碼檔案編輯器都持有程式碼檔案的檔編輯鎖定，則在關閉程式碼檔案或表單時，系統會提示使用者進行儲存。 屆時，儲存的變更會反映在表單和程式碼檔案中。 如需類別圖的詳細資訊，請參閱使用 [類別圖表 (類別設計工具) ](../ide/class-designer/designing-and-viewing-classes-and-types.md)。

請注意，如果您需要在非編輯器的檔上放置編輯鎖定，就必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 介面。

UI 設計工具以程式設計方式修改程式碼檔案的許多時候，會變更一個以上的檔案。 在這種情況下， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> 方法會透過下列方式來處理一或多個檔的儲存： **您是否要將變更儲存至下列專案？** 對話方塊。

## <a name="see-also"></a>另請參閱

- [執行中的檔資料表](../extensibility/internals/running-document-table.md)
- [持續性與執行中的檔資料表](../extensibility/internals/persistence-and-the-running-document-table.md)
