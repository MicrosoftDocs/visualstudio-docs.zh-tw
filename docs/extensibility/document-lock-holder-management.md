---
title: "鎖定擁有者管理的文件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: df782cd974adcd589824e8a47cd0249842bd8d48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="document-lock-holder-management"></a>文件鎖定持有者管理
執行文件資料表 (RDT) 維護的計數為開啟的文件和它們的任何編輯鎖定。 以程式設計方式編輯在背景中沒有看到文件視窗中開啟的文件的使用者時，您可以編輯鎖定放置 RDT 中的文件。 修改多個檔案的圖形化使用者介面的設計工具通常會使用這項功能。  
  
## <a name="document-lock-holder-scenarios"></a>文件鎖定持有者案例  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>檔案"a"已在檔案上的相依性"b"  
 假設您用來實作的檔案類型的標準編輯器"A""a"，以及每個檔案的型別"a"有參考 （或相依性） 類型"b"的檔案。 類型"b"的檔案存在於標準編輯器"B"。 "A"編輯器開啟檔案時"a"，它會擷取對應的檔案"b"的參考。 不會顯示檔案"b"，但編輯器"A"可以進行修改。 編輯器"A"取得的參考文件資料檔案的"b"從<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法，也會維護檔案"b"的編輯鎖定。 編輯器"A"完畢後修改的檔案"b"可以遞減編輯鎖定倚賴檔案"b"藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>方法。 您可以省略此步驟中，如果已經呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法與參數`dwRDTLockType`設<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>。  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>不同的編輯器開啟檔案"b"  
 "B"的檔案已經開啟的編輯器"B""A"編輯器開啟它時，有兩個不同的案例，以處理：  
  
-   如果是相容的編輯器中開啟檔案"b"，您必須擁有編輯器"A"註冊"b"檔案使用的文件編輯鎖定<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>方法。 您的編輯器"A"是修改檔案"b"之後，取消註冊文件編輯鎖定使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>方法。  
  
-   如果在不相容的方式開啟檔案"b"，您可以讓嘗試的開啟檔案"b""A"失敗，或者您可以讓使用編輯器開啟並顯示適當的錯誤訊息部分的"A"相關聯之檢視的編輯器。 錯誤訊息應該指示使用者關閉不相容的編輯器中的檔案"b"，然後再重新開啟檔案"a"使用編輯器"A"。 您也可以實作[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>來提示使用者關閉"b"的檔案不相容的編輯器中開啟。 如果使用者關閉"b"，檔案的開啟檔案"A""a"在編輯器會繼續正常進行。  
  
## <a name="additional-document-edit-lock-considerations"></a>其他文件編輯鎖定考量  
 如果編輯器"A"是唯一具有文件編輯鎖定檔案"b"比"B"編輯器也會包含文件時的編輯器編輯鎖定檔案"b"，您會收到不同的行為。 在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，**類別設計工具**是沒有相關聯的程式碼檔案已編輯鎖定的視覺化設計工具的範例。 也就是說，如果該使用者可以在 [設計] 檢視中開啟類別圖，且同時開啟相關聯的程式碼檔案，而且使用者修改的程式碼檔案，但不是儲存變更，所做的變更也會遺失類別圖 (.cd) 檔案。 如果**類別設計工具**具有唯一的文件編輯程式碼檔案上的鎖定，不要求使用者在關閉程式碼檔案時，儲存的變更。 IDE 會詢問使用者是否要儲存變更，只有在使用者關閉之後，才**類別設計工具**。 儲存的變更會反映在這兩個檔案。 如果兩個**類別設計工具**且程式碼檔案編輯器保留文件編輯鎖定程式碼檔案，則系統會提示使用者儲存程式碼檔或表單關閉時。 此時，儲存的變更會反映在表單和程式碼檔案。 在類別圖表上的詳細資訊，請參閱[使用類別圖表 （類別設計工具）](../ide/working-with-class-diagrams-class-designer.md)。  
  
 請注意，是否您需要編輯鎖定置於非編輯器的文件，您必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>介面。  
  
 多次 UI 設計工具，以程式設計方式修改程式碼檔會對多個檔案進行變更。 在此情況下<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>方法會處理一或多個文件，藉由儲存**您要將變更儲存到下列項目嗎？**  對話方塊。  
  
## <a name="see-also"></a>請參閱  
 [執行中的文件表格](../extensibility/internals/running-document-table.md)   
 [持續性與執行中的文件資料表](../extensibility/internals/persistence-and-the-running-document-table.md)