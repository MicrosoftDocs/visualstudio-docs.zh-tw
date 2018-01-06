---
title: "工作階段偵錯 Manager |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7d7acd147fd8d2b73b2172900baf7e1f49808e9a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="session-debug-manager"></a>工作階段偵錯管理員
工作階段的偵錯管理員 (SDM) 會管理任何數目的偵錯引擎 (DE) 偵錯任意數目的任意數目的機器上的多個處理程序中的程式。 除了多工器偵錯引擎，SDM 會提供 ide 偵錯工作階段的統一的檢視。  
  
## <a name="session-debug-manager-operation"></a>工作階段偵錯管理員作業  
 工作階段的偵錯管理員 (SDM) 管理 DE。 可能有多部電腦上同時執行的偵錯引擎。 多工處理 DEs，SDM 包裝的 DEs 介面的數字，其公開為單一介面 ide。  
  
 若要增加效能，某些介面不是多工。 相反地，其使用直接從 DE，以及這些介面的呼叫不會通過 SDM。 例如，用於記憶體、 程式碼，以及文件內容的介面都是不多工，因為兩者參考特定指令、 記憶體或文件中的特定 DE 偵錯的特定程式。 沒有其他 DE 必須涉及在該層級的通訊。  
  
 這不是所有內容的則為 true。 運算式評估內容介面呼叫移到 SDM。 在運算式評估期間包裝 SDM [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面，它可讓在 IDE 因為評估該運算式時，它可能包含多個正在偵錯程式可能之同一處理序的 DEs在相同執行緒上執行。  
  
 SDM 通常是做為委派機制，但它可能會做為廣播機制。 例如，在運算式評估期間 SDM 做為廣播機制來通知所有 DEs，它們可以在指定的執行緒上執行程式碼。 同樣地，當 SDM 收到停止事件，它會廣播，應停止執行的所有程式。 呼叫步驟時，SDM 廣播到所有程式，他們可以繼續執行。 中斷點也已廣播給每個 DE 中。  
  
 SDM 不會追蹤目前的處理序、 執行緒或堆疊框架。 處理程序、 程式和執行緒資訊傳送給特定的偵錯事件搭配 SDM。  
  
## <a name="see-also"></a>請參閱  
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)