---
title: "IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerServiceProvider::CreateVisualizerService"
helpviewer_keywords: 
  - "IEEVisualizerServiceProvider::CreateVisualizerService 方法"
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會建立視覺化檢視的服務。  
  
## 語法  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```c#  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### 參數  
 `binder`  
 \[in\][IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件傳遞至[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。  
  
 `pSymProv`  
 \[in\][IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)物件傳遞至`IDebugParsedExpression::EvaluateSync`。  
  
 `pAddress`  
 \[in\][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件傳遞至`IDebugParsedExression::EvaluateSync`。  
  
 `dataProvider`  
 \[in\]物件實作[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) \(運算式評估工具所提供\) 的介面。  
  
 `ppService`  
 \[\] out建立的服務。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 `binder`， `pSymProv`，以及`pAddress`參數已傳遞至`IDebugParsedExpression::EvaluateSync`方法。  `CreateVisualizerService`只從呼叫是`IDebugParsedExpression::EvaluateSync`做為型別視覺化檢視的運算式評估工具支援的一部分。  
  
## 請參閱  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)