---
title: IActiveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b7e3a0172a798eab9a743f446dff3d339a785b2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150995"
---
# <a name="iactivescript"></a>IActiveScript
提供初始化指令碼引擎所需的方法。 指令碼引擎必須實作`IActiveScript`介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|通知的指令碼引擎[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)主應用程式所提供的站台。|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|擷取與 Windows 指令碼引擎相關聯的站台物件。|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|指令碼引擎置於指定的狀態。|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|擷取指令碼引擎的目前狀態。|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|使指令碼引擎放棄任何目前載入的指令碼，其狀態，並釋放任何它對其他物件，因此輸入 已關閉的狀態的介面指標。|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|將指令碼引擎的命名空間中的根層級項目名稱。|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|將指令碼的命名空間中的型別程式庫。|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|擷取`IDispatch`介面執行的指令碼。|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|擷取目前執行中執行緒的指令碼引擎-定義識別項。|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|擷取與指定的 Microsoft Win32 執行緒相關聯執行緒的指令碼引擎-定義識別碼。|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|擷取的指令碼執行緒的目前狀態。|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|中斷執行中指令碼的執行緒執行。|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|複製目前指令碼引擎 （減去任何目前的執行狀態），傳回不已在目前的執行緒中的任何網站載入指令碼引擎。|  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)