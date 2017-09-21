---
title: "IDebugPointerObject::GetBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::GetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::GetBytes 方法"
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得指向分頁，作為一系列連續的位元組的值。  
  
## 語法  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### 參數  
 `dwStart`  
 \[in\]位移，以位元組為單位，從一開始所指向的物件。  
  
 `dwCount`  
 \[in\]若要擷取的位元組數目。  
  
 `pBytes`  
 輸入 \[、 輸出\]被填入的值為一系列連續的位元組陣列，開始於指定的位移，從物件所指向。  
  
 `pdwBytes`  
 \[\] out傳回實際擷取的位元組的數目。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 如果使用這個方法的指標，以這[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)所指向的點的基本型別或基本型別 \(也就是物件只能透過簡單的一連串的位元組陣列\) 的簡單陣列。  
  
## 請參閱  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)