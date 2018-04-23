---
title: IDebugCustomAttribute::GetAttributeTypeField |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53511cf8549071795576c661e6a38f0c0973d269
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
取得自訂屬性的類別類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAttributeTypeField(   
   IDebugClassField** ppCAType  
);  
```  
  
```csharp  
int GetAttributeTypeField(  
   out IDebugClassField ppCAType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppCAType`  
 [out]傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件，表示為的類別的自訂屬性執行個體。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 自訂屬性一定是類別。 這個方法會提供存取[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)描述該類別的物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)