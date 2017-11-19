---
title: "IDebugGenericFieldDefinition::GetFormalTypeParams |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 12325210ca73b82a84aece8726637b67eda5867a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
擷取指定的參數數目的型別參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```csharp  
int GetFormalTypeParams(  
   uint                          cParams,  
   out IDebugGenericParamField[] ppParams,  
   ref uint                      pcParams  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cParams`  
 [in]參數數目。  
  
 `ppParams`  
 [out]型別參數的陣列。  
  
 `pcParams`  
 [in、 out]中的參數數目`ppParams`陣列。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 傳回的型別參數順序從左到右。 例如，字典\<K，V > 傳回 IDebugFormalGenericParameters {K，V}。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)