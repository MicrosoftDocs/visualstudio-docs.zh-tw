---
title: IDebugStackFrameSnifferEx：： EnumStackFramesEx |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a4062e7c0a9b3a82578daffa2ab7ef7e9ba614d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576701"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
傳回目前線程之堆疊框架的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwSpMin`  
 在列舉堆疊框架的較低位址限制。  
  
 `ppedsf`  
 脫銷目前線程之堆疊框架的列舉值。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 堆疊框架列舉值會傳回從堆疊頂端開始的框架，以及最近推送的框架。 列舉值只包含位址大於或等於 `dwSpMin` 的堆疊框架。  
  
## <a name="see-also"></a>請參閱  
 [IDebugStackFrameSnifferEx 介面](../../winscript/reference/idebugstackframesnifferex-interface.md)