---
title: 儲存自訂檔 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf67335b6a12b966eb148b3f8dcaf16339e2a29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724079"
---
# <a name="saving-a-custom-document"></a>儲存自訂文件
環境會處理 [**儲存**]、[**另存**新檔] 和 [**儲存所有**] 命令。 當使用者**按一下 [檔案**] 功能表上的 [**儲存**]、[**另**存新檔]**或 [全部儲存**]，或關閉解決方案，並產生 [全部儲存] 時，就會發生下列進程。

 ![客戶編輯器儲存](../../extensibility/internals/media/private.gif "Private")[儲存]、[另存新檔] 和 [儲存自訂編輯器的所有命令處理]

 此程式會在下列步驟中詳細說明：

1. 針對 [**儲存**] 和 [**另存**新檔] 命令，環境會使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服務來判斷活動文件視窗，以及應該儲存的專案。 一旦知道活動文件視窗，環境就會在執行中的檔資料表中尋找檔的階層指標和專案識別碼（itemID）。 如需詳細資訊，請參閱執行[檔資料表](../../extensibility/internals/running-document-table.md)。

     針對 [全部儲存] 命令，環境會使用 [執行檔] 資料表中的資訊來編譯要儲存的所有專案清單。

2. 當解決方案收到 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 呼叫時，它會逐一查看所選取專案的集合（也就是由 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服務公開的多個選項）。

3. 在選取範圍內的每個專案上，解決方案會使用階層指標來呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 方法，以判斷是否應該啟用 [儲存] 功能表命令。 如果一或多個專案已變更，則會啟用 [儲存] 命令。 如果階層使用標準編輯器，則階層會藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> 方法，將已變更狀態的查詢委派給編輯器。

4. 在每個已變更的專案上，解決方案會使用階層指標，在適當的階層上呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 方法。

     在自訂編輯器的情況下，檔資料物件與專案之間的通訊是私用的。 因此，任何特殊的持續性考慮都會在這兩個物件之間處理。

    > [!NOTE]
    > 如果您執行自己的持續性，請務必呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 方法來節省時間。 這個方法會檢查以確定儲存檔案是安全的（例如，檔案不是唯讀檔案）。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)