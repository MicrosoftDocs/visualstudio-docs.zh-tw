---
title: 執行文件資料表 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ea32df892efa47c91d8292bdc9065080318a059
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044602"
---
# <a name="running-document-table"></a>執行中的文件資料表
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE 會維護呼叫執行的文件資料表 (RDT) 的內部結構中所有目前開啟的文件的清單。 此清單包含所有開啟的文件在記憶體中，不論是否目前正在編輯這些文件。 文件是會保留，包括檔案的專案或主要專案檔 （例如.vcxproj 檔案） 中的任何項目。  
  
## <a name="elements-of-the-running-document-table"></a>執行文件表格的項目  
 執行文件資料表包含下列項目。  
  
|項目|描述|  
|-------------|-----------------|  
|文件 moniker|字串，可唯一識別文件資料物件。 這會是可管理的檔案 (例如 C:\MyProject\MyFile) 的專案系統的絕對檔案路徑。 這個字串也會儲存在檔案系統，例如在資料庫中的預存程序以外的存放區中的專案。 在此情況下，專案系統可以發明的唯一字串，它可以辨識和可能剖析以判斷如何儲存文件。|  
|階層擁有者|擁有文件，表示的階層物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面。|  
|項目識別碼|在階層內的特定項目的項目識別項。 這個值是擁有這份文件的階層中的所有文件中的唯一性，但此值不保證是唯一的不同階層。|  
|文件資料物件|這是最小值， `IUnknown`<br /><br /> 物件。 IDE 不需要任何特定的介面之外`IUnknown`自訂編輯器的文件資料物件的介面。 不過，對於標準編輯器中，編輯器實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>介面，才能處理檔案從專案的持續性呼叫。 如需詳細資訊，請參閱 <<c0> [ 儲存標準文件](../../extensibility/internals/saving-a-standard-document.md)。|  
|旗標|項目新增至 RDT 時，可以指定旗標，以控制是否將儲存的文件，是否套用的讀取或編輯的鎖定，並依此類推。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 列舉。|  
|編輯鎖定計數|編輯鎖定計數。 編輯鎖定指出某些編輯器已開啟進行編輯的文件。 時的編輯鎖定計數轉換為零，會提示使用者儲存文件，如果已修改。 例如，每次您使用編輯器中開啟文件**開新視窗**命令時，編輯鎖定會加入在 RDT 該文件。 為了讓設定編輯鎖定，文件必須有階層，或項目識別碼。|  
|讀取鎖定計數|讀取鎖定的計數。 讀取的鎖定會指出，正在透過一些機制，例如精靈中讀取文件。 讀取的鎖定會保留在文件存留在 RDT 同時表示無法編輯文件。 您可以設定讀取的鎖定，即使文件不會有階層或項目識別碼。 這項功能可讓您在記憶體中開啟文件，並進入 RDT 中沒有任何階層所擁有的文件。 這項功能很少使用。|  
|鎖定持有者|執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>介面。 鎖定持有者會實作功能，例如精靈，可開啟及編輯外部編輯器的文件。 鎖定持有者可讓要新增的編輯鎖定文件以防止文件正在關閉，但仍被編輯的功能。 一般來說，編輯鎖定只會新增文件視窗 （也就是編輯器）。|  
  
 RDT 中的每個項目具有唯一的階層或項目 ID 與其相關聯，這通常會對應至專案中的一個節點。 可供編輯的所有文件通常是由某階層擁有。 RDT 中所做的項目會控制哪一個專案，或-更精確地說，哪一個階層，目前擁有要編輯的文件資料物件。 RDT 中使用的資訊，IDE 可以防止文件一次開啟多個專案。  
  
 階層也會控制資料的持續性，並使用 RDT 中的資訊來更新**儲存**並**另存新檔**對話方塊。 當使用者修改文件，然後選擇 **結束**命令**檔案**功能表中，IDE 可以會提示他們具有**儲存變更**對話方塊以顯示所有專案和目前修改的專案項目。 這可讓使用者選擇其中一個要儲存的文件。 若要儲存的文件清單 （也就是這些文件有變更） 從 RDT 產生。 您會看到在任何項目**儲存變更**對話方塊中，在結束應用程式時應該在 RDT 的記錄。 RDT 協調儲存的文件，及是否會提示使用者儲存的相關作業使用指定的旗標項目，每個文件中的值。 如需有關 RDT 旗標的詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>列舉型別。  
  
## <a name="edit-locks-and-read-locks"></a>編輯鎖定和讀取鎖定  
 編輯鎖定和讀取的鎖定位於 RDT。 文件視窗的遞增和遞減編輯鎖定。 因此，當使用者開啟新的文件視窗，編輯鎖定計數遞增一。 當編輯鎖定數目到達零時，階層會接收信號，以保存資料或儲存為相關聯的文件。 階層可接著保留任何的方式，包括保存為檔案或儲存機制中的項目中的資料。 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A>方法中的<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>介面，以新增編輯鎖定和讀取鎖定，而<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>方法來移除這些鎖定。  
  
 一般來說，文件視窗中，編輯器會具現化，視窗框架會自動新增文件的編輯鎖定 RDT 中。 不過，如果您建立文件的自訂檢視，不使用標準的文件視窗 (也就是它不會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>介面)，則您需要設定您自己的編輯鎖定。 例如，在精靈中，編輯文件而不需要在編輯器中開啟。 為了讓文件鎖定，來開啟精靈和類似的實體，這些實體必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>介面。 若要註冊您的文件鎖定持有者，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>方法，並傳入您<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>實作。 如此一來，是在 RDT 中將您的文件鎖定持有者。 實作文件鎖定持有者的另一種情況是如果您開啟的文件，透過特殊的工具視窗。 在此情況下，您就無法將工具視窗的關閉文件項目。 不過，註冊為 RDT 中的文件鎖定持有者，IDE 可以呼叫您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A>提示關閉文件的方法。  
  
## <a name="other-uses-of-the-running-document-table"></a>執行 Document 資料表的其他用法  
 在 IDE 中的其他實體使用 RDT 取得文件的相關資訊。 比方說，原始檔控制管理員會使用 RDT 來告訴系統它會取得檔案的最新版本之後，重新載入在編輯器中，文件。 若要這樣做，原始檔控制管理員會查閱 RDT，若要查看其中是否有任何開啟中的檔案。 如果是，則原始檔控制管理員會先檢查以查看階層實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法。 如果專案不會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法，則原始檔控制管理員檢查實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>文件資料物件直接的方法。  
  
 IDE 也使用 RDT resurface （提到最上層） 開啟的文件，如果使用者要求該文件。 如需詳細資訊，請參閱 <<c0> [ 使用 開啟檔案命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)。 若要判斷檔案是否為開啟 RDT 中，執行下列任一種。  
  
- 若要找出項目是否已開啟的文件 moniker （也就是完整的文件路徑） 的查詢。  
  
- 使用階層或項目識別碼來要求專案系統的完整文件路徑，並接著 RDT 中查閱項目。  
  
## <a name="see-also"></a>另請參閱  
 [RDT_ReadLock 使用方式](../../extensibility/internals/rdt-readlock-usage.md)   
 [持續性與執行中的文件資料表](../../extensibility/internals/persistence-and-the-running-document-table.md)
