---
title: "正在儲存標準文件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0cdfb4631420f6803e6434bd67b93bd713cfd1f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="saving-a-standard-document"></a>正在儲存標準文件
環境會處理儲存、 另存新檔，以及儲存所有命令。 當使用者選取**儲存**，**存**，或**全部儲存**從**檔案**功能表或關閉方案，導致**儲存所有**，執行下列程序。  
  
 ![標準編輯器](../../extensibility/internals/media/public.gif "公用")  
儲存另存新檔，及儲存所有的命令處理標準編輯器  
  
 下列步驟將有詳細說明此程序：  
  
1.  當**儲存**和**另存新檔**選取命令，環境會使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務以判斷使用中的文件視窗，因此哪些項目應妥善保存。 主動式文件視窗知道後，環境會尋找執行中文件資料表中的文件的階層指標和項目識別項 （識別碼）。 如需詳細資訊，請參閱[執行中的文件表格](../../extensibility/internals/running-document-table.md)。  
  
     當**全部儲存**選取命令，環境中執行的 document 資料表使用的資訊來編譯儲存的所有項目的清單。  
  
2.  當方案收到<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼叫時，它會逐一選取項目的集合 (也就是多個選取項目所公開<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務)。  
  
3.  選取範圍中每個項目的，解決方案會使用階層指標呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>方法，以判斷是否**儲存**應該已啟用功能表命令。 如果一或多個項目已變更，然後在**儲存**已啟用命令。 如果階層中使用標準編輯器，然後查詢的階層委派中途狀態編輯器 中，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>方法。  
  
4.  已變更每個選取項目的，解決方案會使用階層指標呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>適當的階層上的方法。  
  
     通常會使用標準的編輯器來編輯文件階層。 在此情況下，文件資料物件的編輯器應該支援<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>介面。 在收到<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>呼叫方法時，專案應該告知呼叫正在儲存文件編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A>文件資料物件上的方法。 編輯器可讓處理環境**存**對話方塊中的，藉由呼叫`Query Service`如<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>介面。 這將指標傳回至<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>介面。 然後呼叫編輯器 中，必須<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>方法，將指標傳遞至編輯器的<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>藉由實作`pPersistFile`參數。 環境之後執行儲存作業，並提供**存**編輯器 對話方塊。 環境然後回撥的編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>。  
  
5.  如果使用者嘗試儲存未命名的文件 （也就是先前未儲存文件），會實際執行 [另存新檔] 命令。  
  
6.  另存新檔命令中，環境會顯示 [另存新檔] 對話方塊，提示使用者輸入檔案名稱。  
  
     如果已變更的檔案名稱，則階層負責更新文件框架的快取的資訊呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument)。  
  
 如果**存**命令會將文件，位置且階層機密文件位置，然後階層負責處理關閉開啟的文件視窗的擁有權至另一個階層。 例如，會發生這個專案會追蹤檔案是否為內部或外部的檔案 （其他檔案） 相對於專案。 若要將檔案的擁有權變更為其他檔案專案中使用下列程序。  
  
## <a name="changing-file-ownership"></a>變更檔案的擁有權  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>若要將檔案擁有權變更為其他檔案專案  
  
1.  查詢服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>介面。  
  
     指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>傳回。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A>(`pszMkDocumentNew`， `punkWindowFrame`) 方法來傳輸至新階層的文件。 執行 [另存新檔] 命令的階層架構會呼叫這個方法。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)