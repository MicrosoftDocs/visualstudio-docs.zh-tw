---
title: 正在執行檔資料表 |Microsoft Docs
description: 瞭解 Visual Studio IDE 如何維護執行中的檔資料表，包括記憶體中所有開啟的檔。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d260534d58853afc6b84ba484eb3a806250e2aa6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900404"
---
# <a name="running-document-table"></a>執行中的文件資料表
IDE 會在名為執行檔資料表 (RDT) 的內部結構中，維護所有目前開啟的檔案清單。 這份清單包含記憶體中所有開啟的檔，不論目前是否正在編輯這些檔。 檔是保存的任何專案，包括專案或主要專案檔中的檔案 (例如，.vcxproj 檔案) 。

## <a name="elements-of-the-running-document-table"></a>正在執行之檔資料表的元素
 執行中的檔資料表包含下列專案。

|元素|描述|
|-------------|-----------------|
|檔的名字|可唯一識別檔資料物件的字串。 這會是管理檔案 (之專案系統的絕對檔案路徑，例如 C:\MyProject\MyFile) 。 這個字串也適用于儲存在檔案系統以外之存放區中的專案，例如資料庫中的預存程式。 在此情況下，專案系統可以建立一個可辨識的唯一字串，並可能剖析以判斷如何儲存檔。|
|階層擁有者|擁有檔的階層物件，以 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 介面表示。|
|專案識別碼|階層內特定專案的專案識別碼。 此值在擁有這份檔之階層中的所有檔之間是唯一的，但在不同的階層中，此值不保證是唯一的。|
|Document data 物件|最小值為 `IUnknown`<br /><br /> 物件。 IDE 不需要 `IUnknown` 自訂編輯器的檔資料物件介面以外的任何特定介面。 不過，針對標準編輯器，需要編輯器的介面執行， <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 才能處理來自專案的檔案持續性呼叫。 如需詳細資訊，請參閱 [儲存標準檔](../../extensibility/internals/saving-a-standard-document.md)。|
|Flags|當專案加入至 RDT 時，可以指定是否要儲存檔、是否套用讀取或編輯鎖定等的旗標。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 列舉。|
|編輯鎖定計數|編輯鎖定的計數。 編輯鎖定表示某些編輯器已開啟檔以進行編輯。 當編輯鎖定的計數轉換為零時，系統會提示使用者儲存檔（如果已經修改的話）。 例如，您每次在編輯器中使用 [ **新視窗]** 命令開啟檔時，就會在 RDT 中為該檔新增編輯鎖定。 為了設定編輯鎖定，檔必須有階層或專案識別碼。|
|讀取鎖定計數|讀取鎖定的計數。 讀取鎖定指出正在透過部分機制（例如 wizard）來讀取檔。 讀取鎖定會在 RDT 中保存一份檔，並指出無法編輯檔。 您可以設定讀取鎖定，即使檔沒有階層或專案識別碼也一樣。 這項功能可讓您在記憶體中開啟檔，並在 RDT 中輸入該檔，而不會有任何階層所擁有的檔。 這項功能很少使用。|
|鎖定持有者|介面的實例 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 。 鎖定持有者是由可在編輯器外部開啟和編輯檔的功能所執行。 鎖定持有者可讓功能將編輯鎖定新增至檔，以防止在檔仍在編輯時關閉檔。 一般情況下，編輯鎖定只會由檔視窗新增 (也就是編輯) 。|

 RDT 中的每個專案都有與其相關聯的唯一階層或專案識別碼，通常會對應到專案中的一個節點。 所有可供編輯的檔通常都是由階層所擁有。 在 RDT 中所做的專案，可讓您更精確地控制要編輯的檔資料物件。 使用 RDT 中的資訊，IDE 可以防止一次超過一個專案開啟檔。

 階層也會控制資料的持續性，並使用 RDT 中的資訊來更新 [ **儲存** ] 和 [ **另存** 新檔] 對話方塊。 當使用者修改 **檔**，然後從 [檔案] 功能表中選擇 [結束 **] 命令時**，IDE 會以 [**儲存變更**] 對話方塊提示他們，以顯示目前修改過的所有專案和專案專案。 這可讓使用者選擇要儲存的檔。 要儲存 (的檔案清單，這些檔具有變更) 是從 RDT 產生。 在結束應用程式時，您預期會在 [ **儲存變更** ] 對話方塊中看到的任何專案，都應該在 RDT 中有記錄。 RDT 會協調儲存的檔，以及是否會使用每份檔的旗標專案中指定的值，提示使用者有關儲存作業的提示。 如需 RDT 旗標的詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 列舉。

## <a name="edit-locks-and-read-locks"></a>編輯鎖定和讀取鎖定
 編輯鎖定和讀取鎖定位於 RDT 中。 文件視窗會遞增和遞減編輯鎖定。 因此，當使用者開啟新的文件視窗時，編輯鎖定計數會遞增一。 當編輯鎖定的數目達到零時，會發出階層的信號以保存或儲存相關聯檔的資料。 然後階層可以使用任何方式來保存資料，包括保存為檔案或儲存機制中的專案。 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> 介面中的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> 來加入編輯鎖定和讀取鎖定，以及使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> 方法來移除這些鎖定。

 一般來說，當編輯器的文件視窗具現化時，視窗框架會自動在 RDT 中加入檔的編輯鎖定。 但是，如果您建立不使用標準文件視窗之檔的自訂視圖 (亦即，它並不會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>) 執行介面，那麼您就必須設定自己的編輯鎖定。 例如，在嚮導中，會編輯檔，而不會在編輯器中開啟。 為了讓檔鎖定可由嚮導和類似的實體開啟，這些實體必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 介面。 若要註冊您的檔鎖定持有者，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> 方法，並傳入您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 實作為。 這樣做會將您的檔鎖定持有者新增至 RDT。 執行檔鎖定持有者的另一種情況是，如果您透過特殊的工具視窗開啟檔。 在此情況下，您將無法讓工具視窗關閉檔。 不過，藉由在 RDT 中註冊為檔鎖定持有者，IDE 可以呼叫方法的執行， <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> 以提示您關閉檔。

## <a name="other-uses-of-the-running-document-table"></a>正在執行之檔資料表的其他用途
 IDE 中的其他實體會使用 RDT 來取得檔的相關資訊。 例如，原始檔控制管理員會使用 RDT，告訴系統在編輯器中取得檔案的最新版本之後，重載檔。 若要這樣做，原始檔控制管理員會在 RDT 中查閱檔案，以查看是否有任何這些檔案開啟。 如果是，則原始檔控制管理員會先檢查階層是否已執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 方法。 如果專案未執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 方法，則原始檔控制管理員會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 直接在檔資料物件上檢查方法的實作為。

 如果使用者要求該檔，IDE 也會使用 RDT 來 resurface (將開啟的檔移至前端) 。 如需詳細資訊，請參閱 [使用開啟檔案命令顯示](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)檔案。 若要判斷檔案是否在 RDT 中開啟，請執行下列其中一項動作。

- 查詢檔的標記 (也就是完整檔路徑) ，以找出專案是否已開啟。

- 使用階層或專案識別碼來要求專案系統提供完整的檔路徑，然後在 RDT 中查閱專案。

## <a name="see-also"></a>另請參閱
- [RDT_ReadLock 使用方式](../../extensibility/internals/rdt-readlock-usage.md)
- [持續性與執行中的文件資料表](../../extensibility/internals/persistence-and-the-running-document-table.md)
