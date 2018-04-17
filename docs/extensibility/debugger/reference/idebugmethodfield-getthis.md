---
title: IDebugMethodField::GetThis |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: af534ee57a68158e3f909ba69a1771a5073320e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
取得`this`(`Me`中[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) 的物件，包含方法的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppClass`  
 [out]傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件，代表"this"指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 在物件導向語言中，有通常是目前的具現化類別的隱含的指標。 這稱為`this`在 C# / c + + 和 as`Me`中[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]。  
  
## <a name="see-also"></a>請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)