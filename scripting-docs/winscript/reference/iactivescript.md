---
title: IActiveScript |Microsoft Docs
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
ms.openlocfilehash: 7a33db2bcbcb356a508fec2e6bc5449a899a1299
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577242"
---
# <a name="iactivescript"></a>IActiveScript
提供初始化腳本引擎所需的方法。 腳本引擎必須執行 `IActiveScript` 介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|通知主機所提供之[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)網站的腳本引擎。|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|抓取與 Windows 腳本引擎相關聯的網站物件。|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|將腳本引擎置於指定的狀態。|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|抓取腳本引擎的目前狀態。|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|使腳本引擎放棄任何目前載入的腳本、失去其狀態，以及釋放它對其他物件的任何介面指標，因而進入封閉式狀態。|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|將根層級專案的名稱加入腳本引擎的命名空間。|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|將類型程式庫加入至腳本的命名空間。|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|抓取執行中腳本的 `IDispatch` 介面。|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|針對目前執行中的執行緒，抓取腳本引擎定義的識別碼。|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|針對與指定的 Microsoft Win32 執行緒相關聯的執行緒，抓取腳本引擎定義的識別碼。|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|抓取腳本執行緒的目前狀態。|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|中斷執行中腳本執行緒的執行。|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|複製目前的腳本引擎（減去任何目前的執行狀態），並傳回在目前線程中沒有任何網站的已載入腳本引擎。|  
  
## <a name="see-also"></a>請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)