---
title: "IDebugMethodField::EnumAllLocals |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::EnumAllLocals
helpviewer_keywords: IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2c8208b0d803dc5cbf6333f15cbda5b0f34bbd16
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
建立的方法，包括由編譯器在內部產生的所有區域變數的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 [in][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件，表示在方法中，指向特定範圍或內容的偵錯位址。  
  
 `ppLocals`  
 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)表示的指定範圍中的所有區域變數清單的物件; 否則會傳回 null 值，指出無區域變數。  
  
## <a name="return-value"></a>傳回值  
 如果成功的話，會傳回 S_OK，或如果沒有任何區域變數闇 S_FALSE。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 列舉只能定義在包含指定的偵錯位址區塊內的變數。 這個方法會包含任何編譯器產生的區域變數。 如果所需要的就是來源，呼叫中明確定義的區域變數[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)方法。  
  
 一種方法可以包含多個範圍的內容或區塊。  
  
## <a name="see-also"></a>請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)