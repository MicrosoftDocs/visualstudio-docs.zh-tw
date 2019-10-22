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
ms.openlocfilehash: 10dd6366e2d0783ec2e9d6bdadc001e9f999901e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575673"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE 列舉
指定腳本引擎的狀態。 [IActiveScript：： GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) 、 [IActiveScript：： SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)和[IActiveScriptSite：： OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法會使用這個列舉。  
  
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
|SCRIPTSTATE_UNINITIALIZED|腳本剛建立完成，但是尚未使用 `IPersist*` 介面和[IActiveScript：： SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)初始化。|  
|SCRIPTSTATE_INITIALIZED|腳本已經初始化，但不在執行中（連接到其他物件或接收事件）或正在執行任何程式碼。 藉由呼叫[IActiveScriptParse：:P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md)方法，即可查詢程式碼以進行執行。|  
|SCRIPTSTATE_STARTED|腳本可以執行程式碼，但尚未接收[IActiveScript：： AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法所新增之物件的事件。|  
|SCRIPTSTATE_CONNECTED|載入並連接腳本以接收事件。|  
|SCRIPTSTATE_DISCONNECTED|腳本已載入並具有執行時間執行狀態，但暫時與接收事件中斷連接。|  
|SCRIPTSTATE_CLOSED|腳本已關閉。 指令碼引擎不再運作，並傳回大部分方法的錯誤。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)