---
title: "IActiveScript |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68d91a7ad91364d0c2133150d76cdb221929b16b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescript"></a>IActiveScript
提供初始化指令碼引擎所需的方法。 指令碼引擎必須實作`IActiveScript`介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|通知的指令碼引擎[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)主機提供的站台。|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|擷取 Windows 指令碼引擎與相關聯的站台物件。|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|將指令碼引擎放入指定的狀態。|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|擷取指令碼引擎的目前的狀態。|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|會導致指令碼引擎放棄任何目前載入的指令碼，其狀態，並釋放任何它對其他物件，因此可進入已關閉的狀態的介面指標。|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|將指令碼引擎的命名空間的根層級項目的名稱。|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|將類型程式庫加入至指令碼的命名空間。|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|擷取`IDispatch`執行指令碼的介面。|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|擷取目前執行中執行緒的指令碼引擎-定義識別項。|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|擷取與指定的 Microsoft Win32 執行緒相關聯的執行緒指令碼引擎-定義識別項。|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|擷取目前執行緒狀態的指令碼。|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|會中斷執行中指令碼的執行緒執行。|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|複製目前指令碼引擎 （減去任何目前的執行狀態），傳回不已在目前執行緒中的任何網站載入指令碼引擎。|  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)