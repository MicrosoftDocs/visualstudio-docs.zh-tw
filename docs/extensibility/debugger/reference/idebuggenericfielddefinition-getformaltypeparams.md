---
title: "IDebugGenericFieldDefinition::GetFormalTypeParams | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetFormalTypeParams"
  - "IDebugGenericFieldDefinition::GetFormalTypeParams"
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericFieldDefinition::GetFormalTypeParams
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取指定的參數數目的型別參數。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```c#  
int GetFormalTypeParams(  
   uint                          cParams,  
   out IDebugGenericParamField[] ppParams,  
   ref uint                      pcParams  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cParams`  
 [in]參數的數目。  
  
 `ppParams`  
 [out]型別參數的陣列。  
  
 `pcParams`  
 [in、 out]中的參數數目 `ppParams` 陣列。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 `S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 傳回型別參數的順序從左到右。 例如，字典 \< K，V > 會傳回 IDebugFormalGenericParameters {K，V}。  
  
## <a name="see-also"></a>請參閱  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)