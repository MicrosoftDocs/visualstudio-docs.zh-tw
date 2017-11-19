---
title: "IDebugStackFrame::GetDebugProperty |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrame.GetDebugProperty
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrame::GetDebugProperty
ms.assetid: e03c7504-bce4-4a44-81e4-db8c0216538d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 898c80dc4f5ef9010db6396a78c1b17b50603dc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetdebugproperty"></a>IDebugStackFrame::GetDebugProperty
傳回目前的框架屬性瀏覽器。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetDebugProperty(  
   IDebugProperty**  ppDebugProp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppDebugProp`  
 [out]目前的框架屬性瀏覽器。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回目前的框架屬性瀏覽器。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame 介面](../../winscript/reference/idebugstackframe-interface.md)