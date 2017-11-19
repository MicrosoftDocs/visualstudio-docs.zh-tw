---
title: "IDebugMethodField::GetGlobalContainer |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::GetGlobalContainer
helpviewer_keywords: IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ffeb7c7c1abe6e5a816c2d7a67ad6820e0921bc8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
取得全域方法的容器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppClass`  
 [out]傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)代表這個方法定義所在的模組。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件代表整個模組，而且是假造的物件，也就是模組本身並沒有實際的類別，但以表示`IDebugClassField`物件，讓各種要列舉並探索到之模組的項目。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)