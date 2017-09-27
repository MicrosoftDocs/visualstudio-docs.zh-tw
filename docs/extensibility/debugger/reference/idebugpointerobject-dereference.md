---
title: "IDebugPointerObject::Dereference |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
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
ms.openlocfilehash: d69fbe6a4f3c5453053f81cffd1753dca0470438
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
取得指向的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwIndex`  
 [in]簡單的位元組位移，從物件的開頭所指向。  
  
 `ppObject`  
 [out]傳回[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件代表物件指向，再加上位移，如果有的話。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。 如果此物件不是指向另一個物件，則傳回 E_FAIL。  
  
## <a name="remarks"></a>備註  
 指向的物件可以是基本或複雜的類型，例如類別或結構。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
