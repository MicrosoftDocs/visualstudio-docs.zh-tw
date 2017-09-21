---
title: "IDebugAddress::GetAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress::GetAddress"
helpviewer_keywords: 
  - "IDebugAddress:GetAddress 方法"
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回結構描述物件和它的範圍或容器中的位置。  
  
## 語法  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```c#  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### 參數  
 `pAddress`  
 輸入 \[、 輸出\]A [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構，這個方法會填入。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構傳遞給這個方法，然後以適當的資訊在填滿它。  這項資訊的解譯方式，則傳回的資訊和符號處理常式本身的種類而定。  如需詳細資訊，請參閱 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)。  
  
## 請參閱  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)