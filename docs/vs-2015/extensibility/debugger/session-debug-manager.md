---
title: 會話 Debug Manager |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fd7c7555c19f850a15161f6fba00b1184621a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157834"
---
# <a name="session-debug-manager"></a>工作階段偵錯管理員
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

會話 debug manager (SDM) 管理任意數量的偵錯工具， (在任意數目的電腦上，將多個進程中的任何程式數目進行調試) 。 除了做為「偵測引擎多工器」之外，SDM 也提供對 IDE 之 debug 會話的統一觀點。  
  
## <a name="session-debug-manager-operation"></a>會話 Debug Manager 作業  
 會話 debug manager (SDM) 管理 DE。 電腦上可能同時執行一個以上的 debug engine。 為了多工演算法，SDM 會包裝來自 DEs 的一些介面，並將其公開至 IDE 作為單一介面。  
  
 為了提高效能，某些介面不會多工。 相反地，它們會直接從 DE 中使用，而這些介面的呼叫不會經過 SDM。 例如，搭配記憶體、程式碼和檔內容使用的介面不會多工處理，因為它們會參考特定的程式碼，由特定的 DE 所調試的特定程式中的特定指令、記憶體或檔。 在這種通訊層級中，不需要其他任何取消作業。  
  
 這不是所有內容的事實。 運算式評估內容介面的呼叫會經歷 SDM。 在運算式評估期間，SDM 會包裝它對 IDE 所提供的 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面，因為在評估運算式時，可能會牽涉到多個 DEs 在相同進程中正在相同執行緒上執行的程式。  
  
 SDM 通常會做為委派機制，但它可能會做為廣播機制。 例如，在運算式評估期間，SDM 會作為廣播機制，以通知所有 DEs 可在指定的執行緒上執行程式碼。 同樣地，當 SDM 收到停止事件時，它會廣播至應該停止執行的所有程式。 當呼叫某個步驟時，SDM 會廣播至它們可以繼續執行的所有程式。 中斷點也會廣播到每一次 DE。  
  
 SDM 不會追蹤目前的程式、執行緒或堆疊框架。 進程、程式和執行緒資訊會與特定的偵錯工具事件一起傳送至 SDM。  
  
## <a name="see-also"></a>另請參閱  
 [Debug 引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)
