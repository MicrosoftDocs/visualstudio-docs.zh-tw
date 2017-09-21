---
title: "IEnumDebugCustomAttributes::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes::Reset"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes::Reset"
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCustomAttributes::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

將列舉型別 \(Enumeration\) 序列重設到開頭。  
  
## 語法  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法呼叫下, 一步呼叫之後[下一步](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)方法會傳回列舉型別的第一個項目。  
  
## 請參閱  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)