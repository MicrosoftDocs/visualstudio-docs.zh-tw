---
title: 儲存標準檔 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df93813d339a45689845b82fe4f5a185301b6c74
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724090"
---
# <a name="saving-a-standard-document"></a>儲存標準文件
環境會處理 [儲存]、[另存新檔] 和 [儲存所有] 命令。 當使用者**選取 [檔案**] 功能表中的 [**儲存**]、[**另**存新檔] 或 [**全部儲存**] 時，或關閉解決方案，導致**全部儲存**，就會發生下列進程。

 ![標準編輯器](../../extensibility/internals/media/public.gif "Public")儲存、另存新檔，並儲存標準編輯器的所有命令處理

 此程式會在下列步驟中詳細說明：

1. 選取 [**儲存**] 和 [**另存**新檔] 命令時，環境會使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服務來判斷活動文件視窗，以及應該儲存的專案。 一旦知道活動文件視窗，環境就會在執行中的檔資料表中尋找檔的階層指標和專案識別碼（itemID）。 如需詳細資訊，請參閱執行[檔資料表](../../extensibility/internals/running-document-table.md)。

    選取 [**全部儲存**] 命令時，環境會使用執行檔資料表中的資訊來編譯要儲存的所有專案清單。

2. 當解決方案收到 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 呼叫時，它會逐一查看所選取專案的集合（也就是由 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服務公開的多個選項）。

3. 在選取範圍內的每個專案上，解決方案會使用階層指標來呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 方法，以判斷是否應該啟用 [**儲存**] 功能表命令。 如果一或多個專案已變更，則會啟用 [**儲存**] 命令。 如果階層使用標準編輯器，則階層會藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> 方法，將已變更狀態的查詢委派給編輯器。

4. 在每個已變更的專案上，解決方案會使用階層指標，在適當的階層上呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 方法。

    階層通常會使用標準編輯器來編輯檔。 在此情況下，該編輯器的檔資料物件應該支援 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 介面。 收到 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 方法呼叫時，專案應該在檔資料物件上呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> 方法，以通知編輯器該檔正在儲存。 編輯器可以藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 介面的 `Query Service`，讓環境處理 [**另存**新檔] 對話方塊。 這會傳回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 介面的指標。 然後，編輯器必須呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> 方法，藉由 `pPersistFile` 參數，將指標傳遞至編輯器的 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 執行。 環境接著會執行儲存作業，並提供編輯器的 [**另存**新檔] 對話方塊。 環境接著會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 回呼至編輯器。

5. 如果使用者嘗試儲存未命名的檔（也就是先前未儲存的檔），則實際上會執行 [另存新檔] 命令。

6. 針對 [另存新檔] 命令，環境會顯示 [另存新檔] 對話方塊，提示使用者輸入檔案名。

    如果檔案的名稱已變更，則階層會負責藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> （VSFPROPID_MkDocument）來更新檔框架的快取資訊。

   如果 [**另存**新檔] 命令移動檔的位置，而且階層對檔位置很敏感，則階層會負責將開啟文件視窗的擁有權交給另一個階層。 例如，如果專案追蹤檔案是否為與專案相關的內部或外部檔案（其他檔案），就會發生這種情況。 使用下列程式，將檔案的擁有權變更為 [其他檔案] 專案。

## <a name="changing-file-ownership"></a>變更檔案擁有權

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>將檔案擁有權變更為其他檔案專案

1. @No__t_0 介面的查詢服務。

     傳回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> 的指標。

2. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> （`pszMkDocumentNew`，`punkWindowFrame`）方法，將檔傳送至新的階層。 執行 [另存新檔] 命令的階層會呼叫這個方法。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)