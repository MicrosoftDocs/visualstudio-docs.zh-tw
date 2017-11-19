---
title: "執行文件表格 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf66dce40cda2d72757c3a2fe141ed023b286d78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="running-document-table"></a>執行中的文件表格
IDE 會維護呼叫執行中文件資料表 (RDT) 的內部結構中所有目前開啟的文件的清單。 這份清單包括在記憶體中，不論是否目前正在編輯這些文件的所有開啟的文件。 文件是會保存，包括檔案的專案或主要專案檔 （例如，.vcxproj 檔案） 中的任何項目。  
  
## <a name="elements-of-the-running-document-table"></a>執行文件表格的項目  
 執行中文件資料表包含下列項目。  
  
|項目|說明|  
|-------------|-----------------|  
|文件 moniker|字串，可唯一識別文件資料物件。 這會是專案系統所管理的檔案 (例如，C:\MyProject\MyFile) 的絕對檔案路徑。 這個字串也用於儲存在檔案系統，例如資料庫中的預存程序以外的存放區中的專案。 在此情況下，專案系統可以自創唯一的字串，它可以辨識和可能剖析以判斷如何儲存文件。|  
|階層的擁有者|擁有文件中，所表示的階層物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面。|  
|項目識別碼|在階層內的特定項目的項目識別項。 這個值是擁有這份文件的階層中的所有文件中的唯一性，但此值不保證是唯一的不同階層。|  
|文件資料物件|這是最小值，`IUnknown`<br /><br /> 物件。 IDE 不需要任何特定的介面之外`IUnknown`自訂編輯器的文件資料物件的介面。 不過，對於標準編輯器中，編輯器的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>介面，才能處理檔案從專案的持續性呼叫。 如需詳細資訊，請參閱[儲存標準文件](../../extensibility/internals/saving-a-standard-document.md)。|  
|旗標|RDT 中加入項目時，可以指定旗標，以控制是否套用讀取或編輯鎖定時，是否已儲存的文件等等。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 列舉。|  
|編輯鎖定計數|編輯的計數鎖定。 編輯鎖定表示某些編輯器已開啟進行編輯的文件。 當編輯鎖定的計數轉換為零時，會提示使用者儲存文件，如果已修改。 例如，每當您在使用編輯器中開啟文件**新視窗**命令時，該文件 RDT 加入編輯鎖定。 為了要設定之編輯鎖定，或文件必須有階層項目識別碼。|  
|讀取鎖定計數|讀取鎖定的計數。 讀取的鎖定表示文件閱讀一些機制，例如精靈。 讀取的鎖定會保留文件存留在 RDT 同時表示無法編輯的文件。 您可以設定的讀取的鎖定，即使文件沒有階層或項目識別碼。 這項功能可讓您在記憶體中開啟文件，並進入 RDT 中沒有任何階層所擁有的文件。 很少使用這項功能。|  
|鎖定持有者|執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>介面。 鎖定擁有者會實作功能，例如精靈，可開啟及編輯外部編輯器的文件。 鎖定擁有者可編輯鎖定加入要防止文件關閉時仍被編輯的文件的功能。 一般來說，編輯文件視窗 （也就是編輯器） 只會新增鎖定。|  
  
 RDT 中的每個項目都有唯一的階層或關聯，通常會對應至專案中的一個節點的項目 ID。 所有可供編輯的文件通常是階層所擁有。 RDT 中所做的項目控制的專案，或-更精確地 — 哪些階層中，目前擁有正在編輯的文件資料物件。 RDT 中使用的資訊，在 IDE 可以防止文件的多個專案開啟一次。  
  
 階層也會控制資料持續性，並使用 RDT 中的資訊來更新**儲存**和**存**對話方塊。 當使用者修改文件，然後選擇 **結束**命令**檔案**功能表上，在 IDE 提示他們輸入與**儲存變更**對話方塊以顯示所有專案和目前修改的專案項目。 這可讓使用者選擇要儲存的文件。 若要儲存的文件的清單 （也就是這些文件有變更） 從 RDT 產生。 您會看到在任何項目**儲存變更**對話方塊結束應用程式時應該 RDT 中有記錄。 RDT 座標會儲存哪些文件和是否會提示使用者儲存有關作業使用的旗標項目，每個文件中指定的值。 如需有關 RDT 旗標的詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>列舉型別。  
  
## <a name="edit-locks-and-read-locks"></a>編輯鎖定，以及讀取鎖定  
 編輯鎖定，以及讀取的鎖定位於 RDT。 文件視窗遞增和遞減編輯鎖定。 因此，當使用者在開啟新文件視窗中，編輯鎖定計數就會遞增一。 編輯鎖定數目為零時，階層會接收信號，以保存或儲存的資料相關聯的文件。 階層仍將保存的資料，以任何方式，包括保存為檔案，或為儲存機制中的項目。 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A>方法中的<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>介面來新增編輯鎖定及讀取鎖定，而<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>方法來移除這些鎖定。  
  
 一般來說，文件視窗的編輯器是具現化，視窗框架中，自動加入文件的編輯鎖定 RDT。 不過，如果您建立文件的自訂檢視，不使用標準文件視窗 (也就是它不會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>介面)，則您需要設定您自己的編輯鎖定。 例如，在精靈中，編輯文件不在編輯器中開啟。 為了讓文件的鎖定，來開啟精靈和類似的實體，必須實作這些實體<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>介面。 若要註冊您的文件鎖定持有者，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>方法，並傳入您<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>實作。 這樣將 RDT 文件的鎖定擁有者。 實作文件鎖定持有者的另一個案例是如果您開啟文件通過特殊工具視窗。 在本例中，您就無法將工具視窗關閉的文件項目。 不過，註冊為 RDT 在文件鎖定持有者，IDE 就可以呼叫您的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A>提示關閉文件的方法。  
  
## <a name="other-uses-of-the-running-document-table"></a>執行 Document 資料表的其他用法  
 在 IDE 中的其他實體使用 RDT 來取得文件的相關資訊。 例如，原始檔控制管理員會使用 RDT 來告知它會取得檔案的最新版本之後，重新載入文件在編輯器中，系統。 若要這樣做，原始檔控制管理員查詢，看看其中是否開啟 RDT 中的檔案。 如果是，則原始檔控制管理員會先檢查以查看階層實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法。 如果專案沒有實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法，則來源控制管理員檢查的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>直接文件資料物件上的方法。  
  
 IDE 也使用 RDT resurface （提到最上層） 開啟的文件，如果使用者要求該文件。 如需詳細資訊，請參閱[使用開啟的 [檔案] 命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)。 若要判斷檔案是否為開啟 RDT 中，執行下列任一種。  
  
-   若要找出項目是否開啟的文件 moniker （也就是完整的文件路徑） 的查詢。  
  
-   用於向專案系統要求的完整文件路徑，然後接著 RDT 中查閱項目階層或項目識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [RDT_ReadLock 使用量](../../extensibility/internals/rdt-readlock-usage.md)   
 [持續性與執行中的文件資料表](../../extensibility/internals/persistence-and-the-running-document-table.md)