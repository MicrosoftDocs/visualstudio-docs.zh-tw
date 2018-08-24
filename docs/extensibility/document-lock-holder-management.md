---
title: 文件鎖定持有者管理 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 92d19e3edde058a8f0d2ca571ee8e909e010c1da
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637704"
---
# <a name="document-lock-holder-management"></a>文件鎖定持有者管理
執行文件資料表 (RDT) 會維持開啟的文件和它們所擁有的任何編輯鎖定計數。 以程式設計方式編輯在背景中沒有看到文件視窗中開啟的文件的使用者時，您可以編輯鎖定放置 RDT 中的文件上。 這項功能常用的設計工具，可修改的圖形化使用者介面的多個檔案。  
  
## <a name="document-lock-holder-scenarios"></a>文件鎖定持有者案例  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>檔案"a"具有檔案 「 b 」 的相依性  
 假設您用來實作檔案類型的標準編輯器"A""a"，以及每個檔案類型"a"的參考 （或相依性） 的類型"b"的檔案。 標準編輯器"B"存在於類型"b"的檔案。 "A"編輯器開啟檔案時"a"it 就會擷取對應的檔案"b"的參考。 不會顯示檔案"b"，但編輯器"A"可以進行修改。 編輯器"A"取得的參考文件資料檔案的"b"從<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法，也會維護檔案 「 b 」 的編輯鎖定。 完成編輯程式"A"之後修改檔案 「 b 」 可以遞減編輯鎖定仰賴檔案 「 b 」 藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>方法。 您可以省略此步驟中，如果已呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法搭配參數`dwRDTLockType`設定為<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>。  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>不同的編輯器開啟檔案"b"  
 "B"的檔案已經開啟的 編輯器"B""A"編輯器嘗試開啟它時，有兩種不同的案例來處理：  
  
-   如果在相容的編輯器中開啟檔案"b"，您必須編輯程式"A"註冊"b"的檔案使用的文件編輯鎖定<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>方法。 取消註冊文件編輯器"A"是修改檔案 「 b 」 之後，編輯鎖定使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>方法。  
  
-   如果以不相容的方式開啟檔案"b"，您可以讓嘗試的開啟檔案"b""A"失敗，或者您可以讓檢視與編輯器開啟並顯示適當的錯誤訊息部分的"A"關聯的編輯器。 錯誤訊息應該指示使用者關閉不相容的編輯器中的檔案"b"，然後再重新開啟檔案"a"使用編輯器"A"。 您也可以實作[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>來提示使用者關閉檔案"b"不相容的編輯器中開啟。 如果使用者關閉檔案"b"，開啟檔案"A""a"的編輯器會繼續正常執行。  
  
## <a name="additional-document-edit-lock-considerations"></a>其他文件編輯鎖定考量  
 如果編輯器"A"是唯一的編輯器，可編輯鎖定檔案"b"，"B"編輯器也會保存在文件時的文件編輯鎖定檔案"b"，您會得到不同的行為。 在  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，**類別設計工具**是不會保留編輯鎖定相關聯的程式碼檔案的視覺化設計工具的範例。 也就是說，如果使用者已在 [設計] 檢視中開啟類別圖，而且相關聯的程式碼檔案，同時開啟，而且使用者修改的程式碼檔案，但不會儲存所做的變更，所做的變更也會遺失加入類別圖 (.cd) 檔案。 如果**類別設計工具**具有唯一的文件編輯鎖定的程式碼檔案，不會要求使用者儲存的變更，關閉程式碼檔案時。 IDE 會要求使用者儲存變更，只有在使用者關閉之後，才**類別設計工具**。 已儲存的變更會反映在這兩個檔案。 如果兩個**類別設計工具**且程式碼檔案編輯器保留文件編輯鎖定程式碼檔案，則系統會提示使用者儲存的程式碼檔案或表單關閉時。 此時，儲存的變更會反映在表單和程式碼檔案。 如需有關類別圖的詳細資訊，請參閱[使用類別圖表 （類別設計工具）](../ide/working-with-class-diagrams-class-designer.md)。  
  
 請注意，是否您需要將編輯鎖定放在非編輯器的文件上，您必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>介面。  
  
 許多次的 UI 設計工具以程式設計方式修改程式碼檔案會對多個檔案進行變更。 在此情況下<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>方法會處理一或多個文件，藉由儲存**您要儲存下列項目的變更嗎？**  對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [執行文件資料表](../extensibility/internals/running-document-table.md)   
 [持續性和執行的 document 資料表](../extensibility/internals/persistence-and-the-running-document-table.md)