---
title: IDebugMethodField::EnumParameters |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f60fbde074f660647aedd65a7bae7f98576d485d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
建立方法的參數的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppParams`  
 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)表示方法的參數清單的物件; 否則傳回 null 值，如果沒有任何參數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK，或如果沒有任何參數，則傳回 S_FALSE。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 每個項目是[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，代表不同類型的參數。 呼叫[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)每個物件，以判斷正確的參數類型所代表的物件上的方法。  
  
 參數包含其變數名稱和其型別。 類別方法的第一個參數通常是"this"指標。  
  
 如果只需要參數的類型時，呼叫[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)方法。  
  
## <a name="see-also"></a>請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)