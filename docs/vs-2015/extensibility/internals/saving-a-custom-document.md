---
title: 儲存自訂文件 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1402dd3ed2acf6c4801953c59f14d2454b95c01d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235725"
---
# <a name="saving-a-custom-document"></a>儲存自訂文件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

環境控制代碼**儲存**，**另存新檔**，並**全部儲存**命令。 當使用者按一下**儲存**，**另存新檔**，**或 全部儲存**上**檔案**功能表或關閉方案，導致 全部儲存，下列處理程序就會發生。  
  
 ![客戶編輯器儲存](../../extensibility/internals/media/private.gif "私用")  
儲存另存新檔，及儲存所有的命令處理的自訂編輯器  
  
 下列步驟會詳細說明此程序：  
  
1.  針對**儲存**並**另存新檔**命令，在此環境使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務以判斷使用中的文件視窗，並因此項目應該儲存。 現用文件視窗知道後，環境就會尋找文件中執行的 document 資料表的階層指標和項目識別項 (itemID)。 如需詳細資訊，請參閱 <<c0> [ 執行文件表格](../../extensibility/internals/running-document-table.md)。  
  
     全部儲存 命令，環境會使用的資訊，在執行中的文件表格中編譯儲存的所有項目的清單。  
  
2.  當解決方案收到<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼叫時，它會逐一選取項目組 (也就是由多重選取<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務)。  
  
3.  每個項目選取範圍中，解決方案會使用階層指標來呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>方法，以判斷是否應該啟用 [儲存] 功能表命令。 如果一或多個項目已變更，則會啟用 [儲存] 命令。 如果階層會使用標準的編輯器，然後查詢的階層委派中途至編輯器的狀態呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>方法。  
  
4.  在已經變更每個選取的項目，解決方案會使用階層指標來呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>適當的階層上的方法。  
  
     自訂編輯器，在文件資料物件和專案之間的通訊都是私用的。 因此，任何特殊的持續性的問題被處理這兩個物件之間。  
  
    > [!NOTE]
    >  如果您實作您自己的持續性時，務必呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>方法，以節省時間。 這個方法會檢查以確定它是安全儲存檔案 （例如，檔案不是唯讀）。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)

