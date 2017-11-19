---
title: "IDebugArrayField::GetElementType |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayField::GetElementType
helpviewer_keywords: IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2286f201e358a190510fdff634b01f7ec9a64d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
取得項目的型別陣列中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppType`  
 [out]傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)描述項目類型的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)物件假設陣列的所有項目是相同的型別。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)