---
title: "IDebugFunctionObject2::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::Evaluate"
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

呼叫函式，並傳回產生的值做為物件。  
  
## 語法  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### 參數  
 `ppParams`  
 \[in\]陣列的[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ，表示輸入的參數的物件。  這些參數被建立使用這個介面中的其中一個建立方法。  
  
 `dwParams`  
 \[in\]中的參數數目`ppParams`陣列。  
  
 `dwEvalFlags`  
 \[in\]從的旗標組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)列舉型別，指定要如何進行評估。  
  
 `dwTimeout`  
 \[in\]以毫秒為單位，這個方法傳回之前等待指定的最長的時間。  使用**無限**無限期地等待。  
  
 `ppResult`  
 \[\] out傳回 **IDebugObject** ，表示為物件的函式的值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)