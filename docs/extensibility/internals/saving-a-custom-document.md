---
title: "儲存自訂的文件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3cd6f5f45736a7b2578bc9df80a8472d3b50c3d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="saving-a-custom-document"></a>儲存自訂的文件
環境控制代碼**儲存**，**存**，和**全部儲存**命令。 當使用者按一下**儲存**，**存**，**或 全部儲存**上**檔案**功能表或關閉方案，導致 全部儲存，下列程序。  
  
 ![客戶編輯器儲存](../../extensibility/internals/media/private.gif "私用")  
儲存另存新檔，及儲存所有的命令處理的自訂編輯器  
  
 下列步驟將有詳細說明此程序：  
  
1.  如**儲存**和**存**命令，環境會使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務以判斷使用中的文件視窗，因此哪些項目應妥善保存。 主動式文件視窗知道後，環境會尋找執行中文件資料表中的文件的階層指標和項目識別項 （識別碼）。 如需詳細資訊，請參閱[執行中的文件表格](../../extensibility/internals/running-document-table.md)。  
  
     全部儲存 命令，環境會使用的資訊，在執行中的文件表格中編譯儲存的所有項目的清單。  
  
2.  當方案收到<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼叫時，它會逐一選取項目的集合 (也就是多個選取項目所公開<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務)。  
  
3.  選取範圍中每個項目的，解決方案會使用階層指標呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>方法，以判斷是否應該啟用 [儲存] 功能表命令。 如果一或多個項目已變更，會啟用 [儲存] 命令。 如果階層中使用標準編輯器，然後查詢的階層委派中途狀態編輯器 中，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>方法。  
  
4.  已變更每個選取項目的，解決方案會使用階層指標呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>適當的階層上的方法。  
  
     在自訂編輯器中，文件資料物件和專案之間的通訊是私人的。 因此，任何特殊的持續性疑慮處理這兩個物件之間。  
  
    > [!NOTE]
    >  如果您實作您自己的持續性，請務必呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>方法，以節省時間。 這個方法會檢查並確定它是安全儲存檔案 （例如，檔案不是唯讀）。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)