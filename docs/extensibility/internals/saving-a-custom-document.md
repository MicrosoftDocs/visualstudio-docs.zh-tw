---
title: 儲存自訂檔 |Microsoft Docs
description: 瞭解您加入 Visual Studio IDE 之專案類型的自訂檔所發生的程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a536a5f0f2b1cac09c65079974c661e09e9139ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080914"
---
# <a name="saving-a-custom-document"></a>儲存自訂文件
環境會處理 [ **儲存**]、[ **另存** 新檔] 和 [ **儲存所有** ] 命令。 當使用者按一下 [ **儲存**]、[ **另存** 新檔]，或 [檔案] 功能表上的 [ **全部儲存** ] **或 [** 全部儲存] 或 [關閉方案] 時，就會出現下列程式。

 ![客戶編輯器儲存](../../extensibility/internals/media/private.gif "私人") [儲存]、[另存新檔]，並儲存自訂編輯器的所有命令處理

 下列步驟會詳細說明此程式：

1. 針對 [ **儲存** ] 和 [ **另存** 新檔] 命令，環境 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 會使用服務來決定使用中的文件視窗，以及應儲存的專案。 一旦知道使用中的文件視窗之後，環境會在執行中的檔資料表中尋找檔 (itemID) 的階層指標和專案識別碼。 如需詳細資訊，請參閱執行 [檔資料表](../../extensibility/internals/running-document-table.md)。

     針對 [全部儲存] 命令，環境會使用執行中的檔資料表中的資訊來編譯要儲存的所有專案清單。

2. 當解決方案收到呼叫時 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ，會逐一查看一組選取的專案， (也就是服務所公開的多個選項 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>) 。

3. 在選取專案中的每個專案上，方案都會使用階層指標來呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 方法，以判斷是否應該啟用 [儲存] 功能表命令。 如果有一或多個專案已變更，則會啟用 [儲存] 命令。 如果階層使用標準編輯器，則階層會藉由呼叫方法，將查詢變更狀態委派給編輯器 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> 。

4. 在每個已變更的專案上，方案都會使用階層指標來呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 適當階層上的方法。

     在自訂編輯器的情況下，檔資料物件與專案之間的通訊是私用的。 因此，會在這兩個物件之間處理任何特殊的持續性問題。

    > [!NOTE]
    > 如果您要執行自己的持續性，請務必呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 方法來節省時間。 這個方法會檢查以確定可以安全地儲存檔案 (例如，檔案不是唯讀) 。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)
