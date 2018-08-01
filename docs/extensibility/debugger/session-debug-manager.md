---
title: 工作階段進行偵錯 Manager |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 109dce19f85e0742217c1c478b1b1687fd5a33e8
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276321"
---
# <a name="session-debug-manager"></a>工作階段偵錯管理員
工作階段的偵錯管理員 (SDM) 管理任何偵錯引擎 (DE) 要進行偵錯跨任意數目的機器的任意數目的多個處理序中的程式的數目。 除了多工器的偵錯引擎，SDM 提供 ide 的偵錯工作階段的統一的檢視。  
  
## <a name="session-debug-manager-operation"></a>工作階段偵錯管理員作業  
 工作階段的偵錯管理員 (SDM) 管理的裝置。 可以有多部電腦上同時執行的偵錯引擎。 若要進行多工處理 DEs，SDM 包裝 DEs 介面的數目，並公開這些屬性的單一介面與 IDE。  
  
 若要增加效能，某些介面不是多工。 相反地，它們會使用直接從德國，和呼叫這些介面並不會通過 SDM。 例如，搭配記憶體、 程式碼，以及文件內容的介面不是多工，因為它們參考特定的指示、 記憶體或在偵錯特定 DE 特定程式的文件。 沒有其他 DE 必須包含在該層級的通訊。  
  
 這不是所有內容的則為 true。 運算式評估內容介面的呼叫皆會透過在 SDM。 運算式評估期間包裝在 SDM [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面，它可讓 IDE 因為評估該運算式時，它可能會牽涉到多個正在偵錯程式可能會在相同處理序的 DEs在相同的執行緒上執行。  
  
 在 SDM 通常是做為委派機制，但它可能會做為廣播機制。 例如，運算式評估期間 SDM 做為廣播機制來通知所有 DEs，他們可以在指定的執行緒上執行程式碼。 同樣地，當 SDM 收到停止事件，它會廣播應該停止執行的程式。 呼叫步驟時，在 SDM 廣播的程式，他們可以繼續執行。 中斷點也會以每個裝置廣播。  
  
 在 SDM 不會追蹤目前的處理序、 執行緒或堆疊框架。 處理程序、 program 和執行緒資訊會傳送至特定的偵錯事件搭配 SDM 中。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)