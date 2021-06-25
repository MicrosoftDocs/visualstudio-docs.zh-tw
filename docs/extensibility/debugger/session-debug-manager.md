---
title: 會話 Debug Manager |Microsoft Docs
description: 深入瞭解會話 debug manager，此管理員可跨任意數目的電腦管理多個進程中的多個偵測引擎偵錯工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 217a2d401e61c58a58d958bb754265a19a2a367d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902081"
---
# <a name="session-debug-manager"></a>會話偵錯工具管理員
會話 debug manager (SDM) 管理任何數目的偵錯工具， (取消在任意數目的電腦之間，對多個進程中任何數目的程式進行偵錯工具的) 。 除了做為「偵測引擎多工器」之外，SDM 也提供對 IDE 之 debug 會話的統一觀點。

## <a name="session-debug-manager-operation"></a>會話 debug manager 作業
 會話 debug manager (SDM) 管理 DE。 電腦上可以同時執行一個以上的 debug engine。 為了多工演算法，SDM 會包裝來自 DEs 的一些介面，並將其公開至 IDE 作為單一介面。

 為了提高效能，某些介面不會多工。 相反地，它們會直接從 DE 中使用，而這些介面的呼叫不會經過 SDM。 例如，搭配記憶體、程式碼和檔內容使用的介面不會進行多工處理，因為它們會參考特定的程式碼，該程式是由特定的 DE 所調試的特定程式。 在這種通訊層級中，不需要其他任何取消作業。

 這不是所有內容的事實。 運算式評估內容介面的呼叫會經歷 SDM。 在運算式評估期間，SDM 會包裝它對 IDE 所提供的 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面，因為在評估運算式時，可能會牽涉到多個 DEs 在相同進程中正在相同執行緒上執行的程式。

 SDM 通常會做為委派機制，但它可能會做為廣播機制。 例如，在運算式評估期間，SDM 會作為廣播機制，以通知所有 DEs 可在指定的執行緒上執行程式碼。 同樣地，當 SDM 收到停止事件時，它會廣播至應該停止執行的程式。 當呼叫某個步驟時，SDM 會廣播至可繼續執行的程式。 中斷點也會廣播到每一次 DE。

 SDM 不會追蹤目前的程式、執行緒或堆疊框架。 進程、程式和執行緒資訊會與特定的偵測事件一起傳送至 SDM。

## <a name="see-also"></a>另請參閱
- [Debug 引擎](../../extensibility/debugger/debug-engine.md)
- [偵錯工具元件](../../extensibility/debugger/debugger-components.md)
- [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)
