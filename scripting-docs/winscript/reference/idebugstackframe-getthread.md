---
title: "IDebugStackFrame::GetThread |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrame.GetThread
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrame::GetThread
ms.assetid: ece24728-a6b2-4b01-a6f0-0a82b15be39b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 888e15bdd154fbac444eb91fc31ad7f17c2981ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetthread"></a>IDebugStackFrame::GetThread
傳回此堆疊框架相關聯的執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetThread(  
   IDebugApplicationThread**  ppat  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppat`  
 [out]與此堆疊框架關聯的執行緒。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回此堆疊框架相關聯的執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame 介面](../../winscript/reference/idebugstackframe-interface.md)