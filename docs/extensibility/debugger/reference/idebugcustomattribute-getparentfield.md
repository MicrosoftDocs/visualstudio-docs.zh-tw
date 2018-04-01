---
title: IDebugCustomAttribute::GetParentField |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: cad1876a366f46c11e296dc58d5ad4f01e6583f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
取得要附加自訂屬性的欄位。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppField`  
 [out]傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，代表要附加自訂屬性的欄位。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法在傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)來判斷什麼種類的欄位父物件。  
  
## <a name="see-also"></a>請參閱  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)