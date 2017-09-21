---
title: "IDebugFunctionObject2::CreateObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::CreateObject"
  - "建立物件"
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立使用建構函式評估的旗標設定和等候逾時值的物件。  
  
## 語法  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### 參數  
 `pConstructor`  
 \[in\][IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)物件，表示要建立物件的建構函式。  
  
 `dwArgs`  
 \[in\]中的參數數目`pArg`陣列。  表示傳遞至建構函式的參數數目。  
  
 `pArgs`  
 \[in\]陣列的[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ，表示參數的物件傳遞至建構函式。  
  
 `dwEvalFlags`  
 \[in\]從的旗標組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)列舉型別，指定要如何進行評估。  
  
 `dwTimeout`  
 \[in\]最大時間 \(毫秒\)，從這個方法傳回之前等待。  使用**無限**無限期地等待。  
  
 `ppObject`  
 \[\] out傳回 **IDebugObject** 代表剛建立的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 呼叫這個方法來建立物件，表示類別或其他複雜型別所需的建構函式，為參數的執行個體。  
  
## 請參閱  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)