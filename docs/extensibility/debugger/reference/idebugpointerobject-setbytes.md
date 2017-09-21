---
title: "IDebugPointerObject::SetBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::SetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::SetBytes 方法"
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

設定一系列連續的位元組數所指向的值。  
  
## 語法  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### 參數  
 `dwStart`  
 \[in\]位移，以位元組為單位，從一開始所指向的物件。  
  
 `dwCount`  
 \[in\]若要設定的位元組數目。  
  
 `pBytes`  
 \[in\]表示新值的位元組陣列。  這個值會儲存到物件，開始於指定的位移。  
  
 `pdwBytes`  
 \[\] out會傳回實際設定的位元組數目。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 如果使用這個方法的指標，以這[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)所指向的點的基本型別或基本型別 \(也就是物件只能透過簡單的一連串的位元組陣列\) 的簡單陣列。  這`IDebugPointerObject`物件不能是 null 參考 \(它必須指向在記憶體中的地址\)。  
  
## 請參閱  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)