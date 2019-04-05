---
title: 工作階段進行偵錯 Manager |Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944693"
---
# <a name="session-debug-manager"></a>工作階段偵錯管理員
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

工作階段的偵錯管理員 (SDM) 管理任意數目的任意數目的任意數目的機器上的多個處理程序中的程式進行偵錯的偵錯引擎 (DE)。 除了多工器的偵錯引擎，SDM 提供 ide 的偵錯工作階段的統一的檢視。  
  
## <a name="session-debug-manager-operation"></a>工作階段偵錯管理員作業  
 工作階段的偵錯管理員 (SDM) 管理的裝置。 可能有多部電腦上同時執行的偵錯引擎。 若要進行多工處理 DEs，SDM 包裝 DEs 介面的數目，並公開這些屬性的單一介面與 IDE。  
  
 若要增加效能，某些介面不是多工。 相反地，它們會使用直接從德國，和呼叫這些介面不會通過 SDM。 例如，用於記憶體、 程式碼，以及文件內容的介面是不多工，因為它們參考特定的指示、 記憶體或在偵錯特定 DE 特定程式的文件。 沒有其他 DE 必須包含在該層級的通訊。  
  
 這不是所有內容的則為 true。 運算式評估內容介面的呼叫皆會透過在 SDM。 運算式評估期間包裝在 SDM [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面，它可讓 IDE 因為評估該運算式時，它可能會牽涉到多個正在偵錯程式可能會在相同處理序的 DEs在相同的執行緒上執行。  
  
 在 SDM 通常是做為委派機制，但它可能會做為廣播機制。 例如，運算式評估期間 SDM 做為廣播機制來通知所有 DEs，他們可以在指定的執行緒上執行程式碼。 同樣地，當 SDM 收到停止事件，它會廣播應該停止執行的所有程式。 呼叫步驟時，在 SDM 廣播至所有程式，他們可以繼續執行。 中斷點也會以每個裝置廣播。  
  
 在 SDM 不會追蹤目前的處理序、 執行緒或堆疊框架。 處理程序、 program 和執行緒資訊傳送給特定的偵錯事件搭配 SDM。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)
