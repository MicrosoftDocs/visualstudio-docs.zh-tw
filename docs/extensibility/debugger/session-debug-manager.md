---
title: 工作階段調試管理員 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953b4e948ef5e21531a3e73bceed3a363ed3cec5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712876"
---
# <a name="session-debug-manager"></a>工作階段除錯管理員
工作階段除錯管理員 (SDM) 管理任意數量的除錯引擎 (DE),這些引擎正在任意數量的跨任意數量的電腦在多個程序中調試任意數量的程式。 除了作為調試引擎多路複用器外,SDM 還為 IDE 提供了調試會話的統一視圖。

## <a name="session-debug-manager-operation"></a>工作階段除錯管理員操作
 工作階段除錯管理員 (SDM) 管理 DE。 可以同時在計算機上運行多個調試引擎。 要對 DE 進行多路複用,SDM 會從 DE 包裝多個介面,並將它們作為單個介面公開給 IDE。

 為了提高性能,某些介面不會進行多路複用。 相反,它們直接從 DE 使用,並且對這些介面的調用不會透過 SDM。 例如,與記憶體、代碼和文檔上下文一起使用的介面不會進行多路複用,因為它們是指特定 DE 調試的特定程式中的特定指令、記憶體或文檔。 沒有其他 DE 需要參與該級別的通信。

 並非所有上下文都如此。 對表達式計算上下文介面的調用通過 SDM。 在運算式計算期間,SDM 會包裝它給IDE的[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面,因為計算該運算式時,它可能涉及多個正在調試程式的IDE,這些進程可能在同一線程上運行。

 SDM 通常充當委派機制,但它可以充當廣播機制。 例如,在表達式計算期間,SDM 充當廣播機制,通知所有 D 可以運行指定線程上的代碼。 同樣,當 SDM 收到停止事件時,它將廣播到它們應停止運行的節目。 調用步驟時,SDM 會廣播到它們可以繼續運行的程式。 斷點也會廣播到每個 DE。

 SDM 不跟蹤當前程序、線程或堆疊幀。 進程、程式和線程資訊與特定調試事件一起發送到 SDM。

## <a name="see-also"></a>另請參閱
- [偵錯引擎](../../extensibility/debugger/debug-engine.md)
- [除錯器元件](../../extensibility/debugger/debugger-components.md)
- [除錯器上下文](../../extensibility/debugger/debugger-contexts.md)
