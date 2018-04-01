---
title: IEnumDebugBoundBreakpoints2::Clone |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugBoundBreakpoints2::Clone
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Clone
ms.assetid: c6ce01a2-7da3-46ec-9837-855042fa7244
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d264aea3918f7e6d36e112cd3b7d0568214838c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugboundbreakpoints2clone"></a>IEnumDebugBoundBreakpoints2::Clone
傳回目前的列舉，為個別物件的複本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Clone(  
   IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回這個列舉型別為個別物件的複本。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 列舉的副本會呼叫這個方法只有在有相同的原始狀態。 不過，複製和原始的狀態分開的而且可以個別變更。  
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)