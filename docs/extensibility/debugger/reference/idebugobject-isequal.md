---
title: "IDebugObject::IsEqual |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::IsEqual
helpviewer_keywords: IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d5fd33bf626fe04159ac5bae12c586776ac334e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
比較物件與此物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pObject`  
 [in][IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件，代表要比較的物件。  
  
 `pfIsEqual`  
 [out]傳回非零 (`TRUE`) 如果物件的值相等，否則，傳回零 (`FALSE`)。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 一般而言，這個方法來比較所代表之值的位址`pObject`參數，而這[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件; 如果的位址是相等的物件可視為相等。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)