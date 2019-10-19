---
title: IDebugStackFrame：： GetCodeCoNtext |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetCodeContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetCodeContext
ms.assetid: 3dd378f3-e4b7-413e-8812-0f6c72952544
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b640238b9c1212f477c6a26a9cc251678758f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574294"
---
# <a name="idebugstackframegetcodecontext"></a>IDebugStackFrame::GetCodeContext
傳回與堆疊框架相關聯的目前程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppcc`  
 脫銷與堆疊框架相關聯的程式碼內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回與堆疊框架相關聯的目前程式碼內容。  
  
## <a name="see-also"></a>請參閱  
 [IDebugStackFrame 介面](../../winscript/reference/idebugstackframe-interface.md)