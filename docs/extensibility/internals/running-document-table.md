---
title: 執行的文件表 ( C) :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e6aa882921786b1592922372581beae8c4c2443
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705559"
---
# <a name="running-document-table"></a>執行中的文件資料表
IDE 在稱為正在運行的文件表 (RDT) 的內部結構中維護所有當前打開的文檔的清單。 此清單包括記憶體中的所有打開的文件,無論這些文檔當前是否正在編輯。 文件是持久化的任何項,包括專案或主專案檔中的檔(例如 .vcxproj 檔)。

## <a name="elements-of-the-running-document-table"></a>執行的文件表的元素
 正在運行的文件表包含以下條目。

|元素|描述|
|-------------|-----------------|
|文件名稱|唯一識別文件資料物件的字串。 這將是管理檔的專案系統(例如,C:_MyProject_MyFile)的絕對檔路徑。 此字串還用於儲存在檔案系統以外的存儲中的專案,例如資料庫中的存儲過程。 在這種情況下,專案系統可以發明一個唯一的字串,它可以識別並可能解析,以確定如何存儲文檔。|
|層次結構擁有者|擁有文檔的層次結構物件,<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>由介面表示。|
|項目 ID|層次結構中特定項的項標識符。 此值在層次結構中擁有此文檔的所有文檔中是唯一的,但不能保證此值在不同的層次結構中是唯一的。|
|文件資料物件|至少,這是一個`IUnknown`<br /><br /> 物件。 IDE 不需要自定義編輯器文件數據物件`IUnknown`的介面之外的任何特定介面。 但是,對於標準編輯器,需要編輯器實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>介面來處理來自專案的檔持久性調用。 有關詳細資訊,請參閱[儲存標準文件](../../extensibility/internals/saving-a-standard-document.md)。|
|Flags|當項目加入 RDT 時,可以指定控制文件是否儲存、是否應用讀取鎖或編輯鎖的標誌,等等。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 列舉。|
|編輯鎖定計數|編輯鎖計數。 編輯鎖指示某些編輯器打開了文件進行編輯。 當編輯的計數鎖定轉換為零時,如果文檔已被修改,系統將提示使用者保存文檔。 例如,每次使用 **「新建視窗」** 命令在編輯器中打開文檔時,RDT 中都會為該文檔添加編輯鎖。 為了設置編輯鎖,文檔必須具有層次結構或專案 ID。|
|讀取鎖定計數|讀取鎖計數。 讀取鎖表示文檔正在通過某些機制(如嚮導)進行讀取。 讀取鎖在 RDT 中保留文檔處於活動狀態,同時指示無法編輯文檔。 即使文檔沒有層次結構或項目 ID,也可以設置讀取鎖。 此功能允許您在記憶體中打開文檔,並在 RDT 中輸入它,而無需任何層次結構擁有該文檔。 此功能很少使用。|
|鎖架|介面的<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>實例。 鎖架由打開和編輯編輯器外部文檔的嚮導等功能實現。 鎖定持有人允許該功能向文檔添加編輯鎖,以防止文檔在仍在編輯時關閉。 通常,編輯鎖僅由文檔視窗(即編輯器)添加。|

 RDT 中的每個條目都有與其關聯的唯一層次結構或項 ID,通常對應於專案中的一個節點。 所有可用於編輯的文檔通常歸層次結構所有。 RDT 中所做的條目控制當前具有要編輯的文檔數據物件的哪個專案(或者更準確地說)哪個層次結構。 使用 RDT 中的資訊,IDE 可以防止文檔一次被多個項目打開。

 層次結構還控制資料的持久性,並使用 RDT 中的資訊更新 **"保存****和保存為"** 對話框。 當使用者修改文件,然後從 **「檔」** 選單中選擇 **「退出**」命令時,IDE 會用 **「儲存更改」** 對話方塊提示他們,向他們顯示目前的修改的所有項目和專案項。 這允許用戶選擇要保存的文檔。 要保存的文件清單(即具有更改的文檔)是從 RDT 生成的。 您希望在退出應用程式時在「**儲存更改」** 對話框中看到的任何項都應在 RDT 中具有記錄。 RDT 協調保存的文檔以及是否使用每個文件的"標誌"條目中指定的值提示使用者進行保存操作。 有關 RDT 標誌的詳細資訊,請<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>參閱 枚舉。

## <a name="edit-locks-and-read-locks"></a>編輯鎖定與讀取鎖
 編輯鎖和讀取鎖駐留在 RDT 中。 文件視窗遞增並遞減編輯鎖。 因此,當使用者打開新的文檔視窗時,編輯鎖計數將遞增 1。 當編輯鎖數達到零時,將發出策略,以保留或保存關聯文檔的數據。 然後,層次結構可以以任何方式保留數據,包括作為檔或存儲庫中的項保留。 可以使用介面中<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>的方法添加編輯鎖和讀取鎖<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>, 以及刪除這些鎖的方法。

 通常,當實例化編輯器的文檔視窗時,視窗框架會自動在 RDT 中為文檔添加編輯鎖。 但是,如果創建不使用標準文件視窗的文檔的自定義檢視(即,它不實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>介面),則需要設置自己的編輯鎖。 例如,在嚮導中,在不在編輯器中打開的情況下編輯文檔。 為了使嚮導和類似實體打開文檔鎖,這些實體必須<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>實現介面。 要註冊文件鎖定持有者,<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>請呼叫方法並傳遞實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>。 這樣做會將文檔鎖定持有者添加到 RDT。 實現文檔鎖定持有者的另一個方案是,如果通過專用工具窗口打開文檔。 在這種情況下,您無法讓工具視窗關閉文檔。 但是,通過在 RDT 中註冊為文檔鎖定持有者,IDE 可以<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A>調用方法的 實現以提示文檔的關閉。

## <a name="other-uses-of-the-running-document-table"></a>執行的文件表的其他用途
 IDE 中的其他實體使用 RDT 獲取有關文件的資訊。 例如,原始程式碼管理管理器在獲取檔的最新版本後,使用 RDT 告訴系統在編輯器中重新載入文件。 為此,原始程式碼管理管理員會尋找 RDT 中的檔案,以查看這些檔中是否有任何檔案處於打開狀態。 如果是,則源代碼管理管理器首先檢查層次結構是否實現該方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>。 如果專案未實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>該方法,則原始程式碼管理管理員將直接檢查文件資料<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>物件上方法的實現。

 如果使用者請求該文檔,IDE 還使用 RDT 重新顯示(將打開的文檔帶到前面)。 關於詳細資訊,請參考[檔案指令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)。 要確定該檔是否在 RDT 中打開,請執行以下操作之一。

- 查詢文檔名字物件(即完整文檔路徑),以瞭解專案是否打開。

- 使用層次結構或專案 ID 向專案系統詢問完整的文檔路徑,然後在 RDT 中向上查找該專案。

## <a name="see-also"></a>另請參閱
- [RDT_ReadLock 使用方式](../../extensibility/internals/rdt-readlock-usage.md)
- [持續性與執行中的文件資料表](../../extensibility/internals/persistence-and-the-running-document-table.md)
