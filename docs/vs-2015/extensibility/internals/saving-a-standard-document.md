---
title: 正在儲存標準文件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5040070287db6486fa62c9010fe023be31b04cbe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198076"
---
# <a name="saving-a-standard-document"></a>儲存標準文件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

環境會處理儲存、 另存新檔，並儲存所有命令。 當使用者選取**儲存**，**另存新檔**，或**全部儲存**從**檔案**功能表或關閉方案，因而導致**全部儲存**，執行下列程序。  
  
 ![標準編輯器](../../extensibility/internals/media/public.gif "公用")  
儲存另存新檔，及儲存所有的命令處理的標準編輯器  
  
 下列步驟會詳細說明此程序：  
  
1. 當**儲存**並**另存新檔**選取命令時，環境會使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務以判斷使用中的文件視窗，並因此項目應該儲存。 現用文件視窗知道後，環境就會尋找文件中執行的 document 資料表的階層指標和項目識別項 (itemID)。 如需詳細資訊，請參閱 <<c0> [ 執行文件表格](../../extensibility/internals/running-document-table.md)。  
  
    當**全部儲存**選取命令時，環境中執行的 document 資料表使用的資訊，以編譯儲存的所有項目的清單。  
  
2. 當解決方案收到<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼叫時，它會逐一選取項目組 (也就是由多重選取<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務)。  
  
3. 每個項目選取範圍中，解決方案會使用階層指標來呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>方法，以判斷是否**儲存**應該啟用功能表命令。 如果一或多個項目已變更，則**儲存**已啟用命令。 如果階層會使用標準的編輯器，然後查詢的階層委派中途至編輯器的狀態呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>方法。  
  
4. 在已經變更每個選取的項目，解決方案會使用階層指標來呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>適當的階層上的方法。  
  
    通常會使用標準的編輯器來編輯文件階層。 在此情況下，文件資料物件應該支援該編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>介面。 在收到<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>方法呼叫中，專案應該告知呼叫正在儲存文件編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A>文件資料物件上的方法。 編輯器可讓環境，以處理**另存新檔**對話方塊中，藉由呼叫`Query Service`如<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>介面。 這會傳回的指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>介面。 編輯器必須再呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>方法，將指標傳遞至編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>藉由實作`pPersistFile`參數。 環境再執行儲存作業，並提供**另存新檔**編輯器的對話方塊。 環境然後回呼至編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>。  
  
5. 如果使用者嘗試儲存未命名的文件 （也就是先前未儲存文件），則會實際執行 [另存新檔] 命令。  
  
6. 另存新檔 命令中，環境會顯示 另存新檔 對話方塊，提示使用者輸入檔案名稱。  
  
    如果已變更的檔案名稱，則階層負責更新文件框架的快取資訊，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument)。  
  
   如果**另存新檔**命令會將移動的文件的位置和階層機密文件的位置，則階層會負責關閉開啟的文件視窗的擁有權交給另一個階層。 比方說，會發生這個錯誤的檔案是否為內部或外部的檔案 （其他檔案） 相對於專案，專案會追蹤。 若要將檔案的擁有權變更為其他檔案專案中使用下列程序。  
  
## <a name="changing-file-ownership"></a>變更檔案擁有權  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>若要將檔案擁有權變更為其他檔案專案  
  
1. 查詢服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>介面。  
  
     指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>會傳回。  
  
2. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A>(`pszMkDocumentNew`， `punkWindowFrame`) 方法，以將文件傳送至新的階層。 執行 [另存新檔] 命令的階層架構會呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)
