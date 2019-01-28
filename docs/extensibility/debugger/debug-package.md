---
title: 偵錯封裝 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb843e63dbc4ff711b56ff457ca930dc9df0207
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010177"
---
# <a name="debug-package"></a>偵錯封裝
偵錯封裝在 Visual Studio shell 中執行，並會處理所有的使用者介面。 它會使用 Visual Studio 偵錯介面，並與工作階段的偵錯管理員 (SDM) 通訊。  
  
 透過在 SDM 傳送 break 事件切換偵錯工具執行模式下從中斷模式，並將焦點變更為在發生中斷的程式。 偵錯封裝會從資訊傳送給它的事件追蹤的堆疊框架和執行緒。  
  
 偵錯封裝有任何語言或執行階段環境相依性。 您不需要實作或修改套件偵錯。  
  
 偵錯封裝由實作*vsdebug.dll*。  
  
## <a name="see-also"></a>另請參閱  
 [工作階段偵錯管理員](../../extensibility/debugger/session-debug-manager.md)   
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [執行緒](../../extensibility/debugger/threads.md)   
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)