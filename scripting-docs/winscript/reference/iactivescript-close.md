---
title: "IActiveScript::Close |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c90b5d089ea6665060944e0a6f720a43aa1295a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
會導致指令碼引擎放棄任何目前載入的指令碼，其狀態，並釋放任何它對其他物件，因此可進入已關閉的狀態的介面指標。 事件接收器、 立即執行的指令碼文字，以及已經在進行中的巨集引動過程完成之前的狀態變更 (使用[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)取消執行中指令碼的執行緒)。 介面會釋放，以防發生循環參考問題之前，必須呼叫這個方法所建立的主機。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|`S_OK`|成功。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎中已存在於已關閉狀態）。|  
|`OLESCRIPT_S_PENDING`|方法成功，已佇列但狀態未變更。 當狀態變更的站台是在回撥[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法。|  
|`S_FALSE`|方法成功，但已經關閉指令碼。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)