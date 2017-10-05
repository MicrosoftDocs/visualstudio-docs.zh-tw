---
title: "IDebugObject::SetValue |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 7249c2bc64afea2ca1037cc7fa1cf617357341d7
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
設定物件的值從一系列連續的位元組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pValue`  
 [in]代表新值的位元組陣列。  
  
 `nSize`  
 [in]值，以位元組為單位的大小。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 陣列中的值會複製到這個[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件，並取代任何現有的值。 大於或小於現有的值，可以是新值的大小。 這`IDebugObject`不能是 null 參考。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
