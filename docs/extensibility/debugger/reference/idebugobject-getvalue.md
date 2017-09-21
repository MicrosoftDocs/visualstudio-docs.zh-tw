---
title: "IDebugObject::GetValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetValue"
helpviewer_keywords: 
  - "IDebugObject::GetValue 方法"
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得物件的值，以連續的一連串的位元組。  
  
## 語法  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```c#  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### 參數  
 `pValue`  
 輸入 \[、 輸出\]陣列中以連續的一連串的位元組代表物件的值填滿。  
  
 `nSize`  
 \[in\]要擷取的位元組數目上限。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 取得的值可以藉由呼叫讀取的位元組總數[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)方法。  
  
## 請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)