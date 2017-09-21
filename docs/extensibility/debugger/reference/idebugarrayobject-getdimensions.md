---
title: "IDebugArrayObject::GetDimensions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetDimensions"
helpviewer_keywords: 
  - "IDebugArrayObject::GetDimensions 方法"
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得陣列的維度。  
  
## 語法  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```c#  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### 參數  
 `dwCount`  
 \[in\]若要擷取的維度數目。  
  
 `dwDimensions`  
 輸入 \[、 輸出\]這類陣列會被填入每個維度的大小。  `dwCount`指定的最大`dwDimensions`陣列。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 多維陣列可以有不同的大小，每個維度。  例如，假設三維陣列`myarray[3][2][6]`，3、 2 和 6 中的，這個方法會傳回`dwDimensions`參數的順序。  
  
## 請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)