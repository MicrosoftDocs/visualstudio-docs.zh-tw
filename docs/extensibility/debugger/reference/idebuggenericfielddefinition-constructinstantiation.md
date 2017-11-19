---
title: "IDebugGenericFieldDefinition::ConstructInstantiation |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3c11eb3578cd547265a6d0f14727c931364dc0c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
建構指定型別引數陣列的欄位執行個體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cArgs`  
 [in]中的引數`ppArgs`陣列。  
  
 `ppArgs`  
 [in]包含型別引數的陣列。 型別引數必須是關閉的型別 （非泛型或完整具現化泛型）。  
  
 `ppConstructedField`  
 [out]傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面，表示新的欄位。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 不會檢查條件約束。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)