---
title: "IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IEEVisualizerService::GetValueDisplayStringCount"
  - "GetValueDisplayStringCount"
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEEVisualizerService::GetValueDisplayStringCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取值的字串，以顯示指定的屬性或欄位的數目。  
  
## 語法  
  
```cpp#  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```c#  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### 參數  
 `displayKind`  
 \[in\]從數值[DisplayKind](../../../extensibility/debugger/reference/displaykind.md)列舉型別。  
  
 `propertyOrField`  
 \[in\][IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ，表示屬性或欄位的介面。  
  
 `pcelt`  
 \[\] out傳回值的字串，以顯示數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)