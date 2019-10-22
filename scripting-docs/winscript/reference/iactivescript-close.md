---
title: IActiveScript：： Close |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f858de42ef2948d218aac6c3194cc6af544da5e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575785"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
使腳本引擎放棄任何目前載入的腳本、失去其狀態，以及釋放它對其他物件的任何介面指標，因而進入封閉式狀態。 事件接收器、立即執行的腳本文字，以及已在進行中的宏調用，會在狀態變更之前完成（使用[IActiveScript：： InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)來取消執行中的腳本執行緒）。 在釋放介面之前，建立主控制項必須呼叫這個方法，以避免發生迴圈參考問題。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|值|意義|  
|-----------|-------------|  
|`S_OK`|成功。|  
|`E_UNEXPECTED`|不需要進行呼叫（例如，腳本引擎已處於 [已關閉] 狀態）。|  
|`OLESCRIPT_S_PENDING`|已成功將方法排入佇列，但狀態尚未變更。 當狀態變更時，會在[IActiveScriptSite：： OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法上呼叫網站。|  
|`S_FALSE`|方法成功，但腳本已經關閉。|  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)