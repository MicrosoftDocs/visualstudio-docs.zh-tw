---
title: Windows Script Hosts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Script Host, implementing hosts
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eec1824bd3ba1a8acb7e3c540656151cd4b11d1f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145105"
---
# <a name="windows-script-hosts"></a>Windows Script Host
實作 Microsoft Windows Script Host 時，您可以安全地假設指令碼引擎只呼叫基底執行緒內容中的 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 介面，只要主機進行下列作業：  
  
- 選擇基底執行緒 (通常是包含訊息迴圈的執行緒)。  
  
- 在基底執行緒中具現化指令碼引擎。  
  
- 除非特別允許，如 [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) 和 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) 的情況，否則只從基底執行緒呼叫指令碼引擎方法。  
  
- 只從基底執行緒呼叫指令碼引擎的分派物件。  
  
- 如果提供視窗控制代碼，確保訊息迴圈會在基底執行緒中執行。  
  
- 確保主機物件模型中的物件，只以基底執行緒中的事件為來源。  
  
  所有單一執行緒的主機都會自動遵循這些規則。 上述限制模型是刻意鬆散到足以允許主機放棄無法停止的指令碼，只要從另一個執行緒 (由 CTRL+BREAK 或類似的處理常式起始) 呼叫 [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md)，或使用 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) 複製新執行緒中的指令碼。  
  
## <a name="remarks"></a>備註  
 這些限制都不適用選擇實作無限制執行緒 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 介面和無限制執行緒物件模型的主機。 這類主機可以從任何執行緒使用 [IActiveScript](../winscript/reference/iactivescript.md) 介面，完全沒有限制。  
  
## <a name="see-also"></a>請參閱  
 [Windows 指令碼的介面](../winscript/windows-script-interfaces.md)