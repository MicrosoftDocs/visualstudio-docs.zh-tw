---
title: IDebugField::Equal |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7fdfc2abd407c586c949ade4e8085e282fb465a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984349"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
這個方法會比較此欄位與指定欄位相等。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pField`  
 [in]要與這個比較的欄位。  
  
## <a name="return-value"></a>傳回值  
 如果欄位是相同時，會傳回`S_OK`。 如果欄位不相同，就會傳回`S_FALSE.`否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)