---
title: "IDebugGenericFieldDefinition::TypeParamCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TypeParamCount"
  - "IDebugGenericFieldDefinition::TypeParamCount"
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugGenericFieldDefinition::TypeParamCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取一般欄位相關聯的型別參數的數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT TypeParamCount(  
   ULONG32* pcParams  
);  
```  
  
```c#  
int TypeParamCount(  
   ref uint pcParams  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcParams`  
 [in、 out]類型參數的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 `S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果清單 \< T>, ，這個方法會傳回 1，並在清單 \< T1、 T2 >，這個方法會傳回 2。 如果沒有型別參數，這個方法會傳回 0。  
  
## <a name="see-also"></a>請參閱  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)