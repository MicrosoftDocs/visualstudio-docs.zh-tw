---
title: "IEnumDebugReferenceInfo2::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugReferenceInfo2::Reset"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2::Reset"
ms.assetid: cf8ce649-5ce1-44a6-9d5a-89760021bde4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugReferenceInfo2::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

將重設第一個項目，為列舉型別。  
  
## 語法  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```c#  
int Reset();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法呼叫下, 一步呼叫之後[下一步](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)方法會傳回列舉型別的第一個項目。  
  
## 請參閱  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)