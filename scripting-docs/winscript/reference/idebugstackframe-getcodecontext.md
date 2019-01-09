---
title: IDebugStackFrame::GetCodeContext |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 14c7acc9070edb0e63dee8c71cb0b16c5f85e4cd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095611"
---
# <a name="idebugstackframegetcodecontext"></a>IDebugStackFrame::GetCodeContext
傳回目前的堆疊框架相關聯的程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppcc`  
 [out]程式碼相關聯的內容與堆疊框架。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回目前的堆疊框架相關聯的程式碼內容。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame 介面](../../winscript/reference/idebugstackframe-interface.md)