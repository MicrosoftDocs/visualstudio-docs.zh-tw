---
title: IDebugStackFrame::GetDescriptionString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDescriptionString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDescriptionString
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f6479485a508f71797d6965f71edd3253927088
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097223"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
傳回堆疊框架的短或長時間的文字描述。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fLong`  
 [in]旗標，其中`TRUE`傳回的詳細描述和`FALSE`傳回的簡短描述。  
  
 `pbstrDescription`  
 [out]堆疊框架的描述。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 一般而言，如果`fLong`是`FALSE`，這個方法會提供函式的堆疊框架相關聯的名稱。 當`fLong`是`TRUE`，這個方法也可提供函式參數和其他相關資訊。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame 介面](../../winscript/reference/idebugstackframe-interface.md)