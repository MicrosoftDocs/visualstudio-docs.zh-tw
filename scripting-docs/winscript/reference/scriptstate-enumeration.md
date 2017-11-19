---
title: "SCRIPTSTATE 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e062a9c2f3076144063ffb77895c8a03ecc4ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE 列舉
指定指令碼引擎的狀態。 這個列舉型別由[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) ， [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) ，和[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>列舉值  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|指令碼剛剛建立，但是尚未已初始化使用`IPersist*`介面和[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) 。|  
|SCRIPTSTATE_INITIALIZED|指令碼已初始化，但為不執行 （連接至其他物件或接收事件） 或執行任何程式碼。 程式碼可以執行查詢，藉由呼叫[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)方法。|  
|SCRIPTSTATE_STARTED|指令碼可以執行程式碼，但還未接收由新增的物件事件[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法。|  
|SCRIPTSTATE_CONNECTED|指令碼是載入，而且連線的接收事件。|  
|SCRIPTSTATE_DISCONNECTED|指令碼載入和執行階段的執行狀態，但暫時中斷連線時接收事件。|  
|SCRIPTSTATE_CLOSED|指令碼已關閉。 指令碼引擎不再運作，並傳回大部分方法的錯誤。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)