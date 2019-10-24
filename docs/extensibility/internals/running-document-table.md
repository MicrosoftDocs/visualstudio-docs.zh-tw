---
title: 正在執行檔資料表 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4645899e8c4cd73758316a3c2a8d74ccb169aa2d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724063"
---
# <a name="running-document-table"></a>執行中的文件資料表
IDE 會以名為執行檔資料表（RDT）的內部結構來維護所有目前開啟的檔案清單。 這份清單包含記憶體中所有開啟的檔，不論目前是否正在編輯這些檔。 檔是任何保存的專案，包括專案中的檔案或主要專案檔（例如，.vcxproj 檔案）。

## <a name="elements-of-the-running-document-table"></a>執行檔資料表的元素
 執行中的檔資料表包含下列專案。

|項目|描述|
|-------------|-----------------|
|檔標記|可唯一識別檔資料物件的字串。 這會是管理檔案之專案系統的絕對檔案路徑（例如，C:\MyProject\MyFile）。 這個字串也用於儲存于檔案系統以外之存放區中的專案，例如資料庫中的預存程式。 在此情況下，專案系統可以建立一個可辨識的唯一字串，而且可能會進行剖析以判斷如何儲存檔。|
|階層擁有者|擁有檔的階層物件，如 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 介面所表示。|
|專案識別碼|階層中特定專案的專案識別碼。 這個值在擁有這份檔的階層中的所有檔之間是唯一的，但此值不保證在不同的階層之間是唯一的。|
|檔資料物件|這是最小的 `IUnknown`<br /><br /> 物件。 IDE 不需要自訂編輯器的檔資料物件之 `IUnknown` 介面以外的任何特定介面。 不過，針對標準編輯器，需要編輯器的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 介面的執行，才能處理來自專案的檔案持續性呼叫。 如需詳細資訊，請參閱[儲存標準檔](../../extensibility/internals/saving-a-standard-document.md)。|
|旗標|當專案新增至 RDT 時，可以指定是否要儲存檔、是否套用讀取或編輯鎖定等等的旗標。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 列舉。|
|編輯鎖定計數|編輯鎖定的計數。 編輯鎖定表示某些編輯器已開啟檔進行編輯。 當編輯鎖定的計數轉換成零時，系統會提示使用者儲存檔（如果已修改的話）。 例如，每次您使用 [**新增視窗]** 命令在編輯器中開啟檔時，就會在 RDT 中新增該檔的編輯鎖定。 為了設定編輯鎖定，檔必須具有階層或專案識別碼。|
|讀取鎖定計數|讀取鎖定的計數。 「讀取鎖定」表示會透過一些機制（例如 wizard）來讀取檔。 讀取鎖定會在 RDT 中保存檔，同時指出無法編輯檔。 即使檔沒有階層或專案識別碼，您也可以設定讀取鎖定。 這項功能可讓您在記憶體中開啟檔，並在沒有任何階層所擁有檔的 RDT 中輸入。 這項功能很少使用。|
|鎖定持有者|@No__t_0 介面的實例。 鎖定持有者是由功能所執行，例如在編輯器之外開啟和編輯檔的程式。 鎖定持有者可讓功能在檔中加入編輯鎖定，以防止檔在仍在編輯時關閉。 一般來說，編輯鎖定只會由文件視窗（也就是編輯器）新增。|

 RDT 中的每個專案都有與其相關聯的唯一階層或專案識別碼，這通常會對應至專案中的一個節點。 所有可供編輯的檔通常都是由階層所擁有。 在 RDT 中進行的專案，可控制哪些是目前擁有正在編輯之檔資料物件的階層（或更精確）。 藉由使用 RDT 中的資訊，IDE 可以防止一次有一個以上的專案開啟檔。

 階層也會控制資料的持續性，並使用 RDT 中的資訊來更新 [**儲存**] 和 [**另存**新檔] 對話方塊。 當使用者修改**檔**，然後從 [檔案] 功能表中選擇 [結束 **] 命令時**，IDE 會以 [**儲存變更**] 對話方塊提示它們，以顯示目前已修改的所有專案和專案專案。 這可讓使用者選擇要儲存的檔。 要儲存的檔案清單（也就是那些有變更的檔）是從 RDT 產生的。 在結束應用程式時，您預期會在 [**儲存變更**] 對話方塊中看到的任何專案，都應該具有 RDT 中的記錄。 RDT 會使用每份檔的 Flags 專案中指定的值，來協調儲存的檔，以及使用者是否會收到儲存作業的提示。 如需 RDT 旗標的詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 列舉。

## <a name="edit-locks-and-read-locks"></a>編輯鎖定和讀取鎖定
 [編輯鎖定] 和 [讀取鎖定] 位於 RDT 中。 文件視窗會遞增並遞減編輯鎖定。 因此，當使用者開啟新的文件視窗時，編輯鎖定計數會遞增一。 當編輯鎖定的數目達到零時，會通知階層以保存或儲存相關聯檔的資料。 然後，階層可以任何方式保存資料，包括保存為檔案或存放庫中的專案。 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> 介面中的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> 方法來新增編輯鎖定和讀取鎖定，以及用來移除這些鎖定的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> 方法。

 一般來說，當編輯器的文件視窗具現化時，視窗框架會自動在 RDT 中加入檔的編輯鎖定。 不過，如果您建立的檔不是使用標準檔視窗的自訂視圖（也就是，它不會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 介面），則您必須設定自己的編輯鎖定。 例如，在嚮導中，會編輯檔，而不會在編輯器中開啟。 為了讓檔鎖定能夠由「嚮導」和「類似」實體開啟，這些實體必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 介面。 若要註冊您的檔鎖定持有者，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> 方法，並傳入您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 執行。 這麼做會將您的檔鎖定持有者新增至 RDT。 執行檔鎖定持有者的另一個案例是，如果您透過特殊工具視窗來開啟檔。 在此情況下，您無法讓工具視窗關閉檔。 不過，藉由在 RDT 中註冊為檔鎖定持有者，IDE 可以呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> 方法的執行，以提示檔的關閉。

## <a name="other-uses-of-the-running-document-table"></a>執行檔資料表的其他用途
 IDE 中的其他實體會使用 RDT 來取得檔的相關資訊。 例如，原始檔控制管理員會在取得檔案的最新版本之後，使用 RDT 來指示系統在編輯器中重載檔。 若要這樣做，原始檔控制管理員會查閱 RDT 中的檔案，以查看其中是否有任何開啟的檔案。 如果是，則原始檔控制管理員會先檢查階層是否會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 方法。 如果專案未執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 方法，則原始檔控制管理員會直接在檔資料物件上檢查 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 方法的執行。

 如果使用者要求該檔，IDE 也會使用 RDT 來 resurface （帶入 front）開啟的檔。 如需詳細資訊，請參閱[使用開啟檔案命令顯示](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)檔案。 若要判斷檔案是否已在 RDT 中開啟，請執行下列其中一項動作。

- 查詢檔標記（也就是完整檔路徑），以找出專案是否已開啟。

- 使用 [階層] 或 [專案識別碼]，要求專案系統提供完整的檔路徑，然後在 RDT 中查看專案。

## <a name="see-also"></a>請參閱
- [RDT_ReadLock 使用方式](../../extensibility/internals/rdt-readlock-usage.md)
- [持續性與執行中的文件資料表](../../extensibility/internals/persistence-and-the-running-document-table.md)