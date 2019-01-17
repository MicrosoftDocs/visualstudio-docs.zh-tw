---
title: IActiveScript::Close | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 886ab1c4c39cf7c64571862bfd28f2fbd1062694
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348799"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
使指令碼引擎放棄任何目前載入的指令碼，其狀態，並釋放任何它對其他物件，因此輸入 已關閉的狀態的介面指標。 事件接收器、 立即執行的指令碼的文字，並已在進行中的巨集引動過程完成之前的狀態變更 (使用[iactivescript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md)取消執行中指令碼的執行緒)。 介面會發行以避免循環參考問題之前，必須呼叫這個方法所建立的主機。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|`S_OK`|成功。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎已存在於已關閉狀態）。|  
|`OLESCRIPT_S_PENDING`|方法已排入佇列成功，但是狀態未變更。 當狀態變更的站台是以回撥[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法。|  
|`S_FALSE`|此方法成功，但指令碼已關閉。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)