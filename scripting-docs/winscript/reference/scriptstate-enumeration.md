---
title: SCRIPTSTATE 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe6a05c5e73d26a8daa9e46c317422d85d1c40be
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155546"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE 列舉
指定指令碼引擎的狀態。 這個列舉型別由[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) ， [iactivescript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) ，並[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
|SCRIPTSTATE_UNINITIALIZED|指令碼剛剛建立，但還尚未初始化使用`IPersist*`介面和[iactivescript:: Setscriptsite](../../winscript/reference/iactivescript-setscriptsite.md) 。|  
|SCRIPTSTATE_INITIALIZED|指令碼已初始化，但未執行 （連接至其他物件或接收事件） 或執行任何程式碼。 程式碼可以執行查詢，藉由呼叫[iactivescriptparse:: Parsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md)方法。|  
|SCRIPTSTATE_STARTED|指令碼可以執行程式碼，但還未接收的事件所加入的物件[iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md)方法。|  
|SCRIPTSTATE_CONNECTED|指令碼會載入，並已連線的接收事件。|  
|SCRIPTSTATE_DISCONNECTED|指令碼會載入和執行階段的執行狀態，但暫時中斷接收事件。|  
|SCRIPTSTATE_CLOSED|指令碼已關閉。 指令碼引擎不再運作，並傳回大部分方法的錯誤。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)