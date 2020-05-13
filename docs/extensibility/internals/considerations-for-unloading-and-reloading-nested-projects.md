---
title: 卸載和重新載入嵌套專案的注意事項 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab705953eea1fcac99883bb4f88c0e95eced108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709294"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>卸載並重新載入嵌套項目的注意事項

實現嵌套項目類型時,在卸載和重新載入專案時必須執行其他步驟。 要正確通知偵聽器到解決方案事件,必須正確引發`OnBeforeUnloadProject``OnAfterLoadProject`和事件。

引發這些事件的一個原因是原始程式碼控制 (SCC)。 您不希望 SCC 從伺服器中刪除這些項目,然後將其添加為*新*專案(如果 SCC 中有操作`Get`)。 在這種情況下,將從 SCC 載入新檔。 您必須卸載並重新載入所有檔,以防它們不同。

原始碼控制呼叫`ReloadItem`。 實現要<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>調`OnBeforeUnloadProject`用的介面`OnAfterLoadProject`並 刪除專案並重新創建它。 以這種方式實現介面時,SCC 會被告知專案已暫時刪除並再次添加。 因此,SCC 不會在專案上運行,就像*項目實際上*已被刪除並重新添加一樣。

## <a name="reload-projects"></a>重新載入項目

要支援重新載入嵌套專案,可以實現 該<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法 。 在實現`ReloadItem`中 ,將關閉嵌套專案,然後重新創建這些專案。

通常,在重新載入專案時,IDE 會<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>引發和事件。 但是,對於刪除並重新載入的嵌套專案,父專案將啟動進程,而不是 IDE。 由於父專案不引發解決方案事件,並且IDE沒有關於進程初始化的資訊,因此不會引發這些事件。

要處理此過程,父專案調用`QueryInterface`<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>介面。 `IVsFireSolutionEvents`具有告訴 IDE`OnBeforeUnloadProject`引發 事件以卸載嵌套專案`OnAfterLoadProject`,然後引發 事件以重新載入同一專案的函數。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [巢狀專案](../../extensibility/internals/nesting-projects.md)
