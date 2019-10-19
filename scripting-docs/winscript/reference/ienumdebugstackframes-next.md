---
title: IEnumDebugStackFrames：： Next |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17261f8ba9b2957d33ed7019c16f2e1423b6b42e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575555"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
抓取列舉序列中指定數目的區段。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 在要取出的區段數目。  
  
 `prgdsfd`  
 脫銷傳回 `DebugStackFrameDescriptor` 介面的陣列，表示要抓取的區段。  
  
 `pceltFetched`  
 脫銷列舉值所提取的實際區段數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會抓取列舉序列中指定數目的區段。  
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugStackFrames 介面](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [DebugStackFrameDescriptor 結構](../../winscript/reference/debugstackframedescriptor-structure.md)