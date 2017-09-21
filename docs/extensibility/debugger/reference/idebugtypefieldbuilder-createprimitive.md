---
title: "IDebugTypeFieldBuilder::CreatePrimitive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CreatePrimitive"
  - "IDebugTypeFieldBuilder::CreatePrimitive"
ms.assetid: 512c6ff0-97c5-409f-939f-4cc969bc4bb9
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugTypeFieldBuilder::CreatePrimitive
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立代表基本類型的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT CreatePrimitive (  
   DWORD          dwElementType,  
   IDebugField ** pTypeField  
);  
```  
  
```c#  
int CreatePrimitive (  
   uint            dwElementType,  
   out IDebugField pTypeField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwElementType`  
 [in]從值 [CorElementType 列舉](CorElementType%20Enumeration.xml) 表示基本類型。  
  
 `pTypeField`  
 [out]傳回新的類型 IDebugField 介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 `S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)