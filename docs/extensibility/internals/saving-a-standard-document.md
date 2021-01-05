---
title: 儲存標準檔 |Microsoft Docs
description: 深入瞭解您新增至 Visual Studio IDE 之專案類型的標準檔所發生的處理常式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81c79ece83bc8aaaf7ca4dd28642de5973ad94c1
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875662"
---
# <a name="saving-a-standard-document"></a>儲存標準文件
環境會處理 [儲存]、[另存新檔] 和 [儲存所有] 命令。 當使用者選取 [ **儲存**]、[ **另存** 新檔] 或 [ **全部儲存** ]，或從 [檔案] 功能表中選取 [全部儲存] **或 [** 全部儲存] **之後，就** 會發生下列進程。

 ![標準編輯器](../../extensibility/internals/media/public.gif "公開") 儲存、另存新檔，並儲存標準編輯器的所有命令處理

 下列步驟會詳細說明此程式：

1. 當選取 [ **儲存** ] 和 [ **另存** 新檔] 命令時，環境會使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服務來決定使用中的文件視窗，以及應儲存的專案。 一旦知道使用中的文件視窗之後，環境會在執行中的檔資料表中尋找檔 (itemID) 的階層指標和專案識別碼。 如需詳細資訊，請參閱執行 [檔資料表](../../extensibility/internals/running-document-table.md)。

    當選取 [ **全部儲存** ] 命令時，環境會使用執行中檔資料表中的資訊來編譯要儲存的所有專案清單。

2. 當解決方案收到呼叫時 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ，會逐一查看一組選取的專案， (也就是服務所公開的多個選項 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>) 。

3. 在選取專案中的每個專案上，方案都會使用階層指標來呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 方法，以判斷是否應該啟用 [ **儲存** ] 功能表命令。 如果有一或多個專案已變更，則會啟用 [ **儲存** ] 命令。 如果階層使用標準編輯器，則階層會藉由呼叫方法，將查詢變更狀態委派給編輯器 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> 。

4. 在每個已變更的專案上，方案都會使用階層指標來呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 適當階層上的方法。

    階層通常會使用標準編輯器來編輯檔。 在此情況下，該編輯器的檔資料物件應該支援 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 介面。 在收到 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 方法呼叫時，專案應該會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> 在檔資料物件上呼叫方法，以通知編輯器正在儲存檔。 編輯器可以藉由呼叫介面，允許環境處理 [ **另存** 新檔] 對話方塊 `Query Service` <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 。 這會傳回介面的指標 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 。 然後，編輯器必須呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> 方法，透過參數將指標傳遞給編輯器的 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 執行 `pPersistFile` 。 然後，環境會執行儲存作業，並提供編輯器的 [ **另存** 新檔] 對話方塊。 然後，環境會使用重新呼叫編輯器 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 。

5. 如果使用者嘗試儲存未命名的檔 (也就是先前未儲存的檔) ，則實際上會執行 [另存新檔] 命令。

6. 若為 [另存新檔] 命令，環境會顯示 [另存新檔] 對話方塊，提示使用者輸入檔案名。

    如果檔案的名稱已變更，則階層會藉由呼叫 (VSFPROPID_MkDocument) ，負責更新檔框架的快取資訊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> 。

   如果 [ **另存** 新檔] 命令移動檔的位置，而且階層對檔位置是敏感的，則階層會負責將開啟文件視窗的擁有權交給另一個階層。 例如，如果專案追蹤檔案是否為內部或外部檔案 (與專案相關的) 其他檔案，就會發生這種情況。 使用下列程式，將檔案的擁有權變更為其他檔案專案。

## <a name="changing-file-ownership"></a>變更檔案擁有權

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>將檔案擁有權變更為其他檔案專案

1. 介面的查詢服務 <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> 。

     傳回的指標 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> 。

2. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew` ， `punkWindowFrame`) 方法，將檔傳送至新的階層。 執行 [另存新檔] 命令的階層會呼叫這個方法。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)
