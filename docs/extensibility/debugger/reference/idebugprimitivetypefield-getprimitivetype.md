---
title: "IDebugPrimitiveTypeField::GetPrimitiveType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetPrimitiveType"
  - "IDebugPrimitiveTypeField::GetPrimitiveType"
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPrimitiveTypeField::GetPrimitiveType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取這個欄位相關聯的基本型別。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetPrimitiveType (  
   DWORD* pdwType  
);  
```  
  
```c#  
int GetPrimitiveType (  
   out uint pdwType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwType`  
 [out]從值 [CorElementType 列舉](CorElementType%20Enumeration.xml) 表示基本類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 `S_OK`，否則會傳回 `S_FALSE`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)