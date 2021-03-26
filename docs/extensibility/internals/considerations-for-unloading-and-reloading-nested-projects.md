---
title: 卸載和重載嵌套專案
description: 瞭解在 Visual Studio 中卸載和重載嵌套專案時必須執行的其他步驟。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9852454d487ab2a7ee08218c9712aa0afc1467ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057067"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>卸載和重載嵌套專案的考慮

當您執行嵌套專案類型時，當您卸載並重載專案時，必須執行額外的步驟。 若要正確通知接聽程式的解決方案事件，您必須正確地引發 `OnBeforeUnloadProject` 和 `OnAfterLoadProject` 事件。

引發這些事件的其中一個原因是 (SCC) 的原始程式碼控制。 您不想要讓 SCC 刪除伺服器中的專案，並在從 SCC 進行作業時將它們新增回 *新* 的 `Get` 。 在此情況下，會從 SCC 載入新的檔案。 如果有不同的檔案，您就必須卸載並重載所有檔案。

原始程式碼控制呼叫 `ReloadItem` 。 執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> 要呼叫的介面 `OnBeforeUnloadProject` ，並 `OnAfterLoadProject` 刪除專案並重新建立。 當您以這種方式執行介面時，系統會通知 SCC 已暫時刪除專案，並再次新增。 因此，SCC 無法在專案上操作，如同 *實際* 刪除和重新加入專案一樣。

## <a name="reload-projects"></a>重載專案

若要支援重載嵌套專案，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 方法。 在的執行中 `ReloadItem` ，您會關閉嵌套專案，然後重新建立它們。

通常在重載專案時，IDE 會引發 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> 事件。 但是，如果是刪除並重載的嵌套專案，父專案就會起始進程，而不是 IDE。 因為父專案不會引發方案事件，而且 IDE 沒有進程初始化的相關資訊，所以不會引發事件。

為了處理這個程式，父專案會呼叫 `QueryInterface` 介面上的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> 。 `IVsFireSolutionEvents` 的函式會告訴 IDE 引發 `OnBeforeUnloadProject` 事件以卸載嵌套的專案，然後引發 `OnAfterLoadProject` 事件以重載相同的專案。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [嵌套專案](../../extensibility/internals/nesting-projects.md)
