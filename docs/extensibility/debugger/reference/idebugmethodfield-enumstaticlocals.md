---
title: "IDebugMethodField::EnumStaticLocals |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::EnumStaticLocals
helpviewer_keywords: IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0aa4a5e044dfc28302735e058c8863d4eb683670
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
建立方法的靜態區域變數的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppLocals`  
 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，代表靜態區域變數的清單。 如果沒有任何靜態區域變數，則傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK，或如果沒有任何靜態區域變數闇 S_FALSE。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 每個項目是[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，代表不同類型的靜態區域變數。 呼叫[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)每個物件，以判斷確切的靜態區域變數的類型所代表的物件上的方法。  
  
## <a name="see-also"></a>請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)